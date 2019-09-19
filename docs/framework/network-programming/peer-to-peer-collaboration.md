---
title: Eşler Arası İş Birliği
ms.date: 03/30/2017
ms.assetid: b6216d88-bccb-4a59-9f1c-9f751708e811
ms.openlocfilehash: 7cf92f6bf3c269e584cb8b3cdcf910be5b89fd7e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047378"
---
# <a name="peer-to-peer-collaboration"></a>Eşler arası işbirliği

Eşler arası ağ, yalnızca istemci tabanlı bilgi işlem görevlerinin daha fazla olması için Internet 'in kenarında bulunan görece güçlü bilgisayarların (kişisel bilgisayarlar) kullanımından yararlanılır. Modern kişisel bilgisayar (PC) çok hızlı bir işlemciye, büyük belleğe ve e-posta ve Web 'e göz atma gibi yaygın bilgi işlem görevleri gerçekleştirirken tam olarak kullanılan büyük bir sabit diske sahiptir. Modern bılgısayar, birçok tür uygulama için kolayca istemci ve sunucu (eş) görevi görür.  
  
Eşler arası Işbirliği altyapısı, Windows Vista ve sonraki platformlarda hizmet Yakınımdaki kişilerden yararlanan Microsoft Windows Eşler arası altyapısı 'nın basitleştirilmiş bir uygulamasıdır. En iyi yöntem, hizmet Yakınımdaki Kişiler 'in çalıştığı bir alt ağ içinde, İnternet uç noktalarına veya kişilerine da hizmet verebilir. Canlı Messenger ve diğer canlı özellikli uygulamalar tarafından, iletişim uç noktalarını, kullanılabilirliği ve varlığı tespit etmek üzere kullanılan ortak Iletişim Yöneticisi 'Ni içerir.  
  
## <a name="collaboration-applications"></a>İşbirliği uygulamaları

 Tipik bir eşler arası işbirliği uygulaması aşağıdaki adımlardan oluşur:  
  
- Eş, işbirliği oturumunu barındırmak isteyen bir eşin kimliğini belirler  
  
- Bir oturumu barındırma isteği gönderilir, bir şekilde ve konak eşi işbirliği etkinliğini yönetmeyi kabul eder.  
  
- Ana bilgisayar, alt ağdaki (istek sahibi dahil) kişileri bir oturuma davet eder.  
  
- İşbirliği yapmak isteyen tüm Peers ana bilgisayar, iletişim yöneticilerine eklenebilir.  
  
- Çoğu eş, kabul edilen veya reddedilen davet yanıtlarını, ana bilgisayar eşine zamanında geri gönderilir.  
  
- İşbirliği yapmak isteyen tüm Peers konak eşine abone olur.  
  
- Eşler ilk işbirliği etkinliklerini gerçekleştirirken, konak eşi uzak eşleri ilgili kişi yöneticisine ekleyebilir. Ayrıca kimlerin kabul edildiğini, kimin reddettiğini ve kimin yanıtlanmadığını belirleme için tüm davet yanıtlarını işler.  Yanıtlamadığınıza veya başka bir etkinliğe yönelik davetleri iptal edebilir.  
  
- Bu noktada, konak eşi tüm davet eden eşleri ile bir işbirliği oturumu başlatabilir veya bir uygulamayı işbirliği altyapısına kaydedebilir.  P2P uygulamaları, Oyunlar, bülten panoları, konferans ve diğer sunucusuz <xref:System.Net.PeerToPeer.Collaboration> varlık uygulamalarına yönelik iletişimleri koordine etmek için eşler arası işbirliği altyapısını ve ad alanını kullanır.  
  
## <a name="peer-to-peer-networking-security"></a>Eşler arası ağ güvenliği  

 Active Directory etki alanında, etki alanı denetleyicileri Kerberos kullanarak kimlik doğrulama hizmetleri sağlar. Sunucusuz bir eş ortamında, eşler kendi kimlik doğrulamasını sağlamalıdır. Eşler arası ağ için, herhangi bir düğüm CA işlevi görebilir ve her eşin güvenilen kök deposundaki bir kök sertifika gereksinimini ortadan kaldırır. Kimlik doğrulaması, X. 509.440 sertifikaları olarak biçimlendirilen, otomatik olarak imzalanan sertifikalar kullanılarak sağlanır. Bunlar, ortak anahtar/özel anahtar çiftini ve özel anahtar kullanılarak imzalanmış sertifikayı üreten her bir eş tarafından oluşturulan sertifikalardır. Otomatik olarak imzalanan sertifika, kimlik doğrulaması için kullanılır ve eş varlık hakkında bilgi sağlar. X. 509.440 kimlik doğrulaması gibi, Eş ağ kimlik doğrulaması da güvenilen bir ortak anahtara geri doğru bir sertifika zincirini izleme işlemi kullanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.PeerToPeer.Collaboration>
- [System.Net.PeerToPeer.Collaboration Ad Alanı Hakkında](about-the-system-net-peertopeer-collaboration-namespace.md)
