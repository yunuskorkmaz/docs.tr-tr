---
title: "Nasıl yapılır: Windows Forms DomainUpDown Denetimlerinden Öğeleri Kaldırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DomainUpDown control [Windows Forms], removing items from
- spin button control [Windows Forms], removing items
ms.assetid: e70f5cbc-b497-41a9-975a-344c00e56ed2
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7cab9bf4445c7322c1b4824f26c0821de8c58657
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-remove-items-from-windows-forms-domainupdown-controls"></a><span data-ttu-id="f8c4e-102">Nasıl yapılır: Windows Forms DomainUpDown Denetimlerinden Öğeleri Kaldırma</span><span class="sxs-lookup"><span data-stu-id="f8c4e-102">How to: Remove Items from Windows Forms DomainUpDown Controls</span></span>
<span data-ttu-id="f8c4e-103">Windows Forms öğeleri kaldırabilirsiniz <xref:System.Windows.Forms.DomainUpDown> çağırarak denetim <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> veya <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> yöntemi <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f8c4e-103">You can remove items from the Windows Forms <xref:System.Windows.Forms.DomainUpDown> control by calling the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> or <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> method of the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> class.</span></span> <span data-ttu-id="f8c4e-104"><xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> Yöntemi, belirli bir öğeyi kaldırır ancak <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> yöntemi konumuna göre bir öğeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f8c4e-104">The <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> method removes a specific item, while the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> method removes an item by its position.</span></span>  
  
### <a name="to-remove-an-item"></a><span data-ttu-id="f8c4e-105">Bir öğeyi kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="f8c4e-105">To remove an item</span></span>  
  
-   <span data-ttu-id="f8c4e-106">Kullanım <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> yöntemi <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> sınıf adına göre bir öğeyi kaldırmak için.</span><span class="sxs-lookup"><span data-stu-id="f8c4e-106">Use the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> method of the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> class to remove an item by name.</span></span>  
  
    ```vb  
    DomainUpDown1.Items.Remove("noodles")  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Remove("noodles");  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Remove("noodles");  
    ```  
  
     <span data-ttu-id="f8c4e-107">veya</span><span class="sxs-lookup"><span data-stu-id="f8c4e-107">-or-</span></span>  
  
-   <span data-ttu-id="f8c4e-108">Kullanım <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> konumuna göre bir öğeyi kaldırmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="f8c4e-108">Use the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> method to remove an item by its position.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f8c4e-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f8c4e-109">See Also</span></span>  
 <xref:System.Windows.Forms.DomainUpDown>  
 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="f8c4e-110">DomainUpDown denetimi</span><span class="sxs-lookup"><span data-stu-id="f8c4e-110">DomainUpDown Control</span></span>](../../../../docs/framework/winforms/controls/domainupdown-control-windows-forms.md)  
 [<span data-ttu-id="f8c4e-111">DomainUpDown denetimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="f8c4e-111">DomainUpDown Control Overview</span></span>](../../../../docs/framework/winforms/controls/domainupdown-control-overview-windows-forms.md)
