---
title: Visual Studio Code’da F# Kullanmaya Başlama
description: Visual Studio Code ve ıonıde eklenti Suite ile nasıl kullanacağınızı F# öğrenin.
ms.date: 12/23/2018
ms.openlocfilehash: 91265303c2954387df0f500940c9af68b3c97dac
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559670"
---
# <a name="get-started-with-f-in-visual-studio-code"></a><span data-ttu-id="38f9e-103">Visual Studio Code’da F# Kullanmaya Başlama</span><span class="sxs-lookup"><span data-stu-id="38f9e-103">Get Started with F# in Visual Studio Code</span></span>

<span data-ttu-id="38f9e-104">IntelliSense ve Code F# yeniden düzenlemeler ile harika platformlar arası, hafif tümleşik geliştirme ORTAMı (IDE) deneyimi almak Için [ıonıde eklentisine](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) [Visual Studio Code](https://code.visualstudio.com) yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38f9e-104">You can write F# in [Visual Studio Code](https://code.visualstudio.com) with the [Ionide plugin](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) to get a great cross-platform, lightweight Integrated Development Environment (IDE) experience with IntelliSense and code refactorings.</span></span> <span data-ttu-id="38f9e-105">Eklenti hakkında daha fazla bilgi edinmek için [Ionide.io](http://ionide.io) ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="38f9e-105">Visit [Ionide.io](http://ionide.io) to learn more about the plugin.</span></span>

