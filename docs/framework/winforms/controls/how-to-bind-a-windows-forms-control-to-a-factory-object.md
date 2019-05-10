---
title: 'Nasıl yapılır: Windows Forms Denetimini Bir Fabrika Nesnesine Bağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], binding
- factory objects [Windows Forms], binding to
- BindingSource component [Windows Forms], binding to a factory object
- BindingSource component [Windows Forms], examples
ms.assetid: 7d59af89-ff82-41d8-a48a-f1fbae788b0d
ms.openlocfilehash: 61ed671b48fd07559c8403b9f5761dbaee3a66ab
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64612573"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-factory-object"></a><span data-ttu-id="cb1e2-102">Nasıl yapılır: Windows Forms Denetimini Bir Fabrika Nesnesine Bağlama</span><span class="sxs-lookup"><span data-stu-id="cb1e2-102">How to: Bind a Windows Forms Control to a Factory Object</span></span>
<span data-ttu-id="cb1e2-103">Verilerle etkileşimde bulunmak denetimleri oluştururken, bazı durumlarda, bir denetim için bir nesne veya diğer nesneleri oluşturan yöntemi bağlamak gerekli bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="cb1e2-103">When you are building controls that interact with data, you will sometimes find it necessary to bind a control to an object or method that generates other objects.</span></span> <span data-ttu-id="cb1e2-104">Böyle bir nesne veya yöntem bir Fabrika adı verilir.</span><span class="sxs-lookup"><span data-stu-id="cb1e2-104">Such an object or method is called a factory.</span></span> <span data-ttu-id="cb1e2-105">Veri kaynağı, örneğin, bellek veya bir türü bir nesne yerine bir yöntem çağrısının dönüş değeri olabilir.</span><span class="sxs-lookup"><span data-stu-id="cb1e2-105">Your data source might be, for example, the return value from a method call, instead of an object in memory or a type.</span></span> <span data-ttu-id="cb1e2-106">Kaynak koleksiyonu döndürdüğü sürece bu tür bir veri kaynağı için bir denetim bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cb1e2-106">You can bind a control to this kind of data source as long as the source returns a collection.</span></span>  
  
 <span data-ttu-id="cb1e2-107">Kullanarak bir denetimi bir Fabrika nesnesine kolayca bağlayabilirsiniz <xref:System.Windows.Forms.BindingSource> denetimi.</span><span class="sxs-lookup"><span data-stu-id="cb1e2-107">You can easily bind a control to a factory object by using the <xref:System.Windows.Forms.BindingSource> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb1e2-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="cb1e2-108">Example</span></span>  
 <span data-ttu-id="cb1e2-109">Aşağıdaki örnek nasıl bağlanacağını gösterir. bir <xref:System.Windows.Forms.DataGridView> denetlemek için bir Üreteç yöntemi kullanarak bir <xref:System.Windows.Forms.BindingSource> denetimi.</span><span class="sxs-lookup"><span data-stu-id="cb1e2-109">The following example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a factory method by using a <xref:System.Windows.Forms.BindingSource> control.</span></span> <span data-ttu-id="cb1e2-110">Üreteç yöntemi adlı `GetOrdersByCustomerId`, Northwind veritabanında belirli bir müşteri için tüm siparişleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="cb1e2-110">The factory method is named `GetOrdersByCustomerId`, and it returns all the orders for a given customer in the Northwind database.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cb1e2-111">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="cb1e2-111">Compiling the Code</span></span>  
 <span data-ttu-id="cb1e2-112">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="cb1e2-112">This example requires:</span></span>  
  
- <span data-ttu-id="cb1e2-113">Sistem, System.Data System.Drawing ve System.Windows.Forms derlemelere başvuruları.</span><span class="sxs-lookup"><span data-stu-id="cb1e2-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="cb1e2-114">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="cb1e2-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="cb1e2-115">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cb1e2-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb1e2-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb1e2-116">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="cb1e2-117">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="cb1e2-117">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="cb1e2-118">Nasıl yapılır: Bir Windows Forms denetimini bir türe bağlama</span><span class="sxs-lookup"><span data-stu-id="cb1e2-118">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
