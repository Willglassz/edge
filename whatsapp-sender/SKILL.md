---
name: whatsapp-sender
description: Bu yetenek, LLM'in bir webhook aracılığıyla WhatsApp mesajları göndermesini sağlar. Telefon numarası veya mesaj metni eksikse kullanıcıya sormayı bilir.
---

# WhatsApp Mesaj Gönderici

Bu yetenek, bir on-device LLM'in bir webhook servisi (n8n gibi) üzerinden WhatsApp mesajları göndermesine olanak tanır.

## Talimatlar

1.  **Bilgi Kontrolü:** Kullanıcı bir mesaj göndermek istediğinde, her zaman mesaj metnini (`message_text`) ve alıcının telefon numarasını (`phone_number`) kontrol edin.
2.  **Eksik Bilgi:** Eğer telefon numarası veya mesaj metni sağlanmamışsa, devam etmeden önce nazikçe bu bilgileri kullanıcıdan isteyin.
3.  **Araç Çağrısı:** Her iki bilgi de mevcut olduğunda, `send_whatsapp_message` aracını uygun parametrelerle çağırın.

## Araçlar

### send_whatsapp_message

WhatsApp mesajını bir arka plan işlemi (webview) aracılığıyla webhook'a gönderir.

**Parametreler:**

- `phone_number` (string): Mesajın gönderileceği uluslararası formatta telefon numarası (örn: "+905001234567").
- `message_text` (string): Gönderilecek mesajın içeriği.
