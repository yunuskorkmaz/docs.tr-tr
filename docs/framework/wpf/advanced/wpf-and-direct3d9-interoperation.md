---
title: WPF ve Direct3D9 Birlikte Çalışması
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- WPF [WPF], creating Direct3D9 content
- Direct3D9 [WPF interoperability], creating Direct3D9 content
ms.assetid: 1b14b823-69c4-4e8d-99e4-f6dade58f89a
ms.openlocfilehash: 38f5eb36e3e5c055c5a354a67e15cde8049a2967
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59307736"
---
# <a name="wpf-and-direct3d9-interoperation"></a>WPF ve Direct3D9 Birlikte Çalışması
Direct3D9 içeriği bir Windows Presentation Foundation (WPF) uygulamasında içerebilir. Bu konuda, verimli bir şekilde WPF ile birlikte çalışır, böylece Direct3D9 içeriği oluşturma işlemini açıklar.  
  
> [!NOTE]
>  WPF'de Direct3D9 içeriği kullanırken, ayrıca performans hakkında düşünmeniz gerekir. Performans için en iyi duruma getirme hakkında daha fazla bilgi için bkz. [Direct3D9 ve WPF birlikte çalışabilirlik için başarım düşünceleri](performance-considerations-for-direct3d9-and-wpf-interoperability.md).  
  
## <a name="display-buffers"></a>Arabellekleri görüntüleme  
 <xref:System.Windows.Interop.D3DImage> Sınıfı olarak adlandırılan iki görüntü arabelleğini yöneten *arka arabellek* ve *ön arabellek*. Geri arabelleği Direct3D9 yüzeyiniz olur. Arka arabellek değişiklikleri kopyalanır ön arabelleğe çağırdığınızda <xref:System.Windows.Interop.D3DImage.Unlock%2A> yöntemi.  
  
 Geri arabelleği ve ön arabellek arasındaki ilişki aşağıda gösterilmiştir.  
  
 ![D3DImage görüntü arabellekleri](./media/d3dimage-buffers.png "D3DImage_buffers")  
  
## <a name="direct3d9-device-creation"></a>Direct3D9 cihaz oluşturma  
 Direct3D9 içeriğini işlemek için Direct3D9 cihaz oluşturmanız gerekir. Bir cihaz oluşturmak için kullanabileceğiniz iki Direct3D9 nesneler `IDirect3D9` ve `IDirect3D9Ex`. Oluşturmak için bu nesneleri kullanmaya `IDirect3DDevice9` ve `IDirect3DDevice9Ex` cihazlar, sırasıyla.  
  
 Aşağıdaki yöntemlerden birini çağırarak bir cihaz oluşturun.  
  
-   `IDirect3D9 * Direct3DCreate9(UINT SDKVersion);`  
  
-   `HRESULT Direct3DCreate9Ex(UINT SDKVersion, IDirect3D9Ex **ppD3D);`  
  
 Windows Vista veya sonraki bir işletim sistemi, kullanın `Direct3DCreate9Ex` Windows görüntü sürücü modeli (WDDM) kullanacak şekilde yapılandırılmış bir görüntü ile yöntemi. Kullanım `Direct3DCreate9` herhangi bir platformda yöntemi.  
  
### <a name="availability-of-the-direct3dcreate9ex-method"></a>Kullanılabilirlik Direct3DCreate9Ex yöntemi  
 D3d9.dll sahip `Direct3DCreate9Ex` yöntemi yalnızca Windows Vista veya sonraki bir işletim sistemi. Windows XP işlevi doğrudan bağlantı varsa, uygulama yüklemesi başarısız olur. Belirlemek için olup olmadığını `Direct3DCreate9Ex` yöntemi desteklenir, DLL'yi ve proc adresine bakın. Aşağıdaki kod, test etmek gösterilmektedir `Direct3DCreate9Ex` yöntemi. Tam kod örneği için bkz: [izlenecek yol: WPF'de barındırmak için Direct3D9 içeriği oluşturma](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_EnsureD3DObjects](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_ensured3dobjects)]  
  
### <a name="hwnd-creation"></a>HWND oluşturma  
 Bir cihaz oluşturmak için bir HWND gerekir. Genel olarak bir işlevsiz bir HWND Direct3D9 kullanmak için oluşturun. Aşağıdaki kod örneği işlevsiz bir HWND oluşturma işlemini gösterir.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_EnsureHWND](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_ensurehwnd)]  
  
