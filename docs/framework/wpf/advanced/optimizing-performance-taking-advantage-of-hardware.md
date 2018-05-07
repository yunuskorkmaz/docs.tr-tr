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
ms.openlocfilehash: eb790da63b4636e3dd6c25ea118075304702acc0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="optimizing-performance-taking-advantage-of-hardware"></a>Performansı İyileştirme: Donanımdan Yararlanma
İç mimarisi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ardışık düzen iki işleme, donanım ve yazılıma sahip. Bu konu, uygulamalarınızın performansını en iyi duruma getirme hakkında kararlar almanıza yardımcı olmak için bu ardışık düzen işleme hakkında bilgi sağlar.  
  
## <a name="hardware-rendering-pipeline"></a>Donanım işleme ardışık düzeni  
 Aşağıdakilerden birini belirlemede en önemli etkenlerden [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] performans olan işleme bağlı olduğunu — daha fazla piksel işlemek zorunda kalırsanız maliyeti daha yüksek performans. Ancak, daha fazla bilgi işleme için boşaltılabilecek [!INCLUDE[TLA#tla_gpu](../../../../includes/tlasharptla-gpu-md.md)], daha fazla performans faydaları elde. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Uygulaması donanım işleme ardışık tam avantajlarından yararlanır [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] en az destekleyen donanım özellikleri [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] sürüm 7.0. İyileştirmelerin destekleyen donanım tarafından kazanılabilir [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] sürüm 7.0 ve PixelShader 2.0 + özelliklerini.  
  
## <a name="software-rendering-pipeline"></a>Yazılım işleme ardışık düzeni  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Yazılım işleme ardışık düzeni olan tamamen CPU'ya bağlıdır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir en iyi duruma getirilmiş, tam özellikli yazılım tarayıcısını uygulamak için CPU içindeki SSE ve SSE2 yönerge yararlanır ayarlar. Geri dönüş yazılım için uygulama işlevselliği kullanılarak donanım işleme ardışık düzeni işlenemiyor. istediğiniz zaman sorunsuz olarak gerçekleştirilir.  
  
 En büyük performans sorunu işlediğiniz piksel sayısı tanımlanan oranı doldurmak için yazılım modunda işleme işlerken karşılaşırsınız. Bir piksel çizilme sayısını en aza indirmek yazılım işleme modunu performansı hakkında endişeleriniz varsa deneyin. Örneğin, ardından biraz saydam bir görüntü üzerinde işleyen, mavi arka plan ile bir uygulamanız varsa, tüm pikselleri iki kez uygulamada işlemez. Sonuç olarak, bu iki kez uygulama, yalnızca mavi arka plana sahip daha görüntü ile işlemek için zaman alacaktır.  
  
### <a name="graphics-rendering-tiers"></a>Grafik İşleme Katmanları  
 Uygulamanızın üzerinde çalışacağı donanım yapılandırmasını tahmin etmek oldukça zor olabilir. Ancak, böylece her farklı donanım yapılandırması tam anlamıyla yararlanabilmek sorunsuz bir şekilde özellikleri farklı donanım üzerinde çalışırken geçiş yapmak, uygulamanızın izin veren bir tasarım düşünmek isteyebilirsiniz.  
  
 Bunu başarmak için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zamanında sistemin grafik yeteneğini belirlemek için işlevsellik sağlar. Grafik yeteneği, video kartı üç işleme yeteneği katmanından biri olarak sınıflandırarak belirlenir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullanıma sunan bir [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] işleme yeteneği katmanını sorgulamak için bir uygulama sağlar. Uygulamanız, daha sonra donanım tarafından desteklenen işleme katmanına bağlı olarak çalışma zamanında farklı kod yollarını alabilir.  
  
 Çoğu işleme katmanı düzeylerini etkileyen grafik donanım özellikleri şunlardır:  
  
-   **Video RAM** birleştirme grafikler için kullanılan arabellek sayısı ve boyutu grafik donanımı üzerindeki video bellek miktarını belirler.  
  
-   **Piksel gölgelendirici** piksel gölgelendirici grafik piksel başına temelinde etkileri hesaplar işlevi değil. Görüntülenen grafiklerin çözümleme bağlı olarak, her görüntü çerçevesi için işlenmesi gereken birkaç milyon piksel olabilir.  
  
-   **Köşe gölgelendirici** köşe gölgelendirici grafik nesnesinin köşe veriler üzerinde matematiksel işlemler gerçekleştiren işlevi değil.  
  
-   **Çoklu doku desteği** 3B grafik nesnesi üzerinde yakınsama işlemi sırasında iki veya daha fazla farklı dokuları uygulama özelliği için çoklu doku desteği başvuruyor. Çoklu doku desteğinin derecesi grafik donanımı üzerindeki çoklu doku birimlerinin sayısı tarafından belirlenir.  
  
 Piksel gölgelendirici, köşe gölgelendirici ve çoklu doku özellikleri belirli tanımlamak için kullanılan [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] hangi sırayla, farklı işleme katmanlarını tanımlamak için kullanılan sürüm düzeylerini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Grafik donanım özellikleri işleme yeteneğini belirlemek bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Sistem üç işleme katmanı tanımlar:  
  
-   **Katman 0 işleme** hiçbir grafik donanım hızlandırmasını. [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Sürüm düzeyi sürüm 7.0 azdır.  
  
-   **Katman 1 işleme** kısmi grafik donanım hızlandırmasını. [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Sürüm düzeyi 7.0 sürümüne eşit veya daha büyük ve **küçük** 9.0 sürümünden.  
  
-   **Katman 2 işleme** çoğu grafik özelliği grafik donanım hızlandırmasını kullanır. [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Sürüm düzeyi 9.0 sürümüne eşit veya daha büyük.  
  
 Daha fazla bilgi için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] işleme katmanları bkz [grafik işleme katmanları](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF Uygulama Performansını İyileştirme](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Uygulama Performansını Planlama](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [Düzen ve Tasarım](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [2B Grafikleri ve Görüntüleme](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Nesne Davranışı](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [Uygulama Kaynakları](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Metin](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Veri Bağlama](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Diğer Performans Önerileri](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
