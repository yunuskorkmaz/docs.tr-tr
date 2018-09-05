---
title: ClearType Kayıt Defteri Ayarları
ms.date: 03/30/2017
helpviewer_keywords:
- ClearType [WPF], registry settings
- typography [WPF], ClearType registry settings
ms.assetid: 56f314bb-b30b-4f67-8492-8b8a9fa432ae
ms.openlocfilehash: d6a121e2a95ce4005b43937f83c6c74ec7d8f1c1
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514864"
---
# <a name="cleartype-registry-settings"></a>ClearType Kayıt Defteri Ayarları
Bu konu, genel bir bakış sağlar. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] tarafından kullanılan kayıt defteri ayarları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar.  
  
  
<a name="overview"></a>   
## <a name="technology-overview"></a>Teknoloji genel bakış  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir görüntü cihazı kullanmak için metin işleme uygulamaları [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] okuma deneyimi sağlamak için özellikleri. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] bir yazılım teknolojisi tarafından geliştirilen [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] , dizüstü ekranları, Pocket PC ekranları ve düz panel izleyiciler gibi mevcut LCD'ler (Sıvı Crystal gösterir), metnin okunabilirliğini artırır. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] her piksel LCD ekranın tek dikey renk Şerit öğelerine erişerek çalışır. Daha fazla bilgi için [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)], bkz: [ClearType genel bakışı](../../../../docs/framework/wpf/advanced/cleartype-overview.md).  
  
 İle işlenen metin [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] çeşitli görüntü cihazlarında görüntülendiğinde önemli ölçüde farklı görünebilir. Örneğin, az sayıda izleyiciler uygulamak renk Şerit öğeleri mavi yeşil, kırmızı sırayla yerine daha yaygın kırmızı, yeşil, mavi ( [!INCLUDE[TLA#tla_rgb](../../../../includes/tlasharptla-rgb-md.md)]) sırası.  
  
 İle işlenen metin [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] renk duyarlılık değişen düzeylerde kişiler tarafından görüntülendiğinde önemli ölçüde farklı görünebilir. Bazı kişiler diğerlerine göre daha iyi renk küçük farklılıklar algılayabilir.  
  
 Bu gibi durumlarda, her [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] özellikleri en iyi deneyimi her bir kişinin okuma sağlamak için değiştirilmesi gerekir.  
  
<a name="registry_settings"></a>   
## <a name="registry-settings"></a>Kayıt defteri ayarları  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dört kayıt defteri ayarlarını denetlemek için belirtir [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] özellikleri:  
  
|Ayar|Açıklama|  
|-------------|-----------------|  
|[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] düzeyi|Düzeyini açıklayan [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] renk anlaşılabilir.|  
|Gama düzeyi|Piksel renk bileşeni görüntüleme cihazı için düzeyini açıklar.|  
|Piksel yapısı|Piksel görüntüleme cihazı için düzenlemeyi açıklar.|  
|Metin Karşıtlık düzeyi|Görüntülenen metin karşıtlık düzeyini açıklar.|  
  
 Bu ayarlar, tanımlanan başvurmak nasıl bilen bir dış yapılandırma yardımcı programı tarafından erişilebilen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] kayıt defteri ayarları. Bu ayarlar da oluşturulabilir veya değerleri kullanarak doğrudan erişerek [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Kayıt Defteri Düzenleyicisi.  
  
 Varsa [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] kayıt defteri ayarları ayarlanmadı (olan varsayılan durumu), [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama sorguları [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] sistem parametreleri bilgi yazı tipi düzeltmeye ayarları için.  
  
> [!NOTE]
>  Görüntü cihaz adları listelendirmek hakkında daha fazla bilgi için bkz: `SystemParametersInfo` [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] işlevi.  
  
<a name="ClearType_level"></a>   
## <a name="cleartype-level"></a>ClearType düzeyi  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] Düzeyi işleme metin rengi duyarlılık ve bireysel algısı göre ayarlamanıza olanak verir. Bazı kişiler için metin işleme kullanan [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] en yüksek düzeyde en iyi deneyimi okuma üretmez.  
  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] Düzeyidir 0 ile 100 arasında bir tamsayı değeri. Varsayılan düzey 100, yani [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] görüntü cihazı renk Şerit öğelerinin maksimum özelliğine kullanır. Ancak, bir [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] düzeyi 0 olarak gri tonlamalı metin çizer. Ayarlayarak [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] düzeyi 0 ile 100 arasında bir yerde, bir kişinin renk duyarlılık için uygun bir ara düzeyi oluşturabilirsiniz.  
  
### <a name="registry-setting"></a>Kayıt defteri ayarı  
 Kayıt defteri ayarı konumunun [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] düzeyidir özel bir görüntü cihaz adına karşılık gelen bir kullanıcı ayarı:  
  
 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Bir kullanıcı için her bir görüntü cihazı adı için bir `ClearTypeLevel` DWORD değerini tanımlanır. Aşağıdaki ekran görüntüsünde Kayıt Defteri Düzenleyicisi'ayarı için gösterir [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] düzeyi.  
  
 ![ClearType ayarları kayıt defteri Düzenleyicisi'nde](../../../../docs/framework/wpf/advanced/media/cleartyperegistry01.png "ClearTypeRegistry01")  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları olan ve olmayan ya da iki moddan birini metin işleme [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]. Ne zaman metin işlenen olmadan [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)], onu gri tonlamalı işleme olarak adlandırılır.  
  
<a name="gamma_level"></a>   
## <a name="gamma-level"></a>Gama düzeyi  
 Gama düzeyi bir piksel değeri aydınlatma ile doğrusal ilişkisi ifade eder. Gama düzeyi ayarı fiziksel özelliklerini görüntüleme cihazı için eşleşmelidir; Aksi takdirde, işlenmiş çıktı süreklilikle ortaya çıkabilir. Örneğin, test, çok geniş veya dar görünebilir veya renk fringes glif dikey gövdelerini kenarlara görünebilir.  
  
 Gama 2200 için 1000'den arasında bir tamsayı değeri düzeyidir. Varsayılan düzey 1900 ' dir.  
  
### <a name="registry-setting"></a>Kayıt defteri ayarı  
 Kayıt defteri konumu gama düzeyi ayarı, bir özel bir görüntü cihaz adına karşılık gelen bir yerel makine ayarı şöyle olur:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Bir kullanıcı için her bir görüntü cihazı adı için bir `GammaLevel` DWORD değerini tanımlanır. Aşağıdaki ekran görüntüsünde gama düzeyi için Kayıt Defteri Düzenleyicisi'ni ayarı gösterir.  
  
 ![ClearType ayarları kayıt defteri Düzenleyicisi'nde](../../../../docs/framework/wpf/advanced/media/cleartyperegistry02.png "ClearTypeRegistry02")  
  
<a name="pixel_structure"></a>   
## <a name="pixel-structure"></a>Piksel yapısı  
 Piksel yapısı bir görüntü cihazı olun piksel türünü açıklar. Piksel yapısı üç türlerden biri tanımlanır:  
  
|Tür|Değer|Açıklama|  
|----------|-----------|-----------------|  
|Düz|0|Görüntü cihazı hiçbir piksel yapısına sahip olabilir. Bu her renk için açık kaynakları piksel alana eşit olarak yayılır anlamına gelir; bu gri tonlamalı işleme olarak adlandırılır. Standart bir cihaz works görüntülenme budur. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] işlenen metnin hiçbir zaman uygulanır.|  
|RGB|1.|Görüntü cihazı üç şeritler aşağıdaki sırada oluşur piksel vardır: kırmızı, yeşil ve mavi. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] işlenen metnin uygulanır.|  
|BGR|2|Görüntü cihazı üç şeritler aşağıdaki sırada oluşur piksel vardır: yeşil, mavi ve kırmızı. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] işlenen metnin uygulanır. Sipariş RGB türünden nasıl ters dikkat edin.|  
  
 Piksel yapısı, 0'dan 2 arasında bir tamsayı değerine karşılık gelir. Varsayılan düzey düz piksel yapısını temsil eden 0 ' dır.  
  
> [!NOTE]
>  Görüntü cihaz adları listelendirmek hakkında daha fazla bilgi için bkz: `EnumDisplayDevices` [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] işlevi.  
  
### <a name="registry-setting"></a>Kayıt defteri ayarı  
 Kayıt defteri ayarı piksel yapısı için konum, özel bir görüntü cihaz adına karşılık gelen bir yerel makine ayarı şöyle olur:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Bir kullanıcı için her bir görüntü cihazı adı için bir `PixelStructure` DWORD değerini tanımlanır. Aşağıdaki ekran görüntüsünde, Kayıt Defteri Düzenleyicisi'ni ayarı piksel yapısının gösterir.  
  
 ![ClearType ayarları kayıt defteri Düzenleyicisi'nde](../../../../docs/framework/wpf/advanced/media/cleartyperegistry02.png "ClearTypeRegistry02")  
  
<a name="text_contrast_level"></a>   
## <a name="text-contrast-level"></a>Metin Karşıtlık düzeyi  
 Metin Karşıtlık düzeyi, metin karakterleri fetemm genişliklerini tabanlı işlenmesi ayarlamanıza olanak sağlar. 0 ila 6 arasında bir tamsayı değeri metin Karşıtlık düzeyidir: tamsayı değeri, geniş gövdesi. Varsayılan Düzey 1'dir.  
  
### <a name="registry-setting"></a>Kayıt defteri ayarı  
 Kayıt defteri konumu metin Karşıtlık düzeyi ayarı özel bir görüntü cihaz adına karşılık gelen bir kullanıcı ayarı şöyle olur:  
  
 `HKEY_CURRENT_USER\Software\Microsoft\Avalon.Graphics\<displayName>`  
  
 Bir kullanıcı için her bir görüntü cihazı adı için bir `TextContrastLevel` DWORD değerini tanımlanır. Aşağıdaki ekran görüntüsünde, metin Karşıtlık düzeyi için Kayıt Defteri Düzenleyicisi'ni ayarı gösterir.  
  
 ![ClearType ayarları kayıt defteri Düzenleyicisi'nde](../../../../docs/framework/wpf/advanced/media/cleartyperegistry01.png "ClearTypeRegistry01")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClearType Genel Bakışı](../../../../docs/framework/wpf/advanced/cleartype-overview.md)  
 [ClearType düzgünleştirme](/windows/desktop/gdi/cleartype-antialiasing)
