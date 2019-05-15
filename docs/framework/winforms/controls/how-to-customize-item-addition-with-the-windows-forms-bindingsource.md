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
ms.openlocfilehash: 94c7b304dd8b909d60ef6b25f828524594caf886
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592821"
---
# <a name="how-to-customize-item-addition-with-the-windows-forms-bindingsource"></a><span data-ttu-id="1c0cf-102">Nasıl yapılır: Windows Forms BindingSource ile Öğe Eklemeyi Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="1c0cf-102">How to: Customize Item Addition with the Windows Forms BindingSource</span></span>
<span data-ttu-id="1c0cf-103">Kullandığınızda, bir <xref:System.Windows.Forms.BindingSource> bir Windows Forms denetimini bir veri kaynağına bağlamak için bileşen oluşturma işlemini yeni öğeleri özelleştirmek gerekli bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c0cf-103">When you use a <xref:System.Windows.Forms.BindingSource> component to bind a Windows Forms control to a data source, you may find it necessary to customize the creation of new items.</span></span> <span data-ttu-id="1c0cf-104"><xref:System.Windows.Forms.BindingSource> Bileşeni hale getirir bu basit sağlayarak <xref:System.Windows.Forms.BindingSource.AddingNew> ilişkili denetim yeni bir öğe oluşturmak gerektiğinde genellikle oluşan olayı,.</span><span class="sxs-lookup"><span data-stu-id="1c0cf-104">The <xref:System.Windows.Forms.BindingSource> component makes this straightforward by providing the <xref:System.Windows.Forms.BindingSource.AddingNew> event, which is typically raised when the bound control needs to create a new item.</span></span> <span data-ttu-id="1c0cf-105">Hangi özel davranış (örneğin, bir Web hizmeti üzerinde bir yöntemi çağırmak veya yeni bir nesne bir sınıf üreteci almak) gerekli değildir, olay işleyicisi sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="1c0cf-105">Your event handler can provide whatever custom behavior is required (for example, calling a method on a Web service or getting a new object from a class factory).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c0cf-106">İşleme göre bir öğe eklendiğinde <xref:System.Windows.Forms.BindingSource.AddingNew> olay eklenmesini iptal edilemez.</span><span class="sxs-lookup"><span data-stu-id="1c0cf-106">When an item is added by handling the <xref:System.Windows.Forms.BindingSource.AddingNew> event, the addition cannot be canceled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c0cf-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="1c0cf-107">Example</span></span>  
 <span data-ttu-id="1c0cf-108">Aşağıdaki örnek nasıl bağlanacağını gösterir. bir <xref:System.Windows.Forms.DataGridView> kullanarak bir sınıf üreteci denetimine bir <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="1c0cf-108">The following example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a class factory by using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="1c0cf-109">Kullanıcı tıkladığında <xref:System.Windows.Forms.DataGridView> denetimin yeni satır <xref:System.Windows.Forms.BindingSource.AddingNew> olayı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1c0cf-109">When the user clicks the <xref:System.Windows.Forms.DataGridView> control's new row, the <xref:System.Windows.Forms.BindingSource.AddingNew> event is raised.</span></span> <span data-ttu-id="1c0cf-110">Yeni bir olay işleyicisi oluşturur `DemoCustomer` öğesine atanan nesne <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="1c0cf-110">The event handler creates a new `DemoCustomer` object, which is assigned to the <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="1c0cf-111">Bu yeni neden `DemoCustomer` eklenecek nesne <xref:System.Windows.Forms.BindingSource> bileşenin listesi ve yeni satırında görüntülenecek <xref:System.Windows.Forms.DataGridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="1c0cf-111">This causes the new `DemoCustomer` object to be added to the <xref:System.Windows.Forms.BindingSource> component's list and to be displayed in the new row of the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1c0cf-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="1c0cf-112">Compiling the Code</span></span>  
 <span data-ttu-id="1c0cf-113">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="1c0cf-113">This example requires:</span></span>  
  
- <span data-ttu-id="1c0cf-114">Sistem, System.Data System.Drawing ve System.Windows.Forms derlemelere başvuruları.</span><span class="sxs-lookup"><span data-stu-id="1c0cf-114">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c0cf-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c0cf-115">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="1c0cf-116">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="1c0cf-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="1c0cf-117">Nasıl yapılır: Bir Windows Forms denetimini bir türe bağlama</span><span class="sxs-lookup"><span data-stu-id="1c0cf-117">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
