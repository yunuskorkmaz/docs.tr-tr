---
title: Eş Adı Çözümleme Protokolü
ms.date: 03/30/2017
ms.assetid: 11940511-c124-4d91-ae31-d4ed6e81ee58
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 70c49198c0198610eaa5001971b7de7efd2951aa
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45518145"
---
# <a name="peer-name-resolution-protocol"></a>Eş Adı Çözümleme Protokolü
Eşler arası ortamlarında eşleri belirli ad çözümleme sistemleri birbirlerinin ağ konumlarını (adresleri, protokoller ve bağlantı noktaları) çözümlemek için adları veya türlerini kullanın. Geçmişte, diğer etki alanı adı sistemi (DNS) içinde eksiklikleri yanı sıra, doğası gereği geçici bir bağlantı tarafından eş adı çözümleme karmaşık.  
  
 Microsoft® Windows® Eşler arası ağ platformu ile Eş Adı Çözümleme Protokolü (PNRP), güvenli, ölçeklenebilir ve dinamik ad kayıt ve Windows XP için ilk kez geliştirilen ve sonra yükseltme adı çözümleme protokolü bu sorunu çözer. Windows Vista™. PNRP uygulama geliştiricileri için heyecan verici yeni olasılıklara açma geleneksel ad çözümlemesi sistemlerden çok farklı şekilde çalışır.  
  
 PNRP ile eş adları, makine veya tek tek uygulamalar veya hizmetler makinede uygulanabilir. Eş adı çözümleme bir adresi, bağlantı noktası ve büyük olasılıkla bir genişletilmiş yükü içerir. Bu sistemin hata toleransı, hiçbir performans sorunlarını ve eski adreslerin hiçbir zaman döndüreceği ad çözünürlüğü avantajına sahip olur; Protokolü, mobil kullanıcıların bulmak için mükemmel bir çözüm yapılıyor.  
  
 Güvenlik açısından, eş adları olabilir (korumalı) güvenli olarak yayımlanan veya güvenli olmayan (korumasız). PNRP güvenli eş adları yanıltmaya karşı korumak için ortak anahtar şifrelemesi kullanır; hem bilgisayarları hem de Hizmetleri ile PNRP adlandırılabilir.  
  
-   Eş Adı Çözümleme Protokolü'nü aşağıdaki özellikleri göstermektedir:  
  
-   Dağıtılmış ve neredeyse tamamen sunucusuz. Sunucular, yalnızca önyükleme işlemi için gereklidir.  
  
-   Ada yayın olmadan üçüncü taraflara katılımı güvenli hale getirin. DNS adı yayını, anlık ve finansal maliyeti PNRP adı yayını.  
  
-   PNRP güncelleştirmeleri gerçek zamanlı olarak çözümleme eski adresi engeller.  
  
-   PNRP aracılığıyla ad çözümlemesi, ad çözümleme hizmetleri için de izin vererek bilgisayarlar genişletir.  
  
-  
  
## <a name="the-systemnetpeertopeer-namespace"></a>System.Net.PeerToPeer Namespace  
  
-   PNRP işlevleri tarafından tanımlanan <xref:System.Net.PeerToPeer> ad alanı içinde .NET Framework sürüm 3.5. Bu, kullanılabilir bir PNRP Service eş adları kaydetmek ve çözümlemek için kullanılan türleri kümesi sağlar.  
  
-  
  
-   (PNRP ve özel eş çözücüler oluşturulabilir ve örneklenen türlerini kullanarak sağlanan içinde <xref:System.ServiceModel.PeerResolvers> ad.)  
  
-  
  
-   Adları kullanılabilir bir PNRP hizmetiyle kaydetmek ve çözümlemek için kullanılan temel türleri aşağıdaki gibidir:  
  
-  
  
-   <xref:System.Net.PeerToPeer.Cloud>: Kapsamı dahil olmak üzere bir kullanılabilir PNRP bulut açıklayan bilgileri tanımlar.  
  
-   <xref:System.Net.PeerToPeer.PeerName>: Kaydetmek ve sonradan Bulutu içinde bir eş çözümlemek için kullanılan bir eş adını tanımlar.  
  
-   <xref:System.Net.PeerToPeer.PeerNameRecord>: PNRP bulutta eş kurulabileceğinden ağ uç noktaları içeren bir eş için kayıt bilgileri içeriyor kayıt tanımlar.  
  
-   <xref:System.Net.PeerToPeer.PeerNameRegistration>: Kayıt işlemi için eş ad kaydı durdurmak ve başlatmak yöntemleri dahil olmak üzere bir eş adını tanımlar.  
  
-   <xref:System.Net.PeerToPeer.PeerNameResolver>: Çözümleme için zaman uyumlu ve zaman uyumsuz yöntemleri dahil olmak üzere kendi ağ uç noktası için eş adı çözümleme sürecini tanımlar.  
  
-  
  
-  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.PeerResolvers>  
 <xref:System.Net.PeerToPeer>  
 [Ağ Programlama Örnekleri](../../../docs/framework/network-programming/network-programming-samples.md)  
 [PeerToPeer teknolojisi örneği](https://go.microsoft.com/fwlink/?LinkID=179571)
