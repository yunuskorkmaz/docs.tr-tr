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
ms.openlocfilehash: 4e8344ebcb0406a7da29787c5a4377760f55597e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54499138"
---
# <a name="how-to-add-an-event-handler-using-code"></a><span data-ttu-id="84f39-102">Nasıl yapılır: Kod Kullanarak bir Olay İşleyicisi Ekleme</span><span class="sxs-lookup"><span data-stu-id="84f39-102">How to: Add an Event Handler Using Code</span></span>
<span data-ttu-id="84f39-103">Bu örnek kod kullanarak bir öğe için bir olay işleyicisi eklemek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="84f39-103">This example shows how to add an event handler to an element by using code.</span></span>  
  
 <span data-ttu-id="84f39-104">Bir olay işleyicisi eklemek istiyorsanız bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öğesi ve öğeyi içeren biçimlendirme sayfası zaten yüklendi, kod kullanarak işleyicisi eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="84f39-104">If you want to add an event handler to a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] element, and the markup page that contains the element has already been loaded, you must add the handler using code.</span></span> <span data-ttu-id="84f39-105">Alternatif olarak, uygulamanın tamamen kodla ve kullanarak herhangi bir öğeyi bildirmeyerek öğe ağacında oluşturmakta olduğunuz varsa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], oluşturulmuş öğe ağacına olay işleyicileri eklemek için özel bir yöntem çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84f39-105">Alternatively, if you are building up the element tree for an application entirely using code and not declaring any elements using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can call specific methods to add event handlers to the constructed element tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84f39-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="84f39-106">Example</span></span>  
 <span data-ttu-id="84f39-107">Aşağıdaki örnek yeni bir ekler <xref:System.Windows.Controls.Button> başlangıçta tanımlanan varolan sayfasına [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="84f39-107">The following example adds a new <xref:System.Windows.Controls.Button> to an existing page that is initially defined in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="84f39-108">Arka plan kod dosyasında olay işleyicisi yöntemi uygular ve sonra bu yöntem yeni bir olay işleyicisi ekler <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="84f39-108">A code-behind file implements an event handler method and then adds that method as a new event handler on the <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="84f39-109">C# Örnekte `+=` bir olaya bir işleyici atamak için işleç.</span><span class="sxs-lookup"><span data-stu-id="84f39-109">The C# example uses the `+=` operator to assign a handler to an event.</span></span> <span data-ttu-id="84f39-110">Bu işleyici atamak için kullanılan, aynı işlecidir [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] olay işleme modeli.</span><span class="sxs-lookup"><span data-stu-id="84f39-110">This is the same operator that is used to assign a handler in the [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] event handling model.</span></span> <span data-ttu-id="84f39-111">Microsoft Visual Basic, olay işleyicileri ekleme bir yol bu işleci desteklemez.</span><span class="sxs-lookup"><span data-stu-id="84f39-111">Microsoft Visual Basic does not support this operator as a means of adding event handlers.</span></span> <span data-ttu-id="84f39-112">Bunun yerine iki tekniklerden birini gerektirir:</span><span class="sxs-lookup"><span data-stu-id="84f39-112">It instead requires one of two techniques:</span></span>  
  
-   <span data-ttu-id="84f39-113">Kullanım <xref:System.Windows.UIElement.AddHandler%2A> yöntemi ile birlikte bir `AddressOf` olay işleyicisinin uygulaması başvurmak için işleci.</span><span class="sxs-lookup"><span data-stu-id="84f39-113">Use the <xref:System.Windows.UIElement.AddHandler%2A> method, together with an `AddressOf` operator, to reference the event handler implementation.</span></span>  
  
-   <span data-ttu-id="84f39-114">Kullanım `Handles` olay işleyici tanımının bir parçası olarak anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="84f39-114">Use the `Handles` keyword as part of the event handler definition.</span></span> <span data-ttu-id="84f39-115">Bu teknik burada gösterilmez; bkz: [Visual Basic ve WPF olay işleme](../../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md).</span><span class="sxs-lookup"><span data-stu-id="84f39-115">This technique is not shown here; see [Visual Basic and WPF Event Handling](../../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md).</span></span>  
  
 [!code-xaml[RoutedEventAddRemoveHandler#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
>  <span data-ttu-id="84f39-116">Olay işleyici başlangıçta ayrıştırılmış ekleme [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfası çok basittir.</span><span class="sxs-lookup"><span data-stu-id="84f39-116">Adding an event handler in the initially parsed [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page is much simpler.</span></span> <span data-ttu-id="84f39-117">Olay işleyicisi eklemek istediğiniz nesne öğesi içinde kullanmak istediğiniz olay adıyla eşleşen bir öznitelik ekleyin.</span><span class="sxs-lookup"><span data-stu-id="84f39-117">Within the object element where you want to add the event handler, add an attribute that matches the name of the event that you want to handle.</span></span> <span data-ttu-id="84f39-118">Bu özniteliğin değeri arka plan kod dosyasında tanımlanan olay işleyicisi yönteminin adı belirtmezseniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfası.</span><span class="sxs-lookup"><span data-stu-id="84f39-118">Then specify the value of that attribute as the name of the event handler method that you defined in the code-behind file of the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page.</span></span> <span data-ttu-id="84f39-119">Daha fazla bilgi için [XAML genel bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) veya [yönlendirilmiş olaylara genel bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md).</span><span class="sxs-lookup"><span data-stu-id="84f39-119">For more information, see [XAML Overview (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) or [Routed Events Overview](../../../../docs/framework/wpf/advanced/routed-events-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84f39-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84f39-120">See also</span></span>
- [<span data-ttu-id="84f39-121">Yönlendirilmiş Olaylara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="84f39-121">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
- [<span data-ttu-id="84f39-122">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="84f39-122">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)
