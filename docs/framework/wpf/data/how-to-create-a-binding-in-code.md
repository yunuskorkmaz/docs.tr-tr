---
title: 'Nasıl yapılır: Kod İçinde Bağlama Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], creating
- data binding [WPF], creating
ms.assetid: 1a606db9-cf5f-42ed-a1c5-9e4722ec77a0
ms.openlocfilehash: 616487a16ebbe6e23fe067fb7ce72644aa3f919f
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458849"
---
# <a name="how-to-create-a-binding-in-code"></a><span data-ttu-id="348be-102">Nasıl yapılır: Kod İçinde Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="348be-102">How to: Create a Binding in Code</span></span>
<span data-ttu-id="348be-103">Bu örnek, kodda <xref:System.Windows.Data.Binding> oluşturma ve ayarlama işlemlerinin nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="348be-103">This example shows how to create and set a <xref:System.Windows.Data.Binding> in code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="348be-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="348be-104">Example</span></span>  
 <span data-ttu-id="348be-105"><xref:System.Windows.FrameworkElement> sınıfı ve <xref:System.Windows.FrameworkContentElement> sınıfı her ikisi de bir `SetBinding` yöntemi sunar.</span><span class="sxs-lookup"><span data-stu-id="348be-105">The <xref:System.Windows.FrameworkElement> class and the <xref:System.Windows.FrameworkContentElement> class both expose a `SetBinding` method.</span></span> <span data-ttu-id="348be-106">Bu sınıflardan birini devralan bir öğe bağlıyorsanız, <xref:System.Windows.FrameworkElement.SetBinding%2A> yöntemini doğrudan çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="348be-106">If you are binding an element that inherits either of these classes, you can call the <xref:System.Windows.FrameworkElement.SetBinding%2A> method directly.</span></span>  
  
 <span data-ttu-id="348be-107">Aşağıdaki örnek, `MyDataProperty`adlı bir özelliği içeren `MyData`adlı bir sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="348be-107">The following example creates a class named, `MyData`, which contains a property named `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 <span data-ttu-id="348be-108">Aşağıdaki örnek, bağlamanın kaynağını ayarlamak için bağlama nesnesinin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="348be-108">The following example shows how to create a binding object to set the source of the binding.</span></span>  <span data-ttu-id="348be-109">Örnek, `MyDataProperty`için <xref:System.Windows.Controls.TextBlock> denetimi olan `myText`<xref:System.Windows.Controls.TextBlock.Text%2A> özelliğini bağlamak için <xref:System.Windows.FrameworkElement.SetBinding%2A> kullanır.</span><span class="sxs-lookup"><span data-stu-id="348be-109">The example uses <xref:System.Windows.FrameworkElement.SetBinding%2A> to bind the <xref:System.Windows.Controls.TextBlock.Text%2A> property of `myText`, which is a <xref:System.Windows.Controls.TextBlock> control, to `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 <span data-ttu-id="348be-110">Tam kod örneği için bkz. [yalnızca kod bağlama örneği](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="348be-110">For the complete code sample, see [Code-only Binding Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).</span></span>  
  
 <span data-ttu-id="348be-111"><xref:System.Windows.FrameworkElement.SetBinding%2A>çağırmak yerine <xref:System.Windows.Data.BindingOperations> sınıfının <xref:System.Windows.Data.BindingOperations.SetBinding%2A> static yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="348be-111">Instead of calling <xref:System.Windows.FrameworkElement.SetBinding%2A>, you can use the <xref:System.Windows.Data.BindingOperations.SetBinding%2A> static method of the <xref:System.Windows.Data.BindingOperations> class.</span></span> <span data-ttu-id="348be-112">Aşağıdaki örnek, `myText` `myDataProperty`bağlamak için <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> yerine <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> çağırır.</span><span class="sxs-lookup"><span data-stu-id="348be-112">The following example, calls <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> instead of <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> to bind `myText` to `myDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a><span data-ttu-id="348be-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="348be-113">See also</span></span>

- [<span data-ttu-id="348be-114">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="348be-114">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="348be-115">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="348be-115">How-to Topics</span></span>](data-binding-how-to-topics.md)
