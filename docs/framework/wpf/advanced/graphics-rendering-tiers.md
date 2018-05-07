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
ms.openlocfilehash: 4f9de7736851027c9f6b851984953e37b96d456a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="graphics-rendering-tiers"></a>Grafik İşleme Katmanları
Bir işleme katmanı grafik donanım yeteneğini ve çalışan bir aygıt için performans düzeyini tanımlayan bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama.  
  

  
<a name="graphics_hardware"></a>   
## <a name="graphics-hardware"></a>Grafik donanımı  
 Çoğu işleme katmanı düzeylerini etkileyen grafik donanım özellikleri şunlardır:  
  
-   **Video RAM** birleştirme grafikler için kullanılan arabellek sayısı ve boyutu grafik donanımı üzerindeki video bellek miktarını belirler.  
  
-   **Piksel gölgelendirici** piksel gölgelendirici grafik piksel başına temelinde etkileri hesaplar işlevi değil. Görüntülenen grafiklerin çözümleme bağlı olarak, her görüntü çerçevesi için işlenmesi gereken birkaç milyon piksel olabilir.  
  
-   **Köşe gölgelendirici** köşe gölgelendirici grafik nesnesinin köşe veriler üzerinde matematiksel işlemler gerçekleştiren işlevi değil.  
  
-   **Çoklu doku desteği** 3B grafik nesnesi üzerinde yakınsama işlemi sırasında iki veya daha fazla farklı dokuları uygulama özelliği için çoklu doku desteği başvuruyor. Çoklu doku desteğinin derecesi grafik donanımı üzerindeki çoklu doku birimlerinin sayısı tarafından belirlenir.  
  
<a name="rendering_tier_definitions"></a>   
## <a name="rendering-tier-definitions"></a>Katman tanımları oluşturma  
 Grafik donanım özellikleri işleme yeteneğini belirlemek bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Sistem üç işleme katmanı tanımlar:  
  
