---
title: 'Performansı İyileştirme: Diğer Öneriler'
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
ms.openlocfilehash: 6b4a5379145ebdffde0d5b76d8c7b9ab57261007
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975784"
---
# <a name="optimizing-performance-other-recommendations"></a>Performansı İyileştirme: Diğer Öneriler
<a name="introduction"></a>Bu konu, [WPF uygulama performansını En Iyi duruma getirme](optimizing-wpf-application-performance.md) bölümünde yer almayan konular kapsamında ele alınanlara ek olarak performans önerileri sağlar.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
- [Fırçalar üzerinde opaklık ve öğeler üzerinde opaklık](#Opacity)  
  
- [Nesneye gezinti](#Navigation_Objects)  
  
- [Büyük 3B yüzeyler üzerinde isabet testi](#Hit_Testing)  
  
- [Kompozisyontiontarget. Rendering olayı](#CompositionTarget_Rendering_Event)  
  
- [ScrollBarVisibility = Auto kullanmaktan kaçının](#Avoid_Using_ScrollBarVisibility)  
  
- [Başlangıç saatini azaltmak için yazı tipi önbellek hizmetini yapılandırın](#FontCache)  
  
<a name="Opacity"></a>   
## <a name="opacity-on-brushes-versus-opacity-on-elements"></a>Fırçalar üzerinde opaklık ve öğeler üzerinde opaklık  
 Bir öğenin <xref:System.Windows.Shapes.Shape.Fill%2A> veya <xref:System.Windows.Shapes.Shape.Stroke%2A> ayarlamak için bir <xref:System.Windows.Media.Brush> kullandığınızda, öğenin <xref:System.Windows.UIElement.Opacity%2A> özelliğini ayarlamak yerine <xref:System.Windows.Media.Brush.Opacity%2A?displayProperty=nameWithType> değeri ayarlamak daha iyidir. Bir öğenin <xref:System.Windows.UIElement.Opacity%2A> özelliğini değiştirmek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] geçici bir yüzey oluşturulmasına neden olabilir.  
  
<a name="Navigation_Objects"></a>   
## <a name="navigation-to-object"></a>Nesneye gezinti  
 <xref:System.Windows.Navigation.NavigationWindow> nesnesi <xref:System.Windows.Window> türetilir ve öncelikle <xref:System.Windows.Navigation.NavigationService> ve günlüğü toplayarak içerik gezintisi desteğiyle genişletir. Bir Tekdüzen Kaynak tanımlayıcısı (URI) veya bir nesnesi belirterek <xref:System.Windows.Navigation.NavigationWindow> istemci alanını güncelleştirebilirsiniz. Aşağıdaki örnek her iki yöntemi göstermektedir:  
  
 [!code-csharp[Performance#PerformanceSnippet14](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/TestNavigation.xaml.cs#performancesnippet14)]
 [!code-vb[Performance#PerformanceSnippet14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/testnavigation.xaml.vb#performancesnippet14)]  
  
 Her bir <xref:System.Windows.Navigation.NavigationWindow> nesnesinin, bu pencerede kullanıcının gezinti geçmişini kaydeden bir günlüğü vardır. Günlüğün amaçlarından biri, kullanıcıların kendi adımlarını yeniden izlemesine izin vermelidir.  
  
 Tekdüzen Kaynak tanımlayıcısı (URI) kullanarak gittiğinizde, günlük yalnızca Tekdüzen Kaynak tanımlayıcısı (URI) başvurusunu depolar. Bu, sayfayı her ziyaret ettiğiniz zaman dinamik olarak yeniden oluşturulduğu ve sayfanın karmaşıklığına bağlı olarak zaman alıcı olabilen bir anlamına gelir. Bu durumda, günlük depolama maliyeti düşüktür, ancak sayfanın edilmeyen süresi yüksek olabilir.  
  
 Bir nesne kullanarak gittiğinizde, günlük nesnenin tüm görsel ağacını depolar. Bu, sayfayı her ziyaret ettiğiniz zaman yeniden yapılandırılması gerekmeden hemen işlediğini anlamına gelir. Bu durumda, günlük depolama maliyeti yüksektir, ancak sayfanın edilmeyen süresi düşüktür.  
  
 <xref:System.Windows.Navigation.NavigationWindow> nesnesini kullandığınızda, günlüğe kaydetme desteğinin uygulamanızın performansını nasıl etkilediğini göz önünde bulundurmanız gerekir. Daha fazla bilgi için bkz. [gezintiye genel bakış](../app-development/navigation-overview.md).  
  
<a name="Hit_Testing"></a>   
## <a name="hit-testing-on-large-3d-surfaces"></a>Büyük 3B yüzeyler üzerinde isabet testi  
 Büyük 3B yüzeyler üzerinde isabet testi, CPU tüketimi açısından çok performanslı, yoğun bir işlemdir. Bu, 3B Yüzey animasyon eklendiğinde özellikle doğrudur. Bu yüzeyler üzerinde isabet testi gerektirmiyorsa, isabet sınamasını devre dışı bırakın. <xref:System.Windows.UIElement> türetilen nesneler <xref:System.Windows.UIElement.IsHitTestVisible%2A> özelliğini `false`ayarlayarak isabet sınamasını devre dışı bırakabilir.  
  
<a name="CompositionTarget_Rendering_Event"></a>   
## <a name="compositiontargetrendering-event"></a>Kompozisyontiontarget. Rendering olayı  
 <xref:System.Windows.Media.CompositionTarget.Rendering?displayProperty=nameWithType> olay, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sürekli olarak animasyon almasına neden olur. Bu olayı kullanırsanız, her fırsat üzerinde ayırın.  
  
<a name="Avoid_Using_ScrollBarVisibility"></a>   
## <a name="avoid-using-scrollbarvisibilityauto"></a>ScrollBarVisibility = Auto kullanmaktan kaçının  
 Mümkün olduğunda, `HorizontalScrollBarVisibility` ve `VerticalScrollBarVisibility` özellikleri için <xref:System.Windows.Controls.ScrollBarVisibility.Auto?displayProperty=nameWithType> değerini kullanmaktan kaçının. Bu özellikler <xref:System.Windows.Controls.RichTextBox>, <xref:System.Windows.Controls.ScrollViewer> ve <xref:System.Windows.Controls.TextBox> nesneleri için ve <xref:System.Windows.Controls.ListBox> nesnesi için iliştirilmiş bir özellik olarak tanımlanmıştır. Bunun yerine, <xref:System.Windows.Controls.ScrollBarVisibility> <xref:System.Windows.Controls.ScrollBarVisibility.Disabled>, <xref:System.Windows.Controls.ScrollBarVisibility.Hidden> veya <xref:System.Windows.Controls.ScrollBarVisibility.Visible> olarak ayarlayın.  
  
 <xref:System.Windows.Controls.ScrollBarVisibility.Auto> değeri, boşluk sınırlı olduğunda ve kaydırma çubuklarının yalnızca gerektiğinde görüntülenmesi gerektiği durumlar için tasarlanmıştır. Örneğin, yüzlerce satırlık metin içeren bir <xref:System.Windows.Controls.TextBox> aksine bu <xref:System.Windows.Controls.ScrollBarVisibility> değerini 30 öğe <xref:System.Windows.Controls.ListBox> ile kullanmak yararlı olabilir.  
  
<a name="FontCache"></a>   
## <a name="configure-font-cache-service-to-reduce-start-up-time"></a>Başlangıç saatini azaltmak için yazı tipi önbellek hizmetini yapılandırın  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] yazı tipi önbellek hizmeti, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamalar arasında yazı tipi verilerini paylaşır. Çalıştırdığınız ilk [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulaması, hizmet zaten çalışmıyorsa bu hizmeti başlatır. Windows Vista kullanıyorsanız, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamalarının ilk başlangıç zamanını azaltmak için "Windows Presentation Foundation (WPF) yazı tipi önbelleği 3.0.0.0" hizmetini "El Ile" (varsayılan) "otomatik (Gecikmeli başlatma)" olarak ayarlayabilirsiniz.  
  
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
