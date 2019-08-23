---
title: Multimedyaya Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF]
- media [WPF]
ms.assetid: feb25b15-d741-4ac3-818f-1b19f63a3562
ms.openlocfilehash: 44059fe96a0deeda18f0abd9079100b55be98e77
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929617"
---
# <a name="multimedia-overview"></a>Multimedyaya Genel Bakış
' Deki [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] multimedya özellikleri, Kullanıcı deneyimini geliştirmek için uygulamalarınızı ses ve videoyu tümleştirmenize imkan tanır. Bu konu, öğesinin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]multimedya özelliklerini tanıtır.  

<a name="mediaapi"></a>   
## <a name="media-api"></a>Medya API 'SI  
 <xref:System.Windows.Controls.MediaElement> Ve<xref:System.Windows.Media.MediaPlayer> sınıfları, ses veya video içeriğini sunmak için kullanılır. Bu sınıflar etkileşimli bir şekilde veya bir saatle denetlenebilir. Bu sınıflar, [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] medya kayıttan yürütme için 10 denetiminde kullanılabilir. Kullandığınız sınıf, senaryoya bağlıdır.  
  
 <xref:System.Windows.Controls.MediaElement>Düzen tarafından desteklenir ve birçok denetimin içeriği olarak tüketilebilir. [](../advanced/layout.md) <xref:System.Windows.UIElement> Ayrıca, kod olarak da [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kullanılabilir. <xref:System.Windows.Media.MediaPlayer>, diğer yandan nesneler için <xref:System.Windows.Media.Drawing> tasarlanmıştır ve düzen desteği yoktur. Kullanılarak <xref:System.Windows.Media.MediaPlayer> yüklenen medya yalnızca <xref:System.Windows.Media.VideoDrawing> veya kullanılarak veya doğrudan ile <xref:System.Windows.Media.DrawingContext>etkileşimde bulunarak sunulabilir. <xref:System.Windows.Media.MediaPlayer>XAML 'de kullanılamaz.  
  
 Çizim nesneleri ve çizim bağlamı hakkında daha fazla bilgi için bkz. [çizim nesnelerine genel bakış](drawing-objects-overview.md).  
  
> [!NOTE]
> Medyayı uygulamanızla dağıtırken proje kaynağı olarak bir medya dosyası kullanamazsınız. Proje dosyanızda, bunun yerine medya `Content` türünü olarak ayarlamanız ve ya `Always`da olarak `PreserveNewest` ayarlamanız `CopyToOutputDirectory` gerekir.  
  
<a name="mediaplaybackmodes"></a>   
## <a name="media-playback-modes"></a>Medya kayıttan yürütme modları  
  
> [!NOTE]
> Her ikisi de <xref:System.Windows.Controls.MediaElement> benzer üyelere sahiptir.<xref:System.Windows.Media.MediaPlayer> Bu bölümdeki bağlantılar <xref:System.Windows.Controls.MediaElement> sınıf üyelerine başvurur. Özellikle belirtilmedikçe, <xref:System.Windows.Controls.MediaElement> sınıfta bağlantılı üyeler de <xref:System.Windows.Media.MediaPlayer> sınıfında bulunabilir.  
  
 Ortamında medya kayıttan yürütmeyi [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]anlamak için, medyanın çalınabilecek farklı modların anlaşılması gerekir. Her ikisi <xref:System.Windows.Controls.MediaElement> de iki farklı medya modunda, bağımsız modda ve saat modunda kullanılabilir. <xref:System.Windows.Media.MediaPlayer> Medya modu, <xref:System.Windows.Controls.MediaElement.Clock%2A> özelliği tarafından belirlenir. Ne zaman olduğunda <xref:System.Windows.Controls.MediaElement.Clock%2A> ,medyanesnesibağımsızmoddadır.`null` <xref:System.Windows.Controls.MediaElement.Clock%2A> Null olmadığında, medya nesnesi saat modundadır. Varsayılan olarak, medya nesneleri bağımsız modundadır.  
  
### <a name="independent-mode"></a>Bağımsız mod  
 Bağımsız modda, medya içeriği medya kayıttan yürütmeyi yürütür. Bağımsız mod aşağıdaki seçenekleri sunar:  
  
- <xref:System.Uri> Medya, doğrudan belirtilebilir.  
  
- Medya kayıttan yürütme doğrudan denetlenebilir.  
  
- <xref:System.Windows.Controls.MediaElement.Position%2A> Medya ve <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> Özellikler değiştirilebilir.  
  
 Medya, <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Media.MediaPlayer.Open%2A> nesnenin <xref:System.Windows.Controls.MediaElement.Source%2A> özelliği<xref:System.Windows.Media.MediaPlayer> ayarlanarak ya da nesnenin yöntemi çağırarak yüklenir.  
  
 Medya kayıttan yürütmeyi bağımsız modda denetlemek için, medya nesnesinin denetim yöntemleri kullanılabilir. Kullanılabilir <xref:System.Windows.Controls.MediaElement.Play%2A>denetim yöntemleri <xref:System.Windows.Controls.MediaElement.Pause%2A> ,<xref:System.Windows.Controls.MediaElement.Close%2A>, ve<xref:System.Windows.Controls.MediaElement.Stop%2A>' dir. İçin <xref:System.Windows.Controls.MediaElement>, bu yöntemleri kullanan etkileşimli denetim yalnızca, <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> olarak <xref:System.Windows.Controls.MediaState.Manual>ayarlandığında kullanılabilir. Medya nesnesi saat modundayken bu yöntemler kullanılamaz.  
  
 Bağımsız mod örneği için bkz. [MediaElement (Play, Duraklat, durdur, hacim ve Speed)](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md) .  
  
### <a name="clock-mode"></a>Saat modu  
 Saat modunda, bir <xref:System.Windows.Media.MediaTimeline> sürücü medyası kayıttan yürütme. Saat modu aşağıdaki özelliklere sahiptir:  
  
- Medya, dolaylı olarak bir <xref:System.Windows.Media.MediaTimeline>ile ayarlanır. <xref:System.Uri>  
  
- Medya kayıttan yürütme, saat tarafından denetlenebilir. Medya nesnesinin denetim yöntemleri kullanılamıyor.  
  
- Medya, bir <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.MediaTimeline.Source%2A> nesnenin özelliği ayarlanarak, zaman çizelgesinden saati oluşturarak ve saati medya nesnesine atanarak yüklenir. Medya, bir ' a <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.Animation.Storyboard> hedeflediğinde <xref:System.Windows.Controls.MediaElement>de bu şekilde yüklenir.  
  
 Medya kayıttan yürütmeyi saat modunda <xref:System.Windows.Media.Animation.ClockController> denetlemek için denetim yöntemlerinin kullanılması gerekir. <xref:System.Windows.Media.Animation.ClockController> <xref:System.Windows.Media.Animation.ClockController> , Öğesinin<xref:System.Windows.Media.MediaClock>özelliğinden elde edilir. Saat modundayken bir <xref:System.Windows.Controls.MediaElement> veya <xref:System.Windows.Media.MediaPlayer> nesnesinin denetim yöntemlerini kullanmaya çalışırsanız, bir <xref:System.InvalidOperationException> oluşturulur.  
  
 Saatler ve zaman çizelgeleri hakkında daha fazla bilgi için [animasyona genel bakış](animation-overview.md) bölümüne bakın.  
  
 Bkz. saat modu örneği için [görsel taslak kullanarak MediaElement 'ı denetleme](how-to-control-a-mediaelement-by-using-a-storyboard.md) .  
  
<a name="mediaelement"></a>   
## <a name="mediaelement-class"></a>MediaElement sınıfı  
 Bir uygulamaya medya eklemek, uygulamanın içine bir <xref:System.Windows.Controls.MediaElement> denetim [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] eklemek ve dahil etmek istediğiniz medyaya sağlamak <xref:System.Uri> kadar basittir. 10 tarafından [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] desteklenen tüm medya türleri ' de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]desteklenir. Aşağıdaki örnek, <xref:System.Windows.Controls.MediaElement> içinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]basit bir kullanımını gösterir.  
  
 [!code-xaml[MediaElement_snip#SimpleMediaElementUsageWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaElement_snip/CSharp/SimpleUsage.xaml#simplemediaelementusagewholepage)]  
  
 Bu örnekte, medya yüklendikten hemen sonra otomatik olarak oynatılır. Medyanın yürütülmesi bittikten sonra medya kapatılır ve tüm medya kaynakları yayın (video belleği dahil) olur. Bu, <xref:System.Windows.Controls.MediaElement> nesnesinin varsayılan davranışıdır ve <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> ve <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> özellikleri tarafından denetlenir.  
  
### <a name="controlling-a-mediaelement"></a>MediaElement 'i denetleme  
 <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.FrameworkElement.IsLoaded%2A> Ve özellikleri, sırasıyla`true` veya ,`false`sırasıyla davranışını denetler. <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> <xref:System.Windows.Controls.MediaState> Özellikler, medya kayıttan yürütme davranışını etkileyecek şekilde ayarlanır. Örneğin <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> , varsayılan <xref:System.Windows.Controls.MediaState.Play> , ve varsayılandır <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> <xref:System.Windows.Controls.MediaState.Close>. Yani, <xref:System.Windows.Controls.MediaElement> yüklendiği anda ve PreRoll tamamlandıktan hemen sonra medya oynatılmaya başlar. Kayıttan yürütme tamamlandıktan sonra medya kapatılır ve tüm medya kaynakları serbest bırakılır.  
  
 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> Ve<xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> özellikleri, medya kayıttan yürütmeyi denetlemek için tek yol değildir. Saat modunda, saat ' i denetleyebilir <xref:System.Windows.Controls.MediaElement> ve etkileşimli denetim yöntemlerinin olduğunda denetimi <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> <xref:System.Windows.Controls.MediaState.Manual>vardır. <xref:System.Windows.Controls.MediaElement>aşağıdaki öncelikleri değerlendirerek denetim için bu yarışma işler.  
  
1. <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>. Medya kaldırıldığında yerinde. Bu, <xref:System.Windows.Media.MediaClock> <xref:System.Windows.Controls.MediaElement>ile ilişkili olduğunda bile tüm medya kaynaklarının varsayılan olarak serbest bırakılacağını sağlar.  
  
2. <xref:System.Windows.Media.MediaClock>. Medyada olduğu <xref:System.Windows.Controls.MediaElement.Clock%2A>zaman yerinde. Medya kaldırıldığında <xref:System.Windows.Media.MediaClock> , <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> olduğu <xref:System.Windows.Controls.MediaState.Manual>sürece geçerli olur. Saat modu, <xref:System.Windows.Controls.MediaElement>uygulamasının yüklenen davranışını her zaman geçersiz kılar.  
  
3. <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>. Medya yüklendiğinde yerinde.  
  
4. Etkileşimli denetim yöntemleri. Ne zaman <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> <xref:System.Windows.Controls.MediaState.Manual>yerinde. Kullanılabilir <xref:System.Windows.Controls.MediaElement.Play%2A>denetim yöntemleri <xref:System.Windows.Controls.MediaElement.Pause%2A> ,<xref:System.Windows.Controls.MediaElement.Close%2A>, ve<xref:System.Windows.Controls.MediaElement.Stop%2A>' dir.  
  
### <a name="displaying-a-mediaelement"></a>MediaElement 'i görüntüleme  
 Göstermek için, <xref:System.Windows.Controls.MediaElement> bir içeriğin işlenmesi gerekir ve içerik yükleninceye kadar, <xref:System.Windows.FrameworkElement.ActualWidth%2A> ve <xref:System.Windows.FrameworkElement.ActualHeight%2A> özellikleri sıfır olarak ayarlanır. Yalnızca ses içeriği için bu özellikler her zaman sıfırdır. Video içeriği için, <xref:System.Windows.Controls.MediaElement.MediaOpened> olay <xref:System.Windows.FrameworkElement.ActualWidth%2A> <xref:System.Windows.FrameworkElement.ActualHeight%2A> uygulandıktan sonra yüklenen medyanın boyutunu rapor eder. Bu, medya yüklenene <xref:System.Windows.Controls.MediaElement> kadar, <xref:System.Windows.FrameworkElement.Width%2A> veya <xref:System.Windows.FrameworkElement.Height%2A> özellikleri ayarlanmadığı [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] sürece ' de herhangi bir fiziksel alanı kaplamayacak anlamına gelir.  
  
 Hem hem de <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> özelliklerinin ayarlanması, medyanın, <xref:System.Windows.Controls.MediaElement>için belirtilen alanı dolduracak şekilde uzamasına neden olur. Medyanın özgün en boy oranını korumak için <xref:System.Windows.FrameworkElement.Width%2A> ya <xref:System.Windows.FrameworkElement.Height%2A> da özelliği ayarlanmalıdır, ancak her ikisi birden belirtilmemelidir. Hem hem de <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> özelliklerinin ayarlanması, medyanın istenmeyen sabit bir öğe boyutunda olmasına neden olur.  
  
 Sabit boyutlu bir öğe kullanmaktan kaçınmak için, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] medyayı ön yükleyebilir. Bu, <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> ya <xref:System.Windows.Controls.MediaState.Play>da' a ayarlanarak yapılır. <xref:System.Windows.Controls.MediaState.Pause> Bir <xref:System.Windows.Controls.MediaState.Pause> durumda, medya ön, ön ek olur ve ilk kareyi sunacaktır. Bir <xref:System.Windows.Controls.MediaState.Play> durumda, medya ön ek olur ve yürütmeye başlar.  
  
<a name="mediaplayer"></a>   
## <a name="mediaplayer-class"></a>MediaPlayer Sınıfı  
 Sınıfın çerçeve öğesi olduğu yerlerde <xref:System.Windows.Media.MediaPlayer> , sınıfı <xref:System.Windows.Media.Drawing> nesnelerinde kullanılmak üzere tasarlanmıştır. <xref:System.Windows.Controls.MediaElement> Çizim nesneleri, performans avantajları elde etmek veya özelliklerden yararlanmak için çerçeve düzeyi özelliklerinin Fede olması <xref:System.Windows.Freezable> durumunda kullanılır. <xref:System.Windows.Media.MediaPlayer>, uygulamalarınızda medya içeriği sağlarken bu özelliklerden yararlanmanızı sağlar. Benzer <xref:System.Windows.Controls.MediaElement>şekilde <xref:System.Windows.Media.MediaPlayer> , bağımsız veya saat modunda kullanılabilir <xref:System.Windows.Controls.MediaElement> ancak nesnenin yüklenmemiş ve yüklü durumları yoktur. Bu, <xref:System.Windows.Media.MediaPlayer>öğesinin kayıttan yürütme denetim karmaşıklığını azaltır.  
  
### <a name="controlling-mediaplayer"></a>MediaPlayer 'yi denetleme  
 Durum <xref:System.Windows.Media.MediaPlayer> bilgisiz olduğundan, medya kayıttan yürütmeyi denetlemek için yalnızca iki yol vardır.  
  
1. Etkileşimli denetim yöntemleri. Bağımsız modda (`null` <xref:System.Windows.Media.MediaPlayer.Clock%2A> özellik) yerinde.  
  
2. <xref:System.Windows.Media.MediaClock>. Medyada olduğu <xref:System.Windows.Media.MediaPlayer.Clock%2A>zaman yerinde.  
  
### <a name="displaying-a-mediaplayer"></a>MediaPlayer görüntüleme  
 Teknik olarak, <xref:System.Windows.Media.MediaPlayer> bir fiziksel temsili olmadığından görüntülenemez. Ancak, <xref:System.Windows.Media.Drawing> <xref:System.Windows.Media.VideoDrawing> sınıfını kullanarak bir ortamında medya sunmak için kullanılabilir. Aşağıdaki örnek, uygulamasının <xref:System.Windows.Media.VideoDrawing> görüntüleme medyası kullanımını gösterir.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Nesneler hakkında <xref:System.Windows.Media.Drawing> daha fazla bilgi için bkz. [çizim nesnelerine genel bakış](drawing-objects-overview.md) .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.DrawingGroup>
- [Düzen](../advanced/layout.md)
- [Nasıl Yapılır Konuları](audio-and-video-how-to-topics.md)
