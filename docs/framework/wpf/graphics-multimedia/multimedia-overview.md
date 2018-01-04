---
title: "Multimedyaya Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multimedia [WPF]
- media [WPF]
ms.assetid: feb25b15-d741-4ac3-818f-1b19f63a3562
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 65553e18fc66825c9c0a991aba600b4b90d0d4c0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="multimedia-overview"></a>Multimedyaya Genel Bakış
Multimedya özellikleri [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ses ve video kullanıcı deneyimini geliştirmek için uygulamalarınıza tümleştirmenize olanak sağlar. Bu konu multimedya özelliklerini tanıtır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 
  
<a name="mediaapi"></a>   
## <a name="media-api"></a>Ortam API  
 <xref:System.Windows.Controls.MediaElement> Ve <xref:System.Windows.Media.MediaPlayer> sınıfları, ses veya video içeriği sunmak için kullanılır. Bu sınıfları, etkileşimli olarak veya bir saat ile denetlenebilir. Bu sınıfların kullanabilirsiniz [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] medya kayıttan yürütme için 10 denetimi. Kullandığınız, hangi sınıfın senaryoya bağlıdır.  
  
 <xref:System.Windows.Controls.MediaElement>olan bir <xref:System.Windows.UIElement> tarafından desteklenen [düzeni](../../../../docs/framework/wpf/advanced/layout.md) ve birçok denetimleri içeriği olarak tüketilebilir. Ayrıca kullanılabilir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] yanı sıra kodu. <xref:System.Windows.Media.MediaPlayer>, diğer yandan için tasarlanmış <xref:System.Windows.Media.Drawing> nesneleri ve düzen desteğini azaltır. Kullanılarak yüklenen ortam bir <xref:System.Windows.Media.MediaPlayer> kullanarak yalnızca sunulabilen bir <xref:System.Windows.Media.VideoDrawing> veya doğrudan etkileşimde bir <xref:System.Windows.Media.DrawingContext>. <xref:System.Windows.Media.MediaPlayer>XAML'de kullanılamaz.  
  
 Çizim nesneleri ve içeriği çizim hakkında daha fazla bilgi için bkz: [çizim nesnelere genel bakış](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).  
  
> [!NOTE]
>  Uygulamanız ile birlikte medyayı dağıtırken, medya dosyasını proje kaynağı olarak kullanamazsınız. Proje dosyanızda, bunun yerine medya türü ayarlamalısınız `Content` ve `CopyToOutputDirectory` için `PreserveNewest` veya `Always`.  
  
<a name="mediaplaybackmodes"></a>   
## <a name="media-playback-modes"></a>Medya Kayıttan çalma modları  
  
> [!NOTE]
>  Her ikisi de <xref:System.Windows.Controls.MediaElement> ve <xref:System.Windows.Media.MediaPlayer> benzer üyelere sahiptir. Bu bölümdeki bağlantılar başvurmak <xref:System.Windows.Controls.MediaElement> sınıfı üyeleri. Özellikle belirtilmedikçe bağlantılı üyeler <xref:System.Windows.Controls.MediaElement> sınıfı ayrıca bulunabilir <xref:System.Windows.Media.MediaPlayer> sınıfı.  
  
 Medya kayıttan yürütme anlamak için [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], içinde yürütülen ortam farklı modlarını anlaşılması gereklidir. Her ikisi de <xref:System.Windows.Controls.MediaElement> ve <xref:System.Windows.Media.MediaPlayer> iki farklı ortam modunda, bağımsız mod ve saat modunda kullanılabilir. Ortam modu belirlenir <xref:System.Windows.Controls.MediaElement.Clock%2A> özelliği. Zaman <xref:System.Windows.Controls.MediaElement.Clock%2A> olan `null`, ortam nesnesi bağımsız modda olur. Zaman <xref:System.Windows.Controls.MediaElement.Clock%2A> olan null olmayan, ortam nesnesi saat modunda olur. Varsayılan olarak, medya bağımsız modda nesneleridir.  
  
