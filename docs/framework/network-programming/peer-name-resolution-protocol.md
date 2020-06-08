---
title: Eş Adı Çözümleme Protokolü
description: Eş adı çözümleme Protokolü (PNRP), güvenli, ölçeklenebilir ve dinamik ad kaydı ve ad çözümleme protokolü hakkında bilgi edinin.
ms.date: 03/30/2017
ms.assetid: 11940511-c124-4d91-ae31-d4ed6e81ee58
ms.openlocfilehash: 72eb63c2c90f398c515d77cd2b2d693237e533a5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502229"
---
# <a name="peer-name-resolution-protocol"></a>Eş Adı Çözümleme Protokolü
Eşler arası ortamlarda, eşler, her birinin ağ konumlarını (adresler, protokoller ve bağlantı noktaları) adlarla veya diğer tanımlayıcı türlerinden çözümlemek için belirli ad çözümleme sistemlerini kullanır. Geçmişte, eş adı çözümlemesi, etki alanı adı sistemi (DNS) içindeki diğer eksikler tarafından da doğal olarak geçici bağlantı tarafından karmaşıktır.  
  
 Microsoft® Windows® Eşler arası ağ platformu, ilk olarak Windows XP için geliştirilmiş ve ardından Windows Vista™ ' de yükseltilen eş adı çözümleme Protokolü (PNRP), güvenli, ölçeklenebilir ve dinamik bir ad kaydı ve ad çözümleme protokolü ile bu sorunu çözer. PNRP geleneksel ad çözümleme sistemlerinden çok farklı çalışır ve uygulama geliştiricileri için heyecan verici yeni olanaklar sunar.  
  
 PNRP ile, eş adları makineye veya makinedeki ayrı uygulamalara veya hizmetlere uygulanabilir. Eş adı çözümlemesi bir adres, bağlantı noktası ve büyük olasılıkla genişletilmiş bir yük içerir. Bu sistemin avantajları arasında hata toleransı, performans sorunu olmaması ve hiçbir şekilde eski adresleri döndürmeyecek ad çözümlemeleri dahildir; Protokolü mobil kullanıcıları bulmaya yönelik harika bir çözüm haline getirme.  
  
 Güvenlik açısından, eş adları güvenli (korumalı) veya güvenli olmayan (korumasız) olarak yayımlanabilir. PNRP güvenli eş adlarını yanıltmaya karşı korumak için ortak anahtar şifrelemeyi kullanır; Her iki bilgisayar ve hizmet da PNRP ile adlandırılabilir.  
  
Eş adı çözümleme protokolü aşağıdaki özellikleri gösterir:  
  
- Dağıtılmış ve neredeyse tamamen sunucusuz. Sunucular yalnızca önyükleme işlemi için gereklidir.  
  
- Üçüncü tarafların katılımı olmadan güvenli ad yayını. DNS ad yayınının aksine, PNRP ad yayını anında ve finans maliyeti olmadan olur.  
  
- PNRP, eski adreslerin çözümlenmesini önleyen gerçek zamanlı olarak güncelleştirilir.  
  
- PNRP aracılığıyla adların çözümlenmesi bilgisayarların ötesinde de hizmetler için ad çözümlemesine izin verir.  
  
## <a name="the-systemnetpeertopeer-namespace"></a>System .net. PeerToPeer ad alanı  
  
- PNRP işlevselliği <xref:System.Net.PeerToPeer> .NET Framework sürüm 3,5 içinde ad alanı tarafından tanımlanır. Kullanılabilir bir PNRP hizmeti ile eş adlarını kaydetmek ve çözümlemek için kullanılabilecek bir tür kümesi sağlar.  
  
- (PNRP ve özel eşdüzey çözümleyiciler ad alanında belirtilen türler kullanılarak oluşturulabilir ve oluşturulabilir <xref:System.ServiceModel.PeerResolvers> .)  
  
- Kullanılabilir bir PNRP hizmeti ile adları kaydettirmek ve çözümlemek için kullanılan temel türler aşağıdaki gibidir:  
  
- <xref:System.Net.PeerToPeer.Cloud>: Kapsamı dahil olmak üzere kullanılabilir bir PNRP bulutunu açıklayan bilgileri tanımlar.  
  
- <xref:System.Net.PeerToPeer.PeerName>: Bir bulut içindeki bir eşi kaydettirmek ve daha sonra çözümlemek için kullanılabilen bir eş adı tanımlar.  
  
- <xref:System.Net.PeerToPeer.PeerNameRecord>: Eşin iletişim kurulabileceği ağ uç noktalarını içeren bir eş için kayıt bilgilerini içeren, PNRP bulutundaki kaydı tanımlar.  
  
- <xref:System.Net.PeerToPeer.PeerNameRegistration>: Eş adı kaydını başlatma ve durdurma yöntemleri de dahil olmak üzere bir eş adı için kayıt işlemini tanımlar.  
  
- <xref:System.Net.PeerToPeer.PeerNameResolver>: Çözüm için hem zaman uyumlu hem de zaman uyumsuz yöntemler de dahil olmak üzere, eş adı ağ uç noktaları için çözümleme işlemini tanımlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.PeerResolvers>
- <xref:System.Net.PeerToPeer>
- [Ağ Programlama Örnekleri](network-programming-samples.md)

<!-- to-do: review sample links
- [PeerToPeer Technology Sample](https://go.microsoft.com/fwlink/?LinkID=179571)
-->
