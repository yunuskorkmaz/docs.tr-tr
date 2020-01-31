---
title: Direct3D9 ve WPF birlikte çalışabilirliği için performans konuları
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- WPF [WPF], Direct3D9 interop performance
- Direct3D9 [WPF interoperability], performance
ms.assetid: ea8baf91-12fe-4b44-ac4d-477110ab14dd
ms.openlocfilehash: 2445732c27d210a41da26303d6a9ce07ef6fcc94
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743936"
---
# <a name="performance-considerations-for-direct3d9-and-wpf-interoperability"></a>Direct3D9 ve WPF Birlikte Çalışabilirliği için Performans ile İlgili Önemli Noktalar
<xref:System.Windows.Interop.D3DImage> sınıfını kullanarak Direct3D9 içeriğini barındırabilirsiniz. Direct3D9 içeriğinin barındırılması uygulamanızın performansını etkileyebilir. Bu konuda, bir Windows Presentation Foundation (WPF) uygulamasında Direct3D9 içeriğini barındırırken performansı iyileştirmek için en iyi yöntemler açıklanmaktadır. Bu en iyi uygulamalar, Windows Vista, Windows XP ve çoklu monitör ekranları kullanırken <xref:System.Windows.Interop.D3DImage> ve en iyi uygulamaları kullanmayı içerir.  
  
> [!NOTE]
> Bu en iyi uygulamaları gösteren kod örnekleri için bkz. [WPF ve Direct3D9 birlikte](wpf-and-direct3d9-interoperation.md)çalışma.  
  
## <a name="use-d3dimage-sparingly"></a>D3DImage gelişigüzel kullanın  
 Bir <xref:System.Windows.Interop.D3DImage> örneğinde barındırılan Direct3D9 İçeriği, saf Direct3D uygulamasında olduğu kadar hızlı işlenir. Yüzeyi kopyalama ve komut arabelleğini Temizleme maliyetli işlemler olabilir. <xref:System.Windows.Interop.D3DImage> örneklerinin sayısı arttıkça, daha fazla boşaltma oluşur ve performans düşer. Bu nedenle <xref:System.Windows.Interop.D3DImage> gelişigüzel bir şekilde kullanmanız gerekir.  
  
## <a name="best-practices-on-windows-vista"></a>Windows Vista 'da en iyi yöntemler  
 Windows görüntü sürücüsü modeli (WDDM) kullanmak üzere yapılandırılmış bir ekran ile Windows Vista 'da en iyi performansı elde etmek için, bir `IDirect3DDevice9Ex` cihazında Direct3D9 yüzeyini oluşturun. Bu, yüzey paylaşımını mümkün bir şekilde sunar. Video kartı Windows Vista 'da `D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES` ve `D3DCAPS2_CANSHARERESOURCE` sürücü yeteneklerini desteklemelidir. Diğer tüm ayarlar, yüzeyin yazılım üzerinden kopyalanmasına neden olur ve bu da performansı önemli ölçüde azaltır.  
  
> [!NOTE]
> Windows Vista, Windows XP görüntü sürücüsü modeli (XDDM) kullanmak üzere yapılandırılmış bir ekran içeriyorsa, bu yüzey, ayarlardan bağımsız olarak her zaman yazılım üzerinden kopyalanır. Doğru ayarlar ve ekran kartıyla, WDDM kullandığınızda Windows Vista 'da daha iyi performans görürsünüz çünkü Surface kopyaları donanımda gerçekleştirilir.  
  
## <a name="best-practices-on-windows-xp"></a>Windows XP 'de en iyi yöntemler  
 Windows XP görüntü sürücüsü modelini (XDDM) kullanan Windows XP 'de en iyi performansı elde etmek için `IDirect3DSurface9::GetDC` yöntemi çağrıldığında doğru şekilde davranan bir kilitlenebilir yüzey oluşturun. Dahili olarak `BitBlt` yöntemi, yüzeyi donanımlardaki cihazlara aktarır. `GetDC` yöntemi her zaman XRGB yüzeyleri üzerinde çalışmaktadır. Ancak, istemci bilgisayar SP3 veya SP2 ile Windows XP çalıştırıyorsa ve istemci Ayrıca katmanlı pencere özelliğine yönelik düzeltme içeriyorsa, bu yöntem yalnızca ARGB yüzeyleri üzerinde çalışır. Video kartı `D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES` sürücü özelliğini desteklemelidir.  
  
 16 bit masaüstü görüntü derinliği performansı önemli ölçüde azaltabilir. 32 bitlik bir masaüstü önerilir.  
  
 Windows Vista ve Windows XP için geliştiriyorsanız, Windows XP 'de performansı test edin. Windows XP 'de video belleği tükenme sorunu. Ayrıca, Windows XP 'deki <xref:System.Windows.Interop.D3DImage>, gerekli bir ekstra video belleği kopyalaması nedeniyle Windows Vista WDDM 'den daha fazla video belleği ve bant genişliği kullanır. Bu nedenle, aynı video donanımı için Windows Vista 'dan Windows XP 'den daha kötüleşme performansı sağlayabilirsiniz.  
  
