---
title: "Visual Studio 2017 ile C# Hello World uygulamanızda hata ayıklama"
description: "C# Visual Studio 2017 ile yazılmış bir Hello World uygulama hata ayıklama öğrenin."
keywords: ".NET core, .NET Core konsol uygulaması, .NET Core hata ayıklama"
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: cb213625-cc60-438b-9b9e-49aed0e4a974
ms.workload: dotnetcore
ms.openlocfilehash: 3ab19566acb36cb96e0572931ba39f2ae99a3ca7
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="debug-your-hello-world-application-with-visual-studio-2017"></a><span data-ttu-id="42a06-104">Visual Studio 2017 ile Hello World uygulamanızda hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="42a06-104">Debug your Hello World application with Visual Studio 2017</span></span>

<span data-ttu-id="42a06-105">Şu ana kadar adımları izledikten [bir C# Hello World uygulaması ile Visual Studio 2017 .NET Core yapı](.\with-visual-studio.md) veya [bir Visual Basic Hello World uygulaması ile Visual Studio 2017 .NET Core yapı](vb-with-visual-studio.md) oluşturmak için ve basit bir konsol uygulaması çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="42a06-105">So far, you've followed the steps in [Build a C# Hello World Application with .NET Core in Visual Studio 2017](.\with-visual-studio.md) or [Build a Visual Basic Hello World Application with .NET Core in Visual Studio 2017](vb-with-visual-studio.md) to create and run a simple console application.</span></span> <span data-ttu-id="42a06-106">Yazılan ve uygulamanızı derlenmiş sonra sınama başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42a06-106">Once you've written and compiled your application, you can begin testing it.</span></span> <span data-ttu-id="42a06-107">Visual Studio test etme ve sorun giderme uygulamanızı kullanabileceğiniz araçlar hata ayıklama kapsamlı kümesi içerir.</span><span class="sxs-lookup"><span data-stu-id="42a06-107">Visual Studio includes a comprehensive set of debugging tools that you can use when testing and troubleshooting your application.</span></span>

## <a name="debugging-in-debug-mode"></a><span data-ttu-id="42a06-108">Hata ayıklama modunda hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="42a06-108">Debugging in Debug mode</span></span>

<span data-ttu-id="42a06-109">*Hata ayıklama* ve *sürüm* iki Visual Studio'nun varsayılan derleme yapılandırmaları.</span><span class="sxs-lookup"><span data-stu-id="42a06-109">*Debug* and *Release* are two of Visual Studio's default build configurations.</span></span> <span data-ttu-id="42a06-110">Geçerli yapı yapılandırması araç çubuğunda gösterilir.</span><span class="sxs-lookup"><span data-stu-id="42a06-110">The current build configuration is shown on the toolbar.</span></span> <span data-ttu-id="42a06-111">Visual Studio, uygulamanızda derlemek için yapılandırıldığını aşağıdaki araç resim göstermektedir **hata ayıklama** modu.</span><span class="sxs-lookup"><span data-stu-id="42a06-111">The following toolbar image shows that Visual Studio is configured to compile your application in **Debug** mode.</span></span>

   ![Visual Studio araç çubuğu](./media/debugging-with-visual-studio/toolbar1.png)

<span data-ttu-id="42a06-113">Hata ayıklama modunda programınızı test ederek her zaman başlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="42a06-113">You should always begin by testing your program in Debug mode.</span></span> <span data-ttu-id="42a06-114">Çoğu derleyici iyileştirmelerini modunu kapatır hata ayıklama ve yapılandırma işlemi sırasında daha zengin bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="42a06-114">Debug mode turns off most compiler optimizations and provides richer information during the build process.</span></span>

## <a name="setting-a-breakpoint"></a><span data-ttu-id="42a06-115">Kesme noktası ayarlama</span><span class="sxs-lookup"><span data-stu-id="42a06-115">Setting a breakpoint</span></span>

<span data-ttu-id="42a06-116">Hata ayıklama modunda programınızı çalıştırma ve birkaç deneyin hata ayıklama özellikleri:</span><span class="sxs-lookup"><span data-stu-id="42a06-116">Run your program in Debug mode and try a few debugging features:</span></span>

1. <span data-ttu-id="42a06-117">A *kesme noktası* geçici olarak uygulamanın çalışmasını kesintiye uğratır *önce* kesme satırıyla yürütülür.</span><span class="sxs-lookup"><span data-stu-id="42a06-117">A *breakpoint* temporarily interrupts the execution of the application *before* the line with the breakpoint is executed.</span></span> 

# <a name="ctabcsharp"></a>[<span data-ttu-id="42a06-118">C#</span><span class="sxs-lookup"><span data-stu-id="42a06-118">C#</span></span>](#tab/csharp)
   <span data-ttu-id="42a06-119">Okur satırında bir kesme noktası belirleyerek `Console.WriteLine($"\nHello, {name}, on {date:d} at {date:t}!");` o satırdaki veya seçerek kod penceresinin sol kenar boşluğunda tıklayarak **hata ayıklama** > **kesme** satırı ile menü öğesi Seçili.</span><span class="sxs-lookup"><span data-stu-id="42a06-119">Set a breakpoint on the line that reads `Console.WriteLine($"\nHello, {name}, on {date:d} at {date:t}!");` by clicking in the left margin of the code window on that line or by choosing the **Debug** > **Toggle Breakpoint** menu item with the line selected.</span></span> <span data-ttu-id="42a06-120">Aşağıdaki şekilde gösterildiği gibi Visual Studio kesme noktası vurgulayarak ve sol kenar boşluğu içinde kırmızı bir daire görüntüleyerek ayarlamak satır gösterir.</span><span class="sxs-lookup"><span data-stu-id="42a06-120">As the following figure shows, Visual Studio indicates the line on which the breakpoint is set by highlighting it and displaying a red circle in its left margin.</span></span>

   ![Visual Studio programı penceresiyle kesme noktası ayarlama](./media/debugging-with-visual-studio/setbreakpoint.png)
# <a name="visual-basictabvisual-basic"></a>[<span data-ttu-id="42a06-122">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="42a06-122">Visual Basic</span></span>](#tab/visual-basic)
   <span data-ttu-id="42a06-123">Okur satırında bir kesme noktası belirleyerek `Console.WriteLine(vbCrLf + $"Hello, {name}, on {currentDate:d} at {currentDate:t}!")` o satırdaki veya seçerek kod penceresinin sol kenar boşluğunda tıklayarak **hata ayıklama** > **kesme** satırı ile menü öğesi Seçili.</span><span class="sxs-lookup"><span data-stu-id="42a06-123">Set a breakpoint on the line that reads `Console.WriteLine(vbCrLf + $"Hello, {name}, on {currentDate:d} at {currentDate:t}!")` by clicking in the left margin of the code window on that line or by choosing the **Debug** > **Toggle Breakpoint** menu item with the line selected.</span></span> <span data-ttu-id="42a06-124">Aşağıdaki şekilde gösterildiği gibi Visual Studio kesme noktası vurgulayarak ve sol kenar boşluğu içinde kırmızı bir daire görüntüleyerek ayarlamak satır gösterir.</span><span class="sxs-lookup"><span data-stu-id="42a06-124">As the following figure shows, Visual Studio indicates the line on which the breakpoint is set by highlighting it and displaying a red circle in its left margin.</span></span>

   <a name="visual-studio-program-window-with-breakpoint-setmediadebugging-with-visual-studiovb-setbreakpointpng"></a>![Visual Studio programı penceresiyle kesme noktası ayarlama](./media/debugging-with-visual-studio/vb-setbreakpoint.png)
---

1. <span data-ttu-id="42a06-126">Program seçerek hata ayıklama modunda çalıştırılması **HelloWorld** yeşil ok F5 tuşuna basarak veya seçme araç çubuğundan düğme **hata ayıklama** > **hata ayıklamayıBaşlat**.</span><span class="sxs-lookup"><span data-stu-id="42a06-126">Run the program in Debug mode by selecting the **HelloWorld** button with the green arrow on the toolbar, pressing F5, or choosing **Debug** > **Start Debugging**.</span></span>

1. <span data-ttu-id="42a06-127">Program için bir ad istediğinde konsol penceresinde bir dize girin ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="42a06-127">Enter a string in the console window when the program prompts for a name and press Enter.</span></span>

1. <span data-ttu-id="42a06-128">Program yürütme durdurur kesme noktasına ulaştığında ve önce `Console.WriteLine` yöntemini yürütür.</span><span class="sxs-lookup"><span data-stu-id="42a06-128">Program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span> <span data-ttu-id="42a06-129">**Otomobiller** penceresi geçerli satırında kullanılan değişkenlerin değerleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="42a06-129">The **Autos** window displays the values of variables that are used around the current line.</span></span> <span data-ttu-id="42a06-130">**Yereller** penceresi (tıklatarak görüntüleyebileceğiniz **Yereller** sekmesinde) şu anda yürütülen yönteminde tanımlı değişkenlerin değerleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="42a06-130">The **Locals** window (which you can view by clicking the **Locals** tab) displays the values of variables that are defined in the currently executing method.</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="42a06-131">C#</span><span class="sxs-lookup"><span data-stu-id="42a06-131">C#</span></span>](#tab/csharp)
   ![Visual Studio uygulama penceresi](./media/debugging-with-visual-studio/break.png)
# <a name="visual-basictabvisual-basic"></a>[<span data-ttu-id="42a06-133">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="42a06-133">Visual Basic</span></span>](#tab/visual-basic)
   <a name="visual-studio-application-windowmediadebugging-with-visual-studiovb-breakpng"></a>![Visual Studio uygulama penceresi](./media/debugging-with-visual-studio/vb-break.png)
---

1. <span data-ttu-id="42a06-135">Programınızı nasıl etkilediği görmek için değişkenlerin değerini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42a06-135">You can change the value of the variables to see how it affects your program.</span></span> <span data-ttu-id="42a06-136">Varsa **komut penceresi** görünür durumda değilse seçerek görüntülemek **hata ayıklama** > **Windows** > **hemen**menü öğesi.</span><span class="sxs-lookup"><span data-stu-id="42a06-136">If the **Immediate Window** is not visible, display it by choosing the **Debug** > **Windows** > **Immediate** menu item.</span></span> <span data-ttu-id="42a06-137">**Komut penceresi** hata ayıklama uygulama ile etkileşim sağlar.</span><span class="sxs-lookup"><span data-stu-id="42a06-137">The **Immediate Window** lets you interact with the application you're debugging.</span></span>

1. <span data-ttu-id="42a06-138">Değişkenlerin değerleri etkileşimli olarak değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42a06-138">You can interactively change the values of variables.</span></span> <span data-ttu-id="42a06-139">ENTER `name = "Gracie"` içinde **komut penceresi** ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="42a06-139">Enter `name = "Gracie"` in the **Immediate Window** and press the Enter key.</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="42a06-140">C#</span><span class="sxs-lookup"><span data-stu-id="42a06-140">C#</span></span>](#tab/csharp)
1. <span data-ttu-id="42a06-141">ENTER `date = new DateTime(2016,11,01,11,59,00)` içinde **komut penceresi** ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="42a06-141">Enter `date = new DateTime(2016,11,01,11,59,00)` in the **Immediate Window** and press the Enter key.</span></span>

   <span data-ttu-id="42a06-142">**Komut penceresi** dize değişkenin değerini ve özelliklerini görüntüler <xref:System.DateTime> değeri.</span><span class="sxs-lookup"><span data-stu-id="42a06-142">The **Immediate Window** displays the value of the string variable and the properties of the <xref:System.DateTime> value.</span></span> <span data-ttu-id="42a06-143">Ayrıca, değişkenlerin değerini güncelleştirilmiştir **otomobiller** ve **Yereller** windows.</span><span class="sxs-lookup"><span data-stu-id="42a06-143">In addition, the value of the variables is updated in the **Autos** and **Locals** windows.</span></span>

   ![Otomatik değişkenler penceresi ve komut penceresi](./media/debugging-with-visual-studio/autosimmediate.png)
# <a name="visual-basictabvisual-basic"></a>[<span data-ttu-id="42a06-145">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="42a06-145">Visual Basic</span></span>](#tab/visual-basic)
1. <span data-ttu-id="42a06-146">ENTER `currentDate = new DateTime(2016,11,01,11,59,00)` içinde **komut penceresi** ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="42a06-146">Enter `currentDate = new DateTime(2016,11,01,11,59,00)` in the **Immediate Window** and press the Enter key.</span></span>

<!-- The **Immediate Window** displays the value of the string variable and the properties of the <xref:System.DateTime> value. In addition, the value of the variables is updated in the **Autos** and **Locals** windows.

   ![Autos window and Immediate Window](./media/debugging-with-visual-studio/vb-autosimmediate.png)
-->
---

1. <span data-ttu-id="42a06-147">Program yürütme seçerek devam **devam** düğmesini seçerek veya araç çubuğunda **hata ayıklama** > **devam** menü öğesi.</span><span class="sxs-lookup"><span data-stu-id="42a06-147">Continue program execution by selecting the **Continue** button in the toolbar or by selecting the **Debug** > **Continue** menu item.</span></span> <span data-ttu-id="42a06-148">Konsol penceresinde görüntülenen değerler, yaptığınız değişiklikleri karşılık **komut penceresi**.</span><span class="sxs-lookup"><span data-stu-id="42a06-148">The values displayed in the console window correspond to the changes you made in the **Immediate Window**.</span></span>

   ![Yazılı değerinde prizine ne gösteren konsol penceresi nedir? 11: 59'de 1/11/2016'Hello Gracie tarafından izlenen istemi](./media/debugging-with-visual-studio/changed.png)

1. <span data-ttu-id="42a06-150">Uygulama ve son hata ayıklama modundan çıkmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="42a06-150">Press any key to exit the application and end Debug mode.</span></span>

## <a name="setting-a-conditional-breakpoint"></a><span data-ttu-id="42a06-151">Koşullu kesme noktası ayarlama</span><span class="sxs-lookup"><span data-stu-id="42a06-151">Setting a conditional breakpoint</span></span>

<span data-ttu-id="42a06-152">Programınızı kullanıcının girdiği dizesini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="42a06-152">Your program displays the string that the user enters.</span></span> <span data-ttu-id="42a06-153">Kullanıcı herhangi bir şey girmezse ne olur?</span><span class="sxs-lookup"><span data-stu-id="42a06-153">What happens if the user doesn't enter anything?</span></span> <span data-ttu-id="42a06-154">Bu yararlı bir hata ayıklama özellik ile test edebilirsiniz *koşullu kesme noktası*, hangi sonları program yürütme biri veya daha fazla koşullar.</span><span class="sxs-lookup"><span data-stu-id="42a06-154">You can test this with a useful debugging feature, the *conditional breakpoint*, which breaks program execution when one or more conditions are met.</span></span>

<span data-ttu-id="42a06-155">Koşullu kesme noktası ayarlayın ve kullanıcı bir dize girin başarısız olduğunda ne olacağını test etmek için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="42a06-155">To set a conditional breakpoint and test what happens when the user fails to enter a string, do the following:</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="42a06-156">C#</span><span class="sxs-lookup"><span data-stu-id="42a06-156">C#</span></span>](#tab/csharp)
1. <span data-ttu-id="42a06-157">Kesme noktası temsil eden kırmızı nokta üzerinde sağ tıklayın.</span><span class="sxs-lookup"><span data-stu-id="42a06-157">Right-click on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="42a06-158">Bağlam menüsünde seçin **koşullar** açmak için **kesme noktası ayarları** iletişim.</span><span class="sxs-lookup"><span data-stu-id="42a06-158">On the context menu, select **Conditions** to open the **Breakpoint Settings** dialog.</span></span> <span data-ttu-id="42a06-159">Onay kutusunu için **koşullar**.</span><span class="sxs-lookup"><span data-stu-id="42a06-159">Check the box for **Conditions**.</span></span>

   ![Kesme noktası ayarlar paneli](./media/debugging-with-visual-studio/breakpointsettings.png)

1. <span data-ttu-id="42a06-161">İçin **koşullu ifade** Değiştir "Örneğin x 5 ==" aşağıdaki:</span><span class="sxs-lookup"><span data-stu-id="42a06-161">For the **Conditional Expression** replace "e.g. x == 5" with the following:</span></span>

   ```csharp
   String.IsNullOrEmpty(name)
   ```
# <a name="visual-basictabvisual-basic"></a>[<span data-ttu-id="42a06-162">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="42a06-162">Visual Basic</span></span>](#tab/visual-basic)
1. <span data-ttu-id="42a06-163">Kesme noktası temsil eden kırmızı nokta üzerinde sağ tıklayın.</span><span class="sxs-lookup"><span data-stu-id="42a06-163">Right-click on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="42a06-164">Bağlam menüsünde seçin **koşullar** açmak için **kesme noktası ayarları** iletişim.</span><span class="sxs-lookup"><span data-stu-id="42a06-164">On the context menu, select **Conditions** to open the **Breakpoint Settings** dialog.</span></span> <span data-ttu-id="42a06-165">Onay kutusunu için **koşullar**.</span><span class="sxs-lookup"><span data-stu-id="42a06-165">Check the box for **Conditions**.</span></span>

   ![Kesme noktası ayarlar paneli](./media/debugging-with-visual-studio/vb-breakpointsettings.png)

1. <span data-ttu-id="42a06-167">İçin **koşullu ifade** Değiştir "Örneğin x 5 =" aşağıdaki:</span><span class="sxs-lookup"><span data-stu-id="42a06-167">For the **Conditional Expression** replace "e.g. x = 5" with the following:</span></span>

   ```vb
   String.IsNullOrEmpty(name)
   ```
---

   <span data-ttu-id="42a06-168">Kod koşulu için test ediyorsanız, `String.IsNullOrEmpty(name)` yöntemi çağrısı `true` ya da çünkü *adı* bir değer atanmadı ya da boş bir dize değeri olduğu için ("").</span><span class="sxs-lookup"><span data-stu-id="42a06-168">You're testing for a code condition, that the `String.IsNullOrEmpty(name)` method call is `true` either because *name* has not been assigned a value or because its value is an empty string ("").</span></span> <span data-ttu-id="42a06-169">De belirtebilirsiniz bir *isabet sayısı*, belirtilen kaç kez, yürütülen bir açıklamadır önce hangi kesmeler yürütme programı veya bir *filtre koşulu*, kesmeleri programı gibi üzerinde temel yürütme bir iş parçacığı tanımlayıcısı, işlem adı veya iş parçacığı adı olarak öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="42a06-169">You can also specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times, or a *filter condition*, which interrupts program execution based on such attributes as a thread identifier, process name, or thread name.</span></span>

1. <span data-ttu-id="42a06-170">Seçin **kapatmak** düğmesi iletişim kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="42a06-170">Select the **Close** button to close the dialog.</span></span>

1. <span data-ttu-id="42a06-171">Program hata ayıklama modunda çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="42a06-171">Run the program in Debug mode.</span></span>

1. <span data-ttu-id="42a06-172">Konsol penceresinde adınızı girmeniz istendiğinde Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="42a06-172">In the console window, press the Enter key when prompted to enter your name.</span></span>

1. <span data-ttu-id="42a06-173">Koşul biz belirtilmediğinden `name` ya `null` veya <xref:System.String.Empty?displayProperty=nameWithType>, memnun, program yürütme durdurur kesme noktasına ulaştığında ve önce `Console.WriteLine` yöntemini yürütür.</span><span class="sxs-lookup"><span data-stu-id="42a06-173">Because the condition we specified, `name` is either `null` or <xref:System.String.Empty?displayProperty=nameWithType>, has been satisfied, program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span>

1. <span data-ttu-id="42a06-174">Seçin **Yereller** olduğundan şu anda yürütülen yönteme yerel değişkenlerin değerleri gösterir penceresi `Main` programınızdaki yöntemi.</span><span class="sxs-lookup"><span data-stu-id="42a06-174">Select the **Locals** window, which shows the values of variables that are local to the currently executing method, which is the `Main` method in your program.</span></span> <span data-ttu-id="42a06-175">Görüntülendiğini değerini `name` değişken `""`, veya <xref:System.String.Empty?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="42a06-175">Observe that the value of the `name` variable is `""`, or <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="42a06-176">C#</span><span class="sxs-lookup"><span data-stu-id="42a06-176">C#</span></span>](#tab/csharp)
1. <span data-ttu-id="42a06-177">Değer boş bir dize aşağıdaki ifadeyi girerek onaylayın **komut penceresi**.</span><span class="sxs-lookup"><span data-stu-id="42a06-177">Confirm the value is an empty string by entering the following statement in the **Immediate Window**.</span></span> <span data-ttu-id="42a06-178">Sonuç `true`.</span><span class="sxs-lookup"><span data-stu-id="42a06-178">The result is `true`.</span></span>

   ```csharp
   ? name == String.Empty
   ```

   ![Deyim yürütüldükten sonra true değeri döndüren komut penceresi](./media/debugging-with-visual-studio/emptystring.png)
# <a name="visual-basictabvisual-basic"></a>[<span data-ttu-id="42a06-180">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="42a06-180">Visual Basic</span></span>](#tab/visual-basic)
1. <span data-ttu-id="42a06-181">Değer boş bir dize aşağıdaki ifadeyi girerek onaylayın **komut penceresi**.</span><span class="sxs-lookup"><span data-stu-id="42a06-181">Confirm the value is an empty string by entering the following statement in the **Immediate Window**.</span></span> <span data-ttu-id="42a06-182">Sonuç `true`.</span><span class="sxs-lookup"><span data-stu-id="42a06-182">The result is `true`.</span></span>

   ```vb
   ? String.IsNullOrEmpty(name)
   ```
  ![Deyim yürütüldükten sonra true değeri döndüren komut penceresi](./media/debugging-with-visual-studio/vb-emptystring.png)
---

1. <span data-ttu-id="42a06-184">Seçin **devam** program yürütme devam etmek için araç çubuğunda.</span><span class="sxs-lookup"><span data-stu-id="42a06-184">Select the **Continue** button on the toolbar to continue program execution.</span></span>

1. <span data-ttu-id="42a06-185">Konsol penceresini kapatın ve hata ayıklama modundan çıkmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="42a06-185">Press any key to close the console window and exit Debug mode.</span></span>

1. <span data-ttu-id="42a06-186">Kesme noktası kod penceresinin sol kenar boşluğunda nokta tıklayarak veya seçerek temizleyin **hata ayıklama > kesme** menü öğesi seçili satır.</span><span class="sxs-lookup"><span data-stu-id="42a06-186">Clear the breakpoint by clicking on the dot in the left margin of the code window or by choosing the **Debug > Toggle Breakpoint** menu item with the row selected.</span></span>

---
## <a name="stepping-through-a-program"></a><span data-ttu-id="42a06-187">Bir program aracılığıyla Adımlama</span><span class="sxs-lookup"><span data-stu-id="42a06-187">Stepping through a program</span></span>

<span data-ttu-id="42a06-188">Visual Studio bir program aracılığıyla satır adım ve yürütülmesinin izlemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="42a06-188">Visual Studio also allows you to step line by line through a program and monitor its execution.</span></span> <span data-ttu-id="42a06-189">Normalde, bir kesme noktası ayarlayın ve program kodunuzu küçük bir parçası olsa program akışı izlemek için bu özelliği kullanmak.</span><span class="sxs-lookup"><span data-stu-id="42a06-189">Ordinarily, you'd set a breakpoint and use this feature to follow program flow though a small part of your program code.</span></span> <span data-ttu-id="42a06-190">Programınızı küçük olduğundan, aşağıdakileri yaparak tüm program aracılığıyla geçebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="42a06-190">Since your program is small, you can step through the entire program by doing the following:</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="42a06-191">C#</span><span class="sxs-lookup"><span data-stu-id="42a06-191">C#</span></span>](#tab/csharp)
1. <span data-ttu-id="42a06-192">Menü çubuğunda seçin **hata ayıklama** > **Step Into** veya F11 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="42a06-192">On the menu bar, choose **Debug** > **Step Into** or press the F11 key.</span></span> <span data-ttu-id="42a06-193">Visual Studio vurgular ve bir sonraki satıra yürütme dönüşecektir görüntüler.</span><span class="sxs-lookup"><span data-stu-id="42a06-193">Visual Studio highlights and displays an arrow beside the next line of execution.</span></span>

   ![Visual Studio penceresi](./media/debugging-with-visual-studio/stepinto1.png)

   <span data-ttu-id="42a06-195">Bu noktada, **otomobiller** penceresi gösterir, program, yalnızca bir değişken tanımlanmış `args`.</span><span class="sxs-lookup"><span data-stu-id="42a06-195">At this point, the **Autos** window shows that your program has defined only one variable, `args`.</span></span> <span data-ttu-id="42a06-196">Herhangi bir komut satırı bağımsız değişkeni programına aktarılan henüz çünkü değeri boş bir dize dizisi olduğu.</span><span class="sxs-lookup"><span data-stu-id="42a06-196">Because you haven't passed any command-line arguments to the program, its value is an empty string array.</span></span> <span data-ttu-id="42a06-197">Ayrıca, Visual Studio boş konsol penceresi açtı.</span><span class="sxs-lookup"><span data-stu-id="42a06-197">In addition, Visual Studio has opened a blank console window.</span></span>

1. <span data-ttu-id="42a06-198">Seçin **hata ayıklama** > **Step Into** veya F11 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="42a06-198">Select **Debug** > **Step Into** or press the F11 key.</span></span> <span data-ttu-id="42a06-199">Visual Studio artık yürütme sonraki satıra vurgular.</span><span class="sxs-lookup"><span data-stu-id="42a06-199">Visual Studio now highlights the next line of execution.</span></span> <span data-ttu-id="42a06-200">Aşağıdaki şekilde gösterildiği gibi son deyim ve bunu arasında kod yürütmek için kısa bir milisaniye sürdü.</span><span class="sxs-lookup"><span data-stu-id="42a06-200">As the figure shows, it has taken less than one millisecond to execute the code between the last statement and this one.</span></span> <span data-ttu-id="42a06-201">`args`yalnızca bildirilen değişken kalır ve konsol penceresi boş kalır.</span><span class="sxs-lookup"><span data-stu-id="42a06-201">`args` remains the only declared variable, and the console window remains blank.</span></span>

   ![Visual Studio penceresi](./media/debugging-with-visual-studio/stepinto2.png)
# <a name="visual-basictabvisual-basic"></a>[<span data-ttu-id="42a06-203">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="42a06-203">Visual Basic</span></span>](#tab/visual-basic)
1. <span data-ttu-id="42a06-204">Menü çubuğunda seçin **hata ayıklama** > **Step Into** veya F11 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="42a06-204">On the menu bar, choose **Debug** > **Step Into** or press the F11 key.</span></span> <span data-ttu-id="42a06-205">Visual Studio vurgular ve bir sonraki satıra yürütme dönüşecektir görüntüler.</span><span class="sxs-lookup"><span data-stu-id="42a06-205">Visual Studio highlights and displays an arrow beside the next line of execution.</span></span>

   ![Visual Studio penceresi](./media/debugging-with-visual-studio/vb-stepinto1.png)

   <span data-ttu-id="42a06-207">AT noktada, program için herhangi bir komut satırı bağımsız değişkeni geçirilen henüz çünkü **otomobiller** penceresi gösterir, değeri `args` değişkeni, boş bir dize dizisi.</span><span class="sxs-lookup"><span data-stu-id="42a06-207">At this point, because you haven't passed any command-line arguments to the program, the **Autos** window shows that the value of the `args` variable is an empty string array.</span></span> <span data-ttu-id="42a06-208">Ayrıca, Visual Studio boş konsol penceresi açtı.</span><span class="sxs-lookup"><span data-stu-id="42a06-208">In addition, Visual Studio has opened a blank console window.</span></span>

1. <span data-ttu-id="42a06-209">Seçin **hata ayıklama** > **Step Into** veya F11 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="42a06-209">Select **Debug** > **Step Into** or press the F11 key.</span></span> <span data-ttu-id="42a06-210">Visual Studio artık yürütme sonraki satıra vurgular.</span><span class="sxs-lookup"><span data-stu-id="42a06-210">Visual Studio now highlights the next line of execution.</span></span> <span data-ttu-id="42a06-211">Aşağıdaki şekilde gösterildiği gibi son deyim ve bunu arasında kod yürütmek için kısa bir milisaniye sürdü.</span><span class="sxs-lookup"><span data-stu-id="42a06-211">As the figure shows, it has taken less than one millisecond to execute the code between the last statement and this one.</span></span> <span data-ttu-id="42a06-212">`args`yalnızca bildirilen değişken kalır ve konsol penceresi boş kalır.</span><span class="sxs-lookup"><span data-stu-id="42a06-212">`args` remains the only declared variable, and the console window remains blank.</span></span>

   ![Visual Studio penceresi](./media/debugging-with-visual-studio/vb-stepinto2.png)
---

1. <span data-ttu-id="42a06-214">Seçin **hata ayıklama** > **Step Into** veya F11 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="42a06-214">Select **Debug** > **Step Into** or press the F11 key.</span></span> <span data-ttu-id="42a06-215">Visual Studio vurgular içeren deyimi `name` değişken atama.</span><span class="sxs-lookup"><span data-stu-id="42a06-215">Visual Studio highlights the statement that includes the `name` variable assignment.</span></span> <span data-ttu-id="42a06-216">**Otomobiller** penceresi gösterir `name` olan `null` (C# ' ta) veya `Nothing` (Visual Basic'te), ve "Adınızı nedir?" dizesini konsol penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="42a06-216">The **Autos** window shows that `name` is `null` (in C#) or `Nothing` (in Visual Basic), and the console window displays the string "What is your name?".</span></span>

1. <span data-ttu-id="42a06-217">Konsol penceresinde bir dize girerek ve Enter tuşuna basarak komutuna yanıt.</span><span class="sxs-lookup"><span data-stu-id="42a06-217">Respond to the prompt by entering a string in the console window and pressing Enter.</span></span> <span data-ttu-id="42a06-218">Konsol yanıt vermiyor ve girdiğiniz dize konsol penceresinde görüntülenmez ancak <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> yöntemi yine de girişinizi yakalayın.</span><span class="sxs-lookup"><span data-stu-id="42a06-218">The console is unresponsive, and the string you enter isn't displayed in the console window, but the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method will nevertheless capture your input.</span></span>

1. <span data-ttu-id="42a06-219">Seçin **hata ayıklama** > **Step Into** veya F11 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="42a06-219">Select **Debug** > **Step Into** or press the F11 key.</span></span> <span data-ttu-id="42a06-220">Visual Studio vurgular içeren deyimi `date` (C# ' ta) veya `currentDate` (Visual Basic'te) değişken atama.</span><span class="sxs-lookup"><span data-stu-id="42a06-220">Visual Studio highlights the statement that includes the `date` (in C#) or `currentDate` (in Visual Basic) variable assignment.</span></span> <span data-ttu-id="42a06-221">**Otomobiller** penceresi şunu gösterir <xref:System.DateTime.Now?displayProperty=nameWithType> özellik değeri ve çağrı tarafından döndürülen değer <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="42a06-221">The **Autos** window shows the <xref:System.DateTime.Now?displayProperty=nameWithType> property value and the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="42a06-222">Konsol penceresi de konsol için giriş istendiğinde girilen dizesini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="42a06-222">The console window also displays the string entered when the console prompted for input.</span></span>

1. <span data-ttu-id="42a06-223">Seçin **hata ayıklama** > **Step Into** veya F11 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="42a06-223">Select **Debug** > **Step Into** or press the F11 key.</span></span> <span data-ttu-id="42a06-224">**Otomobiller** penceresi gösterir değerini `date` atama sonra değişken <xref:System.DateTime.Now?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="42a06-224">The **Autos** window shows the value of the `date` variable after the assignment from the <xref:System.DateTime.Now?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="42a06-225">Konsol penceresinde değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="42a06-225">The console window is unchanged.</span></span>

1. <span data-ttu-id="42a06-226">Seçin **hata ayıklama** > **Step Into** veya F11 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="42a06-226">Select **Debug** > **Step Into** or press the F11 key.</span></span> <span data-ttu-id="42a06-227">Visual Studio çağırır <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="42a06-227">Visual Studio calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="42a06-228">Değerlerini `date` (veya `currentDate`) ve `name` değişkenleri görünür **otomobiller** ve konsol penceresinde görüntüler biçimlendirilmiş dize.</span><span class="sxs-lookup"><span data-stu-id="42a06-228">The values of the `date` (or `currentDate`) and `name` variables appear in the **Autos** window, and the console window displays the formatted string.</span></span>

1. <span data-ttu-id="42a06-229">Seçin **hata ayıklama** > **Step Out** veya kaydırma ve F11 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="42a06-229">Select **Debug** > **Step Out** or press Shift and the F11 key.</span></span> <span data-ttu-id="42a06-230">Bu adım adım çalışmayı durdurur.</span><span class="sxs-lookup"><span data-stu-id="42a06-230">This stops step-by-step execution.</span></span> <span data-ttu-id="42a06-231">Konsol penceresinde bir ileti görüntüler ve herhangi bir tuşa basın için bekler.</span><span class="sxs-lookup"><span data-stu-id="42a06-231">The console window displays a message and waits for you to press a key.</span></span>

1. <span data-ttu-id="42a06-232">Konsol penceresini kapatın ve hata ayıklama modundan çıkmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="42a06-232">Press any key to close the console window and exit Debug mode.</span></span>

## <a name="building-a-release-version"></a><span data-ttu-id="42a06-233">Bir yayın sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="42a06-233">Building a Release version</span></span>

<span data-ttu-id="42a06-234">Hata ayıklama derlemesi uygulamanızın test ettikten sonra ayrıca derlemek ve yayın sürümü test gerekir.</span><span class="sxs-lookup"><span data-stu-id="42a06-234">Once you've tested the Debug build of your application, you should also compile and test the Release version.</span></span> <span data-ttu-id="42a06-235">Yayın sürümü uygulamanın davranışı bazen olumsuz şekilde etkileyebilecek derleyici iyileştirmeler içerir.</span><span class="sxs-lookup"><span data-stu-id="42a06-235">The Release version incorporates compiler optimizations that can sometimes negatively affect the behavior of an application.</span></span> <span data-ttu-id="42a06-236">Örneğin, performansı iyileştirmek için tasarlanmış derleyici iyileştirmelerini zaman uyumsuz veya birden çok iş parçacıklı uygulamalarda yarış durumları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42a06-236">For example, compiler optimizations that are designed to improve performance can create race conditions in asynchronous or multithreaded applications.</span></span>

<span data-ttu-id="42a06-237">Derleme ve sürümünü Konsol uygulamanızı test etmek için araç çubuğundaki derleme yapılandırması değiştirme **hata ayıklama** için **sürüm**.</span><span class="sxs-lookup"><span data-stu-id="42a06-237">To build and test the Release version of your console application, change the build configuration on the toolbar from **Debug** to **Release**.</span></span>

![Görüntü](./media/debugging-with-visual-studio/toolbar2.png)

<span data-ttu-id="42a06-239">Ne zaman F5 tuşuna basın veya seçin **yapı çözümü** gelen **yapı** menüsünde, Visual Studio konsol uygulamanızın sürümünü derler.</span><span class="sxs-lookup"><span data-stu-id="42a06-239">When you press F5 or choose **Build Solution** from the **Build** menu, Visual Studio compiles the Release version of your console application.</span></span> <span data-ttu-id="42a06-240">Uygulama hata ayıklama sürümü yaptığınız gibi test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42a06-240">You can test it as you did the Debug version of the application.</span></span>

<span data-ttu-id="42a06-241">Uygulamanızın hatalarını ayıklama bitirdikten sonra sonraki adım, uygulamanızın dağıtılabilir sürüm yayımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="42a06-241">Once you've finished debugging your application, the next step is to publish a deployable version of your application.</span></span> <span data-ttu-id="42a06-242">Bunun nasıl yapılacağı hakkında daha fazla bilgi için bkz: [Visual Studio 2017 Hello World uygulamayla yayımlama](./publishing-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="42a06-242">For information on how to do this, see [Publish the Hello World application with Visual Studio 2017](./publishing-with-visual-studio.md).</span></span>
