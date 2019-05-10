---
title: 'Performansı iyileştirme: Diğer öneriler'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Terminal Services rendering [WPF]
- opacity [WPF]
- hit-test objects [WPF]
- ScrollBarVisibility enumeration [WPF]
- brushes [WPF], performance
ms.assetid: d028cc65-7e97-4a4f-9859-929734eaf40d
ms.openlocfilehash: 9757a8c8327feb40018387473b479e467149f0ed
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64611905"
---
# <a name="optimizing-performance-other-recommendations"></a>Performansı iyileştirme: Diğer öneriler
<a name="introduction"></a> Bu konu başlığı altında ek olarak konularındaki tarafından kapsanan performans önerileri sağlar [WPF uygulama performansını en iyi duruma getirme](optimizing-wpf-application-performance.md) bölümü.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
- [Opaklık karşı öğeler üzerinde Fırçalar hakkında](#Opacity)  
  
- [Nesne gitme](#Navigation_Objects)  
  
- [İsabet sınaması 3B yüzeyler üzerinde](#Hit_Testing)  
  
- [CompositionTarget.işleme olayı](#CompositionTarget_Rendering_Event)  
  
- [ScrollBarVisibility kullanmaktan kaçının otomatik =](#Avoid_Using_ScrollBarVisibility)  
  
- [Başlatma süresini azaltmak için yazı tipi önbellek hizmetini yapılandırma](#FontCache)  
  
<a name="Opacity"></a>   
## <a name="opacity-on-brushes-versus-opacity-on-elements"></a>Opaklık karşı öğeler üzerinde Fırçalar hakkında  
 Kullandığınızda, bir <xref:System.Windows.Media.Brush> ayarlanacak <xref:System.Windows.Shapes.Shape.Fill%2A> veya <xref:System.Windows.Shapes.Shape.Stroke%2A> bir öğenin ayarlamak daha iyi <xref:System.Windows.Media.Brush.Opacity%2A?displayProperty=nameWithType> değeri ayarı yerine öğenin <xref:System.Windows.UIElement.Opacity%2A> özelliği. Bir öğenin değiştirme <xref:System.Windows.UIElement.Opacity%2A> özelliği neden olabilecek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] geçici bir yüzey oluşturmak için.  
  
<a name="Navigation_Objects"></a>   
## <a name="navigation-to-object"></a>Nesne gitme  
 <xref:System.Windows.Navigation.NavigationWindow> Nesne türetilir <xref:System.Windows.Window> ve içerik gezinti desteği ile öncelikli olarak toplayarak genişletir <xref:System.Windows.Navigation.NavigationService> ve günlük. İstemci alanının güncelleştirebilirsiniz <xref:System.Windows.Navigation.NavigationWindow> ya da belirterek bir [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] veya bir nesne. Aşağıdaki örnek, her iki yöntem de gösterir:  
  
 [!code-csharp[Performance#PerformanceSnippet14](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/TestNavigation.xaml.cs#performancesnippet14)]
 [!code-vb[Performance#PerformanceSnippet14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/testnavigation.xaml.vb#performancesnippet14)]  
  
 Her <xref:System.Windows.Navigation.NavigationWindow> nesnesi, pencerede kullanıcının Gezinti geçmişini kaydeden bir günlük sahiptir. Günlük amaçlarından kullanıcılar kendi adımları yeniden izlemesine izin vermektir.  
  
 Kullanarak gittiğinizde bir [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], günlüğü yalnızca depolar [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] başvuru. Bu her zaman sayfayı yeniden ziyaret, bunu dinamik olarak, zaman alıcı sayfanın karmaşıklığına bağlı olarak olabilecek oluşturulduğunu gösterir. Bu durumda, günlük depolama maliyeti düşük ancak sayfayı yeniden oluşturmak için zaman olasılığı yüksektir.  
  
 Bir nesneyi kullanmayı gittiğinizde günlük visual nesne ağacının tümünü depolar. Bu sayfayı yeniden ziyaret her seferinde, hemen oluşturulmadan gerek kalmadan anlamına gelir. Bu durumda, günlük depolama maliyeti yüksektir, ancak sayfa yeniden oluşturmak için zaman düşüktür.  
  
 Kullanırken <xref:System.Windows.Navigation.NavigationWindow> nesnesi, günlüğe kaydetme desteği, uygulamanızın performansını nasıl etkilediğini göz önünde bulundurmanız gerekir. Daha fazla bilgi için [gezintiye genel bakış](../app-development/navigation-overview.md).  
  
<a name="Hit_Testing"></a>   
## <a name="hit-testing-on-large-3d-surfaces"></a>İsabet sınaması 3B yüzeyler üzerinde  
 3B yüzeyler üzerinde isabet sınaması bir çok performansı yoğun CPU tüketimi açısından işlemdir. Bu, özellikle 3B yüzeyi hareketli olduğunda geçerlidir. İsabet testi üzerinde bu yüzeyleri gerektirmeyen isabet sınaması devre dışı. Öğesinden türetilen nesneler <xref:System.Windows.UIElement> devre dışı bırakma isabet ayarlayarak test <xref:System.Windows.UIElement.IsHitTestVisible%2A> özelliğini `false`.  
  
<a name="CompositionTarget_Rendering_Event"></a>   
## <a name="compositiontargetrendering-event"></a>CompositionTarget.işleme olayı  
 <xref:System.Windows.Media.CompositionTarget.Rendering?displayProperty=nameWithType> Olayına neden olmadan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sürekli animasyon uygulamak için. Bu olayı kullanın, her fırsatta çıkarın.  
  
<a name="Avoid_Using_ScrollBarVisibility"></a>   
## <a name="avoid-using-scrollbarvisibilityauto"></a>ScrollBarVisibility kullanmaktan kaçının otomatik =  
 Mümkün olduğunda, kullanmaktan kaçının <xref:System.Windows.Controls.ScrollBarVisibility.Auto?displayProperty=nameWithType> değerini `HorizontalScrollBarVisibility` ve `VerticalScrollBarVisibility` özellikleri. Bu özellikler için tanımlanan <xref:System.Windows.Controls.RichTextBox>, <xref:System.Windows.Controls.ScrollViewer>, ve <xref:System.Windows.Controls.TextBox> nesneler için eklenen bir özellik olarak <xref:System.Windows.Controls.ListBox> nesne. Bunun yerine, <xref:System.Windows.Controls.ScrollBarVisibility> için <xref:System.Windows.Controls.ScrollBarVisibility.Disabled>, <xref:System.Windows.Controls.ScrollBarVisibility.Hidden>, veya <xref:System.Windows.Controls.ScrollBarVisibility.Visible>.  
  
 <xref:System.Windows.Controls.ScrollBarVisibility.Auto> Sınırlı sayıda yer olduğu ve kaydırma çubukları, yalnızca gerekli olduğunda görüntülenecek değer durumlar için tasarlanmıştır. Örneğin, bunu kullanmak kullanışlı olabilir <xref:System.Windows.Controls.ScrollBarVisibility> değerini bir <xref:System.Windows.Controls.ListBox> 30 öğe olarak bir <xref:System.Windows.Controls.TextBox> satırlık metin yüzlerce.  
  
<a name="FontCache"></a>   
## <a name="configure-font-cache-service-to-reduce-start-up-time"></a>Başlatma süresini azaltmak için yazı tipi önbellek hizmetini yapılandırma  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Yazı tipi önbellek hizmeti, yazı tipi verileri arasında paylaştığı [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamalar. İlk [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] çalıştırdığınız uygulaması, hizmet zaten çalışmıyorsa bu hizmetini başlatır. Kullanıyorsanız [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)], "Windows Presentation Foundation (WPF) yazı tipi önbellek 3.0.0.0" hizmet "El ile" (varsayılan) "Otomatik (Gecikmeli Başlatma)", ilk başlatma süresini azaltmak için ayarlayabileceğiniz [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamalar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Performansını Planlama](planning-for-application-performance.md)
- [Donanımdan Yararlanma](optimizing-performance-taking-advantage-of-hardware.md)
- [Düzen ve Tasarım](optimizing-performance-layout-and-design.md)
- [2B Grafikleri ve Görüntüleme](optimizing-performance-2d-graphics-and-imaging.md)
- [Nesne Davranışı](optimizing-performance-object-behavior.md)
- [Uygulama Kaynakları](optimizing-performance-application-resources.md)
- [Metin](optimizing-performance-text.md)
- [Veri Bağlama](optimizing-performance-data-binding.md)
- [Animasyon İpuçları ve Püf Noktaları](../graphics-multimedia/animation-tips-and-tricks.md)
