---
title: Mac için Visual Studio kullanarak bir .NET Core konsol uygulamasında hata ayıklama
description: Visual Studio Mac kullanarak bir .NET Core konsol uygulamasında hata ayıklamayı öğrenin.
ms.date: 06/08/2020
ms.openlocfilehash: 4941605923a9897d481aca4ec31408ab62e873f3
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2020
ms.locfileid: "84713821"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio-for-mac"></a><span data-ttu-id="80459-103">Öğretici: Mac için Visual Studio kullanarak bir .NET Core konsol uygulamasında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="80459-103">Tutorial: Debug a .NET Core console application using Visual Studio for Mac</span></span>

<span data-ttu-id="80459-104">Bu öğreticide Mac için Visual Studio bulunan hata ayıklama araçları tanıtılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="80459-104">This tutorial introduces the debugging tools available in Visual Studio for Mac.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="80459-105">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="80459-105">Prerequisites</span></span>

- <span data-ttu-id="80459-106">Bu öğretici, [Mac için Visual Studio bir .NET Core konsol uygulaması oluşturma](using-on-mac-vs.md)bölümünde oluşturduğunuz konsol uygulamasıyla birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="80459-106">This tutorial works with the console app that you create in [Create a .NET Core console application in Visual Studio for Mac](using-on-mac-vs.md).</span></span>

## <a name="use-debug-build-configuration"></a><span data-ttu-id="80459-107">Hata ayıklama derleme yapılandırmasını kullan</span><span class="sxs-lookup"><span data-stu-id="80459-107">Use Debug build configuration</span></span>

<span data-ttu-id="80459-108">*Hata ayıklama* ve *yayın* , Visual Studio 'nun yerleşik derleme yapılandırmalarıdır.</span><span class="sxs-lookup"><span data-stu-id="80459-108">*Debug* and *Release* are Visual Studio's built-in build configurations.</span></span> <span data-ttu-id="80459-109">Hata ayıklama oluşturma yapılandırması hata ayıklama için ve son sürüm dağıtımı için sürüm yapılandırması ' nı kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="80459-109">You use the Debug build configuration for debugging and the Release configuration for the final release distribution.</span></span>

<span data-ttu-id="80459-110">Hata ayıklama yapılandırmasında, bir program tam sembolik hata ayıklama bilgileriyle derlenir ve iyileştirmesi yoktur.</span><span class="sxs-lookup"><span data-stu-id="80459-110">In the Debug configuration, a program compiles with full symbolic debug information and no optimization.</span></span> <span data-ttu-id="80459-111">Kaynak kodu ve oluşturulan yönergeler arasındaki ilişki daha karmaşık olduğundan iyileştirme, hata ayıklamayı karmaşıklaştırır.</span><span class="sxs-lookup"><span data-stu-id="80459-111">Optimization complicates debugging, because the relationship between source code and generated instructions is more complex.</span></span> <span data-ttu-id="80459-112">Bir programın yayın yapılandırmasında sembolik hata ayıklama bilgisi yoktur ve tamamen iyileştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="80459-112">The release configuration of a program has no symbolic debug information and is fully optimized.</span></span>

<span data-ttu-id="80459-113">Varsayılan olarak, Visual Studio hata ayıklama derleme yapılandırmasını kullanır, bu nedenle hata ayıklamadan önce değiştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="80459-113">By default, Visual Studio uses the Debug build configuration, so you don't need to change it before debugging.</span></span>

