---
title: "Nasıl yapılır: ContextMenuStrip'ni Bir Denetimle İlişkilendirme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- context menus [Windows Forms], relating
- ContextMenuStrips [Windows Forms], associating with controls
- context menus [Windows Forms], associating with controls
- ContextMenuStrips [Windows Forms], relating
ms.assetid: 6fc40a42-5d69-427f-aa30-0a146193226b
ms.openlocfilehash: e1b2a49196d6da66d478a3d44eab64298cebe969
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586608"
---
# <a name="how-to-associate-a-contextmenustrip-with-a-control"></a><span data-ttu-id="71809-102">Nasıl yapılır: ContextMenuStrip'ni Bir Denetimle İlişkilendirme</span><span class="sxs-lookup"><span data-stu-id="71809-102">How to: Associate a ContextMenuStrip with a Control</span></span>
<span data-ttu-id="71809-103">Denetimleri ve kısayol menüleri oluşturduktan sonra kullanıcı denetimi tıklattığında verilen kısayol menüsünü görüntülemek için aşağıdaki yordamları kullanın.</span><span class="sxs-lookup"><span data-stu-id="71809-103">After creating your controls and shortcut menus, use the following procedures to display a given shortcut menu when the user right-clicks the control.</span></span> <span data-ttu-id="71809-104">Bu yordamlar ilişkilendirmek bir <xref:System.Windows.Forms.ContextMenuStrip> ve bir Windows formu ile bir <xref:System.Windows.Forms.ToolStrip> denetimi.</span><span class="sxs-lookup"><span data-stu-id="71809-104">These procedures associate a <xref:System.Windows.Forms.ContextMenuStrip> with a Windows Form and with a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
### <a name="to-associate-a-contextmenustrip-with-a-windows-form"></a><span data-ttu-id="71809-105">Contextmenustrip'ni bir Windows formu ile ilişkilendirmek için</span><span class="sxs-lookup"><span data-stu-id="71809-105">To associate a ContextMenuStrip with a Windows Form</span></span>  
  
1. <span data-ttu-id="71809-106">Ayarlama <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> özelliğini ilişkili adı <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="71809-106">Set the <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property to the name of the associated <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
### <a name="to-associate-a-contextmenustrip-with-a-toolstrip-control"></a><span data-ttu-id="71809-107">Contextmenustrip'ni bir ToolStrip denetimi ile ilişkilendirmek için</span><span class="sxs-lookup"><span data-stu-id="71809-107">To associate a ContextMenuStrip with a ToolStrip control</span></span>  
  
1. <span data-ttu-id="71809-108">Denetimin ayarlamak <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> özelliğini ilişkili adı <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="71809-108">Set the control's <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property to the name of the associated <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71809-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="71809-109">Example</span></span>  
 <span data-ttu-id="71809-110">Aşağıdaki kod örneği, bir Windows formu oluşturur ve bir <xref:System.Windows.Forms.ToolStrip>ve farklı bir ilişkilendirir <xref:System.Windows.Forms.ContextMenuStrip> denetimi ile bunların her biri.</span><span class="sxs-lookup"><span data-stu-id="71809-110">The following code example creates a Windows Form and a <xref:System.Windows.Forms.ToolStrip>, and associates a different <xref:System.Windows.Forms.ContextMenuStrip> control with each of them.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ContextMenuStrip#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ContextMenuStrip#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="71809-111">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="71809-111">Compiling the Code</span></span>  
 <span data-ttu-id="71809-112">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="71809-112">This example requires:</span></span>  
  
- <span data-ttu-id="71809-113">Sistem, System.Data System.Drawing ve System.Windows.Forms derlemelere başvuruları.</span><span class="sxs-lookup"><span data-stu-id="71809-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71809-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71809-114">See also</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.Control.ContextMenuStrip%2A>
- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="71809-115">Nasıl yapılır: Bir Contextmenustrip'e menü öğeleri ekleme</span><span class="sxs-lookup"><span data-stu-id="71809-115">How to: Add Menu Items to a ContextMenuStrip</span></span>](how-to-add-menu-items-to-a-contextmenustrip.md)
- [<span data-ttu-id="71809-116">ContextMenuStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="71809-116">ContextMenuStrip Control</span></span>](contextmenustrip-control.md)
