---
title: Visual Studio Code ile bir .NET Core konsol uygulamasında hata ayıklama
description: Visual Studio Code bir .NET Core konsol uygulamasında hata ayıklamayı öğrenin.
ms.date: 05/26/2020
ms.openlocfilehash: 82b2798397d702aa2a50c04bf6e4d569b97e3666
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241519"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio-code"></a><span data-ttu-id="dc117-103">Öğretici: Visual Studio Code kullanarak bir .NET Core konsol uygulamasında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="dc117-103">Tutorial: Debug a .NET Core console application using Visual Studio Code</span></span>

<span data-ttu-id="dc117-104">Bu öğreticide, .NET Core uygulamalarıyla çalışmak üzere Visual Studio Code sağlanan hata ayıklama araçları tanıtılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dc117-104">This tutorial introduces the debugging tools available in Visual Studio Code for working with .NET Core apps.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dc117-105">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="dc117-105">Prerequisites</span></span>

- <span data-ttu-id="dc117-106">Bu öğretici, [Visual Studio Code bir .NET Core konsol uygulaması oluşturma](with-visual-studio-code.md)bölümünde oluşturduğunuz konsol uygulamasıyla birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dc117-106">This tutorial works with the console app that you create in [Create a .NET Core console application in Visual Studio Code](with-visual-studio-code.md).</span></span>

## <a name="use-debug-build-configuration"></a><span data-ttu-id="dc117-107">Hata ayıklama derleme yapılandırmasını kullan</span><span class="sxs-lookup"><span data-stu-id="dc117-107">Use Debug build configuration</span></span>

<span data-ttu-id="dc117-108">*Hata ayıklama* ve *yayın* , .NET Core 'un derleme yapılandırmalarının ikýdýr.</span><span class="sxs-lookup"><span data-stu-id="dc117-108">*Debug* and *Release* are two of .NET Core's build configurations.</span></span> <span data-ttu-id="dc117-109">Hata ayıklama oluşturma yapılandırması hata ayıklama için ve son sürüm dağıtımı için sürüm yapılandırması ' nı kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="dc117-109">You use the Debug build configuration for debugging and the Release configuration for the final release distribution.</span></span>

<span data-ttu-id="dc117-110">Hata ayıklama yapılandırmasında, bir program tam sembolik hata ayıklama bilgileriyle derlenir ve iyileştirmesi yoktur.</span><span class="sxs-lookup"><span data-stu-id="dc117-110">In the Debug configuration, a program compiles with full symbolic debug information and no optimization.</span></span> <span data-ttu-id="dc117-111">Kaynak kodu ve oluşturulan yönergeler arasındaki ilişki daha karmaşık olduğundan iyileştirme, hata ayıklamayı karmaşıklaştırır.</span><span class="sxs-lookup"><span data-stu-id="dc117-111">Optimization complicates debugging, because the relationship between source code and generated instructions is more complex.</span></span> <span data-ttu-id="dc117-112">Bir programın yayın yapılandırmasında sembolik hata ayıklama bilgisi yoktur ve tamamen iyileştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="dc117-112">The release configuration of a program has no symbolic debug information and is fully optimized.</span></span>

 <span data-ttu-id="dc117-113">Varsayılan olarak, Visual Studio Code hata ayıklama derleme yapılandırmasını kullanır, bu nedenle hata ayıklamadan önce değiştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="dc117-113">By default, Visual Studio Code uses the Debug build configuration, so you don't need to change it before debugging.</span></span>

## <a name="set-a-breakpoint"></a><span data-ttu-id="dc117-114">Kesme noktası ayarlama</span><span class="sxs-lookup"><span data-stu-id="dc117-114">Set a breakpoint</span></span>

<span data-ttu-id="dc117-115">Kesme noktası, kesme noktası olan satır yürütülmeden *önce* uygulamanın yürütülmesini geçici olarak keser.</span><span class="sxs-lookup"><span data-stu-id="dc117-115">A breakpoint temporarily interrupts the execution of the application *before* the line with the breakpoint is executed.</span></span>

1. <span data-ttu-id="dc117-116">Visual Studio Code'u açın.</span><span class="sxs-lookup"><span data-stu-id="dc117-116">Open Visual Studio Code.</span></span>