> [!NOTE]
> Windows XP ve Windows Vista 'da XDDM kullanılabilir; Ancak, WDDM yalnızca Windows Vista 'da kullanılabilir.  
  
## <a name="general-best-practices"></a>Genel En Iyi Yöntemler  
 Cihazı oluştururken `D3DCREATE_MULTITHREADED` oluşturma bayrağını kullanın. Bu, performansı düşürür, ancak WPF işleme sistemi bu cihazdaki yöntemleri başka bir iş parçacığından çağırır. Kilitleme protokolünü doğru şekilde izlediğinizden emin olun, böylece iki iş parçacığı cihaza aynı anda erişemez.  
  
 Bir WPF yönetilen iş parçacığında işleme gerçekleştirilirse, cihazı `D3DCREATE_FPU_PRESERVE` oluşturma bayrağıyla oluşturmanız önemle tavsiye edilir. Bu ayar olmadan, D3D işleme WPF çift duyarlıklı işlemlerinin doğruluğunu azaltabilir ve işleme sorunlarını ortaya çıkarabilir.  
  
 Donanım desteği olmadan pow2 olmayan bir yüzeyi döşemediğiniz veya bir <xref:System.Windows.Media.DrawingBrush> ya da <xref:System.Windows.Interop.D3DImage>içeren <xref:System.Windows.Media.VisualBrush> döşediğiniz müddetçe <xref:System.Windows.Interop.D3DImage> döşeme hızlıdır.  
  
## <a name="best-practices-for-multi-monitor-displays"></a>Çoklu Izleyici ekranları için en iyi uygulamalar  
 Birden çok monitöre sahip bir bilgisayar kullanıyorsanız, önceden açıklanan en iyi yöntemleri izlemeniz gerekir. Ayrıca, çok izleyicili bir yapılandırma için bazı ek performans konuları da vardır.  
  
 Arka arabelleği oluşturduğunuzda, bu, belirli bir cihaz ve bağdaştırıcı üzerinde oluşturulur, ancak WPF, ön arabelleği herhangi bir bağdaştırıcıda gösterebilir. Ön arabelleği güncelleştirmek için bağdaştırıcılar arasında kopyalama çok pahalı olabilir. Windows Vista 'da, birden çok video kartıyla ve bir `IDirect3DDevice9Ex` cihazla, ön arabellek farklı bir bağdaştırıcıyla, ancak yine de aynı ekran kartına sahip olan WDDM 'yi kullanacak şekilde yapılandırılmış bir performans cezası yoktur. Ancak, Windows XP ve birden çok video kartına sahip olan XDDM, ön arabellek geri arabelleğin farklı bir bağdaştırıcısında görüntülendiğinde önemli bir performans cezası vardır. Daha fazla bilgi için bkz. [WPF ve Direct3D9 birlikte](wpf-and-direct3d9-interoperation.md)çalışma.  
  
## <a name="performance-summary"></a>Performans Özeti  
 Aşağıdaki tabloda, işletim sistemi, piksel biçimi ve yüzey lockabilirliği işlevi olarak ön arabellek güncelleştirmesinin performansı gösterilmektedir. Ön arabelleğin ve arka arabelleğin aynı bağdaştırıcıda olduğu varsayılır. Bağdaştırıcı yapılandırmasına bağlı olarak, donanım güncelleştirmeleri yazılım güncelleştirmelerinden genellikle çok daha hızlıdır.  
  
|Yüzey piksel biçimi|Windows Vista, WDDM ve 9Ex|Diğer Windows Vista yapılandırması|Windows XP SP3 veya SP2 w/Hotfix|Windows XP SP2|  
|--------------------------|---------------------------------|----------------------------------------|--------------------------------------|--------------------|  
|D3DFMT_X8R8G8B8 (kilitlenmemelidir)|**Donanım Güncelleştirmesi**|Yazılım güncelleştirmesi|Yazılım güncelleştirmesi|Yazılım güncelleştirmesi|  
|D3DFMT_X8R8G8B8 (kilitlenebilir)|**Donanım Güncelleştirmesi**|Yazılım güncelleştirmesi|**Donanım Güncelleştirmesi**|**Donanım Güncelleştirmesi**|  
|D3DFMT_A8R8G8B8 (kilitlenmemelidir)|**Donanım Güncelleştirmesi**|Yazılım güncelleştirmesi|Yazılım güncelleştirmesi|Yazılım güncelleştirmesi|  
|D3DFMT_A8R8G8B8 (kilitlenebilir)|**Donanım Güncelleştirmesi**|Yazılım güncelleştirmesi|**Donanım Güncelleştirmesi**|Yazılım güncelleştirmesi|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Interop.D3DImage>
- [WPF ve Direct3D9 Birlikte Çalışması](wpf-and-direct3d9-interoperation.md)
- [İzlenecek yol: WPF'de Barındırmak için Direct3D9 İçeriği Oluşturma](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)
- [İzlenecek yol: WPF'de Direct3D9 İçeriği Barındırma](walkthrough-hosting-direct3d9-content-in-wpf.md)
