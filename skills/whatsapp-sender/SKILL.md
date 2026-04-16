---
name: "whatsapp-sender"
description: "Webhook tabanlı WhatsApp mesaj gönderimi. Kullanıcı bir mesaj göndermek istediğinde bu yeteneği kullanın. Telefon numarası veya mesaj metni eksikse kullanıcıdan talep edin."
---

# WhatsApp Mesaj Gönderici (Agent Skill)

Bu beceri, on-device LLM'in harici bir n8n webhook'u aracılığıyla WhatsApp mesajları göndermesini sağlar.

## Kullanım Durumları (Triggers)
- Birine WhatsApp mesajı gönderilmek istendiğinde.
- "X kişisine Y mesajını at" gibi komutlarda.
- WhatsApp üzerinden iletişim kurma taleplerinde.

## Talimatlar
1.  **Doğrulama:** `phone_number` ve `message_text` parametrelerinin mevcut olduğundan emin olun.
2.  **Eksik Bilgi:** Eğer numara eksikse "Kime göndermemi istersiniz?" diye sorun. Mesaj eksikse "Mesajınız ne olsun?" diye sorun.
3.  **Format:** Telefon numarasının uluslararası formatta (+ ile başlayan) olmasını tercih edin, ancak kullanıcı sadece rakam verirse kabul edin.
4.  **İşlem:** Bilgiler tamamsa `send_whatsapp_message` aracını çağırın.

## Araçlar

### send_whatsapp_message
Arka plandaki bir webview aracılığıyla mesajı webhook'a iletir.

**Parametreler:**
- `phone_number` (string, required): Alıcının telefon numarası. Örn: "+905001234567"
- `message_text` (string, required): Gönderilecek metin içeriği.

**Yanıtlar:**
- `status: "success"` -> Mesaj başarıyla sıraya alındı.
- `status: "error"` -> Bir ağ hatası veya webhook sorunu oluştu.
