---
title: Eşler Arası İş Birliği
ms.date: 03/30/2017
ms.assetid: b6216d88-bccb-4a59-9f1c-9f751708e811
ms.openlocfilehash: 7cf92f6bf3c269e584cb8b3cdcf910be5b89fd7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047378"
---
# <a name="peer-to-peer-collaboration"></a>Eşler arası işbirliği

Eşler arası ağ, Internet'in kenarında bulunan nispeten güçlü bilgisayarların (kişisel bilgisayarlar) istemci tabanlı bilgi işlem görevlerinden daha fazlası için kullanılmasıdır. Modern kişisel bilgisayar (PC) çok hızlı bir işlemci, geniş bellek ve büyük bir sabit disk, hiçbiri tam olarak e-posta ve Web tarama gibi ortak bilgi işlem görevleri gerçekleştirirken kullanılmaktadır vardır. Modern BILGISAYAR kolayca birçok uygulama türleri için hem istemci hem de sunucu (eş) olarak hareket edebilir.  
  
Eşler Arası İşbirliği Altyapısı, Windows Vista'da ve sonraki platformlarda Bana Yakın Kişiler hizmetinden yararlanan Microsoft Windows Eşler Arası Altyapı'nın basitleştirilmiş bir uygulamasıdır. İnternet uç noktalarına veya kişilere de hizmet verebilse de, en iyi, Yakınımdaki Kişiler hizmetinin çalıştığı bir alt ağ daki eş özellikli uygulamalar için kullanılır. İletişim uç noktalarını, kullanılabilirliği ve mevcudiyeti belirlemek için Live Messenger ve diğer Live-aware uygulamaları tarafından kullanılan ortak İletişim Yöneticisi'ni içerir.  
  
## <a name="collaboration-applications"></a>İşbirliği uygulamaları

 Tipik bir eşler arası işbirliği uygulaması aşağıdaki adımlardan oluşur:  
  
- Eş, bir işbirliği oturumuna ev sahipliği yapmak isteyen bir eşin kimliğini belirler  
  
- Bir oturumbarındırma isteği bir şekilde gönderilir ve ev sahibi eş işbirliği etkinliğini yönetmeyi kabul eder.  
  
- Ev sahibi, alt ağdaki (istekte bulundu) kişileri bir oturuma davet eder.  
  
- İşbirliği yapmak isteyen tüm eşler, ana bilgisayarı iletişim yöneticilerine ekleyebilir.  
  
- Çoğu eş, kabul edilmiş veya reddedilmiş olsun, zamanında ev sahibi eşe davet yanıtları gönderir.  
  
- İşbirliği yapmak isteyen tüm eşler ana bilgisayar eşinabone olur.  
  
- Eşler ilk işbirliği etkinliklerini gerçekleştirirken, ana bilgisayar eş kişi yöneticisine uzak eşler ekleyebilir. Ayrıca, kimin kabul ettiğini, kimin reddettiğini ve kimin yanıtlamadığını belirlemek için tüm davet yanıtlarını işler.  Yanıtlamayanların davetlerini iptal edebilir veya başka bir etkinlik gerçekleştirebilir.  
  
- Bu noktada, ana bilgisayar eş, davet edilen tüm eşlerle bir işbirliği oturumu başlatabilir veya bir uygulamayı işbirliği altyapısıyla kaydedebilir.  P2P uygulamaları, oyunlar, bülten panoları, konferans <xref:System.Net.PeerToPeer.Collaboration> ve diğer sunucusuz durum uygulamaları için iletişimi koordine etmek için Eşler Arası İşbirliği Altyapısını ve ad alanını kullanır.  
  
## <a name="peer-to-peer-networking-security"></a>Eşler arası ağ güvenliği  

 Etkin Dizin etki alanında, etki alanı denetleyicileri Kerberos kullanarak kimlik doğrulama hizmetleri sağlar. Sunucusuz bir eş ortamında, eşler kendi kimlik doğrulamasını sağlamalıdır. Eşler Arası Ağ için, herhangi bir düğüm, her eşin güvenilen kök deposundaki kök sertifikası gereksinimini kaldırarak CA olarak hareket edebilir. Kimlik doğrulama, X.509 sertifikaları olarak biçimlendirilmiş kendi imzalı sertifikalar kullanılarak sağlanır. Bunlar, ortak anahtar/özel anahtar çiftini ve özel anahtar kullanılarak imzalanan sertifikayı oluşturan her eş tarafından oluşturulan sertifikalardır. Kendi imzalı sertifika kimlik doğrulama ve eş varlık hakkında bilgi sağlamak için kullanılır. X.509 kimlik doğrulaması gibi, eş ağ kimlik doğrulaması da güvenilen ortak bir anahtara geri dönen bir sertifika zincirine dayanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.PeerToPeer.Collaboration>
- [System.Net.PeerToPeer.Collaboration Ad Alanı Hakkında](about-the-system-net-peertopeer-collaboration-namespace.md)
