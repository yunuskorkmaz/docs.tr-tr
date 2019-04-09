---
title: 'Nasıl yapılır: MDI Uygulamaları için Otomatik Menü Birleştirmeyi Ayarlama'
ms.date: 03/30/2017
helpviewer_keywords:
- MenuStrip [Windows Forms], merging
- Merging [Windows Forms], automatic menu
ms.assetid: 55e32cad-1141-4a56-aa33-d9543ca3d393
ms.openlocfilehash: 17edde6e3968823abc915eb5faed6d2751ed9393
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129362"
---
# <a name="how-to-set-up-automatic-menu-merging-for-mdi-applications"></a><span data-ttu-id="3c743-102">Nasıl yapılır: MDI Uygulamaları için Otomatik Menü Birleştirmeyi Ayarlama</span><span class="sxs-lookup"><span data-stu-id="3c743-102">How to: Set Up Automatic Menu Merging for MDI Applications</span></span>
<span data-ttu-id="3c743-103">Otomatik ile Çok Belgeli Arabirim (MDI) uygulamasında birleştirmeyi ayarlamak için aşağıdaki yordamı temel adımları sunar <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="3c743-103">The following procedure gives the basic steps for setting up automatic merging in a multiple-document interface (MDI) application with <xref:System.Windows.Forms.MenuStrip>.</span></span>  
  
### <a name="to-set-up-automatic-menu-merging"></a><span data-ttu-id="3c743-104">Otomatik menü birleştirmeyi ayarlama</span><span class="sxs-lookup"><span data-stu-id="3c743-104">To set up automatic menu merging</span></span>  
  
1.  <span data-ttu-id="3c743-105">MDI üst formunun oluşturabilmek, <xref:System.Windows.Forms.Form.IsMdiContainer%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="3c743-105">Create the MDI parent form by setting its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2.  <span data-ttu-id="3c743-106">Ekleme bir <xref:System.Windows.Forms.MenuStrip> ayarlama MDI için kendi <xref:System.Windows.Forms.Form.MainMenuStrip%2A> özelliğini <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="3c743-106">Add a <xref:System.Windows.Forms.MenuStrip> to the MDI parent, setting its <xref:System.Windows.Forms.Form.MainMenuStrip%2A> property to that <xref:System.Windows.Forms.MenuStrip>.</span></span>  
  
3.  <span data-ttu-id="3c743-107">MDI alt formu oluşturun ve ayarlayın, <xref:System.Windows.Forms.Form.MdiParent%2A> özelliğini üst formun adı.</span><span class="sxs-lookup"><span data-stu-id="3c743-107">Create an MDI child form, and set its <xref:System.Windows.Forms.Form.MdiParent%2A> property to the name of the parent form.</span></span>  
  
4.  <span data-ttu-id="3c743-108">Ekleme bir <xref:System.Windows.Forms.MenuStrip> MDI alt formu.</span><span class="sxs-lookup"><span data-stu-id="3c743-108">Add a <xref:System.Windows.Forms.MenuStrip> to the MDI child form.</span></span>  
  
5.  <span data-ttu-id="3c743-109">Alt formunda <xref:System.Windows.Forms.ToolStripItem.Visible%2A> özelliği <xref:System.Windows.Forms.MenuStrip> için `false`.</span><span class="sxs-lookup"><span data-stu-id="3c743-109">On the child form, set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of the <xref:System.Windows.Forms.MenuStrip> to `false`.</span></span>  
  
6.  <span data-ttu-id="3c743-110">Alt formun menü öğeleri ekleme <xref:System.Windows.Forms.MenuStrip> üst form birleştirmek istediğiniz <xref:System.Windows.Forms.MenuStrip> alt formun zaman etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3c743-110">Add menu items to the child form's <xref:System.Windows.Forms.MenuStrip> that you want to merge into the parent form's <xref:System.Windows.Forms.MenuStrip> when the child form is activated.</span></span>  
  
7.  <span data-ttu-id="3c743-111">Kullanım <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> özelliği menüsündeki öğeler alt formu <xref:System.Windows.Forms.MenuStrip> üst formun nasıl birleştirecek denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="3c743-111">Use the <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> property on the menu items in the child form's <xref:System.Windows.Forms.MenuStrip> to control how they merge into the parent form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c743-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c743-112">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="3c743-113">MenuStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3c743-113">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
