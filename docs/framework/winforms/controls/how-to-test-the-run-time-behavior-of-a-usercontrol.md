---
title: "Nasıl yapılır: Bir UserControl Denetiminin Çalışma Zamanı Davranışını Sınama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UserControl class [Windows Forms], testing
- user controls [Windows Forms], testing
- composite controls [Windows Forms], testing
- UserControl Test Container
- UserControl class [Windows Forms], run-time behavior
ms.assetid: 4e4d5c49-1346-40ac-9d96-40211b573583
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2ce4f821a7b964b3ed2e03c795346b47bb88d618
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="5c4e7-102">Nasıl yapılır: Bir UserControl Denetiminin Çalışma Zamanı Davranışını Sınama</span><span class="sxs-lookup"><span data-stu-id="5c4e7-102">How to: Test the Run-Time Behavior of a UserControl</span></span>
<span data-ttu-id="5c4e7-103">Geliştirirken bir <xref:System.Windows.Forms.UserControl>, çalışma zamanı davranışını sınama gerekir.</span><span class="sxs-lookup"><span data-stu-id="5c4e7-103">When you develop a <xref:System.Windows.Forms.UserControl>, you need to test its run-time behavior.</span></span> <span data-ttu-id="5c4e7-104">Ayrı Windows tabanlı uygulama projesi oluşturun ve test form üzerindeki denetiminizi yerleştirin, ancak bu yordam, kullanışsız kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5c4e7-104">You can create a separate Windows-based application project and place your control on a test form, but this procedure is inconvenient.</span></span> <span data-ttu-id="5c4e7-105">Daha hızlı ve kolay bir yolu kullanmaktır **UserControl Test kapsayıcısı** Visual Studio tarafından sağlanan.</span><span class="sxs-lookup"><span data-stu-id="5c4e7-105">A faster and easier way is to use the **UserControl Test Container** provided by Visual Studio.</span></span> <span data-ttu-id="5c4e7-106">Bu test kapsayıcısı doğrudan Windows Denetim Kitaplığı projenizden başlatır.</span><span class="sxs-lookup"><span data-stu-id="5c4e7-106">This test container starts directly from your Windows control library project.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5c4e7-107">Yüklemek test kapsayıcısı için <xref:System.Windows.Forms.UserControl>, Denetim en az bir public oluşturucuya sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5c4e7-107">For the test container to load your <xref:System.Windows.Forms.UserControl>, the control must have at least one public constructor.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c4e7-108">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="5c4e7-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="5c4e7-109">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="5c4e7-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="5c4e7-110">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="5c4e7-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c4e7-111">Kullanarak bir Visual C++ denetimi sınanamıyor **UserControl Test kapsayıcısı**.</span><span class="sxs-lookup"><span data-stu-id="5c4e7-111">A Visual C++ control cannot be tested using the **UserControl Test Container**.</span></span>  
  
### <a name="to-test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="5c4e7-112">Bir UserControl denetiminin çalışma zamanı davranışını sınamak için</span><span class="sxs-lookup"><span data-stu-id="5c4e7-112">To test the run-time behavior of a UserControl</span></span>  
  
