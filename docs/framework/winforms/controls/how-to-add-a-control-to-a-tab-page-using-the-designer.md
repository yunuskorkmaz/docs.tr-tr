---
title: "Nasıl yapılır: Tasarımcı Kullanarak bir Sekme Sayfasına Denetim Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TabPage control
- tab controls [Windows Forms], tab order
- tab pages [Windows Forms], adding controls
ms.assetid: 7ee734e1-e31e-4ed0-bbc0-a7e8a1f20fef
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b5efe73f9d8ae2621cca075f77051cb9c7402e57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-a-control-to-a-tab-page-using-the-designer"></a><span data-ttu-id="f525d-102">Nasıl yapılır: Tasarımcı Kullanarak bir Sekme Sayfasına Denetim Ekleme</span><span class="sxs-lookup"><span data-stu-id="f525d-102">How to: Add a Control to a Tab Page Using the Designer</span></span>
<span data-ttu-id="f525d-103">Windows Forms kullanımını <xref:System.Windows.Forms.TabControl> düzenli bir şekilde diğer denetimleri görüntülemektir.</span><span class="sxs-lookup"><span data-stu-id="f525d-103">The use of the Windows Forms <xref:System.Windows.Forms.TabControl> is to display other controls in an organized fashion.</span></span> <span data-ttu-id="f525d-104">Bir resmi bir sekme sayfası ana bölümü görüntülemek için bu yönergeleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="f525d-104">You can use these instructions to display a picture on the main part of a tab page.</span></span> <span data-ttu-id="f525d-105">Simge bir sekme sayfası etiket parçası ekleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms Tabcontrol'nin görünüşünü değiştirme](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md).</span><span class="sxs-lookup"><span data-stu-id="f525d-105">For information about adding an icon to the label part of a tab page, see [How to: Change the Appearance of the Windows Forms TabControl](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md).</span></span>  
  
 <span data-ttu-id="f525d-106">Aşağıdaki yordam gerektiren bir **Windows uygulaması** içeren bir form ile proje bir <xref:System.Windows.Forms.TabControl> denetim.</span><span class="sxs-lookup"><span data-stu-id="f525d-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.TabControl> control.</span></span> <span data-ttu-id="f525d-107">Böyle bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) ve [nasıl yapılır: Windows Forms denetimlerine ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="f525d-107">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f525d-108">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="f525d-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="f525d-109">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="f525d-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="f525d-110">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="f525d-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-a-control-using-the-designer"></a><span data-ttu-id="f525d-111">Tasarımcı kullanarak bir denetim eklemek için</span><span class="sxs-lookup"><span data-stu-id="f525d-111">To add a control using the designer</span></span>  
  
1.  <span data-ttu-id="f525d-112">En üstte görünmesi uygun sekme sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f525d-112">Click the appropriate tab page so that it appears on top.</span></span>  
  
2.  <span data-ttu-id="f525d-113">Sekme sayfasına denetim çizin.</span><span class="sxs-lookup"><span data-stu-id="f525d-113">Draw the control on the tab page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f525d-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f525d-114">See Also</span></span>  
 [<span data-ttu-id="f525d-115">TabControl denetimi</span><span class="sxs-lookup"><span data-stu-id="f525d-115">TabControl Control</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)  
 [<span data-ttu-id="f525d-116">TabControl denetimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="f525d-116">TabControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [<span data-ttu-id="f525d-117">Nasıl yapılır: Windows Forms Tabcontrol'nin görünüşünü değiştirme</span><span class="sxs-lookup"><span data-stu-id="f525d-117">How to: Change the Appearance of the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)  
 [<span data-ttu-id="f525d-118">Nasıl yapılır: sekme sayfalarını devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="f525d-118">How to: Disable Tab Pages</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 [<span data-ttu-id="f525d-119">Nasıl yapılır: Windows Forms TabControl ile sekme ekleme ve kaldırma</span><span class="sxs-lookup"><span data-stu-id="f525d-119">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
