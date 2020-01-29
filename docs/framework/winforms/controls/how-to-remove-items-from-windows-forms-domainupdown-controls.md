---
title: Öğeleri DomainUpDown Denetimlerinden kaldır
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DomainUpDown control [Windows Forms], removing items from
- spin button control [Windows Forms], removing items
ms.assetid: e70f5cbc-b497-41a9-975a-344c00e56ed2
ms.openlocfilehash: e52af5c5add4fda93e2b51c8afdb90c92e8d2f62
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735776"
---
# <a name="how-to-remove-items-from-windows-forms-domainupdown-controls"></a><span data-ttu-id="4923c-102">Nasıl yapılır: Windows Forms DomainUpDown Denetimlerinden Öğeleri Kaldırma</span><span class="sxs-lookup"><span data-stu-id="4923c-102">How to: Remove Items from Windows Forms DomainUpDown Controls</span></span>
<span data-ttu-id="4923c-103"><xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> sınıfının <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> veya <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> yöntemini çağırarak Windows Forms <xref:System.Windows.Forms.DomainUpDown> denetiminden öğeleri kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4923c-103">You can remove items from the Windows Forms <xref:System.Windows.Forms.DomainUpDown> control by calling the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> or <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> method of the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> class.</span></span> <span data-ttu-id="4923c-104"><xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> yöntemi belirli bir öğeyi kaldırır, ancak <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> yöntemi bir öğeyi konumuna göre kaldırır.</span><span class="sxs-lookup"><span data-stu-id="4923c-104">The <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> method removes a specific item, while the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> method removes an item by its position.</span></span>  
  
### <a name="to-remove-an-item"></a><span data-ttu-id="4923c-105">Bir öğeyi kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="4923c-105">To remove an item</span></span>  
  
- <span data-ttu-id="4923c-106">Bir öğeyi ada göre kaldırmak için <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> sınıfının <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="4923c-106">Use the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> method of the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> class to remove an item by name.</span></span>  
  
    ```vb  
    DomainUpDown1.Items.Remove("noodles")  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Remove("noodles");  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Remove("noodles");  
    ```  
  
     <span data-ttu-id="4923c-107">veya</span><span class="sxs-lookup"><span data-stu-id="4923c-107">-or-</span></span>  
  
- <span data-ttu-id="4923c-108">Bir öğeyi konumuna göre kaldırmak için <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="4923c-108">Use the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> method to remove an item by its position.</span></span>  
  
    ```vb  
    ' Removes the first item in the list.  
    DomainUpDown1.Items.RemoveAt(0)  
    ```  
  
    ```csharp  
    // Removes the first item in the list.  
    domainUpDown1.Items.RemoveAt(0);  
    ```  
  
    ```cpp  
    // Removes the first item in the list.  
    domainUpDown1->Items->RemoveAt(0);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4923c-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4923c-109">See also</span></span>

- <xref:System.Windows.Forms.DomainUpDown>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A?displayProperty=nameWithType>
- [<span data-ttu-id="4923c-110">DomainUpDown Denetimi</span><span class="sxs-lookup"><span data-stu-id="4923c-110">DomainUpDown Control</span></span>](domainupdown-control-windows-forms.md)
- [<span data-ttu-id="4923c-111">DomainUpDown Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4923c-111">DomainUpDown Control Overview</span></span>](domainupdown-control-overview-windows-forms.md)
