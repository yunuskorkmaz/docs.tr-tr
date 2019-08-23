---
title: WPF ve Direct3D9 Birlikte Çalışması
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- WPF [WPF], creating Direct3D9 content
- Direct3D9 [WPF interoperability], creating Direct3D9 content
ms.assetid: 1b14b823-69c4-4e8d-99e4-f6dade58f89a
ms.openlocfilehash: 5fccd49b4f6fa64e5902197423d732ba0b31790e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917431"
---
# <a name="wpf-and-direct3d9-interoperation"></a>WPF ve Direct3D9 Birlikte Çalışması
Direct3D9 içeriğini bir Windows Presentation Foundation (WPF) uygulamasına ekleyebilirsiniz. Bu konuda, Direct3D9 içeriğinin WPF ile verimli bir şekilde birlikte çalışması için nasıl oluşturulacağı açıklanmaktadır.  
  
> [!NOTE]
> WPF 'te Direct3D9 İçeriği kullanırken performans hakkında da düşünmeniz gerekir. Performansı iyileştirmek hakkında daha fazla bilgi için bkz. [Direct3D9 ve WPF birlikte çalışabilirliği Için performans konuları](performance-considerations-for-direct3d9-and-wpf-interoperability.md).  
  
## <a name="display-buffers"></a>Ara bellek görüntüle  
 Sınıfı, *geri arabellek* ve *ön arabellek*olarak adlandırılan iki görüntüleme arabelleğini yönetir. <xref:System.Windows.Interop.D3DImage> Arka arabellek, Direct3D9 yüzeyiniz. Geri arabellek değişiklikleri, <xref:System.Windows.Interop.D3DImage.Unlock%2A> yöntemini çağırdığınızda ön arabelleğe doğru kopyalanır.  
  
 Aşağıdaki çizimde, arka arabelleğin ve ön arabelleğin arasındaki ilişki gösterilmektedir.  
  
 ![D3DImage ekran arabellekleri](./media/d3dimage-buffers.png "D3DImage_buffers")  
  
## <a name="direct3d9-device-creation"></a>Direct3D9 cihaz oluşturma  
 Direct3D9 içeriğini işlemek için bir Direct3D9 cihazı oluşturmanız gerekir. Bir cihaz `IDirect3D9` oluşturmak için kullanabileceğiniz iki Direct3D9 nesnesi vardır ve `IDirect3D9Ex`. Sırasıyla ve `IDirect3DDevice9` `IDirect3DDevice9Ex` cihazları oluşturmak için bu nesneleri kullanın.  
  
 Aşağıdaki yöntemlerden birini çağırarak bir cihaz oluşturun.  
  
- `IDirect3D9 * Direct3DCreate9(UINT SDKVersion);`  
  
- `HRESULT Direct3DCreate9Ex(UINT SDKVersion, IDirect3D9Ex **ppD3D);`  
  
 Windows Vista veya sonraki işletim sistemlerinde, Windows görüntüleme sürücüsü `Direct3DCreate9Ex` modelini (WDDM) kullanmak üzere yapılandırılmış bir ekran ile yöntemini kullanın. `Direct3DCreate9` Yöntemini diğer tüm platformlarda kullanın.  
  
### <a name="availability-of-the-direct3dcreate9ex-method"></a>Direct3DCreate9Ex yönteminin kullanılabilirliği  
 D3d9. dll, yalnızca Windows `Direct3DCreate9Ex` Vista veya sonraki işletim sistemlerinde yöntemi vardır. Windows XP 'de işlevi doğrudan bağlarsanız, uygulamanız yükleme başarısız olur. `Direct3DCreate9Ex` Yöntemin desteklenip desteklenmediğini anlamak için dll 'yi yükleyin ve proc adresini arayın. Aşağıdaki kod `Direct3DCreate9Ex` yöntemi için nasıl test yapılacağını gösterir. Tam kod örneği için bkz [. İzlenecek yol: WPF](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)'de barındırmak için Direct3D9 İçeriği oluşturma.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_EnsureD3DObjects](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_ensured3dobjects)]  
  
### <a name="hwnd-creation"></a>HWND oluşturma  
 Bir cihaz oluşturmak için bir HWND gerekir. Genel olarak, Direct3D9 için kullanmak üzere kukla bir HWND oluşturursunuz. Aşağıdaki kod örneği, bir kukla HWND oluşturmayı gösterir.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_EnsureHWND](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_ensurehwnd)]  
  
