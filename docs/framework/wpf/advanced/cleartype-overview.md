---
title: ClearType Genel Bakışı
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], ClearType technology
- ClearType [WPF], technology
ms.assetid: 7e2392e0-75dc-463d-a716-908772782431
ms.openlocfilehash: 11019d564e7e658b745aec4254ad9a0c582b8416
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964921"
---
# <a name="cleartype-overview"></a>ClearType Genel Bakışı
Bu konu, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]Içinde bulunan Microsoft ClearType teknolojisine genel bir bakış sağlar.  

<a name="overview"></a>   
## <a name="technology-overview"></a>Teknolojiye genel bakış  
 ClearType, dizüstü ekranları, Pocket PC [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] ekranları ve düz panel izleyicileri gibi mevcut LCD 'lerde (sıvı kristal ekranlar) metnin okunabilirliğini artıran, tarafından geliştirilen bir yazılım teknolojisidir.  ClearType, bir LCD ekranın her pikseline tek dikey renk Stripe öğelerine erişerek işe yarar. ClearType 'Tan önce, bir bilgisayarın görüntüleyeceği en düşük ayrıntı düzeyi tek bir pikseldir, ancak bir LCD monitörde çalışan ClearType ile, artık metnin özelliklerini piksel genişliği kadar küçük bir sayı olarak görüntüleriz. Ek çözüm, metin görüntüleme içindeki küçük ayrıntıların keskinliğini artırarak uzun süreleri okumayı çok daha kolay hale getirir.  
  
 ' De [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] kullanılabilen ClearType, Microsoft Windows grafik cihaz arabirimi (GDI) sürümünde bulunan sürüm üzerinde çeşitli geliştirmeler içeren en son ClearType sürümüdür.  
  