### <a name="present-parameters"></a>Mevcut Parametreler  
 Bir cihaz oluşturmak için de gerekir bir `D3DPRESENT_PARAMETERS` yapısı, ancak yalnızca birkaç parametre önemlidir. Bu parametreler, bellek Ayak izi en aza indirmek için seçilir.  
  
 Ayarlama `BackBufferHeight` ve `BackBufferWidth` alanlarını 1. Bunları 0 olarak ayarlanması bunları HWND boyutları için ayarlanacak neden olur.  
  
 Her zaman `D3DCREATE_MULTITHREADED` ve `D3DCREATE_FPU_PRESERVE` önlemek için bayrakları Direct3D9 ve Direct3D9 FPU ayarlarını değiştirmesini önlemek için kullanılan bellek bozulmasını.  
  
 Aşağıdaki kod nasıl başlatılacağını gösterir `D3DPRESENT_PARAMETERS` yapısı.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#Renderer_Init](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderer_init)]  
  
## <a name="creating-the-back-buffer-render-target"></a>Arka arabellek işleme hedefi oluşturma  
 Direct3D9 içeriği görüntülemek için bir <xref:System.Windows.Interop.D3DImage>, Direct3D9 surface oluşturup çağırarak atarsanız <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> yöntemi.  
  
### <a name="verifying-adapter-support"></a>Bağdaştırıcı desteğini doğrulanıyor  
 Bir yüzeyi oluşturmadan önce tüm bağdaştırıcıları ihtiyaç duyduğunuz yüzey özelliklerini desteklediğini doğrulayın. Okno WPF yalnızca bir bağdaştırıcıya işleme bile herhangi bir bağdaştırıcı sistemde görüntülenebilir. Her zaman çok bağdaştırıcısı yapılandırmalarının işleme Direct3D9 kod yazmanız gerekir ve WPF yüzey kullanılabilir bağdaştırıcıları arasında taşınmasını gerektirecek için desteği tüm bağdaştırıcıların denetlemeniz gerekir.  
  
 Aşağıdaki kod örneği için Direct3D9 sistemdeki tüm bağdaştırıcılarını destekleyen nasıl kontrol edileceğini gösterir.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_TestSurfaceSettings](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_testsurfacesettings)]  
  
### <a name="creating-the-surface"></a>Surface'ı oluşturma  
 Bir yüzeyi oluşturmadan önce cihaz özelliklerini hedef işletim sistemi iyi bir performans desteklediğini doğrulayın. Daha fazla bilgi için [Direct3D9 ve WPF birlikte çalışabilirlik için başarım düşünceleri](performance-considerations-for-direct3d9-and-wpf-interoperability.md).  
  
 Cihaz özellikleri doğrulandıktan sonra surface oluşturabilirsiniz. Aşağıdaki kod örneği, işleme hedefi oluşturma işlemini gösterir.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#Renderer_CreateSurface](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderer_createsurface)]  
  
### <a name="wddm"></a>WDDM  
 Windows Vista ve WDDM kullanmak üzere yapılandırılmış, sonraki işletim sistemlerinde işleme hedef dokusu oluşturmak ve düzeyi 0 yüzeyine geçirmek <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> yöntemi. Bu yaklaşım, Windows XP'de, çünkü kilitlenebilir işleme hedef dokusu oluşturulamıyor ve performansı düşecektir önerilmez.  
  
