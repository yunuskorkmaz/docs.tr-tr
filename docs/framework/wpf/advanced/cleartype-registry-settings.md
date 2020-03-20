---
title: ClearType Kayıt Defteri Ayarları
ms.date: 03/30/2017
helpviewer_keywords:
- ClearType [WPF], registry settings
- typography [WPF], ClearType registry settings
ms.assetid: 56f314bb-b30b-4f67-8492-8b8a9fa432ae
ms.openlocfilehash: bedd99fcf9b4ca1d10b4c24d7cff9de320e6fd12
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186169"
---
# <a name="cleartype-registry-settings"></a>ClearType Kayıt Defteri Ayarları
Bu konu, WPF uygulamaları tarafından kullanılan Microsoft ClearType kayıt defteri ayarlarına genel bir bakış sağlar.  

<a name="overview"></a>
## <a name="technology-overview"></a>Teknolojiye Genel Bakış  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]metin görüntüleme aygıtına metin işleyen uygulamalar, gelişmiş bir okuma deneyimi sağlamak için ClearType özelliklerini kullanır. ClearType, Microsoft tarafından geliştirilen ve dizüstü bilgisayar ekranları, Pocket PC ekranları ve düz panel monitörler gibi mevcut CD'lerde (Liquid Crystal Displays) metnin okunabilirliğini artıran bir yazılım teknolojisidir. ClearType, LCD ekranın her pikselinde tek tek dikey renkli şerit öğelerine erişerek çalışır. ClearType hakkında daha fazla bilgi için [ClearType Genel Bakış'a](cleartype-overview.md)bakın.  
  
 ClearType ile işlenen metin, çeşitli görüntüleme aygıtlarında görüntülendiğinde önemli ölçüde farklı görünebilir. Örneğin, az sayıda monitör, daha yaygın kırmızı, yeşil, mavi (RGB) sırasına göre renk çizgi öğelerini mavi, yeşil, kırmızı sırada uygular.  
  
 ClearType ile işlenen metin, farklı renk duyarlılığı düzeylerine sahip kişiler tarafından görüntülendiğinde de önemli ölçüde farklı görünebilir. Bazı bireyler diğerlerinden daha iyi renk hafif farklılıklar algılayabilir.  
  
 Bu durumların her birinde, ClearType özelliklerinin her birey için en iyi okuma deneyimini sağlamak için değiştirilmesi gerekir.  
  
<a name="registry_settings"></a>
## <a name="registry-settings"></a>Kayıt Defteri Ayarları  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ClearType özelliklerini denetlemek için dört kayıt defteri ayarı belirtir:  
  
|Ayar|Açıklama|  
|-------------|-----------------|  
|ClearType düzeyi|ClearType renk netliği düzeyini açıklar.|  
|Gama seviyesi|Bir görüntü aygıtının piksel renk bileşeninin düzeyini açıklar.|  
|Piksel yapısı|Bir görüntü aygıtı için piksellerin düzenlenmesini açıklar.|  
|Metin kontrast düzeyi|Görüntülenen metnin kontrast düzeyini açıklar.|  
  
 Bu ayarlara, tanımlanan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ClearType kayıt defteri ayarlarına nasıl başvuruleceğini bilen harici bir yapılandırma yardımcı programı tarafından erişilebilir. Bu ayarlar, windows kayıt defteri düzenleyicisini kullanarak değerlere doğrudan erişerek de oluşturulabilir veya değiştirilebilir.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ClearType kayıt defteri ayarları ayarlanmazsa (varsayılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] durum buysa), uygulama yazı tipi düzgünleme ayarları için Windows sistem parametreleri bilgilerini sorgular.  
  
> [!NOTE]
> Görüntü aygıtı adlarını listeleyen hakkında bilgi `SystemParametersInfo`için Win32 işlevine bakın.  
  
<a name="ClearType_level"></a>
## <a name="cleartype-level"></a>ClearType Düzeyi  
 ClearType düzeyi, bir bireyin renk hassasiyetine ve algısına göre metnin işlenmesini ayarlamanızı sağlar. Bazı kişiler için, ClearType'ı en üst düzeyde kullanan metnin işlenmesi en iyi okuma deneyimini oluşturmaz.  
  
 ClearType düzeyi 0 ile 100 arasında değişen bir bir gerçek değeridir. Varsayılan düzey 100'dür, bu da ClearType'ın görüntü aygıtının renk şerit öğelerinin maksimum kapasitesini kullandığı anlamına gelir. Ancak, 0'lık ClearType düzeyi metni gri ölçek olarak işler. ClearType düzeyini 0 ile 100 arasında bir yere ayarlayarak, bireyin renk hassasiyetine uygun bir ara düzey oluşturabilirsiniz.  
  
