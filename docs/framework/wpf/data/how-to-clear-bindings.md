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
ms.workload: dotnet
ms.openlocfilehash: af45d504eb4e7d45808f787925a90c8e0ed19476
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-clear-bindings"></a><span data-ttu-id="00549-102">Nasıl yapılır: Bağlamaları Temizleme</span><span class="sxs-lookup"><span data-stu-id="00549-102">How to: Clear Bindings</span></span>
<span data-ttu-id="00549-103">Bu örnek, bir nesneden bağlamaları temizlemek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="00549-103">This example shows how to clear bindings from an object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00549-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="00549-104">Example</span></span>  
 <span data-ttu-id="00549-105">Bir nesne üzerinde tek bir özellikten bağlamayı temizlemek için arama <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="00549-105">To clear a binding from an individual property on an object, call <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> as shown in the following example.</span></span> <span data-ttu-id="00549-106">Aşağıdaki örnek bağlamayı kaldırır <xref:System.Windows.Controls.TextBlock.TextProperty> , *mytext*, <xref:System.Windows.Controls.TextBlock> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="00549-106">The following example removes the binding from the <xref:System.Windows.Controls.TextBlock.TextProperty> of *mytext*, a <xref:System.Windows.Controls.TextBlock> object.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#ClearBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#clearbinding)]
 [!code-vb[CodeOnlyBinding#ClearBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#clearbinding)]  
  
 <span data-ttu-id="00549-107">Bağlama temizlenirken bağımlılık özelliğinin değeri bağlama yokken olması gereken şekilde değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="00549-107">Clearing the binding removes the binding so that the value of the dependency property is changed to whatever it would have been without the binding.</span></span> <span data-ttu-id="00549-108">Bu değer, varsayılan değer, devralınan değerinin ya da bir veri şablonu bağlama arasında bir değer olabilir.</span><span class="sxs-lookup"><span data-stu-id="00549-108">This value could be a default value, an inherited value, or a value from a data template binding.</span></span>  
  
 <span data-ttu-id="00549-109">Bir nesne üzerinde tüm olası özelliklerinden bağlamaları temizlemek için kullanın <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.</span><span class="sxs-lookup"><span data-stu-id="00549-109">To clear bindings from all possible properties on an object, use <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00549-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="00549-110">See Also</span></span>  
 <xref:System.Windows.Data.BindingOperations>  
 [<span data-ttu-id="00549-111">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="00549-111">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="00549-112">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="00549-112">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
