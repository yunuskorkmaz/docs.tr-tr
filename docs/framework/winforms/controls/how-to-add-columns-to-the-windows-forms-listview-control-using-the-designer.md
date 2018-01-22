---
title: "Nasıl yapılır: Tasarımcı Kullanarak Windows Formları ListView Denetimine Sütunlar Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
ms.assetid: 5b1a8b4d-587e-479a-95c1-f9b90884f13a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 971d3918fd6085bea85e43183ea67745d40e51b8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="ee209-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Formları ListView Denetimine Sütunlar Ekleme</span><span class="sxs-lookup"><span data-stu-id="ee209-102">How to: Add Columns to the Windows Forms ListView Control Using the Designer</span></span>
<span data-ttu-id="ee209-103">Windows Forms <xref:System.Windows.Forms.ListView> denetimi her listesi için birden çok sütun görüntüleyebilir durumlarda öğesi **ayrıntıları** görünümü.</span><span class="sxs-lookup"><span data-stu-id="ee209-103">The Windows Forms <xref:System.Windows.Forms.ListView> control can display multiple columns for each list item when in the **Details** view.</span></span> <span data-ttu-id="ee209-104">Sütunları, çeşitli her liste öğesi hakkında bilgi görüntülemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee209-104">You can use the columns to display several types of information about each list item.</span></span> <span data-ttu-id="ee209-105">Örneğin, dosya adı, dosya türü, boyutu ve dosyanın en son değiştirildiği tarih dosyaların bir listesini görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee209-105">For example, a list of files could display the file name, file type, size, and date the file was last modified.</span></span> <span data-ttu-id="ee209-106">Oluşturulduktan sonra sütun doldurma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms ListView denetimiyle sütunlardaki alt öğeleri görüntüleme](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span><span class="sxs-lookup"><span data-stu-id="ee209-106">For information on populating the columns once they are created, see [How to: Display Subitems in Columns with the Windows Forms ListView Control](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span></span>  
  
 <span data-ttu-id="ee209-107">Aşağıdaki yordam gerektiren bir **Windows uygulaması** içeren bir form ile proje bir <xref:System.Windows.Forms.ListView> denetim.</span><span class="sxs-lookup"><span data-stu-id="ee209-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="ee209-108">Böyle bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) ve [nasıl yapılır: Windows Forms denetimlerine ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="ee209-108">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ee209-109">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="ee209-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="ee209-110">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="ee209-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="ee209-111">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="ee209-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-columns-in-the-designer"></a><span data-ttu-id="ee209-112">Tasarımcıda sütun eklemek için</span><span class="sxs-lookup"><span data-stu-id="ee209-112">To add columns in the designer</span></span>  
  
1.  <span data-ttu-id="ee209-113">İçinde **özellikleri** penceresindeki ayarlayın denetimin <xref:System.Windows.Forms.ListView.View%2A> özelliğine <xref:System.Windows.Forms.View.Details>.</span><span class="sxs-lookup"><span data-stu-id="ee209-113">In the **Properties** window, set the control's <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Details>.</span></span>  
  
2.  <span data-ttu-id="ee209-114">İçinde **özellikleri** penceresinde tıklatın **üç nokta** düğmesi (![VisualStudioEllipsesButton ekran görüntüsü](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) yanındaki <xref:System.Windows.Forms.ListView.Columns%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="ee209-114">In the **Properties** window, click the **Ellipsis** button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.ListView.Columns%2A> property.</span></span>  
  
     <span data-ttu-id="ee209-115">**Sütun üstbilgisi Koleksiyonu Düzenleyicisi** görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ee209-115">The **ColumnHeader Collection Editor** appears.</span></span>  
  
3.  <span data-ttu-id="ee209-116">Kullanım **Ekle** yeni sütun ekleme düğmesi.</span><span class="sxs-lookup"><span data-stu-id="ee209-116">Use the **Add** button to add new columns.</span></span> <span data-ttu-id="ee209-117">Ardından sütun başlığını seçin ve metin (sütun başlığını), metin hizalamasını ve genişlik ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ee209-117">You can then select the column header and set its text (the caption of the column), text alignment, and width.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee209-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ee209-118">See Also</span></span>  
 [<span data-ttu-id="ee209-119">ListView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ee209-119">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="ee209-120">Nasıl yapılır: Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="ee209-120">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="ee209-121">Nasıl yapılır: Windows Forms ListView Denetimiyle Sütunlardaki Alt Öğeleri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="ee209-121">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="ee209-122">Nasıl yapılır: Windows Forms ListView Denetimi için Simgeler Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="ee209-122">How to: Display Icons for the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="ee209-123">Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="ee209-123">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
