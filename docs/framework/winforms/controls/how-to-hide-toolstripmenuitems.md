---
title: 'Nasıl yapılır: Toolstripmenuıtems gizleme'
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
ms.openlocfilehash: 73e49c96c20f145490a2d494177e21bc957605b8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54727631"
---
# <a name="how-to-hide-toolstripmenuitems"></a><span data-ttu-id="037c0-102">Nasıl yapılır: Toolstripmenuıtems gizleme</span><span class="sxs-lookup"><span data-stu-id="037c0-102">How to: Hide ToolStripMenuItems</span></span>
<span data-ttu-id="037c0-103">Menü öğelerini gizleme, uygulamanızın kullanıcı arayüzü denetlemek ve kullanıcı komutları kısıtlamak için bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="037c0-103">Hiding menu items is a way to control the user interface of your application and restrict user commands.</span></span> <span data-ttu-id="037c0-104">Genellikle, tüm menü öğeleri kullanılamadığında bir tüm menüyü Gizle isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="037c0-104">Often, you will want to hide an entire menu when all of the menu items on it are unavailable.</span></span> <span data-ttu-id="037c0-105">Bu kullanıcı için daha az dikkat dağıtıcı faktör sunar.</span><span class="sxs-lookup"><span data-stu-id="037c0-105">This presents fewer distractions for the user.</span></span> <span data-ttu-id="037c0-106">Ayrıca, tek başına bir gizleme kullanıcı bir menü komutu bir kısayol tuşu kullanarak erişmesini önlemez gibi hem gizleyebilir ve menü veya menü öğesi devre dışı bırakmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="037c0-106">Furthermore, you might want to both hide and disable the menu or menu item, as hiding alone does not prevent the user from accessing a menu command by using a shortcut key.</span></span>  
  
### <a name="to-hide-any-menu-item-programmatically"></a><span data-ttu-id="037c0-107">Program aracılığıyla herhangi bir menü öğesini gizlemek için</span><span class="sxs-lookup"><span data-stu-id="037c0-107">To hide any menu item programmatically</span></span>  
  
-   <span data-ttu-id="037c0-108">Menü öğesi özelliklerini ayarladığınız yöntemi içinde ayarlamak üzere kod eklemek <xref:System.Windows.Forms.ToolStripItem.Visible%2A> özelliğini `false`.</span><span class="sxs-lookup"><span data-stu-id="037c0-108">Within the method where you set the properties of the menu item, add code to set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property to `false`.</span></span>  
  
    ```vb  
    MenuItem3.Visible = False  
    ```  
  
    ```csharp  
    menuItem3.Visible = false;  
    ```  
  
    ```cpp  
    menuItem3->Visible = false;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="037c0-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="037c0-109">See also</span></span>
- <xref:System.Windows.Forms.ToolStripItem.Visible%2A>
- <xref:System.Windows.Forms.MenuStrip>
- [<span data-ttu-id="037c0-110">MenuStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="037c0-110">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
- [<span data-ttu-id="037c0-111">Nasıl yapılır: Toolstripmenuıtems öğelerini devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="037c0-111">How to: Disable ToolStripMenuItems</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems.md)
