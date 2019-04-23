---
title: 'Nasıl yapılır: ToolStripMenuItems Gizleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding
- MenuStrip control [Windows Forms], hiding menu items
- menus [Windows Forms], hiding menu items
- menu items [Windows Forms], hiding
- hiding menu items
ms.assetid: 418a768f-808a-44cd-8cef-f4e161883621
ms.openlocfilehash: dc9daa945f2a546548f2cc6ea033378bd9ceff93
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59127432"
---
# <a name="how-to-hide-toolstripmenuitems"></a>Nasıl yapılır: ToolStripMenuItems Gizleme
Menü öğelerini gizleme, uygulamanızın kullanıcı arayüzü denetlemek ve kullanıcı komutları kısıtlamak için bir yoldur. Genellikle, tüm menü öğeleri kullanılamadığında bir tüm menüyü Gizle isteyeceksiniz. Bu kullanıcı için daha az dikkat dağıtıcı faktör sunar. Ayrıca, tek başına bir gizleme kullanıcı bir menü komutu bir kısayol tuşu kullanarak erişmesini önlemez gibi hem gizleyebilir ve menü veya menü öğesi devre dışı bırakmak isteyebilirsiniz.  
  
### <a name="to-hide-any-menu-item-programmatically"></a>Program aracılığıyla herhangi bir menü öğesini gizlemek için  
  
-   Menü öğesi özelliklerini ayarladığınız yöntemi içinde ayarlamak üzere kod eklemek <xref:System.Windows.Forms.ToolStripItem.Visible%2A> özelliğini `false`.  
  
    ```vb  
    MenuItem3.Visible = False  
    ```  
  
    ```csharp  
    menuItem3.Visible = false;  
    ```  
  
    ```cpp  
    menuItem3->Visible = false;  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ToolStripItem.Visible%2A>
- <xref:System.Windows.Forms.MenuStrip>
- [MenuStrip Denetimine Genel Bakış](menustrip-control-overview-windows-forms.md)
- [Nasıl yapılır: Toolstripmenuıtems öğelerini devre dışı bırak](how-to-disable-toolstripmenuitems.md)
