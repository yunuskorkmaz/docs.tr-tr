---
title: Multimedyaya Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF]
- media [WPF]
ms.assetid: feb25b15-d741-4ac3-818f-1b19f63a3562
ms.openlocfilehash: d4abf4d9fd324ffbf2737dc686c02e50ca1a8a5a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181880"
---
# <a name="multimedia-overview"></a>Multimedyaya Genel Bakış
Multimedya özellikleri, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] kullanıcı deneyimini geliştirmek için uygulamalarınıza ses ve video entegre etmenizi sağlar. Bu konu multimedya özelliklerini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]tanır.  

<a name="mediaapi"></a>
## <a name="media-api"></a>Medya API'si  
 Ve <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Media.MediaPlayer> sınıflar ses veya video içeriğini sunmak için kullanılır. Bu sınıflar etkileşimli olarak veya saat tarafından denetlenebilir. Bu sınıflar, ortam oynatma için Microsoft Windows Media Player 10 denetiminde kullanılabilir. Hangi sınıfı kullandığınız senaryoya bağlıdır.  
  
 <xref:System.Windows.Controls.MediaElement>Düzen <xref:System.Windows.UIElement> tarafından desteklenen ve [Layout](../advanced/layout.md) birçok denetimin içeriği olarak tüketilebilen bir durumdur. Ayrıca kod [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] yanı sıra kullanılabilir. <xref:System.Windows.Media.MediaPlayer>, diğer taraftan, nesneler <xref:System.Windows.Media.Drawing> için tasarlanmıştır ve düzen desteği yoksundur. A <xref:System.Windows.Media.MediaPlayer> kullanılarak yüklenen ortamlar yalnızca <xref:System.Windows.Media.VideoDrawing> a kullanarak veya <xref:System.Windows.Media.DrawingContext>bir . <xref:System.Windows.Media.MediaPlayer>XAML'de kullanılamaz.  
  
 Nesneleri çizme ve bağlam çizme hakkında daha fazla bilgi için [bkz.](drawing-objects-overview.md)  
  
> [!NOTE]
> Uygulamanızla ortam dağıtırken, medya dosyalarını proje kaynağı olarak kullanamazsınız. Proje dosyanızda, bunun yerine ortam türünü `Content` ayarlamanız `PreserveNewest` `Always`ve ayarlamalısınız. `CopyToOutputDirectory`  
  
<a name="mediaplaybackmodes"></a>
## <a name="media-playback-modes"></a>Medya Oynatma Modları  
  
> [!NOTE]
> Her <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Media.MediaPlayer> ikisi de ve benzer üyeleri var. Bu bölümdeki bağlantılar sınıf <xref:System.Windows.Controls.MediaElement> üyelerine başvurur. Özel olarak belirtilmediği sürece, <xref:System.Windows.Controls.MediaElement> sınıfta ki üyeler <xref:System.Windows.Media.MediaPlayer> de sınıfta bulunabilir.  
  
 Medya oynatma anlamak [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]için, hangi ortam oynatılabilir farklı modların bir anlayış gereklidir. Her <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Media.MediaPlayer> ikisi de ve iki farklı medya modları, bağımsız mod ve saat modu kullanılabilir. Ortam modu <xref:System.Windows.Controls.MediaElement.Clock%2A> özellik tarafından belirlenir. Ne <xref:System.Windows.Controls.MediaElement.Clock%2A> `null`zaman , medya nesnesi bağımsız modda. Null <xref:System.Windows.Controls.MediaElement.Clock%2A> olmadığında, ortam nesnesi saat modundadır. Varsayılan olarak, ortam nesneleri bağımsız moddadır.  
  
### <a name="independent-mode"></a>Bağımsız Mod  
 Bağımsız modda, medya içeriği medya oynatmayı yönlendirir. Bağımsız mod aşağıdaki seçenekleri sağlar:  
  
- Ortamın <xref:System.Uri> ki doğrudan belirtilebilir.  
  
- Medya oynatma doğrudan kontrol edilebilir.  
  
