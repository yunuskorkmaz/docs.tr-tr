---
title: 'Performansı İyileştirme: Donanımdan Yararlanma'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], performance
- hardware rendering pipeline [WPF]
- rendering tiers [WPF]
- graphics rendering tiers [WPF]
- graphics [WPF], rendering tiers
- software rendering pipeline [WPF]
ms.assetid: bfb89bae-7aab-4cac-a26c-a956eda8fce2
ms.openlocfilehash: a47a4aae785d817904c30fe7c865a1c033eb3cca
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68709219"
---
# <a name="optimizing-performance-taking-advantage-of-hardware"></a>Performansı İyileştirme: Donanımdan Yararlanma
İç mimarisi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , iki işleme işlem hattı, donanım ve yazılım içerir. Bu konuda, uygulamalarınızın performans iyileştirmeleri hakkında kararlar almanıza yardımcı olmak üzere bu işleme işlem hatları hakkında bilgi verilmektedir.  
  
## <a name="hardware-rendering-pipeline"></a>Donanım Işleme işlem hattı  
 Performansı belirlemede [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en önemli faktörlerden biri işleme bağlıdır — daha fazla piksel işlemek için, performans maliyeti artar. Ancak, grafik işleme birimi (GPU) üzerinde boşaltılabilecek daha fazla işleme elde edeceğiniz performans avantajları daha fazla olabilir. Uygulama [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] donanımı işleme işlem hattı, en az Microsoft DirectX 7,0 sürümünü destekleyen donanımda Microsoft DirectX özelliklerinden tam olarak yararlanır. Microsoft DirectX sürüm 7,0 ve PixelShader 2.0 + özelliklerini destekleyen donanımlar tarafından daha fazla iyileştirmeler kazanılabilir.  
  
## <a name="software-rendering-pipeline"></a>Yazılım Işleme işlem hattı  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Yazılım işleme işlem hattı tamamen CPU bağlanmıştır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], iyileştirilmiş ve tam özellikli bir yazılım tarayıcısı uygulamak için CPU 'daki SSE ve SSE2 yönerge kümelerinden faydalanır. Yazılıma geri dönüş, uygulama işlevlerinin donanım işleme işlem hattı kullanılarak işlenemediğinde sorunsuz bir şekilde gerçekleştirilir.  
  
 Yazılım modunda işleme yaparken karşılaşacağınız en büyük performans sorunu, işleme yaptığınız piksel sayısı olarak tanımlanmış olan Fill Rate ile ilgilidir. Yazılım işleme modundaki performansla ilgili endişeleriniz varsa, bir pikselin yeniden çizilme sayısını en aza indirmenize çalışın. Örneğin, mavi bir arka plana sahip bir uygulamanız varsa, daha sonra bunun üzerinde biraz saydam bir görüntü oluşturup uygulamadaki tüm pikselleri iki kez işleyebilirsiniz. Sonuç olarak, yalnızca mavi arka plana sahip olmak yerine, uygulamanın görüntüyle işlenmesi iki kat sürer.  
  
### <a name="graphics-rendering-tiers"></a>Grafik İşleme Katmanları  
 Uygulamanızın üzerinde çalıştığı donanım yapılandırmasını tahmin etmek çok zor olabilir. Bununla birlikte, uygulamanızın farklı donanımlar üzerinde çalışırken sorunsuz bir şekilde geçiş yapmasına olanak tanıyan bir tasarıma göz önünde bulundurabilirsiniz, böylece her bir farklı donanım yapılandırmasının avantajlarından faydalanabilirsiniz.  
  
 Bunu başarmak için, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çalışma zamanında bir sistemin grafik yeteneklerini belirleme işlevselliği sağlar. Grafik özelliği, video kartını üç işleme özelliği katmanlarından biri olarak kategorilere ayırarak belirlenir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]uygulamanın işleme yeteneği katmanını sorgulamasını sağlayan bir API sunar. Daha sonra uygulamanız, donanım tarafından desteklenen işleme katmanına bağlı olarak, çalışma zamanında farklı kod yolları alabilir.  
  
 İşleme katmanı düzeylerini en çok etkileyen grafik donanımının özellikleri şunlardır:  
  
- **VIDEO RAM** 'i Grafik donanımındaki video belleği miktarı, birleştirme grafikleri için kullanılabilecek arabelleklerin boyutunu ve sayısını belirler.  
  
- **Piksel gölgelendiricisi** Piksel gölgelendiricisi, her piksel temelinde etkileri hesaplayan bir grafik işleme işlevidir. Görüntülenen grafiklerin çözümüne bağlı olarak, her bir görüntüleme çerçevesi için işlenmesi gereken birkaç milyon piksel olabilir.  
  
- **Köşe gölgelendiricisi** Köşe gölgelendiricisi, nesnenin köşe verilerinde matematik işlemleri gerçekleştiren bir grafik işleme işlevidir.  
  
- **Multitexture desteği** Multitexture desteği, 3B grafik nesnesindeki bir karıştırma işlemi sırasında iki veya daha fazla farklı doku uygulama imkanını ifade eder. Çoklu doku desteğinin derecesi, Grafik donanımındaki çok modelli birim sayısına göre belirlenir.  
  
 Piksel gölgelendirici, köşe gölgelendiricisi ve Multitexture özellikleri, içinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]farklı işleme katmanlarını tanımlamak Için kullanılan belirli DirectX sürüm düzeylerini tanımlamak için kullanılır.  
  
 Grafik donanımının özellikleri, bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamanın işleme yeteneğini tespit. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Sistem üç işleme katmanı tanımlar:  
  
- **Işleme katmanı 0** Grafik donanım hızlandırma yok. DirectX sürüm düzeyi 7,0 sürümünden düşüktür.  
  
- **Işleme katmanı 1** Kısmi grafik donanım hızlandırma. DirectX sürüm düzeyi 7,0 sürümüne eşit veya daha büyük ve sürüm 9,0 ' den **küçük** .  
  
- **Işleme katmanı 2** Çoğu grafik özelliği grafik donanım hızlandırmasını kullanır. DirectX sürüm düzeyi 9,0 sürümüne eşit veya ondan daha büyük.  
  
 Katmanları işleme hakkında [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] daha fazla bilgi için bkz. [grafik işleme katmanları](graphics-rendering-tiers.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF Uygulama Performansını İyileştirme](optimizing-wpf-application-performance.md)
- [Uygulama Performansını Planlama](planning-for-application-performance.md)
- [Düzen ve Tasarım](optimizing-performance-layout-and-design.md)
- [2B Grafikleri ve Görüntüleme](optimizing-performance-2d-graphics-and-imaging.md)
- [Nesne Davranışı](optimizing-performance-object-behavior.md)
- [Uygulama Kaynakları](optimizing-performance-application-resources.md)
- [Metin](optimizing-performance-text.md)
- [Veri Bağlama](optimizing-performance-data-binding.md)
- [Diğer Performans Önerileri](optimizing-performance-other-recommendations.md)
