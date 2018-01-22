---
title: "Nasıl yapılır: Bir ToolStripContainer Kapsayıcısından bir ToolStrip Öğesini bir Forma Taşıma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolStrip control [Windows Forms], parenting to forms
- Windows Forms, parenting ToolStrip controls
ms.assetid: a1c94a7f-6fc5-4e4c-84cf-ff11dc573d33
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 97d65abf38ee434218fa9bec0d8a9cade31fb687
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a><span data-ttu-id="ac88f-102">Nasıl yapılır: Bir ToolStripContainer Kapsayıcısından bir ToolStrip Öğesini bir Forma Taşıma</span><span class="sxs-lookup"><span data-stu-id="ac88f-102">How to: Move a ToolStrip Out of a ToolStripContainer onto a Form</span></span>
<span data-ttu-id="ac88f-103">Taşımak için aşağıdaki yordamı kullanın bir <xref:System.Windows.Forms.ToolStrip> dışında bir <xref:System.Windows.Forms.ToolStripContainer> forma.</span><span class="sxs-lookup"><span data-stu-id="ac88f-103">Use the following procedure to move a <xref:System.Windows.Forms.ToolStrip> out of a <xref:System.Windows.Forms.ToolStripContainer> onto a form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ac88f-104">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="ac88f-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="ac88f-105">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="ac88f-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="ac88f-106">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="ac88f-106">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a><span data-ttu-id="ac88f-107">Forma ToolStripContainer dışında bir ToolStrip taşımak için</span><span class="sxs-lookup"><span data-stu-id="ac88f-107">To move a ToolStrip out of a ToolStripContainer onto a form</span></span>  
  
1.  <span data-ttu-id="ac88f-108">Seçin <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="ac88f-108">Select the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
2.  <span data-ttu-id="ac88f-109">Kesme <xref:System.Windows.Forms.ToolStrip> göre CTRL + X tuşlarına veya sağ <xref:System.Windows.Forms.ToolStrip> ve **Kes** ve bağlam menüsünden.</span><span class="sxs-lookup"><span data-stu-id="ac88f-109">Cut the <xref:System.Windows.Forms.ToolStrip> by pressing CTRL+X, or right-click the <xref:System.Windows.Forms.ToolStrip> and choose **Cut** from the context menu.</span></span>  
  
3.  <span data-ttu-id="ac88f-110">Formu seçin.</span><span class="sxs-lookup"><span data-stu-id="ac88f-110">Select the form.</span></span>  
  
4.  <span data-ttu-id="ac88f-111">Yapıştır <xref:System.Windows.Forms.ToolStrip> göre CTRL + V tuşuna basarak veya seçin **Yapıştır** gelen **Düzenle** menüsü.</span><span class="sxs-lookup"><span data-stu-id="ac88f-111">Paste the <xref:System.Windows.Forms.ToolStrip> by pressing CTRL+V, or choose **Paste** from the **Edit** menu.</span></span>  
  
5.  <span data-ttu-id="ac88f-112">Ayarlama <xref:System.Windows.Forms.ToolStrip.Dock%2A> özelliği <xref:System.Windows.Forms.ToolStrip> için **üst**.</span><span class="sxs-lookup"><span data-stu-id="ac88f-112">Set the <xref:System.Windows.Forms.ToolStrip.Dock%2A> property of the <xref:System.Windows.Forms.ToolStrip> to **Top**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac88f-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ac88f-113">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripContainer>  
 [<span data-ttu-id="ac88f-114">ToolStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ac88f-114">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