### <a name="present-parameters"></a>Mevcut Parametreler  
 Bir cihaz oluşturmak için de bir `D3DPRESENT_PARAMETERS` yapı gerekir, ancak yalnızca birkaç parametre önemlidir. Bu parametreler, bellek parmak izini en aza indirmek için seçilir.  
  
 `BackBufferHeight` Ve`BackBufferWidth` alanlarını 1 olarak ayarlayın. Bunların 0 olarak ayarlanması, HWND 'nin boyutlarına ayarlanmasına neden olur.  
  
 Direct3D9 tarafından kullanılan `D3DCREATE_MULTITHREADED` belleğin `D3DCREATE_FPU_PRESERVE` bozulmasını engellemek ve Direct3D9 'ın FPU ayarlarını değiştirmesini engellemek için her zaman ve bayraklarını ayarlayın.  
  
 Aşağıdaki kod `D3DPRESENT_PARAMETERS` yapının nasıl başlatılacağını gösterir.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#Renderer_Init](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderer_init)]  
  
## <a name="creating-the-back-buffer-render-target"></a>Arka arabellek Işleme hedefi oluşturuluyor  
 Direct3D9 içeriğini bir <xref:System.Windows.Interop.D3DImage>içinde göstermek için bir Direct3D9 yüzeyi oluşturup <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> yöntemini çağırarak atayabilirsiniz.  
  
### <a name="verifying-adapter-support"></a>Bağdaştırıcı desteği doğrulanıyor  
 Bir yüzey oluşturmadan önce, tüm bağdaştırıcıların gereken yüzey özelliklerini desteklediğini doğrulayın. Yalnızca bir bağdaştırıcıya İşleseniz bile, WPF penceresi sistemdeki herhangi bir bağdaştırıcıda görüntülenebilir. Birden çok bağdaştırıcılı yapılandırmayı işleyen her zaman Direct3D9 kodu yazmanız gerekir ve WPF, kullanılabilir bağdaştırıcılar arasında yüzeyi taşıyabileceğinden, destek için tüm bağdaştırıcıları denetlemeniz gerekir.  
  
 Aşağıdaki kod örneğinde, Direct3D9 desteği için sistemdeki tüm bağdaştırıcıların nasıl kontrol yapılacağı gösterilmektedir.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_TestSurfaceSettings](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_testsurfacesettings)]  
  
### <a name="creating-the-surface"></a>Yüzey oluşturma  
 Bir yüzey oluşturmadan önce, cihaz yeteneklerinin hedef işletim sisteminde iyi performansı desteklediğini doğrulayın. Daha fazla bilgi için bkz. [Direct3D9 ve WPF birlikte çalışabilirliği Için performans konuları](performance-considerations-for-direct3d9-and-wpf-interoperability.md).  
  
 Cihaz yeteneklerini doğruladıysanız yüzeyi oluşturabilirsiniz. Aşağıdaki kod örneği, oluşturma hedefinin nasıl oluşturulacağını göstermektedir.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#Renderer_CreateSurface](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderer_createsurface)]  
  
### <a name="wddm"></a>'DEN  
 WDDM 'yi kullanmak üzere yapılandırılmış Windows Vista ve sonraki işletim sistemlerinde, işleme hedefi dokusu oluşturabilir ve düzey 0 yüzeyini <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> yönteme geçirebilirsiniz. Bu yaklaşım Windows XP 'de önerilmez, çünkü bir kilitlenebilir işleme hedefi dokusu oluşturamazsınız ve performans azaltılabilir.  
  
