---
title: "İleti Güvenliğinde Etkinlik İzleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68862534-3b2e-4270-b097-8121b12a2c97
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: db9b05217bbbf91bfc3cd315801b4e511f82d04c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="activity-tracing-in-message-security"></a>İleti Güvenliğinde Etkinlik İzleme
Bu konu, aşağıdaki üç aşamaya olur güvenlik işleme için etkinlik izleme açıklar.  
  
-   Anlaşma/SCT exchange. Bu, daha sonra (aracılığıyla ikili veri değişimi) taşıma veya ileti katman (aracılığıyla SOAP ileti alışverişlerinde) olabilir.  
  
-   İleti şifreleme/şifre çözme, imza doğrulaması ve kimlik doğrulaması ile. İzlemeler ortam etkinlik, genellikle "işlem eylem." görüntülenir  
  
-   Yetkilendirme ve doğrulama. Bu, yerel olarak veya ne zaman uç noktalar arasında iletişim meydana gelebilir.  
  
## <a name="negotiationsct-exchange"></a>Anlaşma/SCT exchange  
 Anlaşma/SCT exchange aşamasında, istemcide iki etkinlik türleri oluşturulur: "Ayarlamak yukarı güvenli oturum" ve "Güvenli oturumu kapat." "Güvenli oturum ayarlayın", "Güvenli Oturumu Kapat" Cancel iletisi izlemelerini içerir ancak RSTR/RST/SCT ileti alışverişlerinde izlemelerini kapsar.  
  
 Sunucuda, her istek/yanıt RST/RSTR/SCT için kendi etkinliğinde görüntülenir. Varsa `propagateActivity` = `true` hem sunucu hem de istemci, sunucunun etkinliklerde aynı Kimliğe sahip ve birlikte "Kurulum güvenli hizmet izleme görüntüleyicisini görüntülendiğinde oturum" görünür.  
  
 Bu etkinlik izleme modeli kullanıcı adı/parola kimlik doğrulaması, sertifika kimlik doğrulaması ve NTLM kimlik doğrulaması için geçerli değil.  
  
 Etkinlikleri ve anlaşma ve SCT exchange izlemelerini aşağıdaki tabloda listelenmektedir.  
  
||Anlaşma/SCT exchange durumda süre|Etkinlikler|İzlemeler|  
|-|-------------------------------------------------|----------------|------------|  
|Güvenli aktarım<br /><br /> (HTTPS, SSL)|İlk iletisi aldı.|İzlemeler ortam etkinliğin gösterilen.|-Exchange izler<br />-Oluşturulan güvenli kanal<br />-Alınan gizlilikler paylaşın.|  
|Güvenli ileti katmanı<br /><br /> (WSHTTP)|İlk iletisi aldı.|İstemci üzerinde:<br /><br /> -"Kurulum güvenli oturum" söz konusu ilk iletinin "işlem eylem" dışında her istek/yanıt RSTR/RST/SCT için.<br />-"Kapat güvenli oturum" için "Kapat Proxy etkinliği." dışında iptal exchange Bu etkinlik, güvenli oturum kapatıldığında bağlı olarak bazı diğer ortam etkinliği dışında ortaya çıkabilir.<br /><br /> Sunucuda:<br /><br /> -Bir "İşlem eylem" etkinlik her istek/yanıt SCT/RST/iptal için sunucu üzerinde. Varsa `propagateActivity` = `true`RSTR/RST/SCT etkinlikler "Ayarlamak yukarı güvenlik oturumla" birleştirilir ve iptal istemciden "Kapat" etkinliği ile birleştirilir.<br /><br /> "Ayarla yukarı güvenli oturum için" iki aşama vardır:<br /><br /> 1.  Kimlik doğrulama anlaşma. Bu istemci uygun kimlik bilgilerine zaten sahipse, isteğe bağlıdır. Bu aşama, güvenli aktarım aracılığıyla ya da ileti alışverişlerinde aracılığıyla yapılabilir. İkinci durumda, 1 veya 2 RST/RSTR alışverişleri oluşabilir. Bu değişimler için daha önce tasarlanan yeni istek/yanıt aktivitelerde izlemeleri gösterilen.<br />2.  Bir RST/RSTR exchange burada olur oturum kurma (SCT) güvenli hale getirin. Bu, daha önce açıklandığı gibi aynı ortam etkinlikler içeriyor.|-Exchange izler<br />-Oluşturulan güvenli kanal<br />-Alınan gizlilikler paylaşın.|  
  
> [!NOTE]
>  Karışık güvenlik modunda ikili alışverişlerine Anlaşma kimlik doğrulaması gerçekleşir, ancak ileti değiş tokuşunu SCT olur. Saf aktarım modunda anlaşma yalnızca hiçbir ek etkinlikler ile aktarma içinde gerçekleşir.  
  
## <a name="message-encryption-and-decryption"></a>İleti şifreleme ve şifre çözme  
 Aşağıdaki tabloda imzası kimlik doğrulaması yanı sıra ileti şifreleme/şifre çözme için izlemeleri ve etkinlikleri listeler.  
  
||Güvenli aktarım<br /><br /> (HTTPS, SSL) ve güvenli ileti katmanı<br /><br /> (WSHTTP)|  
|-|---------------------------------------------------------------------------------|  
|Saati şifreleme/şifre çözme, yanı sıra imzası kimlik doğrulaması gerçekleşir iletisi|İleti alındı|  
|Etkinlikler|İstemci ve sunucu ProcessAction etkinliğinde izlemeleri gösterilen.|  
|İzlemeler|-sendSecurityHeader (gönderen):<br />-Oturum iletisi<br />-İstek verileri şifreleme<br />-receiveSecurityHeader (alıcı):<br />-İmzası doğrulayın<br />-Yanıt verilerin şifresini<br />-Kimlik doğrulama|  
  
> [!NOTE]
>  Saf aktarım modunda ileti şifreleme/şifre çözme yalnızca hiçbir ek etkinlikler ile aktarma içinde gerçekleşir.  
  
## <a name="authorization-and-verification"></a>Yetkilendirme ve doğrulama  
 Aşağıdaki tabloda etkinlikler ve yetkilendirme için izlemeleri listeler.  
  
||Yetkilendirme durumda süre|Etkinlikler|İzlemeler|  
|-|-------------------------------------|----------------|------------|  
|Yerel (varsayılan)|İletinin sonra sunucuda şifresi çözülür|Sunucuda ProcessAction etkinliğinde izlemeleri gösterilen.|Yetkili kullanıcı.|  
|Remote|İletinin sonra sunucuda şifresi çözülür|İzlemeler ProcessAction etkinlik tarafından çağrılan yeni bir etkinlik olarak gösterilen.|Yetkili kullanıcı.|
