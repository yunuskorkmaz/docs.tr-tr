---
title: Visual Studio Code kullanarak bir .NET konsol uygulamasında hata ayıklama
description: Visual Studio Code kullanarak bir .NET konsol uygulamasında hata ayıklamayı öğrenin.
ms.date: 05/26/2020
ms.openlocfilehash: 7215ed4a93b31ebac313c04708734667148c4e02
ms.sourcegitcommit: 30fef5b0ed76e334377d28fa8e80159b29353e10
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96556115"
---
# <a name="tutorial-debug-a-net-console-application-using-visual-studio-code"></a><span data-ttu-id="d2fc8-103">Öğretici: Visual Studio Code kullanarak bir .NET konsol uygulamasında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="d2fc8-103">Tutorial: Debug a .NET console application using Visual Studio Code</span></span>

<span data-ttu-id="d2fc8-104">Bu öğreticide, .NET uygulamalarıyla çalışmak üzere Visual Studio Code sağlanan hata ayıklama araçları tanıtılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-104">This tutorial introduces the debugging tools available in Visual Studio Code for working with .NET apps.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d2fc8-105">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="d2fc8-105">Prerequisites</span></span>

- <span data-ttu-id="d2fc8-106">Bu öğretici, [Visual Studio Code kullanarak bir .NET konsol uygulaması oluşturma](with-visual-studio-code.md)bölümünde oluşturduğunuz konsol uygulamasıyla birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-106">This tutorial works with the console app that you create in [Create a .NET console application using Visual Studio Code](with-visual-studio-code.md).</span></span>

## <a name="use-debug-build-configuration"></a><span data-ttu-id="d2fc8-107">Hata ayıklama derleme yapılandırmasını kullan</span><span class="sxs-lookup"><span data-stu-id="d2fc8-107">Use Debug build configuration</span></span>

<span data-ttu-id="d2fc8-108">*Hata ayıklama* ve *yayın* .NET Core 'un yerleşik derleme yapılandırmalarıdır.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-108">*Debug* and *Release* are .NET Core's built-in build configurations.</span></span> <span data-ttu-id="d2fc8-109">Hata ayıklama oluşturma yapılandırması hata ayıklama için ve son sürüm dağıtımı için sürüm yapılandırması ' nı kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-109">You use the Debug build configuration for debugging and the Release configuration for the final release distribution.</span></span>

<span data-ttu-id="d2fc8-110">Hata ayıklama yapılandırmasında, bir program tam sembolik hata ayıklama bilgileriyle derlenir ve iyileştirmesi yoktur.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-110">In the Debug configuration, a program compiles with full symbolic debug information and no optimization.</span></span> <span data-ttu-id="d2fc8-111">Kaynak kodu ve oluşturulan yönergeler arasındaki ilişki daha karmaşık olduğundan iyileştirme, hata ayıklamayı karmaşıklaştırır.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-111">Optimization complicates debugging, because the relationship between source code and generated instructions is more complex.</span></span> <span data-ttu-id="d2fc8-112">Bir programın yayın yapılandırmasında sembolik hata ayıklama bilgisi yoktur ve tamamen iyileştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-112">The release configuration of a program has no symbolic debug information and is fully optimized.</span></span>

<span data-ttu-id="d2fc8-113">Varsayılan olarak, Visual Studio Code başlatma ayarları hata ayıklama derleme yapılandırmasını kullanır, bu nedenle hata ayıklamadan önce değiştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-113">By default, Visual Studio Code launch settings use the Debug build configuration, so you don't need to change it before debugging.</span></span>

1. <span data-ttu-id="d2fc8-114">Visual Studio Code’u başlatın.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-114">Start Visual Studio Code.</span></span>

1. <span data-ttu-id="d2fc8-115">[Visual Studio Code kullanarak .NET konsol uygulaması oluşturma](with-visual-studio-code.md)bölümünde oluşturduğunuz projenin klasörünü açın.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-115">Open the folder of the project that you created in [Create a .NET console application using Visual Studio Code](with-visual-studio-code.md).</span></span>

## <a name="set-a-breakpoint"></a><span data-ttu-id="d2fc8-116">Kesme noktası ayarlama</span><span class="sxs-lookup"><span data-stu-id="d2fc8-116">Set a breakpoint</span></span>