- Ortam ve <xref:System.Windows.Controls.MediaElement.Position%2A> <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> özellikleri değiştirilebilir.  
  
 Ortam, <xref:System.Windows.Controls.MediaElement> nesnenin <xref:System.Windows.Controls.MediaElement.Source%2A> özelliğini ayarlayarak veya nesnenin <xref:System.Windows.Media.MediaPlayer> <xref:System.Windows.Media.MediaPlayer.Open%2A> yöntemini çağırarak yüklenir.  
  
 Ortam oynatmayı bağımsız modda denetlemek için ortam nesnesinin denetim yöntemleri kullanılabilir. Mevcut kontrol yöntemleri <xref:System.Windows.Controls.MediaElement.Play%2A> <xref:System.Windows.Controls.MediaElement.Pause%2A>, <xref:System.Windows.Controls.MediaElement.Close%2A>, <xref:System.Windows.Controls.MediaElement.Stop%2A>, ve . Bunun <xref:System.Windows.Controls.MediaElement>için, bu yöntemleri kullanarak etkileşimli denetim yalnızca <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> . <xref:System.Windows.Controls.MediaState.Manual> Ortam nesnesi saat modundayken bu yöntemler kullanılamaz.  
  
 Bağımsız mod örneği için [mediaelementi (Oynatma, Duraklatma, Durdurma, Ses ve Hız)](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md) denetimi'ne bakın.  
  
### <a name="clock-mode"></a>Saat Modu  
 Saat modunda, <xref:System.Windows.Media.MediaTimeline> medya oynatmayı yönlendirir. Saat modu aşağıdaki özelliklere sahiptir:  
  
- Medya dolaylı <xref:System.Uri> olarak bir <xref:System.Windows.Media.MediaTimeline>.  
  
- Medya oynatma saati tarafından kontrol edilebilir. Ortam nesnesinin denetim yöntemleri kullanılamaz.  
  
