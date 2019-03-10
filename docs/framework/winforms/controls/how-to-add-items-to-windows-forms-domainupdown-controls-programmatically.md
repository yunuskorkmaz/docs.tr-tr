---
title: 'Nasıl yapılır: Windows Forms DomainUpDown denetimlerine programlı olarak öğeleri Ekle'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- spin button control [Windows Forms], adding items
- DomainUpDown control [Windows Forms], adding items to
ms.assetid: fd31d314-33eb-4181-90f8-d32ed0c4e072
ms.openlocfilehash: 06c2c83ddfba67aaff775065cc2aa4515978bf81
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57722717"
---
# <a name="how-to-add-items-to-windows-forms-domainupdown-controls-programmatically"></a>Nasıl yapılır: Windows Forms DomainUpDown denetimlerine programlı olarak öğeleri Ekle
Windows Forms için öğeleri ekleyebilirsiniz <xref:System.Windows.Forms.DomainUpDown> kod denetimi. Çağrı <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> veya <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> yöntemi <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> denetimin öğeleri eklemek için sınıfı <xref:System.Windows.Forms.DomainUpDown.Items%2A> özelliği. <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> Yöntemi, bir koleksiyonun sonuna bir öğe ekler sırada <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> yöntemi, belirtilen konumda bir öğe ekler.  
  
### <a name="to-add-a-new-item"></a>Yeni bir öğe eklemek için  
  
1.  Kullanım <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> öğelerin listesini sonuna bir öğe eklemek için yöntemi.  
  
    ```vb  
    DomainUpDown1.Items.Add("noodles")  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Add("noodles");  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Add("noodles");  
    ```  
  
     -veya-  
  
2.  Kullanım <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> belirtilen konumda listeye bir öğe eklemek için yöntemi.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.DomainUpDown>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A?displayProperty=nameWithType>
- <xref:System.Collections.ArrayList.Insert%2A?displayProperty=nameWithType>
- [DomainUpDown Denetimi](domainupdown-control-windows-forms.md)
- [DomainUpDown Denetimine Genel Bakış](domainupdown-control-overview-windows-forms.md)