<span data-ttu-id="d2fc8-117">Kesme *noktası,* kesme noktası olan satır yürütülmeden önce uygulamanın yürütülmesini geçici olarak keser.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-117">A *breakpoint* temporarily interrupts the execution of the application before the line with the breakpoint is executed.</span></span>

1. <span data-ttu-id="d2fc8-118">*Program.cs* dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-118">Open the *Program.cs* file.</span></span>

1. <span data-ttu-id="d2fc8-119">Kod penceresinin sol kenar boşluğuna tıklayarak adı, tarihi ve saati gösteren satırda bir *kesme noktası* ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-119">Set a *breakpoint* on the line that displays the name, date, and time, by clicking in the left margin of the code window.</span></span> <span data-ttu-id="d2fc8-120">Sol kenar boşluğu satır numaralarının solunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-120">The left margin is to the left of the line numbers.</span></span> <span data-ttu-id="d2fc8-121">Bir kesme noktası ayarlamak için diğer yollar <kbd>F9</kbd> tuşuna basarak veya **Run**  >  kod satırı seçiliyken menüden **geçiş kesme noktası** Çalıştır ' i seçmektir.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-121">Other ways to set a breakpoint are by pressing <kbd>F9</kbd> or choosing **Run** > **Toggle Breakpoint** from the menu while the line of code is selected.</span></span>

   <span data-ttu-id="d2fc8-122">Visual Studio Code, sol kenar boşluğunda kırmızı bir nokta görüntüleyerek kesme noktasının ayarlandığı satırı gösterir.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-122">Visual Studio Code indicates the line on which the breakpoint is set by displaying a red dot in the left margin.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-set.png" alt-text="Kesme noktası kümesi":::

## <a name="set-up-for-terminal-input"></a><span data-ttu-id="d2fc8-124">Terminal girişi için ayarlama</span><span class="sxs-lookup"><span data-stu-id="d2fc8-124">Set up for terminal input</span></span>

<span data-ttu-id="d2fc8-125">Kesme noktası bir `Console.ReadLine` Yöntem çağrısından sonra bulunur.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-125">The breakpoint is located after a `Console.ReadLine` method call.</span></span> <span data-ttu-id="d2fc8-126">**Hata ayıklama konsolu** çalışan bir program için Terminal girişini kabul etmez.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-126">The **Debug Console** doesn't accept terminal input for a running program.</span></span> <span data-ttu-id="d2fc8-127">Hata ayıklama sırasında terminal girişini işlemek için tümleşik terminali (Visual Studio Code pencerelerinden birisi) veya bir dış terminali kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-127">To handle terminal input while debugging, you can use the integrated terminal (one of the Visual Studio Code windows) or an external terminal.</span></span> <span data-ttu-id="d2fc8-128">Bu öğreticide, tümleşik terminal kullanacağız.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-128">For this tutorial, you use the integrated terminal.</span></span>

1. <span data-ttu-id="d2fc8-129">*.vscode/launch.json* dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-129">Open *.vscode/launch.json*.</span></span>

1. <span data-ttu-id="d2fc8-130">`console`Ayarını `internalConsole` olarak değiştirin `integratedTerminal` :</span><span class="sxs-lookup"><span data-stu-id="d2fc8-130">Change the `console` setting from `internalConsole` to `integratedTerminal`:</span></span>

   ```json
   "console": "integratedTerminal",
   ```

1. <span data-ttu-id="d2fc8-131">Yaptığınız değişiklikleri kaydedin.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-131">Save your changes.</span></span>

## <a name="start-debugging"></a><span data-ttu-id="d2fc8-132">Hata ayıklamayı Başlat</span><span class="sxs-lookup"><span data-stu-id="d2fc8-132">Start debugging</span></span>

1. <span data-ttu-id="d2fc8-133">Sol taraftaki menüdeki hata ayıklama simgesini seçerek hata ayıklama görünümünü açın.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-133">Open the Debug view by selecting the Debugging icon on the left side menu.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/select-debug-pane.png" alt-text="Visual Studio Code hata ayıkla sekmesini açın":::