1. <span data-ttu-id="80459-114">Mac için Visual Studio başlatın.</span><span class="sxs-lookup"><span data-stu-id="80459-114">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="80459-115">[Mac için Visual Studio .NET Core konsol uygulaması oluşturma](using-on-mac-vs.md)bölümünde oluşturduğunuz projeyi açın.</span><span class="sxs-lookup"><span data-stu-id="80459-115">Open the project that you created in [Create a .NET Core console application in Visual Studio for Mac](using-on-mac-vs.md).</span></span>

   <span data-ttu-id="80459-116">Geçerli derleme yapılandırması araç çubuğunda gösterilir.</span><span class="sxs-lookup"><span data-stu-id="80459-116">The current build configuration is shown on the toolbar.</span></span> <span data-ttu-id="80459-117">Aşağıdaki araç çubuğu görüntüsünde, Visual Studio 'nun uygulamanın hata ayıklama sürümünü derlemek üzere yapılandırıldığı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="80459-117">The following toolbar image shows that Visual Studio is configured to compile the Debug version of the app:</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/visual-studio-toolbar-debug.png" alt-text="Hata ayıklama vurgulanmış Visual Studio araç çubuğu":::

## <a name="set-a-breakpoint"></a><span data-ttu-id="80459-119">Kesme noktası ayarlama</span><span class="sxs-lookup"><span data-stu-id="80459-119">Set a breakpoint</span></span>

<span data-ttu-id="80459-120">Kesme *noktası,* kesme noktası olan satır yürütülmeden önce uygulamanın yürütülmesini geçici olarak keser.</span><span class="sxs-lookup"><span data-stu-id="80459-120">A *breakpoint* temporarily interrupts the execution of the application before the line with the breakpoint is executed.</span></span>

1. <span data-ttu-id="80459-121">Ad, tarih ve saati gösteren satırda bir kesme noktası ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="80459-121">Set a breakpoint on the line that displays the name, date, and time.</span></span> <span data-ttu-id="80459-122">Bunu yapmak için imleci kod satırına yerleştirin ve <kbd>⌘</kbd> <kbd>\\</kbd> (<kbd>komut</kbd>) tuşuna basın + <kbd>\\</kbd> .</span><span class="sxs-lookup"><span data-stu-id="80459-122">To do that, place the cursor in the line of code and press <kbd>⌘</kbd><kbd>\\</kbd> (<kbd>command</kbd>+<kbd>\\</kbd>).</span></span> <span data-ttu-id="80459-123">Bir kesme noktası ayarlamak için başka bir yol **Run**  >  da menüden**geçiş kesme noktası** Çalıştır ' i seçmektir.</span><span class="sxs-lookup"><span data-stu-id="80459-123">Another way to set a breakpoint is by selecting **Run** > **Toggle Breakpoint** from the menu.</span></span>

   <span data-ttu-id="80459-124">Visual Studio, kesme noktasının ayarlandığı çizgiyi gösterir ve sol kenar boşluğunda kırmızı bir nokta görüntüler.</span><span class="sxs-lookup"><span data-stu-id="80459-124">Visual Studio indicates the line on which the breakpoint is set by highlighting it and displaying a red dot in the left margin.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/set-breakpoint-in-editor.png" alt-text="Kesme noktası ayarlanmış Visual Studio program penceresi":::

1. <span data-ttu-id="80459-126"><kbd>⌘</kbd><kbd>↵</kbd> <kbd>command</kbd> + Programı hata ayıklama modunda başlatmak için ⌘ ↵ (komut<kbd>ENTER</kbd>) tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="80459-126">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to start the program in debugging mode.</span></span> <span data-ttu-id="80459-127">Hata ayıklamayı başlatmak için başka bir yol **Run**  >  da, menüden**hata ayıklamayı Başlat** Çalıştır ' i seçmektir.</span><span class="sxs-lookup"><span data-stu-id="80459-127">Another way to start debugging is by choosing **Run** > **Start Debugging** from the menu.</span></span>

1. <span data-ttu-id="80459-128">Program bir ad isteminde bulunduğunda Terminal penceresine bir dize girin ve ardından <kbd>ENTER</kbd>tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="80459-128">Enter a string in the terminal window when the program prompts for a name, and then press <kbd>enter</kbd>.</span></span>

