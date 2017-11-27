---
title: "Performansı İyileştirme: Diğer Öneriler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eda112db6dd977b6ef25a1b3a9ae40349d3a045f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="optimizing-performance-other-recommendations"></a>Performansı İyileştirme: Diğer Öneriler
<a name="introduction"></a>Bu konu, konular tarafından kapsanan olanları yanı sıra performans önerileri sağlar [WPF Uygulama performansı en iyi duruma getirme](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md) bölümü.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
-   [Opaklık karşı öğeler üzerinde Fırçalar üzerinde](#Opacity)  
  
-   [Nesneye Gezinti](#Navigation_Objects)  
  
-   [İsabet üzerinde büyük 3B yüzeyleri sınaması](#Hit_Testing)  
  
-   [CompositionTarget.işleme olayı](#CompositionTarget_Rendering_Event)  
  
-   [ScrollBarVisibility kullanmaktan kaçının otomatik =](#Avoid_Using_ScrollBarVisibility)  
  
-   [Başlatma süresini azaltmak için yazı tipi önbelleği hizmetini yapılandırma](#FontCache)  
  
<a name="Opacity"></a>   
## <a name="opacity-on-brushes-versus-opacity-on-elements"></a>Opaklık karşı öğeler üzerinde Fırçalar üzerinde  
 Kullandığınızda, bir <xref:System.Windows.Media.Brush> ayarlamak için <xref:System.Windows.Shapes.Shape.Fill%2A> veya <xref:System.Windows.Shapes.Shape.Stroke%2A> bir öğenin ayarlamak daha iyi <xref:System.Windows.Media.Brush.Opacity%2A?displayProperty=nameWithType> yerine ayarı değeri öğenin <xref:System.Windows.UIElement.Opacity%2A> özelliği. Bir öğenin değiştirme <xref:System.Windows.UIElement.Opacity%2A> özelliği neden olabilecek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] geçici yüzey oluşturmak için.  
  
<a name="Navigation_Objects"></a>   
## <a name="navigation-to-object"></a>Nesneye Gezinti  
 <xref:System.Windows.Navigation.NavigationWindow> Nesne türer <xref:System.Windows.Window> ve öncelikle toplayarak içerik gezinti desteği ile genişletir <xref:System.Windows.Navigation.NavigationService> ve günlük. İstemci alanını güncelleştirebilirsiniz <xref:System.Windows.Navigation.NavigationWindow> ya da belirterek bir [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] veya bir nesne. Aşağıdaki örnek, her iki yöntem gösterir:  
  
 [!code-csharp[Performance#PerformanceSnippet14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/TestNavigation.xaml.cs#performancesnippet14)]
 [!code-vb[Performance#PerformanceSnippet14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/testnavigation.xaml.vb#performancesnippet14)]  
  
 Her <xref:System.Windows.Navigation.NavigationWindow> nesnesi bu penceresinde kullanıcının Gezinti geçmişini kaydeden bir günlük sahiptir. Günlük amacı kullanıcıların kendi adımları yeniden izlemesine izin vermek için biridir.  
  
 Kullanarak gittiğinizde bir [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], günlük yalnızca depolar [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] başvuru. Bunun anlamı her sayfanın yeniden ziyaret, bunu dinamik olarak, zaman alıcıdır ve sayfa karmaşıklığına bağlı olarak olabilecek yeniden düzenlenir. Bu durumda, günlüğün depolama maliyeti düşüktür, ancak sayfa yeniden oluşturma zamanı olasılığı yüksektir.  
  
 Bir nesne kullanarak gittiğinizde günlük görsel nesne ağacının tümünü depolar. Bu sayfa yeniden ziyaret her seferinde onu hemen oluşturulmadan gerek kalmadan anlamına gelir. Bu durumda, günlüğün depolama maliyeti yüksek, ancak sayfa yeniden oluşturma zamanı düşüktür.  
  
 Kullandığınızda <xref:System.Windows.Navigation.NavigationWindow> nesnesi, günlük kaydı desteğinin uygulamanızın performansını nasıl etkilediğini göz önünde bulundurmanız gerekir. Daha fazla bilgi için bkz: [Gezinti genel bakış](../../../../docs/framework/wpf/app-development/navigation-overview.md).  
  
<a name="Hit_Testing"></a>   
## <a name="hit-testing-on-large-3d-surfaces"></a>İsabet üzerinde büyük 3B yüzeyleri sınaması  
 İsabet testi büyük 3B Yüzey üzerinde bir çok performansı yoğun CPU tüketimi açısından işlemdir. Bu, özellikle 3B Yüzey hareketli olduğunda geçerlidir. Ardından bu yüzey üzerinde isabet testi gerektirmiyorsa isabet testi devre dışı. Öğesinden türetilen nesneler <xref:System.Windows.UIElement> devre dışı bırak isabet ayarlayarak sınaması <xref:System.Windows.UIElement.IsHitTestVisible%2A> özelliğine `false`.  
  
<a name="CompositionTarget_Rendering_Event"></a>   
## <a name="compositiontargetrendering-event"></a>CompositionTarget.işleme olayı  
 <xref:System.Windows.Media.CompositionTarget.Rendering?displayProperty=nameWithType> Olaya neden [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sürekli olarak hareketli için. Bu olayı kullanırsanız, her fırsatta kullanımdan çıkarın.  
  
<a name="Avoid_Using_ScrollBarVisibility"></a>   
## <a name="avoid-using-scrollbarvisibilityauto"></a>ScrollBarVisibility kullanmaktan kaçının otomatik =  
 Mümkün olduğunda, kullanmaktan kaçının <xref:System.Windows.Controls.ScrollBarVisibility.Auto?displayProperty=nameWithType> değerini `HorizontalScrollBarVisibility` ve `VerticalScrollBarVisibility` özellikleri. Bu özellikler için tanımlanan <xref:System.Windows.Controls.RichTextBox>, <xref:System.Windows.Controls.ScrollViewer>, ve <xref:System.Windows.Controls.TextBox> nesneleri ve için eklenen bir özellik olarak <xref:System.Windows.Controls.ListBox> nesnesi. Bunun yerine, ayarlamak <xref:System.Windows.Controls.ScrollBarVisibility> için <xref:System.Windows.Controls.ScrollBarVisibility.Disabled>, <xref:System.Windows.Controls.ScrollBarVisibility.Hidden>, veya <xref:System.Windows.Controls.ScrollBarVisibility.Visible>.  
  
 <xref:System.Windows.Controls.ScrollBarVisibility.Auto> Alanı sınırlıdır ve kaydırma çubukları, yalnızca gerekli olduğunda görüntülenecek değer durumlar için amaçlanmıştır. Örneğin, bunu kullanmak yararlı olabilir <xref:System.Windows.Controls.ScrollBarVisibility> değerini bir <xref:System.Windows.Controls.ListBox> tersine 30 öğelerinin bir <xref:System.Windows.Controls.TextBox> satırlık metin yüzlerce.  
  
<a name="FontCache"></a>   
## <a name="configure-font-cache-service-to-reduce-start-up-time"></a>Başlatma süresini azaltmak için yazı tipi önbelleği hizmetini yapılandırma  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Yazı tipi önbellek hizmeti arasında yazı tipi veri paylaşır [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamalar. İlk [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] çalıştırdığınız uygulama hizmet zaten çalışmıyorsa bu hizmetini başlatır. Kullanıyorsanız [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)], ayarlayabileceğiniz "[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] yazı tipi önbelleği 3.0.0.0" hizmet "Elle" (varsayılan)'den "ilk başlangıç zamanını azaltmak için otomatik (Gecikmeli Başlangıç)" [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamalar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uygulama performansını planlama](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [Donanım yararlanarak](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [Düzen ve tasarım](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [2B grafik ve görüntü](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Nesne davranışı](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [Uygulama kaynakları](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Metin](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Veri bağlama](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Animasyon ipuçları ve püf noktaları](../../../../docs/framework/wpf/graphics-multimedia/animation-tips-and-tricks.md)
