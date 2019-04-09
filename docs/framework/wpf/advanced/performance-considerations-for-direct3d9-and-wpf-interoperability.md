---
title: Direct3D9 ve WPF Birlikte Çalışabilirliği için Performans ile İlgili Önemli Noktalar
ms.date: 03/30/2017
helpviewer_keywords:
- WPF [WPF], Direct3D9 interop performance
- Direct3D9 [WPF interoperability], performance
ms.assetid: ea8baf91-12fe-4b44-ac4d-477110ab14dd
ms.openlocfilehash: 1371fa901bebc503a0091f3229a8fd7e6ccc2c86
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162639"
---
# <a name="performance-considerations-for-direct3d9-and-wpf-interoperability"></a>Direct3D9 ve WPF Birlikte Çalışabilirliği için Performans ile İlgili Önemli Noktalar
Direct3D9 içeriği kullanarak barındırabilirsiniz <xref:System.Windows.Interop.D3DImage> sınıfı. Direct3D9 içeriği barındırma, uygulamanızın performansını etkileyebilir. Bu konu, bir Windows Presentation Foundation (WPF) uygulamasındaki Direct3D9 içeriği barındırma, performansı iyileştirmek için en iyi uygulamaları açıklar. Bu en iyi uygulamaları nasıl kullanılacağını dahil <xref:System.Windows.Interop.D3DImage> ve en iyi uygulamalar, Windows XP, Windows Vista'yı kullanırken ve çoklu monitör görüntüler.  
  
> [!NOTE]
>  Bu en iyi uygulamaları gösteren kod örnekleri için bkz: [WPF ve Direct3D9 birlikte çalışması](wpf-and-direct3d9-interoperation.md).  
  
## <a name="use-d3dimage-sparingly"></a>D3DImage tedbirli şekilde kullanın  
 Direct3D9 içeriği barındırılan bir <xref:System.Windows.Interop.D3DImage> örneği olarak saf bir Direct3D uygulaması hızlı işleme yok. Surface kopyalama ve komut arabelleğini boşaltma pahalı bir işlem olabilir. Sayısı arttıkça <xref:System.Windows.Interop.D3DImage> örnekleri arttıkça, daha fazla bir temizlemeye gerçekleşir ve performansı düşürür. Bu nedenle, kullanmalısınız <xref:System.Windows.Interop.D3DImage> gerektiğinde.  
  
## <a name="best-practices-on-windows-vista"></a>Windows Vista en iyi uygulamalar  
 Windows görüntü sürücü modeli (WDDM) kullanacak şekilde yapılandırılmış bir görüntü ile Windows Vista en iyi performans için Direct3D9 yüzeyinizi oluşturmak bir `IDirect3DDevice9Ex` cihaz. Bu paylaşımı yüzeyi sağlar. Video kartı desteklemelidir `D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES` ve `D3DCAPS2_CANSHARERESOURCE` Windows Vista sürücü özellikleri. Tüm diğer ayarlar performansı önemli ölçüde azaltan yazılım kopyalanacak yüzey neden.  
  
> [!NOTE]
>  Windows Vista, Windows XP görüntüleme sürücü modeli (XDDM) kullanacak şekilde yapılandırılmış bir görüntü varsa, surface ayarlarına bakılmaksızın yazılım aracılığıyla her zaman kopyalanır. Yüzey kopya donanım gerçekleştirildiğinden WDDM kullandığınızda uygun ayarları ve ekran kartı ile daha iyi performans Windows Vista'da görürsünüz.  
  
## <a name="best-practices-on-windows-xp"></a>Windows XP üzerinde en iyi yöntemler  
 Windows XP, Windows XP görünen sürücü modeli (XDDM) kullanır, en iyi performans için düzgün şekilde davranan kilitlenebilir yüzey oluşturmak zaman `IDirect3DSurface9::GetDC` yöntemi çağrılır. Dahili olarak `BitBlt` yöntemi yüzey donanım aygıtları arasında aktarır. `GetDC` Yöntem her zaman XRGB yüzeyler üzerinde çalışır. Ancak, istemci bilgisayar Windows XP SP3 veya SP2 ile çalışıyorsa ve istemci de katmanlı penceresi özelliği düzeltme varsa, bu yöntem yalnızca ARGB yüzeyler üzerinde çalışır. Video kartı desteklemelidir `D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES` sürücü özelliği.  
  
 Bir 16 bit Masaüstü görüntü derinliği performansı önemli ölçüde azaltabilir. Bir 32 bit Masaüstü önerilir.  
  
 Windows Vista ve Windows XP için geliştiriyorsanız, Windows XP performansını test edin. Windows XP video bellek yetersiz çalışan bir konudur. Ayrıca, <xref:System.Windows.Interop.D3DImage> Windows XP daha fazla video belleği ve daha fazla video belleği kopyası gerektiği nedeniyle Windows Vista WDDM bant genişliği kullanır. Bu nedenle, performans için video aynı donanımı Windows Vista Windows XP da kötüsü olmasını bekleyebilirsiniz.  
  
