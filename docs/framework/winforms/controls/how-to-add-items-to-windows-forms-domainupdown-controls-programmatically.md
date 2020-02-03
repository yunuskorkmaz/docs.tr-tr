---
title: DomainUpDown Denetimlerine Programlı Olarak Öğe Ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- spin button control [Windows Forms], adding items
- DomainUpDown control [Windows Forms], adding items to
ms.assetid: fd31d314-33eb-4181-90f8-d32ed0c4e072
ms.openlocfilehash: 2e9f51fa051bf9b62e95f289db97bffd83450036
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745587"
---
# <a name="how-to-add-items-to-windows-forms-domainupdown-controls-programmatically"></a><span data-ttu-id="54489-102">Nasıl yapılır: Windows Forms DomainUpDown Denetimlerine Programlı Olarak Öğe Ekleme</span><span class="sxs-lookup"><span data-stu-id="54489-102">How to: Add Items to Windows Forms DomainUpDown Controls Programmatically</span></span>
<span data-ttu-id="54489-103">Kodda Windows Forms <xref:System.Windows.Forms.DomainUpDown> denetimine öğe ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54489-103">You can add items to the Windows Forms <xref:System.Windows.Forms.DomainUpDown> control in code.</span></span> <span data-ttu-id="54489-104">Denetimin <xref:System.Windows.Forms.DomainUpDown.Items%2A> özelliğine öğe eklemek için <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> sınıfının <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> veya <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="54489-104">Call the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> or <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> method of the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> class to add items to the control's <xref:System.Windows.Forms.DomainUpDown.Items%2A> property.</span></span> <span data-ttu-id="54489-105"><xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> yöntemi bir koleksiyonun sonuna bir öğe ekler, ancak <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> yöntemi belirtilen konuma bir öğe ekler.</span><span class="sxs-lookup"><span data-stu-id="54489-105">The <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> method adds an item to the end of a collection, while the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> method adds an item at a specified position.</span></span>  
  
### <a name="to-add-a-new-item"></a><span data-ttu-id="54489-106">Yeni bir öğe eklemek için</span><span class="sxs-lookup"><span data-stu-id="54489-106">To add a new item</span></span>  
  
1. <span data-ttu-id="54489-107">Öğe listesinin sonuna bir öğe eklemek için <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="54489-107">Use the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> method to add an item to the end of the list of items.</span></span>  
  
    ```vb  
    DomainUpDown1.Items.Add("noodles")  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Add("noodles");  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Add("noodles");  
    ```  
  
     <span data-ttu-id="54489-108">veya</span><span class="sxs-lookup"><span data-stu-id="54489-108">-or-</span></span>  
  
2. <span data-ttu-id="54489-109">Belirli bir konumdaki listeye bir öğe eklemek için <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="54489-109">Use the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> method to insert an item into the list at a specified position.</span></span>  
  
    ```vb  
    ' Inserts an item at the third position in the list  
    DomainUpDown1.Items.Insert(2, "rice")  
    ```  
  
    ```csharp  
    // Inserts an item at the third position in the list  
    domainUpDown1.Items.Insert(2, "rice");  
    ```  
  
    ```cpp  
    // Inserts an item at the third position in the list  
    domainUpDown1->Items->Insert(2, "rice");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="54489-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54489-110">See also</span></span>

- <xref:System.Windows.Forms.DomainUpDown>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A?displayProperty=nameWithType>
- <xref:System.Collections.ArrayList.Insert%2A?displayProperty=nameWithType>
- [<span data-ttu-id="54489-111">DomainUpDown Denetimi</span><span class="sxs-lookup"><span data-stu-id="54489-111">DomainUpDown Control</span></span>](domainupdown-control-windows-forms.md)
- [<span data-ttu-id="54489-112">DomainUpDown Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="54489-112">DomainUpDown Control Overview</span></span>](domainupdown-control-overview-windows-forms.md)
