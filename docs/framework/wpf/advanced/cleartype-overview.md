---
title: ClearType Genel Bakışı
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], ClearType technology
- ClearType [WPF], technology
ms.assetid: 7e2392e0-75dc-463d-a716-908772782431
ms.openlocfilehash: b76c0cb04e5de498374cbf28c8813fe5c95d41ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186161"
---
# <a name="cleartype-overview"></a>ClearType Genel Bakışı
Bu konu, Microsoft ClearType teknolojisinde bulunan [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]genel bir bakış sağlar.  

<a name="overview"></a>
## <a name="technology-overview"></a>Teknolojiye Genel Bakış  
 ClearType, Microsoft tarafından geliştirilen ve dizüstü bilgisayar ekranları, Pocket PC ekranları ve düz panel monitörler gibi mevcut CD'lerde (Liquid Crystal Displays) metnin okunabilirliğini artıran bir yazılım teknolojisidir.  ClearType, LCD ekranın her pikselinde tek tek dikey renkli şerit öğelerine erişerek çalışır. ClearType'tan önce, bilgisayarın görüntüleyebileceği en küçük ayrıntı düzeyi tek bir pikseldi, ancak ClearType LCD monitörde çalışırken, artık genişliği pikselin bir kısmı kadar küçük metin özelliklerini görüntüleyebiliriz. Ekstra çözünürlük, metin ekranındaki küçük ayrıntıların netliğini artırarak uzun süreler boyunca okunmasını çok daha kolay hale getirir.  
  
 ClearType mevcut [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Microsoft Windows Graphics Device Interface (GDI) bulunan sürümü üzerinde çeşitli iyileştirmeler vardır ClearType en son nesil.  
  
<a name="sub-pixel_positioning"></a>
## <a name="sub-pixel-positioning"></a>Alt Piksel Konumlandırma  
 ClearType'ın önceki sürümüne göre önemli bir gelişme alt piksel konumlandırma kullanımıdır. GDI'de bulunan ClearType uygulamasının aksine, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] bulunan ClearType, gliflerin pikselin yalnızca başlangıç sınırı içinde değil, piksel içinde başlamasını sağlar. Gliflerin konumlandırılmasındaki bu ekstra çözünürlük nedeniyle, gliflerin aralıkları ve oranları daha kesin ve tutarlıdır.  
  
 Aşağıdaki iki örnek, alt piksel konumlandırma kullanıldığında gliflerin herhangi bir alt piksel sınırında nasıl başlayabileceğini gösterir. Soldaki örnek, alt piksel konumlandırmasını kullanmayan ClearType işleyicisinin önceki sürümü kullanılarak işlenir. Sağdaki örnek, alt piksel konumlandırma kullanılarak ClearType işleyicisinin yeni sürümü kullanılarak işlenir. Her biri farklı bir alt pikselde başladığı için sağ daki her **e** ve **l'nin** nasıl biraz farklı görüntülenebildiğini unutmayın. Metni ekranda normal boyutunda görüntülerken, bu fark, glyph görüntüsünün yüksek kontrastı nedeniyle fark edilmez. Bu, yalnızca ClearType'a dahil edilen gelişmiş renk filtrelemi nedeniyle mümkündür.  
  
 ![ClearType'ın iki sürümüyle görüntülenen metin](./media/wcpsdk-mmgraphics-text-cleartype-overview-01.png "wcpsdk_mmgraphics_text_cleartype_overview_01")  
ClearType'ın önceki ve sonraki sürümleriyle görüntülenen metin  
  
 Aşağıdaki iki örnek, önceki ClearType işleyicisinden elde edilen çıktıyla ClearType işleyicisinin yeni sürümünü karşılaştırır. Sağda gösterilen alt piksel konumlandırma, özellikle bir alt piksel ile tüm piksel arasındaki farkın önemli bir oranda glyph genişliğini temsil ettiği küçük boyutlarda, ekrandaki tür aralığını büyük ölçüde artırır. Harfler arasındaki aralığın ikinci resimde daha eşit olduğunu unutmayın. Alt piksel konumlandırmanın bir metin ekranının genel görünümüne olan kümülatif yararı büyük ölçüde artırılır ve ClearType teknolojisinde önemli bir evrimi temsil eder.  
  
 ![ClearType'ın önceki sürümüyle görüntülenen metin](./media/wcpsdk-mmgraphics-text-cleartype-overview-02.png "wcpsdk_mmgraphics_text_cleartype_overview_02")  
ClearType'ın önceki ve sonraki sürümlerine sahip metin  
  
<a name="y-direction_antialiasing"></a>
## <a name="y-direction-antialiasing"></a>Y-Yön Antialiasing  
 ClearType bir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] başka gelişme y-yönü anti-takma olduğunu. GDI'de y yönünde anti-diğer ad olmadan ClearType x ekseninde daha iyi çözünürlük sağlar, ancak y ekseni üzerinde değil. Sığ kıvrımların üst ve alt kısımlarında, pürüzlü kenarlar okunabilirliğini düşürür.  
  
 Aşağıdaki örnek, y yönünde antialiasing sahip etkisini gösterir. Bu durumda, mektubun üst ve alt kısmındapp pürüzlü kenarlar belirgindir.  
  
 ![Sığ eğrilerde pürüzlü kenarları olan metin](./media/wcpsdk-mmgraphics-text-cleartype-overview-03.png "wcpsdk_mmgraphics_text_cleartype_overview_03")  
Sığ eğrilerde pürüzlü kenarları olan metin  
  
 ClearType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] içinde herhangi bir pürüzlü kenarları düzeltmek için y yönü düzeyinde antialiasing sağlar. Bu, özellikle ideografların neredeyse eşit miktarda yatay ve dikey sığ eğrilere sahip olduğu Doğu Asya dillerinin okunabilirliğini artırmak için önemlidir.  
  
 Aşağıdaki örnek, y-yönü antialiasing etkisini gösterir. Bu durumda, mektubun üst ve alt düz bir eğri gösterir.  
  
 ![ClearType y&#45;yönü anti&#45;takma metin](./media/wcpsdk-mmgraphics-text-cleartype-overview-04.png "wcpsdk_mmgraphics_text_cleartype_overview_04")  
ClearType y yönü antialiasing ile metin  
  
<a name="hardware_acceleration"></a>
## <a name="hardware-acceleration"></a>Donanım Hızlandırma  
 ClearType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] in, daha iyi performans için donanım ivmesinden yararlanabilir ve CPU yükünü ve sistem bellek gereksinimlerini azaltabilir. ClearType, bir grafik kartının piksel gölgeli ve video belleği kullanarak, özellikle animasyon kullanıldığında metnin daha hızlı görüntülenir.  
  
 ClearType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] içinde sistem genelinde ClearType ayarlarını değiştirmez. Windows'da ClearType'ı [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] devre dışı bırakmak, antialiasing'i gri tonlama moduna ayarlar. Buna ek olarak, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ClearType içinde [ClearType Tuner PowerToy](https://www.microsoft.com/typography/ClearTypePowerToy.mspx)ayarlarını değiştirmez.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Mimari tasarım kararlarından biri, daha yaygın hale gelen daha yüksek çözünürlüklü DPI monitörleri daha iyi destekleyen çözünürlük bağımsız düzene sahip olmaktır. Bu, her [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ikisi de çözüme bağımlı olduğundan, diğer adla metin oluşturmayı veya bazı Doğu Asya yazı tiplerinde bit eşlemlerini desteklememe sonucunu doğurur.  
  
<a name="further_information"></a>
## <a name="further-information"></a>Daha Fazla Bilgi  
 [ClearType Bilgileri](https://www.microsoft.com/typography/ClearTypeInfo.mspx)  
  
 [ClearType Tuner PowerToy](https://www.microsoft.com/typography/ClearTypePowerToy.mspx)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ClearType Kayıt Defteri Ayarları](cleartype-registry-settings.md)