1. <span data-ttu-id="80459-129">Program yürütme, yöntemi yürütmeden önce kesme noktasına ulaştığında duraklar `Console.WriteLine` .</span><span class="sxs-lookup"><span data-stu-id="80459-129">Program execution stops when it reaches the breakpoint, before the `Console.WriteLine` method executes.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/breakpoint-hit.png" alt-text="Visual Studio 'da bir kesme noktasının ekran görüntüsü":::

## <a name="use-the-immediate-window"></a><span data-ttu-id="80459-131">Hemen penceresini kullanma</span><span class="sxs-lookup"><span data-stu-id="80459-131">Use the Immediate window</span></span>

<span data-ttu-id="80459-132">**Komut** penceresi, hata ayıklamanıza çalıştığınız uygulamayla etkileşime girebilmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="80459-132">The **Immediate** window lets you interact with the application you're debugging.</span></span> <span data-ttu-id="80459-133">Programınızı nasıl etkilediğini görmek için değişkenlerin değerini etkileşimli olarak değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80459-133">You can interactively change the value of variables to see how it affects your program.</span></span>

1. <span data-ttu-id="80459-134">**Hemen** penceresi görünür değilse, **View**  >  **hata ayıklama Pad**'i  >  **hemen**görüntüle ' yi seçerek bunu görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="80459-134">If the **Immediate** window is not visible, display it by choosing **View** > **Debug Pads** > **Immediate**.</span></span>

1. <span data-ttu-id="80459-135">`name = "Gracie"` **Hemen** penceresine girip <kbd>ENTER</kbd>tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="80459-135">Enter `name = "Gracie"` in the **Immediate** window and press <kbd>enter</kbd>.</span></span>

1. <span data-ttu-id="80459-136">`date = date.AddDays(1)` **Hemen** penceresine girip <kbd>ENTER</kbd>tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="80459-136">Enter `date = date.AddDays(1)` in the **Immediate** window and press <kbd>enter</kbd>.</span></span>

   <span data-ttu-id="80459-137">**Komut** penceresi, dize değişkeninin yeni değerini ve değerin özelliklerini görüntüler <xref:System.DateTime> .</span><span class="sxs-lookup"><span data-stu-id="80459-137">The **Immediate** window displays the new value of the string variable and the properties of the <xref:System.DateTime> value.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/immediate-window.png" alt-text="Visual Studio 'da hemen penceresi":::

   <span data-ttu-id="80459-139">**Yereller** penceresi, yürütülmekte olan yöntemde tanımlanan değişkenlerin değerlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="80459-139">The **Locals** window displays the values of variables that are defined in the currently executing method.</span></span> <span data-ttu-id="80459-140">Yeni değiştirdiğiniz değişkenlerin değerleri **Locals** penceresinde güncellenir.</span><span class="sxs-lookup"><span data-stu-id="80459-140">The values of the variables that you just changed are updated in the **Locals** window.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/locals-window.png" alt-text="Visual Studio 'da yerel öğeler penceresi":::

1. <span data-ttu-id="80459-142">Hata <kbd>⌘</kbd>ayıklamaya devam etmek için ⌘<kbd>↵</kbd> (<kbd>komut</kbd> + <kbd>ENTER</kbd>) tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="80459-142">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to continue debugging.</span></span>

   <span data-ttu-id="80459-143">Terminalde görünen değerler, **komut** penceresinde yaptığınız değişikliklere karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="80459-143">The values displayed in the terminal correspond to the changes you made in the **Immediate** window.</span></span>

   <span data-ttu-id="80459-144">Terminali görmüyorsanız, alt gezinti çubuğunda **Terminal-HelloWorld** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="80459-144">If you don't see the Terminal, select **Terminal - HelloWorld** in the bottom navigation bar.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/terminal-hello-world.png" alt-text="Sol gezinti çubuğunda Terminal-Merhaba Dünya":::

1. <span data-ttu-id="80459-146">Programdan çıkmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="80459-146">Press any key to exit the program.</span></span>

1. <span data-ttu-id="80459-147">Terminal penceresini kapatın.</span><span class="sxs-lookup"><span data-stu-id="80459-147">Close the terminal window.</span></span>