1. <span data-ttu-id="dc117-117">[Visual Studio Code .NET Core konsol uygulaması oluşturma](with-visual-studio-code.md)bölümünde oluşturduğunuz *HelloWorld* proje klasörünü açın.</span><span class="sxs-lookup"><span data-stu-id="dc117-117">Open the *HelloWorld* project folder that you created in [Create a .NET Core console application in Visual Studio Code](with-visual-studio-code.md).</span></span>

1. <span data-ttu-id="dc117-118">*Program.cs* dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="dc117-118">Open the *Program.cs* file.</span></span>

1. <span data-ttu-id="dc117-119">Kod penceresinin sol kenar boşluğuna tıklayarak adı, tarihi ve saati gösteren satırda bir *kesme noktası* ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="dc117-119">Set a *breakpoint* on the line that displays the name, date, and time, by clicking in the left margin of the code window.</span></span> <span data-ttu-id="dc117-120">Sol kenar boşluğu satır numaralarının solunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="dc117-120">The left margin is to the left of the line numbers.</span></span> <span data-ttu-id="dc117-121">Bir kesme noktası ayarlamak için başka bir yol ise imleci kod satırına yerleştirip <kbd>F9</kbd>tuşuna basarak olur.</span><span class="sxs-lookup"><span data-stu-id="dc117-121">Another way to set a breakpoint is by placing the cursor in the line of code and then pressing <kbd>F9</kbd>.</span></span>

   <span data-ttu-id="dc117-122">Aşağıdaki görüntüde gösterildiği gibi, Visual Studio Code sol kenar boşluğunda kırmızı bir nokta görüntüleyerek kesme noktasının ayarlandığı satırı gösterir.</span><span class="sxs-lookup"><span data-stu-id="dc117-122">As the following image shows, Visual Studio Code indicates the line on which the breakpoint is set by displaying a red dot in the left margin.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-set.png" alt-text="Kesme noktası kümesi":::

## <a name="set-up-for-terminal-input"></a><span data-ttu-id="dc117-124">Terminal girişi için ayarlama</span><span class="sxs-lookup"><span data-stu-id="dc117-124">Set up for terminal input</span></span>

<span data-ttu-id="dc117-125">Kesme noktası bir `Console.ReadLine` Yöntem çağrısından sonra bulunur.</span><span class="sxs-lookup"><span data-stu-id="dc117-125">The breakpoint is located after a `Console.ReadLine` method call.</span></span> <span data-ttu-id="dc117-126">**Hata ayıklama konsolu** çalışan bir program için Terminal girişini kabul etmez.</span><span class="sxs-lookup"><span data-stu-id="dc117-126">The **Debug Console** doesn't accept terminal input for a running program.</span></span> <span data-ttu-id="dc117-127">Hata ayıklarken Terminal girişini işlemek için tümleşik Terminal (Visual Studio Code Windows) veya harici bir terminalde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc117-127">To handle terminal input while debugging, you can use the integrated terminal (one of the Visual Studio Code windows) or an external terminal.</span></span> <span data-ttu-id="dc117-128">Bu öğreticide, tümleşik Terminal kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dc117-128">For this tutorial, you use the integrated terminal.</span></span>

1. <span data-ttu-id="dc117-129">*. Vscode/Launch. JSON*dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="dc117-129">Open *.vscode/launch.json*.</span></span>

1. <span data-ttu-id="dc117-130">`console`Ayarını olarak değiştirin `integratedTerminal` .</span><span class="sxs-lookup"><span data-stu-id="dc117-130">Change the `console` setting to `integratedTerminal`.</span></span>

   <span data-ttu-id="dc117-131">Kimden:</span><span class="sxs-lookup"><span data-stu-id="dc117-131">From:</span></span>

   ```
   "console": "internalConsole",
   ```

   <span data-ttu-id="dc117-132">Hedef:</span><span class="sxs-lookup"><span data-stu-id="dc117-132">To:</span></span>

   ```
   "console": "integratedTerminal",
   ```

1. <span data-ttu-id="dc117-133">Yaptığınız değişiklikleri kaydedin.</span><span class="sxs-lookup"><span data-stu-id="dc117-133">Save your changes.</span></span>

## <a name="start-debugging"></a><span data-ttu-id="dc117-134">Hata ayıklamayı Başlat</span><span class="sxs-lookup"><span data-stu-id="dc117-134">Start debugging</span></span>

