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
ms.openlocfilehash: f56a8435b1cdebe0e0af6531c37dccfbe6617a0e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357527"
---
# <a name="graphics-rendering-tiers"></a>Grafik İşleme Katmanları
İşleme katmanı bir grafik donanım özelliği ve çalıştıran bir cihaz için performans düzeyi tanımlayan bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama.  
  

  
<a name="graphics_hardware"></a>   
## <a name="graphics-hardware"></a>Grafik donanımı  
 En çok katmanı işleme düzeyleri etkileyen grafik donanımının özellikleri şunlardır:  
  
-   **Video RAM** birleştirme grafik için kullanılan arabellek sayısı ve boyutu grafik donanımının video bellek miktarı belirler.  
  
-   **Piksel gölgelendirici** piksel gölgelendirici efektleri piksel başına temelinde hesaplar işlevi bir grafik olduğundan. Görüntülenen grafiklerin çözümleme bağlı olarak, her görüntü çerçevesi için işlenmesi gereken birkaç milyon piksel olabilir.  
  
-   **Köşe gölgelendirici** köşe gölgelendiricisi olan nesnenin köşe verileri matematiksel işlemler gerçekleştiren işlevi bir grafik.  
  
-   **Çoklu doku desteği** bir 3B grafik nesnede karıştırma işlemi sırasında iki veya daha fazla farklı dokular uygulama özelliği başvurduğu çoklu doku desteği. Çoklu doku desteği derecesini grafik donanımının çoklu doku birimleri sayısına göre belirlenir.  
  
<a name="rendering_tier_definitions"></a>   
## <a name="rendering-tier-definitions"></a>Katman tanımları oluşturma  
 İşleme yeteneğini grafik donanımının özelliklerini belirlemek bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Sistem üç işleme katmanları tanımlar:  
  
