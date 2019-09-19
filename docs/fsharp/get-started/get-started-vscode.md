---
title: Visual Studio Code ile F# çalışmaya başlama
description: Visual Studio Code ve ıonıde eklenti Suite ile nasıl kullanacağınızı F# öğrenin.
ms.date: 12/23/2018
ms.openlocfilehash: 2fa0518488d37b2130aaba96028ac92dac77eb97
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082995"
---
# <a name="get-started-with-f-in-visual-studio-code"></a><span data-ttu-id="12055-103">Visual Studio Code ile F# çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="12055-103">Get Started with F# in Visual Studio Code</span></span>

<span data-ttu-id="12055-104">IntelliSense ve Basic F# Code yeniden düzenlemeler ile harika bir platformlar arası, hafif tümleşik geliştirme ORTAMı (IDE) deneyimi almak Için [ıonıde eklentisine](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) [Visual Studio Code](https://code.visualstudio.com) yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12055-104">You can write F# in [Visual Studio Code](https://code.visualstudio.com) with the [Ionide plugin](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) to get a great cross-platform, lightweight Integrated Development Environment (IDE) experience with IntelliSense and basic code refactorings.</span></span> <span data-ttu-id="12055-105">Eklenti hakkında daha fazla bilgi edinmek için [Ionide.io](http://ionide.io) ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="12055-105">Visit [Ionide.io](http://ionide.io) to learn more about the plugin.</span></span>

