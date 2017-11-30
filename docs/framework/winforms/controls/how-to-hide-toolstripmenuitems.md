---
title: "Nasıl yapılır: ToolStripMenuItems Gizleme"
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
- ToolStripMenuItems [Windows Forms], hiding
- MenuStrip control [Windows Forms], hiding menu items
- menus [Windows Forms], hiding menu items
- menu items [Windows Forms], hiding
- hiding menu items
ms.assetid: 418a768f-808a-44cd-8cef-f4e161883621
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7cb24fd36bdee76fa80a87d48f41b72f01c8f263
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-hide-toolstripmenuitems"></a><span data-ttu-id="3fcb7-102">Nasıl yapılır: ToolStripMenuItems Gizleme</span><span class="sxs-lookup"><span data-stu-id="3fcb7-102">How to: Hide ToolStripMenuItems</span></span>
<span data-ttu-id="3fcb7-103">Menü öğelerini gizleme, uygulamanızın kullanıcı arabirimi denetlemek ve kullanıcı komutları kısıtlamak için bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="3fcb7-103">Hiding menu items is a way to control the user interface of your application and restrict user commands.</span></span> <span data-ttu-id="3fcb7-104">Genellikle, tüm menü öğeleri kullanılamaz duruma geldiğinde tüm menüyü Gizle isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="3fcb7-104">Often, you will want to hide an entire menu when all of the menu items on it are unavailable.</span></span> <span data-ttu-id="3fcb7-105">Bu kullanıcı için daha az karışıklıkları gösterir.</span><span class="sxs-lookup"><span data-stu-id="3fcb7-105">This presents fewer distractions for the user.</span></span> <span data-ttu-id="3fcb7-106">Ayrıca, tek başına bir gizleme kullanıcı bir kısayol tuşu kullanarak menü komutu erişmesini engellemez gibi Gizle hem menüsü veya menü öğesini devre dışı bırakmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fcb7-106">Furthermore, you might want to both hide and disable the menu or menu item, as hiding alone does not prevent the user from accessing a menu command by using a shortcut key.</span></span>  
  
### <a name="to-hide-any-menu-item-programmatically"></a><span data-ttu-id="3fcb7-107">Herhangi bir menü öğesini program aracılığıyla gizleme</span><span class="sxs-lookup"><span data-stu-id="3fcb7-107">To hide any menu item programmatically</span></span>  
  
-   <span data-ttu-id="3fcb7-108">Menü öğesi özelliklerini ayarladığınız yöntemi içinde ayarlamak için kod ekleme <xref:System.Windows.Forms.ToolStripItem.Visible%2A> özelliğine `false`.</span><span class="sxs-lookup"><span data-stu-id="3fcb7-108">Within the method where you set the properties of the menu item, add code to set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property to `false`.</span></span>  
  
    ```vb  
    MenuItem3.Visible = False  
    ```  
  
    ```csharp  
    menuItem3.Visible = false;  
    ```  
  
    ```cpp  
    menuItem3->Visible = false;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3fcb7-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3fcb7-109">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripItem.Visible%2A>  
 <xref:System.Windows.Forms.MenuStrip>  
 [<span data-ttu-id="3fcb7-110">MenuStrip denetimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="3fcb7-110">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)  
 [<span data-ttu-id="3fcb7-111">Nasıl yapılır: Toolstripmenuıtems'ni devre dışı bırakma</span><span class="sxs-lookup"><span data-stu-id="3fcb7-111">How to: Disable ToolStripMenuItems</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems.md)
