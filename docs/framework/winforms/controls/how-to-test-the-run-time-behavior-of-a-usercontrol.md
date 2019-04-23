---
title: 'Nasıl yapılır: Bir UserControl Denetiminin Çalışma Zamanı Davranışını Sınama'
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], testing
- user controls [Windows Forms], testing
- composite controls [Windows Forms], testing
- UserControl Test Container
- UserControl class [Windows Forms], run-time behavior
ms.assetid: 4e4d5c49-1346-40ac-9d96-40211b573583
ms.openlocfilehash: 15b37c71e6643b588c0378510965a9a3e7cb56e9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59321776"
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="87c74-102">Nasıl yapılır: Bir UserControl Denetiminin Çalışma Zamanı Davranışını Sınama</span><span class="sxs-lookup"><span data-stu-id="87c74-102">How to: Test the Run-Time Behavior of a UserControl</span></span>
<span data-ttu-id="87c74-103">Geliştirirken bir <xref:System.Windows.Forms.UserControl>, çalışma zamanı davranışını sınama gerekir.</span><span class="sxs-lookup"><span data-stu-id="87c74-103">When you develop a <xref:System.Windows.Forms.UserControl>, you need to test its run-time behavior.</span></span> <span data-ttu-id="87c74-104">Ayrı Windows tabanlı uygulama projesi oluşturun ve test form üzerindeki denetiminizi yerleştirin, ancak bu zor bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="87c74-104">You can create a separate Windows-based application project and place your control on a test form, but this procedure is inconvenient.</span></span> <span data-ttu-id="87c74-105">Daha hızlı ve kolay bir yolu **UserControl Test kapsayıcısı** Visual Studio tarafından sağlanan.</span><span class="sxs-lookup"><span data-stu-id="87c74-105">A faster and easier way is to use the **UserControl Test Container** provided by Visual Studio.</span></span> <span data-ttu-id="87c74-106">Bu test kapsayıcısında, doğrudan Windows Denetim Kitaplığı projenizden başlatır.</span><span class="sxs-lookup"><span data-stu-id="87c74-106">This test container starts directly from your Windows control library project.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="87c74-107">Yüklemek test kapsayıcısı için <xref:System.Windows.Forms.UserControl>, denetimin en az bir ortak oluşturucuya sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="87c74-107">For the test container to load your <xref:System.Windows.Forms.UserControl>, the control must have at least one public constructor.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="87c74-108">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="87c74-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="87c74-109">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="87c74-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="87c74-110">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="87c74-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="87c74-111">Visual C++ denetimi kullanarak sınanamıyor **UserControl Test kapsayıcısı**.</span><span class="sxs-lookup"><span data-stu-id="87c74-111">A Visual C++ control cannot be tested using the **UserControl Test Container**.</span></span>  
  
### <a name="to-test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="87c74-112">Bir UserControl denetiminin çalışma zamanı davranışını sınama</span><span class="sxs-lookup"><span data-stu-id="87c74-112">To test the run-time behavior of a UserControl</span></span>  
  
