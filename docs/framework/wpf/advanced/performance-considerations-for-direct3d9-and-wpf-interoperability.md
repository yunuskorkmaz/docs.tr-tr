---
title: Direct3D9 ve WPF Birlikte Çalışabilirliği için Performans ile İlgili Önemli Noktalar
ms.date: 03/30/2017
helpviewer_keywords:
- WPF [WPF], Direct3D9 interop performance
- Direct3D9 [WPF interoperability], performance
ms.assetid: ea8baf91-12fe-4b44-ac4d-477110ab14dd
ms.openlocfilehash: 52085579c2a432e7db1ebec096a931e0d51718f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549210"
---
# <a name="performance-considerations-for-direct3d9-and-wpf-interoperability"></a>Direct3D9 ve WPF Birlikte Çalışabilirliği için Performans ile İlgili Önemli Noktalar
Kullanarak Direct3D9 içeriğini barındırabilirsiniz <xref:System.Windows.Interop.D3DImage> sınıfı. Direct3D9 içeriği barındırma, uygulamanızın performansını etkileyebilir. Bu konu, bir Windows Presentation Foundation (WPF) uygulamasında Direct3D9 içeriği barındırma, performansı iyileştirmek için en iyi uygulamaları açıklar. Bu en iyi uygulamaları nasıl kullanılacağı dahil <xref:System.Windows.Interop.D3DImage> ve en iyi uygulamalar Windows Vista, Windows XP kullanırken ve birden çok monitör görüntüler.  
  
> [!NOTE]
>  Bu en iyi yöntemleri gösteren kod örnekleri için bkz: [WPF ve Direct3D9 birlikte çalışabilirlik](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md).  
  
## <a name="use-d3dimage-sparingly"></a>D3DImage tutumlu kullanın  
 Direct3D9 içeriği barındırılan bir <xref:System.Windows.Interop.D3DImage> örneği saf Direct3D uygulamasında olduğu gibi hızlı olarak işleme değil. Yüzeyi kopyalama ve komut arabelleğini boşaltma maliyeti yüksek işlemler olabilir. Sayısı arttıkça <xref:System.Windows.Interop.D3DImage> örnekleri artar, daha fazla boşaltma meydana gelir ve performansı düşürür. Bu nedenle, kullanmanız gereken <xref:System.Windows.Interop.D3DImage> tutumlu.  
  
## <a name="best-practices-on-windows-vista"></a>Windows Vista en iyi uygulamalar  
 Windows görüntü sürücüsü modeli (WDDM) kullanmak üzere yapılandırılmış bir görüntü ile Windows Vista en iyi performans için Direct3D9 yüzeyinizi oluşturma bir `IDirect3DDevice9Ex` aygıt. Bu, yüzey paylaşımı sağlar. Video kartı desteklemelidir `D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES` ve `D3DCAPS2_CANSHARERESOURCE` Windows Vista sürücü özellikleri. Diğer ayarları performansı önemli ölçüde azaltan yazılım aracılığıyla kopyalanacak yüzeyini neden.  
  
> [!NOTE]
>  Windows Vista, Windows XP görüntüleme sürücüsü modeli (XDDM) kullanmak üzere yapılandırılmış bir görüntü varsa, surface ayarlarına bakılmaksızın yazılım aracılığıyla her zaman kopyalanır. Yüzey kopyaları donanımda gerçekleştirildiğinden WDDM kullandığınızda Windows Vista'da uygun ayarları ve video kartı ile daha iyi performans görürsünüz.  
  
## <a name="best-practices-on-windows-xp"></a>Windows XP üzerinde en iyi uygulamalar  
 Windows XP görüntü sürücüsü modeli (XDDM) kullanır, Windows XP en iyi performans için düzgün şekilde davranan kilitlenebilir yüzey oluşturun, `IDirect3DSurface9::GetDC` yöntemi çağrılır. Dahili olarak, `BitBlt` yöntemi donanımdaki aygıtlar arasında yüzeyi aktarır. `GetDC` Yöntem her zaman XRGB yüzey üzerinde çalışır. Ancak, istemci bilgisayar Windows XP SP3 veya SP2 çalıştırıyorsa ve istemci de katmanlı penceresi özelliği düzeltme varsa, bu yöntem yalnızca ARGB yüzey üzerinde çalışır. Video kartı desteklemelidir `D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES` sürücü yeteneği.  
  
 Bir 16 bit Masaüstü görüntü derinliği performansı önemli ölçüde azaltabilir. Bir 32-bit Masaüstü önerilir.  
  
 Windows Vista ve Windows XP için geliştiriyorsanız, Windows XP performansını test edin. Windows XP video bellek yetersiz çalışan bir konudur. Ayrıca, <xref:System.Windows.Interop.D3DImage> Windows XP daha fazla görüntü belleği ve Windows Vista WDDM ekstra ekran belleği kopyası gerektiği nedeniyle bant genişliği kullanır. Bu nedenle, Windows Vista Windows XP da kötüsü için aynı video donanım olacak şekilde performans düşüklüğü görebilir.  
  
