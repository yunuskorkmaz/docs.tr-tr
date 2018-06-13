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
ms.openlocfilehash: 73f67bbe6b2d51a59b6f72ab5faf21db9d6db12d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531959"
---
# <a name="how-to-hide-toolstripmenuitems"></a>Nasıl yapılır: ToolStripMenuItems Gizleme
Menü öğelerini gizleme, uygulamanızın kullanıcı arabirimi denetlemek ve kullanıcı komutları kısıtlamak için bir yoldur. Genellikle, tüm menü öğeleri kullanılamaz duruma geldiğinde tüm menüyü Gizle isteyeceksiniz. Bu kullanıcı için daha az karışıklıkları gösterir. Ayrıca, tek başına bir gizleme kullanıcı bir kısayol tuşu kullanarak menü komutu erişmesini engellemez gibi Gizle hem menüsü veya menü öğesini devre dışı bırakmak isteyebilirsiniz.  
  
### <a name="to-hide-any-menu-item-programmatically"></a>Herhangi bir menü öğesini program aracılığıyla gizleme  
  
-   Menü öğesi özelliklerini ayarladığınız yöntemi içinde ayarlamak için kod ekleme <xref:System.Windows.Forms.ToolStripItem.Visible%2A> özelliğine `false`.  
  
    ```vb  
    MenuItem3.Visible = False  
    ```  
  
    ```csharp  
    menuItem3.Visible = false;  
    ```  
  
    ```cpp  
    menuItem3->Visible = false;  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ToolStripItem.Visible%2A>  
 <xref:System.Windows.Forms.MenuStrip>  
 [MenuStrip Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)  
 [Nasıl yapılır: ToolStripMenuItems'ı Devre Dışı Bırakma](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems.md)
