---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms TreeView Denetimi ile Düğüm Ekleme ve Kaldırma'
ms.date: 03/30/2017
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
ms.openlocfilehash: ca8b19e8019c170f1826660e951294b18a25e96d
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880632"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a><span data-ttu-id="06930-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms TreeView Denetimi ile Düğüm Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="06930-102">How to: Add and Remove Nodes with the Windows Forms TreeView Control Using the Designer</span></span>
<span data-ttu-id="06930-103">Windows Forms çünkü <xref:System.Windows.Forms.TreeView> denetimi dikkat kendi üst düğümlerinin nedir için ödeme gerekir düğüm eklerken bu düğümleri hiyerarşik bir biçimde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="06930-103">Because the Windows Forms <xref:System.Windows.Forms.TreeView> control displays nodes in a hierarchical manner, when adding a node you must pay attention to what its parent node is.</span></span>  
  
 <span data-ttu-id="06930-104">Aşağıdaki yordam gerektirir bir **Windows uygulama** proje içeren bir form içeren bir <xref:System.Windows.Forms.TreeView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="06930-104">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="06930-105">Bu tür bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir Windows Forms uygulaması projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms'a denetimler ekleme](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="06930-105">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06930-106">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="06930-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="06930-107">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="06930-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="06930-108">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="06930-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-or-remove-nodes-in-the-designer"></a><span data-ttu-id="06930-109">Ekleme veya düğümleri kaldırma Tasarımcısı'nda</span><span class="sxs-lookup"><span data-stu-id="06930-109">To add or remove nodes in the designer</span></span>  
  
1. <span data-ttu-id="06930-110">Seçin <xref:System.Windows.Forms.TreeView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="06930-110">Select the <xref:System.Windows.Forms.TreeView> control.</span></span>  
  
2.  <span data-ttu-id="06930-111">İçinde **özellikleri** penceresinde tıklayın **üç nokta** (![Visual Studio Özellikler penceresinde üç nokta düğmesini (…)](./media/visual-studio-ellipsis-button.png)) düğmesinin yanındaki <xref:System.Windows.Forms.TreeView.Nodes%2A> özelliği .</span><span class="sxs-lookup"><span data-stu-id="06930-111">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.TreeView.Nodes%2A> property.</span></span>  
  
     <span data-ttu-id="06930-112">**Editor objektu TreeNode** görünür.</span><span class="sxs-lookup"><span data-stu-id="06930-112">The **TreeNode Editor** appears.</span></span>  
  
3. <span data-ttu-id="06930-113">Düğümler eklemek için bir kök düğümü olmalıdır; bir mevcut değilse, öncelikle bir kök tıklayarak eklemelisiniz **ekleme kök** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="06930-113">To add nodes, a root node must exist; if one does not exist, you must first add a root by clicking the **Add Root** button.</span></span> <span data-ttu-id="06930-114">Kök veya başka bir düğüme seçtikten sonra alt düğümleri ekleyebilirsiniz **alt öğe Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="06930-114">You can then add child nodes by selecting the root or any other node and clicking the **Add Child** button.</span></span>  
  
4. <span data-ttu-id="06930-115">Düğümleri silmek için silin ve ardından için düğümü seçin **Sil** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="06930-115">To delete nodes, select the node to delete and then click the **Delete** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06930-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06930-116">See also</span></span>

- [<span data-ttu-id="06930-117">TreeView Denetimi</span><span class="sxs-lookup"><span data-stu-id="06930-117">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="06930-118">TreeView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="06930-118">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="06930-119">Nasıl yapılır: Windows Forms TreeView denetimi için simgeler ayarlama</span><span class="sxs-lookup"><span data-stu-id="06930-119">How to: Set Icons for the Windows Forms TreeView Control</span></span>](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="06930-120">Nasıl yapılır: Bir Windows Forms TreeView denetiminin tüm düğümlerinde yineleme</span><span class="sxs-lookup"><span data-stu-id="06930-120">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="06930-121">Nasıl yapılır: Hangi TreeView düğümüne tıklandığını belirleme</span><span class="sxs-lookup"><span data-stu-id="06930-121">How to: Determine Which TreeView Node Was Clicked</span></span>](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="06930-122">Nasıl yapılır: Bir TreeView veya ListView denetimi (Windows Forms) özel bilgi ekleme</span><span class="sxs-lookup"><span data-stu-id="06930-122">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
