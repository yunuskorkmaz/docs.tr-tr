---
title: 'Nasıl yapılır: MDI Uygulamaları için Otomatik Menü Birleştirmeyi Ayarlama'
ms.date: 03/30/2017
helpviewer_keywords:
- MenuStrip [Windows Forms], merging
- Merging [Windows Forms], automatic menu
ms.assetid: 55e32cad-1141-4a56-aa33-d9543ca3d393
ms.openlocfilehash: e308ef8327fc439f52c4e3476a663f47fa00a379
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533467"
---
# <a name="how-to-set-up-automatic-menu-merging-for-mdi-applications"></a><span data-ttu-id="94635-102">Nasıl yapılır: MDI Uygulamaları için Otomatik Menü Birleştirmeyi Ayarlama</span><span class="sxs-lookup"><span data-stu-id="94635-102">How to: Set Up Automatic Menu Merging for MDI Applications</span></span>
<span data-ttu-id="94635-103">Otomatik bir Çoklu belge arabirimi (MDI) uygulaması birleştirmeyi ayarlamak için aşağıdaki yordamı temel adımları sunar <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="94635-103">The following procedure gives the basic steps for setting up automatic merging in a multiple-document interface (MDI) application with <xref:System.Windows.Forms.MenuStrip>.</span></span>  
  
### <a name="to-set-up-automatic-menu-merging"></a><span data-ttu-id="94635-104">Otomatik menü birleştirmeyi ayarlama için</span><span class="sxs-lookup"><span data-stu-id="94635-104">To set up automatic menu merging</span></span>  
  
1.  <span data-ttu-id="94635-105">MDI üst formu ayarlayarak oluşturma kendi <xref:System.Windows.Forms.Form.IsMdiContainer%2A> özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="94635-105">Create the MDI parent form by setting its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2.  <span data-ttu-id="94635-106">Ekleme bir <xref:System.Windows.Forms.MenuStrip> ayarı MDI için kendi <xref:System.Windows.Forms.Form.MainMenuStrip%2A> özelliğini <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="94635-106">Add a <xref:System.Windows.Forms.MenuStrip> to the MDI parent, setting its <xref:System.Windows.Forms.Form.MainMenuStrip%2A> property to that <xref:System.Windows.Forms.MenuStrip>.</span></span>  
  
3.  <span data-ttu-id="94635-107">MDI alt formu oluşturma ve ayarlama kendi <xref:System.Windows.Forms.Form.MdiParent%2A> üst formun adını özelliğine.</span><span class="sxs-lookup"><span data-stu-id="94635-107">Create an MDI child form, and set its <xref:System.Windows.Forms.Form.MdiParent%2A> property to the name of the parent form.</span></span>  
  
4.  <span data-ttu-id="94635-108">Ekleme bir <xref:System.Windows.Forms.MenuStrip> MDI alt formu.</span><span class="sxs-lookup"><span data-stu-id="94635-108">Add a <xref:System.Windows.Forms.MenuStrip> to the MDI child form.</span></span>  
  
5.  <span data-ttu-id="94635-109">Alt formunda <xref:System.Windows.Forms.ToolStripItem.Visible%2A> özelliği <xref:System.Windows.Forms.MenuStrip> için `false`.</span><span class="sxs-lookup"><span data-stu-id="94635-109">On the child form, set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of the <xref:System.Windows.Forms.MenuStrip> to `false`.</span></span>  
  
6.  <span data-ttu-id="94635-110">Alt formun için menü öğeleri ekleme <xref:System.Windows.Forms.MenuStrip> üst form birleştirmek istediğiniz <xref:System.Windows.Forms.MenuStrip> alt formu zaman etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="94635-110">Add menu items to the child form's <xref:System.Windows.Forms.MenuStrip> that you want to merge into the parent form's <xref:System.Windows.Forms.MenuStrip> when the child form is activated.</span></span>  
  
7.  <span data-ttu-id="94635-111">Kullanım <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> özelliği menüsünde alt form öğelerini <xref:System.Windows.Forms.MenuStrip> üst forma nasıl birleştirecek denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="94635-111">Use the <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> property on the menu items in the child form's <xref:System.Windows.Forms.MenuStrip> to control how they merge into the parent form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94635-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="94635-112">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [<span data-ttu-id="94635-113">MenuStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="94635-113">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
