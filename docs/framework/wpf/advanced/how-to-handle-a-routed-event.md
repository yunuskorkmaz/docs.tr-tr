---
title: "Nasıl yapılır: Gönderilmiş bir Olayı İşleme"
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
- routed events [WPF], handling
- bubbling events [WPF]
ms.assetid: 157787b4-f469-4047-8777-5b034145f32e
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c491ff4e231d932b3714d2d059b52bad2502368c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-handle-a-routed-event"></a><span data-ttu-id="63abd-102">Nasıl yapılır: Gönderilmiş bir Olayı İşleme</span><span class="sxs-lookup"><span data-stu-id="63abd-102">How to: Handle a Routed Event</span></span>
<span data-ttu-id="63abd-103">Bu örnek nasıl kabarcıklanma olayları iş ve nasıl yönlendirilmiş olay verileri işlemek bir işleyici yazılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="63abd-103">This example shows how bubbling events work and how to write a handler that can process the routed event data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63abd-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="63abd-104">Example</span></span>  
 <span data-ttu-id="63abd-105">İçinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], öğeleri, bir öğenin ağaç yapısında düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="63abd-105">In [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], elements are arranged in an element tree structure.</span></span> <span data-ttu-id="63abd-106">Üst öğenin alt öğelerini öğe ağacındaki tarafından başlangıçta gerçekleştirilen olayları işleme katılabilir.</span><span class="sxs-lookup"><span data-stu-id="63abd-106">The parent element can participate in the handling of events that are initially raised by child elements in the element tree.</span></span> <span data-ttu-id="63abd-107">Olay yönlendirme nedeniyle bu mümkün olur.</span><span class="sxs-lookup"><span data-stu-id="63abd-107">This is possible because of event routing.</span></span>  
  
 <span data-ttu-id="63abd-108">Yönlendirilmiş olaylar genellikle tırmanmasını veya tünel iki yönlendirme stratejiler birini izleyin.</span><span class="sxs-lookup"><span data-stu-id="63abd-108">Routed events typically follow one of two routing strategies, bubbling or tunneling.</span></span> <span data-ttu-id="63abd-109">Bu örnek kabarcıklanma olayı üzerinde odaklanır ve kullanır <xref:System.Windows.Controls.Primitives.ButtonBase.Click?displayProperty=nameWithType> yönlendirmenin nasıl çalıştığını göstermek için olay.</span><span class="sxs-lookup"><span data-stu-id="63abd-109">This example focuses on the bubbling event and uses the <xref:System.Windows.Controls.Primitives.ButtonBase.Click?displayProperty=nameWithType> event to show how routing works.</span></span>  
  
 <span data-ttu-id="63abd-110">Aşağıdaki örnekte iki oluşturur <xref:System.Windows.Controls.Button> denetler ve kullandığı [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öznitelik olan bu örnekte bir ortak üst öğesi için bir olay işleyicisi iliştirmek için sözdizimini <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="63abd-110">The following example creates two <xref:System.Windows.Controls.Button> controls and uses [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attribute syntax to attach an event handler to a common parent element, which in this example is <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="63abd-111">Her biri için ayrı ayrı olay işleyicileri ekleme yerine <xref:System.Windows.Controls.Button> alt öğesi örnek öznitelik sözdizimini kullanır olay işleyicisi iliştirmek için <xref:System.Windows.Controls.StackPanel> üst öğesi.</span><span class="sxs-lookup"><span data-stu-id="63abd-111">Instead of attaching individual event handlers for each <xref:System.Windows.Controls.Button> child element, the example uses attribute syntax to attach the event handler to the <xref:System.Windows.Controls.StackPanel> parent element.</span></span> <span data-ttu-id="63abd-112">Bu olay işleme deseni bir işleyici eklendiği öğelerin sayısını azaltmak için bir yöntem olarak olay yönlendirme kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="63abd-112">This event-handling pattern shows how to use event routing as a technique for reducing the number of elements where a handler is attached.</span></span> <span data-ttu-id="63abd-113">Her tüm kabarcıklanma olayları <xref:System.Windows.Controls.Button> üst öğenin yönlendir.</span><span class="sxs-lookup"><span data-stu-id="63abd-113">All the bubbling events for each <xref:System.Windows.Controls.Button> route through the parent element.</span></span>  
  
 <span data-ttu-id="63abd-114">Üst öğede unutmayın <xref:System.Windows.Controls.StackPanel> öğesi, <xref:System.Windows.Controls.Primitives.ButtonBase.Click> öznitelik adlandırarak kısmen yetkili olarak belirtilen olay adı <xref:System.Windows.Controls.Button> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="63abd-114">Note that on the parent <xref:System.Windows.Controls.StackPanel> element, the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event name specified as the attribute is partially qualified by naming the <xref:System.Windows.Controls.Button> class.</span></span> <span data-ttu-id="63abd-115"><xref:System.Windows.Controls.Button> Sınıfı bir <xref:System.Windows.Controls.Primitives.ButtonBase> olan sınıfın türetildiği <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay sınıftır.</span><span class="sxs-lookup"><span data-stu-id="63abd-115">The <xref:System.Windows.Controls.Button> class is a <xref:System.Windows.Controls.Primitives.ButtonBase> derived class that has the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event in its members listing.</span></span> <span data-ttu-id="63abd-116">O anda işlenen olay üyeleri yoksa, olay işleyicisi iliştirmek için kısmi nitelik tekniği gereklidir yönlendirilmiş olay işleyicinin bağlı öğesinin listesi.</span><span class="sxs-lookup"><span data-stu-id="63abd-116">This partial qualification technique for attaching an event handler is necessary if the event that is being handled does not exist in the members listing of the element where the routed event handler is attached.</span></span>  
  
 [!code-xaml[RoutedEventHandle#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml#xaml)]  
  
 <span data-ttu-id="63abd-117">Aşağıdaki örnek tanıtıcıları <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay.</span><span class="sxs-lookup"><span data-stu-id="63abd-117">The following example handles the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event.</span></span>  <span data-ttu-id="63abd-118">Örnek hangi öğesi olayını işler ve hangi öğesi olayını bildirir.</span><span class="sxs-lookup"><span data-stu-id="63abd-118">The example reports which element handles the event and which element raises the event.</span></span> <span data-ttu-id="63abd-119">Kullanıcı ya da düğmesini tıklattığında olay işleyicisi yürütülür.</span><span class="sxs-lookup"><span data-stu-id="63abd-119">The event handler is executed when the user clicks either button.</span></span>  
  
 [!code-csharp[RoutedEventHandle#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventHandle#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventHandle/VisualBasic/MainWindow.xaml.vb#handler)]  
  
## <a name="see-also"></a><span data-ttu-id="63abd-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="63abd-120">See Also</span></span>  
 <xref:System.Windows.RoutedEvent>  
 [<span data-ttu-id="63abd-121">Girişe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="63abd-121">Input Overview</span></span>](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [<span data-ttu-id="63abd-122">Yönlendirilmiş Olaylara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="63abd-122">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [<span data-ttu-id="63abd-123">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="63abd-123">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)  
 [<span data-ttu-id="63abd-124">Ayrıntılı XAML Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="63abd-124">XAML Syntax In Detail</span></span>](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)
