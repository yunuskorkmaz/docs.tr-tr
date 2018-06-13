---
title: 'Görev 1: yeni bir Windows Presentation Foundation uygulaması oluşturma'
ms.date: 03/30/2017
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
ms.openlocfilehash: 5576d6f893aa405d454758387334b85a473b0c73
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517955"
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a><span data-ttu-id="2bb4c-102">Görev 1: yeni bir Windows Presentation Foundation uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="2bb4c-102">Task 1: Create a New Windows Presentation Foundation Application</span></span>
<span data-ttu-id="2bb4c-103">Bu görevde, WPF uygulaması Visual Studio şablonu kullanarak boş bir Windows Presentation Foundation (WPF) uygulaması oluşturacak ve uygun başvurular ekleyin [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] iş akışı derlemeler.</span><span class="sxs-lookup"><span data-stu-id="2bb4c-103">In this task, you will create an empty Windows Presentation Foundation (WPF) application by using the WPF Application Visual Studio template and add references to the appropriate [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow assemblies.</span></span>  
  
### <a name="to-create-the-wpf-application-project"></a><span data-ttu-id="2bb4c-104">WPF uygulaması projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="2bb4c-104">To create the WPF Application project</span></span>  
  
1.  <span data-ttu-id="2bb4c-105">Visual Studio'yu açın ve **dosya** menüsündeki **yeni**ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="2bb4c-105">Open Visual Studio and on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="2bb4c-106">İçinde **yeni proje** iletişim kutusunda, şunlardan birini seçin **Visual C#** veya **Visual Basic** gelen **yüklü şablonlar** sol tarafındaki bölmesi bir kutu.</span><span class="sxs-lookup"><span data-stu-id="2bb4c-106">In the **New Project** dialog box, select either **Visual C#** or **Visual Basic** from the **Installed Templates** pane on the left side of the box.</span></span> <span data-ttu-id="2bb4c-107">Tercih ettiğiniz dili görünmüyorsa arayın **diğer diller**.</span><span class="sxs-lookup"><span data-stu-id="2bb4c-107">If the language of your choice does not appear, look under **Other Languages**.</span></span>  
  
3.  <span data-ttu-id="2bb4c-108">Seçin **Windows** içinde **yüklü şablonlar** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="2bb4c-108">Select **Windows** in the **Installed Templates** pane.</span></span>  
  
4.  <span data-ttu-id="2bb4c-109">Üst bölmede onaylayın (varsayılan değer) **.NET Framework 4** aşağı açılan liste kutusunda seçili ve ardından olmamıştı **WPF uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="2bb4c-109">In the top pane, confirm that (the default value) **.NET Framework 4** has been selected in the drop-down list box, and then select **WPF Application**.</span></span>  
  
5.  <span data-ttu-id="2bb4c-110">Projeye adını ayarlamak **HostingApplication** pencerenin altındaki.</span><span class="sxs-lookup"><span data-stu-id="2bb4c-110">Set the name of the project to **HostingApplication** at the bottom of the window.</span></span>  
  
6.  <span data-ttu-id="2bb4c-111">Çözüm adı ayarlamak **RehostingTheDesigner**.</span><span class="sxs-lookup"><span data-stu-id="2bb4c-111">Set the solution name to **RehostingTheDesigner**.</span></span>  
  
7.  <span data-ttu-id="2bb4c-112">Tıklatın **Tamam** uygulama projesi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="2bb4c-112">Click **OK** to create the application project.</span></span> <span data-ttu-id="2bb4c-113">Visual Studio, uygulamanız için temel bir WPF UI oluşturur ve uygun XAML ve arka plan kodu dosyalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="2bb4c-113">Visual Studio creates a basic WPF UI for your application and includes the appropriate XAML and code-behind files.</span></span>  
  
8.  <span data-ttu-id="2bb4c-114">Başvurular ekleyin **WorkflowModel** derlemeler.</span><span class="sxs-lookup"><span data-stu-id="2bb4c-114">Add references to **WorkflowModel** assemblies.</span></span> <span data-ttu-id="2bb4c-115">Bunu yapmak için **Çözüm Gezgini**, sağ **HostingApplication** proje ve seçin **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="2bb4c-115">To do this, in **Solution Explorer**, right-click the **HostingApplication** project and select **Add Reference**.</span></span>  
  
9. <span data-ttu-id="2bb4c-116">İçinde **Başvuru Ekle** iletişim kutusu, tıklatın **.NET** sekmesinde, CTRL tuşunu basılı tutun, aşağıdaki derlemeleri seçin ve ardından **Tamam**:</span><span class="sxs-lookup"><span data-stu-id="2bb4c-116">In the **Add Reference** dialog box, click the **.NET** tab, hold down the CTRL key, select the following assemblies, and then click **OK**:</span></span>  
  
    -   <span data-ttu-id="2bb4c-117">System.Activities</span><span class="sxs-lookup"><span data-stu-id="2bb4c-117">System.Activities</span></span>  
  
    -   <span data-ttu-id="2bb4c-118">System.Activities.Presentation</span><span class="sxs-lookup"><span data-stu-id="2bb4c-118">System.Activities.Presentation</span></span>  
  
    -   <span data-ttu-id="2bb4c-119">System.Activities.Core.Presentation</span><span class="sxs-lookup"><span data-stu-id="2bb4c-119">System.Activities.Core.Presentation</span></span>  
  
10. <span data-ttu-id="2bb4c-120">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="2bb4c-120">Click **OK**.</span></span>  
  
11. <span data-ttu-id="2bb4c-121">Bkz: [görev 2: İş Akışı Tasarımcısı konak](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md) iş akışı Tasarımcısı tasarım tuvale barındırmak hakkında bilgi edinmek için.</span><span class="sxs-lookup"><span data-stu-id="2bb4c-121">See [Task 2: Host the Workflow Designer](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md) to learn how to host the workflow designer design canvas.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bb4c-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2bb4c-122">See Also</span></span>  
 [<span data-ttu-id="2bb4c-123">İş Akışı Tasarımcısını Yeniden Barındırma</span><span class="sxs-lookup"><span data-stu-id="2bb4c-123">Rehosting the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [<span data-ttu-id="2bb4c-124">Görev 2: İş Akışı Tasarımcısını Barındırma</span><span class="sxs-lookup"><span data-stu-id="2bb4c-124">Task 2: Host the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)
