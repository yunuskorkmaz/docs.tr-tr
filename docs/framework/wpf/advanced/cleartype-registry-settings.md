---
title: ClearType Kayıt Defteri Ayarları
ms.date: 03/30/2017
helpviewer_keywords:
- ClearType [WPF], registry settings
- typography [WPF], ClearType registry settings
ms.assetid: 56f314bb-b30b-4f67-8492-8b8a9fa432ae
ms.openlocfilehash: cacdc47a35bfd197bcac29edc6f7c780d3b8578f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541719"
---
# <a name="cleartype-registry-settings"></a>ClearType Kayıt Defteri Ayarları
Bu konu genel bir bakış sağlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] tarafından kullanılan kayıt defteri ayarları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar.  
  
  
<a name="overview"></a>   
## <a name="technology-overview"></a>Teknoloji genel bakış  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir görüntü Aygıt kullanımı metne işleme uygulamaları [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] geliştirilmiş okuma deneyimi sağlamak için özellikler. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] bir yazılım teknoloji tarafından geliştirilen [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] dizüstü ekranları, Pocket PC ekranları ve düz panel monitörler gibi varolan LCDler (Sıvı Crystal görüntüler) üzerinde metnin okunabilirliğini artırır. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] her piksel LCD ekranının tek dikey renk Şerit öğelerine erişerek çalışır. Daha fazla bilgi için [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)], bkz: [ClearType genel bakış](../../../../docs/framework/wpf/advanced/cleartype-overview.md).  
  
 İle işlenen metin [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] çeşitli görüntü cihazlarda görüntülendiğinde önemli ölçüde farklı görünebilir. Örneğin, izleyicileri az sayıda uygulama renk Şerit öğelerine mavi, yeşil, kırmızı sırayla yerine daha yaygın kırmızı, yeşil, mavi ( [!INCLUDE[TLA#tla_rgb](../../../../includes/tlasharptla-rgb-md.md)]) sırası.  
  
 İle işlenen metin [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] renk duyarlılık değişen düzeylerine sahip kişiler tarafından görüntülendiğinde önemli ölçüde farklı görünebilir. Bazı kişiler diğerlerinden daha iyi renkte küçük farklar algılayabilir.  
  
 Bu durumların tümünde [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] özellikleri en iyi deneyimi her kişi için okuma sağlamak için değiştirilmesi gerekir.  
  
<a name="registry_settings"></a>   
## <a name="registry-settings"></a>Kayıt defteri ayarları  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dört kayıt defteri ayarlarını denetlemek için belirtir [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] özellikleri:  
  
|Ayar|Açıklama|  
|-------------|-----------------|  
|[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] düzeyi|Düzeyini açıklayan [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] renk daha anlaşılır olması.|  
|Gama düzeyi|Görüntüleme cihazı için piksel renk bileşeni düzeyini açıklar.|  
|Piksel yapısı|Piksel düzenlemeyi görüntüleme cihazı için açıklar.|  
|Metin Karşıtlık düzeyi|Görüntülenen metin karşıtlık düzeyini açıklar.|  
  
 Bu ayarlar, tanımlanan başvurmak bildiği bir dış yapılandırma yardımcı programı tarafından erişilebilen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] kayıt defteri ayarları. Bu ayarları da oluşturulabilir veya değerleri kullanarak doğrudan erişerek [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Kayıt Defteri Düzenleyicisi'ni.  
  
 Varsa [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] kayıt defteri ayarları ayarlı değil (Bu varsayılan durumu), [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama sorguları [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] ayarları düzgünleştirme yazı tipi için sistem parametre bilgileri.  
  
> [!NOTE]
>  Görüntü cihaz adlarını numaralandırma hakkında daha fazla bilgi için bkz: `SystemParametersInfo` [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] işlevi.  
  
<a name="ClearType_level"></a>   
## <a name="cleartype-level"></a>ClearType düzeyi  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] Düzeyi metnin rengi duyarlılık ve tek bir algısı göre işlenmesini ayarlamanıza olanak verir. Bazı kişiler için metin işleme kullanan [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] en yüksek düzeyde en iyi deneyimi okuma üretmez.  
  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] Düzeyidir 0 ile 100 olarak değişen bir tamsayı değeri. Varsayılan 100, yani düzeyidir [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] görüntü aygıtının renk Şerit öğelerinin maksimum özelliğine kullanır. Ancak, bir [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 0 düzeyi metin gri ölçekli olarak işler. Ayarlayarak [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] düzey 0 ile 100 arasında bir yerde, bireyin renk duyarlılık için uygun bir ara düzeyi oluşturabilirsiniz.  
  
### <a name="registry-setting"></a>Kayıt defteri ayarı  
 Kayıt defteri ayarı konumunun [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] düzeyidir özel bir görüntü cihaz adına karşılık gelen bir bireysel kullanıcı ayarı:  
  
 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Bir kullanıcı için her bir görüntü aygıt adı için bir `ClearTypeLevel` DWORD değerini tanımlanır. Aşağıdaki ekran görüntüsü için Kayıt Defteri Düzenleyicisi'ni ayarı gösterir [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] düzeyi.  
  
 ![Kayıt Defteri Düzenleyicisi'nde ClearType ayarları](../../../../docs/framework/wpf/advanced/media/cleartyperegistry01.png "ClearTypeRegistry01")  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları işlemek olan ve olmayan ya da iki moddan birini metinde [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]. Ne zaman metin işlenen olmadan [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)], bunun için gri ölçekli işleme olarak adlandırılır.  
  
<a name="gamma_level"></a>   
## <a name="gamma-level"></a>Gama düzeyi  
 Gama düzeyi piksel değeri ve Aydınlatma arasındaki doğrusal ilişkiyi gösterir. Gama düzeyi ayarı fiziksel özelliklerini görüntüleme cihazı için eşleşmelidir; Aksi takdirde, işlenmiş çıkış süreklilikle ortaya çıkabilir. Örneğin, test çok geniş ya da çok dar görünebilir veya renk fringes karakterlerin dikey gövdelerini kenarlarına görünebilir.  
  
 Gama düzeyi için 2200 1000'den aralıkları bir tamsayı değil. Varsayılan, 1900 düzeydir.  
  
### <a name="registry-setting"></a>Kayıt defteri ayarı  
 Kayıt defteri konumu gama için düzeyi ayarı özel bir görüntü cihaz adına karşılık gelen bir yerel makine ayardır:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Bir kullanıcı için her bir görüntü aygıt adı için bir `GammaLevel` DWORD değerini tanımlanır. Aşağıdaki ekran görüntüsünde gama düzeyi için Kayıt Defteri Düzenleyicisi'ni ayarı gösterir.  
  
 ![Kayıt Defteri Düzenleyicisi'nde ClearType ayarları](../../../../docs/framework/wpf/advanced/media/cleartyperegistry02.png "ClearTypeRegistry02")  
  
<a name="pixel_structure"></a>   
## <a name="pixel-structure"></a>Piksel yapısı  
 Piksel yapısını görüntüleme aygıtı olun piksel türünü açıklar. Piksel yapısı üç türlerinden biri olarak tanımlanır:  
  
|Tür|Değer|Açıklama|  
|----------|-----------|-----------------|  
|Düz|0|Görüntü aygıtı hiçbir piksel yapısına sahip olabilir. Bu açık kaynakları her renk için piksel alana eşit olarak yayılır anlamına gelir — bu gri ölçekli işleme olarak adlandırılır. Bir standart aygıt works görüntülenme budur. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] hiçbir zaman İşlenmiş metin uygulanır.|  
|RGB|1.|Aşağıdaki sırayla üç şeritler oluşur piksel görüntü aygıtın: kırmızı, yeşil ve mavi. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] İşlenmiş metin uygulanır.|  
|BGR|2|Aşağıdaki sırayla üç şeritler oluşur piksel görüntü aygıtın: yeşil, mavi ve kırmızı. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] İşlenmiş metin uygulanır. Sipariş RGB türünden nasıl ters dikkat edin.|  
  
 Piksel yapısı, 0 ile 2'ye değişen bir tam sayı değerine karşılık gelir. Varsayılan düzeyini düz piksel yapısını temsil eden 0 ' dır.  
  
> [!NOTE]
>  Görüntü cihaz adlarını numaralandırma hakkında daha fazla bilgi için bkz: `EnumDisplayDevices` [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] işlevi.  
  
### <a name="registry-setting"></a>Kayıt defteri ayarı  
 Kayıt defteri konumu piksel yapısı için ayarı özel bir görüntü cihaz adına karşılık gelen bir yerel makine ayardır:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Bir kullanıcı için her bir görüntü aygıt adı için bir `PixelStructure` DWORD değerini tanımlanır. Aşağıdaki ekran görüntüsünde piksel yapısı için Kayıt Defteri Düzenleyicisi'ni ayarını gösterir.  
  
 ![Kayıt Defteri Düzenleyicisi'nde ClearType ayarları](../../../../docs/framework/wpf/advanced/media/cleartyperegistry02.png "ClearTypeRegistry02")  
  
<a name="text_contrast_level"></a>   
## <a name="text-contrast-level"></a>Metin Karşıtlık düzeyi  
 Metin Karşıtlık düzeyi karakterlerin stem genişliğini göre metin işleme ayarlamanıza olanak verir. 0 ile 6 için değişen bir tamsayı değeri metin Karşıtlık düzeyidir — büyük tamsayı değeri, daha geniş gövdesi. Varsayılan düzeyini 1'dir.  
  
### <a name="registry-setting"></a>Kayıt defteri ayarı  
 Kayıt defteri konumu metin Karşıtlık düzeyi ayarı özel bir görüntü cihaz adına karşılık gelen bir bireysel kullanıcı ayarı şöyledir:  
  
 `HKEY_CURRENT_USER\Software\Microsoft\Avalon.Graphics\<displayName>`  
  
 Bir kullanıcı için her bir görüntü aygıt adı için bir `TextContrastLevel` DWORD değerini tanımlanır. Aşağıdaki ekran görüntüsünde metin Karşıtlık düzeyi için Kayıt Defteri Düzenleyicisi'ni ayarı gösterir.  
  
 ![Kayıt Defteri Düzenleyicisi'nde ClearType ayarları](../../../../docs/framework/wpf/advanced/media/cleartyperegistry01.png "ClearTypeRegistry01")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClearType Genel Bakışı](../../../../docs/framework/wpf/advanced/cleartype-overview.md)  
 [ClearType düzgünleştirme](https://msdn.microsoft.com/library/dd183433(v=vs.85).aspx)