## <a name="set-a-conditional-breakpoint"></a><span data-ttu-id="80459-148">Koşullu kesme noktası ayarlama</span><span class="sxs-lookup"><span data-stu-id="80459-148">Set a conditional breakpoint</span></span>

<span data-ttu-id="80459-149">Program, kullanıcının girdiği dizeyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="80459-149">The program displays a string that the user enters.</span></span> <span data-ttu-id="80459-150">Kullanıcı hiçbir şey girmezse ne olur?</span><span class="sxs-lookup"><span data-stu-id="80459-150">What happens if the user doesn't enter anything?</span></span> <span data-ttu-id="80459-151">Bunu, *koşullu kesme noktası*adında yararlı bir hata ayıklama özelliği ile test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80459-151">You can test this with a useful debugging feature called a *conditional breakpoint*.</span></span>

1. <span data-ttu-id="80459-152"><kbd>CTRL tuşuna</kbd>basıp kesme noktasını temsil eden kırmızı noktaya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="80459-152"><kbd>ctrl</kbd>-click on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="80459-153">Bağlam menüsünde, **kesme noktasını Düzenle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="80459-153">In the context menu, select **Edit Breakpoint**.</span></span>

1. <span data-ttu-id="80459-154">**Kesme noktasını Düzenle** iletişim kutusunda aşağıdaki alana aşağıdaki kodu girin **ve aşağıdaki koşul doğrudur**ve **Uygula**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="80459-154">In the **Edit Breakpoint** dialog, enter the following code in the field that follows **And the following condition is true**, and select **Apply**.</span></span>

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   :::image type="content" source="media/debugging-with-visual-studio-mac/breakpoint-settings.png" alt-text="Kesme noktası ayarları panelini gösteren düzenleyici":::

   <span data-ttu-id="80459-156">Kesme noktası her isabet edildiğinde, hata ayıklayıcı `String.IsNullOrEmpty(name)` yöntemini çağırır ve yalnızca Yöntem çağrısı döndürürse bu satırı keser `true` .</span><span class="sxs-lookup"><span data-stu-id="80459-156">Each time the breakpoint is hit, the debugger calls the `String.IsNullOrEmpty(name)` method, and it breaks on this line only if the method call returns `true`.</span></span>

   <span data-ttu-id="80459-157">Koşullu bir ifade yerine, bir deyim belirtilen sayıda yürütülmeden önce program yürütmeyi kesen bir *isabet sayısı*belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80459-157">Instead of a conditional expression, you can specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times.</span></span>

1. <span data-ttu-id="80459-158">Hata ayıklamayı başlatmak için <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>komut</kbd> + <kbd>ENTER</kbd>) tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="80459-158">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to start debugging.</span></span>

1. <span data-ttu-id="80459-159">Adınızı girmeniz istendiğinde, Terminal penceresinde <kbd>ENTER</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="80459-159">In the terminal window, press <kbd>enter</kbd> when prompted to enter your name.</span></span>

   <span data-ttu-id="80459-160">Belirttiğiniz koşul (ya `name` da `null` <xref:System.String.Empty?displayProperty=nameWithType> ) karşılandığından, program yürütmesi kesme noktasına ulaştığında durmaktadır.</span><span class="sxs-lookup"><span data-stu-id="80459-160">Because the condition you specified (`name` is either `null` or <xref:System.String.Empty?displayProperty=nameWithType>) has been satisfied, program execution stops when it reaches the breakpoint.</span></span>

1. <span data-ttu-id="80459-161">Şu anda yürütülmekte olan metodun yerellerinin değerlerini gösteren **Yereller** penceresini seçin.</span><span class="sxs-lookup"><span data-stu-id="80459-161">Select the **Locals** window, which shows the values of variables that are local to the currently executing method.</span></span> <span data-ttu-id="80459-162">Bu durumda, `Main` Şu anda yürütülmekte olan yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="80459-162">In this case, `Main` is the currently executing method.</span></span> <span data-ttu-id="80459-163">Değişkenin değerinin olduğunu, yani, olduğunu gözlemleyin `name` `""` <xref:System.String.Empty?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="80459-163">Observe that the value of the `name` variable is `""`, that is, <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

