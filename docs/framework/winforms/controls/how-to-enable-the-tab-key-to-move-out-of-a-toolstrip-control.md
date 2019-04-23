---
title: 'Nasıl yapılır: Bir ToolStrip Denetimi Dışında Hareket Etmek için SEKME tuşunu etkinleştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], moving between
- TAB key [Windows Forms], enabling
- ToolStrip control [Windows Forms], moving from
ms.assetid: 40f9e88b-09a3-428e-8da8-c00bb65079c6
ms.openlocfilehash: d4de7345a4e3ce122c4e1fc0a92f09b447204eb6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59113171"
---
# <a name="how-to-enable-the-tab-key-to-move-out-of-a-toolstrip-control"></a><span data-ttu-id="affb5-102">Nasıl yapılır: Bir ToolStrip Denetimi Dışında Hareket Etmek için SEKME tuşunu etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="affb5-102">How to: Enable the TAB Key to Move Out of a ToolStrip Control</span></span>
<span data-ttu-id="affb5-103">/ Taşımak için SEKME tuşuna basın kullanıcının etkinleştirmek için aşağıdaki yordamı kullanın. bir <xref:System.Windows.Forms.ToolStrip> sonraki denetime sekme sırası.</span><span class="sxs-lookup"><span data-stu-id="affb5-103">Use the following procedure to enable the user to press the TAB key to move out of a <xref:System.Windows.Forms.ToolStrip> to the next control in the tab order.</span></span>  
  
 <span data-ttu-id="affb5-104"><xref:System.Windows.Forms.ToolStrip> SEKME tuşunu ve ok tuşları öğeleri içinde ilk basarak kabul <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="affb5-104">The <xref:System.Windows.Forms.ToolStrip> accepts the first press of the TAB key, and the arrow keys select items within the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="affb5-105">Kullanıcı ikinci kez TAB tuşuna bastığında, kullanıcının sonraki denetime sekme sırasının alır.</span><span class="sxs-lookup"><span data-stu-id="affb5-105">When the user presses the TAB key a second time, it takes the user to the next control in the tab order.</span></span>  
  
### <a name="to-enable-the-user-to-press-the-tab-key-to-move-out-of-a-toolstrip-to-the-next-control"></a><span data-ttu-id="affb5-106">Sonraki denetime bir ToolStrip dışına taşımak için SEKME tuşuna basın kullanıcının etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="affb5-106">To enable the user to press the TAB key to move out of a ToolStrip to the next control</span></span>  
  
-   <span data-ttu-id="affb5-107">Ayarlama <xref:System.Windows.Forms.ToolStrip.TabStop%2A> özelliği <xref:System.Windows.Forms.ToolStrip> için `true`.</span><span class="sxs-lookup"><span data-stu-id="affb5-107">Set the <xref:System.Windows.Forms.ToolStrip.TabStop%2A> property of the <xref:System.Windows.Forms.ToolStrip> to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="affb5-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="affb5-108">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.TabStop%2A>
- [<span data-ttu-id="affb5-109">ToolStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="affb5-109">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
