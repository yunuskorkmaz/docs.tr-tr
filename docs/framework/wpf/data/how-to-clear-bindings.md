---
title: 'Nasıl yapılır: Bağlamaları Temizleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bindings [WPF], clearing
- clearing bindings [WPF]
- data binding [WPF], clearing bindings
ms.assetid: 73962a93-32a9-4bcd-9240-bcfbb239093a
ms.openlocfilehash: bd0f42b868c316cb9a6344134d4aaf01930519ac
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54508438"
---
# <a name="how-to-clear-bindings"></a><span data-ttu-id="a569c-102">Nasıl yapılır: Bağlamaları Temizleme</span><span class="sxs-lookup"><span data-stu-id="a569c-102">How to: Clear Bindings</span></span>
<span data-ttu-id="a569c-103">Bu örnek, bir nesneden bağlamaları temizlemek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a569c-103">This example shows how to clear bindings from an object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a569c-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="a569c-104">Example</span></span>  
 <span data-ttu-id="a569c-105">Bir nesne üzerinde tek bir özellikten bağlamayı temizlemek için arama <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="a569c-105">To clear a binding from an individual property on an object, call <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> as shown in the following example.</span></span> <span data-ttu-id="a569c-106">Aşağıdaki örnek bağlamayı kaldırır <xref:System.Windows.Controls.TextBlock.TextProperty> , *Metnim*, <xref:System.Windows.Controls.TextBlock> nesne.</span><span class="sxs-lookup"><span data-stu-id="a569c-106">The following example removes the binding from the <xref:System.Windows.Controls.TextBlock.TextProperty> of *mytext*, a <xref:System.Windows.Controls.TextBlock> object.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#ClearBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#clearbinding)]
 [!code-vb[CodeOnlyBinding#ClearBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#clearbinding)]  
  
 <span data-ttu-id="a569c-107">Bağlama temizlenirken bağımlılık özelliğinin değeri, bağlama olmadan olması gereken şekilde değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="a569c-107">Clearing the binding removes the binding so that the value of the dependency property is changed to whatever it would have been without the binding.</span></span> <span data-ttu-id="a569c-108">Bu değer, varsayılan değer, devralınan bir değer veya bir veri şablon bağlamayı arasında bir değer olabilir.</span><span class="sxs-lookup"><span data-stu-id="a569c-108">This value could be a default value, an inherited value, or a value from a data template binding.</span></span>  
  
 <span data-ttu-id="a569c-109">Bir nesne üzerinde olası tüm özelliklerinden bağlamaları temizlemek için kullanın <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.</span><span class="sxs-lookup"><span data-stu-id="a569c-109">To clear bindings from all possible properties on an object, use <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a569c-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a569c-110">See also</span></span>
- <xref:System.Windows.Data.BindingOperations>
- [<span data-ttu-id="a569c-111">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a569c-111">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [<span data-ttu-id="a569c-112">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="a569c-112">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
