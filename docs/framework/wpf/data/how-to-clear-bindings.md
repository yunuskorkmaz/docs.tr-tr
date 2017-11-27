---
title: "Nasıl yapılır: Bağlamaları Temizleme"
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
- bindings [WPF], clearing
- clearing bindings [WPF]
- data binding [WPF], clearing bindings
ms.assetid: 73962a93-32a9-4bcd-9240-bcfbb239093a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9f8e009d00960f40abcd3c3913a15fa51f1be4f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-clear-bindings"></a><span data-ttu-id="ed8b5-102">Nasıl yapılır: Bağlamaları Temizleme</span><span class="sxs-lookup"><span data-stu-id="ed8b5-102">How to: Clear Bindings</span></span>
<span data-ttu-id="ed8b5-103">Bu örnek, bir nesneden bağlamaları temizlemek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ed8b5-103">This example shows how to clear bindings from an object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed8b5-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="ed8b5-104">Example</span></span>  
 <span data-ttu-id="ed8b5-105">Bir nesne üzerinde tek bir özellikten bağlamayı temizlemek için arama <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="ed8b5-105">To clear a binding from an individual property on an object, call <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> as shown in the following example.</span></span> <span data-ttu-id="ed8b5-106">Aşağıdaki örnek bağlamayı kaldırır <xref:System.Windows.Controls.TextBlock.TextProperty> , *mytext*, <xref:System.Windows.Controls.TextBlock> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="ed8b5-106">The following example removes the binding from the <xref:System.Windows.Controls.TextBlock.TextProperty> of *mytext*, a <xref:System.Windows.Controls.TextBlock> object.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#ClearBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#clearbinding)]
 [!code-vb[CodeOnlyBinding#ClearBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#clearbinding)]  
  
 <span data-ttu-id="ed8b5-107">Bağlama temizlenirken bağımlılık özelliğinin değeri bağlama yokken olması gereken şekilde değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="ed8b5-107">Clearing the binding removes the binding so that the value of the dependency property is changed to whatever it would have been without the binding.</span></span> <span data-ttu-id="ed8b5-108">Bu değer, varsayılan değer, devralınan değerinin ya da bir veri şablonu bağlama arasında bir değer olabilir.</span><span class="sxs-lookup"><span data-stu-id="ed8b5-108">This value could be a default value, an inherited value, or a value from a data template binding.</span></span>  
  
 <span data-ttu-id="ed8b5-109">Bir nesne üzerinde tüm olası özelliklerinden bağlamaları temizlemek için kullanın <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.</span><span class="sxs-lookup"><span data-stu-id="ed8b5-109">To clear bindings from all possible properties on an object, use <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed8b5-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ed8b5-110">See Also</span></span>  
 <xref:System.Windows.Data.BindingOperations>  
 [<span data-ttu-id="ed8b5-111">Veri bağlama genel bakış</span><span class="sxs-lookup"><span data-stu-id="ed8b5-111">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="ed8b5-112">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="ed8b5-112">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