-   **Katman 0 işleme** donanım grafik ivmesi. Tüm grafik özellikleri yazılım hızlandırma kullanın. [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Sürüm düzeyi sürüm 9.0 azdır.  
  
-   **Katman 1 işleme** grafik donanım hızlandırmayı bazı grafik özellikleri kullanın. [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Sürüm düzeyi 9.0 sürümüne eşit veya daha büyük.  
  
-   **Katman 2 işleme** grafik donanım hızlandırmayı çoğu grafik özellikleri kullanın. [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Sürüm düzeyi 9.0 sürümüne eşit veya daha büyük.  
  
 <xref:System.Windows.Media.RenderCapability.Tier%2A?displayProperty=nameWithType> Özelliği uygulama çalışma zamanı oluşturma katmanında almanızı sağlar. İşleme katmanı, cihazın belirli Donanım hızlandırmalı grafik özellikleri destekleyip desteklemediğini belirlemek için kullanın. Uygulamanızı, daha sonra çalışma zamanında cihaz tarafından desteklenen işleme katmanına bağlı olarak farklı kod yollarını alabilir.  
  
### <a name="rendering-tier-0"></a>Katman 0'ı oluşturma  
 İşleme katmanı değeri donanım hızlandırmasını cihazında uygulama için kullanılabilir grafik olduğunu 0 anlamına gelir. Bu katman düzeyinde tüm grafik hiçbir donanım hızlandırma ile yazılım tarafından işlenir varsaymanız gerekir. Bu katman işlevselliği karşılık gelen bir [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] küçüktür 9.0 sürümü.  
  
### <a name="rendering-tier-1-and-rendering-tier-2"></a>İşleme katmanı 1 ve Katman 2 işleme  
  
> [!NOTE]
>  .NET Framework 4 ile başlayarak, işleme Katman 1 yalnızca destekleyen grafik donanımının içerecek şekilde tanımlandı [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 9.0 veya üzeri. Destekleyen grafik donanımının [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 7 veya 8 işleme katman 0 tanımlanan şimdi.  
  
 İşleme katmanı değerini 1 veya 2 grafik özelliklerinin çoğu anlamına gelir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sistem kaynakları kullanılabilir ve tükendi verilmemiş donanım hızlandırması kullanır. Bu karşılık gelen bir [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] büyüktür veya eşittir 9.0 sürümü.  
  
 Aşağıdaki tabloda farklar grafik işleme Katman 1 ve 2 işleme katmanı için donanım gereksinimlerini gösterir:  
  
|Özellik|Katman 1|Katman 2|  
|-------------|------------|------------|  
|[!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Sürüm|Büyüktür veya eşittir 9.0 olmalıdır.|Büyüktür veya eşittir 9.0 olmalıdır.|  
|Video RAM|Büyüktür veya eşittir 60 MB olmalıdır.|Büyüktür veya eşittir 120 MB olmalıdır.|  
|Piksel gölgelendirici|Büyüktür veya eşittir 2.0 için sürüm düzeyi gerekir.|Büyüktür veya eşittir 2.0 için sürüm düzeyi gerekir.|  
|Köşe gölgelendirici|Gereksinimi yoktur.|Büyüktür veya eşittir 2.0 için sürüm düzeyi gerekir.|  
|Çoklu doku birimleri|Gereksinimi yoktur.|Birim sayısı, en az 4 gerekir.|  
  
 Aşağıdaki özellikleri ve yetenekleri donanım işleme Katman 1 ve işleme Katman 2 için hızlandırılmış şunlardır:  
  
|Özellik|Notlar|  
|-------------|-----------|  
|2B işleme|En 2B işleme desteklenir.|  
|3B tarama|Çoğu 3B tarama desteklenir.|  
|3B anizotropik filtreleme|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 3B içerik işlenirken anizotropik filtreleme kullanmayı dener. Anizotropik filtreleme uzakta ve steeply göre kamera açılı yüzeylere doku görüntü kalitesini geliştirmek için ifade eder.|  
|3B MIP harita|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 3B içerik işlenirken MIP eşleme kullanmayı dener. MIP eşleme, bir küçük görünüm alanı içinde bir doku kapladığı, doku işleme kalitesini artırır bir <xref:System.Windows.Controls.Viewport3D>.|  
|Radyal gradyanlar|Destekleniyorsa, kullanmaktan kaçının <xref:System.Windows.Media.RadialGradientBrush> büyük nesneler üzerinde.|  
|3B ışık hesaplamaları|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Her köşe için Kafes uygulanan her bir malzeme için bir ışık yoğunluğunu hesaplanmalıdır anlamına gelir, köşe başına aydınlatma gerçekleştirir.|  
|Metin oluşturma|Alt piksel yazı tipi işleme kullanılabilir piksel gölgelendiricileri grafik donanımda kullanır.|  
  
 Aşağıdaki özellikler ve yetenekler yalnızca işleme katmanı için 2 hızlandırılmış donanım şunlardır:  
  
|Özellik|Notlar|  
|-------------|-----------|  
|3B düzgünleştirme|3B düzgünleştirme yalnızca Windows görüntü sürücü modeli (WDDM) gibi destekleyen işletim sistemleri üzerinde desteklenen [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] ve [!INCLUDE[win7](../../../../includes/win7-md.md)].|  
  
 Aşağıdaki özellikleri ve yetenekleri **değil** donanım hızlandırılmış:  
  
|Özellik|Notlar|  
|-------------|-----------|  
|Yazdırılan içerik|Yazdırılan tüm içerik kullanılarak işlenir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yazılım ardışık düzeni.|  
|Kullanan taranmış içerik <xref:System.Windows.Media.Imaging.RenderTargetBitmap>|İşlenen kullanarak herhangi bir içerik <xref:System.Windows.Media.Imaging.RenderTargetBitmap.Render%2A> yöntemi <xref:System.Windows.Media.Imaging.RenderTargetBitmap>.|  
|Kullanan döşenmiş içerik <xref:System.Windows.Media.TileBrush>|Herhangi bir içerik döşenmiş <xref:System.Windows.Media.TileBrush.TileMode%2A> özelliği <xref:System.Windows.Media.TileBrush> ayarlanır <xref:System.Windows.Media.TileMode.Tile>.|  
|Grafik donanımının doku maksimum boyutunu aşan yüzeyler|Çoğu grafik donanımının için 2048 x 2048 veya 4096 x 4096 piksel boyutunda yüzeyler var.|  
|Herhangi bir işlem bellek, grafik donanımının, video RAM gereksinim aşıyor|Dahil edilen Perforator aracını kullanarak uygulama video RAM kullanımını izleyebildiğinden [WPF Performans Suite](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100)) Windows SDK.|  
|Katmanlı windows|Katmanlı pencerelere izin ver [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ekrana bir dikdörtgen olmayan pencere içeriğini işlemek için uygulamaları. Windows görüntü sürücü modeli (WDDM) gibi destekleyen işletim sistemlerinde [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] ve [!INCLUDE[win7](../../../../includes/win7-md.md)]katmanlı donanım hızlandırılmış dizisidir. Diğer sistemlerde gibi [!INCLUDE[winxp](../../../../includes/winxp-md.md)]katmanlı windows hiçbir Donanım hızlandırmalı yazılım tarafından işlenir.<br /><br /> Katmanlı windows etkinleştirebilirsiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aşağıdaki ayarlayarak <xref:System.Windows.Window> özellikleri:<br /><br /> -   <xref:System.Windows.Window.WindowStyle%2A> = <xref:System.Windows.WindowStyle.None><br />-   <xref:System.Windows.Window.AllowsTransparency%2A> = `true`<br />-   <xref:System.Windows.Controls.Control.Background%2A> = <xref:System.Windows.Media.Brushes.Transparent%2A>|  
  
<a name="other_resources"></a>   
## <a name="other-resources"></a>Diğer Kaynaklar  
 Aşağıdaki kaynaklar performans özellikleri analiz etmenize yardımcı olabileceğini, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama.  
  
### <a name="graphics-rendering-registry-settings"></a>Grafik İşleme Kayıt Defteri Ayarları  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dört kayıt defteri ayarlarını denetlemek için sağlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] işleme:  
  
|Ayar|Açıklama|  
|-------------|-----------------|  
|**Donanım hızlandırma seçeneği devre dışı bırak**|Donanım hızlandırma etkin olup olmadığını belirtir.|  
|**Çoklu örneklem en yüksek değer**|Düzgünleştirmek için çoklu örnekleme derecesini belirtir [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] içeriği.|  
|**Video sürücüsü gerekli tarih ayarı**|Sistem Kasım 2004'ten önce yayımlanan sürücüler için donanım hızlandırmasını devre dışı bırakır olup olmadığını belirtir.|  
|**Başvuru tarayıcısını seçeneğini kullanın**|Belirtir olup olmadığını [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] görüntüleyiciye kullanmanız gerekir.|  
  
 Bu ayarları dosyasına nasıl başvurulacağı bildiği bir dış yapılandırma yardımcı programı tarafından erişilebilen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kayıt defteri ayarları. Bu ayarlar da oluşturulabilir veya değerleri kullanarak doğrudan erişerek [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Kayıt Defteri Düzenleyicisi. Daha fazla bilgi için [grafik işleme kayıt defteri ayarları](../graphics-multimedia/graphics-rendering-registry-settings.md).  
  
### <a name="wpf-performance-profiling-tools"></a>WPF Performans profil oluşturma araçları  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Performans profili oluşturma, uygulamanızın çalışma zamanı davranışını çözümlemenize ve türde uygulayabilirsiniz performans iyileştirmelerini belirlemenize olanak tanıyan araçlar sağlar. Aşağıdaki tabloda bulunan araçları profil oluşturma performans listeler [!INCLUDE[TLA2#tla_lhsdk](../../../../includes/tla2sharptla-lhsdk-md.md)] WPF Performans Suite aracı:  
  
|Aracı|Açıklama|  
|----------|-----------------|  
|Perforator|İşleme davranışını çözümlemek için kullanın.|  
|Visual Profil Oluşturucu|Kullanımını profil oluşturma için kullanmak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzeni ve olay işleme görsel ağaç öğeler tarafından gibi hizmetler.|  
  
 WPF Performans Suite performans verileri zengin, grafik bir görünümünü sağlar. WPF Performans araçları hakkında daha fazla bilgi için bkz: [WPF Performans Suite](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100)).  
  
### <a name="directx-diagnostic-tool"></a>DirectX Tanılama Aracı  
 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Tanılama aracı, Dxdiag.exe, gidermenize yardımcı olmak üzere tasarlanan [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]-ilgili sorunlar. Varsayılan yükleme klasörünü [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] tanı aracıdır:  
  
 `~\Windows\System32`  
  
 Çalıştırdığınızda [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Tanılama aracı, ana pencereyi görüntülemek ve tanılamanızı sağlayan bir sekme kümesi içeren [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]-ilgili bilgileri. Örneğin, **sistem** sekme bilgisayarınız hakkında sistem bilgisi sağlar ve sürümünü belirten [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] bilgisayarınızda yüklü.  
  
 ![Screenhot: DirectX Tanılama Aracı](./media/directxdiagnostictool-01.png "DirectXDiagnosticTool_01")  
DirectX Tanılama Aracı ana penceresi  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Media.RenderCapability>
- <xref:System.Windows.Media.RenderOptions>
- [WPF Uygulama Performansını İyileştirme](optimizing-wpf-application-performance.md)
- [WPF Performans paketi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100))
- [Grafik İşleme Kayıt Defteri Ayarları](../graphics-multimedia/graphics-rendering-registry-settings.md)
- [Animasyon İpuçları ve Püf Noktaları](../graphics-multimedia/animation-tips-and-tricks.md)
