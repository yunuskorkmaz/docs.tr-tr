---
title: BindingSource bileşeni ile öğe eklemeyi özelleştirme
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
ms.openlocfilehash: 7d74fe6b4bbb1ddb94b359f5ba3ae32ed398d1dd
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738323"
---
# <a name="how-to-customize-item-addition-with-the-windows-forms-bindingsource"></a><span data-ttu-id="271db-102">Nasıl yapılır: Windows Forms BindingSource ile Öğe Eklemeyi Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="271db-102">How to: Customize Item Addition with the Windows Forms BindingSource</span></span>
<span data-ttu-id="271db-103">Bir Windows Forms denetimini bir veri kaynağına bağlamak için bir <xref:System.Windows.Forms.BindingSource> bileşeni kullandığınızda, yeni öğelerin oluşturulmasını özelleştirmek için gerekli olduğunu fark edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="271db-103">When you use a <xref:System.Windows.Forms.BindingSource> component to bind a Windows Forms control to a data source, you may find it necessary to customize the creation of new items.</span></span> <span data-ttu-id="271db-104"><xref:System.Windows.Forms.BindingSource> bileşeni, genellikle, bağlantılı denetimin yeni bir öğe oluşturması gerektiğinde ortaya çıkarılan <xref:System.Windows.Forms.BindingSource.AddingNew> olayını sağlayarak bu işlemi doğrudan hale getirir.</span><span class="sxs-lookup"><span data-stu-id="271db-104">The <xref:System.Windows.Forms.BindingSource> component makes this straightforward by providing the <xref:System.Windows.Forms.BindingSource.AddingNew> event, which is typically raised when the bound control needs to create a new item.</span></span> <span data-ttu-id="271db-105">Olay işleyiciniz hangi özel davranışın gerekli olduğunu (örneğin, bir Web hizmetinde bir yöntemi çağırmak veya bir sınıf fabrikasından yeni bir nesne almak) sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="271db-105">Your event handler can provide whatever custom behavior is required (for example, calling a method on a Web service or getting a new object from a class factory).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="271db-106"><xref:System.Windows.Forms.BindingSource.AddingNew> olayı işlenerek bir öğe eklendiğinde ekleme işlemi iptal edilemez.</span><span class="sxs-lookup"><span data-stu-id="271db-106">When an item is added by handling the <xref:System.Windows.Forms.BindingSource.AddingNew> event, the addition cannot be canceled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="271db-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="271db-107">Example</span></span>  
 <span data-ttu-id="271db-108">Aşağıdaki örnek, bir <xref:System.Windows.Forms.DataGridView> denetimini bir <xref:System.Windows.Forms.BindingSource> bileşeni kullanarak bir sınıf fabrikasına nasıl bağlayabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="271db-108">The following example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a class factory by using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="271db-109">Kullanıcı <xref:System.Windows.Forms.DataGridView> denetiminin yeni satırına tıkladığında <xref:System.Windows.Forms.BindingSource.AddingNew> olay tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="271db-109">When the user clicks the <xref:System.Windows.Forms.DataGridView> control's new row, the <xref:System.Windows.Forms.BindingSource.AddingNew> event is raised.</span></span> <span data-ttu-id="271db-110">Olay işleyicisi, <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> özelliğine atanan yeni bir `DemoCustomer` nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="271db-110">The event handler creates a new `DemoCustomer` object, which is assigned to the <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="271db-111">Bu, yeni `DemoCustomer` nesnesinin <xref:System.Windows.Forms.BindingSource> bileşenin listesine eklenmesine ve <xref:System.Windows.Forms.DataGridView> denetiminin yeni satırında görüntülenmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="271db-111">This causes the new `DemoCustomer` object to be added to the <xref:System.Windows.Forms.BindingSource> component's list and to be displayed in the new row of the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="271db-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="271db-112">Compiling the Code</span></span>  
 <span data-ttu-id="271db-113">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="271db-113">This example requires:</span></span>  
  
- <span data-ttu-id="271db-114">System, System. Data, System. Drawing ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="271db-114">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="271db-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="271db-115">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="271db-116">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="271db-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="271db-117">Nasıl yapılır: Windows Forms Denetimini Bir Türe Bağlama</span><span class="sxs-lookup"><span data-stu-id="271db-117">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
