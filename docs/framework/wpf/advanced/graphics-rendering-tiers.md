---
title: Grafik İşleme Katmanları
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], performance
- rendering graphics [WPF]
- rendering tiers [WPF]
- graphics rendering tiers [WPF]
- graphics [WPF], rendering tiers
ms.assetid: 08dd1606-02a2-4122-9351-c0afd2ec3a70
ms.openlocfilehash: 05847271cf82739a6a0b609771043c02a7ffc0e9
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291582"
---
# <a name="graphics-rendering-tiers"></a>Grafik İşleme Katmanları
İşleme katmanı, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir uygulamayı çalıştıran bir aygıt için grafik donanımı yeteneği ve performansı düzeyini tanımlar.  

<a name="graphics_hardware"></a>
## <a name="graphics-hardware"></a>Grafik Donanımı  
 Grafik donanımının oluşturma katmanı düzeylerini en çok etkileyen özellikleri şunlardır:  
  
- **Video RAM** Grafik donanımındaki video belleği miktarı, grafikleri birbir dizinetmek için kullanılabilecek arabelleklerin boyutunu ve sayısını belirler.  
  
- **Piksel Shader** Piksel gölgeleyici, piksel başına etkileri hesaplayan bir grafik işleme işlevidir. Görüntülenen grafiklerin çözünürlüğüne bağlı olarak, her ekran çerçevesi için işlenmesi gereken birkaç milyon piksel olabilir.  
  
- **Tepe Noktası** Vertex shader nesnenin vertex verileri üzerinde matematiksel işlemler gerçekleştiren bir grafik işleme fonksiyonudur.  
  
- **Multitexture Desteği** Çok doku desteği, 3B grafik nesnesi üzerinde karıştırma işlemi sırasında iki veya daha fazla farklı doku uygulama olanağı anlamına gelir. Çok dokudesteğinin derecesi grafik donanımındaki çok dokulu birimlerin sayısına göre belirlenir.  
  
<a name="rendering_tier_definitions"></a>
## <a name="rendering-tier-definitions"></a>Katman Tanımlarını Oluşturma  
 Grafik donanımının özellikleri, bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamanın oluşturma yeteneğini belirler. Sistem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] üç işleme katmanı tanımlar:  
  
- **Rendering Tier 0** Grafik donanımı ivmesi yok. Tüm grafik özellikleri yazılım ivmesi kullanır. DirectX sürüm düzeyi sürüm 9.0'dan daha azdır.  
  
- **Rendering Tier 1** Bazı grafik özellikleri grafik donanım ıvitme kullanın. DirectX sürüm düzeyi sürüm 9.0'dan daha büyük veya eşittir.  
  
- **Rendering Tier 2** Çoğu grafik özelliği grafik donanımı ivmesi kullanır. DirectX sürüm düzeyi sürüm 9.0'dan daha büyük veya eşittir.  
  
 Özellik, <xref:System.Windows.Media.RenderCapability.Tier%2A?displayProperty=nameWithType> uygulama çalışma zamanında işleme katmanını almanıza olanak tanır. Aygıtın donanım tarafından hızlandırılmış belirli grafik özelliklerini destekleyip desteklemediğini belirlemek için oluşturma katmanını kullanırsınız. Uygulamanız daha sonra, aygıt tarafından desteklenen işleme katmanına bağlı olarak çalışma zamanında farklı kod yolları alabilir.  
  
### <a name="rendering-tier-0"></a>Rendering Tier 0  
 Görüntüleme katmanı değeri 0, aygıttaki uygulama için grafik donanımı ivmesi olmadığı anlamına gelir. Bu katman düzeyinde, tüm grafiklerin donanım ivmesi olmayan yazılımlar tarafından işleneceğini varsaymalısınız. Bu aşamanın işlevselliği, 9.0'dan küçük bir DirectX sürümüne karşılık gelir.  
  
### <a name="rendering-tier-1-and-rendering-tier-2"></a>Katman 1'i oluşturma ve Oluşturma Katmanı 2
  
> [!NOTE]
> .NET Framework 4'ten başlayarak, 1. DirectX 7 veya 8'i destekleyen grafik donanımı artık 0'ı oluşturma olarak tanımlanır.  
  
 1 veya 2 oluşturma katmanı değeri, gerekli sistem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kaynakları varsa ve tükenmemişse, grafik özelliklerinin çoğunun donanım hızlandırmasını kullanacağı anlamına gelir. Bu, 9.0'dan büyük veya eşit bir DirectX sürümüne karşılık gelir.  
  
 Aşağıdaki tablo, katman 1'i oluşturma ve katman 2 oluşturma için grafik donanım gereksinimlerindeki farklılıkları gösterir:  
  