1.  <span data-ttu-id="5c4e7-113">Adlı Windows Denetim Kitaplığı projesi oluşturma **TestContainerExample**.</span><span class="sxs-lookup"><span data-stu-id="5c4e7-113">Create a Windows control library project called **TestContainerExample**.</span></span> <span data-ttu-id="5c4e7-114">Ayrıntılar için bkz [Windows Denetim Kitaplığı şablonu](http://msdn.microsoft.com/en-us/722f4e2d-1310-4ed5-8f33-593337ab66b4).</span><span class="sxs-lookup"><span data-stu-id="5c4e7-114">For details, see [Windows Control Library Template](http://msdn.microsoft.com/en-us/722f4e2d-1310-4ed5-8f33-593337ab66b4).</span></span>  
  
2.  <span data-ttu-id="5c4e7-115">İçinde **Windows Form Tasarımcısı**, sürükleyin bir <xref:System.Windows.Forms.Label> gelen denetim **araç** denetimin tasarım yüzeyine.</span><span class="sxs-lookup"><span data-stu-id="5c4e7-115">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Label> control from the **Toolbox** onto the control's design surface.</span></span>  
  
3.  <span data-ttu-id="5c4e7-116">Projeyi derlemek ve çalıştırmak için F5 tuşuna basın **UserControl Test kapsayıcısı**.</span><span class="sxs-lookup"><span data-stu-id="5c4e7-116">Press F5 to build the project and run the **UserControl Test Container**.</span></span> <span data-ttu-id="5c4e7-117">Test kapsayıcısı olarak görünür, <xref:System.Windows.Forms.UserControl> içinde **Önizleme** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="5c4e7-117">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>  
  
4.  <span data-ttu-id="5c4e7-118">Seçin <xref:System.Windows.Forms.Control.BackColor%2A> görüntülenen özelliği <xref:System.Windows.Forms.PropertyGrid> sağındaki denetim **Önizleme** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="5c4e7-118">Select the <xref:System.Windows.Forms.Control.BackColor%2A> property displayed in the <xref:System.Windows.Forms.PropertyGrid> control to the right of the **Preview** pane.</span></span> <span data-ttu-id="5c4e7-119">Değerine değiştirmek `ControlDark`.</span><span class="sxs-lookup"><span data-stu-id="5c4e7-119">Change its value to `ControlDark`.</span></span> <span data-ttu-id="5c4e7-120">Denetim koyu renge dönüşür gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="5c4e7-120">Observe that the control changes to a darker color.</span></span> <span data-ttu-id="5c4e7-121">Diğer özellik değerleri değiştirmeyi deneyin ve denetiminizin üzerindeki etkisini gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="5c4e7-121">Try changing other property values and observe the effect on your control.</span></span>  
  
5.  <span data-ttu-id="5c4e7-122">Tıklatın **yerleştirme doldurun kullanıcı denetimi** aşağıdaki onay kutusunu **Önizleme** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="5c4e7-122">Click the **Dock Fill User Control** check box below the **Preview** pane.</span></span> <span data-ttu-id="5c4e7-123">Denetim bölmesinde doldurmak için boyutlandırılır gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="5c4e7-123">Observe that the control is resized to fill the pane.</span></span> <span data-ttu-id="5c4e7-124">Test kapsayıcısı yeniden boyutlandırma ve denetim bölmesiyle boyutlandırılır gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="5c4e7-124">Resize the test container and observe that the control is resized with the pane.</span></span>  
  
6.  <span data-ttu-id="5c4e7-125">Test kapsayıcısı kapatın.</span><span class="sxs-lookup"><span data-stu-id="5c4e7-125">Close the test container.</span></span>  
  
7.  <span data-ttu-id="5c4e7-126">Başka bir kullanıcı denetimi Ekle **TestContainerExample** projesi.</span><span class="sxs-lookup"><span data-stu-id="5c4e7-126">Add another user control to the **TestContainerExample** project.</span></span> <span data-ttu-id="5c4e7-127">Ayrıntılar için bkz [NIB: nasıl yapılır: varolan bir proje öğeleri Ekle](http://msdn.microsoft.com/en-us/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).</span><span class="sxs-lookup"><span data-stu-id="5c4e7-127">For details, see [NIB:How to: Add Existing Items to a Project](http://msdn.microsoft.com/en-us/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).</span></span>  
  
8.  <span data-ttu-id="5c4e7-128">İçinde **Windows Form Tasarımcısı**, sürükleyin bir <xref:System.Windows.Forms.Button> gelen denetim **araç** denetimin tasarım yüzeyine.</span><span class="sxs-lookup"><span data-stu-id="5c4e7-128">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the control's design surface.</span></span>  
  
9. <span data-ttu-id="5c4e7-129">Projeyi derlemek ve test kapsayıcısı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="5c4e7-129">Press F5 to build the project and run the test container.</span></span>  
  
10. <span data-ttu-id="5c4e7-130">Tıklatın **kullanıcı denetimi seçin** <xref:System.Windows.Forms.ComboBox> iki kullanıcı denetimleri arasında geçiş yapmak için.</span><span class="sxs-lookup"><span data-stu-id="5c4e7-130">Click the **Select User Control**<xref:System.Windows.Forms.ComboBox> to switch between the two user controls.</span></span>  
  
## <a name="testing-user-controls-from-another-project"></a><span data-ttu-id="5c4e7-131">Kullanıcı denetimleri başka bir projeden test etme</span><span class="sxs-lookup"><span data-stu-id="5c4e7-131">Testing User Controls from Another Project</span></span>  
 <span data-ttu-id="5c4e7-132">Kullanıcı denetimleri diğer projelerden geçerli projenizin test kapsayıcısında test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5c4e7-132">You can test user controls from other projects in your current project's test container.</span></span>  
  
#### <a name="to-test-user-controls-from-another-project"></a><span data-ttu-id="5c4e7-133">Test kullanıcısı için başka bir projeden denetler.</span><span class="sxs-lookup"><span data-stu-id="5c4e7-133">To test user controls from another project</span></span>  
  
1.  <span data-ttu-id="5c4e7-134">Adlı Windows Denetim Kitaplığı projesi oluşturma **TestContainerExample2**.</span><span class="sxs-lookup"><span data-stu-id="5c4e7-134">Create a Windows control library project called **TestContainerExample2**.</span></span> <span data-ttu-id="5c4e7-135">Ayrıntılar için bkz [Windows Denetim Kitaplığı şablonu](http://msdn.microsoft.com/en-us/722f4e2d-1310-4ed5-8f33-593337ab66b4).</span><span class="sxs-lookup"><span data-stu-id="5c4e7-135">For details, see [Windows Control Library Template](http://msdn.microsoft.com/en-us/722f4e2d-1310-4ed5-8f33-593337ab66b4).</span></span>  
  
2.  <span data-ttu-id="5c4e7-136">İçinde **Windows Form Tasarımcısı**, sürükleyin bir <xref:System.Windows.Forms.RadioButton> gelen denetim **araç** denetimin tasarım yüzeyine.</span><span class="sxs-lookup"><span data-stu-id="5c4e7-136">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.RadioButton> control from the **Toolbox** onto the control's design surface.</span></span>  
  
3.  <span data-ttu-id="5c4e7-137">Projeyi derlemek ve test kapsayıcısı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="5c4e7-137">Press F5 to build the project and run the test container.</span></span> <span data-ttu-id="5c4e7-138">Test kapsayıcısı olarak görünür, <xref:System.Windows.Forms.UserControl> içinde **Önizleme** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="5c4e7-138">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>  
  
4.  <span data-ttu-id="5c4e7-139">Tıklatın **yük** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="5c4e7-139">Click the **Load** button.</span></span>  
  
5.  <span data-ttu-id="5c4e7-140">İçinde **açık** iletişim kutusunda, gitmek **TestContainerExample**önceki yordamda oluşturduğunuz .dll.</span><span class="sxs-lookup"><span data-stu-id="5c4e7-140">In the **Open** dialog box, navigate to **TestContainerExample**.dll, which you built in the previous procedure.</span></span> <span data-ttu-id="5c4e7-141">Seçin **TestContainerExample**.dll ve tıklatın **açık** kullanıcı denetimleri yüklemek için düğmeyi</span><span class="sxs-lookup"><span data-stu-id="5c4e7-141">Select **TestContainerExample**.dll and click the **Open** button to load the user controls</span></span>  
  
6.  <span data-ttu-id="5c4e7-142">Kullanım **kullanıcı denetimi seçin** <xref:System.Windows.Forms.ComboBox> iki kullanıcı denetimlerden arasında geçiş yapmak için **TestContainerExample** projesi.</span><span class="sxs-lookup"><span data-stu-id="5c4e7-142">Use the **Select User Control**<xref:System.Windows.Forms.ComboBox> to switch between the two user controls from the **TestContainerExample** project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c4e7-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5c4e7-143">See Also</span></span>  
 <xref:System.Windows.Forms.UserControl>  
 [<span data-ttu-id="5c4e7-144">Nasıl yapılır: bileşik denetimler yazma</span><span class="sxs-lookup"><span data-stu-id="5c4e7-144">How to: Author Composite Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)  
 [<span data-ttu-id="5c4e7-145">İzlenecek yol: Visual Basic ile bileşik denetim yazma</span><span class="sxs-lookup"><span data-stu-id="5c4e7-145">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [<span data-ttu-id="5c4e7-146">İzlenecek yol: Visual C# ile bileşik denetim yazma</span><span class="sxs-lookup"><span data-stu-id="5c4e7-146">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 [<span data-ttu-id="5c4e7-147">Kullanıcı denetimi Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="5c4e7-147">User Control Designer</span></span>](http://msdn.microsoft.com/en-us/2abb9eec-ba32-45cb-b73d-8b52a8bd6bf1)