> [!NOTE]
>  XDDM, Windows XP ve Windows Vista kullanılabilir; Bununla birlikte, WDDM yalnızca Windows Vista'da kullanılabilir.  
  
## <a name="general-best-practices"></a>Genel en iyi yöntemler  
 Cihaz oluştururken `D3DCREATE_MULTITHREADED` oluşturma bayrağı. Bu performans azaltır, ancak WPF işleme sistemi yöntemleri bu cihazda başka bir iş parçacığından çağırır. Böylece iki iş parçacığının aynı anda cihazınıza erişim kilitleme Protokolü doğru şekilde izlediğinizden emin olun.  
  
 İşlemeniz bir WPF yönetilen iş parçacığı üzerinde gerçekleştirilir, cihazla oluşturmak önerilir `D3DCREATE_FPU_PRESERVE` oluşturma bayrağı. Bu ayar olmadan D3D işleme WPF çift duyarlıklı operations doğruluğunu azaltmak ve işleme sorunlarını tanıtır.  
  
 Döşeme bir <xref:System.Windows.Interop.D3DImage> donanım desteği olmadan bir pow2 olmayan yüzeyi döşeme sürece ya da, döşeme hızlıdır bir <xref:System.Windows.Media.DrawingBrush> veya <xref:System.Windows.Media.VisualBrush> içeren bir <xref:System.Windows.Interop.D3DImage>.  
  
## <a name="best-practices-for-multi-monitor-displays"></a>Çoklu monitör görüntüler için en iyi uygulamalar  
 Birden çok ekrana sahip bir bilgisayar kullanıyorsanız, daha önce açıklandığı gibi en iyi uygulamaları izlemelisiniz. Ayrıca bazı ek performans değerlendirmeleri bir çoklu monitör yapılandırması vardır.  
  
 Geri arabelleği oluşturduğunuzda, belirli bir aygıt ve bağdaştırıcı oluşturulur, ancak WPF ön arabellek herhangi bir bağdaştırıcı görüntülenebilir. Ön arabellek güncelleştirmek için bağdaştırıcıları kopyalama çok pahalı olabilir. Windows Vista'da WDDM çoklu ekran kartları ve ile kullanmak üzere yapılandırılmış bir `IDirect3DDevice9Ex` cihaz, ön arabellek farklı bir bağdaştırıcı ama yine de aynı ekran kartı üzerinde ise, performans cezası yoktur. Ancak Windows XP ve birden çok ekran kartı ile XDDM, yapıldığında önemli bir performans cezası ön arabellek geri arabellekten farklı bir bağdaştırıcı görüntülenir. Daha fazla bilgi için [WPF ve Direct3D9 birlikte çalışması](wpf-and-direct3d9-interoperation.md).  
  
## <a name="performance-summary"></a>Performans özeti  
 Aşağıdaki tabloda, işletim sistemi, piksel biçimi ve yüzey kilitlenebilirliğinin işlevi olarak ön buffer güncelleştirmesi performansını gösterir. Geri arabelleği ve ön arabellek aynı bağdaştırıcıda olarak kabul edilir. Bağdaştırıcı yapılandırmasına bağlı olarak donanım güncellemesi yazılım güncelleştirmelerini genellikle çok daha hızlıdır.  
  
|Yüzey piksel biçimi|Windows Vista, WDDM ve 9Ex|Diğer Windows Vista'yı yapılandırma|Windows XP SP3 veya düzeltme ile SP2|Windows XP SP2|  
|--------------------------|---------------------------------|----------------------------------------|--------------------------------------|--------------------|  
|D3DFMT_X8R8G8B8 (kilitlenebilir değil)|**Donanım Güncelleştirme**|Yazılım güncelleştirmesi|Yazılım güncelleştirmesi|Yazılım güncelleştirmesi|  
|D3DFMT_X8R8G8B8 (kilitlenebilir)|**Donanım Güncelleştirme**|Yazılım güncelleştirmesi|**Donanım Güncelleştirme**|**Donanım Güncelleştirme**|  
|D3DFMT_X8R8G8B8 (kilitlenebilir değil)|**Donanım Güncelleştirme**|Yazılım güncelleştirmesi|Yazılım güncelleştirmesi|Yazılım güncelleştirmesi|  
|D3DFMT_X8R8G8B8 (kilitlenebilir)|**Donanım Güncelleştirme**|Yazılım güncelleştirmesi|**Donanım Güncelleştirme**|Yazılım güncelleştirmesi|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Interop.D3DImage>
- [WPF ve Direct3D9 Birlikte Çalışması](wpf-and-direct3d9-interoperation.md)
- [İzlenecek yol: WPF'de Barındırmak için Direct3D9 İçeriği Oluşturma](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)
- [İzlenecek yol: Direct3D9 İçeriğini WPF’de Barındırma](walkthrough-hosting-direct3d9-content-in-wpf.md)
