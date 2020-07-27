---
title: 'Nasıl yapılır: Kod Kullanarak bir Olay İşleyicisi Ekleme'
description: Bu örneği, XAML kullanarak bildirmek yerine kodu kullanarak Windows Presentation Foundation bir öğeye olay işleyicisi ekleme hakkında bilgi almak için kullanın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- event handlers [WPF], adding
- XAML [WPF], adding event handlers
ms.assetid: 269c61e0-6bd9-4291-9bed-1c5ee66da486
ms.openlocfilehash: b36969f7a65ccbf6c9d03b22767d9eacdc177ad1
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166372"
---
# <a name="how-to-add-an-event-handler-using-code"></a><span data-ttu-id="cbd9c-103">Nasıl yapılır: Kod Kullanarak bir Olay İşleyicisi Ekleme</span><span class="sxs-lookup"><span data-stu-id="cbd9c-103">How to: Add an Event Handler Using Code</span></span>
<span data-ttu-id="cbd9c-104">Bu örnek, kod kullanarak bir öğeye bir olay işleyicisinin nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="cbd9c-104">This example shows how to add an event handler to an element by using code.</span></span>  
  
 <span data-ttu-id="cbd9c-105">Bir öğeye bir olay işleyicisi eklemek istiyorsanız [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve öğesini içeren biçimlendirme sayfası zaten yüklüyse, kodu kullanarak işleyiciyi eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="cbd9c-105">If you want to add an event handler to a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] element, and the markup page that contains the element has already been loaded, you must add the handler using code.</span></span> <span data-ttu-id="cbd9c-106">Alternatif olarak, kod kullanarak bir uygulama için öğe ağacını oluşturuyorsanız ve kullanarak herhangi bir öğe bildirmiyorsanız [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , oluşturulan öğe ağacına olay işleyicileri eklemek için belirli yöntemleri çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cbd9c-106">Alternatively, if you are building up the element tree for an application entirely using code and not declaring any elements using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can call specific methods to add event handlers to the constructed element tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbd9c-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="cbd9c-107">Example</span></span>  
 <span data-ttu-id="cbd9c-108">Aşağıdaki örnek, <xref:System.Windows.Controls.Button> içinde başlangıçta tanımlanan varolan bir sayfaya yeni bir ekler [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="cbd9c-108">The following example adds a new <xref:System.Windows.Controls.Button> to an existing page that is initially defined in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="cbd9c-109">Arka plan kod dosyası bir olay işleyicisi yöntemi uygular ve sonra bu yöntemi ' de yeni bir olay işleyicisi olarak ekler <xref:System.Windows.Controls.Button> .</span><span class="sxs-lookup"><span data-stu-id="cbd9c-109">A code-behind file implements an event handler method and then adds that method as a new event handler on the <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="cbd9c-110">C# örneği bir `+=` olaya işleyici atamak için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="cbd9c-110">The C# example uses the `+=` operator to assign a handler to an event.</span></span> <span data-ttu-id="cbd9c-111">Bu, ortak dil çalışma zamanı (CLR) olay işleme modelinde bir işleyici atamak için kullanılan işleçtir.</span><span class="sxs-lookup"><span data-stu-id="cbd9c-111">This is the same operator that is used to assign a handler in the common language runtime (CLR) event handling model.</span></span> <span data-ttu-id="cbd9c-112">Microsoft Visual Basic, olay işleyicilerini ekleme yöntemi olarak bu işleci desteklemez.</span><span class="sxs-lookup"><span data-stu-id="cbd9c-112">Microsoft Visual Basic does not support this operator as a means of adding event handlers.</span></span> <span data-ttu-id="cbd9c-113">Bunun yerine iki teknikten birini gerektirir:</span><span class="sxs-lookup"><span data-stu-id="cbd9c-113">It instead requires one of two techniques:</span></span>  
  
- <span data-ttu-id="cbd9c-114"><xref:System.Windows.UIElement.AddHandler%2A> `AddressOf` Olay işleyicisi uygulamasına başvurmak için yöntemini bir işleçle birlikte kullanın.</span><span class="sxs-lookup"><span data-stu-id="cbd9c-114">Use the <xref:System.Windows.UIElement.AddHandler%2A> method, together with an `AddressOf` operator, to reference the event handler implementation.</span></span>  
  
- <span data-ttu-id="cbd9c-115">`Handles`Anahtar sözcüğünü olay işleyicisi tanımının bir parçası olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="cbd9c-115">Use the `Handles` keyword as part of the event handler definition.</span></span> <span data-ttu-id="cbd9c-116">Bu teknik burada gösterilmez; bkz. [Visual Basic ve WPF olay işleme](visual-basic-and-wpf-event-handling.md).</span><span class="sxs-lookup"><span data-stu-id="cbd9c-116">This technique is not shown here; see [Visual Basic and WPF Event Handling](visual-basic-and-wpf-event-handling.md).</span></span>  
  
 [!code-xaml[RoutedEventAddRemoveHandler#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
> <span data-ttu-id="cbd9c-117">İlk ayrıştırılmış sayfada bir olay işleyicisi eklemek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] çok basittir.</span><span class="sxs-lookup"><span data-stu-id="cbd9c-117">Adding an event handler in the initially parsed [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page is much simpler.</span></span> <span data-ttu-id="cbd9c-118">Olay işleyicisini eklemek istediğiniz nesne öğesi içinde, işlemek istediğiniz olayın adıyla eşleşen bir öznitelik ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cbd9c-118">Within the object element where you want to add the event handler, add an attribute that matches the name of the event that you want to handle.</span></span> <span data-ttu-id="cbd9c-119">Sonra bu özniteliğin değerini, sayfanın arka plan kod dosyasında tanımladığınız olay işleyicisi yönteminin adı olarak belirtin [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="cbd9c-119">Then specify the value of that attribute as the name of the event handler method that you defined in the code-behind file of the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page.</span></span> <span data-ttu-id="cbd9c-120">Daha fazla bilgi için bkz. [xaml 'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md) veya [yönlendirilmiş olaylara genel bakış](routed-events-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cbd9c-120">For more information, see [XAML Overview (WPF)](../../../desktop-wpf/fundamentals/xaml.md) or [Routed Events Overview](routed-events-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbd9c-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cbd9c-121">See also</span></span>

- [<span data-ttu-id="cbd9c-122">Gönderilmiş Olaylara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cbd9c-122">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="cbd9c-123">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="cbd9c-123">How-to Topics</span></span>](events-how-to-topics.md)
