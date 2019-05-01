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
ms.openlocfilehash: 91e335f4d5adaa5279fb16805604f2e2848eeb8b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62002397"
---
# <a name="timing-events-overview"></a>Zamanlama Olaylarına Genel Bakış
Bu konu başlığı altında kullanılabilir beş zamanlama olayları kullanmayı açıklar <xref:System.Windows.Media.Animation.Timeline> ve <xref:System.Windows.Media.Animation.Clock> nesneleri.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuda anlamak için nasıl oluşturmak ve animasyonları kullanmak anlamanız gerekir. Animasyon ile çalışmaya başlamak için bkz. [animasyona genel bakış](animation-overview.md).  
  
 Özellikler animasyon uygulamak için birden çok yolla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:  
  
- **Görsel taslak nesneleri kullanarak** (işaretleme ve kod): Kullanabileceğiniz <xref:System.Windows.Media.Animation.Storyboard> düzenlemek ve bir veya daha fazla nesnelere animasyon dağıtmak için nesneleri. Bir örnek için bkz. [görsel taslak kullanarak özelliğe animasyon ekleme](how-to-animate-a-property-by-using-a-storyboard.md).  
  
- **Yerel animasyon kullanarak** (yalnızca kod): Uygulayabileceğiniz <xref:System.Windows.Media.Animation.AnimationTimeline> nesneleri doğrudan bunlar animasyon ekleme özellikleri. Bir örnek için bkz. [özelliği olmadan kullanarak bir görsel taslak animasyon](how-to-animate-a-property-without-using-a-storyboard.md).  
  
- **Saatler kullanarak** (yalnızca kod): Açıkça saat oluşturma yönetebilir ve animasyon saatler kendiniz dağıtın.  Bir örnek için bkz. [AnimationClock kullanarak bir özelliğe animasyon ekleme](how-to-animate-a-property-by-using-an-animationclock.md).  
  
 Bunları işaretleme ve kod kullanabilirsiniz, çünkü bu genel bakışta örneklerde <xref:System.Windows.Media.Animation.Storyboard> nesneleri. Bununla birlikte, açıklanan kavramlar özellikleri diğer yöntemleri için uygulanabilir.  
  
### <a name="what-is-a-clock"></a>Bir saat nedir?  
 Bir zaman çizelgesi kendisi tarafından gerçekten hiçbir şey yapmıyor dışında zaman kesimini açıklar. Zaman çizelgesinin olan <xref:System.Windows.Media.Animation.Clock> asıl işi yapan nesne: zaman çizelgesi için zamanlama ile ilgili çalışma zamanı durumu korur. Ne zaman kullanarak film şeritleri gibi çoğu durumda, bir saat için zaman çizelgeniz otomatik olarak oluşturulur. Ayrıca oluşturabileceğiniz bir <xref:System.Windows.Media.Animation.Clock> kullanılarak açık şekilde <xref:System.Windows.Media.Animation.Timeline.CreateClock%2A> yöntemi. Hakkında daha fazla bilgi için <xref:System.Windows.Media.Animation.Clock> nesneleri bkz [animasyon ve zamanlama sistemine genel bakış](animation-and-timing-system-overview.md).  
  