1. <span data-ttu-id="dc117-135">Sol taraftaki menüdeki hata ayıklama simgesini seçerek hata ayıklama görünümünü açın.</span><span class="sxs-lookup"><span data-stu-id="dc117-135">Open the Debug view by selecting the Debugging icon on the left side menu.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/select-debug-pane.png" alt-text="Visual Studio Code hata ayıkla sekmesini açın":::

1. <span data-ttu-id="dc117-137">**.NET Core başlatma (konsol)** yanındaki bölmenin üst kısmındaki yeşil oku seçerek hata ayıklamayı başlatın.</span><span class="sxs-lookup"><span data-stu-id="dc117-137">Start debugging by selecting the green arrow at the top of the pane, next to **.NET Core Launch (console)**.</span></span>  <span data-ttu-id="dc117-138">Hata ayıklamayı başlatmak için başka bir yol da <kbd>F5</kbd>'e basılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="dc117-138">Another way to start debugging is by pressing <kbd>F5</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/start-debugging.png" alt-text="Hata ayıklamayı Başlat":::

1. <span data-ttu-id="dc117-140">"Adınız nedir?" öğesini görmek için **Terminal** sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="dc117-140">Select the **Terminal** tab to see the "What is your name?"</span></span> <span data-ttu-id="dc117-141">programın yanıt beklemeden önce görüntülediğini iste.</span><span class="sxs-lookup"><span data-stu-id="dc117-141">prompt that the program displays before waiting for a response.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/select-terminal.png" alt-text="Terminal sekmesini seçin":::

1. <span data-ttu-id="dc117-143">Bir ad istemine yanıt olarak **Terminal** penceresine bir dize girin ve ardından <kbd>ENTER</kbd>tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="dc117-143">Enter a string in the **Terminal** window in response to the prompt for a name, and then press <kbd>Enter</kbd>.</span></span>

   <span data-ttu-id="dc117-144">Program yürütme, kesme noktasına ulaştığında ve Yöntem yürütmeden önce duraklar `Console.WriteLine` .</span><span class="sxs-lookup"><span data-stu-id="dc117-144">Program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span> <span data-ttu-id="dc117-145">**Değişkenler** penceresinin **Yereller** bölümü, yürütülmekte olan yöntemde tanımlanan değişkenlerin değerlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="dc117-145">The **Locals** section of the **Variables** window displays the values of variables that are defined in the currently executing method.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-hit.png" alt-text="Yerelleri gösteren kesme noktası isabet":::

## <a name="change-variable-values"></a><span data-ttu-id="dc117-147">Değişken değerlerini Değiştir</span><span class="sxs-lookup"><span data-stu-id="dc117-147">Change variable values</span></span>

<span data-ttu-id="dc117-148">**Hata ayıklama konsolu** penceresi, hata ayıkladığınızda uygulamayla etkileşime girebilmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc117-148">The **Debug Console** window lets you interact with the application you're debugging.</span></span> <span data-ttu-id="dc117-149">Programınızı nasıl etkileyeceğini görmek için değişkenlerin değerini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc117-149">You can change the value of variables to see how it affects your program.</span></span>

1. <span data-ttu-id="dc117-150">**Hata ayıklama konsolu** sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="dc117-150">Select the **Debug Console** tab.</span></span>

1. <span data-ttu-id="dc117-151">`name = "Gracie"` **Hata ayıklama konsolu** penceresinin en altındaki Istemine yazın ve <kbd>ENTER</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="dc117-151">Enter `name = "Gracie"` at the prompt at the bottom of the **Debug Console** window and press the <kbd>Enter</kbd> key.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/change-variable-values.png" alt-text="Değişken değerlerini Değiştir":::

1. <span data-ttu-id="dc117-153">`date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` **Hata ayıklama konsolu** penceresinin alt kısmına girin ve <kbd>ENTER</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="dc117-153">Enter `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` at the bottom of the **Debug Console** window and press the <kbd>Enter</kbd> key.</span></span>

   <span data-ttu-id="dc117-154">**Değişkenler** penceresi, ve değişkenlerinin yeni değerlerini görüntüler `name` `date` .</span><span class="sxs-lookup"><span data-stu-id="dc117-154">The **Variables** window displays the new values of the `name` and `date` variables.</span></span>

1. <span data-ttu-id="dc117-155">Araç çubuğundaki **devam** düğmesini seçerek program yürütmeye devam edin.</span><span class="sxs-lookup"><span data-stu-id="dc117-155">Continue program execution by selecting the **Continue** button in the toolbar.</span></span> <span data-ttu-id="dc117-156">Devam etmenin başka bir yolu da <kbd>F5</kbd>'e basılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="dc117-156">Another way to continue is by pressing <kbd>F5</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/continue-debugging.png" alt-text="Hata ayıklamaya devam et":::

