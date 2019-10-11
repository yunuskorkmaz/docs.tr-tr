---
title: 'Görev 1: yeni bir Windows Presentation Foundation uygulaması oluşturma'
ms.date: 03/30/2017
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
ms.openlocfilehash: 3205840da575041b449eb841fc8084e89937fca7
ms.sourcegitcommit: 10db6551ea3c971470cf5d2cc21ba1cbcefe5c55
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/08/2019
ms.locfileid: "72031888"
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a><span data-ttu-id="e1717-102">Görev 1: yeni bir Windows Presentation Foundation uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="e1717-102">Task 1: Create a New Windows Presentation Foundation Application</span></span>

<span data-ttu-id="e1717-103">Bu görevde, WPF uygulaması Visual Studio şablonunu kullanarak boş bir Windows Presentation Foundation (WPF) uygulaması oluşturacaksınız ve uygun [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] iş akışı derlemelerine başvurular eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="e1717-103">In this task, you will create an empty Windows Presentation Foundation (WPF) application by using the WPF Application Visual Studio template and add references to the appropriate [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow assemblies.</span></span>  
  
## <a name="to-create-the-wpf-application-project"></a><span data-ttu-id="e1717-104">WPF uygulaması projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e1717-104">To create the WPF Application project</span></span>

1. <span data-ttu-id="e1717-105">Visual Studio 'Yu açın ve **Dosya** menüsünde **Yeni**üzerine gelin ve ardından **Proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e1717-105">Open Visual Studio and on the **File** menu, point to **New**, and then click **Project**.</span></span>

2. <span data-ttu-id="e1717-106">**Yeni proje** iletişim kutusunda, kutunun sol tarafındaki **yüklü şablonlar** bölmesinden  **C# görsel** veya **Visual Basic** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="e1717-106">In the **New Project** dialog box, select either **Visual C#** or **Visual Basic** from the **Installed Templates** pane on the left side of the box.</span></span> <span data-ttu-id="e1717-107">Seçtiğiniz dil görünmezse, **diğer diller**bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e1717-107">If the language of your choice does not appear, look under **Other Languages**.</span></span>

3. <span data-ttu-id="e1717-108">**Yüklü şablonlar** bölmesinde **Windows** ' u seçin.</span><span class="sxs-lookup"><span data-stu-id="e1717-108">Select **Windows** in the **Installed Templates** pane.</span></span>

4. <span data-ttu-id="e1717-109">Üst bölmede, açılan liste kutusunda **.NET Framework 4 ' ün** seçildiğinden emin olun ve ardından **WPF uygulaması**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="e1717-109">In the top pane, confirm that (the default value) **.NET Framework 4** has been selected in the drop-down list box, and then select **WPF Application**.</span></span>

5. <span data-ttu-id="e1717-110">Projenin adını pencerenin alt kısmındaki **HostingApplication** olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e1717-110">Set the name of the project to **HostingApplication** at the bottom of the window.</span></span>

6. <span data-ttu-id="e1717-111">Çözüm adını **yeniden hostingolarak**ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e1717-111">Set the solution name to **RehostingTheDesigner**.</span></span>

7. <span data-ttu-id="e1717-112">Uygulama projesini oluşturmak için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="e1717-112">Click **OK** to create the application project.</span></span> <span data-ttu-id="e1717-113">Visual Studio, uygulamanız için temel bir WPF Kullanıcı arabirimi oluşturur ve uygun XAML ve arka plan kod dosyalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="e1717-113">Visual Studio creates a basic WPF UI for your application and includes the appropriate XAML and code-behind files.</span></span>

8. <span data-ttu-id="e1717-114">**WorkflowModel** derlemelerine başvurular ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e1717-114">Add references to **WorkflowModel** assemblies.</span></span> <span data-ttu-id="e1717-115">Bunu yapmak için, **Çözüm Gezgini**, **HostingApplication** projesine sağ tıklayın ve **Başvuru Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="e1717-115">To do this, in **Solution Explorer**, right-click the **HostingApplication** project and select **Add Reference**.</span></span>

9. <span data-ttu-id="e1717-116">**Başvuru Ekle** iletişim kutusunda, **.net** sekmesine tıklayın, CTRL tuşunu basılı tutarak aşağıdaki derlemeleri seçin ve ardından **Tamam**' a tıklayın:</span><span class="sxs-lookup"><span data-stu-id="e1717-116">In the **Add Reference** dialog box, click the **.NET** tab, hold down the CTRL key, select the following assemblies, and then click **OK**:</span></span>

    - <span data-ttu-id="e1717-117">System. Activities</span><span class="sxs-lookup"><span data-stu-id="e1717-117">System.Activities</span></span>
    - <span data-ttu-id="e1717-118">System. Activities. Presentation</span><span class="sxs-lookup"><span data-stu-id="e1717-118">System.Activities.Presentation</span></span>
    - <span data-ttu-id="e1717-119">System. Activities. Core. Presentation</span><span class="sxs-lookup"><span data-stu-id="e1717-119">System.Activities.Core.Presentation</span></span>

10. <span data-ttu-id="e1717-120">Bkz. görev 2: iş akışı Tasarımcısı tasarım tuvali 'nin nasıl barındıralınacağını öğrenmek için [iş akışı Tasarımcısı barındırın](task-2-host-the-workflow-designer.md) .</span><span class="sxs-lookup"><span data-stu-id="e1717-120">See [Task 2: Host the Workflow Designer](task-2-host-the-workflow-designer.md) to learn how to host the workflow designer design canvas.</span></span>

## <a name="see-also"></a><span data-ttu-id="e1717-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1717-121">See also</span></span>

- [<span data-ttu-id="e1717-122">İş Akışı Tasarımcısı yeniden barındırma</span><span class="sxs-lookup"><span data-stu-id="e1717-122">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)
- [<span data-ttu-id="e1717-123">Görev 2: İş Akışı Tasarımcısı barındırın</span><span class="sxs-lookup"><span data-stu-id="e1717-123">Task 2: Host the Workflow Designer</span></span>](task-2-host-the-workflow-designer.md)
