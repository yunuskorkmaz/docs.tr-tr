---
title: 'Nasıl yapılır: Bir ToolStripContainer Kapsayıcısından bir ToolStrip Öğesini bir Forma Taşıma'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], parenting to forms
- Windows Forms, parenting ToolStrip controls
ms.assetid: a1c94a7f-6fc5-4e4c-84cf-ff11dc573d33
ms.openlocfilehash: c6519add6789485d41146633abb5e11f80913649
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039822"
---
# <a name="how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a><span data-ttu-id="30764-102">Nasıl yapılır: Bir ToolStripContainer Kapsayıcısından bir ToolStrip Öğesini bir Forma Taşıma</span><span class="sxs-lookup"><span data-stu-id="30764-102">How to: Move a ToolStrip Out of a ToolStripContainer onto a Form</span></span>
<span data-ttu-id="30764-103"><xref:System.Windows.Forms.ToolStrip> Bir<xref:System.Windows.Forms.ToolStripContainer> formun dışına taşımak için aşağıdaki yordamı kullanın.</span><span class="sxs-lookup"><span data-stu-id="30764-103">Use the following procedure to move a <xref:System.Windows.Forms.ToolStrip> out of a <xref:System.Windows.Forms.ToolStripContainer> onto a form.</span></span>

## <a name="to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a><span data-ttu-id="30764-104">Bir ToolStripContainer 'ın ToolStrip dışına bir form üzerine taşımak için</span><span class="sxs-lookup"><span data-stu-id="30764-104">To move a ToolStrip out of a ToolStripContainer onto a form</span></span>

1. <span data-ttu-id="30764-105">Öğesini seçin <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="30764-105">Select the <xref:System.Windows.Forms.ToolStrip>.</span></span>

2. <span data-ttu-id="30764-106">CTRL + X tuşlarına basarak kesmeyi kesin veya sağ <xref:System.Windows.Forms.ToolStrip> tıklayıp bağlam menüsünden **Kes** ' i seçin. <xref:System.Windows.Forms.ToolStrip></span><span class="sxs-lookup"><span data-stu-id="30764-106">Cut the <xref:System.Windows.Forms.ToolStrip> by pressing CTRL+X, or right-click the <xref:System.Windows.Forms.ToolStrip> and choose **Cut** from the context menu.</span></span>

3. <span data-ttu-id="30764-107">Formu seçin.</span><span class="sxs-lookup"><span data-stu-id="30764-107">Select the form.</span></span>

4. <span data-ttu-id="30764-108">CTRL + V tuşlarına basarak yapıştırın veya **Düzenle** menüsünden Yapıştır ' ı seçin. <xref:System.Windows.Forms.ToolStrip></span><span class="sxs-lookup"><span data-stu-id="30764-108">Paste the <xref:System.Windows.Forms.ToolStrip> by pressing CTRL+V, or choose **Paste** from the **Edit** menu.</span></span>

5. <span data-ttu-id="30764-109">Öğesinin özelliğini **en üst**olarak ayarlayın. <xref:System.Windows.Forms.ToolStrip> <xref:System.Windows.Forms.ToolStrip.Dock%2A></span><span class="sxs-lookup"><span data-stu-id="30764-109">Set the <xref:System.Windows.Forms.ToolStrip.Dock%2A> property of the <xref:System.Windows.Forms.ToolStrip> to **Top**.</span></span>

## <a name="see-also"></a><span data-ttu-id="30764-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30764-110">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripContainer>
- [<span data-ttu-id="30764-111">ToolStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="30764-111">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