1. <span data-ttu-id="dc117-158">**Terminal** sekmesini yeniden seçin.</span><span class="sxs-lookup"><span data-stu-id="dc117-158">Select the **Terminal** tab again.</span></span>

   <span data-ttu-id="dc117-159">Konsol penceresinde görünen değerler, **hata ayıklama konsolunda**yaptığınız değişikliklere karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="dc117-159">The values displayed in the console window correspond to the changes you made in the **Debug Console**.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/changed-variable-values.png" alt-text="Girilen değerleri gösteren Terminal":::

1. <span data-ttu-id="dc117-161">Uygulamadan çıkmak ve hata ayıklamayı durdurmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="dc117-161">Press any key to exit the application and stop debugging.</span></span>

## <a name="set-a-conditional-breakpoint"></a><span data-ttu-id="dc117-162">Koşullu kesme noktası ayarlama</span><span class="sxs-lookup"><span data-stu-id="dc117-162">Set a conditional breakpoint</span></span>

<span data-ttu-id="dc117-163">Program, kullanıcının girdiği dizeyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="dc117-163">The program displays the string that the user enters.</span></span> <span data-ttu-id="dc117-164">Kullanıcı hiçbir şey girmezse ne olur?</span><span class="sxs-lookup"><span data-stu-id="dc117-164">What happens if the user doesn't enter anything?</span></span> <span data-ttu-id="dc117-165">Bunu, *koşullu kesme noktası*adında yararlı bir hata ayıklama özelliği ile test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc117-165">You can test this with a useful debugging feature called a *conditional breakpoint*.</span></span>

1. <span data-ttu-id="dc117-166">Kesme noktasını temsil eden kırmızı nokta üzerinde sağ tıklayın (macOS üzerinde<kbd>CTRL</kbd>+ tıklama).</span><span class="sxs-lookup"><span data-stu-id="dc117-166">Right-click (<kbd>Ctrl</kbd>+click on macOS) on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="dc117-167">Bağlam menüsünde, bir koşullu ifade girmenize izin veren bir iletişim kutusu açmak için **kesme noktasını Düzenle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="dc117-167">In the context menu, select **Edit Breakpoint** to open a dialog that lets you enter a conditional expression.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-context-menu.png" alt-text="Kesme noktası bağlam menüsü":::

1. <span data-ttu-id="dc117-169">`Expression`Açılan kutudan seçim yapın, aşağıdaki koşullu ifadeyi girin ve <kbd>ENTER</kbd>tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="dc117-169">Select `Expression` in the drop-down, enter the following conditional expression, and press <kbd>Enter</kbd>.</span></span>

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   :::image type="content" source="media/debugging-with-visual-studio-code/conditional-expression.png" alt-text="Koşullu bir ifade girin":::

   <span data-ttu-id="dc117-171">Kesme noktası her isabet edildiğinde, hata ayıklayıcı `String.IsNullOrEmpty(name)` yöntemini çağırır ve yalnızca Yöntem çağrısı döndürürse bu satırı keser `true` .</span><span class="sxs-lookup"><span data-stu-id="dc117-171">Each time the breakpoint is hit, the debugger calls the `String.IsNullOrEmpty(name)` method, and it breaks on this line only if the method call returns `true`.</span></span>

   <span data-ttu-id="dc117-172">Koşullu bir ifade yerine, bir deyim belirtilen sayıda yürütülmeden önce program yürütmeyi kesen bir *isabet sayısı*veya iş parçacığı tanımlayıcısı, işlem adı veya iş parçacığı adı olarak bu tür özniteliklere dayalı olarak program yürütmeyi kesen bir *filtre koşulu*belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc117-172">Instead of a conditional expression, you can specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times, or a *filter condition*, which interrupts program execution based on such attributes as a thread identifier, process name, or thread name.</span></span>

1. <span data-ttu-id="dc117-173"><kbd>F5</kbd>'e basarak programı hata ayıklama ile başlatın.</span><span class="sxs-lookup"><span data-stu-id="dc117-173">Start the program with debugging by pressing <kbd>F5</kbd>.</span></span>

