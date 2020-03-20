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
ms.openlocfilehash: 727331adb41251460209f157d1804ff455bcf473
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186296"
---
# <a name="optimizing-performance-other-recommendations"></a>Performansı İyileştirme: Diğer Öneriler
<a name="introduction"></a>Bu konu, [WPF Uygulama Performansını Optimize Etme](optimizing-wpf-application-performance.md) bölümündeki konuların kapsadığı konulara ek olarak performans önerileri sağlar.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
- [Fırçalarda Elementlerde Opaklık](#Opacity)  
  
- [Nesneye Gezinme](#Navigation_Objects)  
  
- [Büyük 3B Yüzeylerde Hit Testi](#Hit_Testing)  
  
- [CompositionTarget.RenderOlay](#CompositionTarget_Rendering_Event)  
  
- [ScrollBarVisibility=Auto kullanmaktan kaçının](#Avoid_Using_ScrollBarVisibility)  
  
- [Başlangıç Süresini Azaltmak için Font Önbelleği Hizmetini Yapılandırın](#FontCache)  
  
<a name="Opacity"></a>
## <a name="opacity-on-brushes-versus-opacity-on-elements"></a>Fırçalarda Elementlerde Opaklık  
 Bir öğeyi <xref:System.Windows.Media.Brush> <xref:System.Windows.Shapes.Shape.Fill%2A> ayarlamak <xref:System.Windows.Shapes.Shape.Stroke%2A> için a kullandığınızda, öğenin <xref:System.Windows.Media.Brush.Opacity%2A?displayProperty=nameWithType> <xref:System.Windows.UIElement.Opacity%2A> özelliğini ayarlamak yerine değeri ayarlamak daha iyidir. Bir öğenin özelliğini <xref:System.Windows.UIElement.Opacity%2A> değiştirmek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] geçici bir yüzey oluşturmaya neden olabilir.  
  
<a name="Navigation_Objects"></a>
## <a name="navigation-to-object"></a>Nesneye Gezinme  
 Nesne, <xref:System.Windows.Navigation.NavigationWindow> öncelikle toplama <xref:System.Windows.Window> <xref:System.Windows.Navigation.NavigationService> ve günlük tarafından içerik gezintisi desteğinden türetilmiştir ve genişletir. Tek düzen kaynak tanımlayıcısı (URI) veya bir nesne <xref:System.Windows.Navigation.NavigationWindow> belirterek istemci alanını güncelleştirebilirsiniz. Aşağıdaki örnek her iki yöntemi de gösterir:  
  
 [!code-csharp[Performance#PerformanceSnippet14](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/TestNavigation.xaml.cs#performancesnippet14)]
 [!code-vb[Performance#PerformanceSnippet14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/testnavigation.xaml.vb#performancesnippet14)]  
  
 Her <xref:System.Windows.Navigation.NavigationWindow> nesnenin, kullanıcının gezinti geçmişini bu pencerede kaydeden bir günlüğü vardır. Günlüğün amaçlarından biri, kullanıcıların adımlarını yeniden izlemelerine izin vermektir.  
  
 Tek düzen kaynak tanımlayıcısı (URI) kullanarak gezinirken, günlük yalnızca tek düzen kaynak tanımlayıcısı (URI) başvurularını depolar. Bu, sayfayı her yeniden ziyaret edilince, sayfanın karmaşıklığına bağlı olarak zaman alıcı olabilecek dinamik olarak yeniden oluşturuldurabileceği anlamına gelir. Bu durumda, günlük depolama maliyeti düşüktür, ancak sayfayı yeniden oluşturma süresi potansiyel olarak yüksektir.  
  
 Bir nesneyi kullanarak gezindiğinizde, günlük nesnenin tüm görsel ağacını depolar. Bu, sayfayı her yeniden ziyaret edilince, sayfanın yeniden oluşturulmak zorunda kalmadan hemen işlendiği anlamına gelir. Bu durumda, günlük depolama maliyeti yüksektir, ancak sayfayı yeniden oluşturma zamanı düşüktür.  
  
 Nesneyi <xref:System.Windows.Navigation.NavigationWindow> kullandığınızda, günlük desteğinin uygulamanızın performansını nasıl etkilediğini aklınızda bulundurmanız gerekir. Daha fazla bilgi için [Gezintiye Genel Bakış'a](../app-development/navigation-overview.md)bakın.  
  
<a name="Hit_Testing"></a>
## <a name="hit-testing-on-large-3d-surfaces"></a>Büyük 3B Yüzeylerde Hit Testi  
 Büyük 3B yüzeylerde isabet testi CPU tüketimi açısından çok performans yoğun bir işlemdir. Bu, özellikle 3B yüzey imiyating olduğunda doğrudur. Bu yüzeylerde isabet testi gerektirmezseniz, isabet testini devre dışı k. Türetilen nesneler <xref:System.Windows.UIElement> <xref:System.Windows.UIElement.IsHitTestVisible%2A> özelliği `false`' ne ayarlayarak hit testi devre dışı atabilir.  
  
<a name="CompositionTarget_Rendering_Event"></a>
## <a name="compositiontargetrendering-event"></a>CompositionTarget.RenderOlay  
 Olay <xref:System.Windows.Media.CompositionTarget.Rendering?displayProperty=nameWithType> sürekli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyon neden olur. Bu olayı kullanırsanız, her fırsatta ayırın.  
  
<a name="Avoid_Using_ScrollBarVisibility"></a>
## <a name="avoid-using-scrollbarvisibilityauto"></a>ScrollBarVisibility=Auto kullanmaktan kaçının  
 Mümkün olduğunda, değeri <xref:System.Windows.Controls.ScrollBarVisibility.Auto?displayProperty=nameWithType> `HorizontalScrollBarVisibility` ve `VerticalScrollBarVisibility` özellikleri için kullanmaktan kaçının. Bu özellikler, <xref:System.Windows.Controls.RichTextBox> <xref:System.Windows.Controls.ListBox> nesne <xref:System.Windows.Controls.ScrollViewer>için <xref:System.Windows.Controls.TextBox> ve nesne için ekli bir özellik olarak tanımlanır. Bunun yerine, <xref:System.Windows.Controls.ScrollBarVisibility.Disabled> <xref:System.Windows.Controls.ScrollBarVisibility.Hidden>ayarlayın <xref:System.Windows.Controls.ScrollBarVisibility> <xref:System.Windows.Controls.ScrollBarVisibility.Visible>, , veya .  
  
 Değer, alanın sınırlı olduğu ve kaydırma çubuklarının <xref:System.Windows.Controls.ScrollBarVisibility.Auto> yalnızca gerektiğinde görüntülenmesi gereken durumlar için tasarlanmıştır. Örneğin, bu <xref:System.Windows.Controls.ScrollBarVisibility> değeri <xref:System.Windows.Controls.ListBox> yüzlerce metin satırıyla karşı sırayla 30 <xref:System.Windows.Controls.TextBox> öğeden oluşan bir değerle kullanmak yararlı olabilir.  
  
<a name="FontCache"></a>
## <a name="configure-font-cache-service-to-reduce-start-up-time"></a>Başlangıç Süresini Azaltmak için Font Önbelleği Hizmetini Yapılandırın  
 WPF Font Önbelleği hizmeti, yazı tipi verilerini WPF uygulamaları arasında paylaşır. Çalıştırdığınız ilk WPF uygulaması, hizmet zaten çalışmıyorsa bu hizmeti başlatır. Windows Vista kullanıyorsanız, WPF uygulamalarının başlangıç süresini azaltmak için "Windows Presentation Foundation (WPF) Font Önbelleği 3.0.0.0" hizmetini "El Ile" (varsayılan) ile "Otomatik (Gecikmeli Başlat)" olarak ayarlayabilirsiniz.  
  
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
