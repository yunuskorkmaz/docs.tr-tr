---
title: "Nasıl yapılır: Gönderilmiş bir Olay için Sınıf İşleme Ekleme"
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
- routed events [WPF], class handlers
- task_core_add_class_handling_routed_properties [WPF]
- class handlers [WPF], routed events
ms.assetid: 15b7b06c-9112-4ee5-b30a-65d10c5c5df6
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1f0315bbd1d1a5ab2ae08d8bc1810e240cb6a5a7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-class-handling-for-a-routed-event"></a><span data-ttu-id="0b891-102">Nasıl yapılır: Gönderilmiş bir Olay için Sınıf İşleme Ekleme</span><span class="sxs-lookup"><span data-stu-id="0b891-102">How to: Add Class Handling for a Routed Event</span></span>
<span data-ttu-id="0b891-103">Yönlendirilmiş olaylar, sınıf veya örnek işleyicileri verilen herhangi bir düğümde rotadaki tarafından işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="0b891-103">Routed events can be handled either by class handlers or instance handlers on any given node in the route.</span></span> <span data-ttu-id="0b891-104">Sınıf işleyicileri önce çağrılır ve olayların örnek işlemesini bastırmak veya diğer olaya özgü davranışlar temel sınıflar tarafından sahip olunan olaylarına tanıtmak için sınıf uygulamaları tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0b891-104">Class handlers are invoked first, and can be used by class implementations to suppress events from instance handling or introduce other event specific behaviors on events that are owned by base classes.</span></span> <span data-ttu-id="0b891-105">Bu örnek sınıf işleyicileri uygulamak için iki yakından ilgili teknik gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0b891-105">This example illustrates two closely related techniques for implementing class handlers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b891-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="0b891-106">Example</span></span>  
 <span data-ttu-id="0b891-107">Bu örnek dayalı özel bir sınıf kullanır <xref:System.Windows.Controls.Canvas> paneli.</span><span class="sxs-lookup"><span data-stu-id="0b891-107">This example uses a custom class based on the <xref:System.Windows.Controls.Canvas> panel.</span></span> <span data-ttu-id="0b891-108">Uygulama özel bir sınıf herhangi bir sol fare düğmesini tıklattığında kesintiye uğratan ve alt öğe sınıfı veya herhangi bir örnek işleyicileri çağrılacak önce bunları ele işaretleme dahil olmak üzere, kendi alt öğeleri üzerinde davranışlar tanıtır dayanır.</span><span class="sxs-lookup"><span data-stu-id="0b891-108">The basic premise of the application is that the custom class introduces behaviors on its child elements, including intercepting any left mouse button clicks and marking them handled, before the child element class or any instance handlers on it will be invoked.</span></span>  
  
 <span data-ttu-id="0b891-109"><xref:System.Windows.UIElement> Sınıfı sınıf üzerinde işlemesini sağlayan sanal bir yöntem sunar <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> olay yalnızca kılarak olay.</span><span class="sxs-lookup"><span data-stu-id="0b891-109">The <xref:System.Windows.UIElement> class exposes a virtual method that enables class handling on the <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> event, by simply overriding the event.</span></span> <span data-ttu-id="0b891-110">Sanal bir yöntem herhangi bir yerde, sınıf hiyerarşisinde kullanılabilir durumdaysa sınıf işleme uygulamak için en basit yolu budur.</span><span class="sxs-lookup"><span data-stu-id="0b891-110">This is the simplest way to implement class handling if such a virtual method is available somewhere in your class' hierarchy.</span></span> <span data-ttu-id="0b891-111">Aşağıdaki kodda gösterildiği <xref:System.Windows.UIElement.OnPreviewMouseLeftButtonDown%2A> "türetildiği MyEditContainer" uygulamasında <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="0b891-111">The following code shows the <xref:System.Windows.UIElement.OnPreviewMouseLeftButtonDown%2A> implementation in the "MyEditContainer" that is derived from <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="0b891-112">Uygulama olay değişkenlerinde işlenmiş olarak işaretler ve temel görünür bir değişikliğe source öğesi vermek için bazı kod ekler.</span><span class="sxs-lookup"><span data-stu-id="0b891-112">The implementation marks the event as handled in the arguments, and then adds some code to give the source element a basic visible change.</span></span>  
  
 [!code-csharp[ClassHandling#OnStarClassHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#onstarclasshandler)]
 [!code-vb[ClassHandling#OnStarClassHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#onstarclasshandler)]  
  
 <span data-ttu-id="0b891-113">Sanal Taban sınıflar veya bu belirli yöntem için kullanılabilir ise, sınıf işleme yardımcı yöntemi kullanarak doğrudan eklenebilir <xref:System.Windows.EventManager> sınıfı, <xref:System.Windows.EventManager.RegisterClassHandler%2A>.</span><span class="sxs-lookup"><span data-stu-id="0b891-113">If no virtual is available on base classes or for that particular method, class handling can be added directly using a utility method of the <xref:System.Windows.EventManager> class, <xref:System.Windows.EventManager.RegisterClassHandler%2A>.</span></span> <span data-ttu-id="0b891-114">Bu yöntem yalnızca statik sınıf işleme ekleme sınıfları başlatma içinde çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0b891-114">This method should only be called within the static initialization of classes that are adding class handling.</span></span> <span data-ttu-id="0b891-115">Bu örnek için başka bir işleyici ekler <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> , ve bu durumda kayıtlı sınıf özel bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="0b891-115">This example adds another handler for <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> , and in this case the registered class is the custom class.</span></span> <span data-ttu-id="0b891-116">Buna karşılık, sanalların, kayıtlı sınıf gerçekten kullanıldığında <xref:System.Windows.UIElement> temel sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0b891-116">In contrast, when using the virtuals, the registered class is really the <xref:System.Windows.UIElement> base class.</span></span> <span data-ttu-id="0b891-117">Burada temel sınıflar ve alt sınıfların her sınıf işleme kaydettiği durumlarda alt sınıf işleyicileri önce çağrılır.</span><span class="sxs-lookup"><span data-stu-id="0b891-117">In cases where base classes and subclass each register class handling, the subclass handlers are invoked first.</span></span> <span data-ttu-id="0b891-118">Bir uygulamanın davranışı, bu işleyici, ileti kutusu ilk gösterir ve daha sonra sanal yöntemin işleyicisi görsel değişiklikleri gösterilen olacaktır.</span><span class="sxs-lookup"><span data-stu-id="0b891-118">The behavior in an application would be that first this handler would show its message box and then the visual change in the virtual method's handler would be shown.</span></span>  
  
 [!code-csharp[ClassHandling#StaticAndRegisterClassHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#staticandregisterclasshandler)]
 [!code-vb[ClassHandling#StaticAndRegisterClassHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#staticandregisterclasshandler)]  
  
## <a name="see-also"></a><span data-ttu-id="0b891-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0b891-119">See Also</span></span>  
 <xref:System.Windows.EventManager>  
 [<span data-ttu-id="0b891-120">Yönlendirilmiş Olayları İşlenmiş Olarak İşaretleme ve Sınıf İşlemesi</span><span class="sxs-lookup"><span data-stu-id="0b891-120">Marking Routed Events as Handled, and Class Handling</span></span>](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)  
 [<span data-ttu-id="0b891-121">Yönlendirilmiş Olayı İşleme</span><span class="sxs-lookup"><span data-stu-id="0b891-121">Handle a Routed Event</span></span>](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md)  
 [<span data-ttu-id="0b891-122">Yönlendirilmiş Olaylara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0b891-122">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