### <a name="registry-setting"></a>Kayıt Defteri Ayarı  
 ClearType düzeyi için kayıt defteri ayarı konumu, belirli bir görüntü aygıtı adına karşılık gelen tek bir kullanıcı ayarıdır:  
  
 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Bir kullanıcıiçin her görüntü aygıtı `ClearTypeLevel` adı için bir DWORD değeri tanımlanır. Aşağıdaki ekran görüntüsü, ClearType düzeyi için Kayıt Defteri Düzenleyicisi ayarını gösterir.  
  
 ![Kayıt Defteri Düzenleyicisi'ndeki ClearType ayarları.](./media/cleartype-registry-settings/cleartype-settings-registry-editor.png)  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]uygulamalar, ClearType'lı ve ClearType'sız iki moddan birinde metin işler. Metin ClearType olmadan işlendiğinde, gri ölçek işleme olarak adlandırılır.  
  
<a name="gamma_level"></a>
## <a name="gamma-level"></a>Gama Seviyesi  
 Gama düzeyi, piksel değeri ile parlaklık arasındaki doğrusal olmayan ilişkiyi ifade eder. Gama seviyesi ayarı, görüntü aygıtının fiziksel özelliklerine karşılık gelir; aksi takdirde, işlenmiş çıktıda bozulmalar oluşabilir. Örneğin, metin çok geniş veya çok dar görünebilir veya gliflerin dikey saplarının kenarlarında renk saçaklar görünebilir.  
  
 Gama seviyesi 1000 ile 2200 arasında değişen bir bir gerçek değeridir. Varsayılan düzey 1900'dür.  
  
### <a name="registry-setting"></a>Kayıt Defteri Ayarı  
 Gama düzeyi için kayıt defteri ayarı konumu, belirli bir görüntü aygıtı adına karşılık gelen yerel bir makine ayarıdır:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Bir kullanıcıiçin her görüntü aygıtı `GammaLevel` adı için bir DWORD değeri tanımlanır. Aşağıdaki ekran görüntüsü, gama düzeyi için Kayıt Defteri Düzenleyicisi ayarını gösterir.  
  
 ![Kayıt Defteri Düzenleyicisi'nde ClearType gama düzeyi ayarları](./media/cleartype-registry-settings/cleartype-gamma-level-settings-registry-editor.png)  
  
<a name="pixel_structure"></a>
## <a name="pixel-structure"></a>Piksel Yapısı  
 Piksel yapısı, bir görüntü aygıtı oluşturan piksel türünü açıklar. Piksel yapısı üç türden biri olarak tanımlanır:  
  
|Tür|Değer|Açıklama|  
|----------|-----------|-----------------|  
|Düz|0|Görüntü aygıtının piksel yapısı yoktur. Bu, her renk için ışık kaynaklarının piksel alanına eşit olarak yayıldığı anlamına gelir — buna gri ölçek işleme denir. Standart bir görüntüleme aygıtı bu şekilde çalışır. ClearType işlenen metne hiçbir zaman uygulanmaz.|  
|RGB|1|Ekran aygıtı, aşağıdaki sırayla üç şeritten oluşan piksellere sahiptir: kırmızı, yeşil ve mavi. ClearType işlenen metne uygulanır.|  
|Bgr|2|Ekran aygıtı, aşağıdaki sırada üç şeritten oluşan piksellere sahiptir: mavi, yeşil ve kırmızı. ClearType işlenen metne uygulanır. Siparişin RGB türünden nasıl ters çevrilebildiğini fark edin.|  
  
 Piksel yapısı 0 ile 2 arasında değişen bir tamsayı değerine karşılık gelir. Varsayılan düzey, düz piksel yapısını temsil eden 0'dır.  
  
> [!NOTE]
> Görüntü aygıtı adlarını listeleyen hakkında bilgi `EnumDisplayDevices`için Win32 işlevine bakın.  
  
### <a name="registry-setting"></a>Kayıt Defteri Ayarı  
 Piksel yapısıiçin kayıt defteri ayarı konumu, belirli bir görüntü aygıtı adına karşılık gelen yerel bir makine ayarıdır:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Bir kullanıcıiçin her görüntü aygıtı `PixelStructure` adı için bir DWORD değeri tanımlanır. Aşağıdaki ekran görüntüsü, piksel yapısı için Kayıt Defteri Düzenleyicisi ayarını gösterir.  
  
 ![Kayıt Defteri Düzenleyicisi'nde ClearType gama düzeyi ayarları](./media/cleartype-registry-settings/cleartype-gamma-level-settings-registry-editor.png)  
  
<a name="text_contrast_level"></a>
## <a name="text-contrast-level"></a>Metin Kontrast Düzeyi  
 Metin kontrast düzeyi, gliflerin gövde genişliklerine göre metnin işlenmesini ayarlamanızı sağlar. Metin kontrast düzeyi 0 ile 6 arasında değişen bir tamsayı değeridir— tamsayı değeri ne kadar büyükse, kök o kadar geniştir. Varsayılan düzey 1'dir.  
  
### <a name="registry-setting"></a>Kayıt Defteri Ayarı  
 Metin kontrast düzeyi için kayıt defteri ayarı konumu, belirli bir görüntü aygıtı adına karşılık gelen tek bir kullanıcı ayarıdır:  
  
 `HKEY_CURRENT_USER\Software\Microsoft\Avalon.Graphics\<displayName>`  
  
 Bir kullanıcıiçin her görüntü aygıtı `TextContrastLevel` adı için bir DWORD değeri tanımlanır. Aşağıdaki ekran görüntüsü, metin kontrast düzeyi için Kayıt Defteri Düzenleyicisi ayarını gösterir.  
  
 ![Kayıt Defteri Düzenleyicisi'ndeki ClearType ayarları.](./media/cleartype-registry-settings/cleartype-settings-registry-editor.png)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ClearType Genel Bakışı](cleartype-overview.md)
- [ClearType Antialiasing](/windows/desktop/gdi/cleartype-antialiasing)
