---
title: 'Nasıl yapılır: Yönlendirilmiş Olayı İşleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], handling
- bubbling events [WPF]
ms.assetid: 157787b4-f469-4047-8777-5b034145f32e
ms.openlocfilehash: edb3d6724af89b7e85986c50b579084e3c4e5070
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211601"
---
# <a name="how-to-handle-a-routed-event"></a><span data-ttu-id="774a3-102">Nasıl yapılır: Yönlendirilmiş Olayı İşleme</span><span class="sxs-lookup"><span data-stu-id="774a3-102">How to: Handle a Routed Event</span></span>
<span data-ttu-id="774a3-103">Bu örnek nasıl tırmanma olayları iş ve nasıl yönlendirilmiş olay verileri işleyen bir işleyici yazılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="774a3-103">This example shows how bubbling events work and how to write a handler that can process the routed event data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="774a3-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="774a3-104">Example</span></span>  
 <span data-ttu-id="774a3-105">İçinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], öğeleri bir öğe ağaç yapısında düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="774a3-105">In [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], elements are arranged in an element tree structure.</span></span> <span data-ttu-id="774a3-106">Üst öğe, başlangıçta öğe ağacında bir alt öğe tarafından oluşturulan olayları işleme katılabilir.</span><span class="sxs-lookup"><span data-stu-id="774a3-106">The parent element can participate in the handling of events that are initially raised by child elements in the element tree.</span></span> <span data-ttu-id="774a3-107">Olay yönlendirme nedeniyle bu olasıdır.</span><span class="sxs-lookup"><span data-stu-id="774a3-107">This is possible because of event routing.</span></span>  
  
 <span data-ttu-id="774a3-108">Yönlendirilmiş olaylar genellikle tırmanma veya tünel iki yönlendirme stratejileri birini izleyin.</span><span class="sxs-lookup"><span data-stu-id="774a3-108">Routed events typically follow one of two routing strategies, bubbling or tunneling.</span></span> <span data-ttu-id="774a3-109">Bu örnek, tırmanma olayı üzerinde odaklanır ve kullandığı <xref:System.Windows.Controls.Primitives.ButtonBase.Click?displayProperty=nameWithType> yönlendirmenin nasıl çalıştığını göstermek için olay.</span><span class="sxs-lookup"><span data-stu-id="774a3-109">This example focuses on the bubbling event and uses the <xref:System.Windows.Controls.Primitives.ButtonBase.Click?displayProperty=nameWithType> event to show how routing works.</span></span>  
  
 <span data-ttu-id="774a3-110">Aşağıdaki örnek iki oluşturur <xref:System.Windows.Controls.Button> denetler ve kullandığı [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öznitelik olan bu örnekte bir üst öğe, bir olay işleyicisi eklemek için sözdizimi <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="774a3-110">The following example creates two <xref:System.Windows.Controls.Button> controls and uses [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attribute syntax to attach an event handler to a common parent element, which in this example is <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="774a3-111">Her biri için ayrı bir olay işleyicileri ekleme yerine <xref:System.Windows.Controls.Button> alt öğesi örnekte öznitelik sözdizimi için olay işleyicisi eklemek için <xref:System.Windows.Controls.StackPanel> üst öğe.</span><span class="sxs-lookup"><span data-stu-id="774a3-111">Instead of attaching individual event handlers for each <xref:System.Windows.Controls.Button> child element, the example uses attribute syntax to attach the event handler to the <xref:System.Windows.Controls.StackPanel> parent element.</span></span> <span data-ttu-id="774a3-112">Bu olay işleme düzen işleyicisi eklendiği öğelerin sayısını azaltmak için bir yöntem olarak olay yönlendirme kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="774a3-112">This event-handling pattern shows how to use event routing as a technique for reducing the number of elements where a handler is attached.</span></span> <span data-ttu-id="774a3-113">Tırmanma olayları her <xref:System.Windows.Controls.Button> yolunun üst öğesi.</span><span class="sxs-lookup"><span data-stu-id="774a3-113">All the bubbling events for each <xref:System.Windows.Controls.Button> route through the parent element.</span></span>  
  
 <span data-ttu-id="774a3-114">Üst öğede unutmayın <xref:System.Windows.Controls.StackPanel> öğesi <xref:System.Windows.Controls.Primitives.ButtonBase.Click> öznitelik adlandırarak kısmen tam olarak belirtilen olay adı <xref:System.Windows.Controls.Button> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="774a3-114">Note that on the parent <xref:System.Windows.Controls.StackPanel> element, the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event name specified as the attribute is partially qualified by naming the <xref:System.Windows.Controls.Button> class.</span></span> <span data-ttu-id="774a3-115"><xref:System.Windows.Controls.Button> Sınıfı bir <xref:System.Windows.Controls.Primitives.ButtonBase> türetilmiş sınıf <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay sınıftır.</span><span class="sxs-lookup"><span data-stu-id="774a3-115">The <xref:System.Windows.Controls.Button> class is a <xref:System.Windows.Controls.Primitives.ButtonBase> derived class that has the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event in its members listing.</span></span> <span data-ttu-id="774a3-116">Bir olay işleyicisi eklemek için bu kısmi nitelik teknik o anda işlenen olay üyeleri mevcut değilse gerekli olan yönlendirilmiş olay işleyicisi bağlı olduğu öğesinin listeleme.</span><span class="sxs-lookup"><span data-stu-id="774a3-116">This partial qualification technique for attaching an event handler is necessary if the event that is being handled does not exist in the members listing of the element where the routed event handler is attached.</span></span>  
  
 [!code-xaml[RoutedEventHandle#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml#xaml)]  
  
 <span data-ttu-id="774a3-117">Aşağıdaki örnek tutamaçları <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay.</span><span class="sxs-lookup"><span data-stu-id="774a3-117">The following example handles the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event.</span></span>  <span data-ttu-id="774a3-118">Örnek raporları hangi öğe olayını işler ve hangi öğe olayını başlatır.</span><span class="sxs-lookup"><span data-stu-id="774a3-118">The example reports which element handles the event and which element raises the event.</span></span> <span data-ttu-id="774a3-119">Kullanıcı herhangi bir düğmeyi tıkladığında bir olay işleyicisi yürütülür.</span><span class="sxs-lookup"><span data-stu-id="774a3-119">The event handler is executed when the user clicks either button.</span></span>  
  
 [!code-csharp[RoutedEventHandle#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventHandle#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventHandle/VisualBasic/MainWindow.xaml.vb#handler)]  
  
## <a name="see-also"></a><span data-ttu-id="774a3-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="774a3-120">See also</span></span>

- <xref:System.Windows.RoutedEvent>
- [<span data-ttu-id="774a3-121">Girişe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="774a3-121">Input Overview</span></span>](input-overview.md)
- [<span data-ttu-id="774a3-122">Gönderilmiş Olaylara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="774a3-122">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="774a3-123">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="774a3-123">How-to Topics</span></span>](events-how-to-topics.md)
- [<span data-ttu-id="774a3-124">Ayrıntılı XAML Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="774a3-124">XAML Syntax In Detail</span></span>](xaml-syntax-in-detail.md)
