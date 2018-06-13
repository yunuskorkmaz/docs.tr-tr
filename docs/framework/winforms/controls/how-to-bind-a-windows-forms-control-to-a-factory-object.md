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
ms.openlocfilehash: c796071f42f58d12c60031777afa9260142424d4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530126"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-factory-object"></a><span data-ttu-id="bc766-102">Nasıl yapılır: Windows Forms Denetimini Bir Fabrika Nesnesine Bağlama</span><span class="sxs-lookup"><span data-stu-id="bc766-102">How to: Bind a Windows Forms Control to a Factory Object</span></span>
<span data-ttu-id="bc766-103">Verilerle etkileşimli denetimleri oluştururken, bazen, bir denetim için bir nesne veya diğer nesnelerini oluşturan yöntem bağlamak gerekli bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="bc766-103">When you are building controls that interact with data, you will sometimes find it necessary to bind a control to an object or method that generates other objects.</span></span> <span data-ttu-id="bc766-104">Bu tür bir nesneye veya yöntemi bir Fabrika adı verilir.</span><span class="sxs-lookup"><span data-stu-id="bc766-104">Such an object or method is called a factory.</span></span> <span data-ttu-id="bc766-105">Veri kaynağı, örneğin, bellek veya bir türü bir nesne yerine bir yöntem çağrısının dönüş değerini olabilir.</span><span class="sxs-lookup"><span data-stu-id="bc766-105">Your data source might be, for example, the return value from a method call, instead of an object in memory or a type.</span></span> <span data-ttu-id="bc766-106">Kaynak bir koleksiyon döndürür sürece bu türdeki veri kaynağının bir denetim bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc766-106">You can bind a control to this kind of data source as long as the source returns a collection.</span></span>  
  
 <span data-ttu-id="bc766-107">Kullanarak bir denetimi Fabrika nesnesine kolayca bağlayabilirsiniz <xref:System.Windows.Forms.BindingSource> denetim.</span><span class="sxs-lookup"><span data-stu-id="bc766-107">You can easily bind a control to a factory object by using the <xref:System.Windows.Forms.BindingSource> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc766-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="bc766-108">Example</span></span>  
 <span data-ttu-id="bc766-109">Aşağıdaki örnekte nasıl bağlanacağını gösterir bir <xref:System.Windows.Forms.DataGridView> kullanarak bir Üreteç yöntemi denetimine bir <xref:System.Windows.Forms.BindingSource> denetim.</span><span class="sxs-lookup"><span data-stu-id="bc766-109">The following example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a factory method by using a <xref:System.Windows.Forms.BindingSource> control.</span></span> <span data-ttu-id="bc766-110">Üreteç yöntemi adlı `GetOrdersByCustomerId`, ve belirli bir müşteri için tüm siparişleri Northwind veritabanına döndürür.</span><span class="sxs-lookup"><span data-stu-id="bc766-110">The factory method is named `GetOrdersByCustomerId`, and it returns all the orders for a given customer in the Northwind database.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.BindToFactory#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.BindToFactory#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindToFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bc766-111">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="bc766-111">Compiling the Code</span></span>  
 <span data-ttu-id="bc766-112">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="bc766-112">This example requires:</span></span>  
  
-   <span data-ttu-id="bc766-113">Sistem, System.Data, System.Drawing ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="bc766-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="bc766-114">Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="bc766-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="bc766-115">Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc766-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="bc766-116">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="bc766-116">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc766-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bc766-117">See Also</span></span>  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="bc766-118">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="bc766-118">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="bc766-119">Nasıl yapılır: Windows Forms Denetimini Bir Türe Bağlama</span><span class="sxs-lookup"><span data-stu-id="bc766-119">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
