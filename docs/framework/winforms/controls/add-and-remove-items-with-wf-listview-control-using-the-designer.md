---
title: 'Nasıl yapılır: Tasarımcı kullanarak Windows Forms ListView denetimi ile öğe ekleyip'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], populating
- ListView control [Windows Forms], adding list items
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
ms.openlocfilehash: 6343000b5060c3b1e98e68b1aa7e84bfb3e817b7
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56303404"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="4bbcf-102">Nasıl yapılır: Tasarımcı kullanarak Windows Forms ListView denetimi ile öğe ekleyip</span><span class="sxs-lookup"><span data-stu-id="4bbcf-102">How to: Add and Remove Items with the Windows Forms ListView Control Using the Designer</span></span>
<span data-ttu-id="4bbcf-103">Bir Windows Forms için bir öğe ekleme işlemini <xref:System.Windows.Forms.ListView> öncelikle, bulunan öğeyi belirten ve Özellikler atayarak denetimi oluşur.</span><span class="sxs-lookup"><span data-stu-id="4bbcf-103">The process of adding an item to a Windows Forms <xref:System.Windows.Forms.ListView> control consists primarily of specifying the item and assigning properties to it.</span></span> <span data-ttu-id="4bbcf-104">Liste öğe ekleme veya kaldırma herhangi bir zamanda gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="4bbcf-104">Adding or removing list items can be done at any time.</span></span>  
  
 <span data-ttu-id="4bbcf-105">Aşağıdaki yordam gerektirir bir **Windows uygulama** proje içeren bir form içeren bir <xref:System.Windows.Forms.ListView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="4bbcf-105">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="4bbcf-106">Bu tür bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir Windows Forms uygulaması projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms'a denetimler ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="4bbcf-106">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4bbcf-107">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="4bbcf-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="4bbcf-108">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="4bbcf-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="4bbcf-109">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="4bbcf-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-or-remove-items-using-the-designer"></a><span data-ttu-id="4bbcf-110">Tasarımcı kullanarak bir öğe eklemek veya kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="4bbcf-110">To add or remove items using the designer</span></span>  
  
1.  <span data-ttu-id="4bbcf-111">Seçin <xref:System.Windows.Forms.ListView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="4bbcf-111">Select the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
2.  <span data-ttu-id="4bbcf-112">İçinde **özellikleri** penceresinde tıklayın **üç nokta** (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) düğmesinin yanındaki <xref:System.Windows.Forms.ListView.Items%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="4bbcf-112">In the **Properties** window, click the **Ellipsis** (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button next to the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>  
  
     <span data-ttu-id="4bbcf-113">**ListViewItem Koleksiyonu Düzenleyicisi** görünür.</span><span class="sxs-lookup"><span data-stu-id="4bbcf-113">The **ListViewItem Collection Editor** appears.</span></span>  
  
3.  <span data-ttu-id="4bbcf-114">Bir öğe eklemek için tıklayın **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="4bbcf-114">To add an item, click the **Add** button.</span></span> <span data-ttu-id="4bbcf-115">Yeni öğenin özelliklerini aşağıdaki gibi ayarlayabilirsiniz <xref:System.Windows.Forms.ListView.Text%2A> ve <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="4bbcf-115">You can then set properties of the new item, such as the <xref:System.Windows.Forms.ListView.Text%2A> and <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> properties.</span></span>  
  
4.  <span data-ttu-id="4bbcf-116">Bir öğe kaldırmak için onu seçin ve **Kaldır** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="4bbcf-116">To remove an item, select it and click the **Remove** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bbcf-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4bbcf-117">See also</span></span>
- [<span data-ttu-id="4bbcf-118">ListView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4bbcf-118">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
- [<span data-ttu-id="4bbcf-119">Nasıl yapılır: Windows Forms ListView denetimine sütun ekleme</span><span class="sxs-lookup"><span data-stu-id="4bbcf-119">How to: Add Columns to the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)
- [<span data-ttu-id="4bbcf-120">Nasıl yapılır: Windows Forms ListView denetimiyle sütunlardaki alt öğeleri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="4bbcf-120">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="4bbcf-121">Nasıl yapılır: Windows Forms ListView denetimi için simgeler görüntüleme</span><span class="sxs-lookup"><span data-stu-id="4bbcf-121">How to: Display Icons for the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)
- [<span data-ttu-id="4bbcf-122">Nasıl yapılır: Bir TreeView veya ListView denetimi (Windows Forms) özel bilgi ekleme</span><span class="sxs-lookup"><span data-stu-id="4bbcf-122">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [<span data-ttu-id="4bbcf-123">Nasıl yapılır: Bir Windows Forms ListView denetimi içinde öğeleri gruplandırma</span><span class="sxs-lookup"><span data-stu-id="4bbcf-123">How to: Group Items in a Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-group-items-in-a-windows-forms-listview-control.md)