## <a name="handling-device-state"></a>Cihaz durumunu işleme  
 Sınıfı, *geri arabellek* ve *ön arabellek*olarak adlandırılan iki görüntüleme arabelleğini yönetir. <xref:System.Windows.Interop.D3DImage> Arka arabellek Direct3D yüzeyiniz.  Yeniden arabellekte yapılan değişiklikler, <xref:System.Windows.Interop.D3DImage.Unlock%2A> yöntemini çağırdığınızda, donanımda görüntülendiği zaman ön arabelleğe kopyalanır. Bazen ön arabellek kullanılamaz hale gelir. Bu kullanılabilirlik eksikliği, ekran kilitleme, tam ekran özel Direct3D uygulamaları, Kullanıcı geçişi veya diğer sistem etkinliklerinden kaynaklanıyor olabilir. Bu durumda, WPF uygulamanız <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> olay işlenerek bilgilendirilir.  Uygulamanızın ön arabelleğin kullanım dışı olmasına nasıl yanıt verdiği, WPF 'nin yazılım işlemeye geri dönebilmesi için etkin olup olmamasına bağlıdır. Yönteminde <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> , WPF 'nin yazılım işlemeye geri dönüp çağırmayacağını belirten bir parametre alan aşırı yüklemesi vardır.  
  
 <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%29> Aşırı yüklemeyi çağırdığınızda veya `enableSoftwareFallback` parametresi olarak <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%2CSystem.Boolean%29> `false`ayarlanan bir aşırı yüklemeyi çağırdığınızda, ön arabellek kullanılamaz olduğunda ve hiçbir şey olmadığında işleme sistemi başvurusunu geri arabelleğe bırakır görüntülenemeyecek. Ön arabellek yeniden kullanılabilir olduğunda, işleme sistemi, WPF uygulamanıza bildirimde bulunan <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> olayı başlatır.  Geçerli bir Direct3D yüzeyine göre işlemeyi yeniden başlatmak <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> için olay işleyicisi oluşturabilirsiniz. İşlemeyi yeniden başlatmak için çağrısı <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>yapmanız gerekir.  
  
 ' İ ' olarak <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%2CSystem.Boolean%29> `enableSoftwareFallback` `true`ayarlanan parametre ile aşırı yüklemeyi çağırdığınızda, ön arabellek kullanılamaz hale geldiğinde işleme sistemi başvurusunu geri arabelleğe tutar. bu nedenle <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> , önde gelen arabellek yeniden kullanılabilir.  
  
 Yazılım işleme etkinleştirildiğinde, Kullanıcı cihazının kullanılamaz hale geldiği, ancak işleme sisteminin Direct3D yüzeyine bir başvuruyu sakladığı durumlar olabilir. Direct3D9 cihazının kullanılamıyor olup olmadığını denetlemek için `TestCooperativeLevel` yöntemini çağırın. Direct3D9Ex cihazlarını denetlemek için yöntemini çağırın `CheckDeviceState` , `TestCooperativeLevel` çünkü Yöntem kullanım dışıdır ve her zaman başarılı sonucunu döndürür. Kullanıcı aygıtı kullanılamaz hale gelirse, WPF 'nin geri <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> arabellek başvurusunu serbest bırakma çağrısına çağrı yapın.  Cihazınızı sıfırlamanız gerekiyorsa, olarak <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> `null`ayarlanmış `backBuffer` parametresiyle çağırın ve ardından geçerli bir Direct3D yüzeyine ayarla ile `backBuffer` yeniden çağırın <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> .  
  
 Yalnızca çok bağdaştırıcılı destek uygularsanız, geçersiz bir cihazdan kurtarmak için yöntemiçağırın.`Reset` Aksi takdirde, tüm Direct3D9 arabirimlerini serbest bırakın ve tamamen yeniden oluşturun. Bağdaştırıcı düzeni değiştiyse, değişiklikten önce oluşturulan Direct3D9 nesneleri bu nesneler güncellenmez.  
  
## <a name="handling-resizing"></a>Yeniden boyutlandırmayı işleme  
 A, <xref:System.Windows.Interop.D3DImage> yerel boyutundan farklı bir çözünürlükte görüntüleniyorsa, için <xref:System.Windows.Media.BitmapScalingMode.Fant>yerine geçen geçerli <xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A>olan <xref:System.Windows.Media.Effects.SamplingMode.Bilinear> öğesine göre ölçeklendirilir.  
  
 Daha yüksek uygunluğa ihtiyacınız varsa, <xref:System.Windows.Interop.D3DImage> değişiklik boyutu kapsayıcısı olduğunda yeni bir yüzey oluşturmanız gerekir.  
  
 Yeniden boyutlandırmayı işlemek için üç olası yaklaşım vardır.  
  
- Düzen sistemine katılın ve boyut değiştiğinde yeni bir yüzey oluşturun. Video belleğini tüketebilir veya parçalamayabilmeniz için çok fazla yüzey oluşturmayın.  
  
- Yeni yüzeyi oluşturmak için sabit bir süre için yeniden boyutlandırma olayı gerçekleşene kadar bekleyin.  
  
- Saniye başına <xref:System.Windows.Threading.DispatcherTimer> kapsayıcı boyutlarını birkaç kez denetleyen bir oluştur.  
  
