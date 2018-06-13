---
title: WPF ve Direct3D9 Birlikte Çalışması
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- WPF [WPF], creating Direct3D9 content
- Direct3D9 [WPF interoperability], creating Direct3D9 content
ms.assetid: 1b14b823-69c4-4e8d-99e4-f6dade58f89a
ms.openlocfilehash: a66f37e26d8d86e29e81161ea4585737140441ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549441"
---
# <a name="wpf-and-direct3d9-interoperation"></a>WPF ve Direct3D9 Birlikte Çalışması
Bir Windows Presentation Foundation (WPF) uygulamasında Direct3D9 içeriği içerebilir. Bu konu, böylece verimli bir şekilde WPF ile birlikte çalışır Direct3D9 içeriği oluşturmayı açıklar.  
  
> [!NOTE]
>  Direct3D9 içeriği WPF içinde kullanırken, ayrıca performansı hakkında düşünmek gerekir. Performans için en iyi duruma getirme hakkında daha fazla bilgi için bkz: [Direct3D9 ve WPF birlikte çalışabilirlik için başarım düşünceleri](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md).  
  
## <a name="display-buffers"></a>Arabellekleri görüntüleme  
 <xref:System.Windows.Interop.D3DImage> Sınıfı olarak adlandırılan iki görüntü arabelleğini yönetir *geri arabellek* ve *ön arabellek*. Geri arabellek Direct3D9 yüzeyinizi ' dir. Değişiklikleri geri arabellek kopyalanır İleri ön arabellek çağırdığınızda <xref:System.Windows.Interop.D3DImage.Unlock%2A> yöntemi.  
  
 Aşağıdaki çizimde geri arabelleği ve ön arabellek arasındaki ilişkiyi gösterir.  
  
 ![D3DImage görüntü arabellekleri](../../../../docs/framework/wpf/advanced/media/d3dimage-buffers.png "D3DImage_buffers")  
  
## <a name="direct3d9-device-creation"></a>Direct3D9 aygıtı oluşturma  
 Direct3D9 içeriğini işlemek için Direct3D9 aygıtı oluşturmanız gerekir. Bir aygıt oluşturmak için kullanabileceğiniz iki Direct3D9 nesneleri `IDirect3D9` ve `IDirect3D9Ex`. Oluşturmak için bu nesneleri kullanmaya `IDirect3DDevice9` ve `IDirect3DDevice9Ex` aygıtları, sırasıyla.  
  
 Bir aygıt, aşağıdaki yöntemlerden birini çağırarak oluşturun.  
  
-   `IDirect3D9 * Direct3DCreate9(UINT SDKVersion);`  
  
-   `HRESULT Direct3DCreate9Ex(UINT SDKVersion, IDirect3D9Ex **ppD3D);`  
  
 Windows Vista veya sonraki bir işletim sistemi, kullanmak `Direct3DCreate9Ex` Windows görüntü sürücüsü modeli (WDDM) kullanmak üzere yapılandırılmış bir görüntüyle yöntemi. Kullanım `Direct3DCreate9` başka bir platformda yöntemi.  
  
### <a name="availability-of-the-direct3dcreate9ex-method"></a>Direct3DCreate9Ex yönteminin kullanılabilirliği  
 D3d9.dll sahip `Direct3DCreate9Ex` yöntemi yalnızca Windows Vista veya sonraki bir işletim sistemi. Windows XP işlevi doğrudan bağlantı, uygulama yüklemek başarısız olur. Belirlemek için olup olmadığını `Direct3DCreate9Ex` yöntemi desteklenir, DLL yükleyin ve proc adresine bakın. Aşağıdaki kod için test etme gösterir `Direct3DCreate9Ex` yöntemi. Tam kod örneği için bkz: [izlenecek yol: oluşturma Direct3D9 içeriği WPF içinde barındırma](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_EnsureD3DObjects](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_ensured3dobjects)]  
  
### <a name="hwnd-creation"></a>HWND oluşturma  
 Bir aygıt oluşturma HWND gerektirir. Genel olarak, kullanılacak Direct3D9 kukla bir HWND oluşturun. Aşağıdaki kod örneğinde, sahte bir HWND oluşturulacağını gösterir.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_EnsureHWND](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_ensurehwnd)]  
  