<span data-ttu-id="38f9e-106">Başlamak için [ F# ve ıonıde eklentisinin doğru yüklendiğinden](install-fsharp.md#install-f-with-visual-studio-code)emin olun.</span><span class="sxs-lookup"><span data-stu-id="38f9e-106">To begin, ensure that you have [F# and the Ionide plugin correctly installed](install-fsharp.md#install-f-with-visual-studio-code).</span></span>

## <a name="create-your-first-project-with-ionide"></a><span data-ttu-id="38f9e-107">Ionıde ile ilk projenizi oluşturma</span><span class="sxs-lookup"><span data-stu-id="38f9e-107">Create your first project with Ionide</span></span>

<span data-ttu-id="38f9e-108">Yeni F# bir proje oluşturmak için bir komut satırı açın ve .NET Core CLI yeni bir proje oluşturun:</span><span class="sxs-lookup"><span data-stu-id="38f9e-108">To create a new F# project, open a command line and create a new project with the .NET Core CLI:</span></span>

```dotnetcli
dotnet new console -lang "F#" -o FirstIonideProject
```

<span data-ttu-id="38f9e-109">Tamamlandıktan sonra, dizini projeye değiştirin ve Visual Studio Code açın:</span><span class="sxs-lookup"><span data-stu-id="38f9e-109">Once it completes, change directory to the project and open Visual Studio Code:</span></span>

```console
cd FirstIonideProject
code .
```

<span data-ttu-id="38f9e-110">Proje Visual Studio Code yüklendikten sonra, pencerenin sol tarafındaki F# Çözüm Gezgini bölmesini görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="38f9e-110">After the project loads on Visual Studio Code, you should see the F# Solution Explorer pane on the left-hand side of your window open.</span></span> <span data-ttu-id="38f9e-111">Bu, ıonıde 'nin yeni oluşturduğunuz projeyi başarıyla yüklediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="38f9e-111">This means Ionide has successfully loaded the project you just created.</span></span> <span data-ttu-id="38f9e-112">Bu noktadan önce düzenleyicide kod yazabilirsiniz, ancak bu durum gerçekleştiğinde her şeyin yüklenmesi tamamlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="38f9e-112">You can write code in the editor before this point in time, but once this happens, everything has finished loading.</span></span>

## <a name="configure-f-interactive"></a><span data-ttu-id="38f9e-113">Etkileşimli F# yapılandırma</span><span class="sxs-lookup"><span data-stu-id="38f9e-113">Configure F# interactive</span></span>

<span data-ttu-id="38f9e-114">İlk olarak, .NET Core Scripting 'in varsayılan betik ortamınız olduğundan emin olun:</span><span class="sxs-lookup"><span data-stu-id="38f9e-114">First, ensure that .NET Core scripting is your default scripting environment:</span></span>

1. <span data-ttu-id="38f9e-115">Visual Studio Code ayarlarını açın (**kod** > **tercihleri** > **ayarları**).</span><span class="sxs-lookup"><span data-stu-id="38f9e-115">Open the Visual Studio Code settings (**Code** > **Preferences** > **Settings**).</span></span>
1. <span data-ttu-id="38f9e-116">Terim  **F# betiğini**arayın.</span><span class="sxs-lookup"><span data-stu-id="38f9e-116">Search for the term **F# Script**.</span></span>
1. <span data-ttu-id="38f9e-117">**FSharp: SDK betikleri kullan**onay kutusuna tıklayın.</span><span class="sxs-lookup"><span data-stu-id="38f9e-117">Click the checkbox that says **FSharp: use SDK scripts**.</span></span>

<span data-ttu-id="38f9e-118">Bu şu anda, .NET Core komut dosyası ile çalışmayan .NET Framework tabanlı betikteki bazı eski davranışlar nedeniyle gereklidir ve ıonıde Şu anda bu geriye dönük uyumluluk için çaba harcar.</span><span class="sxs-lookup"><span data-stu-id="38f9e-118">This is currently necessary due to some legacy behaviors in .NET Framework-based scripting that don't work with .NET Core scripting, and Ionide is currently striving for that backwards compatibility.</span></span> <span data-ttu-id="38f9e-119">Gelecekte, .NET Core Scripting varsayılan değer olacaktır.</span><span class="sxs-lookup"><span data-stu-id="38f9e-119">In the future, .NET Core scripting will become the default.</span></span>

### <a name="write-your-first-script"></a><span data-ttu-id="38f9e-120">İlk komut dosyanızı yazma</span><span class="sxs-lookup"><span data-stu-id="38f9e-120">Write your first script</span></span>

<span data-ttu-id="38f9e-121">.NET Core komut dosyası kullanmak üzere Visual Studio Code yapılandırdıktan sonra, Visual Studio Code gezgin görünümüne gidin ve yeni bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="38f9e-121">Once you've configured Visual Studio Code to use .NET Core scripting, navigate to the Explorer view in Visual Studio Code and create a new file.</span></span> <span data-ttu-id="38f9e-122">*Myfirstscript. FSX*olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="38f9e-122">Name it *MyFirstScript.fsx*.</span></span>

<span data-ttu-id="38f9e-123">Şimdi aşağıdaki kodu buna ekleyin:</span><span class="sxs-lookup"><span data-stu-id="38f9e-123">Now add the following code to it:</span></span>

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

<span data-ttu-id="38f9e-124">Bu işlev, bir kelimeyi bir [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin)biçimine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="38f9e-124">This function converts a word to a form of [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span></span> <span data-ttu-id="38f9e-125">Bir sonraki adım, bunu etkileşimli (FSI F# ) kullanarak değerlendirmelidir.</span><span class="sxs-lookup"><span data-stu-id="38f9e-125">The next step is to evaluate it using F# Interactive (FSI).</span></span>

<span data-ttu-id="38f9e-126">İşlevin tamamını vurgulayın (11 satır uzunluğunda olmalıdır).</span><span class="sxs-lookup"><span data-stu-id="38f9e-126">Highlight the entire function (it should be 11 lines long).</span></span> <span data-ttu-id="38f9e-127">Vurgulandıktan sonra, **alt** tuşunu basılı tutun ve **ENTER**tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="38f9e-127">Once it's highlighted, hold the **Alt** key and hit **Enter**.</span></span> <span data-ttu-id="38f9e-128">Ekranın alt kısmında bir Terminal penceresi açılır ve şuna benzer görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="38f9e-128">You'll notice a terminal window pop up on the bottom of the screen, and it should look similar to this:</span></span>

![Ionıde ile F# etkileşimli çıkış örneği](./media/getting-started-vscode/vscode-fsi.png)

<span data-ttu-id="38f9e-130">Bu üç şey oldu:</span><span class="sxs-lookup"><span data-stu-id="38f9e-130">This did three things:</span></span>

1. <span data-ttu-id="38f9e-131">Bu işlem, FSI işlemini başlattı.</span><span class="sxs-lookup"><span data-stu-id="38f9e-131">It started the FSI process.</span></span>
2. <span data-ttu-id="38f9e-132">Bu, FSI işlemi üzerinde vurguladığınız kodu gönderdi.</span><span class="sxs-lookup"><span data-stu-id="38f9e-132">It sent the code you highlighted over the FSI process.</span></span>
3. <span data-ttu-id="38f9e-133">FSI işlemi, üzerinden gönderdiğiniz kodu değerlendirdi.</span><span class="sxs-lookup"><span data-stu-id="38f9e-133">The FSI process evaluated the code you sent over.</span></span>

<span data-ttu-id="38f9e-134">Üzerinden gönderildikleriniz bir [işleviydi](../language-reference/functions/index.md), artık bu işlevi FSI ile çağırabilirsiniz!</span><span class="sxs-lookup"><span data-stu-id="38f9e-134">Because what you sent over was a [function](../language-reference/functions/index.md), you can now call that function with FSI!</span></span> <span data-ttu-id="38f9e-135">Etkileşimli pencerede şunları yazın:</span><span class="sxs-lookup"><span data-stu-id="38f9e-135">In the interactive window, type the following:</span></span>

```fsharp
toPigLatin "banana";;
```

<span data-ttu-id="38f9e-136">Aşağıdaki sonucu görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="38f9e-136">You should see the following result:</span></span>

```fsharp
val it : string = "ananabay"
```

<span data-ttu-id="38f9e-137">Şimdi ilk harf olarak bir sesli harf deneyelim.</span><span class="sxs-lookup"><span data-stu-id="38f9e-137">Now, let's try with a vowel as the first letter.</span></span> <span data-ttu-id="38f9e-138">Aşağıdakileri girin:</span><span class="sxs-lookup"><span data-stu-id="38f9e-138">Enter the following:</span></span>

```fsharp
toPigLatin "apple";;
```

<span data-ttu-id="38f9e-139">Aşağıdaki sonucu görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="38f9e-139">You should see the following result:</span></span>

```fsharp
val it : string = "appleyay"
```

<span data-ttu-id="38f9e-140">İşlev beklenen şekilde çalışıyor gibi görünüyor.</span><span class="sxs-lookup"><span data-stu-id="38f9e-140">The function appears to be working as expected.</span></span> <span data-ttu-id="38f9e-141">Tebrikler, ilk F# işlevinizi Visual Studio Code YAZMıŞ ve FSI ile değerlendirdiniz!</span><span class="sxs-lookup"><span data-stu-id="38f9e-141">Congratulations, you just wrote your first F# function in Visual Studio Code and evaluated it with FSI!</span></span>

> [!NOTE]
> <span data-ttu-id="38f9e-142">Fark etmişsinizdir, FSI içindeki satırlar `;;`ile sonlandırılır.</span><span class="sxs-lookup"><span data-stu-id="38f9e-142">As you may have noticed, the lines in FSI are terminated with `;;`.</span></span> <span data-ttu-id="38f9e-143">Bunun nedeni, FSI 'in birden çok satır girmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="38f9e-143">This is because FSI allows you to enter multiple lines.</span></span> <span data-ttu-id="38f9e-144">Uçtaki `;;`, kod tamamlandığında FSI 'in bilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="38f9e-144">The `;;` at the end lets FSI know when the code is finished.</span></span>

## <a name="explaining-the-code"></a><span data-ttu-id="38f9e-145">Kodu açıklayan</span><span class="sxs-lookup"><span data-stu-id="38f9e-145">Explaining the code</span></span>

<span data-ttu-id="38f9e-146">Kodun gerçekten yapmakta olduğu konusunda emin değilseniz, bir adım adım aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="38f9e-146">If you're not sure about what the code is actually doing, here's a step-by-step.</span></span>

<span data-ttu-id="38f9e-147">Gördüğünüz gibi `toPigLatin`, bir sözcüğü giriş olarak alan ve bu sözcüğün Pig-Latin gösterimine dönüştüren bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="38f9e-147">As you can see, `toPigLatin` is a function that takes a word as its input and converts it to a Pig-Latin representation of that word.</span></span> <span data-ttu-id="38f9e-148">Bunun kuralları aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="38f9e-148">The rules for this are as follows:</span></span>

<span data-ttu-id="38f9e-149">Bir sözcükteki ilk karakter sesli harf ile başlıyorsa, sözcüğün sonuna "oley" ekleyin.</span><span class="sxs-lookup"><span data-stu-id="38f9e-149">If the first character in a word starts with a vowel, add "yay" to the end of the word.</span></span> <span data-ttu-id="38f9e-150">Bir sesli harf ile başlamazsa, ilk karakteri sözcüğün sonuna taşıyın ve buna "ay" ekleyin.</span><span class="sxs-lookup"><span data-stu-id="38f9e-150">If it doesn't start with a vowel, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="38f9e-151">FSI içinde aşağıdakileri fark etmiş olabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="38f9e-151">You may have noticed the following in FSI:</span></span>

```fsharp
val toPigLatin : word:string -> string
```

<span data-ttu-id="38f9e-152">Bu `toPigLatin`, giriş olarak bir `string` alan (`word`olarak adlandırılan) ve başka bir `string`döndüren bir işlev olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="38f9e-152">This states that `toPigLatin` is a function that takes in a `string` as input (called `word`), and returns another `string`.</span></span> <span data-ttu-id="38f9e-153">Bu, kodu anlamak F# F# için temel bir parçası olan [işlevin tür imzası](https://fsharpforfunandprofit.com/posts/function-signatures/)olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="38f9e-153">This is known as the [type signature of the function](https://fsharpforfunandprofit.com/posts/function-signatures/), a fundamental piece of F# that's key to understanding F# code.</span></span> <span data-ttu-id="38f9e-154">Ayrıca, Visual Studio Code işlevin üzerine geldiğinizde bunu da fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="38f9e-154">You'll also notice this if you hover over the function in Visual Studio Code.</span></span>

<span data-ttu-id="38f9e-155">İşlevin gövdesinde, iki ayrı bölüm fark edeceksiniz:</span><span class="sxs-lookup"><span data-stu-id="38f9e-155">In the body of the function, you'll notice two distinct parts:</span></span>

1. <span data-ttu-id="38f9e-156">Verilen bir karakterin (`c`), [desen eşleştirme](../language-reference/pattern-matching.md)aracılığıyla sağlanan desenlerden biriyle eşleşip eşleşmediğini denetleyerek, `isVowel`adlı bir iç işlev.</span><span class="sxs-lookup"><span data-stu-id="38f9e-156">An inner function, called `isVowel`, that determines if a given character (`c`) is a vowel by checking if it matches one of the provided patterns via [Pattern Matching](../language-reference/pattern-matching.md):</span></span>

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. <span data-ttu-id="38f9e-157">İlk karakterin bir sesli harf olup olmadığını denetleyen ve ilk karakterin bir sesli harf mi olduğunu ve giriş karakterlerinden bir dönüş değeri mi olduğunu kontrol eden bir [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) ifadesi:</span><span class="sxs-lookup"><span data-stu-id="38f9e-157">An [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expression that checks if the first character is a vowel, and constructs a return value out of the input characters based on if the first character was a vowel or not:</span></span>

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

<span data-ttu-id="38f9e-158">`toPigLatin` akışı bu nedenle:</span><span class="sxs-lookup"><span data-stu-id="38f9e-158">The flow of `toPigLatin` is thus:</span></span>

<span data-ttu-id="38f9e-159">Giriş sözcüğünün ilk karakterinin sesli harf olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="38f9e-159">Check if the first character of the input word is a vowel.</span></span> <span data-ttu-id="38f9e-160">Varsa, sözcüğün sonuna "oley" ekleyin.</span><span class="sxs-lookup"><span data-stu-id="38f9e-160">If it is, attach "yay" to the end of the word.</span></span> <span data-ttu-id="38f9e-161">Aksi takdirde, ilk karakteri sözcüğün sonuna taşıyın ve buna "ay" ekleyin.</span><span class="sxs-lookup"><span data-stu-id="38f9e-161">Otherwise, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="38f9e-162">Bunun hakkında dikkat edilecek bir son şey vardır: başka birçok dilin aksine, işlevden döndürülecek açık yönerge yoktur.</span><span class="sxs-lookup"><span data-stu-id="38f9e-162">There's one final thing to notice about this: there's no explicit instruction to return from the function, unlike many other languages out there.</span></span> <span data-ttu-id="38f9e-163">Bunun nedeni F# , ifade tabanlıdır ve bir işlevin gövdesindeki son ifade dönüş değeridir.</span><span class="sxs-lookup"><span data-stu-id="38f9e-163">This is because F# is Expression-based, and the last expression in the body of a function is the return value.</span></span> <span data-ttu-id="38f9e-164">`if..then..else` kendisinin bir ifadesi olduğundan, giriş değerine bağlı olarak, `then` bloğunun veya `else` bloğunun gövdesi döndürülür.</span><span class="sxs-lookup"><span data-stu-id="38f9e-164">Because `if..then..else` is itself an expression, the body of the `then` block or the body of the `else` block will be returned depending on the input value.</span></span>

## <a name="turn-the-console-app-into-a-pig-latin-generator"></a><span data-ttu-id="38f9e-165">Konsol uygulamasını bir Pig Latin oluşturucusuna dönüştürme</span><span class="sxs-lookup"><span data-stu-id="38f9e-165">Turn the console app into a Pig Latin generator</span></span>

<span data-ttu-id="38f9e-166">Bu makalenin önceki bölümlerinde kod yazmanın F# yaygın bir ilk adımı gösterilmiştir: ilk işlev YAZıLıYOR ve FSI ile etkileşimli olarak yürütülüyor.</span><span class="sxs-lookup"><span data-stu-id="38f9e-166">The previous sections in this article demonstrated a common first step in writing F# code: writing an initial function and executing it interactively with FSI.</span></span> <span data-ttu-id="38f9e-167">Bu, [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) 'un "Read-değerlendir-PRINT loop" IÇIN aldığı REPL temelli geliştirme olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="38f9e-167">This is known as REPL-driven development, where [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) stands for "Read-Evaluate-Print Loop".</span></span> <span data-ttu-id="38f9e-168">Çalışır hale gelene kadar işlevselliği denemek için harika bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="38f9e-168">It's a great way to experiment with functionality until you have something working.</span></span>

<span data-ttu-id="38f9e-169">REPL temelli geliştirmede bir sonraki adım, çalışma kodunu bir F# uygulama dosyasına taşımadır.</span><span class="sxs-lookup"><span data-stu-id="38f9e-169">The next step in REPL-driven development is to move working code into an F# implementation file.</span></span> <span data-ttu-id="38f9e-170">Daha sonra, bu, F# derleyici tarafından yürütülebilecek bir derlemeye derlenebilir.</span><span class="sxs-lookup"><span data-stu-id="38f9e-170">It can then be compiled by the F# compiler into an assembly that can be executed.</span></span>

<span data-ttu-id="38f9e-171">Başlamak için, daha önce .NET Core CLI oluşturduğunuz *program. FS* dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="38f9e-171">To begin, open the *Program.fs* file that you created earlier with the .NET Core CLI.</span></span> <span data-ttu-id="38f9e-172">Bazı kodların zaten orada olduğunu fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="38f9e-172">You'll notice that some code is already in there.</span></span>

<span data-ttu-id="38f9e-173">Sonra, `PigLatin` adlı yeni bir [`module`](../language-reference/modules.md) oluşturun ve daha önce oluşturduğunuz `toPigLatin` işlevini buna benzer şekilde kopyalayın:</span><span class="sxs-lookup"><span data-stu-id="38f9e-173">Next, create a new [`module`](../language-reference/modules.md) called `PigLatin` and copy the `toPigLatin` function you created earlier into it as such:</span></span>

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/pig-latin.fs#L3-L14)]

<span data-ttu-id="38f9e-174">Bu modül `main` işlevin üzerinde ve `open System` bildiriminin altında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="38f9e-174">This module should be above the `main` function and below the `open System` declaration.</span></span> <span data-ttu-id="38f9e-175">' Deki F#bildirimlerin sırası, bu nedenle, bir dosyaya çağrı yapmadan önce işlevi tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="38f9e-175">Order of declarations matters in F#, so you'll need to define the function before you call it in a file.</span></span>

<span data-ttu-id="38f9e-176">Şimdi `main` işlevinde, Pig Latin Oluşturucu işlevinizi bağımsız değişkenlerde çağırın:</span><span class="sxs-lookup"><span data-stu-id="38f9e-176">Now, in the `main` function, call your Pig Latin generator function on the arguments:</span></span>

```fsharp
[<EntryPoint>]
let main argv =
    for name in argv do
        let newName = PigLatin.toPigLatin name
        printfn "%s in Pig Latin is: %s" name newName

    0
```

<span data-ttu-id="38f9e-177">Şimdi, konsol uygulamanızı komut satırından çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="38f9e-177">Now you can run your console app from the command line:</span></span>

```dotnetcli
dotnet run apple banana
```

<span data-ttu-id="38f9e-178">Ayrıca, bu kez çalışan bir program olarak, betik dosyanız ile aynı sonucu verir.</span><span class="sxs-lookup"><span data-stu-id="38f9e-178">And you'll see that it outputs the same result as your script file, but this time as a running program!</span></span>

## <a name="troubleshooting-ionide"></a><span data-ttu-id="38f9e-179">Ionıde sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="38f9e-179">Troubleshooting Ionide</span></span>

<span data-ttu-id="38f9e-180">İşte karşılaşabileceğiniz bazı sorunları giderebilmeniz için birkaç yol aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="38f9e-180">Here are a few ways you can troubleshoot certain problems that you might run into:</span></span>

1. <span data-ttu-id="38f9e-181">Ionıde 'nin kod düzenlemesi özelliklerini almak için F# dosyalarınızın diske ve Visual Studio Code çalışma alanında açık olan bir klasörün içine kaydedilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="38f9e-181">To get the code editing features of Ionide, your F# files need to be saved to disk and inside of a folder that is open in the Visual Studio Code workspace.</span></span>
1. <span data-ttu-id="38f9e-182">Sisteminizde değişiklik yaptıysanız veya Visual Studio Code açık olarak ıonıde önkoşulları yüklediyseniz Visual Studio Code yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="38f9e-182">If you've made changes to your system or installed Ionide prerequisites with Visual Studio Code open, restart Visual Studio Code.</span></span>
1. <span data-ttu-id="38f9e-183">Proje dizinlerinizde geçersiz karakterler varsa, ıonıde çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="38f9e-183">If you have invalid characters in your project directories, Ionide might not work.</span></span>  <span data-ttu-id="38f9e-184">Bu durumda proje dizinlerinizi yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="38f9e-184">Rename your project directories if this is the case.</span></span>
1. <span data-ttu-id="38f9e-185">Ionıde komutlarının hiçbiri çalışmıyorsa, yanlışlıkla geçersiz kıldığınızı görmek için [Visual Studio Code anahtar bağlamalarınızı](https://code.visualstudio.com/docs/getstarted/keybindings#_advanced-customization) denetleyin.</span><span class="sxs-lookup"><span data-stu-id="38f9e-185">If none of the Ionide commands are working, check your [Visual Studio Code Key Bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_advanced-customization) to see if you're overriding them by accident.</span></span>
1. <span data-ttu-id="38f9e-186">Ionıde makinenizde bozulur ve yukarıdakilerden hiçbiri sorununuzu düzeltmediyse, makinenizde `ionide-fsharp` dizinini kaldırmayı ve eklenti paketini yeniden yüklemeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="38f9e-186">If Ionide is broken on your machine and none of the above has fixed your problem, try removing the `ionide-fsharp` directory on your machine and reinstall the plugin suite.</span></span>
1. <span data-ttu-id="38f9e-187">Bir proje yükleme başarısız olursa ( F# Çözüm Gezgini bunu gösterir), bu projeye sağ tıklayıp **Ayrıntıları gör** ' e tıklayarak daha fazla tanılama bilgisi alın.</span><span class="sxs-lookup"><span data-stu-id="38f9e-187">If a project failed to load (the F# Solution Explorer will show this), right-click on that project and click **See details** to get more diagnostic info.</span></span>

<span data-ttu-id="38f9e-188">Ionıde, F# topluluk üyeleri tarafından oluşturulan ve tutulan açık kaynaklı bir projem.</span><span class="sxs-lookup"><span data-stu-id="38f9e-188">Ionide is an open source project built and maintained by members of the F# community.</span></span> <span data-ttu-id="38f9e-189">Lütfen sorunları bildirin ve [ıonıde-vscode-FSharp GitHub deposunda](https://github.com/ionide/ionide-vscode-fsharp)katkıda bulunun.</span><span class="sxs-lookup"><span data-stu-id="38f9e-189">Please report issues and feel free to contribute at the [ionide-vscode-fsharp GitHub repository](https://github.com/ionide/ionide-vscode-fsharp).</span></span>

<span data-ttu-id="38f9e-190">Ayrıca, ıonıde F# [Gitter kanalında](https://gitter.im/ionide/ionide-project)ıonıde geliştiricilerinden ve topluluğundan daha fazla yardım isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38f9e-190">You can also ask for further help from the Ionide developers and F# community in the [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span></span>

## <a name="next-steps"></a><span data-ttu-id="38f9e-191">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="38f9e-191">Next steps</span></span>

<span data-ttu-id="38f9e-192">Ve dilinin özellikleri hakkında F# daha fazla bilgi edinmek Için, [turuna F# ](../tour.md)göz atın.</span><span class="sxs-lookup"><span data-stu-id="38f9e-192">To learn more about F# and the features of the language, check out [Tour of F#](../tour.md).</span></span>