1. <span data-ttu-id="80459-164">Ayrıca, `name` **hemen** penceresinde değişken adını girip <kbd>ENTER</kbd>tuşuna basarak değerin boş bir dize olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80459-164">You can also see that the value is an empty string by entering the `name` variable name in the **Immediate** window and pressing <kbd>enter</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/immediate-window-output.png" alt-text="Adın bir boş dize olduğunu gösteren komut penceresi":::

1. <span data-ttu-id="80459-166">Hata <kbd>⌘</kbd>ayıklamaya devam etmek için ⌘<kbd>↵</kbd> (<kbd>komut</kbd> + <kbd>ENTER</kbd>) tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="80459-166">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to continue debugging.</span></span>

1. <span data-ttu-id="80459-167">Terminal penceresinde programından çıkmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="80459-167">In the terminal window, press any key to exit the program.</span></span>

1. <span data-ttu-id="80459-168">Terminal penceresini kapatın.</span><span class="sxs-lookup"><span data-stu-id="80459-168">Close the terminal window.</span></span>

1. <span data-ttu-id="80459-169">Kod penceresinin sol kenarındaki kırmızı noktaya tıklayarak kesme noktasını temizleyin.</span><span class="sxs-lookup"><span data-stu-id="80459-169">Clear the breakpoint by clicking on the red dot in the left margin of the code window.</span></span> <span data-ttu-id="80459-170">Bir kesme noktasını temizlemek için başka bir yol da kod satırı seçili durumdayken > Çalıştır ' i seçerek **kesme noktasını değiştirir** .</span><span class="sxs-lookup"><span data-stu-id="80459-170">Another way to clear a breakpoint is by choosing **Run > Toggle Breakpoint** while the line of code is selected.</span></span>

## <a name="step-through-a-program"></a><span data-ttu-id="80459-171">Programda adımla</span><span class="sxs-lookup"><span data-stu-id="80459-171">Step through a program</span></span>

<span data-ttu-id="80459-172">Visual Studio Ayrıca, bir program aracılığıyla satıra göre çizgi ve yürütmeyi izlemeye de olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="80459-172">Visual Studio also allows you to step line by line through a program and monitor its execution.</span></span> <span data-ttu-id="80459-173">Normalde, bir kesme noktası ayarlar ve program kodunuzun küçük bir bölümünde program akışını takip edersiniz.</span><span class="sxs-lookup"><span data-stu-id="80459-173">Ordinarily, you'd set a breakpoint and follow program flow through a small part of your program code.</span></span> <span data-ttu-id="80459-174">Bu program küçük olduğundan programın tamamında ilerlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80459-174">Since this program is small, you can step through the entire program.</span></span>

1. <span data-ttu-id="80459-175">Yöntemin başlangıcını işaretleyen küme ayracı üzerinde bir kesme noktası ayarlayın `Main` ( <kbd>Command</kbd>tuşuna basın + <kbd>\\</kbd> ).</span><span class="sxs-lookup"><span data-stu-id="80459-175">Set a breakpoint on the curly brace that marks the start of the `Main` method (press <kbd>command</kbd>+<kbd>\\</kbd>).</span></span>

1. <span data-ttu-id="80459-176">Hata ayıklamayı başlatmak için <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>komut</kbd> + <kbd>ENTER</kbd>) tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="80459-176">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to start debugging.</span></span>

   <span data-ttu-id="80459-177">Visual Studio kesme noktası ile satır üzerinde durmaktadır.</span><span class="sxs-lookup"><span data-stu-id="80459-177">Visual Studio stops on the line with the breakpoint.</span></span>

