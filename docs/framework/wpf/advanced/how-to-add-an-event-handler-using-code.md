---
title: 'Nasıl yapılır: Kod Kullanarak bir Olay İşleyicisi Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- event handlers [WPF], adding
- XAML [WPF], adding event handlers
ms.assetid: 269c61e0-6bd9-4291-9bed-1c5ee66da486
ms.openlocfilehash: 457b8cf5c68096b20df7fe39f1cc3f40358f34d0
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460431"
---
# <a name="how-to-add-an-event-handler-using-code"></a><span data-ttu-id="fadec-102">Nasıl yapılır: Kod Kullanarak bir Olay İşleyicisi Ekleme</span><span class="sxs-lookup"><span data-stu-id="fadec-102">How to: Add an Event Handler Using Code</span></span>
<span data-ttu-id="fadec-103">Bu örnek, kod kullanarak bir öğeye bir olay işleyicisinin nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fadec-103">This example shows how to add an event handler to an element by using code.</span></span>  
  
 <span data-ttu-id="fadec-104">Bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öğesine bir olay işleyicisi eklemek istiyorsanız ve öğesini içeren biçimlendirme sayfası zaten yüklüyse, kodu kullanarak işleyiciyi eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fadec-104">If you want to add an event handler to a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] element, and the markup page that contains the element has already been loaded, you must add the handler using code.</span></span> <span data-ttu-id="fadec-105">Alternatif olarak, kod kullanarak bir uygulama için öğe ağacını oluşturuyorsanız ve [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]kullanarak herhangi bir öğe bildirmiyorsanız, oluşturulan öğe ağacına olay işleyicileri eklemek için belirli yöntemleri çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fadec-105">Alternatively, if you are building up the element tree for an application entirely using code and not declaring any elements using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can call specific methods to add event handlers to the constructed element tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fadec-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="fadec-106">Example</span></span>  
 <span data-ttu-id="fadec-107">Aşağıdaki örnek, ilk olarak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]tanımlanmış varolan bir sayfaya yeni bir <xref:System.Windows.Controls.Button> ekler.</span><span class="sxs-lookup"><span data-stu-id="fadec-107">The following example adds a new <xref:System.Windows.Controls.Button> to an existing page that is initially defined in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="fadec-108">Arka plan kod dosyası bir olay işleyicisi yöntemi uygular ve sonra bu yöntemi <xref:System.Windows.Controls.Button>yeni bir olay işleyicisi olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="fadec-108">A code-behind file implements an event handler method and then adds that method as a new event handler on the <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="fadec-109">Örnek C# , bir olaya bir işleyici atamak için `+=` işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="fadec-109">The C# example uses the `+=` operator to assign a handler to an event.</span></span> <span data-ttu-id="fadec-110">Bu, ortak dil çalışma zamanı (CLR) olay işleme modelinde bir işleyici atamak için kullanılan işleçtir.</span><span class="sxs-lookup"><span data-stu-id="fadec-110">This is the same operator that is used to assign a handler in the common language runtime (CLR) event handling model.</span></span> <span data-ttu-id="fadec-111">Microsoft Visual Basic, olay işleyicilerini ekleme yöntemi olarak bu işleci desteklemez.</span><span class="sxs-lookup"><span data-stu-id="fadec-111">Microsoft Visual Basic does not support this operator as a means of adding event handlers.</span></span> <span data-ttu-id="fadec-112">Bunun yerine iki teknikten birini gerektirir:</span><span class="sxs-lookup"><span data-stu-id="fadec-112">It instead requires one of two techniques:</span></span>  
  
- <span data-ttu-id="fadec-113">Olay işleyicisi uygulamasına başvurmak için <xref:System.Windows.UIElement.AddHandler%2A> yöntemini bir `AddressOf` işleciyle birlikte kullanın.</span><span class="sxs-lookup"><span data-stu-id="fadec-113">Use the <xref:System.Windows.UIElement.AddHandler%2A> method, together with an `AddressOf` operator, to reference the event handler implementation.</span></span>  
  
- <span data-ttu-id="fadec-114">`Handles` anahtar sözcüğünü olay işleyicisi tanımının bir parçası olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="fadec-114">Use the `Handles` keyword as part of the event handler definition.</span></span> <span data-ttu-id="fadec-115">Bu teknik burada gösterilmez; bkz. [Visual Basic ve WPF olay işleme](visual-basic-and-wpf-event-handling.md).</span><span class="sxs-lookup"><span data-stu-id="fadec-115">This technique is not shown here; see [Visual Basic and WPF Event Handling](visual-basic-and-wpf-event-handling.md).</span></span>  
  
 [!code-xaml[RoutedEventAddRemoveHandler#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
> <span data-ttu-id="fadec-116">İlk ayrıştırılmış [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfasında bir olay işleyicisi eklemek çok basittir.</span><span class="sxs-lookup"><span data-stu-id="fadec-116">Adding an event handler in the initially parsed [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page is much simpler.</span></span> <span data-ttu-id="fadec-117">Olay işleyicisini eklemek istediğiniz nesne öğesi içinde, işlemek istediğiniz olayın adıyla eşleşen bir öznitelik ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fadec-117">Within the object element where you want to add the event handler, add an attribute that matches the name of the event that you want to handle.</span></span> <span data-ttu-id="fadec-118">Daha sonra bu özniteliğin değerini, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfasının arka plan kod dosyasında tanımladığınız olay işleyicisi yönteminin adı olarak belirtin.</span><span class="sxs-lookup"><span data-stu-id="fadec-118">Then specify the value of that attribute as the name of the event handler method that you defined in the code-behind file of the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page.</span></span> <span data-ttu-id="fadec-119">Daha fazla bilgi için bkz. [xaml 'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md) veya [yönlendirilmiş olaylara genel bakış](routed-events-overview.md).</span><span class="sxs-lookup"><span data-stu-id="fadec-119">For more information, see [XAML Overview (WPF)](../../../desktop-wpf/fundamentals/xaml.md) or [Routed Events Overview](routed-events-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fadec-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fadec-120">See also</span></span>

- [<span data-ttu-id="fadec-121">Yönlendirilmiş Olaylara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fadec-121">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="fadec-122">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="fadec-122">How-to Topics</span></span>](events-how-to-topics.md)
