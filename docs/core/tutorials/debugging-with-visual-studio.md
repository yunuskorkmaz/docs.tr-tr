---
title: Visual Studio kullanarak bir .NET Core konsol uygulamasında hata ayıklama
description: Visual Studio kullanarak bir .NET Core konsol uygulamasında hata ayıklamayı öğrenin.
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 743603cb037406948190c7090ca3527bfc40db18
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2020
ms.locfileid: "84702073"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio"></a><span data-ttu-id="efcc5-103">Öğretici: Visual Studio kullanarak bir .NET Core konsol uygulamasında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="efcc5-103">Tutorial: Debug a .NET Core console application using Visual Studio</span></span>

<span data-ttu-id="efcc5-104">Bu öğreticide, Visual Studio 'da kullanılabilen hata ayıklama araçları tanıtılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="efcc5-104">This tutorial introduces the debugging tools available in Visual Studio.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="efcc5-105">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="efcc5-105">Prerequisites</span></span>

- <span data-ttu-id="efcc5-106">Bu öğretici, [Visual Studio 2019 ' de .NET Core konsol uygulaması oluşturma](with-visual-studio.md)bölümünde oluşturduğunuz konsol uygulamasıyla birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="efcc5-106">This tutorial works with the console app that you create in [Create a .NET Core console application in Visual Studio 2019](with-visual-studio.md).</span></span>

## <a name="use-debug-build-configuration"></a><span data-ttu-id="efcc5-107">Hata ayıklama derleme yapılandırmasını kullan</span><span class="sxs-lookup"><span data-stu-id="efcc5-107">Use Debug build configuration</span></span>

<span data-ttu-id="efcc5-108">*Hata ayıklama* ve *yayın* , Visual Studio 'nun yerleşik derleme yapılandırmalarıdır.</span><span class="sxs-lookup"><span data-stu-id="efcc5-108">*Debug* and *Release* are Visual Studio's built-in build configurations.</span></span> <span data-ttu-id="efcc5-109">Hata ayıklama oluşturma yapılandırması hata ayıklama için ve son sürüm dağıtımı için sürüm yapılandırması ' nı kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="efcc5-109">You use the Debug build configuration for debugging and the Release configuration for the final release distribution.</span></span>

<span data-ttu-id="efcc5-110">Hata ayıklama yapılandırmasında, bir program tam sembolik hata ayıklama bilgileriyle derlenir ve iyileştirmesi yoktur.</span><span class="sxs-lookup"><span data-stu-id="efcc5-110">In the Debug configuration, a program compiles with full symbolic debug information and no optimization.</span></span> <span data-ttu-id="efcc5-111">Kaynak kodu ve oluşturulan yönergeler arasındaki ilişki daha karmaşık olduğundan iyileştirme, hata ayıklamayı karmaşıklaştırır.</span><span class="sxs-lookup"><span data-stu-id="efcc5-111">Optimization complicates debugging, because the relationship between source code and generated instructions is more complex.</span></span> <span data-ttu-id="efcc5-112">Bir programın yayın yapılandırmasında sembolik hata ayıklama bilgisi yoktur ve tamamen iyileştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="efcc5-112">The release configuration of a program has no symbolic debug information and is fully optimized.</span></span>

 <span data-ttu-id="efcc5-113">Varsayılan olarak, Visual Studio Code hata ayıklama derleme yapılandırmasını kullanır, bu nedenle hata ayıklamadan önce değiştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="efcc5-113">By default, Visual Studio Code uses the Debug build configuration, so you don't need to change it before debugging.</span></span>

1. <span data-ttu-id="efcc5-114">Visual Studio’yu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="efcc5-114">Start Visual Studio.</span></span>

1. <span data-ttu-id="efcc5-115">[Visual Studio 2019 ' de .NET Core konsol uygulaması oluşturma](with-visual-studio.md)bölümünde oluşturduğunuz projeyi açın.</span><span class="sxs-lookup"><span data-stu-id="efcc5-115">Open the project that you created in [Create a .NET Core console application in Visual Studio 2019](with-visual-studio.md).</span></span>

   <span data-ttu-id="efcc5-116">Geçerli derleme yapılandırması araç çubuğunda gösterilir.</span><span class="sxs-lookup"><span data-stu-id="efcc5-116">The current build configuration is shown on the toolbar.</span></span> <span data-ttu-id="efcc5-117">Aşağıdaki araç çubuğu görüntüsünde, Visual Studio 'nun uygulamanın hata ayıklama sürümünü derlemek üzere yapılandırıldığı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="efcc5-117">The following toolbar image shows that Visual Studio is configured to compile the Debug version of the app:</span></span>

   ![Hata ayıklama vurgulanmış Visual Studio araç çubuğu](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

## <a name="set-a-breakpoint"></a><span data-ttu-id="efcc5-119">Kesme noktası ayarlama</span><span class="sxs-lookup"><span data-stu-id="efcc5-119">Set a breakpoint</span></span>

<span data-ttu-id="efcc5-120">Kesme *noktası,* kesme noktası olan satır yürütülmeden önce uygulamanın yürütülmesini geçici olarak keser.</span><span class="sxs-lookup"><span data-stu-id="efcc5-120">A *breakpoint* temporarily interrupts the execution of the application before the line with the breakpoint is executed.</span></span>

1. <span data-ttu-id="efcc5-121">Bu satırdaki kod penceresinin sol kenar boşluğuna tıklayarak adı, tarihi ve saati gösteren satırda bir *kesme noktası* ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="efcc5-121">Set a *breakpoint* on the line that displays the name, date, and time, by clicking in the left margin of the code window on that line.</span></span> <span data-ttu-id="efcc5-122">Sol kenar boşluğu satır numaralarının solunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="efcc5-122">The left margin is to the left of the line numbers.</span></span>  <span data-ttu-id="efcc5-123">Bir kesme noktası ayarlamak için başka bir yol ise imleci kod satırına yerleştirip, sonra da menü çubuğunda **Hata Ayıkla**  >  **geçiş kesme noktası** ' nı seçerek yapılır.</span><span class="sxs-lookup"><span data-stu-id="efcc5-123">Another way to set a breakpoint is by placing the cursor in the line of code and then choosing **Debug** > **Toggle Breakpoint** from the menu bar.</span></span>

   <span data-ttu-id="efcc5-124">Aşağıdaki görüntüde gösterildiği gibi, Visual Studio, kesme noktasının ayarlandığı ve sol kenar boşluğunda kırmızı bir nokta görüntüleyen çizgiyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="efcc5-124">As the following image shows, Visual Studio indicates the line on which the breakpoint is set by highlighting it and displaying a red dot in the left margin.</span></span>

   ![Kesme noktası ayarlanmış Visual Studio program penceresi](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. <span data-ttu-id="efcc5-126">Programı hata ayıklama modunda çalıştırmak için <kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="efcc5-126">Press <kbd>F5</kbd> to run the program in Debug mode.</span></span> <span data-ttu-id="efcc5-127">Hata ayıklamayı başlatmak için başka bir yol da **Debug**menüden hata ayıklama  >  **başlatma hata** Ayıkla ' yı seçmektir.</span><span class="sxs-lookup"><span data-stu-id="efcc5-127">Another way to start debugging is by choosing **Debug** > **Start Debugging** from the menu.</span></span>

1. <span data-ttu-id="efcc5-128">Program bir ad isteminde bulunduğunda konsol penceresine bir dize girin ve ardından <kbd>ENTER</kbd>tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="efcc5-128">Enter a string in the console window when the program prompts for a name, and then press <kbd>Enter</kbd>.</span></span>

1. <span data-ttu-id="efcc5-129">Program yürütme, kesme noktasına ulaştığında ve Yöntem yürütmeden önce duraklar `Console.WriteLine` .</span><span class="sxs-lookup"><span data-stu-id="efcc5-129">Program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span> <span data-ttu-id="efcc5-130">**Yereller** penceresi, yürütülmekte olan yöntemde tanımlanan değişkenlerin değerlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="efcc5-130">The **Locals** window displays the values of variables that are defined in the currently executing method.</span></span>

   ![Visual Studio 'da bir kesme noktasının ekran görüntüsü](./media/debugging-with-visual-studio/breakpoint-hit.png)

## <a name="use-the-immediate-window"></a><span data-ttu-id="efcc5-132">Hemen penceresini kullanma</span><span class="sxs-lookup"><span data-stu-id="efcc5-132">Use the Immediate window</span></span>

<span data-ttu-id="efcc5-133">**Komut** penceresi, hata ayıklamanıza çalıştığınız uygulamayla etkileşime girebilmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="efcc5-133">The **Immediate** window lets you interact with the application you're debugging.</span></span> <span data-ttu-id="efcc5-134">Programınızı nasıl etkilediğini görmek için değişkenlerin değerini etkileşimli olarak değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="efcc5-134">You can interactively change the value of variables to see how it affects your program.</span></span>

1. <span data-ttu-id="efcc5-135">**Komut** penceresi görünür değilse, Windows anında **Hata Ayıkla**' yı seçerek bunu görüntüleyin  >  **Windows**  >  **Immediate**.</span><span class="sxs-lookup"><span data-stu-id="efcc5-135">If the **Immediate** window is not visible, display it by choosing **Debug** > **Windows** > **Immediate**.</span></span>

1. <span data-ttu-id="efcc5-136">`name = "Gracie"` **Hemen** penceresine girip <kbd>ENTER</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="efcc5-136">Enter `name = "Gracie"` in the **Immediate** window and press the <kbd>Enter</kbd> key.</span></span>

1. <span data-ttu-id="efcc5-137">`date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` **Hemen** penceresine girip <kbd>ENTER</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="efcc5-137">Enter `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` in the **Immediate** window and press the <kbd>Enter</kbd> key.</span></span>

   <span data-ttu-id="efcc5-138">**Komut** penceresi, dize değişkeninin değerini ve değerin özelliklerini görüntüler <xref:System.DateTime> .</span><span class="sxs-lookup"><span data-stu-id="efcc5-138">The **Immediate** window displays the value of the string variable and the properties of the <xref:System.DateTime> value.</span></span> <span data-ttu-id="efcc5-139">Ayrıca, değişkenlerin değerleri **Yereller** penceresinde güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="efcc5-139">In addition, the values of the variables are updated in the **Locals** window.</span></span>

   ![Visual Studio 2019 ' de Yereller ve anında Windows](./media/debugging-with-visual-studio/locals-immediate-window.png)

1. <span data-ttu-id="efcc5-141">Program yürütmeye devam etmek için <kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="efcc5-141">Press <kbd>F5</kbd> to continue program execution.</span></span> <span data-ttu-id="efcc5-142">Devam etmenin başka bir yolu da menüden **Debug**  >  **devam et** ' i seçmekten.</span><span class="sxs-lookup"><span data-stu-id="efcc5-142">Another way to continue is by choosing **Debug** > **Continue** from the menu.</span></span>

   <span data-ttu-id="efcc5-143">Konsol penceresinde görünen değerler, **hemen** penceresinde yaptığınız değişikliklere karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="efcc5-143">The values displayed in the console window correspond to the changes you made in the **Immediate** window.</span></span>

   ![Girilen değerleri gösteren konsol penceresi](./media/debugging-with-visual-studio/console-window.png)

1. <span data-ttu-id="efcc5-145">Uygulamadan çıkmak ve hata ayıklamayı durdurmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="efcc5-145">Press any key to exit the application and stop debugging.</span></span>

## <a name="set-a-conditional-breakpoint"></a><span data-ttu-id="efcc5-146">Koşullu kesme noktası ayarlama</span><span class="sxs-lookup"><span data-stu-id="efcc5-146">Set a conditional breakpoint</span></span>

<span data-ttu-id="efcc5-147">Program, kullanıcının girdiği dizeyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="efcc5-147">The program displays the string that the user enters.</span></span> <span data-ttu-id="efcc5-148">Kullanıcı hiçbir şey girmezse ne olur?</span><span class="sxs-lookup"><span data-stu-id="efcc5-148">What happens if the user doesn't enter anything?</span></span> <span data-ttu-id="efcc5-149">Bunu, *koşullu kesme noktası*adında yararlı bir hata ayıklama özelliği ile test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="efcc5-149">You can test this with a useful debugging feature called a *conditional breakpoint*.</span></span>

1. <span data-ttu-id="efcc5-150">Kesme noktasını temsil eden kırmızı noktaya sağ tıklayın.</span><span class="sxs-lookup"><span data-stu-id="efcc5-150">Right-click on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="efcc5-151">Bağlam menüsünde **koşullar** ' ı seçerek **kesme noktası ayarları** iletişim kutusunu açın.</span><span class="sxs-lookup"><span data-stu-id="efcc5-151">In the context menu, select **Conditions** to open the **Breakpoint Settings** dialog.</span></span> <span data-ttu-id="efcc5-152">Henüz seçili değilse, **koşullar** kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="efcc5-152">Select the box for **Conditions** if it's not already selected.</span></span>

   ![Kesme noktası ayarları panelini gösteren düzenleyici-C #](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. <span data-ttu-id="efcc5-154">**Koşullu ifade**için, 5 ise testlerin örnek kodunu gösteren alana aşağıdaki kodu girin `x` .</span><span class="sxs-lookup"><span data-stu-id="efcc5-154">For the **Conditional Expression**, enter the following code in the field that shows example code that tests if `x` is 5.</span></span> <span data-ttu-id="efcc5-155">Kullanmak istediğiniz dil gösterilmiyorsa sayfanın en üstündeki dil seçicisini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="efcc5-155">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   ```vb
   String.IsNullOrEmpty(name)
   ```

   <span data-ttu-id="efcc5-156">Kesme noktası her isabet edildiğinde, hata ayıklayıcı `String.IsNullOrEmpty(name)` yöntemini çağırır ve yalnızca Yöntem çağrısı döndürürse bu satırı keser `true` .</span><span class="sxs-lookup"><span data-stu-id="efcc5-156">Each time the breakpoint is hit, the debugger calls the `String.IsNullOrEmpty(name)` method, and it breaks on this line only if the method call returns `true`.</span></span>

   <span data-ttu-id="efcc5-157">Koşullu bir ifade yerine, bir deyim belirtilen sayıda yürütülmeden önce program yürütmeyi kesen bir *isabet sayısı*belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="efcc5-157">Instead of a conditional expression, you can specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times.</span></span> <span data-ttu-id="efcc5-158">Diğer bir seçenek de bir *filtre koşulu*belirtmektir. Bu, iş parçacığı tanımlayıcısı, işlem adı veya iş parçacığı adı olarak bu tür özniteliklere dayalı olarak program yürütmeyi keser.</span><span class="sxs-lookup"><span data-stu-id="efcc5-158">Another option is to specify a *filter condition*, which interrupts program execution based on such attributes as a thread identifier, process name, or thread name.</span></span>

1. <span data-ttu-id="efcc5-159">İletişim kutusunu kapatmak için **Kapat** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="efcc5-159">Select **Close** to close the dialog.</span></span>

1. <span data-ttu-id="efcc5-160"><kbd>F5</kbd>'e basarak programı hata ayıklama ile başlatın.</span><span class="sxs-lookup"><span data-stu-id="efcc5-160">Start the program with debugging by pressing <kbd>F5</kbd>.</span></span>

1. <span data-ttu-id="efcc5-161">Konsol penceresinde, adınızı girmeniz istendiğinde <kbd>ENTER</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="efcc5-161">In the console window, press the <kbd>Enter</kbd> key when prompted to enter your name.</span></span>

1. <span data-ttu-id="efcc5-162">Belirttiğiniz koşul ( `name` veya ya da `null` <xref:System.String.Empty?displayProperty=nameWithType> ) karşılandığından, program yürütmesi kesme noktasına ulaştığında ve Yöntem yürütülmeden önce durduktan sonra duraklar `Console.WriteLine` .</span><span class="sxs-lookup"><span data-stu-id="efcc5-162">Because the condition you specified (`name` is either `null` or <xref:System.String.Empty?displayProperty=nameWithType>) has been satisfied, program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span>

1. <span data-ttu-id="efcc5-163">Şu anda yürütülmekte olan metodun yerellerinin değerlerini gösteren **Yereller** penceresini seçin.</span><span class="sxs-lookup"><span data-stu-id="efcc5-163">Select the **Locals** window, which shows the values of variables that are local to the currently executing method.</span></span> <span data-ttu-id="efcc5-164">Bu durumda, `Main` Şu anda yürütülmekte olan yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="efcc5-164">In this case, `Main` is the currently executing method.</span></span> <span data-ttu-id="efcc5-165">Değişkenin değerinin veya olduğunu gözlemleyin `name` `""` <xref:System.String.Empty?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="efcc5-165">Observe that the value of the `name` variable is `""`, or <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

1. <span data-ttu-id="efcc5-166">Aşağıdaki ifadeyi **komut** penceresine girip <kbd>ENTER</kbd>tuşuna basarak değeri boş bir dize olduğunu onaylayın.</span><span class="sxs-lookup"><span data-stu-id="efcc5-166">Confirm the value is an empty string by entering the following statement in the **Immediate** window and pressing <kbd>Enter</kbd>.</span></span> <span data-ttu-id="efcc5-167">Sonuç olarak `true` .</span><span class="sxs-lookup"><span data-stu-id="efcc5-167">The result is `true`.</span></span>

   ```csharp
   ? name == String.Empty
   ```

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

   <span data-ttu-id="efcc5-168">Soru işareti, [bir ifadeyi değerlendirmek](/visualstudio/ide/reference/immediate-window#enter-commands)için hemen penceresini yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="efcc5-168">The question mark directs the immediate window to [evaluate an expression](/visualstudio/ide/reference/immediate-window#enter-commands).</span></span>

   ![Deyimin yürütülmesi yapıldıktan sonra bir true değeri döndüren komut penceresi-C #](./media/debugging-with-visual-studio/immediate-window-output.png)

1. <span data-ttu-id="efcc5-170">Program yürütmeye devam etmek için <kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="efcc5-170">Press <kbd>F5</kbd> to continue program execution.</span></span>

1. <span data-ttu-id="efcc5-171">Herhangi bir tuşa basarak konsol penceresini kapatın ve hata ayıklamayı durdurun.</span><span class="sxs-lookup"><span data-stu-id="efcc5-171">Press any key to close the console window and stop debugging.</span></span>

1. <span data-ttu-id="efcc5-172">Kod penceresinin sol kenarındaki noktaya tıklayarak kesme noktasını temizleyin.</span><span class="sxs-lookup"><span data-stu-id="efcc5-172">Clear the breakpoint by clicking on the dot in the left margin of the code window.</span></span> <span data-ttu-id="efcc5-173">Bir kesme noktasını temizlemek için başka bir yol da, kod satırı seçiliyken **kesme noktası > geçiş noktası** ' nı seçmektir.</span><span class="sxs-lookup"><span data-stu-id="efcc5-173">Another way to clear a breakpoint is by choosing **Debug > Toggle Breakpoint** while the line of code is selected.</span></span>

## <a name="step-through-a-program"></a><span data-ttu-id="efcc5-174">Programda adımla</span><span class="sxs-lookup"><span data-stu-id="efcc5-174">Step through a program</span></span>

<span data-ttu-id="efcc5-175">Visual Studio Ayrıca, bir program aracılığıyla satıra göre çizgi ve yürütmeyi izlemeye de olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="efcc5-175">Visual Studio also allows you to step line by line through a program and monitor its execution.</span></span> <span data-ttu-id="efcc5-176">Normalde, bir kesme noktası ayarlar ve program kodunuzun küçük bir bölümünde program akışını takip edersiniz.</span><span class="sxs-lookup"><span data-stu-id="efcc5-176">Ordinarily, you'd set a breakpoint and follow program flow through a small part of your program code.</span></span> <span data-ttu-id="efcc5-177">Bu program küçük olduğundan programın tamamında ilerlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="efcc5-177">Since this program is small, you can step through the entire program.</span></span>

1. <span data-ttu-id="efcc5-178">**Hata ayıklama**  >  **adımını**seçin.</span><span class="sxs-lookup"><span data-stu-id="efcc5-178">Choose **Debug** > **Step Into**.</span></span> <span data-ttu-id="efcc5-179">Tek seferde bir ifadede hata ayıklamanın başka bir yolu da <kbd>F11</kbd>tuşuna basılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="efcc5-179">Another way to debug one statement at a time is by pressing <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="efcc5-180">Visual Studio, sonraki yürütme satırının yanında bir ok görüntüler.</span><span class="sxs-lookup"><span data-stu-id="efcc5-180">Visual Studio highlights and displays an arrow beside the next line of execution.</span></span>

   <span data-ttu-id="efcc5-181">C#</span><span class="sxs-lookup"><span data-stu-id="efcc5-181">C#</span></span>

   ![Visual Studio Step into yöntemi-C #](./media/debugging-with-visual-studio/step-into-method.png)

   <span data-ttu-id="efcc5-183">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="efcc5-183">Visual Basic</span></span>

   ![Visual Studio adımla yöntemi-Visual Basic](./media/debugging-with-visual-studio/vb-step-into-method.png)

   <span data-ttu-id="efcc5-185">Bu noktada, **Yereller** penceresi `args` dizinin boş olduğunu ve `name` `date` varsayılan değerlere sahip olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="efcc5-185">At this point, the **Locals** window shows that the `args` array is empty, and `name` and `date` have default values.</span></span> <span data-ttu-id="efcc5-186">Ayrıca, Visual Studio boş bir konsol penceresi açtı.</span><span class="sxs-lookup"><span data-stu-id="efcc5-186">In addition, Visual Studio has opened a blank console window.</span></span>

1. <span data-ttu-id="efcc5-187"><kbd>F11</kbd>tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="efcc5-187">Press <kbd>F11</kbd>.</span></span> <span data-ttu-id="efcc5-188">Visual Studio artık bir sonraki yürütme satırını vurgulamaktadır.</span><span class="sxs-lookup"><span data-stu-id="efcc5-188">Visual Studio now highlights the next line of execution.</span></span> <span data-ttu-id="efcc5-189">**Yereller** penceresi değiştirilmez ve konsol penceresi boş kalır.</span><span class="sxs-lookup"><span data-stu-id="efcc5-189">The **Locals** window is unchanged, and the console window remains blank.</span></span>

   <span data-ttu-id="efcc5-190">C#</span><span class="sxs-lookup"><span data-stu-id="efcc5-190">C#</span></span>

   ![Metot kaynağı-C içindeki Visual Studio adımı #](./media/debugging-with-visual-studio/step-into-source-method.png)

   <span data-ttu-id="efcc5-192">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="efcc5-192">Visual Basic</span></span>

   ![Visual Studio adımla Yöntem kaynağı-Visual Basic](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. <span data-ttu-id="efcc5-194"><kbd>F11</kbd>tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="efcc5-194">Press <kbd>F11</kbd>.</span></span> <span data-ttu-id="efcc5-195">Visual Studio, değişken atamasını içeren ifadeyi vurgular `name` .</span><span class="sxs-lookup"><span data-stu-id="efcc5-195">Visual Studio highlights the statement that includes the `name` variable assignment.</span></span> <span data-ttu-id="efcc5-196">**Yereller** penceresi olduğunu gösterir `name` `null` ve konsol penceresi "adınız nedir?" dizesini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="efcc5-196">The **Locals** window shows that `name` is `null`, and the console window displays the string "What is your name?".</span></span>

1. <span data-ttu-id="efcc5-197">Konsol penceresine bir dize girerek ve <kbd>ENTER</kbd>' a basarak istemi yanıtlayın.</span><span class="sxs-lookup"><span data-stu-id="efcc5-197">Respond to the prompt by entering a string in the console window and pressing <kbd>Enter</kbd>.</span></span> <span data-ttu-id="efcc5-198">Konsol yanıt vermiyor ve girdiğiniz dize konsol penceresinde görüntülenmiyor, ancak <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> Yöntem yine de girişinizi yakalayacak.</span><span class="sxs-lookup"><span data-stu-id="efcc5-198">The console is unresponsive, and the string you entered isn't displayed in the console window, but the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method will nevertheless capture your input.</span></span>

1. <span data-ttu-id="efcc5-199"><kbd>F11</kbd>tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="efcc5-199">Press <kbd>F11</kbd>.</span></span> <span data-ttu-id="efcc5-200">Visual Studio, `date` değişken atamasını (Visual Basic) içeren ifadeyi vurgular `currentDate` .</span><span class="sxs-lookup"><span data-stu-id="efcc5-200">Visual Studio highlights the statement that includes the `date` variable assignment (`currentDate` in Visual Basic).</span></span> <span data-ttu-id="efcc5-201">**Yereller** penceresi, yöntemi çağrısının döndürdüğü değeri gösterir <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="efcc5-201">The **Locals** window shows the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="efcc5-202">Konsol penceresinde, isteminde girdiğiniz dize de görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="efcc5-202">The console window also displays the string you entered at the prompt.</span></span>

1. <span data-ttu-id="efcc5-203"><kbd>F11</kbd>tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="efcc5-203">Press <kbd>F11</kbd>.</span></span> <span data-ttu-id="efcc5-204">**Yereller** penceresi, `date` özelliğinden atamasından sonra değişkenin değerini gösterir <xref:System.DateTime.Now?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="efcc5-204">The **Locals** window shows the value of the `date` variable after the assignment from the <xref:System.DateTime.Now?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="efcc5-205">Konsol penceresi değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="efcc5-205">The console window is unchanged.</span></span>

1. <span data-ttu-id="efcc5-206"><kbd>F11</kbd>tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="efcc5-206">Press <kbd>F11</kbd>.</span></span> <span data-ttu-id="efcc5-207">Visual Studio yöntemini çağırır <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="efcc5-207">Visual Studio calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="efcc5-208">Konsol penceresi biçimlendirilen dizeyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="efcc5-208">The console window displays the formatted string.</span></span>

1. <span data-ttu-id="efcc5-209">**Hata ayıklama**  >  **adımını**seçin. Adım adım yürütmeyi durdurmaya yönelik başka bir yöntem de <kbd>SHIFT</kbd> + <kbd>F11</kbd>tuşuna basmaktır.</span><span class="sxs-lookup"><span data-stu-id="efcc5-209">Choose **Debug** > **Step Out**. Another way to stop step-by-step execution is by pressing <kbd>Shift</kbd>+<kbd>F11</kbd>.</span></span>

   <span data-ttu-id="efcc5-210">Konsol penceresinde bir ileti görüntülenir ve bir tuşa basmanız bekler.</span><span class="sxs-lookup"><span data-stu-id="efcc5-210">The console window displays a message and waits for you to press a key.</span></span>

1. <span data-ttu-id="efcc5-211">Herhangi bir tuşa basarak konsol penceresini kapatın ve hata ayıklamayı durdurun.</span><span class="sxs-lookup"><span data-stu-id="efcc5-211">Press any key to close the console window and stop debugging.</span></span>

## <a name="use-release-build-configuration"></a><span data-ttu-id="efcc5-212">Yayın derleme yapılandırmasını kullan</span><span class="sxs-lookup"><span data-stu-id="efcc5-212">Use Release build configuration</span></span>

<span data-ttu-id="efcc5-213">Uygulamanızın hata ayıklama sürümünü sınadıktan sonra yayın sürümünü derleyip test etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="efcc5-213">Once you've tested the Debug version of your application, you should also compile and test the Release version.</span></span> <span data-ttu-id="efcc5-214">Yayın sürümü bazen bir uygulamanın davranışını olumsuz yönde etkileyebilecek derleyici iyileştirmeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="efcc5-214">The Release version incorporates compiler optimizations that can sometimes negatively affect the behavior of an application.</span></span> <span data-ttu-id="efcc5-215">Örneğin, performansı artırmak için tasarlanan derleyici iyileştirmeleri, çok iş parçacıklı uygulamalarda yarış koşulları oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="efcc5-215">For example, compiler optimizations that are designed to improve performance can create race conditions in multithreaded applications.</span></span>

<span data-ttu-id="efcc5-216">Konsol uygulamanızın yayın sürümünü derlemek ve test etmek için, araç çubuğundaki derleme yapılandırmasını **Hata Ayıkla** 'dan **Release**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="efcc5-216">To build and test the Release version of your console application, change the build configuration on the toolbar from **Debug** to **Release**.</span></span>

![hata ayıklama vurgulanmış olarak varsayılan Visual Studio araç çubuğu](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

<span data-ttu-id="efcc5-218"><kbd>F5</kbd> tuşuna bastığınızda veya **Build** menüsünden **çözüm oluştur** ' u seçtiğinizde, Visual Studio uygulamanın yayın sürümünü derler.</span><span class="sxs-lookup"><span data-stu-id="efcc5-218">When you press <kbd>F5</kbd> or choose **Build Solution** from the **Build** menu, Visual Studio compiles the Release version of the application.</span></span> <span data-ttu-id="efcc5-219">Hata ayıklama sürümünü yaptığınız gibi test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="efcc5-219">You can test it as you did the Debug version.</span></span>

## <a name="next-steps"></a><span data-ttu-id="efcc5-220">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="efcc5-220">Next steps</span></span>

<span data-ttu-id="efcc5-221">Bu öğreticide, Visual Studio hata ayıklama araçları 'nı kullandınız.</span><span class="sxs-lookup"><span data-stu-id="efcc5-221">In this tutorial, you used Visual Studio debugging tools.</span></span> <span data-ttu-id="efcc5-222">Sonraki öğreticide, uygulamanın dağıtılabilir bir sürümünü yayımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="efcc5-222">In the next tutorial, you publish a deployable version of the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="efcc5-223">Visual Studio ile bir .NET Core konsol uygulaması yayımlama</span><span class="sxs-lookup"><span data-stu-id="efcc5-223">Publish a .NET Core console application with Visual Studio</span></span>](publishing-with-visual-studio.md)
