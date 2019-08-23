---
title: İleti Güvenliğinde Etkinlik İzleme
ms.date: 03/30/2017
ms.assetid: 68862534-3b2e-4270-b097-8121b12a2c97
ms.openlocfilehash: bb8a4c6782cc52de393eacc2458e216d0f069866
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933524"
---
# <a name="activity-tracing-in-message-security"></a>İleti Güvenliğinde Etkinlik İzleme
Bu konu, aşağıdaki üç aşamada gerçekleşen güvenlik işleme için Etkinlik izlemeyi açıklar.  
  
- Anlaşma/SCT değişimi. Bu, aktarımda daha sonra (ikili veri değişimi aracılığıyla) veya ileti katmanında (SOAP ileti alışverişi aracılığıyla) oluşabilir.  
  
- İmza doğrulama ve kimlik doğrulama ile ileti şifreleme/şifre çözme. İzlemeler, genellikle "Işlem eylemi" çevresel etkinlikte görüntülenir.  
  
- Yetkilendirme ve doğrulama. Bu durum yerel olarak veya uç noktalar arasında iletişim kurulurken gerçekleşebilir.  
  
## <a name="negotiationsct-exchange"></a>Anlaşma/SCT değişimi  
 Anlaşma/SCT değişim aşamasında, istemcide iki etkinlik türü oluşturulur: "Güvenli oturum ayarla" ve "güvenli oturumu Kapat". ' Güvenli oturum ayarlama ", RST/RSTR/SCT ileti değişimlerinin izlerini kapsar," güvenli oturumu Kapat ", Iptal iletisi için izlemeleri içerir.  
  
 Sunucusunda, RST/RSTR/SCT için her istek/yanıt kendi etkinliğinde görüntülenir. Hem sunucu hem de istemcide, sunucudaki etkinliklerin kimliği aynı olmalıdır ve hizmet izleme Görüntüleyicisi aracılığıyla görüntülendiğinde "güvenli oturum ayarla" bölümünde birlikte görüntülenir. `propagateActivity` = `true`  
  
 Bu etkinlik izleme modeli Kullanıcı adı/parola kimlik doğrulaması, sertifika kimlik doğrulaması ve NTLM kimlik doğrulaması için geçerlidir.  
  
 Aşağıdaki tabloda, anlaşma ve SCT alışverişi için etkinlikler ve izlemeler listelenmektedir.  
  
||Anlaşmanın/SCT değişiminin meydana geldiğinde geçen süre|Etkinlikler|Lerin|  
|-|-------------------------------------------------|----------------|------------|  
|Güvenli aktarım<br /><br /> (HTTPS, SSL)|Alınan ilk ileti.|İzlemeler çevresel etkinlikte dağıtılır.|-Exchange izlemeleri<br />-Güvenli kanal oluşturuldu<br />-Share gizli dizileri alındı.|  
|Güvenli Ileti katmanı<br /><br /> (WSHTTP)|Alınan ilk ileti.|İstemcide:<br /><br /> -RST/RSTR/SCT için her istek/yanıt için, bu ilk iletinin "Işlem eylemi" için "güvenli oturum ayarla" ayarı.<br />-"Proxy 'yi kapat etkinliği" dışında, Exchange Iptal için "güvenli oturumu Kapat". Bu etkinlik, güvenli oturumun ne zaman kapandığına bağlı olarak diğer bazı çevresel etkinlikten kaynaklanabilir.<br /><br /> Sunucusunda:<br /><br /> -Sunucu üzerinde RST/SCT/Cancel için her istek/yanıt için bir "Işlem eylemi" etkinliği. , RST/RSTR/SCT etkinlikleri "güvenlik oturumu ayarla" ile birleştirilir ve iptal, istemciden "Kapat" etkinliğiyle birleştirilir. `propagateActivity` = `true`<br /><br /> "Güvenli oturum ayarlama" için iki aşama vardır:<br /><br /> 1.  Kimlik doğrulama anlaşması. İstemci zaten uygun kimlik bilgilerine sahipse bu isteğe bağlıdır. Bu aşama, güvenli aktarım veya ileti alışverişi aracılığıyla yapılabilir. İkinci durumda, 1 veya 2 RST/RSTR alışverişi meydana gelebilir. Bu alışverişlerde, izlemeler daha önce tasarlandıkları gibi yeni istek/yanıt etkinliklerine dağıtılır.<br />2.  Bir RST/RSTR Exchange 'in burada bulunduğu güvenli oturum oluşturma (SCT). Bu, daha önce açıklandığı gibi aynı çevresel etkinliklere sahiptir.|-Exchange izlemeleri<br />-Güvenli kanal oluşturuldu<br />-Share gizli dizileri alındı.|  
  
> [!NOTE]
> Karma güvenlik modunda, anlaşma kimlik doğrulaması ikili değişimlerle yapılır, ancak ileti değişimi 'nde SCT oluşur. Saf Aktarım modunda, anlaşma yalnızca ek etkinlik olmadan aktarımda yapılır.  
  
## <a name="message-encryption-and-decryption"></a>İleti şifreleme ve şifre çözme  
 Aşağıdaki tabloda ileti şifreleme/şifre çözme işlemleri ve imza kimlik doğrulaması için etkinlikler ve izlemeler listelenmektedir.  
  
||Güvenli aktarım<br /><br /> (HTTPS, SSL) ve güvenli Ileti katmanı<br /><br /> (WSHTTP)|  
|-|---------------------------------------------------------------------------------|  
|İleti şifreleme/şifre çözme işleminin yanı sıra imza kimlik doğrulaması gerçekleştiğinde geçen süre|Alınan ileti|  
|Etkinlikler|İzlemeler, istemci ve sunucu üzerindeki ProcessAction etkinliğinde yayınlanır.|  
|Lerin|-sendSecurityHeader (Gönderen):<br />-İletiyi imzala<br />-İstek verilerini şifreleyin<br />-receiveSecurityHeader (alıcı):<br />-İmzayı Doğrula<br />-Yanıt verilerinin şifresini çözün<br />-Kimlik doğrulaması|  
  
> [!NOTE]
> Saf Aktarım modunda, ileti şifreleme/şifre çözme yalnızca ek etkinlik olmadan aktarımda olur.  
  
## <a name="authorization-and-verification"></a>Yetkilendirme ve doğrulama  
 Aşağıdaki tabloda yetkilendirme için etkinlikler ve izlemeler listelenmektedir.  
  
||Yetkilendirme gerçekleştiğinde geçen süre|Etkinlikler|Lerin|  
|-|-------------------------------------|----------------|------------|  
|Yerel (varsayılan)|İletinin şifresi sunucuda çözülür|İzlemeler, sunucudaki ProcessAction etkinliğinde dağıtılır.|Kullanıcı yetkilendirildi.|  
|Remote|İletinin şifresi sunucuda çözülür|İzlemeler, ProcessAction etkinliği tarafından çağrılan yeni bir etkinlikte yayınlanır.|Kullanıcı yetkilendirildi.|