1. <span data-ttu-id="dc117-174">Adınızı girmeniz istendiğinde, **Terminal** sekmesinde <kbd>ENTER</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="dc117-174">In the **Terminal** tab, press the <kbd>Enter</kbd> key when prompted to enter your name.</span></span>

   <span data-ttu-id="dc117-175">Belirttiğiniz koşul ( `name` `null` veya <xref:System.String.Empty?displayProperty=nameWithType> ) karşılandı olduğundan, program yürütmesi kesme noktasına ulaştığında ve Yöntem yürütülmeden önce durmaktadır `Console.WriteLine` .</span><span class="sxs-lookup"><span data-stu-id="dc117-175">Because the condition you specified (`name` is `null` or <xref:System.String.Empty?displayProperty=nameWithType>) has been satisfied, program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span>

   <span data-ttu-id="dc117-176">**Değişkenler** penceresi `name` , değişkeninin değerinin veya olduğunu gösterir `""` <xref:System.String.Empty?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="dc117-176">The **Variables** window shows that the value of the `name` variable is `""`, or <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

1. <span data-ttu-id="dc117-177">**Hata ayıklama konsolu** istemine aşağıdaki ifadeyi girerek ve <kbd>ENTER</kbd>tuşuna basarak değerin boş bir dize olduğunu onaylayın.</span><span class="sxs-lookup"><span data-stu-id="dc117-177">Confirm the value is an empty string by entering the following statement at the **Debug Console** prompt and pressing <kbd>Enter</kbd>.</span></span> <span data-ttu-id="dc117-178">Sonuç olarak `true` .</span><span class="sxs-lookup"><span data-stu-id="dc117-178">The result is `true`.</span></span>

   ```csharp
   name == String.Empty
   ```

   :::image type="content" source="media/debugging-with-visual-studio-code/expression-in-debug-console.png" alt-text="Deyimden sonra true değeri döndüren hata ayıklama konsolu":::

1. <span data-ttu-id="dc117-180">Program yürütmeye devam etmek için araç çubuğundaki **devam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="dc117-180">Select the **Continue** button on the toolbar to continue program execution.</span></span>

1. <span data-ttu-id="dc117-181">**Terminal** sekmesini seçin ve herhangi bir tuşa basarak programdan çıkın ve hata ayıklamayı durdurun.</span><span class="sxs-lookup"><span data-stu-id="dc117-181">Select the **Terminal** tab, and press any key to exit the program and stop debugging.</span></span>

1. <span data-ttu-id="dc117-182">Kod penceresinin sol kenarındaki noktaya tıklayarak kesme noktasını temizleyin.</span><span class="sxs-lookup"><span data-stu-id="dc117-182">Clear the breakpoint by clicking on the dot in the left margin of the code window.</span></span> <span data-ttu-id="dc117-183">Bir kesme noktasını temizlemek için başka bir yol ise kod satırı seçiliyken <kbd>F9</kbd> tuşuna basmakla belirlenir.</span><span class="sxs-lookup"><span data-stu-id="dc117-183">Another way to clear a breakpoint is by pressing <kbd>F9</kbd> while the line of code is selected.</span></span>

1. <span data-ttu-id="dc117-184">Kesme noktası koşulunun kaybolacağını belirten bir uyarı alırsanız, **kesme noktasını kaldır**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="dc117-184">If you get a warning that the breakpoint condition will be lost, select **Remove Breakpoint**.</span></span>

## <a name="step-through-a-program"></a><span data-ttu-id="dc117-185">Programda adımla</span><span class="sxs-lookup"><span data-stu-id="dc117-185">Step through a program</span></span>

<span data-ttu-id="dc117-186">Visual Studio Code Ayrıca, bir program aracılığıyla satır içine girerek ve yürütmesini izlemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="dc117-186">Visual Studio Code also allows you to step line by line through a program and monitor its execution.</span></span> <span data-ttu-id="dc117-187">Normalde, bir kesme noktası ayarlar ve program kodunuzun küçük bir bölümünde program akışını takip edersiniz.</span><span class="sxs-lookup"><span data-stu-id="dc117-187">Ordinarily, you'd set a breakpoint and follow program flow through a small part of your program code.</span></span> <span data-ttu-id="dc117-188">Bu program küçük olduğundan programın tamamında ilerlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc117-188">Since this program is small, you can step through the entire program.</span></span>

