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
ms.openlocfilehash: 66f7eb0209d23660b9c7351ca793f509b2f4bb8d
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458871"
---
# <a name="how-to-clear-bindings"></a><span data-ttu-id="a3578-102">Nasıl yapılır: Bağlamaları Temizleme</span><span class="sxs-lookup"><span data-stu-id="a3578-102">How to: Clear Bindings</span></span>
<span data-ttu-id="a3578-103">Bu örnek, bir nesneden bağlamaların nasıl temizyükleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a3578-103">This example shows how to clear bindings from an object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3578-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="a3578-104">Example</span></span>  
 <span data-ttu-id="a3578-105">Bir nesne üzerindeki tek bir özellikten bağlamayı temizlemek için aşağıdaki örnekte gösterildiği gibi <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> çağırın.</span><span class="sxs-lookup"><span data-stu-id="a3578-105">To clear a binding from an individual property on an object, call <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> as shown in the following example.</span></span> <span data-ttu-id="a3578-106">Aşağıdaki örnek, bir <xref:System.Windows.Controls.TextBlock> nesnesi olan *myText*<xref:System.Windows.Controls.TextBlock.TextProperty> bağlamayı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="a3578-106">The following example removes the binding from the <xref:System.Windows.Controls.TextBlock.TextProperty> of *mytext*, a <xref:System.Windows.Controls.TextBlock> object.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#ClearBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#clearbinding)]
 [!code-vb[CodeOnlyBinding#ClearBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#clearbinding)]  
  
 <span data-ttu-id="a3578-107">Bağlamayı Temizleme, bağımlılık özelliğinin değeri bağlama olmadan olacak şekilde değiştirildikten şekilde bağlamayı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="a3578-107">Clearing the binding removes the binding so that the value of the dependency property is changed to whatever it would have been without the binding.</span></span> <span data-ttu-id="a3578-108">Bu değer bir varsayılan değer, devralınan bir değer veya bir veri şablonu bağlamasındaki bir değer olabilir.</span><span class="sxs-lookup"><span data-stu-id="a3578-108">This value could be a default value, an inherited value, or a value from a data template binding.</span></span>  
  
 <span data-ttu-id="a3578-109">Bir nesnedeki tüm olası özelliklerden bağlamaları temizlemek için <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>kullanın.</span><span class="sxs-lookup"><span data-stu-id="a3578-109">To clear bindings from all possible properties on an object, use <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3578-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3578-110">See also</span></span>

- <xref:System.Windows.Data.BindingOperations>
- [<span data-ttu-id="a3578-111">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a3578-111">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="a3578-112">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="a3578-112">How-to Topics</span></span>](data-binding-how-to-topics.md)
