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
ms.openlocfilehash: 48531ab1ef3b30b6516e3f2e7b5858a8884cbfe8
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211706"
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="a8214-102">Nasıl yapılır: Bir UserControl denetiminin çalışma zamanı davranışını sınama</span><span class="sxs-lookup"><span data-stu-id="a8214-102">How to: Test the run-time behavior of a UserControl</span></span>

<span data-ttu-id="a8214-103">Geliştirirken bir <xref:System.Windows.Forms.UserControl>, çalışma zamanı davranışını sınama gerekir.</span><span class="sxs-lookup"><span data-stu-id="a8214-103">When you develop a <xref:System.Windows.Forms.UserControl>, you need to test its run-time behavior.</span></span> <span data-ttu-id="a8214-104">Ayrı Windows tabanlı uygulama projesi oluşturun ve test form üzerindeki denetiminizi yerleştirin, ancak bu zor bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="a8214-104">You can create a separate Windows-based application project and place your control on a test form, but this procedure is inconvenient.</span></span> <span data-ttu-id="a8214-105">Daha hızlı ve kolay bir yolu **UserControl Test kapsayıcısı** Visual Studio tarafından sağlanan.</span><span class="sxs-lookup"><span data-stu-id="a8214-105">A faster and easier way is to use the **UserControl Test Container** provided by Visual Studio.</span></span> <span data-ttu-id="a8214-106">Bu test kapsayıcısında, doğrudan Windows Denetim Kitaplığı projenizden başlatır.</span><span class="sxs-lookup"><span data-stu-id="a8214-106">This test container starts directly from your Windows control library project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a8214-107">Yüklemek test kapsayıcısı için <xref:System.Windows.Forms.UserControl>, denetimin en az bir ortak oluşturucuya sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a8214-107">For the test container to load your <xref:System.Windows.Forms.UserControl>, the control must have at least one public constructor.</span></span>

> [!NOTE]
> <span data-ttu-id="a8214-108">Visual C++ denetimi kullanarak sınanamıyor **UserControl Test kapsayıcısı**.</span><span class="sxs-lookup"><span data-stu-id="a8214-108">A Visual C++ control cannot be tested using the **UserControl Test Container**.</span></span>

## <a name="test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="a8214-109">Bir UserControl denetiminin çalışma zamanı davranışını sınama</span><span class="sxs-lookup"><span data-stu-id="a8214-109">Test the run-time behavior of a UserControl</span></span>

1. <span data-ttu-id="a8214-110">Adlı bir Windows Denetim Kitaplığı projesini Visual Studio'da oluşturma **TestContainerExample**.</span><span class="sxs-lookup"><span data-stu-id="a8214-110">In Visual Studio, create a Windows control library project called **TestContainerExample**.</span></span> <span data-ttu-id="a8214-111">Ayrıntılar için bkz [Windows Denetim Kitaplığı şablonu](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a8214-111">For details, see [Windows Control Library Template](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span></span>

2. <span data-ttu-id="a8214-112">İçinde **Windows Form Tasarımcısı**, sürükleyin bir <xref:System.Windows.Forms.Label> denetimi **araç kutusu** denetimin tasarım yüzeyine.</span><span class="sxs-lookup"><span data-stu-id="a8214-112">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Label> control from the **Toolbox** onto the control's design surface.</span></span>

3. <span data-ttu-id="a8214-113">Tuşuna **F5** Projeyi derlemek ve çalıştırmak için **UserControl Test kapsayıcısı**.</span><span class="sxs-lookup"><span data-stu-id="a8214-113">Press **F5** to build the project and run the **UserControl Test Container**.</span></span> <span data-ttu-id="a8214-114">Test kapsayıcısı ile görünür, <xref:System.Windows.Forms.UserControl> içinde **Önizleme** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="a8214-114">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>

4. <span data-ttu-id="a8214-115">Seçin <xref:System.Windows.Forms.Control.BackColor%2A> görüntülenen özelliği <xref:System.Windows.Forms.PropertyGrid> denetim sağındaki **Önizleme** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="a8214-115">Select the <xref:System.Windows.Forms.Control.BackColor%2A> property displayed in the <xref:System.Windows.Forms.PropertyGrid> control to the right of the **Preview** pane.</span></span> <span data-ttu-id="a8214-116">Değerine değiştirmek `ControlDark`.</span><span class="sxs-lookup"><span data-stu-id="a8214-116">Change its value to `ControlDark`.</span></span> <span data-ttu-id="a8214-117">Denetim daha koyu bir renge dönüşür gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="a8214-117">Observe that the control changes to a darker color.</span></span> <span data-ttu-id="a8214-118">Diğer özellik değerleri değiştirmeyi deneyin ve denetim üzerindeki etkisini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="a8214-118">Try changing other property values and observe the effect on your control.</span></span>

5. <span data-ttu-id="a8214-119">Tıklayın **Dock dolgu kullanıcı denetimi** aşağıdaki onay kutularından **Önizleme** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="a8214-119">Click the **Dock Fill User Control** check box below the **Preview** pane.</span></span> <span data-ttu-id="a8214-120">Denetim bölmesinde doldurmak için boyutlandırılır gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="a8214-120">Observe that the control is resized to fill the pane.</span></span> <span data-ttu-id="a8214-121">Test kapsayıcı yeniden boyutlandırma ve Denetim ile bölmesinde yeniden boyutlandırılır gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="a8214-121">Resize the test container and observe that the control is resized with the pane.</span></span>

