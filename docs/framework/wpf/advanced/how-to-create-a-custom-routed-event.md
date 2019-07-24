---
title: 'Nasıl yapılır: Özel Yönlendirilmiş Olay Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], creating
- events [WPF], routing
ms.assetid: b79f459a-1c3f-4045-b2d4-1659cc8eaa3c
ms.openlocfilehash: cbfb88af4e35e3f090248982bb14d6b7a3a03cef
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401473"
---
# <a name="how-to-create-a-custom-routed-event"></a><span data-ttu-id="e209a-102">Nasıl yapılır: Özel Yönlendirilmiş Olay Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e209a-102">How to: Create a Custom Routed Event</span></span>
<span data-ttu-id="e209a-103">Olay yönlendirmeyi desteklemek için özel olaylarınızın, <xref:System.Windows.RoutedEvent> <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> yöntemini kullanarak kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e209a-103">For your custom event to support event routing, you need to register a <xref:System.Windows.RoutedEvent> using the <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> method.</span></span> <span data-ttu-id="e209a-104">Bu örnekte, özel bir yönlendirilmiş olay oluşturmanın temelleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e209a-104">This example demonstrates the basics of creating a custom routed event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e209a-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="e209a-105">Example</span></span>  
 <span data-ttu-id="e209a-106">Aşağıdaki örnekte gösterildiği gibi, öncelikle <xref:System.Windows.RoutedEvent> <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> yöntemini kullanarak bir kayıt kaydedersiniz.</span><span class="sxs-lookup"><span data-stu-id="e209a-106">As shown in the following example, you first register a <xref:System.Windows.RoutedEvent> using the <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> method.</span></span> <span data-ttu-id="e209a-107">Kurala <xref:System.Windows.RoutedEvent> göre statik alan adı, son ek ***olay***ile bitmelidir.</span><span class="sxs-lookup"><span data-stu-id="e209a-107">By convention, the <xref:System.Windows.RoutedEvent> static field name should end with the suffix ***Event***.</span></span> <span data-ttu-id="e209a-108">Bu örnekte, olayın `Tap` adı ve <xref:System.Windows.RoutingStrategy.Bubble>olay yönlendirme stratejisidir.</span><span class="sxs-lookup"><span data-stu-id="e209a-108">In this example, the name of the event is `Tap` and the routing strategy of the event is <xref:System.Windows.RoutingStrategy.Bubble>.</span></span> <span data-ttu-id="e209a-109">Kayıt çağrısından sonra, olay için ortak dil çalışma zamanı (CLR) olay erişimcileri ekleme ve kaldırma sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e209a-109">After the registration call, you can provide add-and-remove common language runtime (CLR) event accessors for the event.</span></span>  
  
 <span data-ttu-id="e209a-110">Olay bu özel örnekteki `OnTap` sanal yöntem üzerinden oluşturulsa da, olaylarınızı nasıl yükseltebileceğinizi veya olaylarınızın değişikliklere nasıl yanıt vereceğini, gereksinimlerinize bağlı olarak unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e209a-110">Note that even though the event is raised through the `OnTap` virtual method in this particular example, how you raise your event or how your event responds to changes depends on your needs.</span></span>  
  
 <span data-ttu-id="e209a-111">Ayrıca bu örnek, <xref:System.Windows.Controls.Button>temel olarak bir alt sınıfının tamamını uygular; bu alt sınıf ayrı bir derleme olarak oluşturulur ve ardından ayrı [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] bir sayfada özel bir sınıf olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e209a-111">Note also that this example basically implements an entire subclass of <xref:System.Windows.Controls.Button>; that subclass is built as a separate assembly and then instantiated as a custom class on a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page.</span></span> <span data-ttu-id="e209a-112">Bu, alt sınıflı denetimlerin diğer denetimlerden oluşan ağaçlara eklenebilme kavramını göstermek ve bu durumda, bu denetimlerde özel olayların herhangi bir yerel [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] öğe ile aynı olay yönlendirme özelliklerine sahip olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e209a-112">This is to illustrate the concept that subclassed controls can be inserted into trees composed of other controls, and that in this situation, custom events on these controls have the very same event routing capabilities as any native [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] element does.</span></span>  
  
 [!code-csharp[RoutedEventCustom#CustomClass](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#customclass)]
 [!code-vb[RoutedEventCustom#CustomClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#customclass)]  
  
 [!code-xaml[RoutedEventCustom#Page](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/RoutedEventCustomApp/default.xaml#page)]  
  
 <span data-ttu-id="e209a-113">Tünel olayları aynı şekilde oluşturulur, ancak <xref:System.Windows.RoutedEvent.RoutingStrategy%2A> kayıt çağrısında olarak <xref:System.Windows.RoutingStrategy.Tunnel> ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="e209a-113">Tunneling events are created the same way, but with <xref:System.Windows.RoutedEvent.RoutingStrategy%2A> set to <xref:System.Windows.RoutingStrategy.Tunnel> in the registration call.</span></span> <span data-ttu-id="e209a-114">Kurala göre, içindeki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tünel olayları "Preview" kelimesiyle ön ek olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="e209a-114">By convention, tunneling events in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] are prefixed with the word "Preview".</span></span>  
  
 <span data-ttu-id="e209a-115">Kabarcıklanma olaylarının nasıl çalıştığı hakkında bir örnek görmek için bkz. [yönlendirilmiş olayı işleme](how-to-handle-a-routed-event.md).</span><span class="sxs-lookup"><span data-stu-id="e209a-115">To see an example of how bubbling events work, see [Handle a Routed Event](how-to-handle-a-routed-event.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e209a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e209a-116">See also</span></span>

- [<span data-ttu-id="e209a-117">Yönlendirilmiş Olaylara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e209a-117">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="e209a-118">Girişe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e209a-118">Input Overview</span></span>](input-overview.md)
- [<span data-ttu-id="e209a-119">Denetim Yazımına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e209a-119">Control Authoring Overview</span></span>](../controls/control-authoring-overview.md)
