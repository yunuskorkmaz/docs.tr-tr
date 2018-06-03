---
title: 'F # Visual Studio Code ile çalışmaya başlama'
description: 'F # Visual Studio Code ve Ionide eklentisi paketiyle nasıl kullanacağınızı öğrenin.'
ms.date: 05/28/2018
ms.openlocfilehash: e56274caf36be231338876ded5a6d7c7968906b0
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2018
ms.locfileid: "34728634"
---
# <a name="get-started-with-f-in-visual-studio-code"></a><span data-ttu-id="127ff-103">F # Visual Studio Code ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="127ff-103">Get Started with F# in Visual Studio Code</span></span>

<span data-ttu-id="127ff-104">F # yazabileceğiniz [Visual Studio Code](https://code.visualstudio.com) ile [Ionide eklentisi](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp), IntelliSense ve temel kodla harika bir çapraz platform, basit tümleşik geliştirme ortamı (IDE) deneyim almak için yapan yeniden düzenlemeler.</span><span class="sxs-lookup"><span data-stu-id="127ff-104">You can write F# in [Visual Studio Code](https://code.visualstudio.com) with the [Ionide plugin](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp), to get a great cross-platform, lightweight Integrated Development Environment (IDE) experience with IntelliSense and basic code refactorings.</span></span> <span data-ttu-id="127ff-105">Ziyaret [Ionide.io](http://ionide.io) eklentisi paketi hakkında daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="127ff-105">Visit [Ionide.io](http://ionide.io) to learn more about the plugin suite.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="127ff-106">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="127ff-106">Prerequisites</span></span>

