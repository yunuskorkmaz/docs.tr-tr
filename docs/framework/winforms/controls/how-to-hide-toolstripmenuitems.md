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
ms.openlocfilehash: 64c0f093063357c1e8db5933c035cc8295ad4f1e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623047"
---
# <a name="how-to-hide-toolstripmenuitems"></a><span data-ttu-id="495fb-102">Nasıl yapılır: ToolStripMenuItems Gizleme</span><span class="sxs-lookup"><span data-stu-id="495fb-102">How to: Hide ToolStripMenuItems</span></span>
<span data-ttu-id="495fb-103">Menü öğelerini gizleme, uygulamanızın kullanıcı arayüzü denetlemek ve kullanıcı komutları kısıtlamak için bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="495fb-103">Hiding menu items is a way to control the user interface of your application and restrict user commands.</span></span> <span data-ttu-id="495fb-104">Genellikle, tüm menü öğeleri kullanılamadığında bir tüm menüyü Gizle isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="495fb-104">Often, you will want to hide an entire menu when all of the menu items on it are unavailable.</span></span> <span data-ttu-id="495fb-105">Bu kullanıcı için daha az dikkat dağıtıcı faktör sunar.</span><span class="sxs-lookup"><span data-stu-id="495fb-105">This presents fewer distractions for the user.</span></span> <span data-ttu-id="495fb-106">Ayrıca, tek başına bir gizleme kullanıcı bir menü komutu bir kısayol tuşu kullanarak erişmesini önlemez gibi hem gizleyebilir ve menü veya menü öğesi devre dışı bırakmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="495fb-106">Furthermore, you might want to both hide and disable the menu or menu item, as hiding alone does not prevent the user from accessing a menu command by using a shortcut key.</span></span>  
  
### <a name="to-hide-any-menu-item-programmatically"></a><span data-ttu-id="495fb-107">Program aracılığıyla herhangi bir menü öğesini gizlemek için</span><span class="sxs-lookup"><span data-stu-id="495fb-107">To hide any menu item programmatically</span></span>  
  
- <span data-ttu-id="495fb-108">Menü öğesi özelliklerini ayarladığınız yöntemi içinde ayarlamak üzere kod eklemek <xref:System.Windows.Forms.ToolStripItem.Visible%2A> özelliğini `false`.</span><span class="sxs-lookup"><span data-stu-id="495fb-108">Within the method where you set the properties of the menu item, add code to set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property to `false`.</span></span>  
  
    ```vb  
    MenuItem3.Visible = False  
    ```  
  
    ```csharp  
    menuItem3.Visible = false;  
    ```  
  
    ```cpp  
    menuItem3->Visible = false;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="495fb-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="495fb-109">See also</span></span>

- <xref:System.Windows.Forms.ToolStripItem.Visible%2A>
- <xref:System.Windows.Forms.MenuStrip>
- [<span data-ttu-id="495fb-110">MenuStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="495fb-110">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
- [<span data-ttu-id="495fb-111">Nasıl yapılır: Toolstripmenuıtems öğelerini devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="495fb-111">How to: Disable ToolStripMenuItems</span></span>](how-to-disable-toolstripmenuitems.md)
