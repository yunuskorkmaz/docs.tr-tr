---
title: ClearType Genel Bakışı
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], ClearType technology
- ClearType [WPF], technology
ms.assetid: 7e2392e0-75dc-463d-a716-908772782431
ms.openlocfilehash: 1d434fa913d077d72f0f889dc69eccc8a9ed0e9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="cleartype-overview"></a>ClearType Genel Bakışı
Bu konu genel bir bakış sağlar [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] teknolojisi bulunan [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
  
<a name="overview"></a>   
## <a name="technology-overview"></a>Teknoloji genel bakış  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] bir yazılım teknoloji tarafından geliştirilen [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] dizüstü ekranları, Pocket PC ekranları ve düz panel monitörler gibi varolan LCDler (Sıvı Crystal görüntüler) üzerinde metnin okunabilirliğini artırır.  [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] her piksel LCD ekranının tek dikey renk Şerit öğelerine erişerek çalışır. Önce [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)], küçük bir bilgisayarı görüntülemek ayrıntı düzeyini tek pikselli edildi ancak [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] LCD Monitör üzerinde çalışan, biz şimdi piksel kesir olarak küçük metin özelliklerini genişliği görüntüleyebilirsiniz. Ek çözümleme uzun süreler çok okunmasını kolaylaştırmak metin görüntüsündeki küçük ayrıntıların netlik artırır.  
  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] Bulunan [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] son nesil [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] sürümü üzerinde çeşitli geliştirmeleri olan [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)].  
  
<a name="sub-pixel_positioning"></a>   
## <a name="sub-pixel-positioning"></a>Alt piksel konumlandırma  
 Önceki sürümü üzerinde önemli bir iyileştirme [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] alt piksel konumlandırmanın kullanılır. Farklı [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] içinde uygulama bulunan [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)], [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] bulunan [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] piksel ve yalnızca piksel başına sınırları içinde başlatmasına izin verir. Karakterleri konumlandırmada fazladan çözünürlük nedeniyle, aralık ve karakterlerin oranları daha kesin ve tutarlıdır.  
  
 Aşağıdaki iki örnek alt piksel konumlandırma kullanıldığında karakterlerin herhangi alt piksel sınırında nasıl başlatılacağını gösterir. Önceki sürümü kullanılarak işlenmiş soldaki örneği [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] alt piksel konumlandırmayı kullanmayan Oluşturucu. Sağdaki örnek yeni sürümü kullanılarak oluşturulması [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] alt piksel konumlandırmayı kullanarak Oluşturucu. Not nasıl her **e** ve **l** her farklı bir alt pikselini başladığından sağ görüntüde biraz farklı bir şekilde işlenir. Metin ekranında normal boyutunda görüntülerken, bu fark karakter resminin yüksek karşıtlık nedeniyle belirgin değildir. Bu yalnızca karmaşık renk içinde filtrelemesi nedeniyle mümkündür [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)].  
  
 ![İki ClearType sürümleriyle görüntülenen metin](../../../../docs/framework/wpf/advanced/media/wcpsdk-mmgraphics-text-cleartype-overview-01.png "wcpsdk_mmgraphics_text_cleartype_overview_01")  
ClearType önceki ve sonraki sürümleri ile görüntülenen metin  
  
 Aşağıdaki iki örnek önceki çıktısını karşılaştırır [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] işleyicisinin yeni sürümü ile [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] Oluşturucu. Piksel konumlandırma sağ tarafta gösterilen ekranında karakter genişliği önemli bir kısmının alt piksel ve tüm bir piksel arasındaki farkı temsil ettiği özellikle küçük boyutlarda türüne aralığını büyük ölçüde artırır. Harfler arasında daha bile ikinci görüntüde olduğuna dikkat edin. Alt piksel konumlandırmanın metin ekranındaki genel görünüme toplu yararı büyük ölçüde artırılır ve önemli bir evrimi temsil eden [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] teknolojisi.  
  
 ![ClearType önceki sürümü ile görüntülenen metin](../../../../docs/framework/wpf/advanced/media/wcpsdk-mmgraphics-text-cleartype-overview-02.png "wcpsdk_mmgraphics_text_cleartype_overview_02")  
