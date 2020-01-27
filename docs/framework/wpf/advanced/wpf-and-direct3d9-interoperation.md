---
title: WPF ve Direct3D9 birlikte çalışması
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- WPF [WPF], creating Direct3D9 content
- Direct3D9 [WPF interoperability], creating Direct3D9 content
ms.assetid: 1b14b823-69c4-4e8d-99e4-f6dade58f89a
ms.openlocfilehash: 9ec83c48052e1ef29bb91a6b40b7c76f671bb99f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735187"
---
# <a name="wpf-and-direct3d9-interoperation"></a>WPF ve Direct3D9 Birlikte Çalışması
Direct3D9 içeriğini bir Windows Presentation Foundation (WPF) uygulamasına ekleyebilirsiniz. Bu konuda, Direct3D9 içeriğinin WPF ile verimli bir şekilde birlikte çalışması için nasıl oluşturulacağı açıklanmaktadır.  
  
> [!NOTE]
> WPF 'te Direct3D9 İçeriği kullanırken performans hakkında da düşünmeniz gerekir. Performansı iyileştirmek hakkında daha fazla bilgi için bkz. [Direct3D9 ve WPF birlikte çalışabilirliği Için performans konuları](performance-considerations-for-direct3d9-and-wpf-interoperability.md).  
  
## <a name="display-buffers"></a>Ara bellek görüntüle  
 <xref:System.Windows.Interop.D3DImage> sınıfı, *geri arabellek* ve *ön arabellek*olarak adlandırılan iki görüntüleme arabelleğini yönetir. Arka arabellek, Direct3D9 yüzeyiniz. Geri arabellek değişiklikleri, <xref:System.Windows.Interop.D3DImage.Unlock%2A> yöntemini çağırdığınızda ön arabelleğe doğru kopyalanır.  
  
 Aşağıdaki çizimde, arka arabelleğin ve ön arabelleğin arasındaki ilişki gösterilmektedir.  
  
 ![D3DImage ekran arabellekleri](./media/d3dimage-buffers.png "D3DImage_buffers")  
  
## <a name="direct3d9-device-creation"></a>Direct3D9 cihaz oluşturma  
 Direct3D9 içeriğini işlemek için bir Direct3D9 cihazı oluşturmanız gerekir. Bir cihaz oluşturmak için kullanabileceğiniz iki Direct3D9 nesnesi vardır, `IDirect3D9` ve `IDirect3D9Ex`. Sırasıyla `IDirect3DDevice9` ve `IDirect3DDevice9Ex` cihazları oluşturmak için bu nesneleri kullanın.  
  
 Aşağıdaki yöntemlerden birini çağırarak bir cihaz oluşturun.  
  
- `IDirect3D9 * Direct3DCreate9(UINT SDKVersion);`  
  
- `HRESULT Direct3DCreate9Ex(UINT SDKVersion, IDirect3D9Ex **ppD3D);`  
  
 Windows Vista veya sonraki işletim sistemlerinde, Windows görüntüleme sürücüsü modelini (WDDM) kullanmak üzere yapılandırılmış bir ekran ile `Direct3DCreate9Ex` yöntemini kullanın. Diğer tüm platformlarda `Direct3DCreate9` yöntemini kullanın.  
  
### <a name="availability-of-the-direct3dcreate9ex-method"></a>Direct3DCreate9Ex yönteminin kullanılabilirliği  
 D3d9. dll ' nin yalnızca Windows Vista veya sonraki işletim sistemlerinde `Direct3DCreate9Ex` yöntemi vardır. Windows XP 'de işlevi doğrudan bağlarsanız, uygulamanız yükleme başarısız olur. `Direct3DCreate9Ex` yönteminin desteklenip desteklenmediğini anlamak için DLL 'yi yükleyin ve proc adresini bulun. Aşağıdaki kod `Direct3DCreate9Ex` yöntemi için nasıl test yapılacağını gösterir. Tam kod örneği için bkz. [Izlenecek yol: WPF 'de barındırmak Için Direct3D9 Içeriği oluşturma](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_EnsureD3DObjects](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_ensured3dobjects)]  
  
### <a name="hwnd-creation"></a>HWND oluşturma  
 Bir cihaz oluşturmak için bir HWND gerekir. Genel olarak, Direct3D9 için kullanmak üzere kukla bir HWND oluşturursunuz. Aşağıdaki kod örneği, bir kukla HWND oluşturmayı gösterir.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_EnsureHWND](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_ensurehwnd)]  
  