- Ortam, bir <xref:System.Windows.Media.MediaTimeline> nesnenin <xref:System.Windows.Media.MediaTimeline.Source%2A> özelliğini ayarlayarak, zaman çizelgesinden saat oluşturarak ve saati medya nesnesine atayarak yüklenir. Ortam da bu şekilde <xref:System.Windows.Media.MediaTimeline> yüklendiğinde, <xref:System.Windows.Controls.MediaElement>bir iç bir hedef a <xref:System.Windows.Media.Animation.Storyboard> .  
  
 Saat modunda ortam oynatmadenetlemek için <xref:System.Windows.Media.Animation.ClockController> denetim yöntemleri kullanılmalıdır. A <xref:System.Windows.Media.Animation.ClockController> <xref:System.Windows.Media.Animation.ClockController> özelliğinden elde <xref:System.Windows.Media.MediaClock>edilir. Saat modundayken bir <xref:System.Windows.Controls.MediaElement> veya <xref:System.Windows.Media.MediaPlayer> nesnenin denetim yöntemlerini kullanmaya <xref:System.InvalidOperationException> çalışırsanız, bir atılmalıdır.  
  
 Saatler ve zaman çizelgeleri hakkında daha fazla bilgi için [Animasyona Genel Bakış'a](animation-overview.md) bakın.  
  
 Saat modu örneği için [Bir Storyboard kullanarak bir MediaElement'i denetleme](how-to-control-a-mediaelement-by-using-a-storyboard.md) bölümüne bakın.  
  
<a name="mediaelement"></a>
## <a name="mediaelement-class"></a>MediaElement Sınıfı  
 Bir uygulamaya ortam eklemek, uygulamanın <xref:System.Windows.Controls.MediaElement> [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] denetimine bir denetim eklemek <xref:System.Uri> ve eklemek istediğiniz ortama bir denetim sağlamak kadar kolaydır. Microsoft Windows Media Player 10 tarafından desteklenen tüm [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]ortam türleri . Aşağıdaki <xref:System.Windows.Controls.MediaElement> örnekte in'in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]basit bir kullanımı gösterilmektedir.  
  
 [!code-xaml[MediaElement_snip#SimpleMediaElementUsageWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaElement_snip/CSharp/SimpleUsage.xaml#simplemediaelementusagewholepage)]  
  
 Bu örnekte, ortam yüklenir yüklenmez otomatik olarak oynatılır. Ortam oynatılmayı bitirdikten sonra ortam kapatılır ve tüm medya kaynakları serbest bırakılır (video belleği dahil). Bu <xref:System.Windows.Controls.MediaElement> nesnenin varsayılan davranışıdır ve ve <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> özellikleri tarafından denetlenir.  
  
### <a name="controlling-a-mediaelement"></a>Bir MediaElementi Denetleme  
 Ve <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> özellikleri ne <xref:System.Windows.Controls.MediaElement> zaman <xref:System.Windows.FrameworkElement.IsLoaded%2A> `true` veya `false`, sırasıyla davranışını denetler. Özellikler, <xref:System.Windows.Controls.MediaState> ortam oynatma davranışını etkileyecek şekilde ayarlanmış. Örneğin, varsayılan <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> ve <xref:System.Windows.Controls.MediaState.Play> varsayılan <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> . <xref:System.Windows.Controls.MediaState.Close> Bu, <xref:System.Windows.Controls.MediaElement> yükleme yapılır ve ön kayıt tamamlanır tamamlanmaz ortamın çalmaya başladığı anlamına gelir. Oynatma tamamlandıktan sonra ortam kapatılır ve tüm medya kaynakları serbest bırakılır.  
  
 Ve <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> özellikleri medya oynatma denetlemek için tek yol değildir. Saat modunda, saat kontrol <xref:System.Windows.Controls.MediaElement> edebilirsiniz ve etkileşimli kontrol <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> <xref:System.Windows.Controls.MediaState.Manual>yöntemleri olduğunda kontrol edebilirsiniz. <xref:System.Windows.Controls.MediaElement>aşağıdaki öncelikleri değerlendirerek kontrol için bu yarışmayı yönetir.  
  
1. <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>. Ortam boşaltıldığında yerinde. Bu, tüm ortam kaynaklarının varsayılan olarak serbest <xref:System.Windows.Media.MediaClock> bırakılmasını sağlar, ancak bir <xref:System.Windows.Controls.MediaElement>..  
  
2. <xref:System.Windows.Media.MediaClock>. Ortam bir <xref:System.Windows.Controls.MediaElement.Clock%2A>. Ortam boşaltılırsa, ortam <xref:System.Windows.Media.MediaClock> <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> olduğu <xref:System.Windows.Controls.MediaState.Manual>sürece geçerli olacaktır. Saat modu her zaman yüklenmiş <xref:System.Windows.Controls.MediaElement>davranışı geçersiz kılar.  
  
3. <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>. Ortam yüklendiğinde yerinde.  
  
4. İnteraktif kontrol yöntemleri. Yerinde olduğunda <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> <xref:System.Windows.Controls.MediaState.Manual>. Mevcut kontrol yöntemleri <xref:System.Windows.Controls.MediaElement.Play%2A> <xref:System.Windows.Controls.MediaElement.Pause%2A>, <xref:System.Windows.Controls.MediaElement.Close%2A>, <xref:System.Windows.Controls.MediaElement.Stop%2A>, ve .  
  
### <a name="displaying-a-mediaelement"></a>MediaElement Görüntüleme  
 Bir <xref:System.Windows.Controls.MediaElement> görüntülemek için işlemek için içerik olması <xref:System.Windows.FrameworkElement.ActualWidth%2A> gerekir <xref:System.Windows.FrameworkElement.ActualHeight%2A> ve içerik yüklenene kadar kendi ve özellikleri sıfıra ayarlanmış olacaktır. Yalnızca ses içeriği için bu özellikler her zaman sıfırdır. Video içeriği için, <xref:System.Windows.Controls.MediaElement.MediaOpened> olay <xref:System.Windows.FrameworkElement.ActualWidth%2A> yükseltildikten <xref:System.Windows.FrameworkElement.ActualHeight%2A> sonra yüklenen ortamın boyutunu bildirir. Bu, ortam yüklenene <xref:System.Windows.Controls.MediaElement> kadar, [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> özellikler ayarlanmadığı sürece herhangi bir fiziksel alan kaplamayacağım anlamına gelir.  
  
 Hem de <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> özelliklerin ayarlanması, ortamiçin sağlanan alanı <xref:System.Windows.Controls.MediaElement>doldurmak için medyanın esnemesine neden olur. Ortamın özgün en boy oranını korumak <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> için, özellik ayarlanmalıdır, ancak her ikisi de ayarlanmamalıdır. Hem de <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> özellikleri ayarlamak, ortamın istenmeyebilecek sabit bir öğe boyutunda bulunmasına neden olur.  
  
 Ortam [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] alabilen sabit bir boyut öğesine sahip olmaktan kaçınmak için. Bu ya da <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> <xref:System.Windows.Controls.MediaState.Play> <xref:System.Windows.Controls.MediaState.Pause>ayarlayarak yapılır . Bir <xref:System.Windows.Controls.MediaState.Pause> durumda, ortam ön olur ve ilk kareyi sunar. Bir <xref:System.Windows.Controls.MediaState.Play> durumda, medya önceden hazırve oynamaya başlar.  
  
<a name="mediaplayer"></a>
## <a name="mediaplayer-class"></a>MediaPlayer Sınıfı  
 Sınıf <xref:System.Windows.Controls.MediaElement> bir çerçeve öğesi olduğu <xref:System.Windows.Media.MediaPlayer> için, sınıf nesnelerde <xref:System.Windows.Media.Drawing> kullanılmak üzere tasarlanmıştır. Çizim nesneleri, performans avantajları elde etmek için çerçeve düzeyi özelliklerinden <xref:System.Windows.Freezable> ödün verebildiğinizde veya özelliklere ihtiyacınız olduğunda kullanılır. <xref:System.Windows.Media.MediaPlayer>uygulamalarınızda medya içeriği sağlarken bu özelliklerden yararlanmanızı sağlar. Gibi <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Media.MediaPlayer> , bağımsız veya saat modunda kullanılabilir, <xref:System.Windows.Controls.MediaElement> ancak nesnenin boşve yüklü durumları yok. Bu, <xref:System.Windows.Media.MediaPlayer>oynatma denetimi karmaşıklığını azaltır.  
  
### <a name="controlling-mediaplayer"></a>MediaPlayer'ı Kontrol Etme  
 Durum <xref:System.Windows.Media.MediaPlayer> dilsiz olduğundan, medya oynatmayı denetlemenin yalnızca iki yolu vardır.  
  
1. İnteraktif kontrol yöntemleri. Bağımsız modda (özellik)`null` <xref:System.Windows.Media.MediaPlayer.Clock%2A> yerinde.  
  
2. <xref:System.Windows.Media.MediaClock>. Ortam bir <xref:System.Windows.Media.MediaPlayer.Clock%2A>.  
  
### <a name="displaying-a-mediaplayer"></a>MediaPlayer Görüntüleme  
 Teknik olarak, <xref:System.Windows.Media.MediaPlayer> fiziksel bir gösterimi olmadığı için görüntülenemez. Ancak, bir <xref:System.Windows.Media.Drawing> <xref:System.Windows.Media.VideoDrawing> sınıfta medya sunmak için kullanılabilir. Aşağıdaki örnek, bir <xref:System.Windows.Media.VideoDrawing> ortam görüntülemek için kullanımını gösterir.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Nesneler hakkında <xref:System.Windows.Media.Drawing> daha fazla bilgi için [Çizim Nesneleri Genel Bakış'a](drawing-objects-overview.md) bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.DrawingGroup>
- [Düzen](../advanced/layout.md)
- [Nasıl Dır Konular](audio-and-video-how-to-topics.md)
