---
title: "Görev 1: yeni bir Windows Presentation Foundation uygulaması oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bfebf11d66ded668d7c0892d11adde76e0a42c01
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a><span data-ttu-id="6cfd0-102">Görev 1: yeni bir Windows Presentation Foundation uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="6cfd0-102">Task 1: Create a New Windows Presentation Foundation Application</span></span>
<span data-ttu-id="6cfd0-103">Bu görevde, boş bir oluşturacak [!INCLUDE[avalon1](../../../includes/avalon1-md.md)] WPF uygulaması Visual Studio şablonunu kullanarak uygulama ve uygun başvurular ekleyin [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] iş akışı derlemeler.</span><span class="sxs-lookup"><span data-stu-id="6cfd0-103">In this task, you will create an empty [!INCLUDE[avalon1](../../../includes/avalon1-md.md)] application by using the WPF Application Visual Studio template and add references to the appropriate [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow assemblies.</span></span>  
  
### <a name="to-create-the-wpf-application-project"></a><span data-ttu-id="6cfd0-104">WPF uygulaması projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="6cfd0-104">To create the WPF Application project</span></span>  
  
1.  <span data-ttu-id="6cfd0-105">Açık [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] ve **dosya** menüsündeki **yeni**ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="6cfd0-105">Open [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] and on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="6cfd0-106">İçinde **yeni proje** iletişim kutusunda, şunlardan birini seçin **Visual C#** veya **Visual Basic** gelen **yüklü şablonlar** sol tarafındaki bölmesi bir kutu.</span><span class="sxs-lookup"><span data-stu-id="6cfd0-106">In the **New Project** dialog box, select either **Visual C#** or **Visual Basic** from the **Installed Templates** pane on the left side of the box.</span></span> <span data-ttu-id="6cfd0-107">Tercih ettiğiniz dili görünmüyorsa arayın **diğer diller**.</span><span class="sxs-lookup"><span data-stu-id="6cfd0-107">If the language of your choice does not appear, look under **Other Languages**.</span></span>  
  
3.  <span data-ttu-id="6cfd0-108">Seçin **Windows** içinde **yüklü şablonlar** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="6cfd0-108">Select **Windows** in the **Installed Templates** pane.</span></span>  
  
4.  <span data-ttu-id="6cfd0-109">Üst bölmede onaylayın (varsayılan değer) **.NET Framework 4** aşağı açılan liste kutusunda seçili ve ardından olmamıştı **WPF uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="6cfd0-109">In the top pane, confirm that (the default value) **.NET Framework 4** has been selected in the drop-down list box, and then select **WPF Application**.</span></span>  
  
5.  <span data-ttu-id="6cfd0-110">Projeye adını ayarlamak **HostingApplication** pencerenin altındaki.</span><span class="sxs-lookup"><span data-stu-id="6cfd0-110">Set the name of the project to **HostingApplication** at the bottom of the window.</span></span>  
  
6.  <span data-ttu-id="6cfd0-111">Çözüm adı ayarlamak **RehostingTheDesigner**.</span><span class="sxs-lookup"><span data-stu-id="6cfd0-111">Set the solution name to **RehostingTheDesigner**.</span></span>  
  
7.  <span data-ttu-id="6cfd0-112">Tıklatın **Tamam** uygulama projesi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="6cfd0-112">Click **OK** to create the application project.</span></span> [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)]<span data-ttu-id="6cfd0-113">Uygulamanız için temel bir WPF UI oluşturur ve uygun XAML ve arka plan kodu dosyalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="6cfd0-113"> creates a basic WPF UI for your application and includes the appropriate XAML and code-behind files.</span></span>  
  
8.  <span data-ttu-id="6cfd0-114">Başvurular ekleyin **WorkflowModel** derlemeler.</span><span class="sxs-lookup"><span data-stu-id="6cfd0-114">Add references to **WorkflowModel** assemblies.</span></span> <span data-ttu-id="6cfd0-115">Bunu yapmak için **Çözüm Gezgini**, sağ **HostingApplication** proje ve seçin **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="6cfd0-115">To do this, in **Solution Explorer**, right-click the **HostingApplication** project and select **Add Reference**.</span></span>  
  
9. <span data-ttu-id="6cfd0-116">İçinde **Başvuru Ekle** iletişim kutusu, tıklatın **.NET** sekmesinde, CTRL tuşunu basılı tutun, aşağıdaki derlemeleri seçin ve ardından **Tamam**:</span><span class="sxs-lookup"><span data-stu-id="6cfd0-116">In the **Add Reference** dialog box, click the **.NET** tab, hold down the CTRL key, select the following assemblies, and then click **OK**:</span></span>  
  
    -   <span data-ttu-id="6cfd0-117">System.Activities</span><span class="sxs-lookup"><span data-stu-id="6cfd0-117">System.Activities</span></span>  
  
    -   <span data-ttu-id="6cfd0-118">System.Activities.Presentation</span><span class="sxs-lookup"><span data-stu-id="6cfd0-118">System.Activities.Presentation</span></span>  
  
    -   <span data-ttu-id="6cfd0-119">System.Activities.Core.Presentation</span><span class="sxs-lookup"><span data-stu-id="6cfd0-119">System.Activities.Core.Presentation</span></span>  
  
10. <span data-ttu-id="6cfd0-120">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="6cfd0-120">Click **OK**.</span></span>  
  
11. <span data-ttu-id="6cfd0-121">Bkz: [görev 2: İş Akışı Tasarımcısı konak](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md) iş akışı Tasarımcısı tasarım tuvale barındırmak hakkında bilgi edinmek için.</span><span class="sxs-lookup"><span data-stu-id="6cfd0-121">See [Task 2: Host the Workflow Designer](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md) to learn how to host the workflow designer design canvas.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cfd0-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6cfd0-122">See Also</span></span>  
 [<span data-ttu-id="6cfd0-123">İş Akışı Tasarımcısı yeniden barındırma</span><span class="sxs-lookup"><span data-stu-id="6cfd0-123">Rehosting the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [<span data-ttu-id="6cfd0-124">Görev 2: ana bilgisayar iş akışı Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="6cfd0-124">Task 2: Host the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)
