---
title: 'Performansı iyileştirme: Uygulama Kaynakları'
ms.date: 03/30/2017
helpviewer_keywords:
- application resources [WPF], performance
- resources [WPF], performance
- static resources [WPF]
- sharing resources [WPF]
- brushes [WPF], performance
- sharing brushes without copying [WPF]
ms.assetid: 62b88488-c08e-4804-b7de-a1c34fbe929c
ms.openlocfilehash: fa412a4f900179c22868b2ef3e7429e7dc2acc9c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54507557"
---
# <a name="optimizing-performance-application-resources"></a>Performansı iyileştirme: Uygulama Kaynakları
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] benzer yazılmış öğeler arasında tutarlı bir görünüm veya davranış destekleyebilir uygulama kaynaklarını paylaşmasına olanak sağlar. Bu konu, bu alandaki yardımcı olabilecek bazı öneriler, uygulamalarınızın performansını sağlar.  
  
 Kaynaklar hakkında daha fazla bilgi için bkz. [XAML kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
## <a name="sharing-resources"></a>Kaynakları paylaşma  
 Uygulamanız özel denetimlerini kullanır ve kaynakları tanımlayan bir <xref:System.Windows.ResourceDictionary> (veya XAML kaynakları düğümü) ya da kaynakları tanımlayan önerilir <xref:System.Windows.Application> veya <xref:System.Windows.Window> nesne düzeyinde ya da bunları varsayılan tema olarak tanımlayın özel denetimler. Bir özel denetimin kaynakları tanımlama <xref:System.Windows.ResourceDictionary> denetimin her örneği için bir performans etkisi uygular. Örneğin, bir özel denetim kaynak tanımının bir parçası ve özel denetimin birçok örneği tanımlanan yoğun performans fırça işlemleriniz varsa, uygulamanın çalışma kümesinin önemli ölçüde artıracak.  
  
 Bu noktayı anlamak için aşağıdakileri dikkate alın. Kullanarak bir kart oyun geliştirdiğinizi varsayalım [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Kart oyunları için 52 farklı yüzleri 52 kartlarla gerekir. Özel bir kart denetimi uygulamak karar verin ve kart özel denetiminizin kaynakları (her bir kartın ön yüzü temsil eden) 52 Fırçalar tanımlayın. Ana uygulamanızda, başlangıçta bu kart özel denetimi 52 örneğini oluşturun. Her kart özel denetim örneği 52 örneklerini oluşturur <xref:System.Windows.Media.Brush> 52 * 52 toplam sağlayan nesneleri <xref:System.Windows.Media.Brush> uygulamanızdaki nesneleri. Kart özel denetim kaynaklarına fırçaları taşıyarak <xref:System.Windows.Application> veya <xref:System.Windows.Window> nesne düzeyinde veya özel denetim için varsayılan temayı tanımlayarak 52 Fırçalar şimdi paylaşıyorsunuz olduğundan uygulama çalışma kümesini azaltın kart denetimi 52 örnekleri arasında.  
  
## <a name="sharing-a-brush-without-copying"></a>Bir fırçaları kopyalamadan paylaşma  
 Aynı kullanarak birden çok öğe varsa <xref:System.Windows.Media.Brush> nesne, fırça kaynağı olarak tanımlayın ve bunun yerine fırça satır içinde tanımlama başvuru [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]. Bu yöntem bir örnek oluşturur ve onu, Fırçalar satır içinde tanımlama bilgileriyse tekrar [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] her öğe için yeni bir örneğini oluşturur.  
  
 Bu noktaya aşağıdaki biçimlendirme örneği gösterilmektedir:  
  
 [!code-xaml[Performance#PerformanceSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/BrushResource.xaml#performancesnippet7)]  
  
## <a name="use-static-resources-when-possible"></a>Mümkün olduğunda, statik kaynakları kullanma  
 Statik kaynak, bir başvuru zaten tanımlanmış bir kaynağa bakarak, tüm XAML özelliği özniteliği için bir değer sağlar. Bu kaynak için arama davranışı derleme zamanı aramasına benzer.  
  
 Dinamik bir kaynak, diğer taraftan, ilk derleme sırasında geçici bir ifade yaratacak ve istenen kaynak değeri bir nesne oluşturmak için gerçekten gerekli olana kadar bu nedenle kaynaklara arama erteleme. Bu kaynak için arama davranışı bir performans etkisi uygular çalışma zamanı arama için benzerdir. Statik kaynakları yalnızca gerektiğinde dinamik kaynakları kullanarak uygulamanızı mümkün olduğunca kullanın.  
  
 Aşağıdaki biçimlendirme örneği her iki tür kaynak kullanımını gösterir:  
  
 [!code-xaml[Performance#PerformanceSnippet8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/DynamicResource.xaml#performancesnippet8)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [WPF Uygulama Performansını İyileştirme](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)
- [Uygulama Performansını Planlama](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)
- [Donanımdan Yararlanma](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)
- [Düzen ve Tasarım](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)
- [2B Grafikleri ve Görüntüleme](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Nesne Davranışı](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)
- [Metin](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)
- [Veri Bağlama](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)
- [Diğer Performans Önerileri](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
