---
title: 'Nasıl yapılır: Kod Kullanarak bir Olay İşleyicisi Ekleme'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- event handlers [WPF], adding
- XAML [WPF], adding event handlers
ms.assetid: 269c61e0-6bd9-4291-9bed-1c5ee66da486
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4e7627589ff7e422c4ad3cd7a37fdc14c8a9c9f4
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-add-an-event-handler-using-code"></a><span data-ttu-id="509b7-102">Nasıl yapılır: Kod Kullanarak bir Olay İşleyicisi Ekleme</span><span class="sxs-lookup"><span data-stu-id="509b7-102">How to: Add an Event Handler Using Code</span></span>
<span data-ttu-id="509b7-103">Bu örnek kod kullanarak bir öğe olarak olay işleyicisi ekleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="509b7-103">This example shows how to add an event handler to an element by using code.</span></span>  
  
 <span data-ttu-id="509b7-104">Bir olay işleyicisi eklemek istiyorsanız bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öğesi ve öğeyi içeren biçimlendirme sayfası zaten yüklü, kod kullanarak işleyici eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="509b7-104">If you want to add an event handler to a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] element, and the markup page that contains the element has already been loaded, you must add the handler using code.</span></span> <span data-ttu-id="509b7-105">Alternatif olarak, tamamen kod kullanarak ve kullanarak herhangi bir öğeyi bildirme olmayan bir uygulama için öğe ağacı oluşturmakta olduğunuz varsa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], olay işleyicilerini yapılandırılmış öğe ağacına eklemek için belirli yöntemleri çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="509b7-105">Alternatively, if you are building up the element tree for an application entirely using code and not declaring any elements using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can call specific methods to add event handlers to the constructed element tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="509b7-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="509b7-106">Example</span></span>  
 <span data-ttu-id="509b7-107">Aşağıdaki örnek yeni bir ekler <xref:System.Windows.Controls.Button> başlangıçta tanımlanan varolan sayfasına [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="509b7-107">The following example adds a new <xref:System.Windows.Controls.Button> to an existing page that is initially defined in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="509b7-108">Bir arka plan kod dosyasına bir olay işleyicisi yöntemi uygular ve daha sonra bu yöntem yeni bir olay işleyicisi ekler <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="509b7-108">A code-behind file implements an event handler method and then adds that method as a new event handler on the <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="509b7-109">C# örnek kullanır `+=` bir olay için bir işleyici atamak için işleci.</span><span class="sxs-lookup"><span data-stu-id="509b7-109">The C# example uses the `+=` operator to assign a handler to an event.</span></span> <span data-ttu-id="509b7-110">Bu işleyici atamak için kullanılan, aynı işlecidir [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] olay işleme modeli.</span><span class="sxs-lookup"><span data-stu-id="509b7-110">This is the same operator that is used to assign a handler in the [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] event handling model.</span></span> <span data-ttu-id="509b7-111">Microsoft Visual Basic bu işleci olay işleyicileri ekleme bir araç olarak desteklemez.</span><span class="sxs-lookup"><span data-stu-id="509b7-111">Microsoft Visual Basic does not support this operator as a means of adding event handlers.</span></span> <span data-ttu-id="509b7-112">Bunun yerine iki teknikleri birini gerektirir:</span><span class="sxs-lookup"><span data-stu-id="509b7-112">It instead requires one of two techniques:</span></span>  
  
-   <span data-ttu-id="509b7-113">Kullanım <xref:System.Windows.UIElement.AddHandler%2A> yöntemi ile birlikte bir `AddressOf` olay işleyicisi uygulamasına başvurmak için işleci.</span><span class="sxs-lookup"><span data-stu-id="509b7-113">Use the <xref:System.Windows.UIElement.AddHandler%2A> method, together with an `AddressOf` operator, to reference the event handler implementation.</span></span>  
  
-   <span data-ttu-id="509b7-114">Kullanım `Handles` anahtar sözcüğü olay işleyici tanımının bir parçası olarak.</span><span class="sxs-lookup"><span data-stu-id="509b7-114">Use the `Handles` keyword as part of the event handler definition.</span></span> <span data-ttu-id="509b7-115">Bu teknik burada gösterilmiyor; bkz: [Visual Basic ve WPF olay işleme](../../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md).</span><span class="sxs-lookup"><span data-stu-id="509b7-115">This technique is not shown here; see [Visual Basic and WPF Event Handling](../../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md).</span></span>  
  
 [!code-xaml[RoutedEventAddRemoveHandler#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
>  <span data-ttu-id="509b7-116">Olay işleyici başlangıçta ayrıştırılmış ekleme [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfasıdır çok daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="509b7-116">Adding an event handler in the initially parsed [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page is much simpler.</span></span> <span data-ttu-id="509b7-117">Olay işleyicisi eklemek istediğiniz nesne öğesi içinde ele almak istediğiniz olay adıyla eşleşen bir öznitelik ekleyin.</span><span class="sxs-lookup"><span data-stu-id="509b7-117">Within the object element where you want to add the event handler, add an attribute that matches the name of the event that you want to handle.</span></span> <span data-ttu-id="509b7-118">Arka plan kodu dosyasında tanımlanan olay işleyicisi yönteminin adı olarak bu özniteliğin değerini belirtin [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfası.</span><span class="sxs-lookup"><span data-stu-id="509b7-118">Then specify the value of that attribute as the name of the event handler method that you defined in the code-behind file of the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page.</span></span> <span data-ttu-id="509b7-119">Daha fazla bilgi için bkz: [XAML genel bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) veya [yönlendirilmiş olaylara genel bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md).</span><span class="sxs-lookup"><span data-stu-id="509b7-119">For more information, see [XAML Overview (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) or [Routed Events Overview](../../../../docs/framework/wpf/advanced/routed-events-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="509b7-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="509b7-120">See Also</span></span>  
 [<span data-ttu-id="509b7-121">Yönlendirilmiş Olaylara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="509b7-121">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [<span data-ttu-id="509b7-122">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="509b7-122">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)