<span data-ttu-id="12055-106">Başlamak için [ F# ve ıonıde eklentisinin doğru yüklendiğinden](install-fsharp.md#install-f-with-visual-studio-code)emin olun.</span><span class="sxs-lookup"><span data-stu-id="12055-106">To begin, ensure that you have [F# and the Ionide plugin correctly installed](install-fsharp.md#install-f-with-visual-studio-code).</span></span>

> [!NOTE]
> <span data-ttu-id="12055-107">Ionıde, platformlar arası F# uyumluluk sorunlarına sahip olabilen DotNet core olmayan .NET Framework projeler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="12055-107">Ionide will generate .NET Framework F# projects, not dotnet core, which can have cross-platform compatibility issues.</span></span> <span data-ttu-id="12055-108">**Linux** veya **OSX**üzerinde çalıştırıyorsanız, kullanmaya başlamak için daha basit bir yol, [komut satırı araçlarını](get-started-command-line.md)kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="12055-108">If you are running on **Linux** or **OSX**, a simpler way to get started is to use the [command-line tools](get-started-command-line.md).</span></span>

## <a name="creating-your-first-project-with-ionide"></a><span data-ttu-id="12055-109">Ionıde ile ilk projenizi oluşturma</span><span class="sxs-lookup"><span data-stu-id="12055-109">Creating your first project with Ionide</span></span>

<span data-ttu-id="12055-110">Yeni F# bir proje oluşturmak için Visual Studio Code yeni bir klasörde açın (istediğiniz gibi adlandırabilirsiniz).</span><span class="sxs-lookup"><span data-stu-id="12055-110">To create a new F# project, open Visual Studio Code in a new folder (you can name it whatever you like).</span></span>

<span data-ttu-id="12055-111">Sonra, komut paletini açın ( **> komut paletini görüntüleyin**) ve aşağıdakileri yazın:</span><span class="sxs-lookup"><span data-stu-id="12055-111">Next, open the command palette (**View > Command Palette**) and type the following:</span></span>

```console
> F# new project
```

<span data-ttu-id="12055-112">Bu, [Forge](https://github.com/fsharp-editing/Forge) projesi tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="12055-112">This is powered by the [FORGE](https://github.com/fsharp-editing/Forge) project.</span></span>

> [!NOTE]
> <span data-ttu-id="12055-113">Şablon seçeneklerini görmüyorsanız, komut paletinde aşağıdaki komutu çalıştırarak şablonları yenilemeyi deneyin: `>F#: Refresh Project Templates`.</span><span class="sxs-lookup"><span data-stu-id="12055-113">If you don't see template options, try refreshing templates by running the following command in the Command Palette: `>F#: Refresh Project Templates`.</span></span>

<span data-ttu-id="12055-114">Seç "F#: Yeni proje " **ENTER**'a vurarak.</span><span class="sxs-lookup"><span data-stu-id="12055-114">Select "F#: New Project" by hitting **Enter**.</span></span> <span data-ttu-id="12055-115">Bu, sizi bir proje şablonu seçerken bir sonraki adıma götürür.</span><span class="sxs-lookup"><span data-stu-id="12055-115">This takes you to the next step, which is for selecting a project template.</span></span>

<span data-ttu-id="12055-116">Şablonu seçin ve ENTER tuşuna basın. `classlib`</span><span class="sxs-lookup"><span data-stu-id="12055-116">Pick the `classlib` template and hit **Enter**.</span></span>

<span data-ttu-id="12055-117">Ardından, projenin oluşturulacağı bir dizin seçin.</span><span class="sxs-lookup"><span data-stu-id="12055-117">Next, pick a directory to create the project in.</span></span> <span data-ttu-id="12055-118">Boş bırakırsanız, geçerli dizini kullanır.</span><span class="sxs-lookup"><span data-stu-id="12055-118">If you leave it blank, it uses the current directory.</span></span>

<span data-ttu-id="12055-119">Son olarak, projenizi son adımda adlandırın.</span><span class="sxs-lookup"><span data-stu-id="12055-119">Finally, name your project in the final step.</span></span> <span data-ttu-id="12055-120">F#proje adları için [Pascal case](http://c2.com/cgi/wiki?PascalCase) kullanır.</span><span class="sxs-lookup"><span data-stu-id="12055-120">F# uses [Pascal case](http://c2.com/cgi/wiki?PascalCase) for project names.</span></span> <span data-ttu-id="12055-121">Bu makale ad `ClassLibraryDemo` olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="12055-121">This article uses `ClassLibraryDemo` as the name.</span></span> <span data-ttu-id="12055-122">Projeniz için istediğiniz adı girdikten sonra **ENTER**tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="12055-122">Once you've entered the name you want for your project, hit **Enter**.</span></span>

<span data-ttu-id="12055-123">Önceki adımı izlediyseniz, sol taraftaki Visual Studio Code çalışma alanını, aşağıdaki ile görünmesi için almalısınız:</span><span class="sxs-lookup"><span data-stu-id="12055-123">If you followed the previous step, you should get the Visual Studio Code Workspace on the left-hand side to appear with the following:</span></span>

1. <span data-ttu-id="12055-124">F# Projenin kendisi, `ClassLibraryDemo` klasörün altında.</span><span class="sxs-lookup"><span data-stu-id="12055-124">The F# project itself, underneath the `ClassLibraryDemo` folder.</span></span>
2. <span data-ttu-id="12055-125">Aracılığıyla [`Paket`](https://fsprojects.github.io/Paket/)paket eklemeye yönelik doğru dizin yapısı.</span><span class="sxs-lookup"><span data-stu-id="12055-125">The correct directory structure for adding packages via [`Paket`](https://fsprojects.github.io/Paket/).</span></span>
3. <span data-ttu-id="12055-126">İle [`FAKE`](https://fsharp.github.io/FAKE/)platformlar arası bir derleme betiği.</span><span class="sxs-lookup"><span data-stu-id="12055-126">A cross-platform build script with [`FAKE`](https://fsharp.github.io/FAKE/).</span></span>
4. <span data-ttu-id="12055-127">Paketleri alıp sizin için bağımlılıkları çözebilen çalıştırılabilirdosya.`paket.exe`</span><span class="sxs-lookup"><span data-stu-id="12055-127">The `paket.exe` executable that can fetch packages and resolve dependencies for you.</span></span>
5. <span data-ttu-id="12055-128">Bu `.gitignore` projeyi git tabanlı kaynak denetimine eklemek isterseniz bir dosya.</span><span class="sxs-lookup"><span data-stu-id="12055-128">A `.gitignore` file if you wish to add this project to Git-based source control.</span></span>

## <a name="writing-some-code"></a><span data-ttu-id="12055-129">Kod yazma</span><span class="sxs-lookup"><span data-stu-id="12055-129">Writing some code</span></span>

<span data-ttu-id="12055-130">*Classlibrarydemo* klasörünü açın.</span><span class="sxs-lookup"><span data-stu-id="12055-130">Open the *ClassLibraryDemo* folder.</span></span>  <span data-ttu-id="12055-131">Aşağıdaki dosyaları görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="12055-131">You should see the following files:</span></span>

1. <span data-ttu-id="12055-132">`ClassLibraryDemo.fs`, bir F# sınıf tanımlı bir uygulama dosyası.</span><span class="sxs-lookup"><span data-stu-id="12055-132">`ClassLibraryDemo.fs`, an F# implementation file with a class defined.</span></span>
2. <span data-ttu-id="12055-133">`ClassLibraryDemo.fsproj`, bu F# projeyi oluşturmak için kullanılan proje dosyası.</span><span class="sxs-lookup"><span data-stu-id="12055-133">`ClassLibraryDemo.fsproj`, an F# project file used to build this project.</span></span>
3. <span data-ttu-id="12055-134">`Script.fsx`, kaynak F# dosyayı yükleyen bir betik dosyası.</span><span class="sxs-lookup"><span data-stu-id="12055-134">`Script.fsx`, an F# script file that loads the source file.</span></span>
4. <span data-ttu-id="12055-135">`paket.references`, Proje bağımlılıklarını belirten bir paket dosyası.</span><span class="sxs-lookup"><span data-stu-id="12055-135">`paket.references`, a Paket file that specifies the project dependencies.</span></span>

<span data-ttu-id="12055-136">Öğesini `Script.fsx`açın ve sonuna aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="12055-136">Open `Script.fsx`, and add the following code at the end of it:</span></span>

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

<span data-ttu-id="12055-137">Bu işlev, bir kelimeyi bir [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin)biçimine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="12055-137">This function converts a word to a form of [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span></span> <span data-ttu-id="12055-138">Bir sonraki adım, bunu etkileşimli (FSI F# ) kullanarak değerlendirmelidir.</span><span class="sxs-lookup"><span data-stu-id="12055-138">The next step is to evaluate it using F# Interactive (FSI).</span></span>

<span data-ttu-id="12055-139">İşlevin tamamını vurgulayın (11 satır uzunluğunda olmalıdır).</span><span class="sxs-lookup"><span data-stu-id="12055-139">Highlight the entire function (it should be 11 lines long).</span></span> <span data-ttu-id="12055-140">Vurgulandıktan sonra, **alt** tuşunu basılı tutun ve **ENTER**tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="12055-140">Once it is highlighted, hold the **Alt** key and hit **Enter**.</span></span> <span data-ttu-id="12055-141">Aşağıda bir pencere açılır ve şuna benzer bir şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="12055-141">You'll notice a window pop up below, and it should show something like this:</span></span>

![Ionıde ile F# etkileşimli çıkış örneği](./media/getting-started-vscode/vscode-fsi.png)

<span data-ttu-id="12055-143">Bu üç şey oldu:</span><span class="sxs-lookup"><span data-stu-id="12055-143">This did three things:</span></span>

1. <span data-ttu-id="12055-144">Bu işlem, FSI işlemini başlattı.</span><span class="sxs-lookup"><span data-stu-id="12055-144">It started the FSI process.</span></span>
2. <span data-ttu-id="12055-145">Bu, FSI işlemi üzerinde vurguladığınız kodu gönderdi.</span><span class="sxs-lookup"><span data-stu-id="12055-145">It sent the code you highlighted over the FSI process.</span></span>
3. <span data-ttu-id="12055-146">FSI işlemi, üzerinden gönderdiğiniz kodu değerlendirdi.</span><span class="sxs-lookup"><span data-stu-id="12055-146">The FSI process evaluated the code you sent over.</span></span>

<span data-ttu-id="12055-147">Üzerinden gönderildikleriniz bir [işleviydi](../language-reference/functions/index.md), artık bu işlevi FSI ile çağırabilirsiniz!</span><span class="sxs-lookup"><span data-stu-id="12055-147">Because what you sent over was a [function](../language-reference/functions/index.md), you can now call that function with FSI!</span></span> <span data-ttu-id="12055-148">Etkileşimli pencerede şunları yazın:</span><span class="sxs-lookup"><span data-stu-id="12055-148">In the interactive window, type the following:</span></span>

```fsharp
toPigLatin "banana";;
```

<span data-ttu-id="12055-149">Aşağıdaki sonucu görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="12055-149">You should see the following result:</span></span>

```fsharp
val it : string = "ananabay"
```

<span data-ttu-id="12055-150">Şimdi ilk harf olarak bir sesli harf deneyelim.</span><span class="sxs-lookup"><span data-stu-id="12055-150">Now, let's try with a vowel as the first letter.</span></span> <span data-ttu-id="12055-151">Aşağıdakileri girin:</span><span class="sxs-lookup"><span data-stu-id="12055-151">Enter the following:</span></span>

```fsharp
toPigLatin "apple";;
```

<span data-ttu-id="12055-152">Aşağıdaki sonucu görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="12055-152">You should see the following result:</span></span>

```fsharp
val it : string = "appleyay"
```

<span data-ttu-id="12055-153">İşlev beklenen şekilde çalışıyor gibi görünüyor.</span><span class="sxs-lookup"><span data-stu-id="12055-153">The function appears to be working as expected.</span></span> <span data-ttu-id="12055-154">Tebrikler, ilk F# işlevinizi Visual Studio Code YAZMıŞ ve FSI ile değerlendirdiniz!</span><span class="sxs-lookup"><span data-stu-id="12055-154">Congratulations, you just wrote your first F# function in Visual Studio Code and evaluated it with FSI!</span></span>

> [!NOTE]
> <span data-ttu-id="12055-155">Fark etmeyebilirsiniz, FSI içindeki satırlar ile `;;`sonlandırılır.</span><span class="sxs-lookup"><span data-stu-id="12055-155">As you may have noticed, the lines in FSI are terminated with `;;`.</span></span> <span data-ttu-id="12055-156">Bunun nedeni, FSI 'in birden çok satır girmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="12055-156">This is because FSI allows you to enter multiple lines.</span></span> <span data-ttu-id="12055-157">Son `;;` olarak, kod tamamlandığında FSI 'in bu kodu bilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="12055-157">The `;;` at the end lets FSI know when the code is finished.</span></span>

## <a name="explaining-the-code"></a><span data-ttu-id="12055-158">Kodu açıklayan</span><span class="sxs-lookup"><span data-stu-id="12055-158">Explaining the code</span></span>

<span data-ttu-id="12055-159">Kodun gerçekten yapmakta olduğu konusunda emin değilseniz, bir adım adım aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="12055-159">If you're not sure about what the code is actually doing, here's a step-by-step.</span></span>

<span data-ttu-id="12055-160">Görebileceğiniz gibi, `toPigLatin` bir sözcüğü giriş olarak alan ve bu sözcüğün Pig-Latin gösterimine dönüştüren bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="12055-160">As you can see, `toPigLatin` is a function that takes a word as its input and converts it to a Pig-Latin representation of that word.</span></span> <span data-ttu-id="12055-161">Bunun kuralları aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="12055-161">The rules for this are as follows:</span></span>

<span data-ttu-id="12055-162">Bir sözcükteki ilk karakter sesli harf ile başlıyorsa, sözcüğün sonuna "oley" ekleyin.</span><span class="sxs-lookup"><span data-stu-id="12055-162">If the first character in a word starts with a vowel, add "yay" to the end of the word.</span></span> <span data-ttu-id="12055-163">Bir sesli harf ile başlamazsa, ilk karakteri sözcüğün sonuna taşıyın ve buna "ay" ekleyin.</span><span class="sxs-lookup"><span data-stu-id="12055-163">If it doesn't start with a vowel, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="12055-164">FSI içinde aşağıdakileri fark etmiş olabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="12055-164">You may have noticed the following in FSI:</span></span>

```fsharp
val toPigLatin : word:string -> string
```

<span data-ttu-id="12055-165">Bu durum, `toPigLatin` bir `string` as girişi (olarak adlandırılır `word`) ve diğeri `string`döndüren bir işlev olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="12055-165">This states that `toPigLatin` is a function that takes in a `string` as input (called `word`), and returns another `string`.</span></span> <span data-ttu-id="12055-166">Bu, kodu anlamak F# F# için temel bir parçası olan [işlevin tür imzası](https://fsharpforfunandprofit.com/posts/function-signatures/)olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="12055-166">This is known as the [type signature of the function](https://fsharpforfunandprofit.com/posts/function-signatures/), a fundamental piece of F# that's key to understanding F# code.</span></span> <span data-ttu-id="12055-167">Ayrıca, Visual Studio Code işlevin üzerine geldiğinizde bunu da fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="12055-167">You'll also notice this if you hover over the function in Visual Studio Code.</span></span>

<span data-ttu-id="12055-168">İşlevin gövdesinde, iki ayrı bölüm fark edeceksiniz:</span><span class="sxs-lookup"><span data-stu-id="12055-168">In the body of the function, you'll notice two distinct parts:</span></span>

1. <span data-ttu-id="12055-169">Verilen bir karakterin ( `isVowel``c`), [desen eşleştirme](../language-reference/pattern-matching.md)aracılığıyla sağlanan desenlerden biriyle eşleşip eşleşmediğini kontrol ederek bir sesli işlevi olarak adlandırılan bir iç işlev.</span><span class="sxs-lookup"><span data-stu-id="12055-169">An inner function, called `isVowel`, that determines if a given character (`c`) is a vowel by checking if it matches one of the provided patterns via [Pattern Matching](../language-reference/pattern-matching.md):</span></span>

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. <span data-ttu-id="12055-170">İlk [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) karakterin bir sesli harf olup olmadığını denetleyen ve ilk karakterin bir sesli harf mi olduğunu ve giriş karakterlerinden bir dönüş değeri mi olduğunu kontrol eden bir ifade.</span><span class="sxs-lookup"><span data-stu-id="12055-170">An [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expression that checks if the first character is a vowel, and constructs a return value out of the input characters based on if the first character was a vowel or not:</span></span>

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

<span data-ttu-id="12055-171">Flow `toPigLatin` bu nedenle:</span><span class="sxs-lookup"><span data-stu-id="12055-171">The flow of `toPigLatin` is thus:</span></span>

<span data-ttu-id="12055-172">Giriş sözcüğünün ilk karakterinin sesli harf olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="12055-172">Check if the first character of the input word is a vowel.</span></span> <span data-ttu-id="12055-173">Varsa, sözcüğün sonuna "oley" ekleyin.</span><span class="sxs-lookup"><span data-stu-id="12055-173">If it is, attach "yay" to the end of the word.</span></span> <span data-ttu-id="12055-174">Aksi takdirde, ilk karakteri sözcüğün sonuna taşıyın ve buna "ay" ekleyin.</span><span class="sxs-lookup"><span data-stu-id="12055-174">Otherwise, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="12055-175">Bunun hakkında dikkat edilecek bir son şey vardır: başka birçok dilin aksine, işlevden döndürülecek açık yönerge yoktur.</span><span class="sxs-lookup"><span data-stu-id="12055-175">There's one final thing to notice about this: there's no explicit instruction to return from the function, unlike many other languages out there.</span></span> <span data-ttu-id="12055-176">Bunun nedeni F# , ifade tabanlıdır ve bir işlevin gövdesindeki son ifade dönüş değeridir.</span><span class="sxs-lookup"><span data-stu-id="12055-176">This is because F# is Expression-based, and the last expression in the body of a function is the return value.</span></span> <span data-ttu-id="12055-177">Kendisinin bir ifadesi `then` `else` olduğu için, blok gövdesi veya bloğunun gövdesi, giriş değerine göre döndürülür. `if..then..else`</span><span class="sxs-lookup"><span data-stu-id="12055-177">Because `if..then..else` is itself an expression, the body of the `then` block or the body of the `else` block will be returned depending on the input value.</span></span>

## <a name="moving-your-script-code-into-the-implementation-file"></a><span data-ttu-id="12055-178">Betik kodunuzu uygulama dosyasına taşıma</span><span class="sxs-lookup"><span data-stu-id="12055-178">Moving your script code into the implementation file</span></span>

<span data-ttu-id="12055-179">Bu makalenin önceki bölümlerinde kod yazmanın F# yaygın bir ilk adımı gösterilmiştir: ilk işlev YAZıLıYOR ve FSI ile etkileşimli olarak yürütülüyor.</span><span class="sxs-lookup"><span data-stu-id="12055-179">The previous sections in this article demonstrated a common first step in writing F# code: writing an initial function and executing it interactively with FSI.</span></span> <span data-ttu-id="12055-180">Bu, [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) 'un "Read-değerlendir-PRINT loop" IÇIN aldığı REPL temelli geliştirme olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="12055-180">This is known as REPL-driven development, where [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) stands for "Read-Evaluate-Print Loop".</span></span> <span data-ttu-id="12055-181">Çalışır hale gelene kadar işlevselliği denemek için harika bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="12055-181">It's a great way to experiment with functionality until you have something working.</span></span>

<span data-ttu-id="12055-182">REPL temelli geliştirmede bir sonraki adım, çalışma kodunu bir F# uygulama dosyasına taşımadır.</span><span class="sxs-lookup"><span data-stu-id="12055-182">The next step in REPL-driven development is to move working code into an F# implementation file.</span></span> <span data-ttu-id="12055-183">Daha sonra, bu, F# derleyici tarafından yürütülebilecek bir derlemeye derlenebilir.</span><span class="sxs-lookup"><span data-stu-id="12055-183">It can then be compiled by the F# compiler into an assembly that can be executed.</span></span>

<span data-ttu-id="12055-184">Başlamak için öğesini açın `ClassLibraryDemo.fs`.</span><span class="sxs-lookup"><span data-stu-id="12055-184">To begin, open `ClassLibraryDemo.fs`.</span></span>  <span data-ttu-id="12055-185">Bazı kodların zaten orada olduğunu fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="12055-185">You'll notice that some code is already in there.</span></span> <span data-ttu-id="12055-186">Devam edin ve sınıf tanımını silin, ancak [`namespace`](../language-reference/namespaces.md) bildirimin en üstte ayrıldığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="12055-186">Go ahead and delete the class definition, but make sure to leave the [`namespace`](../language-reference/namespaces.md) declaration at the top.</span></span>

<span data-ttu-id="12055-187">Ardından, yeni [`module`](../language-reference/modules.md) bir adlı `PigLatin` oluşturma oluşturun ve `toPigLatin` işlevi bu şekilde kopyalayın:</span><span class="sxs-lookup"><span data-stu-id="12055-187">Next, create a new [`module`](../language-reference/modules.md) called `PigLatin` and copy the `toPigLatin` function into it as such:</span></span>

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

<span data-ttu-id="12055-188">Sonra, `Script.fsx` dosyayı yeniden açın ve tüm `toPigLatin` işlevi silin, ancak dosyada aşağıdaki iki satırı kaydettiğinizden emin olun:</span><span class="sxs-lookup"><span data-stu-id="12055-188">Next, open the `Script.fsx` file again, and delete the entire `toPigLatin` function, but make sure to keep the following two lines in the file:</span></span>

```fsharp
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

<span data-ttu-id="12055-189">Her iki metin satırını da seçin ve bu satırları FSI içinde yürütmek için alt + ENTER tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="12055-189">Select both lines of text and press Alt+Enter to execute these lines in FSI.</span></span> <span data-ttu-id="12055-190">Bu işlem, işlevselliğe erişebilmeniz için Pig Latin kitaplığı içeriğini FSI işlemine ve `open` `ClassLibraryDemo` ad alanına yükler.</span><span class="sxs-lookup"><span data-stu-id="12055-190">These will load the contents of the Pig Latin library into the FSI process and `open` the `ClassLibraryDemo` namespace so that you have access to the functionality.</span></span>

<span data-ttu-id="12055-191">Ardından, FSI penceresinde, daha önce tanımladığınız `PigLatin` modülün bulunduğu işlevi çağırın:</span><span class="sxs-lookup"><span data-stu-id="12055-191">Next, in the FSI window, call the function with the `PigLatin` module that you defined earlier:</span></span>

```console
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

<span data-ttu-id="12055-192">Başarılı!</span><span class="sxs-lookup"><span data-stu-id="12055-192">Success!</span></span> <span data-ttu-id="12055-193">Daha önce olduğu gibi, ancak şimdi bir F# uygulama dosyasından yüklediğiniz sonuçları alırsınız.</span><span class="sxs-lookup"><span data-stu-id="12055-193">You get the same results as before, but now loaded from an F# implementation file.</span></span> <span data-ttu-id="12055-194">Buradaki önemli fark, F# kaynak dosyalarının, yalnızca FSI içinde değil, her yerde yürütülebilecek derlemelerde derlendikleri bir farktır.</span><span class="sxs-lookup"><span data-stu-id="12055-194">The major difference here is that F# source files are compiled into assemblies that can be executed anywhere, not just in FSI.</span></span>

## <a name="summary"></a><span data-ttu-id="12055-195">Özet</span><span class="sxs-lookup"><span data-stu-id="12055-195">Summary</span></span>

<span data-ttu-id="12055-196">Bu makalede şunları öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="12055-196">In this article, you've learned:</span></span>

1. <span data-ttu-id="12055-197">Ionıde ile Visual Studio Code ayarlama.</span><span class="sxs-lookup"><span data-stu-id="12055-197">How to set up Visual Studio Code with Ionide.</span></span>
2. <span data-ttu-id="12055-198">Ionıde ile ilk F# projenizi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="12055-198">How to create your first F# project with Ionide.</span></span>
3. <span data-ttu-id="12055-199">Komut dosyası kullanarak F# ilk F# Işlevinizi ıonıde 'de yazın ve ardından FSI içinde yürütün.</span><span class="sxs-lookup"><span data-stu-id="12055-199">How to use F# Scripting to write your first F# function in Ionide and then execute it in FSI.</span></span>
4. <span data-ttu-id="12055-200">Betik kodunuzu F# kaynağa geçirme ve sonra bu kodu FSI 'dan çağırma.</span><span class="sxs-lookup"><span data-stu-id="12055-200">How to migrate your script code to F# source and then call that code from FSI.</span></span>

<span data-ttu-id="12055-201">Artık Visual Studio Code ve ıonıde kullanarak çok F# daha fazla kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12055-201">You're now equipped to write much more F# code using Visual Studio Code and Ionide.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="12055-202">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="12055-202">Troubleshooting</span></span>

<span data-ttu-id="12055-203">İşte karşılaşabileceğiniz bazı sorunları giderebilmeniz için birkaç yol aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="12055-203">Here are a few ways you can troubleshoot certain problems that you might run into:</span></span>

1. <span data-ttu-id="12055-204">Ionıde 'nin kod düzenlemesi özelliklerini almak için F# dosyalarınızın diske ve Visual Studio Code çalışma alanında açık olan bir klasörün içine kaydedilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="12055-204">To get the code editing features of Ionide, your F# files need to be saved to disk and inside of a folder that is open in the Visual Studio Code workspace.</span></span>
2. <span data-ttu-id="12055-205">Sisteminizde değişiklik yaptıysanız veya Visual Studio Code açık olarak ıonıde önkoşulları yüklediyseniz Visual Studio Code yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="12055-205">If you've made changes to your system or installed Ionide prerequisites with Visual Studio Code open, restart Visual Studio Code.</span></span>
3. <span data-ttu-id="12055-206">Derleyici ve etkileşimli ' i F# F# , tam yol olmadan komut satırından kullanıp kullandığınızı kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="12055-206">Check that you can use the F# compiler and F# interactive from the command line without a fully-qualified path.</span></span> <span data-ttu-id="12055-207">Bunu, F# derleyici için bir komut `fsc` satırına ve `fsi` ya `fsharpi` da Windows ve mono üzerinde Mac/Linux üzerinde bulunan F# görsel araçlar için yazarak yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12055-207">You can do so by typing `fsc` in a command line for the F# compiler, and `fsi` or `fsharpi` for the Visual F# tools on Windows and Mono on Mac/Linux, respectively.</span></span>
4. <span data-ttu-id="12055-208">Proje dizinlerinizde geçersiz karakterler varsa, ıonıde çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="12055-208">If you have invalid characters in your project directories, Ionide might not work.</span></span>  <span data-ttu-id="12055-209">Bu durumda proje dizinlerinizi yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="12055-209">Rename your project directories if this is the case.</span></span>
5. <span data-ttu-id="12055-210">Ionıde komutlarının hiçbiri çalışmıyorsa, yanlışlıkla geçersiz kılıp kıldığınızı görmek için [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) 'nizi denetleyin.</span><span class="sxs-lookup"><span data-stu-id="12055-210">If none of the Ionide commands are working, check your [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) to see if you're overriding them by accident.</span></span>
6. <span data-ttu-id="12055-211">Ionıde makinenizde bozulur ve yukarıdakilerden hiçbiri sorununuzu düzeltmediyse, makinenizde `ionide-fsharp` dizini kaldırmayı ve eklenti paketini yeniden yüklemeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="12055-211">If Ionide is broken on your machine and none of the above has fixed your problem, try removing the `ionide-fsharp` directory on your machine and reinstall the plugin suite.</span></span>

<span data-ttu-id="12055-212">Ionıde, F# topluluk üyeleri tarafından oluşturulan ve tutulan açık kaynaklı bir projem.</span><span class="sxs-lookup"><span data-stu-id="12055-212">Ionide is an open source project built and maintained by members of the F# community.</span></span> <span data-ttu-id="12055-213">Lütfen sorunları bildirin ve [ıonıde-vscode 'da katkıda bulunmak için ücretsizdir: FSharp GitHub deposu](https://github.com/ionide/ionide-vscode-fsharp).</span><span class="sxs-lookup"><span data-stu-id="12055-213">Please report issues and feel free to contribute at the [Ionide-VSCode: FSharp GitHub repository](https://github.com/ionide/ionide-vscode-fsharp).</span></span>

<span data-ttu-id="12055-214">Raporlama sorununuz varsa, lütfen [bir sorunu bildirirken kullanılacak günlükleri alma yönergelerini](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting)izleyin.</span><span class="sxs-lookup"><span data-stu-id="12055-214">If you have an issue to report, please follow [the instructions for getting logs to use when reporting an issue](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span></span>

<span data-ttu-id="12055-215">Ayrıca, ıonıde F# [Gitter kanalında](https://gitter.im/ionide/ionide-project)ıonıde geliştiricilerinden ve topluluğundan daha fazla yardım isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12055-215">You can also ask for further help from the Ionide developers and F# community in the [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span></span>

## <a name="next-steps"></a><span data-ttu-id="12055-216">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="12055-216">Next steps</span></span>

<span data-ttu-id="12055-217">Ve dilinin özellikleri hakkında F# daha fazla bilgi edinmek Için, [turuna F# ](../tour.md)göz atın.</span><span class="sxs-lookup"><span data-stu-id="12055-217">To learn more about F# and the features of the language, check out [Tour of F#](../tour.md).</span></span>