### <a name="present-parameters"></a>Mevcut Parametreler  
 Bir aygıt oluşturma da gerektirir bir `D3DPRESENT_PARAMETERS` yapısı, ancak yalnızca birkaç parametre önemlidir. Bu parametreler, bellek alanını en aza indirmek için seçilir.  
  
 Ayarlama `BackBufferHeight` ve `BackBufferWidth` alanlarını 1. 0 olarak ayarlanması bunları HWND boyutları için ayarlanacak neden olur.  
  
 Her zaman `D3DCREATE_MULTITHREADED` ve `D3DCREATE_FPU_PRESERVE` önlemek için bayrakları Direct3D9 FPU ayarlarını değiştirmesini engellemek için ve Direct3D9 tarafından kullanılan bellek bozulmasını.  
  
 Aşağıdaki kod nasıl başlatılacağını gösterir `D3DPRESENT_PARAMETERS` yapısı.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#Renderer_Init](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderer_init)]  
  
## <a name="creating-the-back-buffer-render-target"></a>Geri arabellek işleme hedefi oluşturma  
 İçinde Direct3D9 içeriği görüntülemek için bir <xref:System.Windows.Interop.D3DImage>, Direct3D9 yüzeyi oluşturun ve çağırarak atayın <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> yöntemi.  
  
### <a name="verifying-adapter-support"></a>Bağdaştırıcı desteğini doğrulama  
 Bir yüzey oluşturmadan önce tüm bağdaştırıcıların gereken yüzey özelliklerini desteklediğini doğrulayın. Yalnızca bir bağdaştırıcıya işlemek olsa bile, WPF penceresi sistemde herhangi bir bağdaştırıcı üzerinde görüntülenebilir. Her zaman çoklu bağdaştırıcı yapılandırmalarını işleyen Direct3D9 kod yazmanız gerekir ve WPF yüzey kullanılabilir bağdaştırıcılardan arasında hareket çünkü destek için tüm bağdaştırıcıları denetlemeniz gerekir.  
  
 Aşağıdaki kod örneği, Direct3D9 için sistemdeki tüm bağdaştırıcıları destek denetlemek gösterilmiştir.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_TestSurfaceSettings](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_testsurfacesettings)]  
  
### <a name="creating-the-surface"></a>Yüzey oluşturma  
 Bir yüzey oluşturmadan önce aygıt yeteneklerinin hedef işletim sisteminde iyi bir performans desteklediğini doğrulayın. Daha fazla bilgi için bkz: [Direct3D9 ve WPF birlikte çalışabilirlik için başarım düşünceleri](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md).  
  
 Cihaz özellikleri belirlediğinizde, surface oluşturabilirsiniz. Aşağıdaki kod örneğinde işleme hedefi oluşturulacağını gösterir.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#Renderer_CreateSurface](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderer_createsurface)]  
  
### <a name="wddm"></a>WDDM  
 Windows Vista ve WDDM kullanmak üzere yapılandırılmış, sonraki işletim sistemlerinde işleme hedef dokusu oluşturabilir ve düzey 0 yüzeye geçirebilirsiniz <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> yöntemi. Bu yaklaşım, çünkü kilitlenebilir işleme hedef dokusu oluşturulamıyor ve performansı düşecektir Windows XP'de önerilmez.  
  