1. <span data-ttu-id="80459-178">Bir satıra ilerlemek için <kbd>⇧</kbd><kbd>⌘</kbd><kbd>ı</kbd> (<kbd>SHIFT</kbd> + <kbd>Command</kbd> + <kbd>ı</kbd>) veya Select Step **Run**with '  >  **a** basın.</span><span class="sxs-lookup"><span data-stu-id="80459-178">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>) or select **Run** > **Step Into** to advance one line.</span></span>

   <span data-ttu-id="80459-179">Visual Studio, sonraki yürütme satırının yanında bir ok görüntüler.</span><span class="sxs-lookup"><span data-stu-id="80459-179">Visual Studio highlights and displays an arrow beside the next line of execution.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/step-into-method.png" alt-text="Visual Studio Step into yöntemi":::

   <span data-ttu-id="80459-181">Bu noktada, **Yereller** penceresi `args` dizinin boş olduğunu ve `name` `date` varsayılan değerlere sahip olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="80459-181">At this point, the **Locals** window shows that the `args` array is empty, and `name` and `date` have default values.</span></span> <span data-ttu-id="80459-182">Ayrıca, Visual Studio boş bir Terminal açtı.</span><span class="sxs-lookup"><span data-stu-id="80459-182">In addition, Visual Studio has opened a blank terminal.</span></span>

1. <span data-ttu-id="80459-183"><kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>Shift</kbd> + <kbd>Command</kbd> + <kbd>ı</kbd>) tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="80459-183">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>).</span></span>

   <span data-ttu-id="80459-184">Visual Studio, değişken atamasını içeren ifadeyi vurgular `name` .</span><span class="sxs-lookup"><span data-stu-id="80459-184">Visual Studio highlights the statement that includes the `name` variable assignment.</span></span> <span data-ttu-id="80459-185">**Yereller** penceresi olduğunu gösterir `name` `null` ve Terminal "adınız nedir?" dizesini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="80459-185">The **Locals** window shows that `name` is `null`, and the terminal displays the string "What is your name?".</span></span>

1. <span data-ttu-id="80459-186">Konsol penceresine bir dize girerek ve <kbd>ENTER</kbd>' a basarak istemi yanıtlayın.</span><span class="sxs-lookup"><span data-stu-id="80459-186">Respond to the prompt by entering a string in the console window and pressing <kbd>enter</kbd>.</span></span>

1. <span data-ttu-id="80459-187"><kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>Shift</kbd> + <kbd>Command</kbd> + <kbd>ı</kbd>) tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="80459-187">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>).</span></span>

   <span data-ttu-id="80459-188">Visual Studio, değişken atamasını içeren ifadeyi vurgular `date` .</span><span class="sxs-lookup"><span data-stu-id="80459-188">Visual Studio highlights the statement that includes the `date` variable assignment.</span></span> <span data-ttu-id="80459-189">**Yereller** penceresi, yöntemi çağrısının döndürdüğü değeri gösterir <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="80459-189">The **Locals** window shows the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="80459-190">Terminal, istemde girdiğiniz dizeyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="80459-190">The terminal displays the string you entered at the prompt.</span></span>

1. <span data-ttu-id="80459-191"><kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>Shift</kbd> + <kbd>Command</kbd> + <kbd>ı</kbd>) tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="80459-191">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>).</span></span>

   <span data-ttu-id="80459-192">**Yereller** penceresi, `date` özelliğinden atamasından sonra değişkenin değerini gösterir <xref:System.DateTime.Now?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="80459-192">The **Locals** window shows the value of the `date` variable after the assignment from the <xref:System.DateTime.Now?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="80459-193">Terminal değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="80459-193">The terminal is unchanged.</span></span>

1. <span data-ttu-id="80459-194"><kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>Shift</kbd> + <kbd>Command</kbd> + <kbd>ı</kbd>) tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="80459-194">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>).</span></span>

   <span data-ttu-id="80459-195">Visual Studio yöntemini çağırır <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="80459-195">Visual Studio calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="80459-196">Terminal, biçimlendirilen dizeyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="80459-196">The terminal displays the formatted string.</span></span>

