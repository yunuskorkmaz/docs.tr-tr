---
title: "Eş Adı Çözümleme Protokolü"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11940511-c124-4d91-ae31-d4ed6e81ee58
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 805f6f6ed7990b42065dfe7985a5d81844961897
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="peer-name-resolution-protocol"></a>Eş Adı Çözümleme Protokolü
Eşler arası ortamlarda, eş belirli ad çözümleme sistemleri birbirlerinin ağ konumlarını (adresler, protokoller ve bağlantı noktaları) gidermek için adlarını veya diğer türlerinden birini kullanın. Geçmişte, diğer etki alanı adı sistemi (DNS) içinde eksiklikleri yanı sıra doğası gereği geçici bir bağlantı tarafından eş adı çözümleme karmaşık.  
  
 Microsoft® Windows® Eşler arası ağ platformu ile Eş Adı Çözümleme Protokolü (PNRP), güvenli, ölçeklenebilir ve dinamik ad kaydı ve ilk Windows XP için geliştirilen ve içinde yükseltme adı çözümleme protokolü bu sorunu çözer Windows Vista™. PNRP uygulama geliştiricileri için heyecan verici yeni olanaklarını açma geleneksel ad çözümleme sistemlerinden çok farklı şekilde çalışır.  
  
 PNRP ile eş adlarını makine veya tek tek uygulamalar veya hizmetler makinede uygulanabilir. Eş adı çözümleme bir adresi, bağlantı noktası ve büyük olasılıkla bir genişletilmiş yükü içerir. Bu sistemin hata toleransı, hiçbir performans sorunlarını ve eski adreslerin hiçbir zaman döndürülecek ad çözünürlüğü yararları; protokol mobil kullanıcılar bulmak için mükemmel bir çözüm sağlayarak.  
  
 Güvenlik açısından, eş adları olabilir olarak güvenli (korumalı) yayımlanan ya da güvenli olmayan (korumasız). PNRP yanıltmaya karşı güvenli eş adlarını korumak için ortak anahtar şifrelemesini kullanır; bilgisayarlar ve hizmetler ile PNRP adlandırılabilir.  
  
-   Eş Adı Çözümleme Protokolü'nü aşağıdaki özellikleri gösterir:  
  
-   Dağıtılmış ve neredeyse tamamen sunucusuz. Sunucular, yalnızca önyükleme işlemi için gereklidir.  
  
-   Ad yayını üçüncü tarafların katılımı olmadan güvenli hale getirin. DNS ad yayını farklı olarak, anlık ve finansal maliyet gerektirmeden PNRP ad yayını.  
  
-   PNRP güncelleştirmeleri gerçek zamanlı, eski adreslerin çözümleme engeller.  
  
-   Adların PNRP aracılığıyla çözümlenmesi bilgisayarlar da ad çözümleme hizmetleri için sağlayarak genişletir.  
  
-  
  
## <a name="the-systemnetpeertopeer-namespace"></a>System.Net.PeerToPeer Namespace  
  
-   PNRP işlevi tarafından tanımlanan <xref:System.Net.PeerToPeer> ad alanı .NET Framework sürüm 3.5 içinde. Eş adları kullanılabilir bir PNRP hizmeti ile kaydetmek ve çözümlemek için kullanılan türleri kümesi sağlar.  
  
-  
  
-   (PNRP ve özel eş çözücüler oluşturulabilir ve başlatılan türlerini kullanarak sağlanan <xref:System.ServiceModel.PeerResolvers> ad.)  
  
-  
  
-   Kullanılabilir bir PNRP hizmetiyle adları kaydetmek ve çözümlemek için kullanılan temel türleri aşağıdaki gibidir:  
  
-  
  
-   <xref:System.Net.PeerToPeer.Cloud>: Kapsamı dahil olmak üzere bir kullanılabilir PNRP bulut açıklayan bilgileri tanımlar.  
  
-   <xref:System.Net.PeerToPeer.PeerName>: Kaydetmek ve daha sonra bir eş Bulutu içindeki çözümlemek için kullanılan bir eş adını tanımlar.  
  
-   <xref:System.Net.PeerToPeer.PeerNameRecord>: PNRP bulutta eş kurulabildiğinden ağ uç noktalarını içeren bir eş için kayıt bilgilerini içeren kayıt tanımlar.  
  
-   <xref:System.Net.PeerToPeer.PeerNameRegistration>: Eş ad kaydı durdurmak ve başlatmak için yöntemleri de dahil olmak üzere eş adını, kayıt işlemini tanımlar.  
  
-   <xref:System.Net.PeerToPeer.PeerNameResolver>: Bir eş adı çözümleme için zaman uyumlu ve zaman uyumsuz yöntemleri de dahil olmak üzere kendi ağ uç çözümleme işlemi tanımlar.  
  
-  
  
-  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.PeerResolvers>  
 <xref:System.Net.PeerToPeer>  
 [Ağ programlama örnekleri](../../../docs/framework/network-programming/network-programming-samples.md)  
 [PeerToPeer teknoloji örnek](http://go.microsoft.com/fwlink/?LinkID=179571)