## <a name="handling-device-state"></a>İşleme cihaz durumu  
 <xref:System.Windows.Interop.D3DImage> Sınıfı olarak adlandırılan iki görüntü arabelleğini yöneten *arka arabellek* ve *ön arabellek*. Geri arabelleği, Direct3D yüzeyidir.  Arka arabellek değişiklikleri kopyalanır ön arabelleğe çağırdığınızda <xref:System.Windows.Interop.D3DImage.Unlock%2A> bunu görüntüleyen donanımda yöntemi. Bazen, ön arabellek kullanılamaz duruma gelir. Bu kullanılabilirlik eksikliği, ekran kilitleme, tam ekran özel Direct3D uygulamalar, kullanıcı değiştirme veya diğer sistem etkinlikleri tarafından kaynaklanabilir. Bu durumda, WPF uygulamanızı işleyerek bildirilir <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> olay.  Uygulamanızı kullanılamaz hale ön arabellek nasıl yanıt vereceğini WPF yazılımla işleme dönmesi için etkinleştirilip etkinleştirilmediği üzerinde bağlıdır. <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> WPF yazılımla işleme geri döner olup olmadığını belirten bir parametre alan bir aşırı yükleme yöntemi vardır.  
  
 Çağırdığınızda <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%29> aşırı yükleme veya çağrı <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%2CSystem.Boolean%29> aşırı yüklemesine `enableSoftwareFallback` parametresini `false`, işleme sistemi geri arabelleği kendi bir referansı ön arabellek kullanılamaz duruma ve bir şey olduğunda serbest bırakır görüntülenir. Ön arabellek yeniden kullanılabilir olduğunda, işleme sistemi başlatır <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> WPF uygulamanızı bildirmek üzere olay.  Bir olay işleyicisi için oluşturabileceğiniz <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> işleme geçerli bir Direct3D yüzeyi ile yeniden başlatmayı, olay. İşleme yeniden başlatmak için çağırmalıdır <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>.  
  
 Çağırdığınızda <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%2CSystem.Boolean%29> aşırı yüklemesine `enableSoftwareFallback` parametresini `true`, çağırmaya gerek bu nedenle ön arabellek kullanılamaz hale geldiğinde, başvuru geri arabelleği işleme sistemi korur <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> olduğunda ön arabellek yeniden kullanılabilir.  
  
 Yazılımla işleme etkin olduğunda, burada kullanıcı cihazının kullanılamaz duruma gelirse ama işleme sistemi Direct3D yüzeyine bir başvuru tutan durumlar olabilir. Direct3D9 aygıtının kullanılabilir olup olmadığını denetlemek için çağrı `TestCooperativeLevel` yöntemi. Direct3D9Ex cihazları çağrı denetlenecek `CheckDeviceState` yöntemi, çünkü `TestCooperativeLevel` yöntemi kullanım dışıdır ve her zaman başarılı döndürür. Kullanıcı cihazı kullanılamaz duruma gelmişse, çağrı <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> geri arabelleği WPF'nin başvuru serbest bırakmak için.  Cihazınızı sıfırlamanız gerekirse, çağrı <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> ile `backBuffer` parametresini `null`ve sonra çağrı <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> ile yeniden `backBuffer` geçerli bir Direct3D yüzeyine ayarlayın.  
  
 Çağrı `Reset` çok bağdaştırıcı desteğini uygularsanız, geçersiz bir CİHAZDAN kurtarmak için yöntemi. Aksi takdirde tüm Direct3D9 arabirimleri Yayınla ve bunları tümüyle yeniden oluşturun. Bağdaştırıcı düzeni değiştiyse, değişiklikten önce oluşturulan Direct3D9 nesneleri güncelleştirilmez.  
  
## <a name="handling-resizing"></a>Yeniden boyutlandırmayı işleme  
 Varsa bir <xref:System.Windows.Interop.D3DImage> görüntülenen yerel boyutu dışındaki bir çözünürlükte, geçerli göre ölçeklendirilir <xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A>dışında <xref:System.Windows.Media.Effects.SamplingMode.Bilinear> için yerine <xref:System.Windows.Media.BitmapScalingMode.Fant>.  
  
 Daha yüksek güvenilirliğe sahip ihtiyacınız varsa, yeni bir oluşturmalısınız yüzey kapsayıcı <xref:System.Windows.Interop.D3DImage> boyutunu değiştirir.  
  
 Yeniden boyutlandırmayı işlemek için üç olası yaklaşım vardır.  
  
-   Düzen sisteme katılan ve boyutu değiştiğinde yeni bir yüzey oluşturur. Tüketebilir veya video belleği parçası olduğundan, çok fazla yüzeyler oluşturmayın.  
  
-   Yeni yüzey oluşturmak için sabit bir süre için yeniden boyutlandır olayını olana kadar bekleyin.  
  
-   Oluşturma bir <xref:System.Windows.Threading.DispatcherTimer> kapsayıcı boyutları saniyede birkaç kez denetler.  
  