|Özellik|Katman 1|Katman 2|  
|-------------|------------|------------|  
|DirectX sürümü|9.0'dan büyük veya eşit olmalıdır.|9.0'dan büyük veya eşit olmalıdır.|  
|Video RAM|60 MB'dan büyük veya eşit olmalıdır.|120 MB'dan büyük veya eşit olmalıdır.|  
|Piksel gölgeleyici|Sürüm düzeyi 2.0'dan büyük veya eşit olmalıdır.|Sürüm düzeyi 2.0'dan büyük veya eşit olmalıdır.|  
|Tepe noktası|Gerek yok.|Sürüm düzeyi 2.0'dan büyük veya eşit olmalıdır.|  
|Çok dokulu birimler|Gerek yok.|Birim sayısı 4'ten büyük veya eşit olmalıdır.|  
  
 Aşağıdaki özellikler ve özellikler, katman 1'i işlemek ve katman 2'yi işlemek için hızlandırılmış donanımdır:  
  
|Özellik|Notlar|  
|-------------|-----------|  
|2B işleme|Çoğu 2B işleme desteklenir.|  
|3D rasterizasyon|Çoğu 3D rasterization desteklenir.|  
|3D anizotropik filtreleme|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]3D içerik görüntülerken anizotropik filtreleme kullanmaya çalışır. Anizotropik filtreleme, çok uzak ve kameraya göre dik açılı yüzeylerde dokuların görüntü kalitesini artırmak anlamına gelir.|  
|3D MIP eşleme|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]3B içerik görüntülerken MIP eşleme kullanmaya çalışır. MIP eşleme, bir doku daha küçük bir görüş alanını kapladığında <xref:System.Windows.Controls.Viewport3D>doku oluşturma kalitesini artırır.|  
|Radyal degradeler|Desteklenirken, büyük <xref:System.Windows.Media.RadialGradientBrush> nesnelerde kullanmaktan kaçının.|  
|3B aydınlatma hesaplamaları|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]bir kafese uygulanan her malzeme için her tepe noktasında bir ışık yoğunluğunun hesaplanması gerektiği anlamına gelir.|  
|Metin oluşturma|Alt piksel yazı tipi işleme grafik donanımı üzerinde kullanılabilir piksel gölgeleyiciler kullanır.|  
  
 Aşağıdaki özellikler ve özellikler yalnızca katman 2'yi işlemek için hızlandırılmış donanımdır:  
  
|Özellik|Notlar|  
|-------------|-----------|  
|3D anti-takma ad|3B karşıtakma ad, yalnızca Windows Vista ve Windows 7 gibi Windows Display Driver Model'i (WDDM) destekleyen işletim sistemlerinde desteklenir.|  
  
 Aşağıdaki özellikler ve özellikler hızlandırılmış donanım **değildir:**  
  
|Özellik|Notlar|  
|-------------|-----------|  
|Yazdırılan içerik|Yazdırılan tüm içerik, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yazılım ardışık alanı kullanılarak işlenir.|  
|Kullanan rasterized içerik<xref:System.Windows.Media.Imaging.RenderTargetBitmap>|Herhangi bir içerik <xref:System.Windows.Media.Imaging.RenderTargetBitmap.Render%2A> yöntemi kullanılarak <xref:System.Windows.Media.Imaging.RenderTargetBitmap>işlenir.|  
|Kullanan kiremitli içerik<xref:System.Windows.Media.TileBrush>|Özelliğinin <xref:System.Windows.Media.TileBrush.TileMode%2A> ayarlandığı herhangi <xref:System.Windows.Media.TileBrush> bir kiremitli <xref:System.Windows.Media.TileMode.Tile>içerik.|  
|Grafik donanımının maksimum doku boyutunu aşan yüzeyler|Çoğu grafik donanımı için büyük yüzeyler 2048x2048 veya 4096x4096 piksel boyutundadır.|  
|Video RAM gereksinimi grafik donanımının belleği aşan herhangi bir işlem|Windows SDK'daki [WPF Performans Paketi'nde](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100)) yer alan Perforatör aracını kullanarak uygulama videosu RAM kullanımını izleyebilirsiniz.|  
|Katmanlı pencereler|Katmanlı pencereler, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaların dikdörtgen olmayan bir pencerede ekrana içerik işlemesine olanak tanır. Windows Vista ve Windows 7 gibi Windows Display Driver Model'i (WDDM) destekleyen işletim sistemlerinde katmanlı pencereler donanım hızlandırılır. Windows XP gibi diğer sistemlerde, katmanlı pencereler donanım hızlandırması olmayan yazılımlar tarafından işlenir.<br /><br /> Aşağıdaki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window> özellikleri ayarlayarak katmanlı pencereleri etkinleştirebilirsiniz:<br /><br /> -   <xref:System.Windows.Window.WindowStyle%2A> = <xref:System.Windows.WindowStyle.None><br />-   <xref:System.Windows.Window.AllowsTransparency%2A> = `true`<br />-   <xref:System.Windows.Controls.Control.Background%2A> = <xref:System.Windows.Media.Brushes.Transparent%2A>|  
  
