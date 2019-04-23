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
ms.openlocfilehash: 57ec845c5c9a5bddb801428b9ecde035a97cf447
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089269"
---
# <a name="how-to-create-a-binding-in-code"></a><span data-ttu-id="478af-102">Nasıl yapılır: Kod İçinde Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="478af-102">How to: Create a Binding in Code</span></span>
<span data-ttu-id="478af-103">Bu örnekte, oluşturma ve ayarlama işlemi gösterilmektedir bir <xref:System.Windows.Data.Binding> kod.</span><span class="sxs-lookup"><span data-stu-id="478af-103">This example shows how to create and set a <xref:System.Windows.Data.Binding> in code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="478af-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="478af-104">Example</span></span>  
 <span data-ttu-id="478af-105"><xref:System.Windows.FrameworkElement> Sınıfı ve <xref:System.Windows.FrameworkContentElement> hem de kullanıma sınıfı bir `SetBinding` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="478af-105">The <xref:System.Windows.FrameworkElement> class and the <xref:System.Windows.FrameworkContentElement> class both expose a `SetBinding` method.</span></span> <span data-ttu-id="478af-106">Bu sınıfların ya da devralan bir öğe bağlanıyorsanız, çağırabilirsiniz <xref:System.Windows.FrameworkElement.SetBinding%2A> doğrudan yöntemi.</span><span class="sxs-lookup"><span data-stu-id="478af-106">If you are binding an element that inherits either of these classes, you can call the <xref:System.Windows.FrameworkElement.SetBinding%2A> method directly.</span></span>  
  
 <span data-ttu-id="478af-107">Aşağıdaki örnekte adlı bir sınıf oluşturur `MyData`, adlı bir özellik içeren `MyDataProperty`.</span><span class="sxs-lookup"><span data-stu-id="478af-107">The following example creates a class named, `MyData`, which contains a property named `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 <span data-ttu-id="478af-108">Aşağıdaki örnek, bağlama kaynağı ayarlamak için bir bağlama nesnesi oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="478af-108">The following example shows how to create a binding object to set the source of the binding.</span></span>  <span data-ttu-id="478af-109">Örnekte <xref:System.Windows.FrameworkElement.SetBinding%2A> bağlamak için <xref:System.Windows.Controls.TextBlock.Text%2A> özelliği `myText`, olduğu bir <xref:System.Windows.Controls.TextBlock> çok denetimi `MyDataProperty`.</span><span class="sxs-lookup"><span data-stu-id="478af-109">The example uses <xref:System.Windows.FrameworkElement.SetBinding%2A> to bind the <xref:System.Windows.Controls.TextBlock.Text%2A> property of `myText`, which is a <xref:System.Windows.Controls.TextBlock> control, to `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 <span data-ttu-id="478af-110">Tam kod örneği için bkz. [yalnızca kod bağlama örnek](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="478af-110">For the complete code sample, see [Code-only Binding Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).</span></span>  
  
 <span data-ttu-id="478af-111">Çağırmak yerine <xref:System.Windows.FrameworkElement.SetBinding%2A>, kullanabileceğiniz <xref:System.Windows.Data.BindingOperations.SetBinding%2A> statik yöntemi <xref:System.Windows.Data.BindingOperations> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="478af-111">Instead of calling <xref:System.Windows.FrameworkElement.SetBinding%2A>, you can use the <xref:System.Windows.Data.BindingOperations.SetBinding%2A> static method of the <xref:System.Windows.Data.BindingOperations> class.</span></span> <span data-ttu-id="478af-112">Aşağıdaki örnek, çağrıları <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> yerine <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> bağlamak için `myText` için `myDataProperty`.</span><span class="sxs-lookup"><span data-stu-id="478af-112">The following example, calls <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> instead of <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> to bind `myText` to `myDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a><span data-ttu-id="478af-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="478af-113">See also</span></span>

- [<span data-ttu-id="478af-114">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="478af-114">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="478af-115">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="478af-115">How-to Topics</span></span>](data-binding-how-to-topics.md)