### <a name="independent-mode"></a>Bağımsız mod  
 Bağımsız modda medya içeriği medya kayıttan yürütme sürücüleri. Bağımsız mod aşağıdaki seçenekleri sağlar:  
  
-   Ortam <xref:System.Uri> doğrudan belirtilebilir.  
  
-   Media çalma doğrudan denetlenebilir.  
  
-   Ortam <xref:System.Windows.Controls.MediaElement.Position%2A> ve <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> özellikleri değiştirilebilir.  
  
 Medya ya da ayarı tarafından yüklenen <xref:System.Windows.Controls.MediaElement> nesnenin <xref:System.Windows.Controls.MediaElement.Source%2A> özelliği veya çağırarak <xref:System.Windows.Media.MediaPlayer> nesnesinin <xref:System.Windows.Media.MediaPlayer.Open%2A> yöntemi.  
  
 Medya Kayıttan bağımsız modda denetlemek için ortam nesnesinin denetim yöntemleri kullanılabilir. Kullanılabilir denetim yöntemleri <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, <xref:System.Windows.Controls.MediaElement.Close%2A>, ve <xref:System.Windows.Controls.MediaElement.Stop%2A>. İçin <xref:System.Windows.Controls.MediaElement>, bu yöntemleri kullanarak etkileşimli denetim kullanılabilir yalnızca ne zaman <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> ayarlanır <xref:System.Windows.Controls.MediaState.Manual>. Bu yöntemler, ortam nesnesi saat modunda olduğunda kullanılamaz.  
  
 Bkz: [MediaElement (Play, duraklatma, durdurma, birim ve hız) kontrol](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md) bağımsız mod örneği.  
  
### <a name="clock-mode"></a>Saat modu  
 Saat modunda bir <xref:System.Windows.Media.MediaTimeline> sürücüleri medya kayıttan yürütme. Saat modu aşağıdaki özelliklere sahiptir:  
  
-   Ortam <xref:System.Uri> üzerinden dolaylı olarak ayarlanmış bir <xref:System.Windows.Media.MediaTimeline>.  
  
-   Medya kayıttan yürütme saati tarafından denetlenebilir. Ortam nesnesinin denetim yöntemleri kullanılamaz.  
  
