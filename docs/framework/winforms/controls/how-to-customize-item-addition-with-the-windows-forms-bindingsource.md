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
ms.openlocfilehash: 59522791408eb9c8cabf97a62be2049aeb17f864
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935357"
---
# <a name="how-to-customize-item-addition-with-the-windows-forms-bindingsource"></a><span data-ttu-id="a2b7c-102">Nasıl yapılır: Windows Forms BindingSource ile Öğe Eklemeyi Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="a2b7c-102">How to: Customize Item Addition with the Windows Forms BindingSource</span></span>
<span data-ttu-id="a2b7c-103">Bir Windows Forms denetimini bir <xref:System.Windows.Forms.BindingSource> veri kaynağına bağlamak için bir bileşeni kullandığınızda, yeni öğelerin oluşturulmasını özelleştirmek için gerekli olduğunu fark edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2b7c-103">When you use a <xref:System.Windows.Forms.BindingSource> component to bind a Windows Forms control to a data source, you may find it necessary to customize the creation of new items.</span></span> <span data-ttu-id="a2b7c-104">Bileşen bunu, genellikle, bağlantılı denetimin yeni <xref:System.Windows.Forms.BindingSource.AddingNew> bir öğe oluşturması gerektiğinde ortaya çıkarılan olayını sağlayarak basittir. <xref:System.Windows.Forms.BindingSource></span><span class="sxs-lookup"><span data-stu-id="a2b7c-104">The <xref:System.Windows.Forms.BindingSource> component makes this straightforward by providing the <xref:System.Windows.Forms.BindingSource.AddingNew> event, which is typically raised when the bound control needs to create a new item.</span></span> <span data-ttu-id="a2b7c-105">Olay işleyiciniz hangi özel davranışın gerekli olduğunu (örneğin, bir Web hizmetinde bir yöntemi çağırmak veya bir sınıf fabrikasından yeni bir nesne almak) sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="a2b7c-105">Your event handler can provide whatever custom behavior is required (for example, calling a method on a Web service or getting a new object from a class factory).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a2b7c-106"><xref:System.Windows.Forms.BindingSource.AddingNew> Olay işlenerek bir öğe eklendiğinde ekleme işlemi iptal edilemez.</span><span class="sxs-lookup"><span data-stu-id="a2b7c-106">When an item is added by handling the <xref:System.Windows.Forms.BindingSource.AddingNew> event, the addition cannot be canceled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2b7c-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2b7c-107">Example</span></span>  
 <span data-ttu-id="a2b7c-108">Aşağıdaki örnek, bir <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.BindingSource> bileşeni kullanarak bir denetimin bir sınıf fabrikasına nasıl bağlanacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="a2b7c-108">The following example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a class factory by using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="a2b7c-109">Kullanıcı <xref:System.Windows.Forms.DataGridView> denetimin yeni satırına <xref:System.Windows.Forms.BindingSource.AddingNew> tıkladığında olay tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="a2b7c-109">When the user clicks the <xref:System.Windows.Forms.DataGridView> control's new row, the <xref:System.Windows.Forms.BindingSource.AddingNew> event is raised.</span></span> <span data-ttu-id="a2b7c-110">Olay işleyicisi, <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> özelliğine atanan yeni `DemoCustomer` bir nesne oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a2b7c-110">The event handler creates a new `DemoCustomer` object, which is assigned to the <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="a2b7c-111">Bu, yeni `DemoCustomer` nesnenin <xref:System.Windows.Forms.BindingSource> bileşenin listesine eklenmesine ve <xref:System.Windows.Forms.DataGridView> denetimin yeni satırında görüntülenmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="a2b7c-111">This causes the new `DemoCustomer` object to be added to the <xref:System.Windows.Forms.BindingSource> component's list and to be displayed in the new row of the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a2b7c-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="a2b7c-112">Compiling the Code</span></span>  
 <span data-ttu-id="a2b7c-113">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="a2b7c-113">This example requires:</span></span>  
  
- <span data-ttu-id="a2b7c-114">System, System. Data, System. Drawing ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="a2b7c-114">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2b7c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2b7c-115">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="a2b7c-116">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="a2b7c-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="a2b7c-117">Nasıl yapılır: Windows Forms denetimini bir türe bağlama</span><span class="sxs-lookup"><span data-stu-id="a2b7c-117">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
