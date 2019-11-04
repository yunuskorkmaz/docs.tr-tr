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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: be6c913c43e3559806bc9f38a9c3152b544e4c07
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73455529"
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="198c1-102">Nasıl yapılır: bir UserControl 'un çalışma zamanı davranışını test etme</span><span class="sxs-lookup"><span data-stu-id="198c1-102">How to: Test the run-time behavior of a UserControl</span></span>

<span data-ttu-id="198c1-103">Bir <xref:System.Windows.Forms.UserControl>geliştirirken, çalışma zamanı davranışını test etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="198c1-103">When you develop a <xref:System.Windows.Forms.UserControl>, you need to test its run-time behavior.</span></span> <span data-ttu-id="198c1-104">Ayrı bir Windows tabanlı uygulama projesi oluşturabilir ve denetiminizi bir test formuna yerleştirebilirsiniz, ancak bu yordam uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="198c1-104">You can create a separate Windows-based application project and place your control on a test form, but this procedure is inconvenient.</span></span> <span data-ttu-id="198c1-105">Visual Studio tarafından sunulan **UserControl Test kapsayıcısını** daha hızlı ve kolay bir şekilde kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="198c1-105">A faster and easier way is to use the **UserControl Test Container** provided by Visual Studio.</span></span> <span data-ttu-id="198c1-106">Bu test kapsayıcısı doğrudan Windows Denetim Kitaplığı projenizden başlatılır.</span><span class="sxs-lookup"><span data-stu-id="198c1-106">This test container starts directly from your Windows control library project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="198c1-107">Test kapsayıcısının <xref:System.Windows.Forms.UserControl>yüklemesi için, denetimin en az bir ortak Oluşturucusu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="198c1-107">For the test container to load your <xref:System.Windows.Forms.UserControl>, the control must have at least one public constructor.</span></span>

> [!NOTE]
> <span data-ttu-id="198c1-108">Görsel C++ denetim, **UserControl Test kapsayıcısı**kullanılarak test edilemez.</span><span class="sxs-lookup"><span data-stu-id="198c1-108">A Visual C++ control cannot be tested using the **UserControl Test Container**.</span></span>

## <a name="test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="198c1-109">UserControl 'un çalışma zamanı davranışını test etme</span><span class="sxs-lookup"><span data-stu-id="198c1-109">Test the run-time behavior of a UserControl</span></span>

1. <span data-ttu-id="198c1-110">Visual Studio 'da bir Windows Denetim Kitaplığı projesi oluşturun ve **TestContainerExample**olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="198c1-110">In Visual Studio, create a Windows control library project, and name it **TestContainerExample**.</span></span>

2. <span data-ttu-id="198c1-111">**Windows Form Tasarımcısı**, bir <xref:System.Windows.Forms.Label> denetimini **araç kutusundan** denetimin tasarım yüzeyine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="198c1-111">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Label> control from the **Toolbox** onto the control's design surface.</span></span>

3. <span data-ttu-id="198c1-112">Projeyi derlemek ve **UserControl Test kapsayıcısını**çalıştırmak için <kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="198c1-112">Press <kbd>F5</kbd> to build the project and run the **UserControl Test Container**.</span></span> <span data-ttu-id="198c1-113">Test kapsayıcısı, **Önizleme** bölmesinde <xref:System.Windows.Forms.UserControl> ile görünür.</span><span class="sxs-lookup"><span data-stu-id="198c1-113">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>

4. <span data-ttu-id="198c1-114">**Önizleme** bölmesinin sağındaki <xref:System.Windows.Forms.PropertyGrid> denetiminde görüntülenecek <xref:System.Windows.Forms.Control.BackColor%2A> özelliğini seçin.</span><span class="sxs-lookup"><span data-stu-id="198c1-114">Select the <xref:System.Windows.Forms.Control.BackColor%2A> property displayed in the <xref:System.Windows.Forms.PropertyGrid> control to the right of the **Preview** pane.</span></span> <span data-ttu-id="198c1-115">Değerini **Controlkoyu**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="198c1-115">Change its value to **ControlDark**.</span></span> <span data-ttu-id="198c1-116">Denetimin daha koyu bir renge değiştiğini gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="198c1-116">Observe that the control changes to a darker color.</span></span> <span data-ttu-id="198c1-117">Diğer özellik değerlerini değiştirmeyi deneyin ve denetiminizin etkisini gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="198c1-117">Try changing other property values and observe the effect on your control.</span></span>

5. <span data-ttu-id="198c1-118">**Önizleme** bölmesinin altındaki **Kullanıcı denetimine dolguyu yerleştir** onay kutusunu tıklatın.</span><span class="sxs-lookup"><span data-stu-id="198c1-118">Click the **Dock Fill User Control** check box below the **Preview** pane.</span></span> <span data-ttu-id="198c1-119">Bölmeyi dolduracak şekilde denetimin yeniden boyutlandırıldığını gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="198c1-119">Observe that the control is resized to fill the pane.</span></span> <span data-ttu-id="198c1-120">Test kapsayıcısını yeniden boyutlandırın ve denetimin bölme ile yeniden boyutlandırıldığını gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="198c1-120">Resize the test container and observe that the control is resized with the pane.</span></span>

