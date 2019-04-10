---
title: 'Nasıl yapılır: Bir ToolStripContainer Kapsayıcısından bir ToolStrip Öğesini bir Forma Taşıma'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], parenting to forms
- Windows Forms, parenting ToolStrip controls
ms.assetid: a1c94a7f-6fc5-4e4c-84cf-ff11dc573d33
ms.openlocfilehash: 9106a69ea9f28442da6e3270f7cf5abb9374b62d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59335270"
---
# <a name="how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a><span data-ttu-id="0521e-102">Nasıl yapılır: Bir ToolStripContainer Kapsayıcısından bir ToolStrip Öğesini bir Forma Taşıma</span><span class="sxs-lookup"><span data-stu-id="0521e-102">How to: Move a ToolStrip Out of a ToolStripContainer onto a Form</span></span>
<span data-ttu-id="0521e-103">Taşımak için aşağıdaki yordamı kullanın. bir <xref:System.Windows.Forms.ToolStrip> dışı bir <xref:System.Windows.Forms.ToolStripContainer> forma.</span><span class="sxs-lookup"><span data-stu-id="0521e-103">Use the following procedure to move a <xref:System.Windows.Forms.ToolStrip> out of a <xref:System.Windows.Forms.ToolStripContainer> onto a form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0521e-104">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="0521e-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="0521e-105">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="0521e-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="0521e-106">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="0521e-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a><span data-ttu-id="0521e-107">Bir ToolStrip forma ToolStripContainer dışına taşımak için</span><span class="sxs-lookup"><span data-stu-id="0521e-107">To move a ToolStrip out of a ToolStripContainer onto a form</span></span>  
  
1. <span data-ttu-id="0521e-108">Seçin <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="0521e-108">Select the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
2. <span data-ttu-id="0521e-109">Kes <xref:System.Windows.Forms.ToolStrip> göre CTRL + X basarak veya sağ <xref:System.Windows.Forms.ToolStrip> ve **Kes** bağlam menüsünden.</span><span class="sxs-lookup"><span data-stu-id="0521e-109">Cut the <xref:System.Windows.Forms.ToolStrip> by pressing CTRL+X, or right-click the <xref:System.Windows.Forms.ToolStrip> and choose **Cut** from the context menu.</span></span>  
  
3. <span data-ttu-id="0521e-110">Formu seçin.</span><span class="sxs-lookup"><span data-stu-id="0521e-110">Select the form.</span></span>  
  
4. <span data-ttu-id="0521e-111">Yapıştırma <xref:System.Windows.Forms.ToolStrip> göre CTRL + V tuşlarına veya tercih **Yapıştır** gelen **Düzenle** menüsü.</span><span class="sxs-lookup"><span data-stu-id="0521e-111">Paste the <xref:System.Windows.Forms.ToolStrip> by pressing CTRL+V, or choose **Paste** from the **Edit** menu.</span></span>  
  
5. <span data-ttu-id="0521e-112">Ayarlama <xref:System.Windows.Forms.ToolStrip.Dock%2A> özelliği <xref:System.Windows.Forms.ToolStrip> için **üst**.</span><span class="sxs-lookup"><span data-stu-id="0521e-112">Set the <xref:System.Windows.Forms.ToolStrip.Dock%2A> property of the <xref:System.Windows.Forms.ToolStrip> to **Top**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0521e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0521e-113">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripContainer>
- [<span data-ttu-id="0521e-114">ToolStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0521e-114">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