1. <span data-ttu-id="d2fc8-135">Bölmenin üst kısmındaki yeşil oku seçerek **.NET Core başlatma (konsol)**' nin yanına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-135">Select the green arrow at the top of the pane, next to **.NET Core Launch (console)**.</span></span> <span data-ttu-id="d2fc8-136">Programı hata ayıklama modunda başlatmak için diğer yollar <kbd>F5</kbd> tuşuna basarak veya **Run**  >  menüden **hata ayıklamayı Başlat** Çalıştır ' i seçmekten yapılır.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-136">Other ways to start the program in debugging mode are by pressing <kbd>F5</kbd> or choosing **Run** > **Start Debugging** from the menu.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/start-debugging.png" alt-text="Hata ayıklamayı Başlat":::

1. <span data-ttu-id="d2fc8-138">"Adınız nedir?" öğesini görmek için **Terminal** sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-138">Select the **Terminal** tab to see the "What is your name?"</span></span> <span data-ttu-id="d2fc8-139">programın yanıt beklemeden önce görüntülediğini iste.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-139">prompt that the program displays before waiting for a response.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/select-terminal.png" alt-text="Terminal sekmesini seçin":::

1. <span data-ttu-id="d2fc8-141">Bir ad istemine yanıt olarak **Terminal** penceresine bir dize girin ve ardından <kbd>ENTER</kbd>tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-141">Enter a string in the **Terminal** window in response to the prompt for a name, and then press <kbd>Enter</kbd>.</span></span>

   <span data-ttu-id="d2fc8-142">Program yürütme, kesme noktasına ulaştığında ve Yöntem yürütmeden önce duraklar `Console.WriteLine` .</span><span class="sxs-lookup"><span data-stu-id="d2fc8-142">Program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span> <span data-ttu-id="d2fc8-143">**Değişkenler** penceresinin **Yereller** bölümü, yürütülmekte olan yöntemde tanımlanan değişkenlerin değerlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-143">The **Locals** section of the **Variables** window displays the values of variables that are defined in the currently executing method.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-hit.png" alt-text="Yerelleri gösteren kesme noktası isabet":::

## <a name="use-the-debug-console"></a><span data-ttu-id="d2fc8-145">Hata ayıklama konsolunu kullanma</span><span class="sxs-lookup"><span data-stu-id="d2fc8-145">Use the Debug Console</span></span>

<span data-ttu-id="d2fc8-146">**Hata ayıklama konsolu** penceresi, hata ayıkladığınızda uygulamayla etkileşime girebilmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-146">The **Debug Console** window lets you interact with the application you're debugging.</span></span> <span data-ttu-id="d2fc8-147">Programınızı nasıl etkileyeceğini görmek için değişkenlerin değerini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-147">You can change the value of variables to see how it affects your program.</span></span>

1. <span data-ttu-id="d2fc8-148">**Hata ayıklama konsolu** sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-148">Select the **Debug Console** tab.</span></span>

1. <span data-ttu-id="d2fc8-149">`name = "Gracie"` **Hata ayıklama konsolu** penceresinin en altındaki Istemine yazın ve <kbd>ENTER</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-149">Enter `name = "Gracie"` at the prompt at the bottom of the **Debug Console** window and press the <kbd>Enter</kbd> key.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/change-variable-values.png" alt-text="Değişken değerlerini Değiştir":::

1. <span data-ttu-id="d2fc8-151">`date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` **Hata ayıklama konsolu** penceresinin alt kısmına girin ve <kbd>ENTER</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-151">Enter `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` at the bottom of the **Debug Console** window and press the <kbd>Enter</kbd> key.</span></span>

   <span data-ttu-id="d2fc8-152">**Değişkenler** penceresi, ve değişkenlerinin yeni değerlerini görüntüler `name` `date` .</span><span class="sxs-lookup"><span data-stu-id="d2fc8-152">The **Variables** window displays the new values of the `name` and `date` variables.</span></span>

1. <span data-ttu-id="d2fc8-153">Araç çubuğundaki **devam** düğmesini seçerek program yürütmeye devam edin.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-153">Continue program execution by selecting the **Continue** button in the toolbar.</span></span> <span data-ttu-id="d2fc8-154">Devam etmenin başka bir yolu da <kbd>F5</kbd>'e basılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-154">Another way to continue is by pressing <kbd>F5</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/continue-debugging.png" alt-text="Hata ayıklamaya devam et":::

