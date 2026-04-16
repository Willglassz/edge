---
name: whatsapp-sender
description: A skill to open WhatsApp natively with a prepared message and phone number. No API key needed.
metadata:
  homepage: https://github.com/Willglassz/edge/tree/main/whatsapp-sender
---

# WhatsApp Yerel Mesaj Gönderici (Agent Skill)

Bu beceri, cihazdaki WhatsApp uygulamasını belirli bir numara ve mesajla doğrudan açmak için Android Intent mekanizmasını kullanır. Herhangi bir API anahtarı veya ücretli servis gerektirmez.

## Kullanım Durumları (Triggers)
- Birine WhatsApp mesajı gönderilmek istendiğinde.
- "WhatsApp'tan X kişisine Y mesajını at" gibi komutlarda.
- WhatsApp üzerinden iletişim kurma taleplerinde.

## Talimatlar
1.  **Doğrulama:** `phone_number` ve `message_text` parametrelerinin mevcut olduğundan emin olun.
2.  **Eksik Bilgi:** Eğer numara eksikse "Kime göndermemi istersiniz?" diye sorun. Mesaj eksikse "Mesajınız ne olsun?" diye sorun.
3.  **Kullanıcı Bilgilendirme:** Bu yöntemde WhatsApp uygulaması açılacaktır. Kullanıcıya **"WhatsApp'ı açıyorum, lütfen gönder butonuna basın."** şeklinde bilgi verin.
4.  **İşlem:** Bilgiler tamamsa `send_whatsapp_message` aracını çağırın.

## Araçlar

### send_whatsapp_message
Cihazdaki WhatsApp uygulamasını (veya web sürümünü) numara ve mesaj hazır şekilde ön plana çıkarır.

**Parametreler:**
- `phone_number` (string, required): Alıcının telefon numarası. Örn: "+905001234567"
- `message_text` (string, required): Hazırlanacak mesaj içeriği.

**Yanıtlar:**
- `status: "success"` -> WhatsApp uygulaması başarıyla tetiklendi.
- `status: "error"` -> Uygulama açılırken bir hata oluştu.
