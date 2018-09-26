---
title: Eşler arası işbirliği
ms.date: 03/30/2017
ms.assetid: b6216d88-bccb-4a59-9f1c-9f751708e811
author: mcleblanc
ms.author: markl
ms.openlocfilehash: c81300d160e2ec175f61f286047fa92015345942
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47198156"
---
# <a name="peer-to-peer-collaboration"></a>Eşler arası işbirliği
Eşler arası ağ Internet kenarında birden fazla yalnızca istemci tabanlı bilgi işlem görevleri için mevcut görece güçlü bilgisayarlar (kişisel bilgisayarlar) kullanımını ' dir. Modern kişisel bilgisayar (PC) çok hızlı bir işlemci, çok sayıda bellek ve bunların hiçbiri tam e-posta ve Web'e göz atma gibi ortak bilgi işlem görevlerini gerçekleştirirken kullanılan büyük sabit disk var. Modern PC kolayca hem istemci hem de birçok türdeki uygulamayı (bir eş) sunucusu olarak işlev görebilir.  
  
-   Eşler arası işbirliği altyapısı, kişilerin Windows Vista ve sonraki platformları bana hizmet yakın yararlanan Microsoft Windows Eşler arası altyapısının basitleştirilmiş bir uygulamadır. Bir alt ağ içinde eş özellikli uygulamalar için en iyi şekilde kullanılan, kişilere yakın service bana çalışır, internet uç noktalar veya kişiler de hizmet olsa da. Bu ortak kişi iletişim uç noktaları, kullanılabilirlik ve varolup olmadığını belirlemek için Live Messenger ve canlı kullanan diğer uygulamalar tarafından kullanılan Yöneticisi kullanmaktadır.  
  
-  
  
## <a name="collaboration-applications"></a>İşbirliği uygulamaları  
 Tipik bir eşler arası işbirliği uygulaması, aşağıdaki adımlardan oluşur:  
  
-   Eş bir işbirliği oturumu barındırma isteyen bir eş kimliğini belirler.  
  
-   Bir oturum barındırmak için bir istek, bu şekilde, gönderilir ve işbirliği etkinlik yönetmek konak eş kabul eder.  
  
-   Konak bir oturuma (istek sahibine dahil) alt ağda bulunan kişileri davet eder.  
  
-   İşbirliği yapmak istediğiniz tüm eşleri kişi yöneticilerinin konağa ekleyebilir.  
  
-   Çoğu eşleri, kabul edilen veya reddedilen zamanında konak eş dön davet yanıt gönderir.  
  
-   Konak eşler arası işbirliği yapmak istediğiniz tüm eşleri abone olur.  
  
-   Eşlerden ilk işbirliği etkinliklerini gerçekleştirirken, konak eş için kişi kendi Yöneticisi uzak eşlerden ekleyebilir. Ayrıca tüm davet yanıtlarını belirlemek için kim, kimin reddetti ve kimin değil yanıtlamasından kabul etti işler.  Bunu verilmemesi olanlar için davetiye iptal edin veya başka bir etkinliği gerçekleştirin.  
  
-   Bu noktada, konak eş, davet edilen meslektaşlarınızla bir işbirliği oturumu başlatın veya ile işbirliği altyapınızın bir uygulamayı kaydetme.  P2p uygulamaları eşler arası işbirliği altyapısı kullanır ve <xref:System.Net.PeerToPeer.Collaboration> oyunlar, Bülten panosu, konferans ve diğer durum sunucusuz uygulamalar için iletişimleri için ad alanı.  
  
-  
  
## <a name="peer-to-peer-networking-security"></a>Eşler arası ağ güvenliği  
 Bir Active Directory etki alanında etki alanı denetleyicileri, Kerberos kullanarak kimlik doğrulama hizmetleri sağlar. Bir eş sunucusuz ortamda eşlere kendi kimlik doğrulaması sağlamanız gerekir. Ağ eşler için herhangi bir düğüm her eşin güvenilen kök deposunda bir kök sertifika gereksinimi kaldırma, bir CA olarak işlev görebilir. X.509 sertifikaları biçimlendirilmiş otomatik olarak imzalanan sertifikaları kullanarak kimlik doğrulaması sağlanır. Ortak anahtar/özel anahtar çifti ve özel anahtar ile imzalanmış bir sertifika oluşturur. her eş tarafından oluşturulan sertifikaları şunlardır. Otomatik olarak imzalanan sertifika kimlik doğrulaması ve eş varlık hakkında bilgi sağlamak için kullanılır. X.509 kimlik doğrulaması gibi izleme için geri güvenilir bir ortak anahtar sertifikaları zincirine eş ağ kimlik doğrulaması kullanır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Net.PeerToPeer.Collaboration>  
 [System.Net.PeerToPeer.Collaboration Ad Alanı Hakkında](../../../docs/framework/network-programming/about-the-system-net-peertopeer-collaboration-namespace.md)