1. <span data-ttu-id="dc117-189">Metodun açılış küme ayracı üzerinde bir kesme noktası ayarlayın `Main` .</span><span class="sxs-lookup"><span data-stu-id="dc117-189">Set a breakpoint on the opening curly brace of the `Main` method.</span></span>

1. <span data-ttu-id="dc117-190">Hata ayıklamaya başlamak için <kbd>F5</kbd>'e basın.</span><span class="sxs-lookup"><span data-stu-id="dc117-190">Press <kbd>F5</kbd> to start debugging.</span></span>

   <span data-ttu-id="dc117-191">Visual Studio Code kesme çizgisi çizgisini vurgular.</span><span class="sxs-lookup"><span data-stu-id="dc117-191">Visual Studio Code highlights the breakpoint line.</span></span>

   <span data-ttu-id="dc117-192">Bu noktada, **değişkenler** penceresi `args` dizinin boş olduğunu ve `name` `date` varsayılan değerlere sahip olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="dc117-192">At this point, the **Variables** window shows that the `args` array is empty, and `name` and `date` have default values.</span></span>

1. <span data-ttu-id="dc117-193">**Adımla** ' yı seçin veya <kbd>F11</kbd>tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="dc117-193">Select **Step Into** or press <kbd>F11</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/step-into.png" alt-text="Adımla düğmesi":::

   <span data-ttu-id="dc117-195">Visual Studio Code sonraki satırı vurgular.</span><span class="sxs-lookup"><span data-stu-id="dc117-195">Visual Studio Code highlights the next line.</span></span>

1. <span data-ttu-id="dc117-196">**Adımla** ' yı seçin veya <kbd>F11</kbd>tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="dc117-196">Select **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="dc117-197">Visual Studio Code, `Console.WriteLine` ad istemi için öğesini yürütür ve sonraki yürütme satırını vurgular.</span><span class="sxs-lookup"><span data-stu-id="dc117-197">Visual Studio Code executes the `Console.WriteLine` for the name prompt and highlights the next line of execution.</span></span> <span data-ttu-id="dc117-198">Sonraki satır, `Console.ReadLine` içindir `name` .</span><span class="sxs-lookup"><span data-stu-id="dc117-198">The next line is the `Console.ReadLine` for the `name`.</span></span> <span data-ttu-id="dc117-199">**Değişkenler** penceresi değiştirilmez ve **Terminal** sekmesi "adınız nedir?" olarak gösterilir.</span><span class="sxs-lookup"><span data-stu-id="dc117-199">The **Variables** window is unchanged, and the **Terminal** tab shows the "What is your name?"</span></span> <span data-ttu-id="dc117-200">isteme.</span><span class="sxs-lookup"><span data-stu-id="dc117-200">prompt.</span></span>

1. <span data-ttu-id="dc117-201">**Adımla** ' yı seçin veya <kbd>F11</kbd>tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="dc117-201">Select **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="dc117-202">Visual Studio, `name` değişken atamasını vurgular.</span><span class="sxs-lookup"><span data-stu-id="dc117-202">Visual Studio highlights the `name` variable assignment.</span></span> <span data-ttu-id="dc117-203">**Değişkenler** penceresi hala olduğunu gösterir `name` `null` .</span><span class="sxs-lookup"><span data-stu-id="dc117-203">The **Variables** window shows that `name` is still `null`.</span></span>

1. <span data-ttu-id="dc117-204">Terminal sekmesine bir dize girerek ve <kbd>ENTER</kbd>' a basarak istemi yanıtlayın.</span><span class="sxs-lookup"><span data-stu-id="dc117-204">Respond to the prompt by entering a string in the Terminal tab and pressing <kbd>Enter</kbd>.</span></span>

   <span data-ttu-id="dc117-205">**Terminal** sekmesi, girerken girdiğiniz dizeyi görüntülemeyebilir, ancak <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> Yöntem girişinizi yakalar.</span><span class="sxs-lookup"><span data-stu-id="dc117-205">The **Terminal** tab might not display the string you enter while you're entering it, but the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method will capture your input.</span></span>

1. <span data-ttu-id="dc117-206">**Adımla** ' yı seçin veya <kbd>F11</kbd>tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="dc117-206">Select **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="dc117-207">Visual Studio Code, `date` değişken atamasını vurgular.</span><span class="sxs-lookup"><span data-stu-id="dc117-207">Visual Studio Code highlights the `date` variable assignment.</span></span> <span data-ttu-id="dc117-208">**Değişkenler** penceresi, yöntemine yapılan çağrı tarafından döndürülen değeri gösterir <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="dc117-208">The **Variables** window shows the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="dc117-209">**Terminal** sekmesi, istemde girdiğiniz dizeyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="dc117-209">The **Terminal** tab displays the string you entered at the prompt.</span></span>