<span data-ttu-id="127ff-107">Sahip olmanız gerekir [yüklü git](https://git-scm.com/download) ve kullanılabilir yapmak için yolunda Ionide proje şablonlarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="127ff-107">You must have [git installed](https://git-scm.com/download) and available on your PATH to make use of project templates in Ionide.</span></span> <span data-ttu-id="127ff-108">Bunu doğru şekilde yazarak yüklendiğini doğrulayabilirsiniz `git --version` bir komut istemi ve tuşlarına basarak **Enter**.</span><span class="sxs-lookup"><span data-stu-id="127ff-108">You can verify that it is installed correctly by typing `git --version` at a command prompt and pressing **Enter**.</span></span>

### <a name="macostabmacos"></a>[<span data-ttu-id="127ff-109">macOS</span><span class="sxs-lookup"><span data-stu-id="127ff-109">macOS</span></span>](#tab/macos)

<span data-ttu-id="127ff-110">Ionide kullanan [Mono](http://www.mono-project.com).</span><span class="sxs-lookup"><span data-stu-id="127ff-110">Ionide uses [Mono](http://www.mono-project.com).</span></span> <span data-ttu-id="127ff-111">Homebrew üzerinde macOS Mono yüklemek için en kolay yoludur.</span><span class="sxs-lookup"><span data-stu-id="127ff-111">The easiest way to install Mono on macOS is via Homebrew.</span></span> <span data-ttu-id="127ff-112">Terminalinizde yalnızca aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="127ff-112">Simply type the following into your terminal:</span></span>

```
brew install mono
```

<span data-ttu-id="127ff-113">Ayrıca yüklemelisiniz [.NET Core SDK](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="127ff-113">You must also install the [.NET Core SDK](https://www.microsoft.com/net/download).</span></span>

### <a name="linuxtablinux"></a>[<span data-ttu-id="127ff-114">Linux</span><span class="sxs-lookup"><span data-stu-id="127ff-114">Linux</span></span>](#tab/linux)

<span data-ttu-id="127ff-115">Linux üzerinde Ionide de kullanır [Mono](https://www.mono-project.com).</span><span class="sxs-lookup"><span data-stu-id="127ff-115">On Linux, Ionide also uses [Mono](https://www.mono-project.com).</span></span> <span data-ttu-id="127ff-116">Debian veya Ubuntu değilseniz, aşağıdakileri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="127ff-116">If you're on Debian or Ubuntu, you can use the following:</span></span>

```
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

<span data-ttu-id="127ff-117">Ayrıca yüklemelisiniz [.NET Core SDK](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="127ff-117">You must also install the [.NET Core SDK](https://www.microsoft.com/net/download).</span></span>

### <a name="windowstabwindows"></a>[<span data-ttu-id="127ff-118">Windows</span><span class="sxs-lookup"><span data-stu-id="127ff-118">Windows</span></span>](#tab/windows)

<span data-ttu-id="127ff-119">Windows üzerinde değilseniz, şunları yapmalısınız [F # desteği ile Visual Studio yükleme](get-started-visual-studio.md#installing-f).</span><span class="sxs-lookup"><span data-stu-id="127ff-119">If you're on Windows, you must [install Visual Studio with F# support](get-started-visual-studio.md#installing-f).</span></span> <span data-ttu-id="127ff-120">Bu, yazma, derlemek ve F # kod yürütmek için gerekli tüm bileşenleri yükler.</span><span class="sxs-lookup"><span data-stu-id="127ff-120">This installs all the necessary components to write, compile, and execute F# code.</span></span>

<span data-ttu-id="127ff-121">Ayrıca yüklemelisiniz [.NET Core SDK](https://www.microsoft.com/net/download/).</span><span class="sxs-lookup"><span data-stu-id="127ff-121">You must also install the [.NET Core SDK](https://www.microsoft.com/net/download/).</span></span>

---

## <a name="installing-visual-studio-code-and-the-ionide-plugin"></a><span data-ttu-id="127ff-122">Visual Studio Code ve Ionide eklentisini yükleme</span><span class="sxs-lookup"><span data-stu-id="127ff-122">Installing Visual Studio Code and the Ionide plugin</span></span>

<span data-ttu-id="127ff-123">Visual Studio koddan yükleyebilirsiniz [code.visualstudio.com](https://code.visualstudio.com) Web sitesi.</span><span class="sxs-lookup"><span data-stu-id="127ff-123">You can install Visual Studio Code from the [code.visualstudio.com](https://code.visualstudio.com) website.</span></span>

<span data-ttu-id="127ff-124">Ardından, "Ionide" için arama ve uzantıları simgesini tıklatın:</span><span class="sxs-lookup"><span data-stu-id="127ff-124">Next, click the Extensions icon and search for "Ionide":</span></span>

<span data-ttu-id="127ff-125">F # Visual Studio Code desteklenmediği için gereken tek eklentisi [Ionide fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span><span class="sxs-lookup"><span data-stu-id="127ff-125">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span> <span data-ttu-id="127ff-126">Ancak, aynı zamanda yükleyebilirsiniz [Ionide sahte](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) almak için [sahte](https://fsharp.github.io/FAKE/) desteklemek ve [Ionide Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) almak için [Paket](https://fsprojects.github.io/Paket/) destekler.</span><span class="sxs-lookup"><span data-stu-id="127ff-126">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) to get [FAKE](https://fsharp.github.io/FAKE/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span> <span data-ttu-id="127ff-127">SAHTE ve Paket projeleri oluşturmak ve bağımlılıkları, sırasıyla yönetmek için ek F # topluluk araçları.</span><span class="sxs-lookup"><span data-stu-id="127ff-127">FAKE and Paket are additional F# community tools for building projects and managing dependencies, respectively.</span></span>

## <a name="creating-your-first-project-with-ionide"></a><span data-ttu-id="127ff-128">Ionide ile ilk projenizi oluşturma</span><span class="sxs-lookup"><span data-stu-id="127ff-128">Creating your first project with Ionide</span></span>

<span data-ttu-id="127ff-129">Yeni bir F # projesi oluşturmak için Visual Studio Code yeni bir klasöre (örneğin, istediğiniz adı verebilirsiniz) açın.</span><span class="sxs-lookup"><span data-stu-id="127ff-129">To create a new F# project, open Visual Studio Code in a new folder (you can name it whatever you like).</span></span>

<span data-ttu-id="127ff-130">Ardından, komut paletinden açın (**Görünüm > komutu paletinden**) ve aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="127ff-130">Next, open the command pallette (**View > Command Pallette**) and type the following:</span></span>

```
> F# new project
```

<span data-ttu-id="127ff-131">Bu tarafından desteklenmektedir [FORGE](https://github.com/fsharp-editing/Forge) projesi.</span><span class="sxs-lookup"><span data-stu-id="127ff-131">This is powered by the [FORGE](https://github.com/fsharp-editing/Forge) project.</span></span>

> [!NOTE]
<span data-ttu-id="127ff-132">Şablon seçenekleri görmüyorsanız, komut Palette aşağıdaki komutu çalıştırarak şablonları yenilemeyi deneyin: `>F#: Refresh Project Templates`.</span><span class="sxs-lookup"><span data-stu-id="127ff-132">If you don't see template options, try refreshing templates by running the following command in the Command Palette: `>F#: Refresh Project Templates`.</span></span>

<span data-ttu-id="127ff-133">"F #: Yeni Proje" basarsa tarafından seçin **Enter**.</span><span class="sxs-lookup"><span data-stu-id="127ff-133">Select "F#: New Project" by hitting **Enter**.</span></span> <span data-ttu-id="127ff-134">Bu, bir proje şablonu seçmek için olan bir sonraki adıma götürür.</span><span class="sxs-lookup"><span data-stu-id="127ff-134">This takes you to the next step, which is for selecting a project template.</span></span>

<span data-ttu-id="127ff-135">Çekme `classlib` şablonu ve isabet **Enter**.</span><span class="sxs-lookup"><span data-stu-id="127ff-135">Pick the `classlib` template and hit **Enter**.</span></span>

<span data-ttu-id="127ff-136">Ardından, projeyi oluşturmak için bir dizin seçin.</span><span class="sxs-lookup"><span data-stu-id="127ff-136">Next, pick a directory to create the project in.</span></span> <span data-ttu-id="127ff-137">Boş bırakırsanız, geçerli dizin kullanır.</span><span class="sxs-lookup"><span data-stu-id="127ff-137">If you leave it blank, it uses the current directory.</span></span>

<span data-ttu-id="127ff-138">Son olarak, son adım projenizde adı.</span><span class="sxs-lookup"><span data-stu-id="127ff-138">Finally, name your project in the final step.</span></span> <span data-ttu-id="127ff-139">F # kullanan [Pascal durumda](http://c2.com/cgi/wiki?PascalCase) proje adları için.</span><span class="sxs-lookup"><span data-stu-id="127ff-139">F# uses [Pascal case](http://c2.com/cgi/wiki?PascalCase) for project names.</span></span> <span data-ttu-id="127ff-140">Bu makalede kullanan `ClassLibraryDemo` adı.</span><span class="sxs-lookup"><span data-stu-id="127ff-140">This article uses `ClassLibraryDemo` as the name.</span></span> <span data-ttu-id="127ff-141">Projeniz için istediğiniz adı girdikten sonra isabet **Enter**.</span><span class="sxs-lookup"><span data-stu-id="127ff-141">Once you've entered the name you want for your project, hit **Enter**.</span></span>

<span data-ttu-id="127ff-142">Önceki adımda izlediyseniz, Visual Studio kodu aşağıdakilerle görünmesi çalışma alanında sol taraftaki almanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="127ff-142">If you followed the previous step, you should get the Visual Studio Code Workspace on the left-hand side to appear with the following:</span></span>

1. <span data-ttu-id="127ff-143">F # proje kendisini altındaki `ClassLibraryDemo` klasörü.</span><span class="sxs-lookup"><span data-stu-id="127ff-143">The F# project itself, underneath the `ClassLibraryDemo` folder.</span></span>
2. <span data-ttu-id="127ff-144">Paketleri yoluyla eklemek için doğru dizin yapısını [ `Paket` ](https://fsprojects.github.io/Paket/).</span><span class="sxs-lookup"><span data-stu-id="127ff-144">The correct directory structure for adding packages via [`Paket`](https://fsprojects.github.io/Paket/).</span></span>
3. <span data-ttu-id="127ff-145">Çapraz platform komut dosyasıyla yapı [ `FAKE` ](https://fsharp.github.io/FAKE/).</span><span class="sxs-lookup"><span data-stu-id="127ff-145">A cross-platform build script with [`FAKE`](https://fsharp.github.io/FAKE/).</span></span>
4. <span data-ttu-id="127ff-146">`paket.exe` Fetch paketleri ve sizin için bağımlılıklar çözümlenmeye çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="127ff-146">The `paket.exe` executable that can fetch packages and resolve dependencies for you.</span></span>
5. <span data-ttu-id="127ff-147">A `.gitignore` bu proje Git tabanlı bir kaynak denetimine eklemek isterseniz, dosya.</span><span class="sxs-lookup"><span data-stu-id="127ff-147">A `.gitignore` file if you wish to add this project to Git-based source control.</span></span>

## <a name="writing-some-code"></a><span data-ttu-id="127ff-148">Bazı kod yazma</span><span class="sxs-lookup"><span data-stu-id="127ff-148">Writing some code</span></span>

<span data-ttu-id="127ff-149">Açık *ClassLibraryDemo* klasör.</span><span class="sxs-lookup"><span data-stu-id="127ff-149">Open the *ClassLibraryDemo* folder.</span></span>  <span data-ttu-id="127ff-150">Aşağıdaki dosyalar görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="127ff-150">You should see the following files:</span></span>

1. <span data-ttu-id="127ff-151">`ClassLibraryDemo.fs`, F # uygulaması olan bir dosya tanımlı bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="127ff-151">`ClassLibraryDemo.fs`, an F# implementation file with a class defined.</span></span>
2. <span data-ttu-id="127ff-152">`ClassLibraryDemo.fsproj`, bu proje oluşturmak için kullanılan bir F # proje dosyası.</span><span class="sxs-lookup"><span data-stu-id="127ff-152">`ClassLibraryDemo.fsproj`, an F# project file used to build this project.</span></span>
3. <span data-ttu-id="127ff-153">`Script.fsx`, kaynak dosya yükleyen bir F # komut dosyası.</span><span class="sxs-lookup"><span data-stu-id="127ff-153">`Script.fsx`, an F# script file that loads the source file.</span></span>
4. <span data-ttu-id="127ff-154">`paket.references`, proje bağımlılıklarını belirten bir Paket dosyası.</span><span class="sxs-lookup"><span data-stu-id="127ff-154">`paket.references`, a Paket file that specifies the project dependencies.</span></span>

<span data-ttu-id="127ff-155">Açık `Script.fsx`ve sonunda, aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="127ff-155">Open `Script.fsx`, and add the following code at the end of it:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

<span data-ttu-id="127ff-156">Bu işlev bir sözcük bir forma dönüştürür [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span><span class="sxs-lookup"><span data-stu-id="127ff-156">This function converts a word to a form of [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span></span> <span data-ttu-id="127ff-157">F # Etkileşimli (FSI) kullanarak değerlendirmek için sonraki adımda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="127ff-157">The next step is to evaluate it using F# Interactive (FSI).</span></span>

<span data-ttu-id="127ff-158">(11 satır uzunluğundaki olmalıdır) tüm işlevi vurgulayın.</span><span class="sxs-lookup"><span data-stu-id="127ff-158">Highlight the entire function (it should be 11 lines long).</span></span> <span data-ttu-id="127ff-159">Vurgulanır sonra tutun **Alt** anahtarı ve isabet **Enter**.</span><span class="sxs-lookup"><span data-stu-id="127ff-159">Once it is highlighted, hold the **Alt** key and hit **Enter**.</span></span> <span data-ttu-id="127ff-160">Aşağıdaki açılır pencere görürsünüz ve şöyle bir şey göstermesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="127ff-160">You'll notice a window pop up below, and it should show something like this:</span></span>

![F # Etkileşimli çıktı Ionide ile örneği](media/getting-started-vscode/vscode-fsi.png)

<span data-ttu-id="127ff-162">Üçünü yapar:</span><span class="sxs-lookup"><span data-stu-id="127ff-162">This did three things:</span></span>

1. <span data-ttu-id="127ff-163">FSI işlemi başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="127ff-163">It started the FSI process.</span></span>
2. <span data-ttu-id="127ff-164">Bu vurguladığınız kodun FSI işlemi gönderilir.</span><span class="sxs-lookup"><span data-stu-id="127ff-164">It sent the code you highlighted over the FSI process.</span></span>
3. <span data-ttu-id="127ff-165">FSI işlemi üzerinden gönderilen kodu değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="127ff-165">The FSI process evaluated the code you sent over.</span></span>

<span data-ttu-id="127ff-166">Üzerinden gönderilen olduğundan bir [işlevi](../language-reference/functions/index.md), o FSI işleviyle çağırabilirsiniz!</span><span class="sxs-lookup"><span data-stu-id="127ff-166">Because what you sent over was a [function](../language-reference/functions/index.md), you can now call that function with FSI!</span></span> <span data-ttu-id="127ff-167">Etkileşimli penceresinde aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="127ff-167">In the interactive window, type the following:</span></span>

```fsharp
toPigLatin "banana";;
```

<span data-ttu-id="127ff-168">Aşağıdaki sonucu görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="127ff-168">You should see the following result:</span></span>

```fsharp
val it : string = "ananabay"
```

<span data-ttu-id="127ff-169">Şimdi, ilk harfi olarak sesli bir ile deneyelim.</span><span class="sxs-lookup"><span data-stu-id="127ff-169">Now, let's try with a vowel as the first letter.</span></span> <span data-ttu-id="127ff-170">Aşağıdakileri girin:</span><span class="sxs-lookup"><span data-stu-id="127ff-170">Enter the following:</span></span>

```fsharp
toPigLatin "apple";;
```

<span data-ttu-id="127ff-171">Aşağıdaki sonucu görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="127ff-171">You should see the following result:</span></span>

```fsharp
val it : string = "appleyay"
```

<span data-ttu-id="127ff-172">İşlev beklendiği gibi çalıştığını görünüyor.</span><span class="sxs-lookup"><span data-stu-id="127ff-172">The function appears to be working as expected.</span></span> <span data-ttu-id="127ff-173">Tebrikler, yalnızca Visual Studio kodda ilk F # işlevinizi yazdı ve FSI ile değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="127ff-173">Congratulations, you just wrote your first F# function in Visual Studio Code and evaluated it with FSI!</span></span>

>[!NOTE]
<span data-ttu-id="127ff-174">Fark etmiş olabilirsiniz gibi FSI satırları ile sona erdirilir `;;`.</span><span class="sxs-lookup"><span data-stu-id="127ff-174">As you may have noticed, the lines in FSI are terminated with `;;`.</span></span> <span data-ttu-id="127ff-175">FSI birden fazla satır girmenizi sağlayan olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="127ff-175">This is because FSI allows you to enter multiple lines.</span></span> <span data-ttu-id="127ff-176">`;;` Sonunda kodu bittiği bilmeniz FSI olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="127ff-176">The `;;` at the end lets FSI know when the code is finished.</span></span>

## <a name="explaining-the-code"></a><span data-ttu-id="127ff-177">Kod açıklayan</span><span class="sxs-lookup"><span data-stu-id="127ff-177">Explaining the code</span></span>

<span data-ttu-id="127ff-178">Kod gerçekte yaptıklarını hakkında emin değilseniz, işte bir adım adım.</span><span class="sxs-lookup"><span data-stu-id="127ff-178">If you're not sure about what the code is actually doing, here's a step-by-step.</span></span>

<span data-ttu-id="127ff-179">Gördüğünüz gibi `toPigLatin` bir sözcük, girdi olarak alır ve bu word'ün bir Pig Latin gösterimine dönüştürür bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="127ff-179">As you can see, `toPigLatin` is a function that takes a word as its input and converts it to a Pig-Latin representation of that word.</span></span> <span data-ttu-id="127ff-180">Bu kurallar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="127ff-180">The rules for this are as follows:</span></span>

<span data-ttu-id="127ff-181">İlk karakter bir sözcük, sesli bir harfle başlarsa, "yay" sözcüğü sonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="127ff-181">If the first character in a word starts with a vowel, add "yay" to the end of the word.</span></span> <span data-ttu-id="127ff-182">Sesli bir harfle başlamazsa, bu ilk karakteri sözcüğün sonuna taşıyın ve "ay" ekleyin.</span><span class="sxs-lookup"><span data-stu-id="127ff-182">If it doesn't start with a vowel, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="127ff-183">FSI aşağıdakileri fark etmiş olabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="127ff-183">You may have noticed the following in FSI:</span></span>

```fsharp
val toPigLatin : word:string -> string
```

<span data-ttu-id="127ff-184">Bu bildiren `toPigLatin` alır, bir işlev değil bir `string` giriş olarak (adlı `word`) ve başka döndürür `string`.</span><span class="sxs-lookup"><span data-stu-id="127ff-184">This states that `toPigLatin` is a function that takes in a `string` as input (called `word`), and returns another `string`.</span></span> <span data-ttu-id="127ff-185">Bu olarak bilinir [işlevinin türü imzası](https://fsharpforfunandprofit.com/posts/function-signatures/), temel bir F #'ın, F # kodunu anlamanın anahtarıdır.</span><span class="sxs-lookup"><span data-stu-id="127ff-185">This is known as the [type signature of the function](https://fsharpforfunandprofit.com/posts/function-signatures/), a fundamental piece of F# that's key to understanding F# code.</span></span> <span data-ttu-id="127ff-186">Visual Studio Code işlevinde üzerine getirirseniz de bu fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="127ff-186">You'll also notice this if you hover over the function in Visual Studio Code.</span></span>

<span data-ttu-id="127ff-187">İşlev gövdesine iki ayrı bölümlere görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="127ff-187">In the body of the function, you'll notice two distinct parts:</span></span>

1. <span data-ttu-id="127ff-188">Adlı bir iç işlevi `isVowel`, belirli bir karakter varsa belirler (`c`) sağlanan desenleri biriyle eşleşiyorsa denetleyerek bir sesli olup [desen eşleştirme](../language-reference/pattern-matching.md):</span><span class="sxs-lookup"><span data-stu-id="127ff-188">An inner function, called `isVowel`, that determines if a given character (`c`) is a vowel by checking if it matches one of the provided patterns via [Pattern Matching](../language-reference/pattern-matching.md):</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. <span data-ttu-id="127ff-189">Bir [ `if..then..else` ](../language-reference/conditional-expressions-if-then-else.md) ilk karakteri bir sesli bir dönüş değeri dışında giriş karakter yapıları ise ilk karakter tabanlı olmadığını denetler ve ifadesi veya bir sesli oluştu:</span><span class="sxs-lookup"><span data-stu-id="127ff-189">An [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expression that checks if the first character is a vowel, and constructs a return value out of the input characters based on if the first character was a vowel or not:</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

<span data-ttu-id="127ff-190">Akışını `toPigLatin` böylece:</span><span class="sxs-lookup"><span data-stu-id="127ff-190">The flow of `toPigLatin` is thus:</span></span>

<span data-ttu-id="127ff-191">Giriş word ilk karakteri bir sesli olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="127ff-191">Check if the first character of the input word is a vowel.</span></span> <span data-ttu-id="127ff-192">Bu durumda, "yay" sözcüğün sonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="127ff-192">If it is, attach "yay" to the end of the word.</span></span> <span data-ttu-id="127ff-193">Aksi takdirde, bu ilk karakteri sözcüğün sonuna taşıyın ve "ay" ekleyin.</span><span class="sxs-lookup"><span data-stu-id="127ff-193">Otherwise, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="127ff-194">Bu konuda fark için son bir şey yok: birçok diğer diller ölçeklendiriyor aksine işlevi döndürmek için açık bir yönerge yoktur.</span><span class="sxs-lookup"><span data-stu-id="127ff-194">There's one final thing to notice about this: there's no explicit instruction to return from the function, unlike many other languages out there.</span></span> <span data-ttu-id="127ff-195">F # ifade tabanlı, ve bir işlev gövdesine son deyim dönüş değeri olduğundan budur.</span><span class="sxs-lookup"><span data-stu-id="127ff-195">This is because F# is Expression-based, and the last expression in the body of a function is the return value.</span></span> <span data-ttu-id="127ff-196">Çünkü `if..then..else` kendisi gövdesi bir ifade değildir `then` engelleme veya gövdesini `else` blok bağlı olarak giriş değeri döndürülecek.</span><span class="sxs-lookup"><span data-stu-id="127ff-196">Because `if..then..else` is itself an expression, the body of the `then` block or the body of the `else` block will be returned depending on the input value.</span></span>

## <a name="moving-your-script-code-into-the-implementation-file"></a><span data-ttu-id="127ff-197">Uygulama dosyasına betik kodunuzu taşıma</span><span class="sxs-lookup"><span data-stu-id="127ff-197">Moving your script code into the implementation file</span></span>

<span data-ttu-id="127ff-198">Bu makalede önceki bölümlerde gösterildiği F # kodu yazarken ortak bir ilk adım: bir başlangıç işlevi yazma ve etkileşimli olarak FSI ile çalıştırma.</span><span class="sxs-lookup"><span data-stu-id="127ff-198">The previous sections in this article demonstrated a common first step in writing F# code: writing an initial function and executing it interactively with FSI.</span></span> <span data-ttu-id="127ff-199">Bu REPL güdümlü geliştirme bilinir nerede [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) "Okuma değerlendirmek yazdırma döngü için" anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="127ff-199">This is known as REPL-driven development, where [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) stands for "Read-Evaluate-Print Loop".</span></span> <span data-ttu-id="127ff-200">Bir çalışma elde edene kadar işlevsellikle denemek için harika bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="127ff-200">It's a great way to experiment with functionality until you have something working.</span></span>

<span data-ttu-id="127ff-201">REPL güdümlü geliştirme sonraki adımda, bir F # uygulama dosyasına çalışan kodu taşımaktır.</span><span class="sxs-lookup"><span data-stu-id="127ff-201">The next step in REPL-driven development is to move working code into an F# implementation file.</span></span> <span data-ttu-id="127ff-202">Ardından yürütülebilir bir derlemeye F # derleyici tarafından olarak da derlenebilir.</span><span class="sxs-lookup"><span data-stu-id="127ff-202">It can then be compiled by the F# compiler into an assembly that can be executed.</span></span>

<span data-ttu-id="127ff-203">Başlamak için açın `ClassLibraryDemo.fs`.</span><span class="sxs-lookup"><span data-stu-id="127ff-203">To begin, open `ClassLibraryDemo.fs`.</span></span>  <span data-ttu-id="127ff-204">Bazı kodu zaten da olduğunu fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="127ff-204">You'll notice that some code is already in there.</span></span> <span data-ttu-id="127ff-205">Devam edin ve sınıf tanımını silin, ancak bıraktığınızdan emin olun [ `namespace` ](../language-reference/namespaces.md) bildiriminin en üstünde.</span><span class="sxs-lookup"><span data-stu-id="127ff-205">Go ahead and delete the class definition, but make sure to leave the [`namespace`](../language-reference/namespaces.md) declaration at the top.</span></span>

<span data-ttu-id="127ff-206">Ardından, yeni bir oluşturun [ `module` ](../language-reference/modules.md) adlı `PigLatin` ve kopyalama `toPigLatin` şekilde işlevi içine:</span><span class="sxs-lookup"><span data-stu-id="127ff-206">Next, create a new [`module`](../language-reference/modules.md) called `PigLatin` and copy the `toPigLatin` function into it as such:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

<span data-ttu-id="127ff-207">Ardından, açık `Script.fsx` dosyasını yeniden ve tüm silme `toPigLatin` çalışır, ancak aşağıdaki iki satırı dosyasında sakladığınızdan emin olun:</span><span class="sxs-lookup"><span data-stu-id="127ff-207">Next, open the `Script.fsx` file again, and delete the entire `toPigLatin` function, but make sure to keep the following two lines in the file:</span></span>

```fsharp
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

<span data-ttu-id="127ff-208">İlk satırı FSI yüklemek için komut dosyası için gereken `ClassLibraryDemo.fs`.</span><span class="sxs-lookup"><span data-stu-id="127ff-208">The first line is needed for FSI scripting to load `ClassLibraryDemo.fs`.</span></span> <span data-ttu-id="127ff-209">İkinci satır bir kolaylık bağlı: Bu atlama isteğe bağlıdır ancak yazmanız gerekir `open ClassLibraryDemo` getirmek isterseniz, bir FSI penceresinde `ToPigLatin` kapsam modüle.</span><span class="sxs-lookup"><span data-stu-id="127ff-209">The second line is a convenience: omitting it is optional, but you will need to type `open ClassLibraryDemo` in an FSI window if you wish to bring the `ToPigLatin` module into scope.</span></span>

<span data-ttu-id="127ff-210">Ardından, FSI penceresinde işlev çağrısı `PigLatin` daha önce tanımlanan Modülü:</span><span class="sxs-lookup"><span data-stu-id="127ff-210">Next, in the FSI window, call the function with the `PigLatin` module that you defined earlier:</span></span>

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

<span data-ttu-id="127ff-211">Başarılı!</span><span class="sxs-lookup"><span data-stu-id="127ff-211">Success!</span></span> <span data-ttu-id="127ff-212">Önce aynı sonuçları alırsınız, ancak bir F # uygulaması dosyasından şimdi yüklendi.</span><span class="sxs-lookup"><span data-stu-id="127ff-212">You get the same results as before, but now loaded from an F# implementation file.</span></span> <span data-ttu-id="127ff-213">Burada en önemli fark, F # kaynak dosyaları yalnızca FSI içinde herhangi bir yere, yürütülebilir derlemeler içine derlenen ' dir.</span><span class="sxs-lookup"><span data-stu-id="127ff-213">The major difference here is that F# source files are compiled into assemblies that can be executed anywhere, not just in FSI.</span></span>

## <a name="summary"></a><span data-ttu-id="127ff-214">Özet</span><span class="sxs-lookup"><span data-stu-id="127ff-214">Summary</span></span>

<span data-ttu-id="127ff-215">Bu makalede, öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="127ff-215">In this article, you've learned:</span></span>

1. <span data-ttu-id="127ff-216">Visual Studio kodu Ionide ile kurulur.</span><span class="sxs-lookup"><span data-stu-id="127ff-216">How to set up Visual Studio Code with Ionide.</span></span>
2. <span data-ttu-id="127ff-217">Ionide ile ilk F # projenizi oluşturma</span><span class="sxs-lookup"><span data-stu-id="127ff-217">How to create your first F# project with Ionide.</span></span>
3. <span data-ttu-id="127ff-218">F # komut dosyası yazma, ilk F # için nasıl kullanılacağını Ionide içinde işlev ve FSI içinde yürütün.</span><span class="sxs-lookup"><span data-stu-id="127ff-218">How to use F# Scripting to write your first F# function in Ionide and then execute it in FSI.</span></span>
4. <span data-ttu-id="127ff-219">Kodunuzu geçirmek nasıl F # kaynak kodu ve sonra bu kodu FSI çağırın.</span><span class="sxs-lookup"><span data-stu-id="127ff-219">How to migrate your script code to F# source and then call that code from FSI.</span></span>

<span data-ttu-id="127ff-220">Şimdi Visual Studio Code ile Ionide olan çok daha fazla F # kod yazmaya donatılmış.</span><span class="sxs-lookup"><span data-stu-id="127ff-220">You're now equipped to write much more F# code using Visual Studio Code and Ionide.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="127ff-221">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="127ff-221">Troubleshooting</span></span>

<span data-ttu-id="127ff-222">İçine çalışabilir belirli sorunları giderme birkaç şekilde şunlardır:</span><span class="sxs-lookup"><span data-stu-id="127ff-222">Here are a few ways you can troubleshoot certain problems that you might run into:</span></span>

1. <span data-ttu-id="127ff-223">Ionide özelliklerini düzenleme kod almak için F # dosyalarınızı diske ve Visual Studio Code çalışma alanında açık olan bir klasör içinde kaydedilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="127ff-223">To get the code editing features of Ionide, your F# files need to be saved to disk and inside of a folder that is open in the Visual Studio Code workspace.</span></span>
2. <span data-ttu-id="127ff-224">Sisteminizde değişiklik yapılan veya Visual Studio Code ile açık Ionide Önkoşullar yüklendi, Visual Studio Code yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="127ff-224">If you've made changes to your system or installed Ionide prerequisites with Visual Studio Code open, restart Visual Studio Code.</span></span>
3. <span data-ttu-id="127ff-225">F # derleyici ve F # Etkileşimli bir tam yol olmadan komut satırından kullanıp kullanmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="127ff-225">Check that you can use the F# compiler and F# interactive from the command line without a fully-qualified path.</span></span> <span data-ttu-id="127ff-226">Yazarak yapabilirsiniz `fsc` F # derleyici, bir komut satırında ve `fsi` veya `fsharpi` Visual F # için Araçlar Windows ve Mac/Linux üzerinde Mono sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="127ff-226">You can do so by typing `fsc` in a command line for the F# compiler, and `fsi` or `fsharpi` for the Visual F# tools on Windows and Mono on Mac/Linux, respectively.</span></span>
4. <span data-ttu-id="127ff-227">Proje dizinlerinizi geçersiz karakterler varsa, Ionide çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="127ff-227">If you have invalid characters in your project directories, Ionide might not work.</span></span>  <span data-ttu-id="127ff-228">Bu durumda proje dizinlerinizi yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="127ff-228">Rename your project directories if this is the case.</span></span>
5. <span data-ttu-id="127ff-229">Ionide komutları hiçbiri çalışıyorsanız, denetleyin, [Visual Studio Code taşıyan](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) , bunları yanlışlıkla geçersiz kılma olmadığını görmek için.</span><span class="sxs-lookup"><span data-stu-id="127ff-229">If none of the Ionide commands are working, check your [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) to see if you're overriding them by accident.</span></span>
6. <span data-ttu-id="127ff-230">Ionide makinenizde bozuk ve Yukarıdakilerin hiçbiri sorununuzu düzeltti kaldırmayı deneyin `ionide-fsharp` makinenizde dizin ve eklenti paketi yeniden yükleyin.</span><span class="sxs-lookup"><span data-stu-id="127ff-230">If Ionide is broken on your machine and none of the above has fixed your problem, try removing the `ionide-fsharp` directory on your machine and reinstall the plugin suite.</span></span>

<span data-ttu-id="127ff-231">Ionide yerleşik ve F # topluluk üyeleri tarafından korunan bir açık kaynak projesidir.</span><span class="sxs-lookup"><span data-stu-id="127ff-231">Ionide is an open source project built and maintained by members of the F# community.</span></span> <span data-ttu-id="127ff-232">Lütfen raporu sorunları ve adresindeki katkıda bulunmaktan çekinmeyin [Ionide VSCode: FSharp GitHub deposunu](https://github.com/ionide/ionide-vscode-fsharp).</span><span class="sxs-lookup"><span data-stu-id="127ff-232">Please report issues and feel free to contribute at the [Ionide-VSCode: FSharp GitHub repository](https://github.com/ionide/ionide-vscode-fsharp).</span></span>

<span data-ttu-id="127ff-233">Rapor için bir sorun varsa, lütfen izleyin [bir sorun raporlama yapılırken kullanılacak günlüklerini alma yönergeleri](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span><span class="sxs-lookup"><span data-stu-id="127ff-233">If you have an issue to report, please follow [the instructions for getting logs to use when reporting an issue](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span></span>

<span data-ttu-id="127ff-234">Daha fazla yardım için Ionide geliştiriciler ve F # topluluğuna sorabilirsiniz [Ionide Gitter kanal](https://gitter.im/ionide/ionide-project).</span><span class="sxs-lookup"><span data-stu-id="127ff-234">You can also ask for further help from the Ionide developers and F# community in the [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span></span>

## <a name="next-steps"></a><span data-ttu-id="127ff-235">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="127ff-235">Next steps</span></span>

<span data-ttu-id="127ff-236">F # ve dil özellikleri hakkında daha fazla bilgi için kullanıma [Tur, F #](../tour.md).</span><span class="sxs-lookup"><span data-stu-id="127ff-236">To learn more about F# and the features of the language, check out [Tour of F#](../tour.md).</span></span>