1. <span data-ttu-id="80459-197"><kbd>⇧</kbd><kbd>⌘</kbd><kbd>U</kbd> (<kbd>SHIFT</kbd> + <kbd>komutu</kbd> + <kbd>U</kbd>) tuşuna basın veya **çalışma adımını Çalıştır**' ı seçin  >  **Step Out**.</span><span class="sxs-lookup"><span data-stu-id="80459-197">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>U</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>U</kbd>) or select **Run** > **Step Out**.</span></span>

   <span data-ttu-id="80459-198">Terminal bir ileti görüntüler ve bir tuşa basmanız için bekler.</span><span class="sxs-lookup"><span data-stu-id="80459-198">The terminal displays a message and waits for you to press a key.</span></span>

1. <span data-ttu-id="80459-199">Programdan çıkmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="80459-199">Press any key to exit the program.</span></span>

## <a name="use-release-build-configuration"></a><span data-ttu-id="80459-200">Yayın derleme yapılandırmasını kullan</span><span class="sxs-lookup"><span data-stu-id="80459-200">Use Release build configuration</span></span>

<span data-ttu-id="80459-201">Uygulamanızın hata ayıklama sürümünü sınadıktan sonra yayın sürümünü derleyip test etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="80459-201">Once you've tested the Debug version of your application, you should also compile and test the Release version.</span></span> <span data-ttu-id="80459-202">Yayın sürümü, bir uygulamanın davranışını olumsuz yönde etkileyebilecek derleyici iyileştirmeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="80459-202">The Release version incorporates compiler optimizations that can negatively affect the behavior of an application.</span></span> <span data-ttu-id="80459-203">Örneğin, performansı artırmak için tasarlanan derleyici iyileştirmeleri, çok iş parçacıklı uygulamalarda yarış koşulları oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="80459-203">For example, compiler optimizations that are designed to improve performance can create race conditions in multithreaded applications.</span></span>

<span data-ttu-id="80459-204">Konsol uygulamasının yayın sürümünü derlemek ve test etmek için aşağıdaki adımları uygulayın:</span><span class="sxs-lookup"><span data-stu-id="80459-204">To build and test the Release version of the console application, do the following steps:</span></span>

1. <span data-ttu-id="80459-205">Araç çubuğundaki derleme yapılandırmasını **Hata Ayıkla** 'dan **Release**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="80459-205">Change the build configuration on the toolbar from **Debug** to **Release**.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/visual-studio-toolbar-release.png" alt-text="hata ayıklama vurgulanmış olarak varsayılan Visual Studio araç çubuğu":::

1. <span data-ttu-id="80459-207"><kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> <kbd>option</kbd> + <kbd>command</kbd> + Hata ayıklamadan çalıştırmak için ⌥ ⌘ ↵ (seçenek komut<kbd>ENTER</kbd>) tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="80459-207">Press <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd>+<kbd>command</kbd>+<kbd>enter</kbd>) to run without debugging.</span></span>

## <a name="next-steps"></a><span data-ttu-id="80459-208">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="80459-208">Next steps</span></span>

<span data-ttu-id="80459-209">Bu öğreticide, Visual Studio hata ayıklama araçları 'nı kullandınız.</span><span class="sxs-lookup"><span data-stu-id="80459-209">In this tutorial, you used Visual Studio debugging tools.</span></span> <span data-ttu-id="80459-210">Sonraki öğreticide, uygulamanın dağıtılabilir bir sürümünü yayımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="80459-210">In the next tutorial, you publish a deployable version of the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="80459-211">Mac için Visual Studio bir .NET Core konsol uygulaması yayımlama</span><span class="sxs-lookup"><span data-stu-id="80459-211">Publish a .NET Core console application with Visual Studio for Mac</span></span>](publishing-with-visual-studio-mac.md)
