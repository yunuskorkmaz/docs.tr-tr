---
title: '1. Görev: Yeni bir Windows Presentation Foundation uygulaması oluşturma'
ms.date: 03/30/2017
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
ms.openlocfilehash: 533b4a1030ab5f47eb96ca62dc2805eae7933b9b
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711904"
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a><span data-ttu-id="ba4c3-102">1. Görev: Yeni bir Windows Presentation Foundation uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="ba4c3-102">Task 1: Create a New Windows Presentation Foundation Application</span></span>
<span data-ttu-id="ba4c3-103">Bu görevde, WPF uygulaması Visual Studio şablonu kullanarak boş bir Windows Presentation Foundation (WPF) uygulaması oluşturun ve uygun başvuruları eklemek [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] iş akışı bütünleştirilmiş kodları.</span><span class="sxs-lookup"><span data-stu-id="ba4c3-103">In this task, you will create an empty Windows Presentation Foundation (WPF) application by using the WPF Application Visual Studio template and add references to the appropriate [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow assemblies.</span></span>  
  
### <a name="to-create-the-wpf-application-project"></a><span data-ttu-id="ba4c3-104">WPF uygulaması projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="ba4c3-104">To create the WPF Application project</span></span>  
  
1.  <span data-ttu-id="ba4c3-105">Visual Studio'yu açın ve **dosya** menüsünde **yeni**ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="ba4c3-105">Open Visual Studio and on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="ba4c3-106">İçinde **yeni proje** iletişim kutusunda, ya da seçin **Visual C#**  veya **Visual Basic** gelen **yüklü şablonlar** sol bölmesi kutunun yanında.</span><span class="sxs-lookup"><span data-stu-id="ba4c3-106">In the **New Project** dialog box, select either **Visual C#** or **Visual Basic** from the **Installed Templates** pane on the left side of the box.</span></span> <span data-ttu-id="ba4c3-107">Tercih ettiğiniz dili görünmüyorsa altına bakın **diğer diller**.</span><span class="sxs-lookup"><span data-stu-id="ba4c3-107">If the language of your choice does not appear, look under **Other Languages**.</span></span>  
  
3.  <span data-ttu-id="ba4c3-108">Seçin **Windows** içinde **yüklü şablonlar** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="ba4c3-108">Select **Windows** in the **Installed Templates** pane.</span></span>  
  
4.  <span data-ttu-id="ba4c3-109">Üst bölmede onaylayın (varsayılan değer) **.NET Framework 4** aşağı açılan liste kutusunda seçili ve ardından **WPF uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="ba4c3-109">In the top pane, confirm that (the default value) **.NET Framework 4** has been selected in the drop-down list box, and then select **WPF Application**.</span></span>  
  
5.  <span data-ttu-id="ba4c3-110">Proje adını ayarlayın **HostingApplication** pencerenin alt kısmındaki.</span><span class="sxs-lookup"><span data-stu-id="ba4c3-110">Set the name of the project to **HostingApplication** at the bottom of the window.</span></span>  
  
6.  <span data-ttu-id="ba4c3-111">Çözüm adı kümesine **RehostingTheDesigner**.</span><span class="sxs-lookup"><span data-stu-id="ba4c3-111">Set the solution name to **RehostingTheDesigner**.</span></span>  
  
7.  <span data-ttu-id="ba4c3-112">Tıklayın **Tamam** uygulaması projesi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="ba4c3-112">Click **OK** to create the application project.</span></span> <span data-ttu-id="ba4c3-113">Visual Studio, uygulamanız için temel bir WPF kullanıcı Arabirimi oluşturur ve uygun XAML ve arka plan kod dosyalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="ba4c3-113">Visual Studio creates a basic WPF UI for your application and includes the appropriate XAML and code-behind files.</span></span>  
  
8.  <span data-ttu-id="ba4c3-114">Başvuruları Ekle **WorkflowModel** derlemeler.</span><span class="sxs-lookup"><span data-stu-id="ba4c3-114">Add references to **WorkflowModel** assemblies.</span></span> <span data-ttu-id="ba4c3-115">Bunu yapmak için **Çözüm Gezgini**, sağ **HostingApplication** seçin ve proje **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="ba4c3-115">To do this, in **Solution Explorer**, right-click the **HostingApplication** project and select **Add Reference**.</span></span>  
  
9. <span data-ttu-id="ba4c3-116">İçinde **Başvuru Ekle** iletişim kutusu, tıklayın **.NET** sekmesinde, CTRL tuşunu basılı tutun, aşağıdaki derlemeler seçin ve ardından **Tamam**:</span><span class="sxs-lookup"><span data-stu-id="ba4c3-116">In the **Add Reference** dialog box, click the **.NET** tab, hold down the CTRL key, select the following assemblies, and then click **OK**:</span></span>  
  
    -   <span data-ttu-id="ba4c3-117">System.Activities</span><span class="sxs-lookup"><span data-stu-id="ba4c3-117">System.Activities</span></span>  
  
    -   <span data-ttu-id="ba4c3-118">System.Activities.Presentation</span><span class="sxs-lookup"><span data-stu-id="ba4c3-118">System.Activities.Presentation</span></span>  
  
    -   <span data-ttu-id="ba4c3-119">System.Activities.Core.Presentation</span><span class="sxs-lookup"><span data-stu-id="ba4c3-119">System.Activities.Core.Presentation</span></span>  
  
10. <span data-ttu-id="ba4c3-120">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="ba4c3-120">Click **OK**.</span></span>  
  
11. <span data-ttu-id="ba4c3-121">Bkz: [görev 2: İş akışı tasarımcısını barındırma](task-2-host-the-workflow-designer.md) nasıl iş akışı Tasarımcısı tasarım tuvali barındıracağınızı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="ba4c3-121">See [Task 2: Host the Workflow Designer](task-2-host-the-workflow-designer.md) to learn how to host the workflow designer design canvas.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba4c3-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba4c3-122">See also</span></span>
- [<span data-ttu-id="ba4c3-123">İş Akışı Tasarımcısını Yeniden Barındırma</span><span class="sxs-lookup"><span data-stu-id="ba4c3-123">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)
- [<span data-ttu-id="ba4c3-124">2. Görev: İş akışı tasarımcısını barındırma</span><span class="sxs-lookup"><span data-stu-id="ba4c3-124">Task 2: Host the Workflow Designer</span></span>](task-2-host-the-workflow-designer.md)