Metni ClearType'nın önceki ve sonraki sürümleri ile  
  
<a name="y-direction_antialiasing"></a>   
## <a name="y-direction-antialiasing"></a>Y yönünde düzgünleştirme  
 Başka bir geliştirilmesini [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] içinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] y yönünde düzgünleştirme değil. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] İçinde [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] y yönünde düzgünleştirme daha iyi çözünürlük x ekseni değil y ekseninde sağlar. Dows masaüstleri ve alta yüzeysel eğrilerinin çentikli kenarları okunabilirlik değerini düşürebilir.  
  
 Aşağıdaki örnek, y yönünde düzgünleştirme sahip etkisini gösterir. Bu durumda, üst ve alt harfi çentikli kenarları görünür.  
  
 ![Yüzeysel eğrileri çentikli kenarları metinle](../../../../docs/framework/wpf/advanced/media/wcpsdk-mmgraphics-text-cleartype-overview-03.png "wcpsdk_mmgraphics_text_cleartype_overview_03")  
Yüzeysel eğrileri çentikli kenarları metinle  
  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] içinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] herhangi çentikli kenarları kesintisiz y yönünde düzeyinin düzgünleştirme sağlar. Bu özellikle İdeogramlar yatay ve dikey yüzeysel eğrileri neredeyse eşit miktarda sahip olduğu Doğu Asya dilleri okunabilirliğini artırmak için önemlidir.  
  
 Aşağıdaki örnek, y yönünde düzgünleştirme etkisini gösterir. Bu durumda, üst ve alt harfi düzgün bir eğri gösterir.  
  
 ![ClearType y metinle&#45;yönü anti&#45;yumuşatma](../../../../docs/framework/wpf/advanced/media/wcpsdk-mmgraphics-text-cleartype-overview-04.png "wcpsdk_mmgraphics_text_cleartype_overview_04")  
ClearType y yönünde düzgünleştirme metinle  
  
<a name="hardware_acceleration"></a>   
## <a name="hardware-acceleration"></a>Donanım hızlandırma  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] içinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] donanım hızlandırmasını daha iyi performans ve CPU yükü ve sistem bellek gereksinimlerini azaltmak için avantajından yararlanabilirsiniz. Piksel gölgelendiriciler ve grafik kartının video belleğini kullanarak [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] özellikle animasyon kullanıldığında, metnin daha hızlı işlenmesini sağlar.  
  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] içinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Sistem genelindeki değiştirmez [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] ayarlar. Devre dışı bırakma [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] içinde [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] ayarlar [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] gri tonlamalı moda düzgünleştirme. Ayrıca, [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] içinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ayarlarını değiştirmez [ClearType tarayıcısı PowerToy](http://www.microsoft.com/typography/ClearTypePowerToy.mspx).  
  
 Aşağıdakilerden birini [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] mimari tasarım kararlarından biri bağımsız düzeni daha iyi destek daha yaygın hale gelirken yüksek çözünürlük DPI monitörlerini Çözümleme sağlamaktır. Bu sonucu olan [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] çözünürlüğe bağlı oldukları için diğer metni işleme veya bit eşlemler bazı Doğu Asya yazı desteklemediğinden.  
  
<a name="further_information"></a>   
## <a name="further-information"></a>Daha fazla bilgi  
 [ClearType bilgileri](http://www.microsoft.com/typography/ClearTypeInfo.mspx)  
  
 [ClearType tarayıcısı PowerToy](http://www.microsoft.com/typography/ClearTypePowerToy.mspx)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClearType Kayıt Defteri Ayarları](../../../../docs/framework/wpf/advanced/cleartype-registry-settings.md)
