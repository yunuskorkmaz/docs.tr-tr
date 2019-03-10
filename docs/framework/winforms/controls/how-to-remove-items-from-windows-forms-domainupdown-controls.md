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
ms.openlocfilehash: 58c93f478414d24c2fdda0f9662936a8b520e381
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708970"
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
- [DomainUpDown Denetimi](domainupdown-control-windows-forms.md)
- [DomainUpDown Denetimine Genel Bakış](domainupdown-control-overview-windows-forms.md)