### <a name="present-parameters"></a>Mevcut Parametreler  
 Bir cihaz oluşturmak `D3DPRESENT_PARAMETERS` yapısını da gerektirir, ancak yalnızca birkaç parametre önemlidir. Bu parametreler, bellek parmak izini en aza indirmek için seçilir.  
  
 `BackBufferHeight` ve `BackBufferWidth` alanlarını 1 olarak ayarlayın. Bunların 0 olarak ayarlanması, HWND 'nin boyutlarına ayarlanmasına neden olur.  
  
 Direct3D9 tarafından kullanılan belleğin bozulmasını engellemek ve Direct3D9 'ın FPU ayarlarını değiştirmesini engellemek için `D3DCREATE_MULTITHREADED` ve `D3DCREATE_FPU_PRESERVE` bayraklarını her zaman ayarlayın.  
  
 Aşağıdaki kod `D3DPRESENT_PARAMETERS` yapının nasıl başlatılacağını gösterir.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#Renderer_Init](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderer_init)]  
  
## <a name="creating-the-back-buffer-render-target"></a>Arka arabellek Işleme hedefi oluşturuluyor  
 Direct3D9 içeriğini bir <xref:System.Windows.Interop.D3DImage>göstermek için, bir Direct3D9 yüzeyi oluşturup <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> yöntemini çağırarak atayabilirsiniz.  
  
### <a name="verifying-adapter-support"></a>Bağdaştırıcı desteği doğrulanıyor  
 Bir yüzey oluşturmadan önce, tüm bağdaştırıcıların gereken yüzey özelliklerini desteklediğini doğrulayın. Yalnızca bir bağdaştırıcıya İşleseniz bile, WPF penceresi sistemdeki herhangi bir bağdaştırıcıda görüntülenebilir. Birden çok bağdaştırıcılı yapılandırmayı işleyen her zaman Direct3D9 kodu yazmanız gerekir ve WPF, kullanılabilir bağdaştırıcılar arasında yüzeyi taşıyabileceğinden, destek için tüm bağdaştırıcıları denetlemeniz gerekir.  
  
 Aşağıdaki kod örneğinde, Direct3D9 desteği için sistemdeki tüm bağdaştırıcıların nasıl kontrol yapılacağı gösterilmektedir.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_TestSurfaceSettings](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_testsurfacesettings)]  
  
### <a name="creating-the-surface"></a>Yüzey oluşturma  
 Bir yüzey oluşturmadan önce, cihaz yeteneklerinin hedef işletim sisteminde iyi performansı desteklediğini doğrulayın. Daha fazla bilgi için bkz. [Direct3D9 ve WPF birlikte çalışabilirliği Için performans konuları](performance-considerations-for-direct3d9-and-wpf-interoperability.md).  
  
 Cihaz yeteneklerini doğruladıysanız yüzeyi oluşturabilirsiniz. Aşağıdaki kod örneği, oluşturma hedefinin nasıl oluşturulacağını göstermektedir.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#Renderer_CreateSurface](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderer_createsurface)]  
  
### <a name="wddm"></a>'Den  
 WDDM 'yi kullanmak üzere yapılandırılmış Windows Vista ve sonraki işletim sistemlerinde, işleme hedefi dokusu oluşturabilir ve düzey 0 yüzeyini <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> metoduna geçirebilirsiniz. Bu yaklaşım Windows XP 'de önerilmez, çünkü bir kilitlenebilir işleme hedefi dokusu oluşturamazsınız ve performans azaltılabilir.  
  
