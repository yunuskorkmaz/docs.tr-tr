---
title: Güvenli Oturumlar
ms.date: 03/30/2017
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
ms.openlocfilehash: cb02adc7514e27175088e7664b12e45bc8ca5cd9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590091"
---
# <a name="secure-sessions"></a>Güvenli Oturumlar
Windows Communication Foundation (WCF) özelliği, iletilerin gönderildikleri sırada alınabileceğini garanti eden güvenilir oturumlardır. Bu bölümdeki konularda, güvenilir bir oturum oluştururken dikkate alınması gereken güvenlik etkileri ele alınmaktadır. Güvenilir oturumlar hakkında daha fazla bilgi için bkz. [oturumları kullanma](../using-sessions.md).  
  
> [!NOTE]
> Windows XP 'de kimliğe bürünme özelliği gerekli olduğunda, durum bilgisi olan güvenlik bağlamı belirteci (SCT) olmadan güvenli bir oturum kullanın. Durum bilgisi olan SCN 'ler kimliğe bürünme ile kullanıldığında bir oluşturulur <xref:System.InvalidOperationException> . Daha fazla bilgi için bkz. [desteklenmeyen senaryolar](unsupported-scenarios.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
|||  
|-|-|  
|[Güvenli İletişimler ve Güvenli Oturumlar](secure-conversations-and-secure-sessions.md)|Güvenli konuşmalar ve güvenli oturumlar eşanlamlı olarak anlamlıdır. Bu konuda, güvenli bir konuşmanın çalışma şekli ve düzenin ne zaman ve neden kullanıldığı açıklanmaktadır.|  
|[Nasıl yapılır: Güvenli Oturum Oluşturma](how-to-create-a-secure-session.md)|Güvenli bir oturum oluşturma hakkındaki temel bilgileri adım adım açıklar.|  
|[Nasıl yapılır: Güvenli Bir Oturum için Güvenlik Bağlamı Belirteci Oluşturma](how-to-create-a-security-context-token-for-a-secure-session.md)|İstemcilerle durum ve oturumları koruyacak bir Web grubu oluşturma adımlarında size yol gösterir.|  
|[Güvenli Oturumlar için Güvenlikli İlgili Önemli Noktalar](security-considerations-for-secure-sessions.md)|Güvenli oturumlar için özel konuları açıklar.|  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Oturumlar, Örnek Oluşturma ve Eşzamanlılık](sessions-instancing-and-concurrency.md)  
  
 [Hizmetleri Tasarlama ve Uygulama](../designing-and-implementing-services.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: İleti Yeniden Yürütme Algılamayı Etkinleştirme](how-to-enable-message-replay-detection.md)
- [Yeniden Yürütme Saldırıları](replay-attacks.md)
- [Nasıl yapılır: Oturum Gerektiren Bir Hizmet Oluşturma](how-to-create-a-service-that-requires-sessions.md)
