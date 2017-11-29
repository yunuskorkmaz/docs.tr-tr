---
title: "Nasıl yapılır: Tasarımcı Kullanarak Windows Formları TabControl ile Sekme Ekleme ve Kaldırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tabs [Windows Forms], removing from pages
- TabPage control
- TabPage control [Windows Forms], adding and removing tabs
- tabs [Windows Forms], adding to pages
- tab pages
ms.assetid: 480633db-413a-45d2-9c8f-0427cc13adbe
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 02bcf434baee0c27ca2674817df0e4033effb125
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol-using-the-designer"></a><span data-ttu-id="66ade-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Formları TabControl ile Sekme Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="66ade-102">How to: Add and Remove Tabs with the Windows Forms TabControl Using the Designer</span></span>
<span data-ttu-id="66ade-103">Yerleştirdiğinizde bir <xref:System.Windows.Forms.TabControl> denetim formunuzda, iki sekme varsayılan olarak içerir.</span><span class="sxs-lookup"><span data-stu-id="66ade-103">When you place a <xref:System.Windows.Forms.TabControl> control on your form, it contains two tabs by default.</span></span> <span data-ttu-id="66ade-104">Ekleyebilir veya sekmeler Tasarımcısı'nı kullanarak kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66ade-104">You can add or remove tabs using the designer.</span></span>  
  
 <span data-ttu-id="66ade-105">Aşağıdaki yordam gerektiren bir **Windows uygulaması** içeren bir form ile proje bir <xref:System.Windows.Forms.TabControl> denetim.</span><span class="sxs-lookup"><span data-stu-id="66ade-105">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.TabControl> control.</span></span> <span data-ttu-id="66ade-106">Böyle bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) ve [nasıl yapılır: Windows Forms denetimlerine ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="66ade-106">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="66ade-107">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="66ade-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="66ade-108">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="66ade-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="66ade-109">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="66ade-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-or-remove-a-tab-using-the-designer"></a><span data-ttu-id="66ade-110">Eklemek veya Tasarımcısı'nı kullanarak bir sekme kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="66ade-110">To add or remove a tab using the designer</span></span>  
  
-   <span data-ttu-id="66ade-111">Denetimin akıllı etiketler üzerinde tıklatın **sekmesi Ekle** veya **sekmesi Kaldır**</span><span class="sxs-lookup"><span data-stu-id="66ade-111">On the control's smart tag, click **Add Tab** or **Remove Tab**</span></span>  
  
     <span data-ttu-id="66ade-112">veya</span><span class="sxs-lookup"><span data-stu-id="66ade-112">-or-</span></span>  
  
     <span data-ttu-id="66ade-113">İçinde **özellikleri** penceresinde tıklatın **üç nokta** düğmesi (![VisualStudioEllipsesButton ekran görüntüsü](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) yanındaki <xref:System.Windows.Forms.TabControl.TabPages%2A> açmak için özellik **TabPage Koleksiyonu Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="66ade-113">In the **Properties** window, click the **Ellipsis** button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.TabControl.TabPages%2A> property to open the **TabPage Collection Editor**.</span></span> <span data-ttu-id="66ade-114">Tıklatın **Ekle** veya **kaldırmak** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="66ade-114">Click the **Add** or **Remove** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66ade-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="66ade-115">See Also</span></span>  
 [<span data-ttu-id="66ade-116">TabControl denetimi</span><span class="sxs-lookup"><span data-stu-id="66ade-116">TabControl Control</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)  
 [<span data-ttu-id="66ade-117">TabControl denetimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="66ade-117">TabControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [<span data-ttu-id="66ade-118">Nasıl yapılır: sekme sayfasına denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="66ade-118">How to: Add a Control to a Tab Page</span></span>](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)  
 [<span data-ttu-id="66ade-119">Nasıl yapılır: sekme sayfalarını devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="66ade-119">How to: Disable Tab Pages</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 [<span data-ttu-id="66ade-120">Nasıl yapılır: Windows Forms Tabcontrol'nin görünüşünü değiştirme</span><span class="sxs-lookup"><span data-stu-id="66ade-120">How to: Change the Appearance of the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
