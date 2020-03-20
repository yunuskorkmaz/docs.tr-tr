---
title: Zamanlama Olaylarına Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- timelines [WPF]
- timing events [WPF]
ms.assetid: 597e3280-0867-4359-a97b-5b2f4149e350
ms.openlocfilehash: ee45441e9ad09c60d8b61ecce4ef08b0027ce29e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145416"
---
# <a name="timing-events-overview"></a>Zamanlama Olaylarına Genel Bakış
Bu konu, kullanılabilir beş zamanlama <xref:System.Windows.Media.Animation.Timeline> olayının <xref:System.Windows.Media.Animation.Clock> ve nesnelerin nasıl kullanılacağını açıklar.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuyu anlamak için animasyonların nasıl oluşturulup kullanılacağını anlamanız gerekir. Animasyona başlamak için [Animasyona Genel Bakış'a](animation-overview.md)bakın.  
  
 Özellikleri animasyona almanın birden çok [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]yolu vardır:  
  
- **Film şeridi nesnelerini** (biçimlendirme ve kod): Animasyonları düzenlemek ve bir veya daha fazla nesneye dağıtmak için nesneleri kullanabilirsiniz. <xref:System.Windows.Media.Animation.Storyboard> Örneğin, [Storyboard kullanarak Bir Özellik Animasyon](how-to-animate-a-property-by-using-a-storyboard.md)bakın.  
  
- **Yerel animasyonları kullanma** (yalnızca kod): Nesneleri doğrudan canlandırdıkları özelliklere uygulayabilirsiniz. <xref:System.Windows.Media.Animation.AnimationTimeline> Örneğin, Bir [Storyboard kullanmadan bir Özellik Animasyon](how-to-animate-a-property-without-using-a-storyboard.md)bakın.  
  
- **Saatleri kullanma** (yalnızca kod): Saat oluşturmayı açıkça yönetebilir ve animasyon saatlerini kendiniz dağıtabilirsiniz.  Örneğin, Animasyon [Saati kullanarak Bir Özelliği Animate'e](how-to-animate-a-property-by-using-an-animationclock.md)bakın.  
  
 Bunları biçimlendirme ve kodda kullanabileceğiniz için, bu <xref:System.Windows.Media.Animation.Storyboard> genel bakışta ki örnekler nesneleri kullanır. Ancak, açıklanan kavramlar canlandırma özelliklerinin diğer yöntemlerine uygulanabilir.  
  
### <a name="what-is-a-clock"></a>Saat nedir?  
 Bir zaman çizelgesi, tek başına, aslında zaman bir segment tanımlamak dışında bir şey yapmaz. Gerçek işi yapan zaman <xref:System.Windows.Media.Animation.Clock> çizelgesinin nesnesidir: zaman çizelgesi için zamanlamayla ilgili çalışma zamanı durumunu korur. Çoğu durumda, örneğin film şeridi kullanırken, zaman tüneliniz için otomatik olarak bir saat oluşturulur. Yöntemi kullanarak <xref:System.Windows.Media.Animation.Timeline.CreateClock%2A> açıkça <xref:System.Windows.Media.Animation.Clock> bir yöntem oluşturabilirsiniz. Nesneler hakkında <xref:System.Windows.Media.Animation.Clock> daha fazla bilgi için [Animasyon ve Zamanlama Sistemine Genel Bakış'a](animation-and-timing-system-overview.md)bakın.  
  
## <a name="why-use-events"></a>Neden Olayları Kullanır?  
 Bir (son kene hizalanmış aramak) dışında, tüm etkileşimli zamanlama işlemleri asynchronous vardır. Tam olarak ne zaman infaz acaklarını bilmenin bir yolu yok. Zamanlama işleminize bağlı başka bir kodunuz olduğunda bu bir sorun olabilir. Dikdörtgeni canlandıran bir zaman çizelgesini durdurmak istediğinizi varsayalım. Zaman çizelgesi durduktan sonra, dikdörtgenin rengini değiştirirsiniz.  
  
 [!code-csharp[events_procedural#NeedForEventsFragment](~/samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#needforeventsfragment)]
 [!code-vb[events_procedural#NeedForEventsFragment](~/samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#needforeventsfragment)]  
  
 Önceki örnekte, ikinci kod satırı film şeridi durmadan önce çalıştırılabilirsiniz. Çünkü durmak eşzamanlı bir operasyondur. Bir zaman çizelgesinin veya saatin durmasını söylemek, zamanlama motorunun bir sonraki işaretine kadar işlenmeyen türden bir "durdurma isteği" oluşturur.  
  
 Bir zaman çizelgesi tamamlandıktan sonra komutları yürütmek için zamanlama olaylarını kullanın. Aşağıdaki örnekte, film şeridi çalmayı durdurduktan sonra dikdörtgenin rengini değiştirmek için bir olay işleyicisi kullanılır.  
  
 [!code-csharp[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#registerforstoryboardcurrentstateinvalidatedevent)]
 [!code-vb[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#registerforstoryboardcurrentstateinvalidatedevent)]  
[!code-csharp[events_procedural#StoryboardCurrentStateInvalidatedEvent2](~/samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#storyboardcurrentstateinvalidatedevent2)]
[!code-vb[events_procedural#StoryboardCurrentStateInvalidatedEvent2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#storyboardcurrentstateinvalidatedevent2)]  
  
 Daha eksiksiz bir örnek için, [Saatin Durumu Değiştiğinde Bildirim Al'a](how-to-receive-notification-when-clock-state-changes.md)bakın.  
  
## <a name="public-events"></a>Ortak Olaylar  
 Ve <xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.Clock> sınıfların her ikisi de beş zamanlama olayı sağlar. Aşağıdaki tabloda bu olaylar ve bunları tetikleyen koşullar listelenmektedir.  
  
|Olay|Etkileşimli işlemi tetikleme|Diğer tetikleyiciler|  
|-----------|--------------------------------------|--------------------|  
|**Tamamlandı**|Doldurmak için atla|Saat tamamlar.|  
|**Currentglobalspeedınvalidated**|Duraklatma, devam etme, arama, hız oranını ayarlama, doldurmak için atla, durdurmak|Saat tersine çevirir, hızlandırır, başlatır veya durur.|  
|**Currentstateınvalidated**|Başlayın, doldurmak için atlayın, durdurun|Saat başlar, durur veya doluyor.|  
|**GeçerliZaman Geçersiz Kılın**|Başlamak, aramak, doldurmak için atlamak, durdurmak|Saat ilerliyor.|  
|**Kaldırma İstenilen**|Kaldır||  
  
## <a name="ticking-and-event-consolidation"></a>Ticking ve Olay Konsolidasyonu  
 Nesneleri animasyona aldığınızda, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]animasyonlarınızı yöneten zamanlama motoruolur. Zamanlama motoru zamanın ilerlemesini izler ve her animasyonun durumunu hesaplar. Bu tür değerlendirme bir saniye içinde birçok geçer yapar. Bu değerlendirme geçişleri "kene" olarak bilinir.  
  
 Keneler sık sık meydana gelirken, keneler arasında birçok şeyin olması mümkündür. Örneğin, bir zaman çizelgesi durdurulabilir, başlatılabilir ve yeniden durdurulabilir ve bu durumda geçerli durumu üç kez değişmiş olur. Teorik olarak, olay tek bir kene birden çok kez yükseltilmiş olabilir; ancak, zamanlama altyapısı olayları birleştirir, böylece her olay kene başına en fazla bir kez yükseltilebilir.  
  
## <a name="registering-for-events"></a>Etkinliklere Kayıt  
 Zamanlama olayları için kaydolmanın iki yolu vardır: zaman çizelgesine veya zaman çizelgesinden oluşturulan saate kaydolabilirsiniz. Yalnızca koddan yapılabilecek olsa da, bir olay için doğrudan bir saatle kaydolmak oldukça kolaydır. Biçimlendirme veya koddan bir zaman çizelgesi olan olaylar için kaydolabilirsiniz. Sonraki bölümde, zaman çizelgesi olan saat olayları için nasıl kaydolunur açıklanır.  
  
<a name="registeringforclockeventswithatimeline"></a>
## <a name="registering-for-clock-events-with-a-timeline"></a>Zaman Çizelgesi ile Saat Olayları için Kayıt  
 Bir zaman çizelgesi <xref:System.Windows.Media.Animation.Timeline.Completed> <xref:System.Windows.Media.Animation.Timeline.CurrentGlobalSpeedInvalidated>, <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> <xref:System.Windows.Media.Animation.Timeline.CurrentTimeInvalidated>, <xref:System.Windows.Media.Animation.Timeline.RemoveRequested> , , ve olaylar zaman çizelgesi ile ilişkili gibi görünse de, <xref:System.Windows.Media.Animation.Clock> bu olaylar için kayıt aslında zaman çizelgesi için oluşturulan bir olay işleyicisi ilişkilendirir.  
  
 Örneğin, <xref:System.Windows.Media.Animation.Timeline.Completed> bir zaman çizelgesinde olay için kaydolduğunuzda, aslında sistemiçin zaman <xref:System.Windows.Media.Animation.Clock.Completed> çizelgesi için oluşturulan her saat in olay için kayıt söylüyorum. Kod olarak, bu zaman çizelgesi <xref:System.Windows.Media.Animation.Clock> oluşturulmadan önce bu olay için kaydolmanız gerekir; aksi takdirde bildirim almazsınız. Bu otomatik olarak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]olur ; parser oluşturulmadan önce <xref:System.Windows.Media.Animation.Clock> olay için otomatik olarak kaydeder.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Animasyon ve Zamanlama Sistemine Genel Bakış](animation-and-timing-system-overview.md)
- [Animasyona Genel bakış](animation-overview.md)
- [Zamanlama Davranışlarına Genel Bakış](timing-behaviors-overview.md)