-   **Katman 0 işleme** hiçbir grafik donanım hızlandırmasını. Tüm grafik özellikleri yazılım hızlandırma kullanın. [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Sürüm düzeyi 9.0 sürümünden azdır.  
  
-   **Katman 1 işleme** bazı grafik özelliği grafik donanım hızlandırmasını kullanır. [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Sürüm düzeyi 9.0 sürümüne eşit veya daha büyük.  
  
-   **Katman 2 işleme** çoğu grafik özelliği grafik donanım hızlandırmasını kullanır. [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Sürüm düzeyi 9.0 sürümüne eşit veya daha büyük.  
  
 <xref:System.Windows.Media.RenderCapability.Tier%2A?displayProperty=nameWithType> Özelliği işleme katmanını uygulama çalışma zamanı almanıza olanak sağlar. İşleme katmanı, cihaz belirli donanım hızlandırılmış grafik özellikleri destekleyip desteklemediğini belirlemek için kullanın. Uygulamanız, daha sonra aygıt tarafından desteklenen işleme katmanına bağlı olarak çalışma zamanında farklı kod yollarını alabilir.  
  
### <a name="rendering-tier-0"></a>Katman 0 işleme  
 Bir işleme katmanı donanım hızlandırmasını cihazda uygulama için kullanılabilir grafik olduğunu 0 değeri anlamına gelir. Bu katman düzeyinde tüm grafik hiçbir donanım hızlandırmasını ile yazılım tarafından işlenir varsayalım. Bu katman işlevselliği karşılık gelen bir [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] değerinden 9.0 sürümü.  
  
### <a name="rendering-tier-1-and-rendering-tier-2"></a>İşleme katmanı 1 ve Katman 2 işleme  
  
> [!NOTE]
>  .NET Framework 4'te başlayarak, işleme Katman 1 yalnızca, destekleyen bir grafik donanım eklemek için tanımlandı [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 9.0 veya büyük. Destekleyen bir grafik donanım [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 7 veya 8 işleme katman 0 tanımlanan şimdi.  
  
 1 veya 2 işleme katmanı değeri grafik özelliklerinin çoğu anlamına gelir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] donanım hızlandırmasını gerekli sistem kaynaklarının kullanılabildiğini ve tükendi edilmemiş kullanır. Bu karşılık gelen bir [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] büyük veya eşit 9.0 sürümü.  
  
 Aşağıdaki tabloda farklar grafik işleme Katman 1 ve 2 işleme katmanı için donanım gereksinimleri gösterilmektedir:  
  
|Özellik|Katman 1|Katman 2|  
|-------------|------------|------------|  
|[!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Sürüm|9.0 eşit veya daha büyük olmalıdır.|9.0 eşit veya daha büyük olmalıdır.|  
|Video RAM|60 MB eşit veya daha büyük olmalıdır.|120 MB eşit veya daha büyük olmalıdır.|  
|Piksel gölgelendirici|Sürüm düzeyi 2.0 eşit veya daha büyük olmalıdır.|Sürüm düzeyi 2.0 eşit veya daha büyük olmalıdır.|  
|Köşe gölgelendirici|Gereksinim yok.|Sürüm düzeyi 2.0 eşit veya daha büyük olmalıdır.|  
|Çoklu doku birimleri|Gereksinim yok.|Birim sayısı 4'e eşit veya daha büyük olmalıdır.|  
  
 Aşağıdaki özellikler ve yetenekler donanım işleme Katman 1 ve işleme Katman 2 için hızlandırılmış şunlardır:  
  
|Özellik|Notlar|  
|-------------|-----------|  
|2B işleme|En 2B işleme desteklenir.|  
|3B tarama|Çoğu 3B tarama desteklenir.|  
|3B Eşyönsüz filtreleme|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 3B içerik işlenirken Eşyönsüz filtreleme kullanmayı dener. Eşyönsüz filtreleme uzakta ve steeply göre kamera açılı yüzeyleri doku görüntü kalitesini arttırma için ifade eder.|  
|3B MIP eşleme|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 3B içerik işlenirken MIP eşleme kullanmayı dener. MIP eşleme daha küçük bir alan of görünümünde bir doku kapladığı zaman doku işleme kalitesini iyileştirir bir <xref:System.Windows.Controls.Viewport3D>.|  
|Radyal gradyanlar|Destekleniyorsa kullanmaktan kaçının <xref:System.Windows.Media.RadialGradientBrush> büyük nesneler üzerinde.|  
|3B aydınlatma hesaplamaları|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ışık yoğunluğunu her köşe için Kafes uygulanan her malzemeler için adresindeki hesaplanmalıdır anlamına gelir köşe başına aydınlatma gerçekleştirir.|  
|Metin oluşturma|Alt piksel yazı tipi işleme grafik donanımındaki kullanılabilir piksel gölgelendiriciler kullanır.|  
  
 Aşağıdaki özellikler ve yetenekler donanım yalnızca işleme katmanı için 2 hızlandırılmış şunlardır:  
  
|Özellik|Notlar|  
|-------------|-----------|  
|3B düzgünleştirme|3B düzgünleştirme yalnızca işletim destekleyen Windows görüntü sürücüsü modeli (WDDM) gibi sistemlerde desteklenir [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] ve [!INCLUDE[win7](../../../../includes/win7-md.md)].|  
  
 Aşağıdaki özellikleri ve yetenekleri **değil** donanım hızlandırılmış:  
  
|Özellik|Notlar|  
|-------------|-----------|  
|Yazdırılan içerik|Yazdırılan tüm içerik kullanılarak oluşturulması [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yazılım ardışık düzeni.|  
|Kullanan taranmış içerik <xref:System.Windows.Media.Imaging.RenderTargetBitmap>|Kullanarak işlenen herhangi bir içerik <xref:System.Windows.Media.Imaging.RenderTargetBitmap.Render%2A> yöntemi <xref:System.Windows.Media.Imaging.RenderTargetBitmap>.|  
|Kullanan döşeli içerik <xref:System.Windows.Media.TileBrush>|Herhangi bir içerik döşenir <xref:System.Windows.Media.TileBrush.TileMode%2A> özelliği <xref:System.Windows.Media.TileBrush> ayarlanır <xref:System.Windows.Media.TileMode.Tile>.|  
|Grafik donanım yüksek doku boyutunu aşan yüzeyleri|Grafik donanımlarının çoğu için 2048 x 2048 veya 4096 x 4096 piksel boyutundan büyük yüzeyleri var.|  
|Video RAM gerektiren grafik donanım belleği aşıyor herhangi bir işlem|Uygulama video RAM kullanımı dahil Perforator aracını kullanarak izleyebilirsiniz [WPF Performance Suite](http://msdn.microsoft.com/library/67cafaad-57ad-4ecb-9c08-57fac144393e) Windows SDK'sındaki.|  
|Katmanlı pencereler|Katmanlı windows izin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dikdörtgen olmayan penceresinde ekran içeriğini işlemek için uygulamalar. Windows görüntü sürücüsü modeli (WDDM) gibi destekleyen işletim sistemleri üzerinde [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] ve [!INCLUDE[win7](../../../../includes/win7-md.md)]katmanlı windows donanım hızlandırılmış şunlardır. Diğer sistemlerde gibi [!INCLUDE[winxp](../../../../includes/winxp-md.md)]katmanlı windows donanım hızlandırmasını yazılım tarafından işlenir.<br /><br /> Katmanlı pencereleri etkinleştirebilirsiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aşağıdaki ayarlayarak <xref:System.Windows.Window> özellikleri:<br /><br /> -   <xref:System.Windows.Window.WindowStyle%2A> = <xref:System.Windows.WindowStyle.None><br />-   <xref:System.Windows.Window.AllowsTransparency%2A> = `true`<br />-   <xref:System.Windows.Controls.Control.Background%2A> = <xref:System.Windows.Media.Brushes.Transparent%2A>|  
  
<a name="other_resources"></a>   
## <a name="other-resources"></a>Diğer Kaynaklar  
 Aşağıdaki kaynaklar performans özellikleri analiz etmenize yardımcı olabilir, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama.  
  
### <a name="graphics-rendering-registry-settings"></a>Grafik İşleme Kayıt Defteri Ayarları  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dört kayıt defteri ayarlarını denetlemek için sağlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] işleme:  
  
|Ayar|Açıklama|  
|-------------|-----------------|  
|**Donanım hızlandırma seçeneği devre dışı bırak**|Donanım hızlandırma etkin olup olmadığını belirtir.|  
|**En büyük çoklu örneklem değeri**|Düzgünleştirmek için çoklu örnekleme derecesini belirtir [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] içeriği.|  
|**Gerekli ekran kartı sürücüsü tarih ayarı**|Sistem Kasım 2004'ten önce yayımlanan sürücüler için donanım hızlandırmasını devre dışı bırakır olup olmadığını belirtir.|  
|**Başvuru tarayıcısını seçeneği kullanma**|Belirtir olup olmadığını [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] görüntüleyiciye kullanmanız gerekir.|  
  
 Bu ayarların nasıl başvurulacağını bildiği bir dış yapılandırma yardımcı programı tarafından erişilebilen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kayıt defteri ayarları. Bu ayarları da oluşturulabilir veya değerleri kullanarak doğrudan erişerek [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Kayıt Defteri Düzenleyicisi'ni. Daha fazla bilgi için bkz: [grafik işleme kayıt defteri ayarları](../../../../docs/framework/wpf/graphics-multimedia/graphics-rendering-registry-settings.md).  
  
### <a name="wpf-performance-profiling-tools"></a>WPF Performans Profil Araçları  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir profil uygulamanızın çalışma zamanı davranışını çözümlemek ve türde uygulayabileceğiniz performans iyileştirmelerini belirlemenize olanak sağlayan araçları performans sağlar. Profil içinde yer alan araçları performans aşağıdaki tabloda listelenmektedir [!INCLUDE[TLA2#tla_lhsdk](../../../../includes/tla2sharptla-lhsdk-md.md)] aracı, WPF Performans paketi:  
  
|Aracı|Açıklama|  
|----------|-----------------|  
|Perforator|İşleme davranışını çözümlemek için kullanın.|  
|Visual Profil Oluşturucu|Kullanımını profil oluşturma için kullanmak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzeni ve olay işleme görsel ağaç öğeler tarafından gibi hizmetleri.|  
  
 WPF Performance Suite performans verileri zengin, grafik bir görünümünü sağlar. WPF Performans araçları hakkında daha fazla bilgi için bkz: [WPF Performance Suite](http://msdn.microsoft.com/library/67cafaad-57ad-4ecb-9c08-57fac144393e).  
  
### <a name="directx-diagnostic-tool"></a>DirectX Tanı Aracı  
 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Tanılama aracı, Dxdiag.exe, gidermenize yardımcı olmak için tasarlanmış [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]-ile ilgili sorunlar. Varsayılan yükleme klasörünü [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] tanı aracıdır:  
  
 `~\Windows\System32`  
  
 Çalıştırdığınızda [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Tanı Aracı ana penceresinde görüntülemek ve tanılamak izin sekmeler kümesi içeren [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]-ilgili bilgileri. Örneğin, **sistem** sekmesi bilgisayarınız hakkında sistem bilgisi sağlar ve sürümünü belirtir [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] bilgisayarınızda yüklü.  
  
 ![Screenhot: DirectX Tanı Aracı](../../../../docs/framework/wpf/advanced/media/directxdiagnostictool-01.png "DirectXDiagnosticTool_01")  
DirectX Tanı Aracı ana penceresi  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.RenderCapability>  
 <xref:System.Windows.Media.RenderOptions>  
 [WPF Uygulama Performansını İyileştirme](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [WPF Performans paketi](http://msdn.microsoft.com/library/67cafaad-57ad-4ecb-9c08-57fac144393e)  
 [Grafik İşleme Kayıt Defteri Ayarları](../../../../docs/framework/wpf/graphics-multimedia/graphics-rendering-registry-settings.md)  
 [Animasyon İpuçları ve Püf Noktaları](../../../../docs/framework/wpf/graphics-multimedia/animation-tips-and-tricks.md)