-   Medya ayarlayarak yüklendiği bir <xref:System.Windows.Media.MediaTimeline> nesnenin <xref:System.Windows.Media.MediaTimeline.Source%2A> çizelgesinden saati oluşturarak ve bu saati ortam nesnesine atayarak özelliği. Medya bu şekilde de yüklü olduğunda bir <xref:System.Windows.Media.MediaTimeline> içinde bir <xref:System.Windows.Media.Animation.Storyboard> hedefleri bir <xref:System.Windows.Controls.MediaElement>.  
  
 Saat modunda ortam kayıttan yürütmeyi denetlemek için <xref:System.Windows.Media.Animation.ClockController> denetim yöntemleri kullanılmalıdır. A <xref:System.Windows.Media.Animation.ClockController> öğesinden alınan <xref:System.Windows.Media.Animation.ClockController> özelliği <xref:System.Windows.Media.MediaClock>. Ya da denetim yöntemlerini kullanmayı denerseniz, bir <xref:System.Windows.Controls.MediaElement> veya <xref:System.Windows.Media.MediaPlayer> Saat modundayken nesne bir <xref:System.InvalidOperationException> oluşturulur.  
  
 Bkz: [animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) zaman çizelgeleri ve saatler hakkında daha fazla bilgi.  
  
 Bkz: [film şeridi kullanarak MediaElement'i kontrol](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-by-using-a-storyboard.md) saat modu örneği.  
  
<a name="mediaelement"></a>   
## <a name="mediaelement-class"></a>MediaElement sınıfı  
 Medya uygulamaya ekleme kadar basittir bir <xref:System.Windows.Controls.MediaElement> denetimini [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] uygulamanın ve sağlama bir <xref:System.Uri> dahil etmek istediğiniz ortam için. Tarafından desteklenen tüm medya türleri [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] 10 de desteklenmektedir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Aşağıdaki örnek, bir basit kullanımını gösterir <xref:System.Windows.Controls.MediaElement> içinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
 [!code-xaml[MediaElement_snip#SimpleMediaElementUsageWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaElement_snip/CSharp/SimpleUsage.xaml#simplemediaelementusagewholepage)]  
  
 Bu örnekte, ortam otomatik olarak yüklendiği hemen oynatılır. Media çalma tamamladığında, ortam kapatılır ve sürüm (video belleği dahil) tüm medya kaynaklardır. Bu, varsayılan davranıştır <xref:System.Windows.Controls.MediaElement> nesne ve tarafından denetlenen <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> ve <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> özellikleri.  
  
### <a name="controlling-a-mediaelement"></a>MediaElement'i denetleme  
 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> Ve <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> davranışını denetim özelliklerini <xref:System.Windows.Controls.MediaElement> zaman <xref:System.Windows.FrameworkElement.IsLoaded%2A> olan `true` veya `false`sırasıyla. <xref:System.Windows.Controls.MediaState> Özellikleri ortam kayıttan yürütme davranışını etkilemek için ayarlanır. Örneğin, varsayılan <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> olan <xref:System.Windows.Controls.MediaState.Play> ve varsayılan <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> olan <xref:System.Windows.Controls.MediaState.Close>. Bunun anlamı hemen <xref:System.Windows.Controls.MediaElement> yüklenir ve önceden döndürülecek tamamlandığında, medya yürütülür. Kayıttan yürütme tamamlandığında ortam kapatılır ve tüm ortam kaynakları serbest bırakılır.  
  
 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> Ve <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> özellikleri medya kayıttan yürütmeyi denetlemek için tek yolu değil. Saat modunda saatini kontrol edebilirsiniz <xref:System.Windows.Controls.MediaElement> ve etkileşimli denetim yöntemleri sahip denetim <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> olan <xref:System.Windows.Controls.MediaState.Manual>. <xref:System.Windows.Controls.MediaElement>aşağıdaki öncelikleri değerlendirerek denetim için bu rekabeti işler.  
  
1.  <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>. Ortam kaldırıldığında yerinde. Bu varsayılan olarak, tüm ortam kaynakları yayımlanan sağlar bile bir <xref:System.Windows.Media.MediaClock> ile ilişkili <xref:System.Windows.Controls.MediaElement>.  
  
2.  <xref:System.Windows.Media.MediaClock>. Medya olduğunda yerinde bir <xref:System.Windows.Controls.MediaElement.Clock%2A>. Ortam kaldırılırsa <xref:System.Windows.Media.MediaClock> sürece etkili <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> olan <xref:System.Windows.Controls.MediaState.Manual>. Saat modu her zaman yüklü davranışını geçersiz kılar <xref:System.Windows.Controls.MediaElement>.  
  
3.  <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>. Ortam yüklendiğinde yerinde.  
  
4.  Etkileşimli denetim yöntemleri. Yerleştirin ne zaman <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> olan <xref:System.Windows.Controls.MediaState.Manual>. Kullanılabilir denetim yöntemleri <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, <xref:System.Windows.Controls.MediaElement.Close%2A>, ve <xref:System.Windows.Controls.MediaElement.Stop%2A>.  
  
### <a name="displaying-a-mediaelement"></a>MediaElement'i görüntüleme  
 Görüntülenecek bir <xref:System.Windows.Controls.MediaElement> sahip olur ve işlemek için içerik gerekir, <xref:System.Windows.FrameworkElement.ActualWidth%2A> ve <xref:System.Windows.FrameworkElement.ActualHeight%2A> özelliklerini ayarlamak içerik yüklenene kadar sıfır olarak. Yalnızca ses içeriği için bu özellikleri her zaman sıfır olur. Video içeriği için bir kez <xref:System.Windows.Controls.MediaElement.MediaOpened> olay gerçekleşti <xref:System.Windows.FrameworkElement.ActualWidth%2A> ve <xref:System.Windows.FrameworkElement.ActualHeight%2A> yüklenen medyanın boyutunu rapor eder. Medya yüklenene kadar Bunun anlamı <xref:System.Windows.Controls.MediaElement> tüm fiziksel yer olmayacak [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] sürece <xref:System.Windows.FrameworkElement.Width%2A> veya <xref:System.Windows.FrameworkElement.Height%2A> özellikler ayarlanır.  
  
 Her ikisi de ayarı <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özellikleri için sağlanan alanı dolduracak şekilde uzatılır ortama neden olacak <xref:System.Windows.Controls.MediaElement>. Ortamın özgün en boy oranını korumak için ya <xref:System.Windows.FrameworkElement.Width%2A> veya <xref:System.Windows.FrameworkElement.Height%2A> özellik kümesi ancak ikisini olmalıdır. Her ikisi de ayarı <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özellikleri arzu olmayabilir sabit öğe boyutunda sunmak medya neden olur.  
  
 Sabit boyutlu bir öğeye zorunda kalmamak için [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] medya video ön payı. Bu ayarlayarak yapılır <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> ya da <xref:System.Windows.Controls.MediaState.Play> veya <xref:System.Windows.Controls.MediaState.Pause>. İçinde bir <xref:System.Windows.Controls.MediaState.Pause> durumunda, ortam döndürülecek ve ilk çerçeveyi sunacaktır. İçinde bir <xref:System.Windows.Controls.MediaState.Play> durumunda, medya video ön payı ve çalmaya başlayacaktır.  
  
<a name="mediaplayer"></a>   
## <a name="mediaplayer-class"></a>MediaPlayer sınıfı  
 Oysa <xref:System.Windows.Controls.MediaElement> sınıftır framework öğesi <xref:System.Windows.Media.MediaPlayer> sınıfı kullanılmak üzere tasarlanmıştır <xref:System.Windows.Media.Drawing> nesneleri. Çizim nesneleri kullanılan çerçeve düzeyi özelliklerinin performans avantajı kazanması için feda veya ne zaman gereksinim duyduğunuz <xref:System.Windows.Freezable> özellikleri. <xref:System.Windows.Media.MediaPlayer>medya içeriği uygulamalarınızda sağlarken bu özelliklerden yararlanmak etkinleştirir. Gibi <xref:System.Windows.Controls.MediaElement>, <xref:System.Windows.Media.MediaPlayer> mod ancak mu saat değil veya bağımsız kullanılabilir sahip <xref:System.Windows.Controls.MediaElement> nesne kaldırıldı ve yüklenen durumları. Bu in kayıttan çalma karmaşıklığını azaltır <xref:System.Windows.Media.MediaPlayer>.  
  
### <a name="controlling-mediaplayer"></a>MediaPlayer denetleme  
 Çünkü <xref:System.Windows.Media.MediaPlayer> olduğu durum bilgisiz, yalnızca iki yolu vardır medya kayıttan yürütmeyi denetlemek için.  
  
1.  Etkileşimli denetim yöntemleri. Bağımsız moddayken yerinde (`null` <xref:System.Windows.Media.MediaPlayer.Clock%2A> özelliği).  
  
2.  <xref:System.Windows.Media.MediaClock>. Medya olduğunda yerinde bir <xref:System.Windows.Media.MediaPlayer.Clock%2A>.  
  
### <a name="displaying-a-mediaplayer"></a>MediaPlayer görüntüleme  
 Teknik olarak, bir <xref:System.Windows.Media.MediaPlayer> fiziksel bir temsili olmadığından görüntülenemiyor. Ancak, bu ortama sunmak için kullanılabilir bir <xref:System.Windows.Media.Drawing> kullanarak <xref:System.Windows.Media.VideoDrawing> sınıfı. Aşağıdaki örnek kullanımını gösteren bir <xref:System.Windows.Media.VideoDrawing> ortamı görüntülemek için.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Bkz: [çizim nesnelere genel bakış](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md) hakkında daha fazla bilgi için <xref:System.Windows.Media.Drawing> nesneleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.DrawingGroup>  
 [Düzen](../../../../docs/framework/wpf/advanced/layout.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)
