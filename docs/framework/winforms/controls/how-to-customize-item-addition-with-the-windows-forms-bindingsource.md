---
title: 'Nasıl yapılır: Windows Forms BindingSource ile Öğe Eklemeyi Özelleştirme'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 400562e49b9566769f42f140f56b733954e01a0d
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-customize-item-addition-with-the-windows-forms-bindingsource"></a><span data-ttu-id="37989-102">Nasıl yapılır: Windows Forms BindingSource ile Öğe Eklemeyi Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="37989-102">How to: Customize Item Addition with the Windows Forms BindingSource</span></span>
<span data-ttu-id="37989-103">Kullandığınızda, bir <xref:System.Windows.Forms.BindingSource> bir Windows Forms denetimini bir veri kaynağına bağlama bileşeni yeni öğeler oluşturma özelleştirmek gerekli bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37989-103">When you use a <xref:System.Windows.Forms.BindingSource> component to bind a Windows Forms control to a data source, you may find it necessary to customize the creation of new items.</span></span> <span data-ttu-id="37989-104"><xref:System.Windows.Forms.BindingSource> Bileşen yapar bu basit sağlayarak <xref:System.Windows.Forms.BindingSource.AddingNew> ilişkili denetim yeni bir öğe oluşturmak gerektiğinde genellikle oluşan olayı,.</span><span class="sxs-lookup"><span data-stu-id="37989-104">The <xref:System.Windows.Forms.BindingSource> component makes this straightforward by providing the <xref:System.Windows.Forms.BindingSource.AddingNew> event, which is typically raised when the bound control needs to create a new item.</span></span> <span data-ttu-id="37989-105">Olay işleyicinizi ne olursa olsun özel davranış (örneğin, bir Web hizmeti bir yöntemi çağırma veya yeni bir nesne bir sınıf fabrikası alma) gereklidir sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="37989-105">Your event handler can provide whatever custom behavior is required (for example, calling a method on a Web service or getting a new object from a class factory).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="37989-106">İşleme göre bir öğe eklendiğinde <xref:System.Windows.Forms.BindingSource.AddingNew> olayı eklenmesi iptal edilemez.</span><span class="sxs-lookup"><span data-stu-id="37989-106">When an item is added by handling the <xref:System.Windows.Forms.BindingSource.AddingNew> event, the addition cannot be canceled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37989-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="37989-107">Example</span></span>  
 <span data-ttu-id="37989-108">Aşağıdaki örnekte nasıl bağlanacağını gösterir bir <xref:System.Windows.Forms.DataGridView> kullanarak bir üreteci denetimine bir <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="37989-108">The following example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a class factory by using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="37989-109">Kullanıcı tıkladığında <xref:System.Windows.Forms.DataGridView> denetimin yeni satır <xref:System.Windows.Forms.BindingSource.AddingNew> olayı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="37989-109">When the user clicks the <xref:System.Windows.Forms.DataGridView> control's new row, the <xref:System.Windows.Forms.BindingSource.AddingNew> event is raised.</span></span> <span data-ttu-id="37989-110">Yeni bir olay işleyicisi oluşturur `DemoCustomer` atandığı nesne <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="37989-110">The event handler creates a new `DemoCustomer` object, which is assigned to the <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="37989-111">Bu yeni neden `DemoCustomer` eklenecek nesne <xref:System.Windows.Forms.BindingSource> bileşenin listesi ve yeni satırında görüntülenecek <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="37989-111">This causes the new `DemoCustomer` object to be added to the <xref:System.Windows.Forms.BindingSource> component's list and to be displayed in the new row of the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="37989-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="37989-112">Compiling the Code</span></span>  
 <span data-ttu-id="37989-113">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="37989-113">This example requires:</span></span>  
  
-   <span data-ttu-id="37989-114">Sistem, System.Data, System.Drawing ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="37989-114">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="37989-115">Bu örnek visual Basic veya Visual C# için komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="37989-115">For information about building this example from the command line for visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="37989-116">Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37989-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="37989-117">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="37989-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37989-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="37989-118">See Also</span></span>  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="37989-119">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="37989-119">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="37989-120">Nasıl yapılır: Windows Forms Denetimini Bir Türe Bağlama</span><span class="sxs-lookup"><span data-stu-id="37989-120">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