## <a name="why-use-events"></a>Olayları neden kullanmalısınız?  
 Biri hariç olmak üzere (son değer çizgisi hizalanmış arama), tüm etkileşimli zamanlama işlemleri zaman uyumsuzdur. Tam olarak ne zaman bunlar yürütülür bilmek bir yolu yoktur. Zamanlama işleminizi bağımlı olan başka bir kod varsa, bir sorun olabilir. Bir dikdörtgene animasyon zaman çizelgesi durdurmak istediğinizi varsayalım. Zaman Çizelgesi durduktan sonra dikdörtgen rengini değiştirin.  
  
 [!code-csharp[events_procedural#NeedForEventsFragment](~/samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#needforeventsfragment)]
 [!code-vb[events_procedural#NeedForEventsFragment](~/samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#needforeventsfragment)]  
  
 Önceki örnekte, film şeridi durdurulmadan önce ikinci satırlık bir kod yürütebilir. Durdurma zaman uyumsuz bir işlem olduğundan olmasıdır. Bir zaman çizelgesi veya durdurmak için saati belirten "zamanlama altyapının kadar sonraki değer çizgisi işlenen değil bir durdurma isteği" türlerdeki oluşturur.  
  
 Bir zaman çizelgesi tamamlandıktan sonra komutları yürütmek için zamanlama olayları kullanın. Aşağıdaki örnekte, bir olay işleyicisi, film şeridini yürütme sona erdikten sonra bir dikdörtgenin rengini değiştirmek için kullanılır.  
  
 [!code-csharp[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#registerforstoryboardcurrentstateinvalidatedevent)]
 [!code-vb[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#registerforstoryboardcurrentstateinvalidatedevent)]  
[!code-csharp[events_procedural#StoryboardCurrentStateInvalidatedEvent2](~/samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#storyboardcurrentstateinvalidatedevent2)]
[!code-vb[events_procedural#StoryboardCurrentStateInvalidatedEvent2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#storyboardcurrentstateinvalidatedevent2)]  
  
 Daha eksiksiz bir örnek için bkz: [alma bildirim, bir saatin durumu değişiklikleri](how-to-receive-notification-when-clock-state-changes.md).  
  
## <a name="public-events"></a>Ortak Olaylar  
 <xref:System.Windows.Media.Animation.Timeline> Ve <xref:System.Windows.Media.Animation.Clock> sınıflarının her ikisi de beş zamanlama olayları sağlar. Aşağıdaki tabloda, bu olaylar ve bunları tetikleme koşulları listeler.  
  
|Olay|Etkileşimli işlemi tetikleniyor|Diğer Tetikleyiciler|  
|-----------|--------------------------------------|--------------------|  
|**Tamamlandı**|Doldurmak için Atla|Saatin tamamlar.|  
|**CurrentGlobalSpeedInvalidated**|Duraklatma, sürdürme, arama, hız oranını ayarlamak, Atla doldurun, durdurmak için|Saatin tersine hızlandırır başlatır veya durdurur.|  
|**CurrentStateInvalidated**|Başlamak için doldurmak, durdurmak için Atla|Saatin başlatır, durdurur, veya doldurur.|  
|**CurrentTimeInvalidated**|Başlamak için arama, doldurmak, durdurmak için Atla|Saat ilerler.|  
|**RemoveRequested**|Kaldır||  
  
## <a name="ticking-and-event-consolidation"></a>Şekilde ilerleyen ve olay birleştirme  
 Nesnelere animasyon zaman [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], animasyonlarınızı yöneten zamanlama altyapısı olan. Zamanlama altyapısı zaman ilerleyişini izler ve her animasyonu durumunu hesaplar. Bir saniye içinde birçok değerlendirme geçişleri kolaylaştırır. Bu değerlendirme pasoları "ticks" bilinir  
  
 Saat döngüsü sık meydana gelirken, çok sayıda Ölçü çizgileri arasında gerçekleşmesi için mümkündür. Örneğin, bir zaman çizelgesi durdurulacak, çalışmaya ve tekrar, bu durumda geçerli durumuna üç kez değişmiş olacak. Teorik olarak, birden çok kez içinde tek bir tick olayı; Ancak, böylece her olay, her değer çizgisi başına en fazla bir kez yükseltilebilir zamanlama altyapısı olayları birleştirir.  
  
## <a name="registering-for-events"></a>Olayları'nın kaydedilmesi  
 Zamanlama etkinliklere kaydolmak için iki yolu vardır: zaman çizelgesinden oluşturulan saat veya zaman çizelgesi ile kaydedebilirsiniz. Yalnızca koddan yapılabilir ancak doğrudan saatiyle için bir olay kaydetme oldukça oldukça basittir. Bir zaman çizelgesi işaretleme veya kod olan olaylar için kaydedebilirsiniz. Sonraki bölümde, bir zaman çizelgesi saati olaylarla kaydolmak açıklar.  
  
<a name="registeringforclockeventswithatimeline"></a>   
## <a name="registering-for-clock-events-with-a-timeline"></a>Bir zaman çizelgesi olan saat olaylar için kaydetme  
 Bir zaman çizelgesi rağmen 's <xref:System.Windows.Media.Animation.Timeline.Completed>, <xref:System.Windows.Media.Animation.Timeline.CurrentGlobalSpeedInvalidated>, <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>, <xref:System.Windows.Media.Animation.Timeline.CurrentTimeInvalidated>, ve <xref:System.Windows.Media.Animation.Timeline.RemoveRequested> olayları görünür bu olaylar gerçekte ilişkilendirir için bir olay işleyicisi ile kaydetme ve zaman çizelgesi ile'ilişkilendirilecek <xref:System.Windows.Media.Animation.Clock> Zaman Çizelgesi oluşturulur.  
  
 İçin kaydolduğunuzda <xref:System.Windows.Media.Animation.Timeline.Completed> olay bir zaman çizelgesi üzerinde örneğin, gerçekten söyleyen kaydolmak için sistem <xref:System.Windows.Media.Animation.Clock.Completed> oluşturulan her zaman çizelgesi saati olayı. Kod içinde bu olayın önce kaydetmeniz gerekir <xref:System.Windows.Media.Animation.Clock> ; bu zaman çizelgesi için oluşturulan Aksi takdirde, bildirim almazsınız. Bu otomatik olarak gerçekleşir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; ayrıştırıcının önce olayı için otomatik olarak kaydeder. <xref:System.Windows.Media.Animation.Clock> oluşturulur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Animasyon ve Zamanlama Sistemine Genel Bakış](animation-and-timing-system-overview.md)
- [Animasyona Genel bakış](animation-overview.md)
- [Zamanlama Davranışlarına Genel Bakış](timing-behaviors-overview.md)