## <a name="handling-device-state"></a>Aygıt durumunu işleme  
 <xref:System.Windows.Interop.D3DImage> Sınıfı olarak adlandırılan iki görüntü arabelleğini yönetir *geri arabellek* ve *ön arabellek*. Geri arabellek Direct3D yüzeyinizi ' dir.  Değişiklikleri geri arabellek kopyalanır İleri ön arabellek çağırdığınızda <xref:System.Windows.Interop.D3DImage.Unlock%2A> burada da görüntülenir donanımda yöntemi. Bazen ön arabellek kullanılamaz duruma gelir. Bu kullanılabilirlik eksikliği ekran kilitleme, tam ekran özel Direct3D uygulamaları, kullanıcı değiştirme veya diğer sistem etkinlikler tarafından neden olabilir. Bu durumda, WPF uygulaması işleyerek bildirilir <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> olay.  Uygulamanızı kullanılamaz hale ön arabellek nasıl yanıt vereceğini WPF yazılım işlemeye geri dönmesi için etkinleştirilip etkinleştirilmediği üzerinde bağlıdır. <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> Yöntemi WPF yazılım işlemeye geri döner olup olmadığını belirten bir parametre alan aşırı sahiptir.  
  
 Çağırdığınızda <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%29> aşırı yükleme veya arama <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%2CSystem.Boolean%29> ile aşırı `enableSoftwareFallback` parametre kümesine `false`, ön arabellek kullanılamaz duruma ve bir şey olduğunda kendi başvuru geri arabellek işleme sistemi serbest bırakır görüntülenir. Ön arabellek yeniden kullanılabilir duruma geldiğinde, işleme sistemi başlatır <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> WPF uygulamanızı bildirmek için olay.  Bir olay işleyicisi için oluşturabileceğiniz <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> olay işleme yeniden geçerli Direct3D yüzeyi ile yeniden başlatın. İşleme yeniden başlatmak için çağırmalısınız <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>.  
  
 Çağırdığınızda <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%2CSystem.Boolean%29> ile aşırı `enableSoftwareFallback` parametre kümesine `true`, böylece çağırmak için gerekli ön arabellek kullanılamaz hale geldiğinde, başvuru geri arabellek işleme sistemi korur <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> olduğunda ön arabellek yeniden kullanılabilir.  
  
 Yazılım işleme etkinleştirildiğinde, burada kullanıcının aygıtına kullanılamaz duruma gelir ancak Direct3D yüzeyini başvuru işleme sistemi korur durumlar olabilir. Direct3D9 aygıtı kullanılabilir olup olmadığını denetlemek için çağrı `TestCooperativeLevel` yöntemi. Direct3D9Ex aygıtları çağrı denetlemek için `CheckDeviceState` yöntemi, çünkü `TestCooperativeLevel` yöntemi kullanım dışıdır ve her zaman başarı döndürür. Kullanıcı cihazı kullanılamaz hale geldi çağırır <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> WPF'in başvuru geri arabellek serbest bırakmak için.  Cihazınızı sıfırlamanız gerekirse, çağrı <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> ile `backBuffer` parametre kümesine `null`ve ardından arama <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> yeniden `backBuffer` geçerli Direct3D yüzeye ayarlayın.  
  
 Çağrı `Reset` yalnızca çoklu bağdaştırıcı desteğini uyguladığınızda geçersiz bir aygıtı kurtarmak için yöntem. Aksi takdirde, tüm Direct3D9 arabirimlerini yayın ve bunları tümüyle yeniden oluşturun. Bağdaştırıcı düzeni değiştiyse, değişiklikten önce oluşturulan Direct3D9 nesneler güncelleştirilmez.  
  
## <a name="handling-resizing"></a>Yeniden boyutlandırma işleme  
 Varsa bir <xref:System.Windows.Interop.D3DImage> görüntülenir yerel boyutu dışında bir çözünürlükte geçerli göre ölçeklenir <xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A>dışında <xref:System.Windows.Media.Effects.SamplingMode.Bilinear> için yerine <xref:System.Windows.Media.BitmapScalingMode.Fant>.  
  
 Daha yüksek uygunluk gerekiyorsa, yeni bir oluşturmalısınız yüzey kapsayıcısını <xref:System.Windows.Interop.D3DImage> boyutu değişir.  
  
 Yeniden boyutlandırma işlemek için üç olası yaklaşım vardır.  
  
-   Düzen sistemine katılır ve boyutu değiştiğinde yeni bir yüzey oluşturun. Tüketebilir veya video belleği parçalara için çok fazla yüzey oluşturmayın.  
  
-   Bir sabit süre yeni yüzey oluşturmak için yeniden boyutlandır olayını olana kadar bekleyin.  
  
-   Oluşturma bir <xref:System.Windows.Threading.DispatcherTimer> saniyede birkaç kez kapsayıcı boyutlarını denetler.  
  
