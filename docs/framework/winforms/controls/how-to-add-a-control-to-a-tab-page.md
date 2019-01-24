---
title: 'Nasıl yapılır: Sekme sayfasına denetim ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TabPage control
- tab controls [Windows Forms], tab order
- tab pages [Windows Forms], adding controls
ms.assetid: b092532e-7346-469f-b9a1-897f9bea4fb7
ms.openlocfilehash: 42f0be64a6ac050fe8873588263b1faf7e2491a6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710189"
---
# <a name="how-to-add-a-control-to-a-tab-page"></a><span data-ttu-id="8d4d2-102">Nasıl yapılır: Sekme sayfasına denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="8d4d2-102">How to: Add a Control to a Tab Page</span></span>
<span data-ttu-id="8d4d2-103">Windows Forms kullanabileceğiniz <xref:System.Windows.Forms.TabControl> diğer denetimleri düzenli bir şekilde görüntülenecek.</span><span class="sxs-lookup"><span data-stu-id="8d4d2-103">You can use the Windows Forms <xref:System.Windows.Forms.TabControl> to display other controls in an organized fashion.</span></span> <span data-ttu-id="8d4d2-104">Aşağıdaki yordam, ilk sekme için bir düğme eklemek gösterilmektedir. Simge bir sekme sayfası etiket parçası ekleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms Tabcontrol'un görünüşünü değiştirme](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md).</span><span class="sxs-lookup"><span data-stu-id="8d4d2-104">The following procedure shows how to add a button to the first tab. For information about adding an icon to the label part of a tab page, see [How to: Change the Appearance of the Windows Forms TabControl](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md).</span></span>  
  
### <a name="to-add-a-control-programmatically"></a><span data-ttu-id="8d4d2-105">Programlı olarak denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="8d4d2-105">To add a control programmatically</span></span>  
  
1.  <span data-ttu-id="8d4d2-106">Kullanım <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> yöntemi tarafından döndürülen koleksiyon <xref:System.Windows.Forms.Control.Controls%2A> özelliği <xref:System.Windows.Forms.TabPage>:</span><span class="sxs-lookup"><span data-stu-id="8d4d2-106">Use the <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> method of the collection returned by the <xref:System.Windows.Forms.Control.Controls%2A> property of <xref:System.Windows.Forms.TabPage>:</span></span>  
  
     [!code-cpp[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cpp/add.cpp#1)]
     [!code-csharp[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cs/add.cs#1)]
     [!code-vb[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/vb/add.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8d4d2-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d4d2-107">See also</span></span>
- [<span data-ttu-id="8d4d2-108">TabControl Denetimi</span><span class="sxs-lookup"><span data-stu-id="8d4d2-108">TabControl Control</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)
- [<span data-ttu-id="8d4d2-109">TabControl Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8d4d2-109">TabControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="8d4d2-110">Nasıl yapılır: Windows Forms Tabcontrol'un görünüşünü değiştirme</span><span class="sxs-lookup"><span data-stu-id="8d4d2-110">How to: Change the Appearance of the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
- [<span data-ttu-id="8d4d2-111">Nasıl yapılır: Sekme sayfalarını devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="8d4d2-111">How to: Disable Tab Pages</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)
- [<span data-ttu-id="8d4d2-112">Nasıl yapılır: Windows Forms TabControl ile sekme ekleyip</span><span class="sxs-lookup"><span data-stu-id="8d4d2-112">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