6. <span data-ttu-id="a8214-122">Test kapsayıcısını kapatın.</span><span class="sxs-lookup"><span data-stu-id="a8214-122">Close the test container.</span></span>

7. <span data-ttu-id="a8214-123">Başka bir kullanıcı denetimine ekleme **TestContainerExample** proje.</span><span class="sxs-lookup"><span data-stu-id="a8214-123">Add another user control to the **TestContainerExample** project.</span></span> <span data-ttu-id="a8214-124">Ayrıntılar için bkz [nasıl yapılır: Projeye var olan öğeleri ekleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a8214-124">For details, see [How to: Add Existing Items to a Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100)).</span></span>

8. <span data-ttu-id="a8214-125">İçinde **Windows Form Tasarımcısı**, sürükleyin bir <xref:System.Windows.Forms.Button> denetimi **araç kutusu** denetimin tasarım yüzeyine.</span><span class="sxs-lookup"><span data-stu-id="a8214-125">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the control's design surface.</span></span>

9. <span data-ttu-id="a8214-126">Projeyi oluşturmak ve test kapsayıcıyı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a8214-126">Press F5 to build the project and run the test container.</span></span>

10. <span data-ttu-id="a8214-127">Tıklayın **kullanıcı denetimi seçin** <xref:System.Windows.Forms.ComboBox> iki kullanıcı denetimler arasında geçiş yapmak için.</span><span class="sxs-lookup"><span data-stu-id="a8214-127">Click the **Select User Control**<xref:System.Windows.Forms.ComboBox> to switch between the two user controls.</span></span>

## <a name="test-user-controls-from-another-project"></a><span data-ttu-id="a8214-128">Kullanıcı denetimleri başka bir projeden test</span><span class="sxs-lookup"><span data-stu-id="a8214-128">Test user controls from another project</span></span>

<span data-ttu-id="a8214-129">Kullanıcı denetimleri diğer projelerden geçerli projenin test kapsayıcısında test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8214-129">You can test user controls from other projects in your current project's test container.</span></span>

1. <span data-ttu-id="a8214-130">Adlı bir Windows Denetim Kitaplığı projesi oluşturun **TestContainerExample2**.</span><span class="sxs-lookup"><span data-stu-id="a8214-130">Create a Windows control library project called **TestContainerExample2**.</span></span> <span data-ttu-id="a8214-131">Ayrıntılar için bkz [Windows Denetim Kitaplığı şablonu](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a8214-131">For details, see [Windows Control Library Template](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span></span>

2. <span data-ttu-id="a8214-132">İçinde **Windows Form Tasarımcısı**, sürükleyin bir <xref:System.Windows.Forms.RadioButton> denetimi **araç kutusu** denetimin tasarım yüzeyine.</span><span class="sxs-lookup"><span data-stu-id="a8214-132">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.RadioButton> control from the **Toolbox** onto the control's design surface.</span></span>

3. <span data-ttu-id="a8214-133">Projeyi oluşturmak ve test kapsayıcıyı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a8214-133">Press F5 to build the project and run the test container.</span></span> <span data-ttu-id="a8214-134">Test kapsayıcısı ile görünür, <xref:System.Windows.Forms.UserControl> içinde **Önizleme** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="a8214-134">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>

4. <span data-ttu-id="a8214-135">Tıklayın **yük** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="a8214-135">Click the **Load** button.</span></span>

5. <span data-ttu-id="a8214-136">İçinde **açık** iletişim kutusunda, gitmek **TestContainerExample**önceki yordamda oluşturulan .dll,.</span><span class="sxs-lookup"><span data-stu-id="a8214-136">In the **Open** dialog box, navigate to **TestContainerExample**.dll, which you built in the previous procedure.</span></span> <span data-ttu-id="a8214-137">Seçin **TestContainerExample**tıklayın ve .dll **açık** yük kullanıcı denetimleri için düğme</span><span class="sxs-lookup"><span data-stu-id="a8214-137">Select **TestContainerExample**.dll and click the **Open** button to load the user controls</span></span>

6. <span data-ttu-id="a8214-138">Kullanım **kullanıcı denetimi seçin** <xref:System.Windows.Forms.ComboBox> iki kullanıcı denetimlerini arasında geçiş yapmak için **TestContainerExample** proje.</span><span class="sxs-lookup"><span data-stu-id="a8214-138">Use the **Select User Control**<xref:System.Windows.Forms.ComboBox> to switch between the two user controls from the **TestContainerExample** project.</span></span>

## <a name="see-also"></a><span data-ttu-id="a8214-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8214-139">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- [<span data-ttu-id="a8214-140">Nasıl yapılır: Bileşik denetimler yazma</span><span class="sxs-lookup"><span data-stu-id="a8214-140">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)
- [<span data-ttu-id="a8214-141">İzlenecek yol: Visual Basic ile bileşik denetim yazma</span><span class="sxs-lookup"><span data-stu-id="a8214-141">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [<span data-ttu-id="a8214-142">İzlenecek yol: Visual C# ile bileşik denetim yazma</span><span class="sxs-lookup"><span data-stu-id="a8214-142">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- <span data-ttu-id="a8214-143">[Kullanıcı denetimi Tasarımcısı](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a8214-143">[User Control Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))</span></span>
