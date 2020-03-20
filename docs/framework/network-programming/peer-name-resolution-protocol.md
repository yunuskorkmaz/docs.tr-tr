---
title: Eş Adı Çözümleme Protokolü
ms.date: 03/30/2017
ms.assetid: 11940511-c124-4d91-ae31-d4ed6e81ee58
ms.openlocfilehash: c8b7b2190349323bf212d816a77f5f7810f6ca2c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74428216"
---
# <a name="peer-name-resolution-protocol"></a>Eş Adı Çözümleme Protokolü
Eşler arası ortamlarda, eşler birbirlerinin ağ konumlarını (adresler, protokoller ve bağlantı noktaları) adlardan veya diğer tanımlayıcıtürlerinden çözmek için belirli ad çözümleme sistemlerini kullanır. Geçmişte, eş adı çözümlemesi doğal olarak geçici bağlantı nın yanı sıra Etki Alanı Adı Sistemi (DNS) içindeki diğer eksiklikler tarafından karmaşık hale gelmiştir.  
  
 Microsoft® Windows® Eşler Arası Ağ platformu, bu sorunu önce Windows XP için geliştirilen ve daha sonra yükseltilmiş güvenli, ölçeklenebilir ve dinamik bir ad kaydı ve ad çözümleme protokolü olan Eş Adı Çözümleme Protokolü (PNRP) ile çözer Windows Vista™. PNRP, geleneksel ad çözümleme sistemlerinden çok farklı çalışır ve uygulama geliştiricileri için heyecan verici yeni olanaklar sunar.  
  
 PNRP ile, eş adları makineye veya makinedeki tek tek uygulamalara veya hizmetlere uygulanabilir. Eş adı çözümlemesi bir adres, bağlantı noktası ve büyük olasılıkla genişletilmiş bir yük içerir. Bu sistemin yararları arasında hata toleransı, darboğaz yok ve eski adresleri asla döndürmeyecek ad çözünürlükleri yer almaktadır; protokolü mobil kullanıcıların yerini bulmak için mükemmel bir çözüm haline getirir.  
  
 Güvenlik açısından, eş adları güvenli (korumalı) veya güvenli olmayan (korumasız) olarak yayımlanabilir. PNRP, güvenli eş adlarını sızdırmaya karşı korumak için ortak anahtar şifrelemesini kullanır; hem bilgisayarlar hem de hizmetler PNRP ile adlandırılabilir.  
  
Eş Adı Çözümleme Protokolü aşağıdaki özellikleri gösterir:  
  
- Dağıtılmış ve neredeyse tamamen sunucusuz. Sunucular yalnızca önyükleme işlemi için gereklidir.  
  
- Üçüncü şahısların katılımı olmadan güvenli ad yayını. DNS ad yayınının aksine, PNRP ad yayını anlıktır ve finansal maliyeti yoktur.  
  
- PNRP, eski adreslerin çözümünü engelleyen gerçek zamanlı olarak güncellenir.  
  
- PNRP üzerinden adların çözünürlüğü, hizmetler için ad çözümlemesine de izin vererek bilgisayarların ötesine uzanır.  
  
## <a name="the-systemnetpeertopeer-namespace"></a>System.Net.PeerToPeer ad alanı  
  
- PNRP işlevselliği,.NET Framework sürüm 3.5'teki <xref:System.Net.PeerToPeer> ad alanı tarafından tanımlanır. Kullanılabilir bir PNRP hizmetiyle eş adlarını kaydetmek ve çözmek için kullanılabilecek bir tür kümesi sağlar.  
  
- (PNRP ve özel eş çözümleyicileri <xref:System.ServiceModel.PeerResolvers> ad alanında sağlanan türler kullanılarak oluşturulabilir ve anında oluşturulabilir.)  
  
- Kullanılabilir bir PNRP hizmetiyle adları kaydetmek ve çözmek için kullanılan temel türler şunlardır:  
  
- <xref:System.Net.PeerToPeer.Cloud>: Kapsamı da dahil olmak üzere kullanılabilir bir PNRP bulutunu açıklayan bilgileri tanımlar.  
  
- <xref:System.Net.PeerToPeer.PeerName>: Bir eşin bulut içinde kaydolması ve daha sonra çözümlemesine yardımcı olmak için kullanılabilecek bir eş adı tanımlar.  
  
- <xref:System.Net.PeerToPeer.PeerNameRecord>: PNRP bulutundaki, eşin bağlantı kurulabileceği ağ uç noktalarını içeren bir eşin kayıt bilgilerini içeren kaydı tanımlar.  
  
- <xref:System.Net.PeerToPeer.PeerNameRegistration>: Eş adı kaydını başlatma ve durdurma yöntemleri de dahil olmak üzere, eş adı için kayıt işlemini tanımlar.  
  
- <xref:System.Net.PeerToPeer.PeerNameResolver>: Eş adı, çözünürlük için hem senkron hem de eşzamanlı yöntemler de dahil olmak üzere, ağ bitiş noktasına(lar) çözme işlemini tanımlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.PeerResolvers>
- <xref:System.Net.PeerToPeer>
- [Ağ Programlama Örnekleri](network-programming-samples.md)

<!-- to-do: review sample links
- [PeerToPeer Technology Sample](https://go.microsoft.com/fwlink/?LinkID=179571)
-->
