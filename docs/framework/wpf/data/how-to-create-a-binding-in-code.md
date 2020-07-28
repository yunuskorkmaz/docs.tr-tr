---
title: 'Nasıl yapılır: Kod İçinde Bağlama Oluşturma'
description: Doğrudan SetBinding metodunu çağırarak Windows Presentation Foundation uygulamasında kodda bağlama oluşturmayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], creating
- data binding [WPF], creating
ms.assetid: 1a606db9-cf5f-42ed-a1c5-9e4722ec77a0
ms.openlocfilehash: aa2a29f4c1262d8ac54641b856c297b284b23a38
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165810"
---
# <a name="how-to-create-a-binding-in-code"></a><span data-ttu-id="aa3c2-103">Nasıl yapılır: Kod İçinde Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="aa3c2-103">How to: Create a Binding in Code</span></span>
<span data-ttu-id="aa3c2-104">Bu örnek, bir kod içinde oluşturma ve ayarlama işlemlerinin nasıl yapılacağını gösterir <xref:System.Windows.Data.Binding> .</span><span class="sxs-lookup"><span data-stu-id="aa3c2-104">This example shows how to create and set a <xref:System.Windows.Data.Binding> in code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa3c2-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="aa3c2-105">Example</span></span>  
 <span data-ttu-id="aa3c2-106"><xref:System.Windows.FrameworkElement>Sınıfı ve <xref:System.Windows.FrameworkContentElement> sınıfı her ikisi de bir yöntemi kullanıma sunar `SetBinding` .</span><span class="sxs-lookup"><span data-stu-id="aa3c2-106">The <xref:System.Windows.FrameworkElement> class and the <xref:System.Windows.FrameworkContentElement> class both expose a `SetBinding` method.</span></span> <span data-ttu-id="aa3c2-107">Bu sınıflardan birini devralan bir öğe bağlıyorsanız, <xref:System.Windows.FrameworkElement.SetBinding%2A> yöntemi doğrudan çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aa3c2-107">If you are binding an element that inherits either of these classes, you can call the <xref:System.Windows.FrameworkElement.SetBinding%2A> method directly.</span></span>  
  
 <span data-ttu-id="aa3c2-108">Aşağıdaki örnek adında bir özelliği içeren adlı bir sınıf oluşturur `MyData` `MyDataProperty` .</span><span class="sxs-lookup"><span data-stu-id="aa3c2-108">The following example creates a class named, `MyData`, which contains a property named `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 <span data-ttu-id="aa3c2-109">Aşağıdaki örnek, bağlamanın kaynağını ayarlamak için bağlama nesnesinin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="aa3c2-109">The following example shows how to create a binding object to set the source of the binding.</span></span>  <span data-ttu-id="aa3c2-110">Örneği, <xref:System.Windows.FrameworkElement.SetBinding%2A> <xref:System.Windows.Controls.TextBlock.Text%2A> `myText` ' a bir denetim olan özelliğini bağlamak için kullanır <xref:System.Windows.Controls.TextBlock> `MyDataProperty` .</span><span class="sxs-lookup"><span data-stu-id="aa3c2-110">The example uses <xref:System.Windows.FrameworkElement.SetBinding%2A> to bind the <xref:System.Windows.Controls.TextBlock.Text%2A> property of `myText`, which is a <xref:System.Windows.Controls.TextBlock> control, to `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 <span data-ttu-id="aa3c2-111">Tam kod örneği için bkz. [yalnızca kod bağlama örneği](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="aa3c2-111">For the complete code sample, see [Code-only Binding Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).</span></span>  
  
 <span data-ttu-id="aa3c2-112">Çağırmak yerine <xref:System.Windows.FrameworkElement.SetBinding%2A> , <xref:System.Windows.Data.BindingOperations.SetBinding%2A> sınıfının statik yöntemini kullanabilirsiniz <xref:System.Windows.Data.BindingOperations> .</span><span class="sxs-lookup"><span data-stu-id="aa3c2-112">Instead of calling <xref:System.Windows.FrameworkElement.SetBinding%2A>, you can use the <xref:System.Windows.Data.BindingOperations.SetBinding%2A> static method of the <xref:System.Windows.Data.BindingOperations> class.</span></span> <span data-ttu-id="aa3c2-113">Aşağıdaki örnek, <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> bağlamak için yerine çağırır <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> `myText` `myDataProperty` .</span><span class="sxs-lookup"><span data-stu-id="aa3c2-113">The following example, calls <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> instead of <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> to bind `myText` to `myDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a><span data-ttu-id="aa3c2-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa3c2-114">See also</span></span>

- [<span data-ttu-id="aa3c2-115">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="aa3c2-115">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="aa3c2-116">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="aa3c2-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