## <a name="multi-monitor-optimization"></a>Çoklu monitör en iyi duruma getirme  
 Önemli ölçüde indirimli performans işleme sistemi hareket ettiğinde sonuçlanabilir bir <xref:System.Windows.Interop.D3DImage> başka bir monitöre.  
  
 WDDM üzerinde aynı video monitör olduğu sürece kart kullandığınızda `Direct3DCreate9Ex`, hiçbir performansta düşüş yoktur. Performans izleyicileri ayrı video kartlarında ise azaltılır. Windows XP'de, her zaman performans küçültülür.  
  
 Zaman <xref:System.Windows.Interop.D3DImage> karşılık gelen bağdaştırıcıda iyi bir performans geri yüklemek için yeni bir yüzey oluşturabilir, başka bir monitöre taşır.  
  
 Performans cezasını önlemek için özellikle çok izleme çalışması için kod yazın. Aşağıdaki liste, çoklu monitör kod yazmak için bir yol gösterir.  
  
1. Noktasını bulun <xref:System.Windows.Interop.D3DImage> ile ekran alanında `Visual.ProjectToScreen` yöntemi.  
  
2. Kullanım `MonitorFromPoint` GDI yöntemi noktayı görüntüleyen izleme bulunamadı.  
  
3. Kullanım `IDirect3D9::GetAdapterMonitor` izleme hangi Direct3D9 Bağdaştırıcı bulunamadı yöntemi açıktır.  
  
4. Bağdaştırıcı bağdaştırıcısı geri arabelleği ile aynı değilse, yeni bir arka arabellek yeni izleyicide oluşturun ve atayın <xref:System.Windows.Interop.D3DImage> arka arabellek.  
  
> [!NOTE]
>  Varsa <xref:System.Windows.Interop.D3DImage> yayılan izleyiciler, performans söz konusu olduğunda WDDM dışında yavaş olacaktır ve `IDirect3D9Ex` aynı bağdaştırıcısında. Bu durumda performansını artırmak için hiçbir yolu yoktur.  
  
 Aşağıdaki kod örneği, geçerli izlemenin nasıl gösterir.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_SetAdapter](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_setadapter)]  
  
 İzleyici güncelleştirme olduğunda <xref:System.Windows.Interop.D3DImage> kapsayıcının boyutu ve konumu değiştiğinde veya güncelleştirme İzleyicisi'ni kullanarak bir `DispatcherTimer` saniyede bir birkaç kez güncelleştirir.  
  
## <a name="wpf-software-rendering"></a>WPF yazılımla işleme  
 WPF yazılım aşağıdaki durumlarda kullanıcı Arabirimi iş parçacığında zaman uyumlu olarak işler.  
  
-   Yazdırma  
  
-   <xref:System.Windows.Media.Effects.BitmapEffect>  
  
-   <xref:System.Windows.Media.Imaging.RenderTargetBitmap>  
  
 Bunlardan biri oluştuğunda, işleme sistemi çağırır <xref:System.Windows.Interop.D3DImage.CopyBackBuffer%2A> yazılıma donanım arabellek kopyalamak için yöntemi. Varsayılan Uygulama çağrıları `GetRenderTargetData` yüzeyinizi yöntemiyle. Bu çağrı Kilitle/Kilidini desenin dışında oluştuğu için başarısız olabilir. Bu durumda, `CopyBackBuffer` yöntemi döndürür `null` ve resim görüntülenir.  
  
 Geçersiz kılabilirsiniz <xref:System.Windows.Interop.D3DImage.CopyBackBuffer%2A> yöntemini temel uygulamayı çağırması ve döndürürse `null`, yer tutucu döndürebilir <xref:System.Windows.Media.Imaging.BitmapSource>.  
  
 Taban uygulamasını çağırmak yerine kendi yazılımla işleme de uygulayabilirsiniz.  
  
> [!NOTE]
>  WPF yazılımlarında, tamamen işliyorsa <xref:System.Windows.Interop.D3DImage> WPF ön arabellek sahip olmadığından gösterilmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Interop.D3DImage>
- [Direct3D9 ve WPF Birlikte Çalışabilirliği için Performans ile İlgili Önemli Noktalar](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
- [İzlenecek yol: WPF'de barındırmak için Direct3D9 içeriği oluşturma](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)
- [İzlenecek yol: WPF'de Direct3D9 içeriği barındırma](walkthrough-hosting-direct3d9-content-in-wpf.md)