<a name="sub-pixel_positioning"></a>   
## <a name="sub-pixel-positioning"></a>Alt piksel konumlandırma  
 ClearType 'ın önceki sürümünde önemli bir geliştirme, alt piksel konumlandırmayı kullanmaktır. GDI 'da bulunan ClearType uygulamasının aksine, içinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] bulunan ClearType karakterlerin yalnızca pikselin başlangıç sınırını değil, piksel içinde başlatılmasına izin verir. Glifleri konumlandırmada bu ek çözünürlük nedeniyle, gliflerin aralığı ve oranları daha kesin ve tutarlıdır.  
  
 Aşağıdaki iki örnekte, alt piksel konumlandırması kullanıldığında karakterlerin herhangi bir alt piksel sınırında nasıl başlayabileceğiniz gösterilmektedir. Sol taraftaki örnek, ClearType işleyicisinin alt piksel konumlandırmayı kullanmayan önceki bir sürümü kullanılarak işlenir. Sağdaki örnek, alt piksel konumlandırma kullanılarak ClearType işleyicisinin yeni sürümü kullanılarak işlenir. Her biri farklı bir alt piksel üzerinde başladığı için sağ görüntüdeki her bir **e** ve **l** 'nin nasıl biraz farklı şekilde işlendiğine göz önünde bulundurun. Metinde normal boyutunda metin görüntülenirken bu fark, glif resminin yüksek karşıtlığı nedeniyle dikkat çekici değildir. Bu yalnızca ClearType 'a eklenen gelişmiş renk filtrelemesi nedeniyle mümkündür.  
  
 ![ClearType 'ın iki sürümüyle birlikte görünen metin](./media/wcpsdk-mmgraphics-text-cleartype-overview-01.png "wcpsdk_mmgraphics_text_cleartype_overview_01")  
ClearType 'ın önceki ve sonraki sürümleriyle birlikte görünen metin  
  
 Aşağıdaki iki örnek, önceki ClearType işleyiciden gelen çıktıyı ClearType işleyicisinin yeni sürümüyle karşılaştırır. Sağ tarafta gösterilen alt piksel konumlandırma, özellikle bir alt piksel ve tam piksel arasındaki farkın önemli bir karakter genişliği oranını temsil eden küçük boyutlarda, ekranda tür boşluklarını büyük ölçüde geliştirir. Harfler arasındaki boşluğun ikinci görüntüde bile daha fazla olduğunu unutmayın. Alt piksel konumlandırmanın bir metin ekranının genel görünümüne toplam avantajı büyük ölçüde artar ve ClearType teknolojisindeki önemli bir evrimi temsil eder.  
  
 ![ClearType 'ın önceki sürümüyle birlikte görünen metin](./media/wcpsdk-mmgraphics-text-cleartype-overview-02.png "wcpsdk_mmgraphics_text_cleartype_overview_02")  
ClearType 'ın önceki ve sonraki sürümlerini içeren metin  
  
<a name="y-direction_antialiasing"></a>   
## <a name="y-direction-antialiasing"></a>Y yönü düzgünleştirme  
 ' De [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ClearType 'ın başka bir geliştirmesi, y yönü kenar yumuşatmadır. Y yönü kenar yumuşatma olmadan GDI 'daki ClearType, y ekseni üzerinde değil, x ekseninde daha iyi çözüm sağlar. Yüzeysel eğrilerin üst ve botları üzerinde, pürüzlü kenarlar okunabilirliği kaldırır.  
  
 Aşağıdaki örnek, y yönü düzgünleştirmenin etkilerini gösterir. Bu durumda, harfin üst ve altındaki pürüzlü kenarlar görünür.  
  
 ![Yüzeysel eğrilerde pürüzlü kenarları olan metin](./media/wcpsdk-mmgraphics-text-cleartype-overview-03.png "wcpsdk_mmgraphics_text_cleartype_overview_03")  
Yüzeysel eğrilerde pürüzlü kenarları olan metin  
  
 İçindeki [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ClearType, pürüzlü kenarları düzgünleştirmek için y yönü düzeyinde düzgünleştirme sağlar. Bu, ideogramların neredeyse eşit miktarda yatay ve dikey yüzeysel eğrilerinin bulunduğu Doğu Asya dillerinin okunabilirliğini geliştirmek için özellikle önemlidir.  
  
 Aşağıdaki örnek, y yönü düzgünleştirmenin etkisini gösterir. Bu durumda, harfin üst ve alt kısmı düz bir eğri gösterir.  
  
 ![ClearType y&#45;yönü düzgünleştirmesini&#45;içeren metin](./media/wcpsdk-mmgraphics-text-cleartype-overview-04.png "wcpsdk_mmgraphics_text_cleartype_overview_04")  
ClearType y yönünde düzgünleştirme içeren metin  
  
<a name="hardware_acceleration"></a>   
## <a name="hardware-acceleration"></a>Donanım hızlandırma  
 İçindeki [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ClearType, daha iyi performans sağlamak ve CPU yükü ve sistem belleği gereksinimlerini azaltmak için donanım hızlandırmasının avantajlarından yararlanabilir. Bir grafik kartının piksel gölgelendiricilerini ve video belleğini kullanarak, özellikle animasyon kullanıldığında ClearType daha hızlı metin işleme sağlar.  
  
 İçindeki [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ClearType, sistem genelinde ClearType ayarlarını değiştirmez. Windows 'da ClearType devre dışı [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] bırakıldığında gri tonlama moduna düzgünleştirme ayarlanır. Ayrıca, içindeki [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ClearType, [ClearType TV tarayıcısı poweroyunno](https://www.microsoft.com/typography/ClearTypePowerToy.mspx)ayarlarını değiştirmez.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Mimari tasarım kararlarından biri, çözünürlükten bağımsız düzeninin daha yaygın hale geçen daha yüksek çözünürlüklü DPI izleyicilerini daha iyi desteklemesidir. Bunun nedeni, her ikisi [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] de çözünürlüğe bağımlı olduklarından, bazı Doğu Asya fontlarda diğer ad metin işlemesini veya bit eşlemlerini desteklememe sonucudur.  
  
<a name="further_information"></a>   
## <a name="further-information"></a>Daha fazla bilgi  
 [ClearType bilgileri](https://www.microsoft.com/typography/ClearTypeInfo.mspx)  
  
 [ClearType TV tarayıcısı Poweroyunno](https://www.microsoft.com/typography/ClearTypePowerToy.mspx)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ClearType Kayıt Defteri Ayarları](cleartype-registry-settings.md)
