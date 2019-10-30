---
title: Multimedyaya Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF]
- media [WPF]
ms.assetid: feb25b15-d741-4ac3-818f-1b19f63a3562
ms.openlocfilehash: 42d0d388e859b556d23b7fc81931cd61470ba541
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039796"
---
# <a name="multimedia-overview"></a>Multimedyaya Genel Bakış
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] multimedya özellikleri, Kullanıcı deneyimini geliştirmek için uygulamalarınızı ses ve videoyu tümleştirmenize imkan tanır. Bu konu, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]multimedya özelliklerini tanıtır.  

<a name="mediaapi"></a>   
## <a name="media-api"></a>Medya API 'SI  
 <xref:System.Windows.Controls.MediaElement> ve <xref:System.Windows.Media.MediaPlayer> sınıfları, ses veya video içeriğini sunmak için kullanılır. Bu sınıflar etkileşimli bir şekilde veya bir saatle denetlenebilir. Bu sınıflar, medya kayıttan yürütme için Microsoft Windows Media Player 10 denetiminde kullanılabilir. Kullandığınız sınıf, senaryoya bağlıdır.  
  
 <xref:System.Windows.Controls.MediaElement>, [Düzen](../advanced/layout.md) tarafından desteklenen bir <xref:System.Windows.UIElement> ve birçok denetimin içeriği olarak tüketilebilir. Ayrıca, kodun yanı sıra [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] de kullanılabilir. diğer yandan <xref:System.Windows.Media.MediaPlayer>, <xref:System.Windows.Media.Drawing> nesneleri için tasarlanmıştır ve düzen desteği yoktur. <xref:System.Windows.Media.MediaPlayer> kullanılarak yüklenen medya, yalnızca bir <xref:System.Windows.Media.VideoDrawing> kullanılarak veya doğrudan bir <xref:System.Windows.Media.DrawingContext>etkileşimde bulunarak sunulabilir. <xref:System.Windows.Media.MediaPlayer> XAML 'de kullanılamaz.  
  
 Çizim nesneleri ve çizim bağlamı hakkında daha fazla bilgi için bkz. [çizim nesnelerine genel bakış](drawing-objects-overview.md).  
  
> [!NOTE]
> Medyayı uygulamanızla dağıtırken proje kaynağı olarak bir medya dosyası kullanamazsınız. Proje dosyanızda, bunun yerine medya türünü `Content` olarak ayarlamanız ve `CopyToOutputDirectory` ' i `PreserveNewest` ' ye `Always` ' e ayarlamanız gerekir.  
  
<a name="mediaplaybackmodes"></a>   
## <a name="media-playback-modes"></a>Medya kayıttan yürütme modları  
  
> [!NOTE]
> Hem <xref:System.Windows.Controls.MediaElement> hem de <xref:System.Windows.Media.MediaPlayer> benzer üyelere sahiptir. Bu bölümdeki bağlantılar <xref:System.Windows.Controls.MediaElement> sınıfı üyelerine başvurur. Özellikle belirtilmedikçe, <xref:System.Windows.Controls.MediaElement> sınıfında bağlantılı Üyeler <xref:System.Windows.Media.MediaPlayer> sınıfında da bulunabilir.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]' de medya kayıttan yürütmeyi anlamak için, medyanın yürütülenbileceği farklı modların anlaşılması gerekir. Hem <xref:System.Windows.Controls.MediaElement> hem de <xref:System.Windows.Media.MediaPlayer> iki farklı medya modunda, bağımsız modda ve saat modunda kullanılabilir. Medya modu <xref:System.Windows.Controls.MediaElement.Clock%2A> özelliği tarafından belirlenir. <xref:System.Windows.Controls.MediaElement.Clock%2A> `null`, medya nesnesi bağımsız moddadır. <xref:System.Windows.Controls.MediaElement.Clock%2A> null olmayan bir değer olduğunda, medya nesnesi saat modundadır. Varsayılan olarak, medya nesneleri bağımsız modundadır.  
  
### <a name="independent-mode"></a>Bağımsız mod  
 Bağımsız modda, medya içeriği medya kayıttan yürütmeyi yürütür. Bağımsız mod aşağıdaki seçenekleri sunar:  
  
