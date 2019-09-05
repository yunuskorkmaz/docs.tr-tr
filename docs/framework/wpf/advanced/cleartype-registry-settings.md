---
title: ClearType Kayıt Defteri Ayarları
ms.date: 03/30/2017
helpviewer_keywords:
- ClearType [WPF], registry settings
- typography [WPF], ClearType registry settings
ms.assetid: 56f314bb-b30b-4f67-8492-8b8a9fa432ae
ms.openlocfilehash: 5113de6d8d333983e6e26579ff9803a9f5a62816
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70254168"
---
# <a name="cleartype-registry-settings"></a>ClearType Kayıt Defteri Ayarları
Bu konu, WPF uygulamaları tarafından kullanılan Microsoft ClearType kayıt defteri ayarlarına genel bir bakış sağlar.  

<a name="overview"></a>   
## <a name="technology-overview"></a>Teknolojiye genel bakış  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]bir görüntüleme cihazına metin işleyen uygulamalar, Gelişmiş okuma deneyimi sağlamak için ClearType özelliklerini kullanır. ClearType, dizüstü ekranları, Pocket PC ekranları ve düz panel izleyicileri gibi mevcut LCD 'lerde (sıvı kristal ekranlar) metinlerin okunabilirliğini artıran Microsoft tarafından geliştirilen bir yazılım teknolojisidir. ClearType, bir LCD ekranın her pikseline tek dikey renk Stripe öğelerine erişerek işe yarar. ClearType hakkında daha fazla bilgi için bkz. [ClearType Genel Bakış](cleartype-overview.md).  
  
 ClearType ile işlenen metin, çeşitli görüntü cihazlarında görüntülendiklerinde önemli ölçüde farklı görünebilir. Örneğin, küçük sayıda izleyici renk Stripe öğelerini, daha sık görülen kırmızı, yeşil, mavi (RGB) sıra yerine mavi, yeşil, kırmızı düzende uygular.  
  
 ClearType ile işlenen metin, farklı renk duyarlılığı düzeylerine sahip kişiler tarafından görüntülendiklerinde önemli ölçüde farklı şekilde de görüntülenebilir. Bazı bireyler renk açısından hafif farklılıkları diğerlerinden daha iyi algılayabilirler.  
  
 Bu durumların her birinde, her biri için en iyi okuma deneyimini sağlamak üzere ClearType özelliklerinin değiştirilmesi gerekir.  
  
<a name="registry_settings"></a>   
## <a name="registry-settings"></a>Kayıt defteri ayarları  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ClearType özelliklerini denetlemek için dört kayıt defteri ayarı belirtir:  
  
|Ayar|Açıklama|  
|-------------|-----------------|  
|ClearType düzeyi|ClearType renk netliği düzeyini açıklar.|  
|Gama düzeyi|Bir görüntü cihazının piksel rengi bileşeninin düzeyini açıklar.|  
|Piksel yapısı|Bir görüntü cihazının piksel düzenlemesini açıklar.|  
|Metin karşıtlığı düzeyi|Görünen metnin kontrast düzeyini açıklar.|  
  
 Bu ayarlara, tanımlanan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ClearType kayıt defteri ayarlarına nasıl başvurulacağını bilen bir dış yapılandırma yardımcı programı tarafından erişilebilir. Bu ayarlar, Windows kayıt defteri Düzenleyicisi kullanılarak değerlere doğrudan erişerek da oluşturulabilir veya değiştirilebilir.  
  
 ClearType kayıt defteri ayarları ayarlanmamışsa (varsayılan durum) [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , uygulama, yazı tipi yumuşatma ayarları için Windows sistem parametreleri bilgilerini sorgular. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]  
  
> [!NOTE]
> Görüntüleme cihaz adlarını numaralandırma hakkında bilgi için bkz `SystemParametersInfo` [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] . işlevi.  
  
<a name="ClearType_level"></a>   
## <a name="cleartype-level"></a>ClearType düzeyi  
 ClearType düzeyi, bir bireyin için renk duyarlılığı ve permütasyon temelinde metin işlemesini ayarlamanıza olanak sağlar. Bazı bireyler için, en yüksek düzeyde ClearType kullanan metnin işlenmesi en iyi okuma deneyimini oluşturmaz.  
  
 ClearType düzeyi, 0 ile 100 arasında değişen bir tamsayı değeridir. Varsayılan düzey 100 ' dir. Bu, ClearType 'ın, görüntüleme cihazının renk şeridi öğelerinin en yüksek yeteneğini kullanması anlamına gelir. Ancak, bir ClearType düzeyi 0, metni gri ölçekli olarak işler. ClearType düzeyini 0 ile 100 arasında bir yere ayarlayarak, bir kişinin renk duyarlılığı için uygun bir ara düzeyi oluşturabilirsiniz.  
  
### <a name="registry-setting"></a>Kayıt defteri ayarı  
 ClearType düzeyi için kayıt defteri ayarı konumu, belirli bir görüntü aygıtı adına karşılık gelen bireysel bir Kullanıcı ayarıdır:  
  
 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Bir kullanıcının her ekran cihaz adı için bir `ClearTypeLevel` DWORD değeri tanımlanmıştır. Aşağıdaki ekran görüntüsünde, ClearType düzeyi için kayıt defteri Düzenleyicisi ayarı gösterilmektedir.  
  
 ![Kayıt defteri düzenleyicisinde ClearType ayarları.](./media/cleartype-registry-settings/cleartype-settings-registry-editor.png)  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]uygulamalar, ClearType ile ve olmayan iki moddan birinde metin işler. Metin ClearType olmadan işlendiğinde gri ölçekli işleme olarak adlandırılır.  
  