1. <span data-ttu-id="d2fc8-156">**Terminal** sekmesini yeniden seçin.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-156">Select the **Terminal** tab again.</span></span>

   <span data-ttu-id="d2fc8-157">Konsol penceresinde görünen değerler, **hata ayıklama konsolunda** yaptığınız değişikliklere karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-157">The values displayed in the console window correspond to the changes you made in the **Debug Console**.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/changed-variable-values.png" alt-text="Girilen değerleri gösteren Terminal":::

1. <span data-ttu-id="d2fc8-159">Uygulamadan çıkmak ve hata ayıklamayı durdurmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-159">Press any key to exit the application and stop debugging.</span></span>

## <a name="set-a-conditional-breakpoint"></a><span data-ttu-id="d2fc8-160">Koşullu kesme noktası ayarlama</span><span class="sxs-lookup"><span data-stu-id="d2fc8-160">Set a conditional breakpoint</span></span>

<span data-ttu-id="d2fc8-161">Program, kullanıcının girdiği dizeyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-161">The program displays the string that the user enters.</span></span> <span data-ttu-id="d2fc8-162">Kullanıcı hiçbir şey girmezse ne olur?</span><span class="sxs-lookup"><span data-stu-id="d2fc8-162">What happens if the user doesn't enter anything?</span></span> <span data-ttu-id="d2fc8-163">Bunu, *koşullu kesme noktası* adında yararlı bir hata ayıklama özelliği ile test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-163">You can test this with a useful debugging feature called a *conditional breakpoint*.</span></span>

1. <span data-ttu-id="d2fc8-164">Kesme noktasını temsil eden kırmızı nokta üzerinde sağ tıklayın (macOS üzerinde<kbd>CTRL</kbd>+ tıklama).</span><span class="sxs-lookup"><span data-stu-id="d2fc8-164">Right-click (<kbd>Ctrl</kbd>-click on macOS) on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="d2fc8-165">Bağlam menüsünde, bir koşullu ifade girmenize izin veren bir iletişim kutusu açmak için **kesme noktasını Düzenle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-165">In the context menu, select **Edit Breakpoint** to open a dialog that lets you enter a conditional expression.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-context-menu.png" alt-text="Kesme noktası bağlam menüsü":::

1. <span data-ttu-id="d2fc8-167">`Expression`Açılan kutudan seçim yapın, aşağıdaki koşullu ifadeyi girin ve <kbd>ENTER</kbd>tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-167">Select `Expression` in the drop-down, enter the following conditional expression, and press <kbd>Enter</kbd>.</span></span>

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   :::image type="content" source="media/debugging-with-visual-studio-code/conditional-expression.png" alt-text="Koşullu bir ifade girin":::

   <span data-ttu-id="d2fc8-169">Kesme noktası her isabet edildiğinde, hata ayıklayıcı `String.IsNullOrEmpty(name)` yöntemini çağırır ve yalnızca Yöntem çağrısı döndürürse bu satırı keser `true` .</span><span class="sxs-lookup"><span data-stu-id="d2fc8-169">Each time the breakpoint is hit, the debugger calls the `String.IsNullOrEmpty(name)` method, and it breaks on this line only if the method call returns `true`.</span></span>

   <span data-ttu-id="d2fc8-170">Koşullu bir ifade yerine, bir deyim belirtilen sayıda yürütülmeden önce program yürütmeyi kesen bir *isabet sayısı* belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-170">Instead of a conditional expression, you can specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times.</span></span> <span data-ttu-id="d2fc8-171">Diğer bir seçenek de bir *filtre koşulu* belirtmektir. Bu, iş parçacığı tanımlayıcısı, işlem adı veya iş parçacığı adı olarak bu tür özniteliklere dayalı olarak program yürütmeyi keser.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-171">Another option is to specify a *filter condition*, which interrupts program execution based on such attributes as a thread identifier, process name, or thread name.</span></span>

1. <span data-ttu-id="d2fc8-172"><kbd>F5</kbd>'e basarak programı hata ayıklama ile başlatın.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-172">Start the program with debugging by pressing <kbd>F5</kbd>.</span></span>