6. <span data-ttu-id="198c1-121">Test kapsayıcısını kapatın.</span><span class="sxs-lookup"><span data-stu-id="198c1-121">Close the test container.</span></span>

7. <span data-ttu-id="198c1-122">**TestContainerExample** projesine başka bir kullanıcı denetimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="198c1-122">Add another user control to the **TestContainerExample** project.</span></span>

8. <span data-ttu-id="198c1-123">**Windows Form Tasarımcısı**, bir <xref:System.Windows.Forms.Button> denetimini **araç kutusundan** denetimin tasarım yüzeyine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="198c1-123">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the control's design surface.</span></span>

9. <span data-ttu-id="198c1-124">Projeyi derlemek ve test kapsayıcısını çalıştırmak için <kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="198c1-124">Press <kbd>F5</kbd> to build the project and run the test container.</span></span>

10. <span data-ttu-id="198c1-125">İki kullanıcı denetimi arasında geçiş yapmak için **Kullanıcı denetimini seç** <xref:System.Windows.Forms.ComboBox> tıklayın.</span><span class="sxs-lookup"><span data-stu-id="198c1-125">Click the **Select User Control** <xref:System.Windows.Forms.ComboBox> to switch between the two user controls.</span></span>

## <a name="test-user-controls-from-another-project"></a><span data-ttu-id="198c1-126">Başka bir projeden kullanıcı denetimlerini test etme</span><span class="sxs-lookup"><span data-stu-id="198c1-126">Test user controls from another project</span></span>

<span data-ttu-id="198c1-127">Kullanıcı denetimlerini, geçerli projenizin test kapsayıcısındaki diğer projelerden test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="198c1-127">You can test user controls from other projects in your current project's test container.</span></span>

1. <span data-ttu-id="198c1-128">Visual Studio 'da bir Windows Denetim Kitaplığı projesi oluşturun ve **TestContainerExample2**olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="198c1-128">In Visual Studio, create a Windows control library project, and name it **TestContainerExample2**.</span></span>

2. <span data-ttu-id="198c1-129">**Windows Form Tasarımcısı**, bir <xref:System.Windows.Forms.RadioButton> denetimini **araç kutusundan** denetimin tasarım yüzeyine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="198c1-129">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.RadioButton> control from the **Toolbox** onto the control's design surface.</span></span>

3. <span data-ttu-id="198c1-130">Projeyi derlemek ve test kapsayıcısını çalıştırmak için <kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="198c1-130">Press <kbd>F5</kbd> to build the project and run the test container.</span></span> <span data-ttu-id="198c1-131">Test kapsayıcısı, **Önizleme** bölmesinde <xref:System.Windows.Forms.UserControl> ile görünür.</span><span class="sxs-lookup"><span data-stu-id="198c1-131">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>

4. <span data-ttu-id="198c1-132">**Yükle** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="198c1-132">Click the **Load** button.</span></span>

5. <span data-ttu-id="198c1-133">**Aç** iletişim kutusunda, önceki yordamda oluşturduğunuz *TestContainerExample. dll*' ye gidin.</span><span class="sxs-lookup"><span data-stu-id="198c1-133">In the **Open** dialog box, navigate to *TestContainerExample.dll*, which you built in the previous procedure.</span></span> <span data-ttu-id="198c1-134">*TestContainerExample. dll* ' yi seçin ve **Aç** düğmesine tıklayarak Kullanıcı denetimlerini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="198c1-134">Select *TestContainerExample.dll* and click the **Open** button to load the user controls.</span></span>

6. <span data-ttu-id="198c1-135">**TestContainerExample** projesinden Iki kullanıcı denetimi arasında geçiş yapmak Için **kullanıcı denetimini Seç** <xref:System.Windows.Forms.ComboBox> ' i kullanın.</span><span class="sxs-lookup"><span data-stu-id="198c1-135">Use the **Select User Control** <xref:System.Windows.Forms.ComboBox> to switch between the two user controls from the **TestContainerExample** project.</span></span>

## <a name="see-also"></a><span data-ttu-id="198c1-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="198c1-136">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- [<span data-ttu-id="198c1-137">Nasıl yapılır: Bileşik Denetimler Yazma</span><span class="sxs-lookup"><span data-stu-id="198c1-137">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)
- [<span data-ttu-id="198c1-138">İzlenecek yol: bileşik denetim yazma</span><span class="sxs-lookup"><span data-stu-id="198c1-138">Walkthrough: Authoring a Composite Control</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- <span data-ttu-id="198c1-139">[Kullanıcı denetimi Tasarımcısı](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="198c1-139">[User Control Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))</span></span>