<a name="gamma_level"></a>   
## <a name="gamma-level"></a>Gama düzeyi  
 Gama düzeyi piksel değeri ve ışıklılık arasındaki doğrusal olmayan ilişkiyi ifade eder. Gama düzeyi ayarı, görüntüleme cihazının fiziksel özelliklerine karşılık gelmelidir; Aksi takdirde, işlenen çıktıda deformasyonlar olabilir. Örneğin, test çok geniş veya çok dar görünebilir ya da karakterlerin dikey steklerin kenarları üzerinde renkli fringes görünebilir.  
  
 Gama düzeyi 1000 ile 2200 arasında değişen bir tamsayı değeridir. Varsayılan düzey 1900 ' dir.  
  
### <a name="registry-setting"></a>Kayıt defteri ayarı  
 Gama düzeyi için kayıt defteri ayarı konumu, belirli bir görüntü aygıtı adına karşılık gelen bir yerel makine ayarıdır:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Bir kullanıcının her ekran cihaz adı için bir `GammaLevel` DWORD değeri tanımlanmıştır. Aşağıdaki ekran görüntüsünde, gama düzeyi için kayıt defteri Düzenleyicisi ayarı gösterilmektedir.  
  
 ![Kayıt defteri düzenleyicisinde ClearType gama düzeyi ayarları](./media/cleartype-registry-settings/cleartype-gamma-level-settings-registry-editor.png)  
  
<a name="pixel_structure"></a>   
## <a name="pixel-structure"></a>Piksel yapısı  
 Piksel yapısı, bir görüntü cihazını oluşturan piksellerin türünü tanımlar. Piksel yapısı, üç türden biri olarak tanımlanır:  
  
|Tür|Değer|Açıklama|  
|----------|-----------|-----------------|  
|Düz|0|Görüntü cihazının piksel yapısı yok. Bu, her renk için açık kaynakların piksel alanına eşit olarak yayıldığı anlamına gelir; buna gri ölçekli işleme denir. Bu, standart görüntü cihazının nasıl çalıştığı. ClearType, işlenen metne hiçbir şekilde uygulanmaz.|  
|RGB|1\.|Görüntü cihazının şu sırada üç şeritden oluşan pikselleri vardır: kırmızı, yeşil ve mavi. ClearType, işlenen metne uygulanır.|  
|BGR|2|Görüntü cihazında şu sırada üç şeritden oluşan pikseller vardır: mavi, yeşil ve kırmızı. ClearType, işlenen metne uygulanır. Sıranın RGB türünden nasıl tersine çevrildiğine dikkat edin.|  
  
 Piksel yapısı, 0 ile 2 arasında değişen bir tamsayı değerine karşılık gelir. Varsayılan düzey, düz bir piksel yapısını temsil eden 0 ' dır.  
  
> [!NOTE]
> Görüntüleme cihaz adlarını numaralandırma hakkında bilgi için bkz `EnumDisplayDevices` [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] . işlevi.  
  
### <a name="registry-setting"></a>Kayıt defteri ayarı  
 Piksel yapısına yönelik kayıt defteri ayarı konumu, belirli bir görüntü aygıtı adına karşılık gelen bir yerel makine ayarıdır:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Bir kullanıcının her ekran cihaz adı için bir `PixelStructure` DWORD değeri tanımlanmıştır. Aşağıdaki ekran görüntüsünde, piksel yapısına yönelik kayıt defteri Düzenleyicisi ayarı gösterilmektedir.  
  
 ![Kayıt defteri düzenleyicisinde ClearType gama düzeyi ayarları](./media/cleartype-registry-settings/cleartype-gamma-level-settings-registry-editor.png)  
  
<a name="text_contrast_level"></a>   
## <a name="text-contrast-level"></a>Metin karşıtlığı düzeyi  
 Metin karşıtlığı düzeyi, karakterlerin alt genişlerine göre metin işlemesini ayarlamanıza olanak sağlar. Metin karşıtlığı düzeyi, 0 ile 6 arasında değişen bir tamsayı değeridir — tamsayı değeri, daha geniş. Varsayılan düzey 1 ' dir.  
  
### <a name="registry-setting"></a>Kayıt defteri ayarı  
 Metin karşıtlığı düzeyi için kayıt defteri ayarı konumu, belirli bir görüntü aygıtı adına karşılık gelen bireysel bir Kullanıcı ayarıdır:  
  
 `HKEY_CURRENT_USER\Software\Microsoft\Avalon.Graphics\<displayName>`  
  
 Bir kullanıcının her ekran cihaz adı için bir `TextContrastLevel` DWORD değeri tanımlanmıştır. Aşağıdaki ekran görüntüsünde, metin karşıtlığı düzeyi için kayıt defteri Düzenleyicisi ayarı gösterilmektedir.  
  
 ![Kayıt defteri düzenleyicisinde ClearType ayarları.](./media/cleartype-registry-settings/cleartype-settings-registry-editor.png)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ClearType Genel Bakışı](cleartype-overview.md)
- [ClearType düzgünleştirme](/windows/desktop/gdi/cleartype-antialiasing)