1. <span data-ttu-id="d2fc8-173">Adınızı girmeniz istendiğinde, **Terminal** sekmesinde <kbd>ENTER</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-173">In the **Terminal** tab, press the <kbd>Enter</kbd> key when prompted to enter your name.</span></span>

   <span data-ttu-id="d2fc8-174">Belirttiğiniz koşul ( `name` veya ya da `null` <xref:System.String.Empty?displayProperty=nameWithType> ) karşılandığından, program yürütmesi kesme noktasına ulaştığında ve Yöntem yürütülmeden önce durduktan sonra duraklar `Console.WriteLine` .</span><span class="sxs-lookup"><span data-stu-id="d2fc8-174">Because the condition you specified (`name` is either `null` or <xref:System.String.Empty?displayProperty=nameWithType>) has been satisfied, program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span>

   <span data-ttu-id="d2fc8-175">**Değişkenler** penceresi `name` , değişkeninin değerinin veya olduğunu gösterir `""` <xref:System.String.Empty?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="d2fc8-175">The **Variables** window shows that the value of the `name` variable is `""`, or <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

1. <span data-ttu-id="d2fc8-176">**Hata ayıklama konsolu** istemine aşağıdaki ifadeyi girerek ve <kbd>ENTER</kbd>tuşuna basarak değerin boş bir dize olduğunu onaylayın.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-176">Confirm the value is an empty string by entering the following statement at the **Debug Console** prompt and pressing <kbd>Enter</kbd>.</span></span> <span data-ttu-id="d2fc8-177">Sonuç olarak `true` .</span><span class="sxs-lookup"><span data-stu-id="d2fc8-177">The result is `true`.</span></span>

   ```csharp
   name == String.Empty
   ```

   :::image type="content" source="media/debugging-with-visual-studio-code/expression-in-debug-console.png" alt-text="Deyimden sonra true değeri döndüren hata ayıklama konsolu":::

1. <span data-ttu-id="d2fc8-179">Program yürütmeye devam etmek için araç çubuğundaki **devam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-179">Select the **Continue** button on the toolbar to continue program execution.</span></span>

1. <span data-ttu-id="d2fc8-180">**Terminal** sekmesini seçin ve herhangi bir tuşa basarak programdan çıkın ve hata ayıklamayı durdurun.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-180">Select the **Terminal** tab, and press any key to exit the program and stop debugging.</span></span>

1. <span data-ttu-id="d2fc8-181">Kod penceresinin sol kenarındaki noktaya tıklayarak kesme noktasını temizleyin.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-181">Clear the breakpoint by clicking on the dot in the left margin of the code window.</span></span> <span data-ttu-id="d2fc8-182">Bir kesme noktasını temizlemek için diğer yollar, kod satırı seçiliyken <kbd>F9</kbd> tuşuna basarak veya menüden **kesme noktası** ' nı seçerek >.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-182">Other ways to clear a breakpoint are by pressing <kbd>F9</kbd> or choosing **Run > Toggle Breakpoint** from the menu while the line of code is selected.</span></span>

1. <span data-ttu-id="d2fc8-183">Kesme noktası koşulunun kaybolacağını belirten bir uyarı alırsanız, **kesme noktasını kaldır**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-183">If you get a warning that the breakpoint condition will be lost, select **Remove Breakpoint**.</span></span>

## <a name="step-through-a-program"></a><span data-ttu-id="d2fc8-184">Programda adımla</span><span class="sxs-lookup"><span data-stu-id="d2fc8-184">Step through a program</span></span>

<span data-ttu-id="d2fc8-185">Visual Studio Code Ayrıca, bir program aracılığıyla satır içine girerek ve yürütmesini izlemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-185">Visual Studio Code also allows you to step line by line through a program and monitor its execution.</span></span> <span data-ttu-id="d2fc8-186">Normalde, bir kesme noktası ayarlar ve program kodunuzun küçük bir bölümünde program akışını takip edersiniz.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-186">Ordinarily, you'd set a breakpoint and follow program flow through a small part of your program code.</span></span> <span data-ttu-id="d2fc8-187">Bu program küçük olduğundan programın tamamında ilerlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-187">Since this program is small, you can step through the entire program.</span></span>

