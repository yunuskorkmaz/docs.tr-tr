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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1be79d52be3b5b84938d8548a8f101e965fa9dbb
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015773"
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="258dc-102">Nasıl yapılır: UserControl 'un çalışma zamanı davranışını test etme</span><span class="sxs-lookup"><span data-stu-id="258dc-102">How to: Test the run-time behavior of a UserControl</span></span>

<span data-ttu-id="258dc-103">Bir <xref:System.Windows.Forms.UserControl>geliştirirken, çalışma zamanı davranışını test etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="258dc-103">When you develop a <xref:System.Windows.Forms.UserControl>, you need to test its run-time behavior.</span></span> <span data-ttu-id="258dc-104">Ayrı bir Windows tabanlı uygulama projesi oluşturabilir ve denetiminizi bir test formuna yerleştirebilirsiniz, ancak bu yordam uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="258dc-104">You can create a separate Windows-based application project and place your control on a test form, but this procedure is inconvenient.</span></span> <span data-ttu-id="258dc-105">Visual Studio tarafından sunulan **UserControl Test kapsayıcısını** daha hızlı ve kolay bir şekilde kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="258dc-105">A faster and easier way is to use the **UserControl Test Container** provided by Visual Studio.</span></span> <span data-ttu-id="258dc-106">Bu test kapsayıcısı doğrudan Windows Denetim Kitaplığı projenizden başlatılır.</span><span class="sxs-lookup"><span data-stu-id="258dc-106">This test container starts directly from your Windows control library project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="258dc-107">Test kapsayıcısının <xref:System.Windows.Forms.UserControl>' yi yüklemesi için, denetimin en az bir ortak Oluşturucusu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="258dc-107">For the test container to load your <xref:System.Windows.Forms.UserControl>, the control must have at least one public constructor.</span></span>

> [!NOTE]
> <span data-ttu-id="258dc-108">Görsel C++ denetim, **UserControl Test kapsayıcısı**kullanılarak test edilemez.</span><span class="sxs-lookup"><span data-stu-id="258dc-108">A Visual C++ control cannot be tested using the **UserControl Test Container**.</span></span>

## <a name="test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="258dc-109">UserControl 'un çalışma zamanı davranışını test etme</span><span class="sxs-lookup"><span data-stu-id="258dc-109">Test the run-time behavior of a UserControl</span></span>

1. <span data-ttu-id="258dc-110">Visual Studio 'da bir Windows Denetim Kitaplığı projesi oluşturun ve **TestContainerExample**olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="258dc-110">In Visual Studio, create a Windows control library project, and name it **TestContainerExample**.</span></span>

2. <span data-ttu-id="258dc-111">**Windows Form Tasarımcısı**, bir <xref:System.Windows.Forms.Label> denetimi **araç kutusundan** denetimin tasarım yüzeyine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="258dc-111">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Label> control from the **Toolbox** onto the control's design surface.</span></span>

3. <span data-ttu-id="258dc-112">Projeyi derlemek ve **UserControl Test kapsayıcısını**çalıştırmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="258dc-112">Press **F5** to build the project and run the **UserControl Test Container**.</span></span> <span data-ttu-id="258dc-113">Test kapsayıcısı, **Önizleme** bölmesinde ile <xref:System.Windows.Forms.UserControl> görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="258dc-113">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>

4. <span data-ttu-id="258dc-114">**Önizleme bölmesinin** sağındaki <xref:System.Windows.Forms.PropertyGrid> denetimde görüntülenecek özelliğiseçin.<xref:System.Windows.Forms.Control.BackColor%2A></span><span class="sxs-lookup"><span data-stu-id="258dc-114">Select the <xref:System.Windows.Forms.Control.BackColor%2A> property displayed in the <xref:System.Windows.Forms.PropertyGrid> control to the right of the **Preview** pane.</span></span> <span data-ttu-id="258dc-115">Değerini **Controlkoyu**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="258dc-115">Change its value to **ControlDark**.</span></span> <span data-ttu-id="258dc-116">Denetimin daha koyu bir renge değiştiğini gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="258dc-116">Observe that the control changes to a darker color.</span></span> <span data-ttu-id="258dc-117">Diğer özellik değerlerini değiştirmeyi deneyin ve denetiminizin etkisini gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="258dc-117">Try changing other property values and observe the effect on your control.</span></span>

5. <span data-ttu-id="258dc-118">**Önizleme** bölmesinin altındaki **Kullanıcı denetimine dolguyu yerleştir** onay kutusunu tıklatın.</span><span class="sxs-lookup"><span data-stu-id="258dc-118">Click the **Dock Fill User Control** check box below the **Preview** pane.</span></span> <span data-ttu-id="258dc-119">Bölmeyi dolduracak şekilde denetimin yeniden boyutlandırıldığını gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="258dc-119">Observe that the control is resized to fill the pane.</span></span> <span data-ttu-id="258dc-120">Test kapsayıcısını yeniden boyutlandırın ve denetimin bölme ile yeniden boyutlandırıldığını gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="258dc-120">Resize the test container and observe that the control is resized with the pane.</span></span>

