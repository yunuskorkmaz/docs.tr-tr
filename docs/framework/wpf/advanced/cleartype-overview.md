---
title: ClearType Genel Bakışı
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], ClearType technology
- ClearType [WPF], technology
ms.assetid: 7e2392e0-75dc-463d-a716-908772782431
ms.openlocfilehash: 236d6dec444c8169c164e9f096c7f81a336fdca4
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44185265"
---
# <a name="cleartype-overview"></a>ClearType Genel Bakışı
Bu konu, genel bir bakış sağlar. [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] teknoloji bulunan [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
  
<a name="overview"></a>   
## <a name="technology-overview"></a>Teknoloji genel bakış  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] bir yazılım teknolojisi tarafından geliştirilen [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] , dizüstü ekranları, Pocket PC ekranları ve düz panel izleyiciler gibi mevcut LCD'ler (Sıvı Crystal gösterir), metnin okunabilirliğini artırır.  [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] her piksel LCD ekranın tek dikey renk Şerit öğelerine erişerek çalışır. Önce [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)], küçük bir bilgisayar görüntüleyebilir ayrıntı düzeyini tek bir piksel olan ancak [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] LCD Monitör üzerinde çalışan, biz artık özellikleri bir pikselin kesir olarak küçük metnin genişliği görüntüleyebilir. Ek çözümleme uzun süreler okumak çok daha kolay hale metin görüntüleme, küçük ayrıntıları netliğini artırır.  
  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] Bulunan [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] en son nesil [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] sürümü üzerinde çeşitli iyileştirmeler olduğu [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)].  
  
<a name="sub-pixel_positioning"></a>   
## <a name="sub-pixel-positioning"></a>Alt piksel konumlandırma  
 Önceki sürümü üzerinde önemli bir iyileştirme [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] alt piksel konumlandırmanın kullanılır. Farklı [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] uygulaması içinde bulunan [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)], [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] bulunan [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] piksel ve yalnızca piksel başına sınırları içinde başlatmasına izin verir. Bu ek çözümleme nedeniyle, karakterleri konumlandırmada karakterleri oranları ve aralığı daha kesin ve tutarlı.  
  
 Aşağıdaki iki örnek, alt piksel konumlandırma kullanıldığında karakterleri bir alt piksel sınırında nasıl başlatılacağını gösterir. Sol taraftaki örnek önceki sürümünü kullanarak işlenir [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] işleyici ise alt piksel konumlandırmayı değil. Sağ taraftaki örnek yeni bir sürümü kullanılarak işlenir [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] alt piksel konumlandırmayı kullanarak, işleyici. Not nasıl her **e** ve **l** her farklı bir alt pikselini başladığı için sağdaki resimde biraz farklı şekilde işlenir. Metin ekranında normal boyutunda görüntülerken, bu fark simge resminin yüksek karşıtlığı nedeniyle belirgin değildir. Bu yalnızca karmaşık renk içinde filtrelemesi nedeniyle mümkündür [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)].  
  
 ![ClearType iki sürümünü görüntülenen metin](../../../../docs/framework/wpf/advanced/media/wcpsdk-mmgraphics-text-cleartype-overview-01.png "wcpsdk_mmgraphics_text_cleartype_overview_01")  
ClearType önceki ve sonraki sürümleri ile görüntülenen metin  
  
 Aşağıdaki iki örnek çıktısı önceki karşılaştırma [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] yeni sürümünü işleyiciyle [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] Oluşturucu. Piksel konumlandırma, sağ tarafta gösterilen aralığı türü ekranında, özellikle küçük boyutlarda karakter genişliği önemli bir kısmı alt piksel ve tüm bir piksel arasındaki farkı temsil ettiği en önemli ölçüde artırır. Harfler aralığını daha da ikinci görüntüde olduğuna dikkat edin. Alt piksel ekrana metnin genel görünümünü konumlandırma toplu avantajı büyük ölçüde artar ve önemli bir aşamadır temsil eden [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] teknoloji.  
  
 ![ClearType önceki bir sürümü ile görüntülenen metin](../../../../docs/framework/wpf/advanced/media/wcpsdk-mmgraphics-text-cleartype-overview-02.png "wcpsdk_mmgraphics_text_cleartype_overview_02")  
