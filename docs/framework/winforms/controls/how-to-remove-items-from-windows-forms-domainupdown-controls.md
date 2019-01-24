---
title: 'Nasıl yapılır: Windows Forms DomainUpDown denetimlerinden öğeleri kaldırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DomainUpDown control [Windows Forms], removing items from
- spin button control [Windows Forms], removing items
ms.assetid: e70f5cbc-b497-41a9-975a-344c00e56ed2
ms.openlocfilehash: f1cc4a26929a39e85fa6028613b0712cc76ed4f9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54644237"
---
# <a name="how-to-remove-items-from-windows-forms-domainupdown-controls"></a>Nasıl yapılır: Windows Forms DomainUpDown denetimlerinden öğeleri kaldırma
Windows Forms öğelerini kaldırabilir <xref:System.Windows.Forms.DomainUpDown> çağırarak denetim <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> veya <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> yöntemi <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> sınıfı. <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> Yöntemi, belirli bir öğeyi kaldırır ancak <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> yöntemi konumuna göre bir öğeyi kaldırır.  
  
### <a name="to-remove-an-item"></a>Bir öğeyi kaldırmak için  
  
-   Kullanım <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> yöntemi <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> sınıf adına göre bir öğeyi kaldırmak için.  
  
    ```vb  
    DomainUpDown1.Items.Remove("noodles")  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Remove("noodles");  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Remove("noodles");  
    ```  
  
     -veya-  
  
-   Kullanım <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> konumuna göre bir öğeyi kaldırmak için yöntemi.  
  
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
- [DomainUpDown Denetimi](../../../../docs/framework/winforms/controls/domainupdown-control-windows-forms.md)
- [DomainUpDown Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/domainupdown-control-overview-windows-forms.md)