## <a name="handling-device-state"></a>Cihaz durumunu işleme  
 <xref:System.Windows.Interop.D3DImage> sınıfı, *geri arabellek* ve *ön arabellek*olarak adlandırılan iki görüntüleme arabelleğini yönetir. Arka arabellek Direct3D yüzeyiniz.  Arka arabelleğin değişiklikleri, donanımda görüntülendiği <xref:System.Windows.Interop.D3DImage.Unlock%2A> yöntemini çağırdığınızda ön arabelleğin önüne kopyalanır. Bazen ön arabellek kullanılamaz hale gelir. Bu kullanılabilirlik eksikliği, ekran kilitleme, tam ekran özel Direct3D uygulamaları, Kullanıcı geçişi veya diğer sistem etkinliklerinden kaynaklanıyor olabilir. Bu durumda, WPF uygulamanız <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> olayı işlenerek bilgilendirilir.  Uygulamanızın ön arabelleğin kullanım dışı olmasına nasıl yanıt verdiği, WPF 'nin yazılım işlemeye geri dönebilmesi için etkin olup olmamasına bağlıdır. <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> yönteminde, WPF 'nin yazılım işlemeye geri dönüp çağırmayacağını belirten bir parametre alan aşırı yüklemesi vardır.  
  
 <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%29> aşırı yüklemesini çağırdığınızda veya `enableSoftwareFallback` parametresi `false`olarak ayarlanan <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%2CSystem.Boolean%29> aşırı yüklemeyi çağırdığınızda, işlem sistemi ön arabellek kullanılamaz olduğunda ve hiçbir şey görüntülenmediğinde, yeniden arabelleği başvurusunu serbest bırakır. Ön arabellek yeniden kullanılabilir olduğunda, işleme sistemi WPF uygulamanıza bildirmek için <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> olayını başlatır.  Geçerli bir Direct3D yüzeyine göre işlemeyi yeniden başlatmak için <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> olayı için bir olay işleyicisi oluşturabilirsiniz. İşlemeyi yeniden başlatmak için <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>çağırmanız gerekir.  
  
 `enableSoftwareFallback` parametresi `true`olarak ayarlanan <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%2CSystem.Boolean%29> aşırı yüklemeyi çağırdığınızda, ön arabellek kullanılamaz hale geldiğinde işleme sistemi başvurusunu geri arabelleğe tutar, bu nedenle ön arabellek yeniden kullanılabilir olduğunda <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> çağrısına gerek yoktur.  
  
 Yazılım işleme etkinleştirildiğinde, Kullanıcı cihazının kullanılamaz hale geldiği, ancak işleme sisteminin Direct3D yüzeyine bir başvuruyu sakladığı durumlar olabilir. Direct3D9 cihazının kullanılamıyor olup olmadığını denetlemek için `TestCooperativeLevel` yöntemini çağırın. Bir Direct3D9Ex cihazlarını denetlemek için `CheckDeviceState` yöntemi çağırın, çünkü `TestCooperativeLevel` yöntemi kullanım dışıdır ve her zaman başarılı olarak döner. Kullanıcı aygıtı kullanılamaz hale gelirse, WPF 'nin geri arabellek başvurusunu serbest bırakmak için <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> çağırın.  Cihazınızı sıfırlamanız gerekiyorsa, `null`olarak ayarlanan `backBuffer` parametresi ile <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> çağırın ve ardından `backBuffer` geçerli bir Direct3D yüzeyine ayarlanmış <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> yeniden çağırın.  
  
 Yalnızca çok bağdaştırıcılı destek uygularsanız, geçersiz bir cihazdan kurtarmak için `Reset` yöntemini çağırın. Aksi takdirde, tüm Direct3D9 arabirimlerini serbest bırakın ve tamamen yeniden oluşturun. Bağdaştırıcı düzeni değiştiyse, değişiklikten önce oluşturulan Direct3D9 nesneleri bu nesneler güncellenmez.  
  
## <a name="handling-resizing"></a>Yeniden boyutlandırmayı işleme  
 Bir <xref:System.Windows.Interop.D3DImage> yerel boyutundan farklı bir çözünürlükte görüntüleniyorsa, <xref:System.Windows.Media.Effects.SamplingMode.Bilinear> <xref:System.Windows.Media.BitmapScalingMode.Fant>yerine, geçerli <xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A>göre ölçeklendirilir.  
  
 Daha yüksek uygunluğa ihtiyacınız varsa <xref:System.Windows.Interop.D3DImage> kapsayıcısı boyutunu değiştirdiğinde yeni bir yüzey oluşturmanız gerekir.  
  
 Yeniden boyutlandırmayı işlemek için üç olası yaklaşım vardır.  
  
- Düzen sistemine katılın ve boyut değiştiğinde yeni bir yüzey oluşturun. Video belleğini tüketebilir veya parçalamayabilmeniz için çok fazla yüzey oluşturmayın.  
  
- Yeni yüzeyi oluşturmak için sabit bir süre için yeniden boyutlandırma olayı gerçekleşene kadar bekleyin.  
  
- Saniye başına kapsayıcı boyutlarını birkaç kez denetleyen bir <xref:System.Windows.Threading.DispatcherTimer> oluşturun.  
  
