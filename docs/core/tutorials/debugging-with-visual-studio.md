---
title: Visual Studio ile bir .NET Core konsol uygulamasında hata ayıklama
description: Visual Studio ile bir .NET Core konsol uygulamasında hata ayıklamayı öğrenin.
ms.date: 05/20/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 4bd2a8a0e4b3cea55e209306dd3788552e4b61f3
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005420"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio"></a><span data-ttu-id="38511-103">Öğretici: Visual Studio kullanarak bir .NET Core konsol uygulamasında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="38511-103">Tutorial: Debug a .NET Core console application using Visual Studio</span></span>

<span data-ttu-id="38511-104">Bu öğreticide, Visual Studio 'da kullanılabilen hata ayıklama araçları tanıtılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="38511-104">This tutorial introduces the debugging tools available in Visual Studio.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="38511-105">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="38511-105">Prerequisites</span></span>

- <span data-ttu-id="38511-106">Bu öğretici, [Visual Studio 2019 ' de .NET Core konsol uygulaması oluşturma](with-visual-studio.md)bölümünde oluşturduğunuz konsol uygulamasıyla birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="38511-106">This tutorial works with the console app that you create in [Create a .NET Core console application in Visual Studio 2019](with-visual-studio.md).</span></span>

## <a name="debug-build-configuration"></a><span data-ttu-id="38511-107">Derleme yapılandırmasında hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="38511-107">Debug build configuration</span></span>

<span data-ttu-id="38511-108">*Hata ayıklama* ve *yayın* , Visual Studio 'nun varsayılan derleme yapılandırmasından ikdir.</span><span class="sxs-lookup"><span data-stu-id="38511-108">*Debug* and *Release* are two of Visual Studio's default build configurations.</span></span> <span data-ttu-id="38511-109">Geçerli derleme yapılandırması araç çubuğunda gösterilir.</span><span class="sxs-lookup"><span data-stu-id="38511-109">The current build configuration is shown on the toolbar.</span></span> <span data-ttu-id="38511-110">Aşağıdaki araç çubuğu görüntüsünde, Visual Studio 'nun uygulamanın hata ayıklama sürümünü derlemek üzere yapılandırıldığı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="38511-110">The following toolbar image shows that Visual Studio is configured to compile the Debug version of the app:</span></span>

![Hata ayıklama vurgulanmış Visual Studio araç çubuğu](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

<span data-ttu-id="38511-112">Uygulamanın hata ayıklama sürümünü çalıştırarak başlayın.</span><span class="sxs-lookup"><span data-stu-id="38511-112">Begin by running the Debug version of the app.</span></span> <span data-ttu-id="38511-113">Hata ayıklama derleme yapılandırması, çoğu derleyici iyileştirmesini kapatır ve derleme işlemi sırasında daha zengin bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="38511-113">The Debug build configuration turns off most compiler optimizations and provides richer information during the build process.</span></span>

## <a name="set-a-breakpoint"></a><span data-ttu-id="38511-114">Kesme noktası ayarlama</span><span class="sxs-lookup"><span data-stu-id="38511-114">Set a breakpoint</span></span>

<!-- markdownlint-disable MD025 -->

1. <span data-ttu-id="38511-115">Bu satırdaki kod penceresinin sol kenar boşluğuna tıklayarak adı, tarihi ve saati gösteren satırda bir *kesme noktası* ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="38511-115">Set a *breakpoint* on the line that displays the name, date, and time, by clicking in the left margin of the code window on that line.</span></span> <span data-ttu-id="38511-116">Bir kesme noktası ayarlamak için başka bir yol ise imleci kod satırına yerleştirip **F9** tuşuna basarak veya menü çubuğundan **hata ayıklama**  >  **geçiş noktası geçişi** ' ni seçmektir.</span><span class="sxs-lookup"><span data-stu-id="38511-116">Another way to set a breakpoint is by placing the cursor in the line of code and then pressing **F9** or choosing **Debug** > **Toggle Breakpoint** from the menu bar.</span></span>

   <span data-ttu-id="38511-117">Kesme noktası, kesme noktası olan satır yürütülmeden *önce* uygulamanın yürütülmesini geçici olarak keser.</span><span class="sxs-lookup"><span data-stu-id="38511-117">A breakpoint temporarily interrupts the execution of the application *before* the line with the breakpoint is executed.</span></span>

   <span data-ttu-id="38511-118">Aşağıdaki görüntüde gösterildiği gibi, Visual Studio, kesme noktasının ayarlandığı ve sol kenar boşluğunda kırmızı bir nokta görüntüleyen çizgiyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="38511-118">As the following image shows, Visual Studio indicates the line on which the breakpoint is set by highlighting it and displaying a red dot in the left margin.</span></span>

   ![Kesme noktası ayarlanmış Visual Studio program penceresi](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. <span data-ttu-id="38511-120">Araç çubuğunda yeşil oklu **HelloWorld** düğmesini seçerek programı hata ayıklama modunda çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="38511-120">Run the program in Debug mode by selecting the **HelloWorld** button with the green arrow on the toolbar.</span></span> <span data-ttu-id="38511-121">Hata ayıklamayı başlatmak için diğer yollar **F5** tuşuna basarak **veya hata ayıklama**  >  **başlatma hata ayıklamayı**seçerek.</span><span class="sxs-lookup"><span data-stu-id="38511-121">Other ways to start debugging are by pressing **F5** or by choosing **Debug** > **Start Debugging**.</span></span>

1. <span data-ttu-id="38511-122">Program bir ad isteminde bulunduğunda konsol penceresine bir dize girin ve ardından **ENTER**tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="38511-122">Enter a string in the console window when the program prompts for a name, and then press **Enter**.</span></span>

1. <span data-ttu-id="38511-123">Program yürütme, kesme noktasına ulaştığında ve Yöntem yürütmeden önce duraklar `Console.WriteLine` .</span><span class="sxs-lookup"><span data-stu-id="38511-123">Program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span> <span data-ttu-id="38511-124">**Yereller** penceresi, yürütülmekte olan yöntemde tanımlanan değişkenlerin değerlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="38511-124">The **Locals** window displays the values of variables that are defined in the currently executing method.</span></span>

   ![Visual Studio 'da bir kesme noktasının ekran görüntüsü](./media/debugging-with-visual-studio/breakpoint-hit.png)

1. <span data-ttu-id="38511-126">**Komut** penceresi, hata ayıklamanıza çalıştığınız uygulamayla etkileşime girebilmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="38511-126">The **Immediate** window lets you interact with the application you're debugging.</span></span> <span data-ttu-id="38511-127">Programınızı nasıl etkilediğini görmek için değişkenlerin değerini etkileşimli olarak değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38511-127">You can interactively change the value of variables to see how it affects your program.</span></span>

   1. <span data-ttu-id="38511-128">**Komut** penceresi görünür değilse, Windows anında **Hata Ayıkla**' yı seçerek bunu görüntüleyin  >  **Windows**  >  **Immediate**.</span><span class="sxs-lookup"><span data-stu-id="38511-128">If the **Immediate** window is not visible, display it by choosing **Debug** > **Windows** > **Immediate**.</span></span>

   1. <span data-ttu-id="38511-129">`name = "Gracie"` **Hemen** penceresine girip **ENTER** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="38511-129">Enter `name = "Gracie"` in the **Immediate** window and press the **Enter** key.</span></span>

   1. <span data-ttu-id="38511-130">`date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` **Hemen** penceresine girip **ENTER** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="38511-130">Enter `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` in the **Immediate** window and press the **Enter** key.</span></span>

   <span data-ttu-id="38511-131">**Komut** penceresi, dize değişkeninin değerini ve değerin özelliklerini görüntüler <xref:System.DateTime> .</span><span class="sxs-lookup"><span data-stu-id="38511-131">The **Immediate** window displays the value of the string variable and the properties of the <xref:System.DateTime> value.</span></span> <span data-ttu-id="38511-132">Ayrıca, değişkenlerin değerleri **Yereller** penceresinde güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="38511-132">In addition, the values of the variables are updated in the **Locals** window.</span></span>

   ![Visual Studio 2019 ' de Yereller ve anında Windows](./media/debugging-with-visual-studio/locals-immediate-window.png)

1. <span data-ttu-id="38511-134">Araç çubuğundaki **devam** düğmesini seçerek program yürütmeye devam edin.</span><span class="sxs-lookup"><span data-stu-id="38511-134">Continue program execution by selecting the **Continue** button in the toolbar.</span></span> <span data-ttu-id="38511-135">Devam etmenin başka bir yolu da **Hata Ayıkla**  >  **devam et**' i seçmektir.</span><span class="sxs-lookup"><span data-stu-id="38511-135">Another way to continue is by choosing **Debug** > **Continue**.</span></span>

   <span data-ttu-id="38511-136">Konsol penceresinde görünen değerler, **hemen** penceresinde yaptığınız değişikliklere karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="38511-136">The values displayed in the console window correspond to the changes you made in the **Immediate** window.</span></span>

   ![Girilen değerleri gösteren konsol penceresi](./media/debugging-with-visual-studio/console-window.png)

1. <span data-ttu-id="38511-138">Uygulamadan çıkmak ve hata ayıklamayı durdurmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="38511-138">Press any key to exit the application and stop debugging.</span></span>

## <a name="set-a-conditional-breakpoint"></a><span data-ttu-id="38511-139">Koşullu kesme noktası ayarlama</span><span class="sxs-lookup"><span data-stu-id="38511-139">Set a conditional breakpoint</span></span>

<span data-ttu-id="38511-140">Program, kullanıcının girdiği dizeyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="38511-140">The program displays the string that the user enters.</span></span> <span data-ttu-id="38511-141">Kullanıcı hiçbir şey girmezse ne olur?</span><span class="sxs-lookup"><span data-stu-id="38511-141">What happens if the user doesn't enter anything?</span></span> <span data-ttu-id="38511-142">Bunu, bir veya daha fazla koşul karşılandığında program yürütmesini kesen, *koşullu kesme noktası*adlı yararlı bir hata ayıklama özelliği ile test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38511-142">You can test this with a useful debugging feature called a *conditional breakpoint*, which breaks program execution when one or more conditions are met.</span></span>

<span data-ttu-id="38511-143">Koşullu bir kesme noktası ayarlamak ve Kullanıcı bir dize giremediğinde ne olacağını sınamak için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="38511-143">To set a conditional breakpoint and test what happens when the user fails to enter a string, do the following:</span></span>

1. <span data-ttu-id="38511-144">Kesme noktasını temsil eden kırmızı noktaya sağ tıklayın.</span><span class="sxs-lookup"><span data-stu-id="38511-144">Right-click on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="38511-145">Bağlam menüsünde **koşullar** ' ı seçerek **kesme noktası ayarları** iletişim kutusunu açın.</span><span class="sxs-lookup"><span data-stu-id="38511-145">In the context menu, select **Conditions** to open the **Breakpoint Settings** dialog.</span></span> <span data-ttu-id="38511-146">Henüz seçili değilse, **koşullar** kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="38511-146">Select the box for **Conditions** if it's not already selected.</span></span>

   ![Kesme noktası ayarları panelini gösteren düzenleyici-C #](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. <span data-ttu-id="38511-148">**Koşullu ifade**için, 5 ise testlerin örnek kodunu gösteren alana aşağıdaki kodu girin `x` .</span><span class="sxs-lookup"><span data-stu-id="38511-148">For the **Conditional Expression**, enter the following code in the field that shows example code that tests if `x` is 5.</span></span> <span data-ttu-id="38511-149">Kullanmak istediğiniz dil gösterilmiyorsa sayfanın en üstündeki dil seçicisini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="38511-149">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   ```vb
   String.IsNullOrEmpty(name)
   ```

   <span data-ttu-id="38511-150">Kesme noktası her isabet edildiğinde, hata ayıklayıcı `String.IsNullOrEmpty(name)` yöntemini çağırır ve yalnızca Yöntem çağrısı döndürürse bu satırı keser `true` .</span><span class="sxs-lookup"><span data-stu-id="38511-150">Each time the breakpoint is hit, the debugger calls the `String.IsNullOrEmpty(name)` method, and it breaks on this line only if the method call returns `true`.</span></span>

   <span data-ttu-id="38511-151">Koşullu bir ifade yerine, bir deyim belirtilen sayıda yürütülmeden önce program yürütmeyi kesen bir *isabet sayısı*veya iş parçacığı tanımlayıcısı, işlem adı veya iş parçacığı adı olarak bu tür özniteliklere dayalı olarak program yürütmeyi kesen bir *filtre koşulu*belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38511-151">Instead of a conditional expression, you can specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times, or a *filter condition*, which interrupts program execution based on such attributes as a thread identifier, process name, or thread name.</span></span>

1. <span data-ttu-id="38511-152">İletişim kutusunu kapatmak için **Kapat** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="38511-152">Select **Close** to close the dialog.</span></span>

1. <span data-ttu-id="38511-153">**F5**'e basarak programı hata ayıklama ile başlatın.</span><span class="sxs-lookup"><span data-stu-id="38511-153">Start the program with debugging by pressing **F5**.</span></span>

1. <span data-ttu-id="38511-154">Konsol penceresinde, adınızı girmeniz istendiğinde **ENTER** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="38511-154">In the console window, press the **Enter** key when prompted to enter your name.</span></span>

1. <span data-ttu-id="38511-155">Belirttiğiniz koşul ( `name` veya ya da `null` <xref:System.String.Empty?displayProperty=nameWithType> ) karşılandığından, program yürütmesi kesme noktasına ulaştığında ve Yöntem yürütülmeden önce durduktan sonra duraklar `Console.WriteLine` .</span><span class="sxs-lookup"><span data-stu-id="38511-155">Because the condition you specified (`name` is either `null` or <xref:System.String.Empty?displayProperty=nameWithType>) has been satisfied, program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span>

1. <span data-ttu-id="38511-156">Şu anda yürütülmekte olan metodun yerellerinin değerlerini gösteren **Yereller** penceresini seçin.</span><span class="sxs-lookup"><span data-stu-id="38511-156">Select the **Locals** window, which shows the values of variables that are local to the currently executing method.</span></span> <span data-ttu-id="38511-157">Bu durumda, `Main` Şu anda yürütülmekte olan yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="38511-157">In this case, `Main` is the currently executing method.</span></span> <span data-ttu-id="38511-158">Değişkenin değerinin veya olduğunu gözlemleyin `name` `""` <xref:System.String.Empty?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="38511-158">Observe that the value of the `name` variable is `""`, or <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

1. <span data-ttu-id="38511-159">Aşağıdaki ifadeyi **komut** penceresine girip **ENTER**tuşuna basarak değeri boş bir dize olduğunu onaylayın.</span><span class="sxs-lookup"><span data-stu-id="38511-159">Confirm the value is an empty string by entering the following statement in the **Immediate** window and pressing **Enter**.</span></span> <span data-ttu-id="38511-160">Sonuç olarak `true` .</span><span class="sxs-lookup"><span data-stu-id="38511-160">The result is `true`.</span></span>

   ```csharp
   ? name == String.Empty
   ```

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

   <span data-ttu-id="38511-161">Soru işareti, [bir ifadeyi değerlendirmek](/visualstudio/ide/reference/immediate-window#enter-commands)için hemen penceresini yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="38511-161">The question mark directs the immediate window to [evaluate an expression](/visualstudio/ide/reference/immediate-window#enter-commands).</span></span>

   ![Deyimin yürütülmesi yapıldıktan sonra bir true değeri döndüren komut penceresi-C #](./media/debugging-with-visual-studio/immediate-window-output.png)

1. <span data-ttu-id="38511-163">Program yürütmeye devam etmek için araç çubuğundaki **devam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="38511-163">Select the **Continue** button on the toolbar to continue program execution.</span></span>

1. <span data-ttu-id="38511-164">Herhangi bir tuşa basarak konsol penceresini kapatın ve hata ayıklamayı durdurun.</span><span class="sxs-lookup"><span data-stu-id="38511-164">Press any key to close the console window and stop debugging.</span></span>

1. <span data-ttu-id="38511-165">Kod penceresinin sol kenarındaki noktaya tıklayarak kesme noktasını temizleyin.</span><span class="sxs-lookup"><span data-stu-id="38511-165">Clear the breakpoint by clicking on the dot in the left margin of the code window.</span></span> <span data-ttu-id="38511-166">Bir kesme noktasını temizlemek için başka bir yol da, kod satırı seçiliyken **kesme noktası > geçiş noktası** ' nı seçmektir.</span><span class="sxs-lookup"><span data-stu-id="38511-166">Another way to clear a breakpoint is by choosing **Debug > Toggle Breakpoint** while the line of code is selected.</span></span>

## <a name="step-through-a-program"></a><span data-ttu-id="38511-167">Programda adımla</span><span class="sxs-lookup"><span data-stu-id="38511-167">Step through a program</span></span>

<span data-ttu-id="38511-168">Visual Studio Ayrıca, bir program aracılığıyla satıra göre çizgi ve yürütmeyi izlemeye de olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="38511-168">Visual Studio also allows you to step line by line through a program and monitor its execution.</span></span> <span data-ttu-id="38511-169">Normalde, bir kesme noktası ayarlar ve program kodunuzun küçük bir bölümünde program akışını takip edersiniz.</span><span class="sxs-lookup"><span data-stu-id="38511-169">Ordinarily, you'd set a breakpoint and follow program flow through a small part of your program code.</span></span> <span data-ttu-id="38511-170">Programınız küçük olduğundan programın tamamında ilerlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38511-170">Since your program is small, you can step through the entire program.</span></span>

1. <span data-ttu-id="38511-171">**Hata ayıklama**  >  **adımını**seçin.</span><span class="sxs-lookup"><span data-stu-id="38511-171">Choose **Debug** > **Step Into**.</span></span> <span data-ttu-id="38511-172">Tek seferde bir ifadede hata ayıklamanın başka bir yolu da **F11**tuşuna basılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="38511-172">Another way to debug one statement at a time is by pressing **F11**.</span></span>

   <span data-ttu-id="38511-173">Visual Studio, sonraki yürütme satırının yanında bir ok görüntüler.</span><span class="sxs-lookup"><span data-stu-id="38511-173">Visual Studio highlights and displays an arrow beside the next line of execution.</span></span>

   <span data-ttu-id="38511-174">C#</span><span class="sxs-lookup"><span data-stu-id="38511-174">C#</span></span>

   ![Visual Studio Step into yöntemi-C #](./media/debugging-with-visual-studio/step-into-method.png)

   <span data-ttu-id="38511-176">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="38511-176">Visual Basic</span></span>

   ![Visual Studio adımla yöntemi-Visual Basic](./media/debugging-with-visual-studio/vb-step-into-method.png)

   <span data-ttu-id="38511-178">Bu noktada, **Yereller** penceresi `args` dizinin boş olduğunu ve `name` `date` varsayılan değerlere sahip olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="38511-178">At this point, the **Locals** window shows that the `args` array is empty, and `name` and `date` have default values.</span></span> <span data-ttu-id="38511-179">Ayrıca, Visual Studio boş bir konsol penceresi açtı.</span><span class="sxs-lookup"><span data-stu-id="38511-179">In addition, Visual Studio has opened a blank console window.</span></span>

1. <span data-ttu-id="38511-180">**F11**tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="38511-180">Press **F11**.</span></span> <span data-ttu-id="38511-181">Visual Studio artık bir sonraki yürütme satırını vurgulamaktadır.</span><span class="sxs-lookup"><span data-stu-id="38511-181">Visual Studio now highlights the next line of execution.</span></span> <span data-ttu-id="38511-182">**Yereller** penceresi değiştirilmez ve konsol penceresi boş kalır.</span><span class="sxs-lookup"><span data-stu-id="38511-182">The **Locals** window is unchanged, and the console window remains blank.</span></span>

   <span data-ttu-id="38511-183">C#</span><span class="sxs-lookup"><span data-stu-id="38511-183">C#</span></span>

   ![Metot kaynağı-C içindeki Visual Studio adımı #](./media/debugging-with-visual-studio/step-into-source-method.png)

   <span data-ttu-id="38511-185">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="38511-185">Visual Basic</span></span>

   ![Visual Studio adımla Yöntem kaynağı-Visual Basic](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. <span data-ttu-id="38511-187">**F11**tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="38511-187">Press **F11**.</span></span> <span data-ttu-id="38511-188">Visual Studio, değişken atamasını içeren ifadeyi vurgular `name` .</span><span class="sxs-lookup"><span data-stu-id="38511-188">Visual Studio highlights the statement that includes the `name` variable assignment.</span></span> <span data-ttu-id="38511-189">**Yereller** penceresi olduğunu gösterir `name` `null` ve konsol penceresi "adınız nedir?" dizesini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="38511-189">The **Locals** window shows that `name` is `null`, and the console window displays the string "What is your name?".</span></span>

1. <span data-ttu-id="38511-190">Konsol penceresine bir dize girerek ve **ENTER**' a basarak istemi yanıtlayın.</span><span class="sxs-lookup"><span data-stu-id="38511-190">Respond to the prompt by entering a string in the console window and pressing **Enter**.</span></span> <span data-ttu-id="38511-191">Konsol yanıt vermiyor ve girdiğiniz dize konsol penceresinde görüntülenmiyor, ancak <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> Yöntem yine de girişinizi yakalayacak.</span><span class="sxs-lookup"><span data-stu-id="38511-191">The console is unresponsive, and the string you entered isn't displayed in the console window, but the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method will nevertheless capture your input.</span></span>

1. <span data-ttu-id="38511-192">**F11**tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="38511-192">Press **F11**.</span></span> <span data-ttu-id="38511-193">Visual Studio, `date` değişken atamasını (Visual Basic) içeren ifadeyi vurgular `currentDate` .</span><span class="sxs-lookup"><span data-stu-id="38511-193">Visual Studio highlights the statement that includes the `date` variable assignment (`currentDate` in Visual Basic).</span></span> <span data-ttu-id="38511-194">**Yereller** penceresi, yöntemi çağrısının döndürdüğü değeri gösterir <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="38511-194">The **Locals** window shows the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="38511-195">Konsol penceresinde, isteminde girdiğiniz dize de görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="38511-195">The console window also displays the string you entered at the prompt.</span></span>

1. <span data-ttu-id="38511-196">**F11**tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="38511-196">Press **F11**.</span></span> <span data-ttu-id="38511-197">**Yereller** penceresi, `date` özelliğinden atamasından sonra değişkenin değerini gösterir <xref:System.DateTime.Now?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="38511-197">The **Locals** window shows the value of the `date` variable after the assignment from the <xref:System.DateTime.Now?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="38511-198">Konsol penceresi değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="38511-198">The console window is unchanged.</span></span>

1. <span data-ttu-id="38511-199">**F11**tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="38511-199">Press **F11**.</span></span> <span data-ttu-id="38511-200">Visual Studio yöntemini çağırır <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="38511-200">Visual Studio calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="38511-201">Konsol penceresi biçimlendirilen dizeyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="38511-201">The console window displays the formatted string.</span></span>

1. <span data-ttu-id="38511-202">**Hata ayıklama**  >  **adımını**seçin. Adım adım yürütmeyi durdurmaya yönelik başka bir yöntem de **SHIFT** + **F11**tuşuna basmaktır.</span><span class="sxs-lookup"><span data-stu-id="38511-202">Choose **Debug** > **Step Out**. Another way to stop step-by-step execution is by pressing **Shift**+**F11**.</span></span>

   <span data-ttu-id="38511-203">Konsol penceresinde bir ileti görüntülenir ve bir tuşa basmanız bekler.</span><span class="sxs-lookup"><span data-stu-id="38511-203">The console window displays a message and waits for you to press a key.</span></span>

1. <span data-ttu-id="38511-204">Herhangi bir tuşa basarak konsol penceresini kapatın ve hata ayıklamayı durdurun.</span><span class="sxs-lookup"><span data-stu-id="38511-204">Press any key to close the console window and stop debugging.</span></span>

## <a name="build-a-release-version"></a><span data-ttu-id="38511-205">Yayın sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="38511-205">Build a Release version</span></span>

<span data-ttu-id="38511-206">Uygulamanızın hata ayıklama sürümünü sınadıktan sonra yayın sürümünü derleyip test etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="38511-206">Once you've tested the Debug version of your application, you should also compile and test the Release version.</span></span> <span data-ttu-id="38511-207">Yayın sürümü bazen bir uygulamanın davranışını olumsuz yönde etkileyebilecek derleyici iyileştirmeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="38511-207">The Release version incorporates compiler optimizations that can sometimes negatively affect the behavior of an application.</span></span> <span data-ttu-id="38511-208">Örneğin, performansı artırmak için tasarlanan derleyici iyileştirmeleri, çok iş parçacıklı uygulamalarda yarış koşulları oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="38511-208">For example, compiler optimizations that are designed to improve performance can create race conditions in multithreaded applications.</span></span>

<span data-ttu-id="38511-209">Konsol uygulamanızın yayın sürümünü derlemek ve test etmek için, araç çubuğundaki derleme yapılandırmasını **Hata Ayıkla** 'dan **Release**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="38511-209">To build and test the Release version of your console application, change the build configuration on the toolbar from **Debug** to **Release**.</span></span>

![hata ayıklama vurgulanmış olarak varsayılan Visual Studio araç çubuğu](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

<span data-ttu-id="38511-211">**F5** tuşuna bastığınızda veya **Build** menüsünden **çözüm oluştur** ' u seçtiğinizde, Visual Studio uygulamanın yayın sürümünü derler.</span><span class="sxs-lookup"><span data-stu-id="38511-211">When you press **F5** or choose **Build Solution** from the **Build** menu, Visual Studio compiles the Release version of the application.</span></span> <span data-ttu-id="38511-212">Hata ayıklama sürümünü yaptığınız gibi test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38511-212">You can test it as you did the Debug version.</span></span>

## <a name="next-steps"></a><span data-ttu-id="38511-213">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="38511-213">Next steps</span></span>

<span data-ttu-id="38511-214">Bu öğreticide, Visual Studio hata ayıklama araçları 'nı kullandınız.</span><span class="sxs-lookup"><span data-stu-id="38511-214">In this tutorial, you used Visual Studio debugging tools.</span></span> <span data-ttu-id="38511-215">Sonraki öğreticide, uygulamanın dağıtılabilir bir sürümünü yayımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="38511-215">In the next tutorial, you publish a deployable version of the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="38511-216">Visual Studio ile bir .NET Core konsol uygulaması yayımlama</span><span class="sxs-lookup"><span data-stu-id="38511-216">Publish a .NET Core console application with Visual Studio</span></span>](publishing-with-visual-studio.md)
