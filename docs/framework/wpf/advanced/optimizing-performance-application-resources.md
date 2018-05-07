---
title: 'Performansı İyileştirme: Uygulama Kaynakları'
ms.date: 03/30/2017
helpviewer_keywords:
- application resources [WPF], performance
- resources [WPF], performance
- static resources [WPF]
- sharing resources [WPF]
- brushes [WPF], performance
- sharing brushes without copying [WPF]
ms.assetid: 62b88488-c08e-4804-b7de-a1c34fbe929c
ms.openlocfilehash: 53e906f31f32fb0f1df3f8d986daa0ae95ea9e4c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="optimizing-performance-application-resources"></a>Performansı İyileştirme: Uygulama Kaynakları
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Böylece yazılan benzer öğeler arasında tutarlı bir görünüm veya davranışı destekleyebilir uygulama kaynaklarını paylaşmanıza olanak sağlar. Bu konu, bu alandaki yardımcı olabilecek birkaç öneri uygulamalarınızın performansını sağlar.  
  
 Kaynaklar hakkında daha fazla bilgi için bkz: [XAML kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
## <a name="sharing-resources"></a>Kaynakları paylaşma  
 Uygulamanız özel denetimler kullanıyor ve kaynakları tanımlayan bir <xref:System.Windows.ResourceDictionary> (veya XAML kaynakları düğümü) ya da kaynakları tanımlamak önerilir <xref:System.Windows.Application> veya <xref:System.Windows.Window> nesne düzeyinde ya için varsayılan tema tanımlayın özel denetimler. Özel denetimin içinde kaynakları tanımlama <xref:System.Windows.ResourceDictionary> denetleyen her örneği için bir performans etkisi uygular. Örneğin, bir özel denetim kaynak tanımının bir parçası ve birçok özel denetim örneği tanımlanan performansı yoğun fırça işlemler varsa, uygulamanın çalışma kümesi önemli ölçüde artırır.  
  
 Bu noktayı anlamak için aşağıdakileri göz önünde bulundurun. Geliştirmekte kullanarak bir kart oyunu düşünelim [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Çoğu kart oyunları için 52 farklı yüzü olan 52 kartları gerekir. Özel bir kart denetimi kullanmaya karar ve kart özel denetim kaynaklarında 52 Fırçalar (her bir kart yüzünü temsil eder) tanımlayın. Ana uygulamanızda, başlangıçta bu kartı özel denetim 52 örneğini oluşturun. Özel kart denetiminin her örneği 52 örneklerini oluşturur <xref:System.Windows.Media.Brush> 52 * 52 toplamını verir nesneleri <xref:System.Windows.Media.Brush> uygulamanızdaki nesneleri. Kart özel denetim kaynaklarına dışında Fırçalar taşıyarak <xref:System.Windows.Application> veya <xref:System.Windows.Window> nesne düzeyinde ya da bunları özel denetim için varsayılan tema tanımlayarak 52 Fırçalar şimdi paylaşıyorsunuz bu yana uygulama çalışma kümesi azaltın Kart denetiminin 52 örnekleri arasında.  
  
## <a name="sharing-a-brush-without-copying"></a>Fırça kopyalamadan paylaşma  
 Aynı kullanarak birden çok öğe varsa <xref:System.Windows.Media.Brush> nesne, bir kaynak olarak fırça tanımlamak ve bunun yerine fırça satır içinde tanımlama başvuru [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]. Bu yöntem bir örnek oluşturur ve onu, Fırçalar satır içinde tanımlama ancak tekrar [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] her öğe için yeni bir örnek oluşturur.  
  
 Aşağıdaki biçimlendirme örneği bu noktayı gösterir:  
  
 [!code-xaml[Performance#PerformanceSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/BrushResource.xaml#performancesnippet7)]  
  
## <a name="use-static-resources-when-possible"></a>Mümkün olduğunca statik kaynakları kullanın  
 Statik kaynak önceden tanımlanan bir kaynağa başvuru bakarak herhangi XAML Özellik özniteliği için bir değer sağlar. Bu kaynak için arama davranışı derleme zamanı aramasına benzer.  
  
 Dinamik bir kaynak diğer taraftan, ilk derleme sırasında geçici bir ifade oluşturur ve bu nedenle istenen kaynak değeri bir nesne oluşturmak için gerçekten gerekli olana kadar kaynaklara arama erteleneceği. Bu kaynak için arama davranışı bir performans etkisi uygular çalışma zamanı arama için benzerdir. Statik kaynaklarla dinamik kaynaklar yalnızca gerekli olduğunda kullanarak uygulamanızı mümkün olduğunca kullanın.  
  
 Aşağıdaki biçimlendirme örneği her iki tür kaynak kullanımını göstermektedir:  
  
 [!code-xaml[Performance#PerformanceSnippet8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/DynamicResource.xaml#performancesnippet8)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF Uygulama Performansını İyileştirme](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Uygulama Performansını Planlama](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [Donanımdan Yararlanma](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [Düzen ve Tasarım](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [2B Grafikleri ve Görüntüleme](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Nesne Davranışı](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [Metin](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Veri Bağlama](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Diğer Performans Önerileri](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
