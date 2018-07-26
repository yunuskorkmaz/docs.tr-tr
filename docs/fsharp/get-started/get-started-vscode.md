---
title: "Visual Studio code'da F # ile çalışmaya başlama"
description: "Visual Studio Code ve Ionide eklenti paketi ile F #'ı kullanmayı öğrenin."
ms.date: 05/28/2018
ms.openlocfilehash: 1afe985a4fe73d18b1e47b071b119c15a4672022
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874357"
---
# <a name="get-started-with-f-in-visual-studio-code"></a><span data-ttu-id="820a4-103">Visual Studio code'da F # ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="820a4-103">Get Started with F# in Visual Studio Code</span></span>

<span data-ttu-id="820a4-104">F # yazabileceğiniz [Visual Studio Code](https://code.visualstudio.com) ile [Ionide eklentisi](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) IntelliSense ve temel bir kodla harika bir çapraz platform, basit tümleşik geliştirme ortamı (IDE) deneyimi almak için yeniden düzenlemeler.</span><span class="sxs-lookup"><span data-stu-id="820a4-104">You can write F# in [Visual Studio Code](https://code.visualstudio.com) with the [Ionide plugin](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) to get a great cross-platform, lightweight Integrated Development Environment (IDE) experience with IntelliSense and basic code refactorings.</span></span> <span data-ttu-id="820a4-105">Ziyaret [Ionide.io](http://ionide.io) eklenti hakkında daha fazla bilgi edinmek için.</span><span class="sxs-lookup"><span data-stu-id="820a4-105">Visit [Ionide.io](http://ionide.io) to learn more about the plugin.</span></span>

