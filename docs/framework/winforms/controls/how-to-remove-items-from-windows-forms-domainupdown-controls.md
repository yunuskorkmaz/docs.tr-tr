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
# <a name="how-to-remove-items-from-windows-forms-domainupdown-controls"></a>Nasıl yapılır: Windows Forms DomainUpDown Denetimlerinden Öğeleri Kaldırma
<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> sınıfının <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> veya <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> yöntemini çağırarak Windows Forms <xref:System.Windows.Forms.DomainUpDown> denetiminden öğeleri kaldırabilirsiniz. <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> yöntemi belirli bir öğeyi kaldırır, ancak <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> yöntemi bir öğeyi konumuna göre kaldırır.  
  
### <a name="to-remove-an-item"></a>Bir öğeyi kaldırmak için  
  
- Bir öğeyi ada göre kaldırmak için <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> sınıfının <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> yöntemini kullanın.  
  
    ```vb  
    DomainUpDown1.Items.Remove("noodles")  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Remove("noodles");  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Remove("noodles");  
    ```  
  
     veya  
  
- Bir öğeyi konumuna göre kaldırmak için <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> yöntemini kullanın.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DomainUpDown>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A?displayProperty=nameWithType>
- [DomainUpDown Denetimi](domainupdown-control-windows-forms.md)
- [DomainUpDown Denetimine Genel Bakış](domainupdown-control-overview-windows-forms.md)
