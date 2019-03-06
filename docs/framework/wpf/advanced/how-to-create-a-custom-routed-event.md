---
title: 'Nasıl yapılır: Özel Gönderilmiş Olay Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], creating
- events [WPF], routing
ms.assetid: b79f459a-1c3f-4045-b2d4-1659cc8eaa3c
ms.openlocfilehash: c351bec05fa8ad8438cb8521f6ab1e6277a40b1d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373406"
---
# <a name="how-to-create-a-custom-routed-event"></a><span data-ttu-id="4ebaf-102">Nasıl yapılır: Özel Gönderilmiş Olay Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4ebaf-102">How to: Create a Custom Routed Event</span></span>
<span data-ttu-id="4ebaf-103">Olay yönlendirme desteklemek özel etkinliği için kaydetmeniz gerekir. bir <xref:System.Windows.RoutedEvent> kullanarak <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4ebaf-103">For your custom event to support event routing, you need to register a <xref:System.Windows.RoutedEvent> using the <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> method.</span></span> <span data-ttu-id="4ebaf-104">Bu örnekte, özel gönderilmiş olay oluşturma hakkındaki temel bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4ebaf-104">This example demonstrates the basics of creating a custom routed event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ebaf-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ebaf-105">Example</span></span>  
 <span data-ttu-id="4ebaf-106">Aşağıdaki örnekte gösterildiği gibi önce kaydetmeniz bir <xref:System.Windows.RoutedEvent> kullanarak <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4ebaf-106">As shown in the following example, you first register a <xref:System.Windows.RoutedEvent> using the <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> method.</span></span> <span data-ttu-id="4ebaf-107">Kural olarak, <xref:System.Windows.RoutedEvent> statik alan adı soneki ile bitmelidir ***olay***.</span><span class="sxs-lookup"><span data-stu-id="4ebaf-107">By convention, the <xref:System.Windows.RoutedEvent> static field name should end with the suffix ***Event***.</span></span> <span data-ttu-id="4ebaf-108">Bu örnekte, olay adıdır `Tap` ve olay yönlendirme stratejisidir <xref:System.Windows.RoutingStrategy.Bubble>.</span><span class="sxs-lookup"><span data-stu-id="4ebaf-108">In this example, the name of the event is `Tap` and the routing strategy of the event is <xref:System.Windows.RoutingStrategy.Bubble>.</span></span> <span data-ttu-id="4ebaf-109">Kayıt çağrısından sonra ekleme ve kaldırma sağlayabilirsiniz [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] olayı için olay erişimcileri.</span><span class="sxs-lookup"><span data-stu-id="4ebaf-109">After the registration call, you can provide add-and-remove [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] event accessors for the event.</span></span>  
  
 <span data-ttu-id="4ebaf-110">Aracılığıyla olayı olsa bile unutmayın `OnTap` söz konusu örnekte, nasıl etkinliğiniz yükseltmeniz veya olayınızın değişiklikleri nasıl yanıt verdiği sanal yöntem gereksinimlerinize bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="4ebaf-110">Note that even though the event is raised through the `OnTap` virtual method in this particular example, how you raise your event or how your event responds to changes depends on your needs.</span></span>  
  
 <span data-ttu-id="4ebaf-111">Ayrıca bu örnek temel bir tüm öğesinin uyguladığını unutmayın <xref:System.Windows.Controls.Button>; o alt sınıf ayrı bir derlemeyi ve ardından özel bir sınıf ayrı olarak örneği [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] sayfası.</span><span class="sxs-lookup"><span data-stu-id="4ebaf-111">Note also that this example basically implements an entire subclass of <xref:System.Windows.Controls.Button>; that subclass is built as a separate assembly and then instantiated as a custom class on a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page.</span></span> <span data-ttu-id="4ebaf-112">Altsınıflanmış denetimler denetimden oluşan ağaçlara eklenebilir ve bu durumda, aynı olay yönlendirme özelliklerini bu denetimlerinde özel olaylar herhangi bir yerel sahip konsepti açıklamak amacıyla budur [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] öğesi.</span><span class="sxs-lookup"><span data-stu-id="4ebaf-112">This is to illustrate the concept that subclassed controls can be inserted into trees composed of other controls, and that in this situation, custom events on these controls have the very same event routing capabilities as any native [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] element does.</span></span>  
  
 [!code-csharp[RoutedEventCustom#CustomClass](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#customclass)]
 [!code-vb[RoutedEventCustom#CustomClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#customclass)]  
  
 [!code-xaml[RoutedEventCustom#Page](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/RoutedEventCustomApp/default.xaml#page)]  
  
 <span data-ttu-id="4ebaf-113">Tünel olayları oluşturulur aynı şekilde ancak ile <xref:System.Windows.RoutedEvent.RoutingStrategy%2A> kümesine <xref:System.Windows.RoutingStrategy.Tunnel> kayıt çağrısında.</span><span class="sxs-lookup"><span data-stu-id="4ebaf-113">Tunneling events are created the same way, but with <xref:System.Windows.RoutedEvent.RoutingStrategy%2A> set to <xref:System.Windows.RoutingStrategy.Tunnel> in the registration call.</span></span> <span data-ttu-id="4ebaf-114">Kural gereği, olayları tünel [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] "Preview" sözcüğü öneki.</span><span class="sxs-lookup"><span data-stu-id="4ebaf-114">By convention, tunneling events in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] are prefixed with the word "Preview".</span></span>  
  
 <span data-ttu-id="4ebaf-115">Nasıl tırmanma olayları iş bir örneğini görmek için bkz: [bir yönlendirilmiş olayı işleme](how-to-handle-a-routed-event.md).</span><span class="sxs-lookup"><span data-stu-id="4ebaf-115">To see an example of how bubbling events work, see [Handle a Routed Event](how-to-handle-a-routed-event.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ebaf-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ebaf-116">See also</span></span>
- [<span data-ttu-id="4ebaf-117">Yönlendirilmiş Olaylara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4ebaf-117">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="4ebaf-118">Girişe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4ebaf-118">Input Overview</span></span>](input-overview.md)
- [<span data-ttu-id="4ebaf-119">Denetim Yazımına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4ebaf-119">Control Authoring Overview</span></span>](../controls/control-authoring-overview.md)
