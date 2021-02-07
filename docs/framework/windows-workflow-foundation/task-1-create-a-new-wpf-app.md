---
description: 'Daha fazla bilgi: 1. görev: yeni bir Windows Presentation Foundation uygulaması oluşturma'
title: 'Görev 1: Yeni Bir Windows Presentation Foundation Uygulaması Oluşturma'
ms.date: 03/30/2017
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
ms.openlocfilehash: 7bbb49e3d663d1878b2b3e150a24f775eeca0135
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755245"
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a><span data-ttu-id="28e38-103">Görev 1: Yeni Bir Windows Presentation Foundation Uygulaması Oluşturma</span><span class="sxs-lookup"><span data-stu-id="28e38-103">Task 1: Create a New Windows Presentation Foundation Application</span></span>

<span data-ttu-id="28e38-104">Bu görevde, WPF uygulaması Visual Studio şablonunu kullanarak boş bir Windows Presentation Foundation (WPF) uygulaması oluşturacaksınız ve ilgili [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] iş akışı derlemelerine başvurular eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="28e38-104">In this task, you will create an empty Windows Presentation Foundation (WPF) application by using the WPF Application Visual Studio template and add references to the appropriate [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow assemblies.</span></span>  
  
## <a name="to-create-the-wpf-application-project"></a><span data-ttu-id="28e38-105">WPF uygulaması projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="28e38-105">To create the WPF Application project</span></span>

1. <span data-ttu-id="28e38-106">Visual Studio 'Yu açın ve **Dosya** menüsünde **Yeni** üzerine gelin ve ardından **Proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="28e38-106">Open Visual Studio and on the **File** menu, point to **New**, and then click **Project**.</span></span>

2. <span data-ttu-id="28e38-107">**Yeni proje** iletişim kutusunda, kutunun sol tarafındaki **yüklü şablonlar** bölmesinden **Visual C#** veya **Visual Basic** seçin.</span><span class="sxs-lookup"><span data-stu-id="28e38-107">In the **New Project** dialog box, select either **Visual C#** or **Visual Basic** from the **Installed Templates** pane on the left side of the box.</span></span> <span data-ttu-id="28e38-108">Seçtiğiniz dil görünmezse, **diğer diller** bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="28e38-108">If the language of your choice does not appear, look under **Other Languages**.</span></span>

3. <span data-ttu-id="28e38-109">**Yüklü şablonlar** bölmesinde **Windows** ' u seçin.</span><span class="sxs-lookup"><span data-stu-id="28e38-109">Select **Windows** in the **Installed Templates** pane.</span></span>

4. <span data-ttu-id="28e38-110">Üst bölmede, açılan liste kutusunda **.NET Framework 4 ' ün** seçildiğinden emin olun ve ardından **WPF uygulaması**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="28e38-110">In the top pane, confirm that (the default value) **.NET Framework 4** has been selected in the drop-down list box, and then select **WPF Application**.</span></span>

5. <span data-ttu-id="28e38-111">Projenin adını pencerenin alt kısmındaki **HostingApplication** olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="28e38-111">Set the name of the project to **HostingApplication** at the bottom of the window.</span></span>

6. <span data-ttu-id="28e38-112">Çözüm adını **yeniden hostingolarak** ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="28e38-112">Set the solution name to **RehostingTheDesigner**.</span></span>

7. <span data-ttu-id="28e38-113">Uygulama projesini oluşturmak için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="28e38-113">Click **OK** to create the application project.</span></span> <span data-ttu-id="28e38-114">Visual Studio, uygulamanız için temel bir WPF Kullanıcı arabirimi oluşturur ve uygun XAML ve arka plan kod dosyalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="28e38-114">Visual Studio creates a basic WPF UI for your application and includes the appropriate XAML and code-behind files.</span></span>

8. <span data-ttu-id="28e38-115">**WorkflowModel** derlemelerine başvurular ekleyin.</span><span class="sxs-lookup"><span data-stu-id="28e38-115">Add references to **WorkflowModel** assemblies.</span></span> <span data-ttu-id="28e38-116">Bunu yapmak için, **Çözüm Gezgini**, **HostingApplication** projesine sağ tıklayın ve **Başvuru Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="28e38-116">To do this, in **Solution Explorer**, right-click the **HostingApplication** project and select **Add Reference**.</span></span>

9. <span data-ttu-id="28e38-117">**Başvuru Ekle** iletişim kutusunda, **.net** sekmesine tıklayın, CTRL tuşunu basılı tutarak aşağıdaki derlemeleri seçin ve ardından **Tamam**' a tıklayın:</span><span class="sxs-lookup"><span data-stu-id="28e38-117">In the **Add Reference** dialog box, click the **.NET** tab, hold down the CTRL key, select the following assemblies, and then click **OK**:</span></span>

    - <span data-ttu-id="28e38-118">System. Activities</span><span class="sxs-lookup"><span data-stu-id="28e38-118">System.Activities</span></span>
    - <span data-ttu-id="28e38-119">System. Activities. Presentation</span><span class="sxs-lookup"><span data-stu-id="28e38-119">System.Activities.Presentation</span></span>
    - <span data-ttu-id="28e38-120">System. Activities. Core. Presentation</span><span class="sxs-lookup"><span data-stu-id="28e38-120">System.Activities.Core.Presentation</span></span>

10. <span data-ttu-id="28e38-121">Bkz. görev 2: iş akışı Tasarımcısı tasarım tuvali 'nin nasıl barındıralınacağını öğrenmek için [iş akışı Tasarımcısı barındırın](task-2-host-the-workflow-designer.md) .</span><span class="sxs-lookup"><span data-stu-id="28e38-121">See [Task 2: Host the Workflow Designer](task-2-host-the-workflow-designer.md) to learn how to host the workflow designer design canvas.</span></span>

## <a name="see-also"></a><span data-ttu-id="28e38-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28e38-122">See also</span></span>

- [<span data-ttu-id="28e38-123">İş Akışı Tasarımcısını Yeniden Barındırma</span><span class="sxs-lookup"><span data-stu-id="28e38-123">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)
- [<span data-ttu-id="28e38-124">Görev 2: İş Akışı Tasarımcısını Barındırma</span><span class="sxs-lookup"><span data-stu-id="28e38-124">Task 2: Host the Workflow Designer</span></span>](task-2-host-the-workflow-designer.md)