## <a name="multi-monitor-optimization"></a>Birden çok monitör en iyi duruma getirme  
 Önemli ölçüde azaltılmış performans işleme sistemi taşındığında sonuçlanabilir bir <xref:System.Windows.Interop.D3DImage> başka bir izleme.  
  
 Kart ve WDDM üzerinde aynı video monitörleri olduğu sürece kullanmak `Direct3DCreate9Ex`, performans, hiçbir azalma yoktur. İzleyiciler ayrı video kartlarında varsa, performansı düşürür. Windows XP'de Performans her zaman azalır.  
  
 Zaman <xref:System.Windows.Interop.D3DImage> taşır başka bir izleyici için iyi bir performans geri yüklemek için karşılık gelen bağdaştırıcı üzerinde yeni bir yüzey oluşturabilirsiniz.  
  
 Yaşanan performans sorunları önlemek için özellikle çok İzleyici durum kodunu yazın. Aşağıdaki liste çok İzleyici kodu yazmak için bir yol gösterir.  
  
1.  Noktasını bulun <xref:System.Windows.Interop.D3DImage> ile ekran alanında `Visual.ProjectToScreen` yöntemi.  
  
2.  Kullanım `MonitorFromPoint` noktayı görüntüleyen monitörü bulmak için GDI yöntemi.  
  
3.  Kullanım `IDirect3D9::GetAdapterMonitor` hangi Direct3D9 bağdaştırıcısı İzleyici bulmak için yöntem açıktır.  
  
4.  Bağdaştırıcı bağdaştırıcı geri arabelleği ile aynı değilse, yeni monitör üzerinde yeni bir geri arabellek oluşturun ve ona atayın <xref:System.Windows.Interop.D3DImage> geri arabellek.  
  
> [!NOTE]
>  Varsa <xref:System.Windows.Interop.D3DImage> yayılan izleyiciler, performans durumunda WDDM dışında yavaş olacaktır ve `IDirect3D9Ex` aynı bağdaştırıcısında. Bu durumda performansı artırmak için bir yolu yoktur.  
  
 Aşağıdaki kod örneği, geçerli izleme bulmak gösterilmiştir.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_SetAdapter](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_setadapter)]  
  
 İzleyici güncelleştirme olduğunda <xref:System.Windows.Interop.D3DImage> kapsayıcının boyut ve konum değişiklikleri veya güncelleştirme İzleyicisi'ni kullanarak bir `DispatcherTimer` saniyede bir birkaç kez güncelleştirir.  
  
## <a name="wpf-software-rendering"></a>WPF Software işleme  
 WPF kullanıcı Arabirimi iş parçacığı aşağıdaki durumlarda yazılım üzerinde eşzamanlı olarak işler.  
  
-   Yazdırma  
  
-   <xref:System.Windows.Media.Effects.BitmapEffect>  
  
-   <xref:System.Windows.Media.Imaging.RenderTargetBitmap>  
  
 Bu durumlardan biri gerçekleştiğinde, işleme sistemi çağırır <xref:System.Windows.Interop.D3DImage.CopyBackBuffer%2A> donanım arabelleğini yazılıma kopyalamak için yöntem. Varsayılan Uygulama çağrıları `GetRenderTargetData` yüzeyinizi yöntemiyle. Bu çağrı dışında kilit/Unlock düzeni oluştuğundan başarısız olabilir. Bu durumda, `CopyBackBuffer` yöntemi döndürür `null` ve hiçbir resim görüntülenir.  
  
 Geçersiz kılabilirsiniz <xref:System.Windows.Interop.D3DImage.CopyBackBuffer%2A> yöntemi, temel uygulamayı çağırması ve döndürürse `null`, bir yer tutucu döndürebilir <xref:System.Windows.Media.Imaging.BitmapSource>.  
  
 Temel uygulama çağırmak yerine kendi yazılım işlemenizi de uygulayabilirsiniz.  
  
> [!NOTE]
>  WPF tamamen yazılımda işliyorsa <xref:System.Windows.Interop.D3DImage> WPF ön arabelleğinin olmadığından gösterilmez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Interop.D3DImage>  
 [Direct3D9 ve WPF Birlikte Çalışabilirliği için Performans ile İlgili Önemli Noktalar](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)  
 [İzlenecek yol: WPF'de Barındırmak için Direct3D9 İçeriği Oluşturma](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)  
 [İzlenecek yol: WPF'de Direct3D9 İçeriği Barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)