- Medyanın <xref:System.Uri> doğrudan belirtilebilir.  
  
- Medya kayıttan yürütme doğrudan denetlenebilir.  
  
- Medyanın <xref:System.Windows.Controls.MediaElement.Position%2A> ve <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> özellikleri değiştirilebilir.  
  
 Medya, <xref:System.Windows.Controls.MediaElement> nesnenin <xref:System.Windows.Controls.MediaElement.Source%2A> özelliği ayarlanarak veya <xref:System.Windows.Media.MediaPlayer> nesnesinin <xref:System.Windows.Media.MediaPlayer.Open%2A> metodu çağırarak yüklenir.  
  
 Medya kayıttan yürütmeyi bağımsız modda denetlemek için, medya nesnesinin denetim yöntemleri kullanılabilir. Kullanılabilir denetim yöntemleri <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, <xref:System.Windows.Controls.MediaElement.Close%2A>ve <xref:System.Windows.Controls.MediaElement.Stop%2A>. <xref:System.Windows.Controls.MediaElement>için, bu yöntemleri kullanan etkileşimli denetim yalnızca <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> <xref:System.Windows.Controls.MediaState.Manual>olarak ayarlandığında kullanılabilir. Medya nesnesi saat modundayken bu yöntemler kullanılamaz.  
  
 Bağımsız mod örneği için bkz. [MediaElement (Play, Duraklat, durdur, hacim ve Speed)](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md) .  
  
### <a name="clock-mode"></a>Saat modu  
 Saat modunda, <xref:System.Windows.Media.MediaTimeline> medya kayıttan yürütmeyi yürütür. Saat modu aşağıdaki özelliklere sahiptir:  
  
- Medya <xref:System.Uri>, bir <xref:System.Windows.Media.MediaTimeline>üzerinden dolaylı olarak ayarlanır.  
  
- Medya kayıttan yürütme, saat tarafından denetlenebilir. Medya nesnesinin denetim yöntemleri kullanılamıyor.  
  
