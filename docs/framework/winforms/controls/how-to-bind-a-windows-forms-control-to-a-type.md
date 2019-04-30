---
title: 'Nasıl yapılır: Windows Forms Denetimini Bir Türe Bağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 94faeebb-d2bc-45d6-86d7-96a42661b43d
ms.openlocfilehash: f47090f5d0765833f7ac17a947691a4693d9923b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761357"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type"></a><span data-ttu-id="bad2b-102">Nasıl yapılır: Windows Forms Denetimini Bir Türe Bağlama</span><span class="sxs-lookup"><span data-stu-id="bad2b-102">How to: Bind a Windows Forms Control to a Type</span></span>
<span data-ttu-id="bad2b-103">Verilerle etkileşimde bulunmak denetimleri oluştururken, bazı durumlarda, bir nesne yerine bir tür bir denetimin bağlanması gerekli bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="bad2b-103">When you are building controls that interact with data, you will sometimes find it necessary to bind a control to a type, rather than an object.</span></span> <span data-ttu-id="bad2b-104">Bu durum, ne zaman veri kullanılamıyor olabilir, ancak bir türün ortak arabirim bilgilerini görüntülemek, verilere bağlı denetimler hala gerekir özellikle, tasarım zamanında ortaya çıkar.</span><span class="sxs-lookup"><span data-stu-id="bad2b-104">This situation arises especially at design time, when data may not be available, but your data-bound controls still need to display information from a type's public interface.</span></span> <span data-ttu-id="bad2b-105">Örneğin, bağlama bir <xref:System.Windows.Forms.DataGridView> denetlemek için bir Web hizmeti tarafından kullanıma sunulan bir nesne ve istediğiniz <xref:System.Windows.Forms.DataGridView> sütunlarını tasarım zamanında bir özel tür adlarını üyesiyle etiket denetimi.</span><span class="sxs-lookup"><span data-stu-id="bad2b-105">For example, you may bind a <xref:System.Windows.Forms.DataGridView> control to an object exposed by a Web service and want the <xref:System.Windows.Forms.DataGridView> control to label its columns at design time with the member names of a custom type.</span></span>  
  
 <span data-ttu-id="bad2b-106">Bir denetim türü ile kolayca bağlayabilirsiniz <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="bad2b-106">You can easily bind a control to a type with the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bad2b-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="bad2b-107">Example</span></span>  
 <span data-ttu-id="bad2b-108">Aşağıdaki kod örneğinde nasıl bağlanacağını gösterir. bir <xref:System.Windows.Forms.DataGridView> kullanarak özel bir tür denetimi bir <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="bad2b-108">The following code example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a custom type by using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="bad2b-109">Örneği çalıştırdığınızda, fark edeceksiniz <xref:System.Windows.Forms.DataGridView> özelliklerini yansıtan sütunları etiketli bir `Customer` nesne önce denetimin verilerle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="bad2b-109">When you run the example, you'll notice the <xref:System.Windows.Forms.DataGridView> has labeled columns that reflect the properties of a `Customer` object, before the control is populated with data.</span></span> <span data-ttu-id="bad2b-110">Örnek verileri eklemek için bir müşteri Ekle düğmesine sahip <xref:System.Windows.Forms.DataGridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="bad2b-110">The example has an Add Customer button to add data to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="bad2b-111">Düğmeye tıkladığınızda yeni bir `Customer` eklenir <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="bad2b-111">When you click the button, a new `Customer` object is added to the <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="bad2b-112">Gerçek hayattaki bir senaryoda, verileri bir Web hizmeti veya başka bir veri kaynağı için bir çağrı tarafından alınabilir.</span><span class="sxs-lookup"><span data-stu-id="bad2b-112">In a real-world scenario, the data might be obtained by a call to a Web service or other data source.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnector.BindingToType#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindingToType#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bad2b-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="bad2b-113">Compiling the Code</span></span>  
 <span data-ttu-id="bad2b-114">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="bad2b-114">This example requires:</span></span>  
  
- <span data-ttu-id="bad2b-115">Sistem ve System.Windows.Forms öğelerini derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="bad2b-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="bad2b-116">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="bad2b-116">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="bad2b-117">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bad2b-117">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bad2b-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bad2b-118">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="bad2b-119">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="bad2b-119">BindingSource Component</span></span>](bindingsource-component.md)
