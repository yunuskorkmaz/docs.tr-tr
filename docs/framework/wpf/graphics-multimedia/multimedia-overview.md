---
title: Multimedyaya Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF]
- media [WPF]
ms.assetid: feb25b15-d741-4ac3-818f-1b19f63a3562
ms.openlocfilehash: ffdcb58cdd332f9c730e7ed367e0f8bcc56da459
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222100"
---
# <a name="multimedia-overview"></a>Multimedyaya Genel Bakış
Multimedya özellikleri [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ses ve video kullanıcı deneyimini iyileştirmek için uygulamalarınızla tümleştirin olanak sağlar. Bu konuda multimedya özelliklerini tanıtır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  

<a name="mediaapi"></a>   
## <a name="media-api"></a>Medya API  
 <xref:System.Windows.Controls.MediaElement> Ve <xref:System.Windows.Media.MediaPlayer> sınıfları, ses veya video içeriği sunmak için kullanılır. Bu sınıflar, etkileşimli olarak veya bir saat olarak denetlenebilir. Bu sınıfların kullanabilirsiniz [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] medya kayıttan yürütme için 10 denetimi. Hangi sınıfı kullanın, senaryoya bağlıdır.  
  
 <xref:System.Windows.Controls.MediaElement> olan bir <xref:System.Windows.UIElement> tarafından desteklenen [Düzen](../advanced/layout.md) ve birçok içeriği olarak kullanılabilir. Ayrıca, kullanılabilir durumda [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] yanı sıra kodu. <xref:System.Windows.Media.MediaPlayer>, diğer taraftan, için tasarlanmış <xref:System.Windows.Media.Drawing> nesneler ve Düzen dönülemiyor. Medya kullanarak yüklenen bir <xref:System.Windows.Media.MediaPlayer> kullanarak yalnızca sunulabilen bir <xref:System.Windows.Media.VideoDrawing> veya doğrudan etkileşim bir <xref:System.Windows.Media.DrawingContext>. <xref:System.Windows.Media.MediaPlayer> XAML içinde kullanılamaz.  
  
 Çizim nesneleri ve içeriği çizim hakkında daha fazla bilgi için bkz. [çizim nesnelerine genel bakış](drawing-objects-overview.md).  
  
> [!NOTE]
>  Uygulamanız ile medya dağıtırken, bir medya dosyası proje kaynağı olarak kullanamazsınız. Proje dosyanızda, bunun yerine ortam türünü ayarlamalısınız `Content` ayarlayıp `CopyToOutputDirectory` için `PreserveNewest` veya `Always`.  
  
<a name="mediaplaybackmodes"></a>   
## <a name="media-playback-modes"></a>Medya kayıttan yürütme modları  
  
> [!NOTE]
>  Her ikisi de <xref:System.Windows.Controls.MediaElement> ve <xref:System.Windows.Media.MediaPlayer> benzer üyelere sahiptir. Bu bölümdeki bağlantılar başvurmak <xref:System.Windows.Controls.MediaElement> sınıf üyeleri. Özellikle belirtilmedikçe bağlantılı üyeler <xref:System.Windows.Controls.MediaElement> sınıfı da bulunabilir <xref:System.Windows.Media.MediaPlayer> sınıfı.  
  
 Medya kayıttan yürütme anlamak için [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], içinde yürütülen ortam farklı modlarını anlaşılması gereklidir. Her ikisi de <xref:System.Windows.Controls.MediaElement> ve <xref:System.Windows.Media.MediaPlayer> iki farklı medya modları, bağımsız modu ve saat modunda kullanılabilir. Ortam modu belirlenir <xref:System.Windows.Controls.MediaElement.Clock%2A> özelliği. Zaman <xref:System.Windows.Controls.MediaElement.Clock%2A> olduğu `null`, bağımsız modda medya nesnesi olur. Zaman <xref:System.Windows.Controls.MediaElement.Clock%2A> olduğu saat modunda medya nesnesi null olmayan, olur. Varsayılan olarak, ortam bağımsız modda nesneleridir.  
  
### <a name="independent-mode"></a>Bağımsız mod  
 Bağımsız modda medya içeriği medya kayıttan yürütme beraberinde getirir. Bağımsız mod, aşağıdaki seçenekleri sağlar:  
  
-   Ortamın <xref:System.Uri> doğrudan belirtilebilir.  
  
-   Medya kayıttan yürütme doğrudan denetlenebilir.  
  
-   Ortamın <xref:System.Windows.Controls.MediaElement.Position%2A> ve <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> özellikleri değiştirilebilir.  
  
 Ortam ya da ayarı tarafından yüklenen <xref:System.Windows.Controls.MediaElement> nesnenin <xref:System.Windows.Controls.MediaElement.Source%2A> özelliği veya çağırarak <xref:System.Windows.Media.MediaPlayer> nesnenin <xref:System.Windows.Media.MediaPlayer.Open%2A> yöntemi.  
  
 Bağımsız modda medya yürütmesini denetlemek için ortam nesnesinin denetim yöntemleri kullanılabilir. Kullanılabilir denetim yöntemleri <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, <xref:System.Windows.Controls.MediaElement.Close%2A>, ve <xref:System.Windows.Controls.MediaElement.Stop%2A>. İçin <xref:System.Windows.Controls.MediaElement>, bu yöntemleri kullanarak etkileşimli denetim, yalnızca kullanılabilir olduğunda <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> ayarlanır <xref:System.Windows.Controls.MediaState.Manual>. Bu yöntemler, medya nesnesi saati modundayken kullanılamaz.  
  
 Bkz: [MediaElement (Yürüt, Duraklat, Durdur, birim ve hızı) denetimi](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md) bağımsız mod ilişkin bir örnek.  
  
### <a name="clock-mode"></a>Saat modu  
 Saat modunda bir <xref:System.Windows.Media.MediaTimeline> sürücüleri medya kayıttan yürütme. Saat modu, aşağıdaki özelliklere sahiptir:  
  
-   Ortamın <xref:System.Uri> aracılığıyla dolaylı olarak ayarlanmış bir <xref:System.Windows.Media.MediaTimeline>.  
  
-   Medya kayıttan yürütme saati tarafından denetlenebilir. Ortam nesnesinin denetim yöntemleri kullanılamaz.  
  
-   Medya ayarlayarak yüklendiği bir <xref:System.Windows.Media.MediaTimeline> nesnenin <xref:System.Windows.Media.MediaTimeline.Source%2A> saati zaman çizelgesinden oluşturarak ve saat için medya nesnesi atama özelliği. Medya bu şekilde de yüklü olduğunda bir <xref:System.Windows.Media.MediaTimeline> içinde bir <xref:System.Windows.Media.Animation.Storyboard> hedefleri bir <xref:System.Windows.Controls.MediaElement>.  
  
 Saat modunda medya kayıttan yürütmeyi denetlemek için <xref:System.Windows.Media.Animation.ClockController> denetim yöntemleri kullanılmalıdır. A <xref:System.Windows.Media.Animation.ClockController> öğesinden alınan <xref:System.Windows.Media.Animation.ClockController> özelliği <xref:System.Windows.Media.MediaClock>. Ya da denetim yöntemlerini kullanmayı denerseniz bir <xref:System.Windows.Controls.MediaElement> veya <xref:System.Windows.Media.MediaPlayer> saati modundayken, nesne bir <xref:System.InvalidOperationException> oluşturulur.  
  
 Bkz: [animasyona genel bakış](animation-overview.md) saatler ve zaman çizelgeleri hakkında daha fazla bilgi.  
  
 Bkz: [görsel taslak kullanarak MediaElement'i denetleme](how-to-control-a-mediaelement-by-using-a-storyboard.md) saat modu örneği.  
  
<a name="mediaelement"></a>   
## <a name="mediaelement-class"></a>MediaElement Class  
 Medya bir uygulamaya eklemek kadar basittir bir <xref:System.Windows.Controls.MediaElement> denetimini [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] uygulamanın ve sağlama bir <xref:System.Uri> dahil etmek istediğiniz ortam için. Tarafından desteklenen tüm medya türleri [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] 10 desteklenir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Aşağıdaki örnek, bir basit kullanımını gösterir. <xref:System.Windows.Controls.MediaElement> içinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
 [!code-xaml[MediaElement_snip#SimpleMediaElementUsageWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaElement_snip/CSharp/SimpleUsage.xaml#simplemediaelementusagewholepage)]  
  
 Bu örnekte, yüklendikten hemen sonra ortam otomatik olarak kayıttan yürütülür. Ortam yürütmeyi tamamladığında, ortam kapatılır ve yayın (video belleği dahil) tüm medya kaynaklardır. Varsayılan davranışı budur <xref:System.Windows.Controls.MediaElement> nesnesi ve tarafından denetlenen <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> ve <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> özellikleri.  
  
### <a name="controlling-a-mediaelement"></a>MediaElement'i denetleme  
 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> Ve <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> davranışını denetim özelliklerini <xref:System.Windows.Controls.MediaElement> olduğunda <xref:System.Windows.FrameworkElement.IsLoaded%2A> olduğu `true` veya `false`sırasıyla. <xref:System.Windows.Controls.MediaState> Medya kayıttan yürütme davranışını etkilemek için özellikleri ayarlayın. Örneğin, varsayılan <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> olduğu <xref:System.Windows.Controls.MediaState.Play> ve varsayılan <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> olduğu <xref:System.Windows.Controls.MediaState.Close>. Diğer bir deyişle hemen sonra <xref:System.Windows.Controls.MediaElement> yüklenir ve önceden döndürülecek tamamlandıktan, medya yürütülür. Kayıttan yürütme tamamlandığında ortam kapatılır ve tüm ortam kaynaklarını serbest bırakılır.  
  
 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> Ve <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> özellikleri medya kayıttan yürütmeyi denetlemek için tek yolu değil. Saatin saat modunda denetleyebilirsiniz <xref:System.Windows.Controls.MediaElement> ve etkileşimli denetim yöntemleri olduğunu kontrol <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> olduğu <xref:System.Windows.Controls.MediaState.Manual>. <xref:System.Windows.Controls.MediaElement> Bu yarışmaya denetimi aşağıdaki öncelikleri değerlendirerek işler.  
  
1.  <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>biçimindeki telefon numarasıdır. Ortam kaldırıldığında yerinde. Bu, tüm ortam kaynakları varsayılan olarak, yayımlanan sağlar bile bir <xref:System.Windows.Media.MediaClock> ilişkili olduğu <xref:System.Windows.Controls.MediaElement>.  
  
2.  <xref:System.Windows.Media.MediaClock>biçimindeki telefon numarasıdır. Medya bulunduğunda bir yerde bir <xref:System.Windows.Controls.MediaElement.Clock%2A>. Ortam kaldırılırsa <xref:System.Windows.Media.MediaClock> sürece etkili <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> olduğu <xref:System.Windows.Controls.MediaState.Manual>. Saat modu her zaman yüklü davranışını geçersiz kılar <xref:System.Windows.Controls.MediaElement>.  
  
3.  <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>biçimindeki telefon numarasıdır. Medya yüklendiğinde yerinde.  
  
4.  Etkileşimli denetim yöntemleri. Yerleştirin ne zaman <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> olduğu <xref:System.Windows.Controls.MediaState.Manual>. Kullanılabilir denetim yöntemleri <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, <xref:System.Windows.Controls.MediaElement.Close%2A>, ve <xref:System.Windows.Controls.MediaElement.Stop%2A>.  
  
### <a name="displaying-a-mediaelement"></a>MediaElement görüntüleme  
 Görüntülenecek bir <xref:System.Windows.Controls.MediaElement> işlemek için içerik olmalıdır ve olması, <xref:System.Windows.FrameworkElement.ActualWidth%2A> ve <xref:System.Windows.FrameworkElement.ActualHeight%2A> içeriği yüklenene kadar sıfıra özelliklerini ayarlayın. Yalnızca ses içeriği için bu özellikleri her zaman sıfırdır. Video içeriği için <xref:System.Windows.Controls.MediaElement.MediaOpened> olay gerçekleşti <xref:System.Windows.FrameworkElement.ActualWidth%2A> ve <xref:System.Windows.FrameworkElement.ActualHeight%2A> yüklenen medyanın boyutu rapor eder. Bunun anlamı ortam yükleninceye kadar <xref:System.Windows.Controls.MediaElement> hiçbir fiziksel alan olmayacak [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] sürece <xref:System.Windows.FrameworkElement.Width%2A> veya <xref:System.Windows.FrameworkElement.Height%2A> özellikleri ayarlanır.  
  
 Her ikisi de ayarını <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özellikleri için sağlanan alanı dolduracak şekilde uzatılır ortama neden <xref:System.Windows.Controls.MediaElement>. Ya da ortamın özgün en boy oranını korumak için <xref:System.Windows.FrameworkElement.Width%2A> veya <xref:System.Windows.FrameworkElement.Height%2A> özelliği, ikisi birden değil olmalıdır. Her ikisi de ayarını <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özellikleri istenmeyebilir bir sabit öğe boyutu sunmak media neden olur.  
  
 Sabit boyutlu bir öğeye kaçınmak için [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] medya video ön payı. Bu ayarı gerçekleştirilir <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> ya da <xref:System.Windows.Controls.MediaState.Play> veya <xref:System.Windows.Controls.MediaState.Pause>. İçinde bir <xref:System.Windows.Controls.MediaState.Pause> durumunda, medya döndürülecek ve ilk kare sunacaktır. İçinde bir <xref:System.Windows.Controls.MediaState.Play> durumunda, medya video ön payı ve yürütmeye başlayabilirsiniz.  
  
<a name="mediaplayer"></a>   
## <a name="mediaplayer-class"></a>MediaPlayer sınıfı  
 Oysa <xref:System.Windows.Controls.MediaElement> sınıfı, bir çerçeve öğesi <xref:System.Windows.Media.MediaPlayer> sınıfı kullanılmak üzere tasarlanmıştır <xref:System.Windows.Media.Drawing> nesneleri. Çizim nesneleri performans avantajı kazanmak için framework düzeyi özellikleri özelliğinden faydalanmasına veya, ihtiyacınız olduğunda kullanılan <xref:System.Windows.Freezable> özellikleri. <xref:System.Windows.Media.MediaPlayer> medya içeriği uygulamalarınızda sağlarken bu özelliklerden yararlanmanızı sağlar. Gibi <xref:System.Windows.Controls.MediaElement>, <xref:System.Windows.Media.MediaPlayer> modu ancak mu saat değil veya bağımsız kullanılabilir olan <xref:System.Windows.Controls.MediaElement> nesne kaldırıldı ve yüklenen durumları. Bu, kayıttan yürütme denetimi karmaşıklığı azaltır <xref:System.Windows.Media.MediaPlayer>.  
  
### <a name="controlling-mediaplayer"></a>MediaPlayer denetleme  
 Çünkü <xref:System.Windows.Media.MediaPlayer> olduğu durum bilgisiz, yalnızca iki yolu vardır medya kayıttan yürütmeyi denetlemek için.  
  
1.  Etkileşimli denetim yöntemleri. Bağımsız modda bir yerde (`null`<xref:System.Windows.Media.MediaPlayer.Clock%2A> özelliği).  
  
2.  <xref:System.Windows.Media.MediaClock>biçimindeki telefon numarasıdır. Medya bulunduğunda bir yerde bir <xref:System.Windows.Media.MediaPlayer.Clock%2A>.  
  
### <a name="displaying-a-mediaplayer"></a>MediaPlayer görüntüleme  
 Teknik olarak, bir <xref:System.Windows.Media.MediaPlayer> fiziksel bir temsili olduğundan görüntülenemiyor. Ancak, bu ortama sunmak için kullanılabilir bir <xref:System.Windows.Media.Drawing> kullanarak <xref:System.Windows.Media.VideoDrawing> sınıfı. Aşağıdaki örnek kullanımını gösterir. bir <xref:System.Windows.Media.VideoDrawing> ortamı görüntülemek için.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Bkz: [çizim nesnelerine genel bakış](drawing-objects-overview.md) hakkında daha fazla bilgi için <xref:System.Windows.Media.Drawing> nesneleri.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.DrawingGroup>
- [Düzen](../advanced/layout.md)
- [Nasıl Yapılır Konuları](audio-and-video-how-to-topics.md)
