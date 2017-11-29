---
title: "Nasıl yapılır: Tasarımcı Kullanarak Windows Formları ListView Denetimindeki Öğeleri Gruplandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 97c9dc3a12227d3c9bfd64c97be61e69b50d2bbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="5ae0f-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Formları ListView Denetimindeki Öğeleri Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="5ae0f-102">How to: Group Items in a Windows Forms ListView Control Using the Designer</span></span>
<span data-ttu-id="5ae0f-103">Gruplandırma özelliğini de <xref:System.Windows.Forms.ListView> denetimi ilgili öğeleri kümesi gruplarında görüntülemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="5ae0f-103">The grouping feature of the <xref:System.Windows.Forms.ListView> control enables you to display related sets of items in groups.</span></span> <span data-ttu-id="5ae0f-104">Bu gruplar ekranda grup başlıklarını içeren yatay grup üstbilgileri tarafından ayrılır.</span><span class="sxs-lookup"><span data-stu-id="5ae0f-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="5ae0f-105">Kullanabileceğiniz <xref:System.Windows.Forms.ListView> öğeleri alfabetik olarak tarihe ya da diğer bir mantıksal gruplandırma göre gruplandırarak büyük listelerini daha kolay gezinme olmak için grupları.</span><span class="sxs-lookup"><span data-stu-id="5ae0f-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="5ae0f-106">Aşağıdaki resimde gruplandırılmış bazı öğeler gösterilir.</span><span class="sxs-lookup"><span data-stu-id="5ae0f-106">The following image shows some grouped items.</span></span>  
  
 <span data-ttu-id="5ae0f-107">![ListView grupları](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")</span><span class="sxs-lookup"><span data-stu-id="5ae0f-107">![ListView Groups](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")</span></span>  
  
 <span data-ttu-id="5ae0f-108">Aşağıdaki yordam gerektiren bir **Windows uygulaması** içeren bir form ile proje bir <xref:System.Windows.Forms.ListView> denetim.</span><span class="sxs-lookup"><span data-stu-id="5ae0f-108">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="5ae0f-109">Böyle bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) ve [nasıl yapılır: Windows Forms denetimlerine ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="5ae0f-109">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
 <span data-ttu-id="5ae0f-110">Gruplandırma etkinleştirmek için önce bir veya daha fazla oluşturmalısınız <xref:System.Windows.Forms.ListViewGroup> nesneleri Tasarımcısı'nda veya program aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="5ae0f-110">To enable grouping, you must first create one or more <xref:System.Windows.Forms.ListViewGroup> objects either in the designer or programmatically.</span></span> <span data-ttu-id="5ae0f-111">Bir grubu oluşturulduktan sonra öğeleri atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5ae0f-111">Once a group has been defined, you can assign items to it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5ae0f-112"><xref:System.Windows.Forms.ListView>gruplar yalnızca [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] uygulamanızı çağırdığında <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5ae0f-112"><xref:System.Windows.Forms.ListView> groups are available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5ae0f-113">Önceki işletim sistemlerinde gruplarına ilgili herhangi bir kod hiçbir etkisi olmaz ve grupları görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="5ae0f-113">On earlier operating systems, any code relating to groups has no effect and the groups will not appear.</span></span> <span data-ttu-id="5ae0f-114">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5ae0f-114">For more information, see <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span></span>  
>   
>  <span data-ttu-id="5ae0f-115">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="5ae0f-115">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="5ae0f-116">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="5ae0f-116">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="5ae0f-117">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="5ae0f-117">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-or-remove-groups-in-the-designer"></a><span data-ttu-id="5ae0f-118">Eklemek veya Tasarımcısı'nda grupları kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="5ae0f-118">To add or remove groups in the designer</span></span>  
  
1.  <span data-ttu-id="5ae0f-119">İçinde **özellikleri** penceresinde tıklatın **üç nokta** (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) düğmesine <xref:System.Windows.Forms.ListView.Groups%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="5ae0f-119">In the **Properties** window, click the **Ellipsis** (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button next to the <xref:System.Windows.Forms.ListView.Groups%2A> property.</span></span>  
  
     <span data-ttu-id="5ae0f-120">**ListViewGroup Koleksiyonu Düzenleyicisi** görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5ae0f-120">The **ListViewGroup Collection Editor** appears.</span></span>  
  
2.  <span data-ttu-id="5ae0f-121">Bir grup eklemek için tıklatın **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="5ae0f-121">To add a group, click the **Add** button.</span></span> <span data-ttu-id="5ae0f-122">Yeni grubu özelliklerini gibi daha sonra ayarlamak <xref:System.Windows.Forms.ListViewGroup.Header%2A> ve <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="5ae0f-122">You can then set properties of the new group, such as the <xref:System.Windows.Forms.ListViewGroup.Header%2A> and <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> properties.</span></span> <span data-ttu-id="5ae0f-123">Bir grubu kaldırmak için onu seçin ve tıklatın **kaldırmak** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="5ae0f-123">To remove a group, select it and click the **Remove** button.</span></span>  
  
### <a name="to-assign-items-to-groups-in-the-designer"></a><span data-ttu-id="5ae0f-124">Tasarımcıda gruplarına öğeleri atamak için</span><span class="sxs-lookup"><span data-stu-id="5ae0f-124">To assign items to groups in the designer</span></span>  
  
1.  <span data-ttu-id="5ae0f-125">İçinde **özellikleri** penceresinde tıklatın **üç nokta** (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) düğmesine <xref:System.Windows.Forms.ListView.Items%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="5ae0f-125">In the **Properties** window, click the **Ellipsis** (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button next to the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>  
  
     <span data-ttu-id="5ae0f-126">**ListViewItem Koleksiyonu Düzenleyicisi** görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5ae0f-126">The **ListViewItem Collection Editor** appears.</span></span>  
  
2.  <span data-ttu-id="5ae0f-127">Yeni bir öğe eklemek için tıklatın **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="5ae0f-127">To add a new item, click the **Add** button.</span></span> <span data-ttu-id="5ae0f-128">Yeni öğe özelliklerini gibi daha sonra ayarlamak <xref:System.Windows.Forms.ListViewItem.Text%2A> ve <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="5ae0f-128">You can then set properties of the new item, such as the <xref:System.Windows.Forms.ListViewItem.Text%2A> and <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> properties.</span></span>  
  
3.  <span data-ttu-id="5ae0f-129">Seçin <xref:System.Windows.Forms.ListViewItem.Group%2A> özelliği ve aşağı açılan listeden bir grup seçin.</span><span class="sxs-lookup"><span data-stu-id="5ae0f-129">Select the <xref:System.Windows.Forms.ListViewItem.Group%2A> property and choose a group from the drop-down list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ae0f-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5ae0f-130">See Also</span></span>  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.Groups%2A>  
 <xref:System.Windows.Forms.ListViewGroup>  
 [<span data-ttu-id="5ae0f-131">ListView denetimi</span><span class="sxs-lookup"><span data-stu-id="5ae0f-131">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [<span data-ttu-id="5ae0f-132">ListView denetimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="5ae0f-132">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="5ae0f-133">Windows XP özellikleri ve Windows Forms denetimleri</span><span class="sxs-lookup"><span data-stu-id="5ae0f-133">Windows XP Features and Windows Forms Controls</span></span>](http://msdn.microsoft.com/en-us/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 [<span data-ttu-id="5ae0f-134">Nasıl yapılır: ekleme ve kaldırma öğeleri Windows Forms ListView denetimi</span><span class="sxs-lookup"><span data-stu-id="5ae0f-134">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