- Medya, <xref:System.Windows.Media.MediaTimeline> nesnenin <xref:System.Windows.Media.MediaTimeline.Source%2A> özelliği ayarlanarak, zaman çizelgesinden saati oluşturarak ve saati medya nesnesine atayarak yüklenir. Medya Ayrıca, bir <xref:System.Windows.Media.Animation.Storyboard> içindeki bir <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Controls.MediaElement>hedefliyorsa bu şekilde yüklenir.  
  
 Medya kayıttan yürütmeyi saat modunda denetlemek için <xref:System.Windows.Media.Animation.ClockController> denetim yöntemlerinin kullanılması gerekir. <xref:System.Windows.Media.Animation.ClockController>, <xref:System.Windows.Media.MediaClock><xref:System.Windows.Media.Animation.ClockController> özelliğinden elde edilir. Saat modundayken bir <xref:System.Windows.Controls.MediaElement> veya <xref:System.Windows.Media.MediaPlayer> nesnesinin denetim yöntemlerini kullanmayı denerseniz, bir <xref:System.InvalidOperationException> oluşturulur.  
  
 Saatler ve zaman çizelgeleri hakkında daha fazla bilgi için [animasyona genel bakış](animation-overview.md) bölümüne bakın.  
  
 Bkz. saat modu örneği için [görsel taslak kullanarak MediaElement 'ı denetleme](how-to-control-a-mediaelement-by-using-a-storyboard.md) .  
  
<a name="mediaelement"></a>   
## <a name="mediaelement-class"></a>MediaElement sınıfı  
 Bir uygulamaya medya eklemek, uygulamanın [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] <xref:System.Windows.Controls.MediaElement> bir denetim eklemek ve dahil etmek istediğiniz medyaya <xref:System.Uri> sağlamak kadar basittir. Microsoft Windows Media Player 10 tarafından desteklenen tüm medya türleri [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]desteklenir. Aşağıdaki örnek, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]<xref:System.Windows.Controls.MediaElement> basit bir kullanımını gösterir.  
  
 [!code-xaml[MediaElement_snip#SimpleMediaElementUsageWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaElement_snip/CSharp/SimpleUsage.xaml#simplemediaelementusagewholepage)]  
  
 Bu örnekte, medya yüklendikten hemen sonra otomatik olarak oynatılır. Medyanın yürütülmesi bittikten sonra medya kapatılır ve tüm medya kaynakları yayın (video belleği dahil) olur. Bu, <xref:System.Windows.Controls.MediaElement> nesnesinin varsayılan davranışıdır ve <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> ve <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> özellikleriyle denetlenir.  
  
### <a name="controlling-a-mediaelement"></a>MediaElement 'i denetleme  
 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> ve <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> özellikleri, sırasıyla <xref:System.Windows.FrameworkElement.IsLoaded%2A> `true` veya `false`olduğunda <xref:System.Windows.Controls.MediaElement> davranışını denetler. <xref:System.Windows.Controls.MediaState> özellikler, medya kayıttan yürütme davranışını etkileyecek şekilde ayarlanır. Örneğin, varsayılan <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> <xref:System.Windows.Controls.MediaState.Play> ve varsayılan <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> <xref:System.Windows.Controls.MediaState.Close>. Bu, <xref:System.Windows.Controls.MediaElement> yüklendiği anda ve PreRoll tamamlandıktan hemen sonra medya oynatılmaya başladığı anlamına gelir. Kayıttan yürütme tamamlandıktan sonra medya kapatılır ve tüm medya kaynakları serbest bırakılır.  
  
 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> ve <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> özellikleri, medya kayıttan yürütmeyi denetlemek için tek yol değildir. Saat modunda, saat <xref:System.Windows.Controls.MediaElement> denetleyebilir ve <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> <xref:System.Windows.Controls.MediaState.Manual>etkileşimli denetim yöntemlerinde denetim vardır. <xref:System.Windows.Controls.MediaElement>, aşağıdaki öncelikleri değerlendirerek denetim için bu rekabeti işler.  
  
1. <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>. Medya kaldırıldığında yerinde. Bu, <xref:System.Windows.Controls.MediaElement>ilişkilendirilmiş bir <xref:System.Windows.Media.MediaClock> olsa bile tüm medya kaynaklarının varsayılan olarak serbest bırakılacağını sağlar.  
  
2. <xref:System.Windows.Media.MediaClock>. Medyada <xref:System.Windows.Controls.MediaElement.Clock%2A>olduğunda. Medya kaldırıldığında, <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> <xref:System.Windows.Controls.MediaState.Manual>olduğu sürece <xref:System.Windows.Media.MediaClock> geçerli olur. Saat modu her zaman <xref:System.Windows.Controls.MediaElement>yüklenen davranışını geçersiz kılar.  
  
3. <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>. Medya yüklendiğinde yerinde.  
  
4. Etkileşimli denetim yöntemleri. <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> <xref:System.Windows.Controls.MediaState.Manual>. Kullanılabilir denetim yöntemleri <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, <xref:System.Windows.Controls.MediaElement.Close%2A>ve <xref:System.Windows.Controls.MediaElement.Stop%2A>.  
  
### <a name="displaying-a-mediaelement"></a>MediaElement 'i görüntüleme  
 Bir <xref:System.Windows.Controls.MediaElement> görüntülemek için, işlenecek içeriğe sahip olmalıdır ve <xref:System.Windows.FrameworkElement.ActualWidth%2A> ve <xref:System.Windows.FrameworkElement.ActualHeight%2A> özellikleri içerik yükleninceye kadar sıfıra ayarlanır. Yalnızca ses içeriği için bu özellikler her zaman sıfırdır. Video içeriği için <xref:System.Windows.Controls.MediaElement.MediaOpened> olayı <xref:System.Windows.FrameworkElement.ActualWidth%2A> olduktan sonra <xref:System.Windows.FrameworkElement.ActualHeight%2A> yüklenen medyanın boyutunu rapor eder. Bu, medya yüklenene kadar, <xref:System.Windows.FrameworkElement.Width%2A> veya <xref:System.Windows.FrameworkElement.Height%2A> özellikleri ayarlanmadığı sürece <xref:System.Windows.Controls.MediaElement> [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] herhangi bir fiziksel alanı kaplamayacak anlamına gelir.  
  
 Hem <xref:System.Windows.FrameworkElement.Width%2A> hem de <xref:System.Windows.FrameworkElement.Height%2A> özelliklerinin ayarlanması, medyanın <xref:System.Windows.Controls.MediaElement>için sunulan alanı dolduracak şekilde uzamasına neden olur. Medyanın özgün en boy oranını korumak için <xref:System.Windows.FrameworkElement.Width%2A> ya da <xref:System.Windows.FrameworkElement.Height%2A> özelliği ayarlanmalıdır ancak her ikisi de kullanılmamalıdır. Hem <xref:System.Windows.FrameworkElement.Width%2A> hem de <xref:System.Windows.FrameworkElement.Height%2A> özelliklerinin ayarlanması, medyanın istenmeyen sabit bir öğe boyutunda olmasına neden olur.  
  
 Sabit boyutlu bir öğe kullanmaktan kaçınmak için [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] medyayı önceden yükleyebilir. Bu, <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> <xref:System.Windows.Controls.MediaState.Play> veya <xref:System.Windows.Controls.MediaState.Pause>olarak ayarlanarak yapılır. <xref:System.Windows.Controls.MediaState.Pause> durumunda medya ön ek olur ve ilk kareyi sunar. <xref:System.Windows.Controls.MediaState.Play> durumda, medya ön ek olur ve yürütmeye başlar.  
  
<a name="mediaplayer"></a>   
## <a name="mediaplayer-class"></a>MediaPlayer Sınıfı  
 <xref:System.Windows.Controls.MediaElement> sınıfı çerçeve öğesi olduğunda, <xref:System.Windows.Media.MediaPlayer> sınıfı <xref:System.Windows.Media.Drawing> nesnelerinde kullanılmak üzere tasarlanmıştır. Çizim nesneleri, performans avantajları elde etmek veya <xref:System.Windows.Freezable> özelliklere ihtiyaç duyduğunuzda çerçeve düzeyindeki özellikleri feda etmek için kullanılır. <xref:System.Windows.Media.MediaPlayer>, uygulamalarınızda medya içeriği sağlarken bu özelliklerden faydalanabilmenizi sağlar. <xref:System.Windows.Controls.MediaElement>gibi, <xref:System.Windows.Media.MediaPlayer> bağımsız veya saat modunda kullanılabilir ancak <xref:System.Windows.Controls.MediaElement> nesnenin yüklenmemiş ve yüklü durumlarına sahip değildir. Bu, <xref:System.Windows.Media.MediaPlayer>oynatma denetimi karmaşıklığını azaltır.  
  
### <a name="controlling-mediaplayer"></a>MediaPlayer 'yi denetleme  
 <xref:System.Windows.Media.MediaPlayer> durum bilgisiz olduğundan, medya kayıttan yürütmeyi denetlemek için yalnızca iki yol vardır.  
  
1. Etkileşimli denetim yöntemleri. Bağımsız modda (`null`<xref:System.Windows.Media.MediaPlayer.Clock%2A> özelliği) yerinde.  
  
2. <xref:System.Windows.Media.MediaClock>. Medyada <xref:System.Windows.Media.MediaPlayer.Clock%2A>olduğunda.  
  
### <a name="displaying-a-mediaplayer"></a>MediaPlayer görüntüleme  
 Teknik olarak, bir <xref:System.Windows.Media.MediaPlayer> bir fiziksel temsili olmadığından görüntülenemez. Ancak, <xref:System.Windows.Media.VideoDrawing> sınıfını kullanarak <xref:System.Windows.Media.Drawing> medya sunmak için kullanılabilir. Aşağıdaki örnek, medyayı göstermek için <xref:System.Windows.Media.VideoDrawing> kullanımını gösterir.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 <xref:System.Windows.Media.Drawing> nesneler hakkında daha fazla bilgi için bkz. [çizim nesnelerine genel bakış](drawing-objects-overview.md) .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.DrawingGroup>
- [Düzen](../advanced/layout.md)
- [Nasıl Yapılır Konuları](audio-and-video-how-to-topics.md)
