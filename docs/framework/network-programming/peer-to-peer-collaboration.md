---
title: Eşler arası işbirliği
ms.date: 03/30/2017
ms.assetid: b6216d88-bccb-4a59-9f1c-9f751708e811
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a933c81105399a9411fcb749a06e47bf769cf532
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="peer-to-peer-collaboration"></a>Eşler arası işbirliği
Eşler arası, birden fazla yalnızca istemci tabanlı bilgi işlem görevleri için Internet kenarında mevcut oldukça güçlü bilgisayarların (kişisel bilgisayarlar) kullanımını ağdır. Modern kişisel bilgisayar (PC) çok hızlı bir işlemciye, büyük bellek ve hangi hiçbiri tam e-posta ve Web'e gözatma gibi ortak bilgi işlem görevler gerçekleştirirken göstermesi büyük sabit disk vardır. Modern PC kolayca hem istemci hem de birçok türdeki uygulamayı (bir eş) sunucusu olarak çalışabilir.  
  
-   Eşler arası işbirliği altyapısı kişiler bana hizmet Windows Vista ve sonraki platformlar yakınlarında yararlanır Microsoft Windows Eşler arası altyapısı basitleştirilmiş bir uygulamasıdır. Bir alt ağ içindeki eş özellikli uygulamalar için en iyi şekilde kullanılan için kişiler yakın service bana faaliyet, Internet uç noktaları veya kişiler de hizmet rağmen. Ortak kişi kişi uç noktaları, kullanılabilirlik ve iletişim durumu belirlemek için Live Messenger ve canlı kullanan diğer uygulamalar tarafından kullanılan Yöneticisi içerir.  
  
-  
  
## <a name="collaboration-applications"></a>Birlikte çalışma uygulamaları  
 Tipik eşler arası işbirliği uygulama aşağıdaki adımlardan oluşur:  
  
-   Eş işbirliği oturumunu barındıran isteyen bir eş kimliğini belirler  
  
-   Bir oturum barındırmak için bir istek, şekilde, gönderilir ve işbirliği etkinlik yönetmek konak eş kabul eder.  
  
-   Konak bir oturuma (istek sahibinin dahil) alt ağda bulunan kişileri davet eder.  
  
-   İşbirliği yapmak istediğiniz tüm eşleri kişi yöneticilerinin konağa ekleyebilir.  
  
-   Çoğu eş davet yanıtları kabul ya da reddedilen zamanında konak eş için geri gönderir.  
  
-   Ana bilgisayar eşler arası işbirliği yapmak istediğiniz tüm eşleri abone olur.  
  
-   Eş ilk işbirliği etkinliklerini gerçekleştirirken, ana bilgisayar eş kendi Kişi Yöneticisi uzak eşlerden ekleyebilir. Bunu ayrıca belirlemek için tüm davet yanıtları, kimin reddetti ve kimlerin verilmemesi kabul işler.  Bunu verilmemesi olanlar için davet iptal edin veya başka bir etkinlikle gerçekleştirin.  
  
-   Bu noktada, ana bilgisayar eş tüm davet edilen kişilerle işbirliği oturumu başlatmak veya bir uygulamayı işbirliği altyapısı ile kaydedin.  P2p uygulamaları eşler arası işbirliği altyapısı kullanır ve <xref:System.Net.PeerToPeer.Collaboration> iletişimleri oyunlar, Bülten panosu, konferans ve diğer sunucusuz varlığı uygulamaları için koordine etmek için ad alanı.  
  
-  
  
## <a name="peer-to-peer-networking-security"></a>Eşler arası ağ güvenliği  
 Bir Active Directory etki alanında etki alanı denetleyicileri, Kerberos kullanarak kimlik doğrulama hizmetleri sağlar. Bir sunucusuz eş ortamında eşlerden kendi kimlik doğrulaması sağlamanız gerekir. Ağ eşler için herhangi bir düğümün bir kök sertifika gereksinimi her eşin güvenilir kök deposuna kaldırma, bir CA olarak çalışabilir. X.509 sertifikaları biçimlendirilmiş otomatik olarak imzalanan sertifikalar kullanarak kimlik doğrulaması sağlanır. Bunlar ortak anahtarı/özel anahtar çifti ve özel anahtarı ile imzalanmış bir sertifika oluşturur her eş tarafından oluşturulan sertifikalardır. Otomatik olarak imzalanan sertifika kimlik doğrulaması ve eş varlık hakkında bilgi sağlamak için kullanılır. X.509 kimlik doğrulaması gibi bir sertifika zinciri geri güvenilir bir ortak anahtar için izleme eş ağ kimlik doğrulaması kullanır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Net.PeerToPeer.Collaboration>  
 [System.Net.PeerToPeer.Collaboration Ad Alanı Hakkında](../../../docs/framework/network-programming/about-the-system-net-peertopeer-collaboration-namespace.md)
