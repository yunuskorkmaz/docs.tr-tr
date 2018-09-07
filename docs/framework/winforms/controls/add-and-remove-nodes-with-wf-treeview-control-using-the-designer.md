---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Formları TreeView Denetimi ile Düğüm Ekleme ve Kaldırma'
ms.date: 03/30/2017
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
ms.openlocfilehash: 95f3f097d8e01828f2727bac742c752b656019e5
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44047643"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a><span data-ttu-id="9df24-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Formları TreeView Denetimi ile Düğüm Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="9df24-102">How to: Add and Remove Nodes with the Windows Forms TreeView Control Using the Designer</span></span>
<span data-ttu-id="9df24-103">Windows Forms çünkü <xref:System.Windows.Forms.TreeView> denetimi dikkat kendi üst düğümlerinin nedir için ödeme gerekir düğüm eklerken bu düğümleri hiyerarşik bir biçimde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9df24-103">Because the Windows Forms <xref:System.Windows.Forms.TreeView> control displays nodes in a hierarchical manner, when adding a node you must pay attention to what its parent node is.</span></span>  
  
 <span data-ttu-id="9df24-104">Aşağıdaki yordam gerektirir bir **Windows uygulama** proje içeren bir form içeren bir <xref:System.Windows.Forms.TreeView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="9df24-104">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="9df24-105">Bu tür bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturmak](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) ve [nasıl yapılır: Windows Forms denetimlerine ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="9df24-105">For information about setting up such a project, see [How to: Create a Windows Application Project](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9df24-106">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="9df24-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="9df24-107">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="9df24-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="9df24-108">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="9df24-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-or-remove-nodes-in-the-designer"></a><span data-ttu-id="9df24-109">Ekleme veya düğümleri kaldırma Tasarımcısı'nda</span><span class="sxs-lookup"><span data-stu-id="9df24-109">To add or remove nodes in the designer</span></span>  
  
1.  <span data-ttu-id="9df24-110">Seçin <xref:System.Windows.Forms.TreeView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="9df24-110">Select the <xref:System.Windows.Forms.TreeView> control.</span></span>  
  
2.  <span data-ttu-id="9df24-111">İçinde **özellikleri** penceresinde tıklayın **üç nokta** (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) düğmesinin yanındaki <xref:System.Windows.Forms.TreeView.Nodes%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="9df24-111">In the **Properties** window, click the **Ellipsis** (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button next to the <xref:System.Windows.Forms.TreeView.Nodes%2A> property.</span></span>  
  
     <span data-ttu-id="9df24-112">**Editor objektu TreeNode** görünür.</span><span class="sxs-lookup"><span data-stu-id="9df24-112">The **TreeNode Editor** appears.</span></span>  
  
3.  <span data-ttu-id="9df24-113">Düğümler eklemek için bir kök düğümü olmalıdır; bir mevcut değilse, öncelikle bir kök tıklayarak eklemelisiniz **ekleme kök** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="9df24-113">To add nodes, a root node must exist; if one does not exist, you must first add a root by clicking the **Add Root** button.</span></span> <span data-ttu-id="9df24-114">Kök veya başka bir düğüme seçtikten sonra alt düğümleri ekleyebilirsiniz **alt öğe Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="9df24-114">You can then add child nodes by selecting the root or any other node and clicking the **Add Child** button.</span></span>  
  
4.  <span data-ttu-id="9df24-115">Düğümleri silmek için silin ve ardından için düğümü seçin **Sil** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="9df24-115">To delete nodes, select the node to delete and then click the **Delete** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9df24-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9df24-116">See Also</span></span>  
 [<span data-ttu-id="9df24-117">TreeView Denetimi</span><span class="sxs-lookup"><span data-stu-id="9df24-117">TreeView Control</span></span>](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [<span data-ttu-id="9df24-118">TreeView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9df24-118">TreeView Control Overview</span></span>](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)  
 [<span data-ttu-id="9df24-119">Nasıl yapılır: Windows Forms TreeView Denetimi için Simgeler Ayarlama</span><span class="sxs-lookup"><span data-stu-id="9df24-119">How to: Set Icons for the Windows Forms TreeView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)  
 [<span data-ttu-id="9df24-120">Nasıl yapılır: Bir Windows Forms TreeView Denetiminin Tüm Düğümlerinde Yineleme</span><span class="sxs-lookup"><span data-stu-id="9df24-120">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)  
 [<span data-ttu-id="9df24-121">Nasıl yapılır: Hangi TreeView Düğümüne Tıklandığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="9df24-121">How to: Determine Which TreeView Node Was Clicked</span></span>](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)  
 [<span data-ttu-id="9df24-122">Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="9df24-122">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