1. <span data-ttu-id="d2fc8-188">Metodun açılış küme ayracı üzerinde bir kesme noktası ayarlayın `Main` .</span><span class="sxs-lookup"><span data-stu-id="d2fc8-188">Set a breakpoint on the opening curly brace of the `Main` method.</span></span>

1. <span data-ttu-id="d2fc8-189">Hata ayıklamaya başlamak için <kbd>F5</kbd>'e basın.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-189">Press <kbd>F5</kbd> to start debugging.</span></span>

   <span data-ttu-id="d2fc8-190">Visual Studio Code kesme çizgisi çizgisini vurgular.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-190">Visual Studio Code highlights the breakpoint line.</span></span>

   <span data-ttu-id="d2fc8-191">Bu noktada, **değişkenler** penceresi `args` dizinin boş olduğunu ve `name` `date` varsayılan değerlere sahip olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-191">At this point, the **Variables** window shows that the `args` array is empty, and `name` and `date` have default values.</span></span>

1. <span data-ttu-id="d2fc8-192">Adımla **Çalıştır**' ı seçin  >  **Step Into** veya <kbd>F11</kbd>tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-192">Select **Run** > **Step Into** or press <kbd>F11</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/step-into.png" alt-text="Adımla düğmesi":::

   <span data-ttu-id="d2fc8-194">Visual Studio Code sonraki satırı vurgular.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-194">Visual Studio Code highlights the next line.</span></span>

1. <span data-ttu-id="d2fc8-195">Adımla **Çalıştır**' ı seçin  >  **Step Into** veya <kbd>F11</kbd>tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-195">Select **Run** > **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="d2fc8-196">Visual Studio Code, `Console.WriteLine` ad istemi için öğesini yürütür ve sonraki yürütme satırını vurgular.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-196">Visual Studio Code executes the `Console.WriteLine` for the name prompt and highlights the next line of execution.</span></span> <span data-ttu-id="d2fc8-197">Sonraki satır, `Console.ReadLine` içindir `name` .</span><span class="sxs-lookup"><span data-stu-id="d2fc8-197">The next line is the `Console.ReadLine` for the `name`.</span></span> <span data-ttu-id="d2fc8-198">**Değişkenler** penceresi değiştirilmez ve **Terminal** sekmesi "adınız nedir?" olarak gösterilir.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-198">The **Variables** window is unchanged, and the **Terminal** tab shows the "What is your name?"</span></span> <span data-ttu-id="d2fc8-199">ekran görüntüsü.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-199">prompt.</span></span>

1. <span data-ttu-id="d2fc8-200">Adımla **Çalıştır**' ı seçin  >  **Step Into** veya <kbd>F11</kbd>tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-200">Select **Run** > **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="d2fc8-201">Visual Studio, `name` değişken atamasını vurgular.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-201">Visual Studio highlights the `name` variable assignment.</span></span> <span data-ttu-id="d2fc8-202">**Değişkenler** penceresi hala olduğunu gösterir `name` `null` .</span><span class="sxs-lookup"><span data-stu-id="d2fc8-202">The **Variables** window shows that `name` is still `null`.</span></span>

1. <span data-ttu-id="d2fc8-203">Terminal sekmesine bir dize girerek ve <kbd>ENTER</kbd>' a basarak istemi yanıtlayın.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-203">Respond to the prompt by entering a string in the Terminal tab and pressing <kbd>Enter</kbd>.</span></span>

   <span data-ttu-id="d2fc8-204">**Terminal** sekmesi, girerken girdiğiniz dizeyi görüntülemeyebilir, ancak <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> Yöntem girişinizi yakalar.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-204">The **Terminal** tab might not display the string you enter while you're entering it, but the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method will capture your input.</span></span>

1. <span data-ttu-id="d2fc8-205">Adımla **Çalıştır**' ı seçin  >  **Step Into** veya <kbd>F11</kbd>tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-205">Select **Run** > **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="d2fc8-206">Visual Studio Code, `date` değişken atamasını vurgular.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-206">Visual Studio Code highlights the `date` variable assignment.</span></span> <span data-ttu-id="d2fc8-207">**Değişkenler** penceresi, yöntemine yapılan çağrı tarafından döndürülen değeri gösterir <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="d2fc8-207">The **Variables** window shows the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d2fc8-208">**Terminal** sekmesi, istemde girdiğiniz dizeyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-208">The **Terminal** tab displays the string you entered at the prompt.</span></span>