1. <span data-ttu-id="dc117-210">**Adımla** ' yı seçin veya <kbd>F11</kbd>tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="dc117-210">Select **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="dc117-211">**Değişkenler** penceresi, `date` özelliğinden atamadan sonraki değişkenin değerini gösterir <xref:System.DateTime.Now?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="dc117-211">The **Variables** window shows the value of the `date` variable after the assignment from the <xref:System.DateTime.Now?displayProperty=nameWithType> property.</span></span>

1. <span data-ttu-id="dc117-212">**Adımla** ' yı seçin veya <kbd>F11</kbd>tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="dc117-212">Select **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="dc117-213">Visual Studio Code yöntemini çağırır <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="dc117-213">Visual Studio Code calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="dc117-214">Konsol penceresi biçimlendirilen dizeyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="dc117-214">The console window displays the formatted string.</span></span>

1. <span data-ttu-id="dc117-215">**Atla** ' yı seçin veya <kbd>SHIFT</kbd> + <kbd>F11</kbd>tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="dc117-215">Select **Step Out** or press <kbd>Shift</kbd>+<kbd>F11</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/step-out.png" alt-text="Adımla düğmesi":::

1. <span data-ttu-id="dc117-217">**Terminal** sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="dc117-217">Select the **Terminal** tab.</span></span>

   <span data-ttu-id="dc117-218">Terminal "çıkmak için herhangi bir tuşa basın..." şeklinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="dc117-218">The terminal displays "Press any key to exit..."</span></span>

1. <span data-ttu-id="dc117-219">Programdan çıkmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="dc117-219">Press any key to exit the program.</span></span>

## <a name="select-release-build-configuration"></a><span data-ttu-id="dc117-220">Yayın derleme yapılandırmasını seçin</span><span class="sxs-lookup"><span data-stu-id="dc117-220">Select Release build configuration</span></span>

<span data-ttu-id="dc117-221">Uygulamanızın hata ayıklama sürümünü sınadıktan sonra yayın sürümünü derleyip test etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="dc117-221">Once you've tested the Debug version of your application, you should also compile and test the Release version.</span></span> <span data-ttu-id="dc117-222">Yayın sürümü, bir uygulamanın davranışını etkileyebilecek derleyici iyileştirmeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="dc117-222">The Release version incorporates compiler optimizations that can affect the behavior of an application.</span></span> <span data-ttu-id="dc117-223">Örneğin, performansı artırmak için tasarlanan derleyici iyileştirmeleri, çok iş parçacıklı uygulamalarda yarış koşulları oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="dc117-223">For example, compiler optimizations that are designed to improve performance can create race conditions in multithreaded applications.</span></span>

<span data-ttu-id="dc117-224">Konsol uygulamanızın yayın sürümünü derlemek ve test etmek için **terminali** açın ve şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="dc117-224">To build and test the Release version of your console application, open the **Terminal** and run the following command:</span></span>

```dotnetcli
dotnet run --configuration Release
```

## <a name="additional-resources"></a><span data-ttu-id="dc117-225">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="dc117-225">Additional resources</span></span>

* [<span data-ttu-id="dc117-226">Visual Studio Code 'de hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="dc117-226">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/docs/editor/debugging)

## <a name="next-steps"></a><span data-ttu-id="dc117-227">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="dc117-227">Next steps</span></span>

<span data-ttu-id="dc117-228">Bu öğreticide hata ayıklama araçları Visual Studio Code kullandınız.</span><span class="sxs-lookup"><span data-stu-id="dc117-228">In this tutorial, you used Visual Studio Code debugging tools.</span></span> <span data-ttu-id="dc117-229">Sonraki öğreticide, uygulamanın dağıtılabilir bir sürümünü yayımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="dc117-229">In the next tutorial, you publish a deployable version of the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="dc117-230">Visual Studio Code bir .NET Core konsol uygulaması yayımlama</span><span class="sxs-lookup"><span data-stu-id="dc117-230">Publish a .NET Core console application with Visual Studio Code</span></span>](publishing-with-visual-studio-code.md)