6. <span data-ttu-id="258dc-121">Test kapsayıcısını kapatın.</span><span class="sxs-lookup"><span data-stu-id="258dc-121">Close the test container.</span></span>

7. <span data-ttu-id="258dc-122">**TestContainerExample** projesine başka bir kullanıcı denetimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="258dc-122">Add another user control to the **TestContainerExample** project.</span></span>

8. <span data-ttu-id="258dc-123">**Windows Form Tasarımcısı**, bir <xref:System.Windows.Forms.Button> denetimi **araç kutusundan** denetimin tasarım yüzeyine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="258dc-123">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the control's design surface.</span></span>

9. <span data-ttu-id="258dc-124">Projeyi derlemek ve test kapsayıcısını çalıştırmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="258dc-124">Press **F5** to build the project and run the test container.</span></span>

10. <span data-ttu-id="258dc-125">İki kullanıcı denetimi arasında geçiş yapmak için **Kullanıcı denetimini** <xref:System.Windows.Forms.ComboBox> Seç ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="258dc-125">Click the **Select User Control**<xref:System.Windows.Forms.ComboBox> to switch between the two user controls.</span></span>

## <a name="test-user-controls-from-another-project"></a><span data-ttu-id="258dc-126">Başka bir projeden kullanıcı denetimlerini test etme</span><span class="sxs-lookup"><span data-stu-id="258dc-126">Test user controls from another project</span></span>

<span data-ttu-id="258dc-127">Kullanıcı denetimlerini, geçerli projenizin test kapsayıcısındaki diğer projelerden test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="258dc-127">You can test user controls from other projects in your current project's test container.</span></span>

1. <span data-ttu-id="258dc-128">Visual Studio 'da bir Windows Denetim Kitaplığı projesi oluşturun ve **TestContainerExample2**olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="258dc-128">In Visual Studio, create a Windows control library project, and name it **TestContainerExample2**.</span></span>

2. <span data-ttu-id="258dc-129">**Windows Form Tasarımcısı**, bir <xref:System.Windows.Forms.RadioButton> denetimi **araç kutusundan** denetimin tasarım yüzeyine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="258dc-129">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.RadioButton> control from the **Toolbox** onto the control's design surface.</span></span>

3. <span data-ttu-id="258dc-130">Projeyi derlemek ve test kapsayıcısını çalıştırmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="258dc-130">Press **F5** to build the project and run the test container.</span></span> <span data-ttu-id="258dc-131">Test kapsayıcısı, **Önizleme** bölmesinde ile <xref:System.Windows.Forms.UserControl> görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="258dc-131">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>

4. <span data-ttu-id="258dc-132">**Yükle** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="258dc-132">Click the **Load** button.</span></span>

5. <span data-ttu-id="258dc-133">**Aç** iletişim kutusunda, önceki yordamda oluşturduğunuz **TestContainerExample**. dll ' ye gidin.</span><span class="sxs-lookup"><span data-stu-id="258dc-133">In the **Open** dialog box, navigate to **TestContainerExample**.dll, which you built in the previous procedure.</span></span> <span data-ttu-id="258dc-134">**TestContainerExample**. dll ' yi seçin ve **Aç** düğmesine tıklayarak Kullanıcı denetimlerini yükleyin</span><span class="sxs-lookup"><span data-stu-id="258dc-134">Select **TestContainerExample**.dll and click the **Open** button to load the user controls</span></span>

6. <span data-ttu-id="258dc-135">**TestContainerExample** projesinden iki kullanıcı denetimi arasında geçiş yapmak için **Kullanıcı Seç denetimini** <xref:System.Windows.Forms.ComboBox> kullanın.</span><span class="sxs-lookup"><span data-stu-id="258dc-135">Use the **Select User Control**<xref:System.Windows.Forms.ComboBox> to switch between the two user controls from the **TestContainerExample** project.</span></span>

## <a name="see-also"></a><span data-ttu-id="258dc-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="258dc-136">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- [<span data-ttu-id="258dc-137">Nasıl yapılır: Bileşik denetimleri yaz</span><span class="sxs-lookup"><span data-stu-id="258dc-137">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)
- [<span data-ttu-id="258dc-138">İzlenecek yol: Bileşik denetim yazma</span><span class="sxs-lookup"><span data-stu-id="258dc-138">Walkthrough: Authoring a Composite Control</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- <span data-ttu-id="258dc-139">[Kullanıcı denetimi Tasarımcısı](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="258dc-139">[User Control Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))</span></span>