## <a name="multi-monitor-optimization"></a>Çoklu izleyici Iyileştirmesi  
 İşleme sistemi bir <xref:System.Windows.Interop.D3DImage> diğer monitöre taşınırsa performansı önemli ölçüde düşürür.  
  
 WDDM 'de, izleyiciler aynı video kartında olduğu ve kullandığınız `Direct3DCreate9Ex`sürece performansta bir azaltma yoktur. İzleyiciler ayrı video kartlarında ise, performans azalır. Windows XP 'de, performans her zaman azalır.  
  
 Başka bir monitöre taşırken, iyi performansı geri yüklemek için ilgili bağdaştırıcıda yeni bir yüzey oluşturabilirsiniz. <xref:System.Windows.Interop.D3DImage>  
  
 Performans cezasından kaçınmak için, özellikle birden çok monitör örneğine kod yazın. Aşağıdaki listede, çok monitörle kod yazmanın bir yolu gösterilmektedir.  
  
1. Yöntemi ile birlikte ekran alanının <xref:System.Windows.Interop.D3DImage> bir noktasını bulun. `Visual.ProjectToScreen`  
  
2. Noktayı görüntüleyen izleyiciyi bulmak için GDIyönteminikullanın.`MonitorFromPoint`  
  
3. İzleyicinin hangi Direct3D9 bağdaştırıcısı üzerinde olduğunu bulmak için yönteminikullanın.`IDirect3D9::GetAdapterMonitor`  
  
4. Bağdaştırıcı, arka arabelleğin bulunduğu bağdaştırıcıyla aynı değilse, yeni monitörde yeni bir geri arabellek oluşturun ve <xref:System.Windows.Interop.D3DImage> geri arabelleğe atayın.  
  
> [!NOTE]
> Kuruluşunda, WDDM ve `IDirect3D9Ex` aynı bağdaştırıcı üzerinde olması dışında, performans yavaş olur. <xref:System.Windows.Interop.D3DImage> Bu durumda performansı geliştirmenin bir yolu yoktur.  
  
 Aşağıdaki kod örneği, geçerli izleyicinin nasıl bulunacağını gösterir.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_SetAdapter](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_setadapter)]  
  
 <xref:System.Windows.Interop.D3DImage> Kapsayıcının boyutu veya konumu değiştiğinde izleyiciyi güncelleştirin veya bir saniyede birkaç kez güncelleştiren bir `DispatcherTimer` güncelleştirme kullanarak izleyiciyi güncelleştirin.  
  
## <a name="wpf-software-rendering"></a>WPF yazılım Işleme  
 WPF, aşağıdaki durumlarda yazılımda Kullanıcı arabirimi iş parçacığında zaman uyumlu olarak işler.  
  
- Yazdırma  
  
- <xref:System.Windows.Media.Effects.BitmapEffect>  
  
- <xref:System.Windows.Media.Imaging.RenderTargetBitmap>  
  
 Bu durumlardan biri gerçekleştiğinde, işleme sistemi donanım arabelleğini yazılıma kopyalamak için <xref:System.Windows.Interop.D3DImage.CopyBackBuffer%2A> yöntemini çağırır. Varsayılan uygulama, yüzeyiniz `GetRenderTargetData` ile yöntemini çağırır. Bu çağrı kilit/kilit açma deseninin dışında gerçekleştiğinden başarısız olabilir. Bu durumda, `CopyBackBuffer` yöntemi döndürür `null` ve görüntü gösterilmez.  
  
 <xref:System.Windows.Interop.D3DImage.CopyBackBuffer%2A> Yöntemi geçersiz kılabilir, temel uygulamayı çağırabilir ve döndürürse `null`, bir yer tutucu <xref:System.Windows.Media.Imaging.BitmapSource>döndürebilirsiniz.  
  
 Temel uygulamayı çağırmak yerine kendi yazılım işlelerinizi de uygulayabilirsiniz.  
  
> [!NOTE]
> WPF, yazılımda tamamen işlenirse, <xref:System.Windows.Interop.D3DImage> WPF 'in ön arabelleği olmadığından gösterilmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Interop.D3DImage>
- [Direct3D9 ve WPF Birlikte Çalışabilirliği için Performans ile İlgili Önemli Noktalar](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
- [İzlenecek yol: WPF 'de barındırmak için Direct3D9 Içeriği oluşturma](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)
- [İzlenecek yol: WPF 'de Direct3D9 Içeriği barındırma](walkthrough-hosting-direct3d9-content-in-wpf.md)
