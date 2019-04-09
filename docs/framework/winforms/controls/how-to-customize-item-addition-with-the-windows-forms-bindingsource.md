---
title: 'Nasıl yapılır: Windows Forms BindingSource ile Öğe Eklemeyi Özelleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], creating new items
- BindingSource component [Windows Forms], customizing item addition with
- examples [Windows Forms], BindingSource component
- BindingSource component [Windows Forms], examples
ms.assetid: 1aae11fc-6fb2-4cb9-b3d0-e0638fe77ef0
ms.openlocfilehash: 0a2f8491d0f027ca834257e2ec3a08d0b8bdb7ef
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129557"
---
# <a name="how-to-customize-item-addition-with-the-windows-forms-bindingsource"></a><span data-ttu-id="b974d-102">Nasıl yapılır: Windows Forms BindingSource ile Öğe Eklemeyi Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="b974d-102">How to: Customize Item Addition with the Windows Forms BindingSource</span></span>
<span data-ttu-id="b974d-103">Kullandığınızda, bir <xref:System.Windows.Forms.BindingSource> bir Windows Forms denetimini bir veri kaynağına bağlamak için bileşen oluşturma işlemini yeni öğeleri özelleştirmek gerekli bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b974d-103">When you use a <xref:System.Windows.Forms.BindingSource> component to bind a Windows Forms control to a data source, you may find it necessary to customize the creation of new items.</span></span> <span data-ttu-id="b974d-104"><xref:System.Windows.Forms.BindingSource> Bileşeni hale getirir bu basit sağlayarak <xref:System.Windows.Forms.BindingSource.AddingNew> ilişkili denetim yeni bir öğe oluşturmak gerektiğinde genellikle oluşan olayı,.</span><span class="sxs-lookup"><span data-stu-id="b974d-104">The <xref:System.Windows.Forms.BindingSource> component makes this straightforward by providing the <xref:System.Windows.Forms.BindingSource.AddingNew> event, which is typically raised when the bound control needs to create a new item.</span></span> <span data-ttu-id="b974d-105">Hangi özel davranış (örneğin, bir Web hizmeti üzerinde bir yöntemi çağırmak veya yeni bir nesne bir sınıf üreteci almak) gerekli değildir, olay işleyicisi sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="b974d-105">Your event handler can provide whatever custom behavior is required (for example, calling a method on a Web service or getting a new object from a class factory).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b974d-106">İşleme göre bir öğe eklendiğinde <xref:System.Windows.Forms.BindingSource.AddingNew> olay eklenmesini iptal edilemez.</span><span class="sxs-lookup"><span data-stu-id="b974d-106">When an item is added by handling the <xref:System.Windows.Forms.BindingSource.AddingNew> event, the addition cannot be canceled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b974d-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="b974d-107">Example</span></span>  
 <span data-ttu-id="b974d-108">Aşağıdaki örnek nasıl bağlanacağını gösterir. bir <xref:System.Windows.Forms.DataGridView> kullanarak bir sınıf üreteci denetimine bir <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="b974d-108">The following example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a class factory by using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="b974d-109">Kullanıcı tıkladığında <xref:System.Windows.Forms.DataGridView> denetimin yeni satır <xref:System.Windows.Forms.BindingSource.AddingNew> olayı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b974d-109">When the user clicks the <xref:System.Windows.Forms.DataGridView> control's new row, the <xref:System.Windows.Forms.BindingSource.AddingNew> event is raised.</span></span> <span data-ttu-id="b974d-110">Yeni bir olay işleyicisi oluşturur `DemoCustomer` öğesine atanan nesne <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="b974d-110">The event handler creates a new `DemoCustomer` object, which is assigned to the <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="b974d-111">Bu yeni neden `DemoCustomer` eklenecek nesne <xref:System.Windows.Forms.BindingSource> bileşenin listesi ve yeni satırında görüntülenecek <xref:System.Windows.Forms.DataGridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="b974d-111">This causes the new `DemoCustomer` object to be added to the <xref:System.Windows.Forms.BindingSource> component's list and to be displayed in the new row of the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b974d-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="b974d-112">Compiling the Code</span></span>  
 <span data-ttu-id="b974d-113">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="b974d-113">This example requires:</span></span>  
  
-   <span data-ttu-id="b974d-114">Sistem, System.Data System.Drawing ve System.Windows.Forms derlemelere başvuruları.</span><span class="sxs-lookup"><span data-stu-id="b974d-114">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="b974d-115">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="b974d-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="b974d-116">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b974d-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b974d-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b974d-117">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="b974d-118">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="b974d-118">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="b974d-119">Nasıl yapılır: Windows Forms Denetimini Bir Türe Bağlama</span><span class="sxs-lookup"><span data-stu-id="b974d-119">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