ClearType önceki ve sonraki sürümleri ile metin  
  
<a name="y-direction_antialiasing"></a>   
## <a name="y-direction-antialiasing"></a>Y yönünde düzgünleştirme  
 Başka bir geliştirme [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] içinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] y yönünde düzgünleştirme olduğu. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] İçinde [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] y yönünde düzgünleştirme daha iyi çözüm x ekseninde y sağlar. Kırpın ve alta yüzeysel eğrilerinin çentikli kenarları okunabilirlik değerini düşürebilir.  
  
 Aşağıdaki örnek, hiçbir y yönünde düzgünleştirme olan etkisini gösterir. Bu durumda, üst ve alt harfi sivri kenarlar görünür.  
  
 ![Yüzeysel eğrileri çentikli kenarlara metinle](../../../../docs/framework/wpf/advanced/media/wcpsdk-mmgraphics-text-cleartype-overview-03.png "wcpsdk_mmgraphics_text_cleartype_overview_03")  
Yüzeysel eğrileri çentikli kenarlara metin  
  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] içinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] düzgünleştirme herhangi çentikli kenarları yumuşak y yönünde düzeyi sağlar. Bu özellikle İdeogramlar eşit miktarda bir yatay ve dikey yüzeysel eğrileri sahip olduğu Doğu Asya dilleri okunabilirliğini artırmak için önemlidir.  
  
 Aşağıdaki örnek, y yönünde düzgünleştirme etkisini gösterir. Bu durumda, üst ve alt harfi düzgün bir eğri gösterir.  
  
 ![ClearType y metinle&#45;anti yönü&#45;yumuşatma](../../../../docs/framework/wpf/advanced/media/wcpsdk-mmgraphics-text-cleartype-overview-04.png "wcpsdk_mmgraphics_text_cleartype_overview_04")  
ClearType y yönünde düzgünleştirme ile metin  
  
<a name="hardware_acceleration"></a>   
## <a name="hardware-acceleration"></a>Donanım hızlandırma  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] içinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] daha iyi performans ve CPU yükü ve sistem bellek gereksinimlerini azaltmak için donanım hızlandırma avantajlarından yararlanabilirsiniz. Piksel gölgelendiricileri ve bir grafik kartının video belleği kullanarak [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] özellikle animasyon kullanıldığında, metnin daha hızlı bir şekilde işlenmesini sağlar.  
  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] içinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sistem genelinde değiştirmez [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] ayarları. Devre dışı bırakma [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] içinde [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] ayarlar [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] düzgünleştirme gri tonlamalı modu. Ayrıca, [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] içinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ayarlarını değiştirmez [ClearType tarayıcısı PowerToy](https://www.microsoft.com/typography/ClearTypePowerToy.mspx).  
  
 Aşağıdakilerden birini [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] mimari tasarım kararları olan bağımsız düzenini daha iyi desteklemek daha yaygın hale gelmektedir daha yüksek çözünürlüklü DPI izleyiciler çözümleme. Bu sonucu olan [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] çözünürlüğe bağımlı oldukları diğer adlı metin işleme ya da bit eşlemler bazı Doğu Asya yazı tiplerini destekleyen değil.  
  
<a name="further_information"></a>   
## <a name="further-information"></a>Daha fazla bilgi  
 [ClearType bilgileri](https://www.microsoft.com/typography/ClearTypeInfo.mspx)  
  
 [ClearType tarayıcısı PowerToy](https://www.microsoft.com/typography/ClearTypePowerToy.mspx)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClearType Kayıt Defteri Ayarları](../../../../docs/framework/wpf/advanced/cleartype-registry-settings.md)