<a name="other_resources"></a>
## <a name="other-resources"></a>Diğer Kaynaklar  
 Aşağıdaki kaynaklar, uygulamanızın performans özelliklerini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çözümlemenize yardımcı olabilir.  
  
### <a name="graphics-rendering-registry-settings"></a>Grafik İşleme Kayıt Defteri Ayarları  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]işlemeyi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetlemek için dört kayıt defteri ayarı sağlar:  
  
|Ayar|Açıklama|  
|-------------|-----------------|  
|**Donanım Hızlandırma Seçeneğini Devre Dışı**|Donanım hızlandırmanın etkinlenip etkinleştirilmeyeceğini belirtir.|  
|**Maksimum Çoklu Örnek değeri**|3B içeriğin antialiasing için çoklu örnekleme derecesini belirtir.|  
|**Gerekli Video Sürücü Tarih Ayarı**|Sistemin Kasım 2004'ten önce yayımlanan sürücüler için donanım ivmesini devre dışı bırakıp devre dışı bırakmayacağını belirtir.|  
|**Referans Rasterizer Seçeneğini Kullanın**|Referans rasterizer kullanılıp [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullanılmaması gerektiğini belirtir.|  
  
 Bu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ayarlara, kayıt defteri ayarlarına nasıl başvuruleceğini bilen herhangi bir dış yapılandırma yardımcı programı erişebilir. Bu ayarlar, windows kayıt defteri düzenleyicisini kullanarak değerlere doğrudan erişerek de oluşturulabilir veya değiştirilebilir. Daha fazla bilgi için [Bkz. Grafik Oluşturma Kayıt Defteri Ayarları.](../graphics-multimedia/graphics-rendering-registry-settings.md)  
  
### <a name="wpf-performance-profiling-tools"></a>WPF Performans ProfilOluşturma Araçları  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]uygulamanızın çalışma zamanı davranışını çözümlemenize ve uygulayabileceğiniz performans optimizasyonları türlerini belirlemenize olanak tanıyan bir performans profil oluşturma araçları paketi sağlar. Aşağıdaki tablo, Windows SDK aracı WPF Performance Suite'te yer alan performans profil oluşturma araçlarını listeler:  
  
|Araç|Açıklama|  
|----------|-----------------|  
|Perforator|Oluşturma davranışını çözümleme için kullanın.|  
|Visual Profil Oluşturucu|Düzen ve olay işleme [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] gibi hizmetlerin görsel ağaçtaki öğeler tarafından kullanılmasını profiloluşturmak için kullanın.|  
  
 WPF Performance Suite, performans verilerinin zengin, grafiksel görünümünü sağlar. WPF performans araçları hakkında daha fazla bilgi için [WPF Performance Suite'e](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100))bakın.  
  
### <a name="directx-diagnostic-tool"></a>DirectX Tanılama Aracı'nda  
 DirectX Tanı Lama Aracı, Dxdiag.exe, DirectX ile ilgili sorunları gidermenize yardımcı olmak için tasarlanmıştır. DirectX Tanılama Aracı için varsayılan yükleme klasörü:  
  
 `~\Windows\System32`  
  
 DirectX Tanılama Aracı'nı çalıştırdığınızda, ana pencere, DirectX ile ilgili bilgileri görüntülemenize ve tanılamanıza olanak tanıyan bir sekme kümesi içerir. Örneğin, **Sistem** sekmesi bilgisayarınız hakkında sistem bilgileri sağlar ve bilgisayarınızda yüklenen DirectX sürümünü belirtir.  
  
 ![Ekran Görüntüsü: DirectX Tanılama Aracı](./media/directxdiagnostictool-01.png "DirectXDiagnosticTool_01")  
DirectX Tanılama Aracı ana pencere  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.RenderCapability>
- <xref:System.Windows.Media.RenderOptions>
- [WPF Uygulama Performansını İyileştirme](optimizing-wpf-application-performance.md)
- [WPF Performans Paketi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100))
- [Grafik İşleme Kayıt Defteri Ayarları](../graphics-multimedia/graphics-rendering-registry-settings.md)
- [Animasyon İpuçları ve Püf Noktaları](../graphics-multimedia/animation-tips-and-tricks.md)