<span data-ttu-id="820a4-106">Başlamak için sahip olduğunuzdan emin olun [F # ve doğru şekilde yüklenip Ionide eklentisi](install-fsharp.md#install-f-with-visual-studio-code).</span><span class="sxs-lookup"><span data-stu-id="820a4-106">To begin, ensure that you have [F# and the Ionide plugin correctly installed](install-fsharp.md#install-f-with-visual-studio-code).</span></span>

## <a name="creating-your-first-project-with-ionide"></a><span data-ttu-id="820a4-107">İlk projenizi Ionide ile oluşturma</span><span class="sxs-lookup"><span data-stu-id="820a4-107">Creating your first project with Ionide</span></span>

<span data-ttu-id="820a4-108">Yeni bir F # projesi oluşturmak için Visual Studio Code (onu istediğiniz gibi adlandırabilirsiniz) yeni bir klasöre açın.</span><span class="sxs-lookup"><span data-stu-id="820a4-108">To create a new F# project, open Visual Studio Code in a new folder (you can name it whatever you like).</span></span>

<span data-ttu-id="820a4-109">Ardından, komut paletinden açın (**Görüntüle > komut paletinden**) ve aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="820a4-109">Next, open the command pallette (**View > Command Pallette**) and type the following:</span></span>

```
> F# new project
```

<span data-ttu-id="820a4-110">Tarafından desteklenen bu [FORGE](https://github.com/fsharp-editing/Forge) proje.</span><span class="sxs-lookup"><span data-stu-id="820a4-110">This is powered by the [FORGE](https://github.com/fsharp-editing/Forge) project.</span></span>

> [!NOTE]
<span data-ttu-id="820a4-111">Şablon seçenekleri görmüyorsanız, komut paletini içinde aşağıdaki komutu çalıştırarak şablonları yenileme deneyin: `>F#: Refresh Project Templates`.</span><span class="sxs-lookup"><span data-stu-id="820a4-111">If you don't see template options, try refreshing templates by running the following command in the Command Palette: `>F#: Refresh Project Templates`.</span></span>

<span data-ttu-id="820a4-112">"F #: Yeni Proje" tuşlarına basarak seçin **Enter**.</span><span class="sxs-lookup"><span data-stu-id="820a4-112">Select "F#: New Project" by hitting **Enter**.</span></span> <span data-ttu-id="820a4-113">Bu, bir proje şablonu seçmek için olan bir sonraki adıma götürür.</span><span class="sxs-lookup"><span data-stu-id="820a4-113">This takes you to the next step, which is for selecting a project template.</span></span>

<span data-ttu-id="820a4-114">Çekme `classlib` şablonu ve isabet **Enter**.</span><span class="sxs-lookup"><span data-stu-id="820a4-114">Pick the `classlib` template and hit **Enter**.</span></span>

<span data-ttu-id="820a4-115">Ardından, projeyi oluşturmak için bir dizin seçin.</span><span class="sxs-lookup"><span data-stu-id="820a4-115">Next, pick a directory to create the project in.</span></span> <span data-ttu-id="820a4-116">Bunu boş bırakırsanız, geçerli dizin kullanır.</span><span class="sxs-lookup"><span data-stu-id="820a4-116">If you leave it blank, it uses the current directory.</span></span>

<span data-ttu-id="820a4-117">Son olarak, son adım, projenizi adlandırın.</span><span class="sxs-lookup"><span data-stu-id="820a4-117">Finally, name your project in the final step.</span></span> <span data-ttu-id="820a4-118">F # kullandığı [baş harfleri büyük](http://c2.com/cgi/wiki?PascalCase) proje adları için.</span><span class="sxs-lookup"><span data-stu-id="820a4-118">F# uses [Pascal case](http://c2.com/cgi/wiki?PascalCase) for project names.</span></span> <span data-ttu-id="820a4-119">Bu makalede `ClassLibraryDemo` adı.</span><span class="sxs-lookup"><span data-stu-id="820a4-119">This article uses `ClassLibraryDemo` as the name.</span></span> <span data-ttu-id="820a4-120">Projeniz için istediğiniz ad girdikten sonra isabet **Enter**.</span><span class="sxs-lookup"><span data-stu-id="820a4-120">Once you've entered the name you want for your project, hit **Enter**.</span></span>

<span data-ttu-id="820a4-121">Önceki adımları izlediyseniz, Visual Studio kodu aşağıdakiyle görünmesini çalışma alanı sol taraftaki almanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="820a4-121">If you followed the previous step, you should get the Visual Studio Code Workspace on the left-hand side to appear with the following:</span></span>

1. <span data-ttu-id="820a4-122">F # projesini altındaki `ClassLibraryDemo` klasör.</span><span class="sxs-lookup"><span data-stu-id="820a4-122">The F# project itself, underneath the `ClassLibraryDemo` folder.</span></span>
2. <span data-ttu-id="820a4-123">Paketler aracılığıyla eklemek için doğru dizin yapısı [ `Paket` ](https://fsprojects.github.io/Paket/).</span><span class="sxs-lookup"><span data-stu-id="820a4-123">The correct directory structure for adding packages via [`Paket`](https://fsprojects.github.io/Paket/).</span></span>
3. <span data-ttu-id="820a4-124">Platformlar arası derleme betiği ile [ `FAKE` ](https://fsharp.github.io/FAKE/).</span><span class="sxs-lookup"><span data-stu-id="820a4-124">A cross-platform build script with [`FAKE`](https://fsharp.github.io/FAKE/).</span></span>
4. <span data-ttu-id="820a4-125">`paket.exe` Fetch paketler ve bağımlılıkları çözümlemeniz için çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="820a4-125">The `paket.exe` executable that can fetch packages and resolve dependencies for you.</span></span>
5. <span data-ttu-id="820a4-126">A `.gitignore` bu proje Git tabanlı kaynak denetimine eklemek isterseniz, dosya.</span><span class="sxs-lookup"><span data-stu-id="820a4-126">A `.gitignore` file if you wish to add this project to Git-based source control.</span></span>

## <a name="writing-some-code"></a><span data-ttu-id="820a4-127">Bazı kodlar yazma</span><span class="sxs-lookup"><span data-stu-id="820a4-127">Writing some code</span></span>

<span data-ttu-id="820a4-128">Açık *ClassLibraryDemo* klasör.</span><span class="sxs-lookup"><span data-stu-id="820a4-128">Open the *ClassLibraryDemo* folder.</span></span>  <span data-ttu-id="820a4-129">Aşağıdaki dosyaları göreceksiniz:</span><span class="sxs-lookup"><span data-stu-id="820a4-129">You should see the following files:</span></span>

1. <span data-ttu-id="820a4-130">`ClassLibraryDemo.fs`, bir F # uygulama dosyasını ile tanımlanmış bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="820a4-130">`ClassLibraryDemo.fs`, an F# implementation file with a class defined.</span></span>
2. <span data-ttu-id="820a4-131">`ClassLibraryDemo.fsproj`, bu projeyi oluşturmak için kullanılan bir F # proje dosyası.</span><span class="sxs-lookup"><span data-stu-id="820a4-131">`ClassLibraryDemo.fsproj`, an F# project file used to build this project.</span></span>
3. <span data-ttu-id="820a4-132">`Script.fsx`, kaynak dosyasını yükleyen bir F # betik dosyası.</span><span class="sxs-lookup"><span data-stu-id="820a4-132">`Script.fsx`, an F# script file that loads the source file.</span></span>
4. <span data-ttu-id="820a4-133">`paket.references`, proje bağımlılıkları belirten bir Paket dosyası.</span><span class="sxs-lookup"><span data-stu-id="820a4-133">`paket.references`, a Paket file that specifies the project dependencies.</span></span>

<span data-ttu-id="820a4-134">Açık `Script.fsx`ve sonunda, aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="820a4-134">Open `Script.fsx`, and add the following code at the end of it:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

<span data-ttu-id="820a4-135">Bu işlev bir forma bir sözcük dönüştürür [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span><span class="sxs-lookup"><span data-stu-id="820a4-135">This function converts a word to a form of [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span></span> <span data-ttu-id="820a4-136">F # Etkileşimli (FSI) kullanarak değerlendirmek için sonraki adımdır bakın.</span><span class="sxs-lookup"><span data-stu-id="820a4-136">The next step is to evaluate it using F# Interactive (FSI).</span></span>

<span data-ttu-id="820a4-137">(11 satır uzunluğunda olmalıdır) tüm işlevi vurgulayın.</span><span class="sxs-lookup"><span data-stu-id="820a4-137">Highlight the entire function (it should be 11 lines long).</span></span> <span data-ttu-id="820a4-138">Vurgulanır sonra tutun **Alt** anahtar ve isabet **Enter**.</span><span class="sxs-lookup"><span data-stu-id="820a4-138">Once it is highlighted, hold the **Alt** key and hit **Enter**.</span></span> <span data-ttu-id="820a4-139">Aşağıdaki açılır penceresi bir pencere görürsünüz ve aşağıdakine benzer göstermelidir:</span><span class="sxs-lookup"><span data-stu-id="820a4-139">You'll notice a window pop up below, and it should show something like this:</span></span>

![Ionide ile F # Etkileşimli bir çıkış örneğidir](media/getting-started-vscode/vscode-fsi.png)

<span data-ttu-id="820a4-141">Bu üç şey yapar:</span><span class="sxs-lookup"><span data-stu-id="820a4-141">This did three things:</span></span>

1. <span data-ttu-id="820a4-142">Bu, FSI işlemi başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="820a4-142">It started the FSI process.</span></span>
2. <span data-ttu-id="820a4-143">Vurguladığınız kodun FSI işlem üzerinden gönderilir.</span><span class="sxs-lookup"><span data-stu-id="820a4-143">It sent the code you highlighted over the FSI process.</span></span>
3. <span data-ttu-id="820a4-144">FSI işlem üzerinden gönderilen kodu değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="820a4-144">The FSI process evaluated the code you sent over.</span></span>

<span data-ttu-id="820a4-145">Üzerinden gönderilen olduğundan bir [işlevi](../language-reference/functions/index.md), FSI ile bu işlevi çağırabilirsiniz!</span><span class="sxs-lookup"><span data-stu-id="820a4-145">Because what you sent over was a [function](../language-reference/functions/index.md), you can now call that function with FSI!</span></span> <span data-ttu-id="820a4-146">Etkileşimli pencerede aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="820a4-146">In the interactive window, type the following:</span></span>

```fsharp
toPigLatin "banana";;
```

<span data-ttu-id="820a4-147">Aşağıdaki sonucu görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="820a4-147">You should see the following result:</span></span>

```fsharp
val it : string = "ananabay"
```

<span data-ttu-id="820a4-148">Artık, bir sesli olarak ilk harfi ile deneyelim.</span><span class="sxs-lookup"><span data-stu-id="820a4-148">Now, let's try with a vowel as the first letter.</span></span> <span data-ttu-id="820a4-149">Aşağıdakileri girin:</span><span class="sxs-lookup"><span data-stu-id="820a4-149">Enter the following:</span></span>

```fsharp
toPigLatin "apple";;
```

<span data-ttu-id="820a4-150">Aşağıdaki sonucu görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="820a4-150">You should see the following result:</span></span>

```fsharp
val it : string = "appleyay"
```

<span data-ttu-id="820a4-151">İşlev beklendiği gibi çalışıyor gibi görünüyor.</span><span class="sxs-lookup"><span data-stu-id="820a4-151">The function appears to be working as expected.</span></span> <span data-ttu-id="820a4-152">Tebrikler, yalnızca Visual Studio Code'da ilk F # işlevinizi yazdı ve FSI ile değerlendirilen!</span><span class="sxs-lookup"><span data-stu-id="820a4-152">Congratulations, you just wrote your first F# function in Visual Studio Code and evaluated it with FSI!</span></span>

>[!NOTE]
<span data-ttu-id="820a4-153">Fark etmiş olabilirsiniz gibi FSI satırları ile sonlandırılır `;;`.</span><span class="sxs-lookup"><span data-stu-id="820a4-153">As you may have noticed, the lines in FSI are terminated with `;;`.</span></span> <span data-ttu-id="820a4-154">Bu durum, FSI birden fazla satır girmenizi sağlar çünkü.</span><span class="sxs-lookup"><span data-stu-id="820a4-154">This is because FSI allows you to enter multiple lines.</span></span> <span data-ttu-id="820a4-155">`;;` Sonunda kodu tamamlandığında bilmeniz FSI olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="820a4-155">The `;;` at the end lets FSI know when the code is finished.</span></span>

## <a name="explaining-the-code"></a><span data-ttu-id="820a4-156">Kod açıklayan</span><span class="sxs-lookup"><span data-stu-id="820a4-156">Explaining the code</span></span>

<span data-ttu-id="820a4-157">Kod gerçekten yaptığı hakkında emin değilseniz, işte bir adım adım.</span><span class="sxs-lookup"><span data-stu-id="820a4-157">If you're not sure about what the code is actually doing, here's a step-by-step.</span></span>

<span data-ttu-id="820a4-158">Gördüğünüz gibi `toPigLatin` , bir sözcük, girdi olarak alır ve söz konusu sözcüğün bir Pig Latin gösterimine dönüştürür bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="820a4-158">As you can see, `toPigLatin` is a function that takes a word as its input and converts it to a Pig-Latin representation of that word.</span></span> <span data-ttu-id="820a4-159">Bu kurallar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="820a4-159">The rules for this are as follows:</span></span>

<span data-ttu-id="820a4-160">İlk karakter bir sözcük, bir harfle başlar "yay" kelimenin sonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="820a4-160">If the first character in a word starts with a vowel, add "yay" to the end of the word.</span></span> <span data-ttu-id="820a4-161">Bir harfle başlamazsa, ilk karakterden kelimenin sonuna taşı ve "ay" ekleyin.</span><span class="sxs-lookup"><span data-stu-id="820a4-161">If it doesn't start with a vowel, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="820a4-162">FSI aşağıdaki fark etmiş olabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="820a4-162">You may have noticed the following in FSI:</span></span>

```fsharp
val toPigLatin : word:string -> string
```

<span data-ttu-id="820a4-163">Bu bildiren `toPigLatin` alır bir işlev, bir `string` giriş olarak (adlı `word`) ve başka döndürür `string`.</span><span class="sxs-lookup"><span data-stu-id="820a4-163">This states that `toPigLatin` is a function that takes in a `string` as input (called `word`), and returns another `string`.</span></span> <span data-ttu-id="820a4-164">Bu olarak bilinir [işlevin türü imzası](https://fsharpforfunandprofit.com/posts/function-signatures/), temel bir F # bu kadar F # kodu anlamanın anahtardır.</span><span class="sxs-lookup"><span data-stu-id="820a4-164">This is known as the [type signature of the function](https://fsharpforfunandprofit.com/posts/function-signatures/), a fundamental piece of F# that's key to understanding F# code.</span></span> <span data-ttu-id="820a4-165">Visual Studio code'da işlevi üzerine getirin, ayrıca bu fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="820a4-165">You'll also notice this if you hover over the function in Visual Studio Code.</span></span>

<span data-ttu-id="820a4-166">İşlevin gövdesinde, iki farklı bölümlerini göreceksiniz:</span><span class="sxs-lookup"><span data-stu-id="820a4-166">In the body of the function, you'll notice two distinct parts:</span></span>

1. <span data-ttu-id="820a4-167">Çağrılan bir iç işlev `isVowel`, belirli bir karakterin belirler (`c`) sağlanan desenlerden biriyle eşleşiyorsa kontrol ederek bir ünlü olduğunu [desen eşleştirme](../language-reference/pattern-matching.md):</span><span class="sxs-lookup"><span data-stu-id="820a4-167">An inner function, called `isVowel`, that determines if a given character (`c`) is a vowel by checking if it matches one of the provided patterns via [Pattern Matching](../language-reference/pattern-matching.md):</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. <span data-ttu-id="820a4-168">Bir [ `if..then..else` ](../language-reference/conditional-expressions-if-then-else.md) veya ilk karakter bir sesli ise ve ilk karakter bir dönüş değeri giriş karakterleri dışında yapıları tabanlı halinde denetleyen bir ifade olan bir sesli:</span><span class="sxs-lookup"><span data-stu-id="820a4-168">An [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expression that checks if the first character is a vowel, and constructs a return value out of the input characters based on if the first character was a vowel or not:</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

<span data-ttu-id="820a4-169">Akışı `toPigLatin` böylece:</span><span class="sxs-lookup"><span data-stu-id="820a4-169">The flow of `toPigLatin` is thus:</span></span>

<span data-ttu-id="820a4-170">Giriş kelimenin ilk karakteri bir sesli olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="820a4-170">Check if the first character of the input word is a vowel.</span></span> <span data-ttu-id="820a4-171">İse, "yay" kelimenin sonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="820a4-171">If it is, attach "yay" to the end of the word.</span></span> <span data-ttu-id="820a4-172">Aksi takdirde, ilk karakterden kelimenin sonuna taşı ve "ay" ekleyin.</span><span class="sxs-lookup"><span data-stu-id="820a4-172">Otherwise, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="820a4-173">Bu konuda fark etmeye son bir şey yoktur: birçok başka dile burada aksine, işlevden döndürülecek hiçbir açık bir yönerge yoktur.</span><span class="sxs-lookup"><span data-stu-id="820a4-173">There's one final thing to notice about this: there's no explicit instruction to return from the function, unlike many other languages out there.</span></span> <span data-ttu-id="820a4-174">F # ifade tabanlı ve bir işlevin gövdesinde son deyim dönüş değeri olduğundan budur.</span><span class="sxs-lookup"><span data-stu-id="820a4-174">This is because F# is Expression-based, and the last expression in the body of a function is the return value.</span></span> <span data-ttu-id="820a4-175">Çünkü `if..then..else` kendisi bir deyim gövdesi olan `then` blok veya gövdesinin `else` blok bağlı olarak giriş değeri döndürülür.</span><span class="sxs-lookup"><span data-stu-id="820a4-175">Because `if..then..else` is itself an expression, the body of the `then` block or the body of the `else` block will be returned depending on the input value.</span></span>

## <a name="moving-your-script-code-into-the-implementation-file"></a><span data-ttu-id="820a4-176">Uygulama dosyasına betik kodunuzu taşıma</span><span class="sxs-lookup"><span data-stu-id="820a4-176">Moving your script code into the implementation file</span></span>

<span data-ttu-id="820a4-177">Bu makalede önceki bölümlerde gösterildiği F # kodu yazarken, ortak bir ilk adım: bir ilk işlevi yazma ve FSI ile etkileşimli olarak yürütme.</span><span class="sxs-lookup"><span data-stu-id="820a4-177">The previous sections in this article demonstrated a common first step in writing F# code: writing an initial function and executing it interactively with FSI.</span></span> <span data-ttu-id="820a4-178">Bu REPL odaklı geliştirme bilinir burada [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) "Okuma değerlendirmek yazdırma döngü için" anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="820a4-178">This is known as REPL-driven development, where [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) stands for "Read-Evaluate-Print Loop".</span></span> <span data-ttu-id="820a4-179">Bir sorun çalışma bulunana kadar işlevselliğe sahip denemek için harika bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="820a4-179">It's a great way to experiment with functionality until you have something working.</span></span>

<span data-ttu-id="820a4-180">REPL odaklı geliştirme sonraki adımda, çalışan kodu bir F # uygulama dosyasına taşımaktır.</span><span class="sxs-lookup"><span data-stu-id="820a4-180">The next step in REPL-driven development is to move working code into an F# implementation file.</span></span> <span data-ttu-id="820a4-181">Ardından yürütülebilecek bir derlemeye F # derleyicisi tarafından olarak da derlenebilir.</span><span class="sxs-lookup"><span data-stu-id="820a4-181">It can then be compiled by the F# compiler into an assembly that can be executed.</span></span>

<span data-ttu-id="820a4-182">Başlamak için açık `ClassLibraryDemo.fs`.</span><span class="sxs-lookup"><span data-stu-id="820a4-182">To begin, open `ClassLibraryDemo.fs`.</span></span>  <span data-ttu-id="820a4-183">Bazı kod zaten kullanımda olduğunu fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="820a4-183">You'll notice that some code is already in there.</span></span> <span data-ttu-id="820a4-184">Devam edin ve sınıf tanımı silin, ancak bıraktığınızdan emin olun [ `namespace` ](../language-reference/namespaces.md) bildiriminin en üstünde.</span><span class="sxs-lookup"><span data-stu-id="820a4-184">Go ahead and delete the class definition, but make sure to leave the [`namespace`](../language-reference/namespaces.md) declaration at the top.</span></span>

<span data-ttu-id="820a4-185">Ardından, yeni bir oluşturma [ `module` ](../language-reference/modules.md) adlı `PigLatin` ve kopyalama `toPigLatin` işleve, bu nedenle:</span><span class="sxs-lookup"><span data-stu-id="820a4-185">Next, create a new [`module`](../language-reference/modules.md) called `PigLatin` and copy the `toPigLatin` function into it as such:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

<span data-ttu-id="820a4-186">Ardından, açık `Script.fsx` dosya yeniden ve tüm silme `toPigLatin` çalışır, ancak aşağıdaki iki satırı dosyasında tutmak olduğundan emin olun:</span><span class="sxs-lookup"><span data-stu-id="820a4-186">Next, open the `Script.fsx` file again, and delete the entire `toPigLatin` function, but make sure to keep the following two lines in the file:</span></span>

```fsharp
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

<span data-ttu-id="820a4-187">İlk satırı yüklemek için betik FSI için gereken `ClassLibraryDemo.fs`.</span><span class="sxs-lookup"><span data-stu-id="820a4-187">The first line is needed for FSI scripting to load `ClassLibraryDemo.fs`.</span></span> <span data-ttu-id="820a4-188">Kolaylık olması açısından ikinci çizgidir: belirlemesini sağlayabilirsiniz isteğe bağlıdır, ancak yazmanız gerekecektir `open ClassLibraryDemo` getirmek istiyorsanız FSI penceresinde `ToPigLatin` kapsama modülü.</span><span class="sxs-lookup"><span data-stu-id="820a4-188">The second line is a convenience: omitting it is optional, but you will need to type `open ClassLibraryDemo` in an FSI window if you wish to bring the `ToPigLatin` module into scope.</span></span>

<span data-ttu-id="820a4-189">Ardından, FSI penceresinde işlevi çağrısı `PigLatin` daha önce tanımladığınız Modülü:</span><span class="sxs-lookup"><span data-stu-id="820a4-189">Next, in the FSI window, call the function with the `PigLatin` module that you defined earlier:</span></span>

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

<span data-ttu-id="820a4-190">Başarılı!</span><span class="sxs-lookup"><span data-stu-id="820a4-190">Success!</span></span> <span data-ttu-id="820a4-191">Önce olarak aynı sonuçlar elde edin, ancak artık bir F # uygulama dosyasından yüklenen.</span><span class="sxs-lookup"><span data-stu-id="820a4-191">You get the same results as before, but now loaded from an F# implementation file.</span></span> <span data-ttu-id="820a4-192">Burada en önemli fark, F # kaynak dosyaları yalnızca FSI içinde her yerden yürütülebilecek derlemeleri halinde derlenir ' dir.</span><span class="sxs-lookup"><span data-stu-id="820a4-192">The major difference here is that F# source files are compiled into assemblies that can be executed anywhere, not just in FSI.</span></span>

## <a name="summary"></a><span data-ttu-id="820a4-193">Özet</span><span class="sxs-lookup"><span data-stu-id="820a4-193">Summary</span></span>

<span data-ttu-id="820a4-194">Bu makalede, öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="820a4-194">In this article, you've learned:</span></span>

1. <span data-ttu-id="820a4-195">Visual Studio Code ve Ionide ayarlama yapma.</span><span class="sxs-lookup"><span data-stu-id="820a4-195">How to set up Visual Studio Code with Ionide.</span></span>
2. <span data-ttu-id="820a4-196">Ionide ile ilk, F # projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="820a4-196">How to create your first F# project with Ionide.</span></span>
3. <span data-ttu-id="820a4-197">İlk F # işlevinizi Ionide içinde yazmak ve FSI içinde çalıştırmak için F # komut dosyası kullanma</span><span class="sxs-lookup"><span data-stu-id="820a4-197">How to use F# Scripting to write your first F# function in Ionide and then execute it in FSI.</span></span>
4. <span data-ttu-id="820a4-198">Kodunuzu geçirme için F # kaynak kodu ve kod FSI çağırın.</span><span class="sxs-lookup"><span data-stu-id="820a4-198">How to migrate your script code to F# source and then call that code from FSI.</span></span>

<span data-ttu-id="820a4-199">Artık Visual Studio Code ve Ionide kullanarak olan çok daha fazla F # kodu yazmak için donatılmış.</span><span class="sxs-lookup"><span data-stu-id="820a4-199">You're now equipped to write much more F# code using Visual Studio Code and Ionide.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="820a4-200">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="820a4-200">Troubleshooting</span></span>

<span data-ttu-id="820a4-201">Karşılaşabileceğiniz bazı sorunları giderebilir birkaç yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="820a4-201">Here are a few ways you can troubleshoot certain problems that you might run into:</span></span>

1. <span data-ttu-id="820a4-202">Kod düzenleme Ionide özelliklerini almak için F # dosyaları diske ve Visual Studio Code çalışma alanında açık olan bir klasör içinde kaydedilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="820a4-202">To get the code editing features of Ionide, your F# files need to be saved to disk and inside of a folder that is open in the Visual Studio Code workspace.</span></span>
2. <span data-ttu-id="820a4-203">Visual Studio Code, sisteme yapılan değişiklikler veya Visual Studio Code ile açık Ionide Önkoşullar yüklendi, yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="820a4-203">If you've made changes to your system or installed Ionide prerequisites with Visual Studio Code open, restart Visual Studio Code.</span></span>
3. <span data-ttu-id="820a4-204">F # derleyicisi ve F # etkileşimli komut satırı tam olarak nitelenmiş bir yol olmadan kullanıp kullanmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="820a4-204">Check that you can use the F# compiler and F# interactive from the command line without a fully-qualified path.</span></span> <span data-ttu-id="820a4-205">Yazarak bunu yapabilirsiniz `fsc` için F # derleyicisi, komut satırında ve `fsi` veya `fsharpi` Visual F # için Araçlar Windows ve Mac/Linux'ta, Mono sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="820a4-205">You can do so by typing `fsc` in a command line for the F# compiler, and `fsi` or `fsharpi` for the Visual F# tools on Windows and Mono on Mac/Linux, respectively.</span></span>
4. <span data-ttu-id="820a4-206">Proje dizinlerinizde geçersiz karakterler varsa, Ionide çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="820a4-206">If you have invalid characters in your project directories, Ionide might not work.</span></span>  <span data-ttu-id="820a4-207">Bu durumda, proje dizinleri yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="820a4-207">Rename your project directories if this is the case.</span></span>
5. <span data-ttu-id="820a4-208">Ionide komutların hiçbiri çalışıyorsanız, denetle, [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) , bunları yanlışlıkla geçersiz kılma olmadığını görmek için.</span><span class="sxs-lookup"><span data-stu-id="820a4-208">If none of the Ionide commands are working, check your [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) to see if you're overriding them by accident.</span></span>
6. <span data-ttu-id="820a4-209">Yukarıdakilerin hiçbiri sorununuzu düzeltmiştir ve Ionide makinenizde bozuk, uygulamadan yetkilendirmeleri `ionide-fsharp` makinenizde dizin ve eklenti paketini yeniden yükleyin.</span><span class="sxs-lookup"><span data-stu-id="820a4-209">If Ionide is broken on your machine and none of the above has fixed your problem, try removing the `ionide-fsharp` directory on your machine and reinstall the plugin suite.</span></span>

<span data-ttu-id="820a4-210">Ionide yerleşik ve F # topluluğunun üyeleri tarafından tutulan bir açık kaynak projesidir.</span><span class="sxs-lookup"><span data-stu-id="820a4-210">Ionide is an open source project built and maintained by members of the F# community.</span></span> <span data-ttu-id="820a4-211">Lütfen rapor sorunları ve en katkıda çekinmeyin [Ionide VSCode: FSharp GitHub deposu](https://github.com/ionide/ionide-vscode-fsharp).</span><span class="sxs-lookup"><span data-stu-id="820a4-211">Please report issues and feel free to contribute at the [Ionide-VSCode: FSharp GitHub repository](https://github.com/ionide/ionide-vscode-fsharp).</span></span>

<span data-ttu-id="820a4-212">Rapor için bir sorun varsa, lütfen izleyin [bir sorun bildirirken kullanmak için günlükleri alma yönergelerini](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span><span class="sxs-lookup"><span data-stu-id="820a4-212">If you have an issue to report, please follow [the instructions for getting logs to use when reporting an issue](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span></span>

<span data-ttu-id="820a4-213">Ionide geliştiriciler ve F # Topluluğu'nda daha fazla yardım için sorabilir [Ionide Gitter kanal](https://gitter.im/ionide/ionide-project).</span><span class="sxs-lookup"><span data-stu-id="820a4-213">You can also ask for further help from the Ionide developers and F# community in the [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span></span>

## <a name="next-steps"></a><span data-ttu-id="820a4-214">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="820a4-214">Next steps</span></span>

<span data-ttu-id="820a4-215">F # ve dil özellikleri hakkında daha fazla bilgi edinmek için kullanıma [turu, F #](../tour.md).</span><span class="sxs-lookup"><span data-stu-id="820a4-215">To learn more about F# and the features of the language, check out [Tour of F#](../tour.md).</span></span>