> [!NOTE]
>  Windows XP ve Windows Vista üzerinde XDDM kullanılabilir; Bununla birlikte, WDDM yalnızca Windows Vista'da kullanılabilir.  
  
## <a name="general-best-practices"></a>Genel en iyi yöntemler  
 Aygıtı oluşturduğunuzda kullanmak `D3DCREATE_MULTITHREADED` oluşturma bayrağı. Bu performans azaltır, ancak WPF işleme sistemi yöntemleri bu aygıtta başka bir iş parçacığından çağırır. İki iş parçacığı aygıt aynı anda erişebilmesi kilitleme protokolünü doğru şekilde izlediğinizden emin olun.  
  
 İşlemeniz WPF tarafından yönetilen iş parçacığı üzerinde gerçekleştirilirse, aygıtla birlikte oluşturmak önerilir `D3DCREATE_FPU_PRESERVE` oluşturma bayrağı. Bu ayar olmadan D3D işleme WPF çift duyarlıklı işlemlerinin doğruluğunu azaltabilir ve işleme sorunlarını tanıtır.  
  
 Döşeme bir <xref:System.Windows.Interop.D3DImage> pow2 olmayan yüzeyi donanım desteği olmadan döşeme sürece ya da, döşeme hızlıdır bir <xref:System.Windows.Media.DrawingBrush> veya <xref:System.Windows.Media.VisualBrush> içeren bir <xref:System.Windows.Interop.D3DImage>.  
  
## <a name="best-practices-for-multi-monitor-displays"></a>Birden çok monitör görüntüler için en iyi yöntemler  
 Birden çok monitör sahip bir bilgisayar kullanıyorsanız, daha önce açıklanan en iyi uygulamaları izlemelisiniz. Birden çok İzleyici yapılandırması için bazı ek performans konuları vardır.  
  
 Geri arabelleği oluşturduğunuzda, belirli bir aygıt ve bağdaştırıcı oluşturulur ancak WPF, herhangi bir bağdaştırıcı üzerinde ön arabellek görüntülenebilir. Ön arabelleği güncelleştirmek için bağdaştırıcılar arasında kopyalama çok pahalı olabilir. Windows Vista'da WDDM ile birden çok video kartı ile kullanmak üzere yapılandırılmış bir `IDirect3DDevice9Ex` aygıt, ön arabellek farklı bağdaştırıcı ama hala aynı ekran kartı üzerinde ise, performansta düşme olmaz yoktur. Ancak, Windows XP ve birden çok video kartı ile XDDM, yapıldığında önemli bir performans sorunu ön arabellek geri arabellekten farklı bir bağdaştırıcı gösterilir. Daha fazla bilgi için bkz: [WPF ve Direct3D9 birlikte çalışabilirlik](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md).  
  
## <a name="performance-summary"></a>Performans özeti  
 Aşağıdaki tabloda ön arabellek güncelleştirme performansı işletim sistemi, piksel biçimi ve yüzey kilitlenebilirliğinin işlevi olarak gösterir. Ön arabellek ve arka arabelleğin aynı bağdaştırıcıda olduğu varsayılır. Bağdaştırıcı yapılandırmasına bağlı olarak, donanım güncelleştirmelerini yazılım güncelleştirmelerini genellikle çok daha hızlıdır.  
  
|Yüzey piksel biçimi|Windows Vista, WDDM ve 9Ex|Diğer Windows Vista yapılandırmaları|Windows XP SP3 veya düzeltme ile SP2|Windows XP SP2|  
|--------------------------|---------------------------------|----------------------------------------|--------------------------------------|--------------------|  
|D3DFMT_X8R8G8B8 (kilitlenebilir olmayan)|**Donanım Güncelleştirme**|Yazılım güncelleştirmesi|Yazılım güncelleştirmesi|Yazılım güncelleştirmesi|  
|D3DFMT_X8R8G8B8 (kilitlenebilir)|**Donanım Güncelleştirme**|Yazılım güncelleştirmesi|**Donanım Güncelleştirme**|**Donanım Güncelleştirme**|  
|D3DFMT_X8R8G8B8 (kilitlenebilir olmayan)|**Donanım Güncelleştirme**|Yazılım güncelleştirmesi|Yazılım güncelleştirmesi|Yazılım güncelleştirmesi|  
|D3DFMT_X8R8G8B8 (kilitlenebilir)|**Donanım Güncelleştirme**|Yazılım güncelleştirmesi|**Donanım Güncelleştirme**|Yazılım güncelleştirmesi|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Interop.D3DImage>  
 [WPF ve Direct3D9 Birlikte Çalışması](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md)  
 [İzlenecek yol: WPF'de Barındırmak için Direct3D9 İçeriği Oluşturma](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)  
 [İzlenecek yol: WPF'de Direct3D9 İçeriği Barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)