## <a name="multi-monitor-optimization"></a>Çoklu izleyici Iyileştirmesi  
 İşleme sistemi bir <xref:System.Windows.Interop.D3DImage> başka bir monitöre taşırken performansı önemli ölçüde düşürür.  
  
 WDDM 'de, izleyiciler aynı video kartında olduğu ve `Direct3DCreate9Ex`kullandığınız sürece performansta bir azaltma yoktur. İzleyiciler ayrı video kartlarında ise, performans azalır. Windows XP 'de, performans her zaman azalır.  
  
 <xref:System.Windows.Interop.D3DImage> başka bir monitöre taşınırsa, iyi performansı geri yüklemek için ilgili bağdaştırıcıda yeni bir yüzey oluşturabilirsiniz.  
  
 Performans cezasından kaçınmak için, özellikle birden çok monitör örneğine kod yazın. Aşağıdaki listede, çok monitörle kod yazmanın bir yolu gösterilmektedir.  
  
1. `Visual.ProjectToScreen` yöntemi ile ekran alanındaki <xref:System.Windows.Interop.D3DImage> bir nokta bulun.  
  
2. Noktayı görüntüleyen izleyiciyi bulmak için `MonitorFromPoint` GDI yöntemini kullanın.  
  
3. İzleyicinin hangi Direct3D9 bağdaştırıcısı üzerinde olduğunu bulmak için `IDirect3D9::GetAdapterMonitor` yöntemini kullanın.  
  
4. Bağdaştırıcı, arka arabellekle bağdaştırıcı ile aynı değilse, yeni monitörde yeni bir geri arabellek oluşturun ve yeniden <xref:System.Windows.Interop.D3DImage> geri arabelleğe atayın.  
  
> [!NOTE]
> <xref:System.Windows.Interop.D3DImage> kuruluşunda, WDDM ve `IDirect3D9Ex` aynı bağdaştırıcı üzerinde olması dışında, performans yavaş olur. Bu durumda performansı geliştirmenin bir yolu yoktur.  
  
 Aşağıdaki kod örneği, geçerli izleyicinin nasıl bulunacağını gösterir.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_SetAdapter](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_setadapter)]  
  
 <xref:System.Windows.Interop.D3DImage> kapsayıcısının boyutu veya konumu değiştiğinde izleyiciyi güncelleştirin veya saniye başına birkaç kez güncelleştiren bir `DispatcherTimer` kullanarak izleyiciyi güncelleştirin.  
  
## <a name="wpf-software-rendering"></a>WPF yazılım Işleme  
 WPF, aşağıdaki durumlarda yazılımda Kullanıcı arabirimi iş parçacığında zaman uyumlu olarak işler.  
  
- Yazdırma  
  
- <xref:System.Windows.Media.Effects.BitmapEffect>  
  
- <xref:System.Windows.Media.Imaging.RenderTargetBitmap>  
  
 Bu durumlardan biri gerçekleştiğinde, işleme sistemi donanım arabelleğini yazılıma kopyalamak için <xref:System.Windows.Interop.D3DImage.CopyBackBuffer%2A> yöntemini çağırır. Varsayılan uygulama `GetRenderTargetData` yöntemini yüzeyiniz ile çağırır. Bu çağrı kilit/kilit açma deseninin dışında gerçekleştiğinden başarısız olabilir. Bu durumda `CopyBackBuffer` yöntemi `null` döndürür ve görüntü gösterilmez.  
  
 <xref:System.Windows.Interop.D3DImage.CopyBackBuffer%2A> yöntemi geçersiz kılabilir, temel uygulamayı çağırabilir ve `null`döndürürse, bir yer tutucu <xref:System.Windows.Media.Imaging.BitmapSource>döndürebilirsiniz.  
  
 Temel uygulamayı çağırmak yerine kendi yazılım işlelerinizi de uygulayabilirsiniz.  
  
> [!NOTE]
> WPF tamamen yazılımda işliyorsa, WPF 'in ön arabelleği olmadığından <xref:System.Windows.Interop.D3DImage> gösterilmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Interop.D3DImage>
- [Direct3D9 ve WPF Birlikte Çalışabilirliği için Performans ile İlgili Önemli Noktalar](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
- [İzlenecek yol: WPF'de Barındırmak için Direct3D9 İçeriği Oluşturma](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)
- [İzlenecek yol: WPF'de Direct3D9 İçeriği Barındırma](walkthrough-hosting-direct3d9-content-in-wpf.md)