1. <span data-ttu-id="87c74-113">Adlı bir Windows Denetim Kitaplığı projesi oluşturun **TestContainerExample**.</span><span class="sxs-lookup"><span data-stu-id="87c74-113">Create a Windows control library project called **TestContainerExample**.</span></span> <span data-ttu-id="87c74-114">Ayrıntılar için bkz [Windows Denetim Kitaplığı şablonu](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="87c74-114">For details, see [Windows Control Library Template](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="87c74-115">İçinde **Windows Form Tasarımcısı**, sürükleyin bir <xref:System.Windows.Forms.Label> denetimi **araç kutusu** denetimin tasarım yüzeyine.</span><span class="sxs-lookup"><span data-stu-id="87c74-115">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Label> control from the **Toolbox** onto the control's design surface.</span></span>  
  
3. <span data-ttu-id="87c74-116">Projeyi derlemek ve çalıştırmak için F5 tuşuna basın **UserControl Test kapsayıcısı**.</span><span class="sxs-lookup"><span data-stu-id="87c74-116">Press F5 to build the project and run the **UserControl Test Container**.</span></span> <span data-ttu-id="87c74-117">Test kapsayıcısı ile görünür, <xref:System.Windows.Forms.UserControl> içinde **Önizleme** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="87c74-117">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>  
  
4. <span data-ttu-id="87c74-118">Seçin <xref:System.Windows.Forms.Control.BackColor%2A> görüntülenen özelliği <xref:System.Windows.Forms.PropertyGrid> denetim sağındaki **Önizleme** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="87c74-118">Select the <xref:System.Windows.Forms.Control.BackColor%2A> property displayed in the <xref:System.Windows.Forms.PropertyGrid> control to the right of the **Preview** pane.</span></span> <span data-ttu-id="87c74-119">Değerine değiştirmek `ControlDark`.</span><span class="sxs-lookup"><span data-stu-id="87c74-119">Change its value to `ControlDark`.</span></span> <span data-ttu-id="87c74-120">Denetim daha koyu bir renge dönüşür gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="87c74-120">Observe that the control changes to a darker color.</span></span> <span data-ttu-id="87c74-121">Diğer özellik değerleri değiştirmeyi deneyin ve denetim üzerindeki etkisini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="87c74-121">Try changing other property values and observe the effect on your control.</span></span>  
  
5. <span data-ttu-id="87c74-122">Tıklayın **Dock dolgu kullanıcı denetimi** aşağıdaki onay kutularından **Önizleme** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="87c74-122">Click the **Dock Fill User Control** check box below the **Preview** pane.</span></span> <span data-ttu-id="87c74-123">Denetim bölmesinde doldurmak için boyutlandırılır gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="87c74-123">Observe that the control is resized to fill the pane.</span></span> <span data-ttu-id="87c74-124">Test kapsayıcı yeniden boyutlandırma ve Denetim ile bölmesinde yeniden boyutlandırılır gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="87c74-124">Resize the test container and observe that the control is resized with the pane.</span></span>  
  
6. <span data-ttu-id="87c74-125">Test kapsayıcısını kapatın.</span><span class="sxs-lookup"><span data-stu-id="87c74-125">Close the test container.</span></span>  
  
7. <span data-ttu-id="87c74-126">Başka bir kullanıcı denetimine ekleme **TestContainerExample** proje.</span><span class="sxs-lookup"><span data-stu-id="87c74-126">Add another user control to the **TestContainerExample** project.</span></span> <span data-ttu-id="87c74-127">Ayrıntılar için bkz [nasıl yapılır: Projeye var olan öğeleri ekleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="87c74-127">For details, see [How to: Add Existing Items to a Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100)).</span></span>  
  
8. <span data-ttu-id="87c74-128">İçinde **Windows Form Tasarımcısı**, sürükleyin bir <xref:System.Windows.Forms.Button> denetimi **araç kutusu** denetimin tasarım yüzeyine.</span><span class="sxs-lookup"><span data-stu-id="87c74-128">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the control's design surface.</span></span>  
  
9. <span data-ttu-id="87c74-129">Projeyi oluşturmak ve test kapsayıcıyı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="87c74-129">Press F5 to build the project and run the test container.</span></span>  
  
10. <span data-ttu-id="87c74-130">Tıklayın **kullanıcı denetimi seçin** <xref:System.Windows.Forms.ComboBox> iki kullanıcı denetimler arasında geçiş yapmak için.</span><span class="sxs-lookup"><span data-stu-id="87c74-130">Click the **Select User Control**<xref:System.Windows.Forms.ComboBox> to switch between the two user controls.</span></span>  
  
## <a name="testing-user-controls-from-another-project"></a><span data-ttu-id="87c74-131">Kullanıcı denetimleri başka bir projeden test</span><span class="sxs-lookup"><span data-stu-id="87c74-131">Testing User Controls from Another Project</span></span>  
 <span data-ttu-id="87c74-132">Kullanıcı denetimleri diğer projelerden geçerli projenin test kapsayıcısında test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87c74-132">You can test user controls from other projects in your current project's test container.</span></span>  
  
#### <a name="to-test-user-controls-from-another-project"></a><span data-ttu-id="87c74-133">Kullanıcı denetimleri başka bir projeden test etmek için</span><span class="sxs-lookup"><span data-stu-id="87c74-133">To test user controls from another project</span></span>  
  
1. <span data-ttu-id="87c74-134">Adlı bir Windows Denetim Kitaplığı projesi oluşturun **TestContainerExample2**.</span><span class="sxs-lookup"><span data-stu-id="87c74-134">Create a Windows control library project called **TestContainerExample2**.</span></span> <span data-ttu-id="87c74-135">Ayrıntılar için bkz [Windows Denetim Kitaplığı şablonu](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="87c74-135">For details, see [Windows Control Library Template](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="87c74-136">İçinde **Windows Form Tasarımcısı**, sürükleyin bir <xref:System.Windows.Forms.RadioButton> denetimi **araç kutusu** denetimin tasarım yüzeyine.</span><span class="sxs-lookup"><span data-stu-id="87c74-136">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.RadioButton> control from the **Toolbox** onto the control's design surface.</span></span>  
  
3. <span data-ttu-id="87c74-137">Projeyi oluşturmak ve test kapsayıcıyı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="87c74-137">Press F5 to build the project and run the test container.</span></span> <span data-ttu-id="87c74-138">Test kapsayıcısı ile görünür, <xref:System.Windows.Forms.UserControl> içinde **Önizleme** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="87c74-138">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>  
  
4. <span data-ttu-id="87c74-139">Tıklayın **yük** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="87c74-139">Click the **Load** button.</span></span>  
  
5. <span data-ttu-id="87c74-140">İçinde **açık** iletişim kutusunda, gitmek **TestContainerExample**önceki yordamda oluşturulan .dll,.</span><span class="sxs-lookup"><span data-stu-id="87c74-140">In the **Open** dialog box, navigate to **TestContainerExample**.dll, which you built in the previous procedure.</span></span> <span data-ttu-id="87c74-141">Seçin **TestContainerExample**tıklayın ve .dll **açık** yük kullanıcı denetimleri için düğme</span><span class="sxs-lookup"><span data-stu-id="87c74-141">Select **TestContainerExample**.dll and click the **Open** button to load the user controls</span></span>  
  
6. <span data-ttu-id="87c74-142">Kullanım **kullanıcı denetimi seçin** <xref:System.Windows.Forms.ComboBox> iki kullanıcı denetimlerini arasında geçiş yapmak için **TestContainerExample** proje.</span><span class="sxs-lookup"><span data-stu-id="87c74-142">Use the **Select User Control**<xref:System.Windows.Forms.ComboBox> to switch between the two user controls from the **TestContainerExample** project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87c74-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87c74-143">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- [<span data-ttu-id="87c74-144">Nasıl yapılır: Bileşik denetimler yazma</span><span class="sxs-lookup"><span data-stu-id="87c74-144">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)
- [<span data-ttu-id="87c74-145">İzlenecek yol: Visual Basic ile bileşik denetim yazma</span><span class="sxs-lookup"><span data-stu-id="87c74-145">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [<span data-ttu-id="87c74-146">İzlenecek yol: Visual C# ile bileşik denetim yazma</span><span class="sxs-lookup"><span data-stu-id="87c74-146">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- <span data-ttu-id="87c74-147">[Kullanıcı denetimi Tasarımcısı](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="87c74-147">[User Control Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))</span></span>