1. <span data-ttu-id="d2fc8-209">Adımla **Çalıştır**' ı seçin  >  **Step Into** veya <kbd>F11</kbd>tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-209">Select **Run** > **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="d2fc8-210">**Değişkenler** penceresi, `date` özelliğinden atamadan sonraki değişkenin değerini gösterir <xref:System.DateTime.Now?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="d2fc8-210">The **Variables** window shows the value of the `date` variable after the assignment from the <xref:System.DateTime.Now?displayProperty=nameWithType> property.</span></span>

1. <span data-ttu-id="d2fc8-211">Adımla **Çalıştır**' ı seçin  >  **Step Into** veya <kbd>F11</kbd>tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-211">Select **Run** > **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="d2fc8-212">Visual Studio Code yöntemini çağırır <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="d2fc8-212">Visual Studio Code calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d2fc8-213">Konsol penceresi biçimlendirilen dizeyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-213">The console window displays the formatted string.</span></span>

1. <span data-ttu-id="d2fc8-214">**Çalışma adımını Çalıştır**' ı seçin  >  **Step Out** veya <kbd>SHIFT</kbd> + <kbd>F11</kbd>tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-214">Select **Run** > **Step Out** or press <kbd>Shift</kbd>+<kbd>F11</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/step-out.png" alt-text="Adımla düğmesi":::

1. <span data-ttu-id="d2fc8-216">**Terminal** sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-216">Select the **Terminal** tab.</span></span>

   <span data-ttu-id="d2fc8-217">Terminal "çıkmak için herhangi bir tuşa basın..." şeklinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-217">The terminal displays "Press any key to exit..."</span></span>

1. <span data-ttu-id="d2fc8-218">Programdan çıkmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-218">Press any key to exit the program.</span></span>

## <a name="use-release-build-configuration"></a><span data-ttu-id="d2fc8-219">Yayın derleme yapılandırmasını kullan</span><span class="sxs-lookup"><span data-stu-id="d2fc8-219">Use Release build configuration</span></span>

<span data-ttu-id="d2fc8-220">Uygulamanızın hata ayıklama sürümünü sınadıktan sonra yayın sürümünü derleyip test etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-220">Once you've tested the Debug version of your application, you should also compile and test the Release version.</span></span> <span data-ttu-id="d2fc8-221">Yayın sürümü, bir uygulamanın davranışını etkileyebilecek derleyici iyileştirmeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-221">The Release version incorporates compiler optimizations that can affect the behavior of an application.</span></span> <span data-ttu-id="d2fc8-222">Örneğin, performansı artırmak için tasarlanan derleyici iyileştirmeleri, çok iş parçacıklı uygulamalarda yarış koşulları oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-222">For example, compiler optimizations that are designed to improve performance can create race conditions in multithreaded applications.</span></span>

<span data-ttu-id="d2fc8-223">Konsol uygulamanızın yayın sürümünü derlemek ve test etmek için **terminali** açın ve şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="d2fc8-223">To build and test the Release version of your console application, open the **Terminal** and run the following command:</span></span>

```dotnetcli
dotnet run --configuration Release
```

## <a name="additional-resources"></a><span data-ttu-id="d2fc8-224">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="d2fc8-224">Additional resources</span></span>

* [<span data-ttu-id="d2fc8-225">Visual Studio Code 'de hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="d2fc8-225">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/docs/editor/debugging)

## <a name="next-steps"></a><span data-ttu-id="d2fc8-226">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="d2fc8-226">Next steps</span></span>

<span data-ttu-id="d2fc8-227">Bu öğreticide hata ayıklama araçları Visual Studio Code kullandınız.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-227">In this tutorial, you used Visual Studio Code debugging tools.</span></span> <span data-ttu-id="d2fc8-228">Sonraki öğreticide, uygulamanın dağıtılabilir bir sürümünü yayımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="d2fc8-228">In the next tutorial, you publish a deployable version of the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d2fc8-229">Visual Studio Code kullanarak bir .NET konsol uygulaması yayımlama</span><span class="sxs-lookup"><span data-stu-id="d2fc8-229">Publish a .NET console application using Visual Studio Code</span></span>](publishing-with-visual-studio-code.md)
