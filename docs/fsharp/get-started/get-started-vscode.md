---
title: "F # Ionide ile Visual Studio Code ile çalışmaya başlama"
description: "F # Visual Studio Code ve Ionide eklentisi paketiyle nasıl kullanacağınızı öğrenin."
keywords: "Visual f #, f #, işlev, .NET, Visual Studio Code vscode Ionide programlama"
author: cartermp
ms.author: phcart
ms.date: 09/28/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 49775139-082e-442f-b5a2-dd402399b5d2
ms.openlocfilehash: 83099005074ea273eae5319edacd2e2ee0f7145f
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2018
---
# <a name="getting-started-with-f-in-visual-studio-code-with-ionide"></a><span data-ttu-id="74ce5-104">F # Ionide ile Visual Studio Code ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="74ce5-104">Getting Started with F# in Visual Studio Code with Ionide</span></span>

<span data-ttu-id="74ce5-105">F # yazabileceğiniz [Visual Studio Code](https://code.visualstudio.com) ile [Ionide eklentisi](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp), IntelliSense ve temel kod yapan yeniden düzenlemeler harika bir çapraz platform, basit IDE deneyimi alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="74ce5-105">You can write F# in [Visual Studio Code](https://code.visualstudio.com) with the [Ionide plugin](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp), to get a great cross-platform, lightweight IDE experience with IntelliSense and basic code refactorings.</span></span>  <span data-ttu-id="74ce5-106">Ziyaret [Ionide.io](https://ionide.io) eklentisi paketi hakkında daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="74ce5-106">Visit [Ionide.io](https://ionide.io) to learn more about the plugin suite.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="74ce5-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="74ce5-107">Prerequisites</span></span>

<span data-ttu-id="74ce5-108">F # 4.0 veya sonraki Ionide kullanmak için makinenizde yüklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="74ce5-108">F# 4.0 or higher must be installed on your machine to use Ionide.</span></span>

<span data-ttu-id="74ce5-109">Oluşturmuş olmanız da gerekir [yüklü git](https://git-scm.com/download) ve kullanılabilir yapmak için yolunda Ionide proje şablonlarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74ce5-109">You must also have [git installed](https://git-scm.com/download) and available on your PATH to make use of project templates in Ionide.</span></span>  <span data-ttu-id="74ce5-110">Bunu doğru şekilde yazarak yüklendiğini doğrulayabilirsiniz `git` komutu prompt.and tuşlarına basarak adresindeki **Enter**.</span><span class="sxs-lookup"><span data-stu-id="74ce5-110">You can verify that it is installed correctly by typing `git` at a command prompt.and pressing **Enter**.</span></span>

### <a name="windows"></a><span data-ttu-id="74ce5-111">Windows</span><span class="sxs-lookup"><span data-stu-id="74ce5-111">Windows</span></span>

<span data-ttu-id="74ce5-112">Windows üzerinde değilseniz, F # yüklemek için iki seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="74ce5-112">If you're on Windows, you have two options for installing F#.</span></span>

<span data-ttu-id="74ce5-113">Visual Studio zaten yüklemiş olduğunuz ve F # yüklü değilse, yapabilecekleriniz [Visual F # Araçları'nı yükleme](get-started-visual-studio.md#installing-f).</span><span class="sxs-lookup"><span data-stu-id="74ce5-113">If you've already installed Visual Studio and don't have F#, you can [Install the Visual F# Tools](get-started-visual-studio.md#installing-f).</span></span>  <span data-ttu-id="74ce5-114">Bu yazma, derlemek ve F # kod yürütmek için gerekli tüm bileşenleri yükler.</span><span class="sxs-lookup"><span data-stu-id="74ce5-114">This will install all the necessary components to write, compile, and execute F# code.</span></span>

<span data-ttu-id="74ce5-115">Visual Studio yüklememeyi tercih ederseniz, aşağıdaki yönergeleri kullanın:</span><span class="sxs-lookup"><span data-stu-id="74ce5-115">If you prefer not to install Visual Studio, use the following instructions:</span></span>

1. <span data-ttu-id="74ce5-116">Yükleme [.NET Framework 4.5 veya üstü](https://www.microsoft.com/en-US/download/details.aspx?id=30653) Windows 7 çalıştırıyorsanız.</span><span class="sxs-lookup"><span data-stu-id="74ce5-116">Install [.NET Framework 4.5 or higher](https://www.microsoft.com/en-US/download/details.aspx?id=30653) if you're running Windows 7.</span></span>  <span data-ttu-id="74ce5-117">Windows 8 veya üzeri kullanıyorsanız, bunu yapmak gerekmez.</span><span class="sxs-lookup"><span data-stu-id="74ce5-117">If you're using Windows 8 or higher, you do not need to do this.</span></span>

2. <span data-ttu-id="74ce5-118">Windows SDK için işletim sistemi yükleyin:</span><span class="sxs-lookup"><span data-stu-id="74ce5-118">Install the Windows SDK for your OS:</span></span>

    * [<span data-ttu-id="74ce5-119">Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="74ce5-119">Windows 10 SDK</span></span>](https://dev.windows.com/en-US/downloads/windows-10-sdk)
    * [<span data-ttu-id="74ce5-120">Windows 8.1 SDK</span><span class="sxs-lookup"><span data-stu-id="74ce5-120">Windows 8.1 SDK</span></span>](https://developer.microsoft.com/windows/downloads/sdk-archive)
    * [<span data-ttu-id="74ce5-121">Windows 8 SDK</span><span class="sxs-lookup"><span data-stu-id="74ce5-121">Windows 8 SDK</span></span>](https://developer.microsoft.com/windows/downloads/sdk-archive)
    * [<span data-ttu-id="74ce5-122">Windows 7 SDK</span><span class="sxs-lookup"><span data-stu-id="74ce5-122">Windows 7 SDK</span></span>](https://www.microsoft.com/download/details.aspx?id=8279)

3. <span data-ttu-id="74ce5-123">Yükleme [Microsoft derleme araçları 2015](https://www.microsoft.com/en-us/download/details.aspx?id=48159).</span><span class="sxs-lookup"><span data-stu-id="74ce5-123">Install the [Microsoft Build Tools 2015](https://www.microsoft.com/en-us/download/details.aspx?id=48159).</span></span>  <span data-ttu-id="74ce5-124">Yüklemeniz gerekebilir [Microsoft derleme araçları 2013](https://www.microsoft.com/en-us/download/details.aspx?id=40760).</span><span class="sxs-lookup"><span data-stu-id="74ce5-124">You may also need to install [Microsoft Build Tools 2013](https://www.microsoft.com/en-us/download/details.aspx?id=40760).</span></span>

4. <span data-ttu-id="74ce5-125">Yükleme [Visual F # Araçları](https://www.microsoft.com/en-us/download/details.aspx?id=48179).</span><span class="sxs-lookup"><span data-stu-id="74ce5-125">Install the [Visual F# Tools](https://www.microsoft.com/en-us/download/details.aspx?id=48179).</span></span>

<span data-ttu-id="74ce5-126">64-bit Windows sürümlerinde derleyici ve araçları burada bulunur:</span><span class="sxs-lookup"><span data-stu-id="74ce5-126">On 64-bit Windows, the compiler and tools are located here:</span></span>

```
C:\Program Files (x86)\Microsoft SDKs\F#\4.0\Framework\v4.0\fsc.exe
C:\Program Files (x86)\Microsoft SDKs\F#\4.0\Framework\v4.0\fsi.exe
C:\Program Files (x86)\Microsoft SDKs\F#\4.0\Framework\v4.0\fsiAnyCpu.exe
```

<span data-ttu-id="74ce5-127">32-bit Windows sürümlerinde derleyici araçları burada bulunur:</span><span class="sxs-lookup"><span data-stu-id="74ce5-127">On 32-bit Windows, the compiler tools are located here:</span></span>

```
C:\Program Files\Microsoft SDKs\F#\4.0\Framework\v4.0\fsc.exe
C:\Program Files\Microsoft SDKs\F#\4.0\Framework\v4.0\fsi.exe
C:\Program Files\Microsoft SDKs\F#\4.0\Framework\v4.0\fsiAnyCpu.exe
```

<span data-ttu-id="74ce5-128">Ionide otomatik olarak algılar derleyici ve araçları, ancak herhangi bir nedenden dolayı olmazsa (örneğin, Visual F # Araçları farklı bir klasöre yüklenen), içeren klasörü el ile ekleyebilirsiniz (`...\Microsoft SDKs\F#\4.0`), yolu.</span><span class="sxs-lookup"><span data-stu-id="74ce5-128">Ionide automatically detects the compiler and tools, but if it doesn't for some reason (for example, the Visual F# Tools were installed to a different directory), you can manually add the containing folder (`...\Microsoft SDKs\F#\4.0`) to your PATH.</span></span>

### <a name="macos"></a><span data-ttu-id="74ce5-129">macOS</span><span class="sxs-lookup"><span data-stu-id="74ce5-129">macOS</span></span>

<span data-ttu-id="74ce5-130">MacOS üzerinde Ionide kullanan [Mono](https://www.mono-project.com).</span><span class="sxs-lookup"><span data-stu-id="74ce5-130">On macOS, Ionide uses [Mono](https://www.mono-project.com).</span></span>  <span data-ttu-id="74ce5-131">Homebrew üzerinde macOS Mono yüklemek için en kolay yoludur.</span><span class="sxs-lookup"><span data-stu-id="74ce5-131">The easiest way to install Mono on macOS is via Homebrew.</span></span>  <span data-ttu-id="74ce5-132">Terminalinizde yalnızca aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="74ce5-132">Simply type the following into your terminal:</span></span>

```
brew install mono
```

### <a name="linux"></a><span data-ttu-id="74ce5-133">Linux</span><span class="sxs-lookup"><span data-stu-id="74ce5-133">Linux</span></span>

<span data-ttu-id="74ce5-134">Linux üzerinde Ionide de kullanır [Mono](https://www.mono-project.com).</span><span class="sxs-lookup"><span data-stu-id="74ce5-134">On Linux, Ionide also uses [Mono](https://www.mono-project.com).</span></span>  <span data-ttu-id="74ce5-135">Debian veya Ubuntu değilseniz, aşağıdakileri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="74ce5-135">If you're on Debian or Ubuntu, you can use the following:</span></span>

```
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

## <a name="installing-visual-studio-code-and-the-ionide-plugin"></a><span data-ttu-id="74ce5-136">Visual Studio Code ve Ionide eklentisini yükleme</span><span class="sxs-lookup"><span data-stu-id="74ce5-136">Installing Visual Studio Code and the Ionide plugin</span></span>

<span data-ttu-id="74ce5-137">Visual Studio koddan yükleyebilirsiniz [code.visualstudio.com](https://code.visualstudio.com) Web sitesi.</span><span class="sxs-lookup"><span data-stu-id="74ce5-137">You can install Visual Studio Code from the [code.visualstudio.com](https://code.visualstudio.com) website.</span></span>  <span data-ttu-id="74ce5-138">Bundan sonra Ionide eklentisi bulmanın iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="74ce5-138">After that, there are two ways to find the Ionide plugin:</span></span>

1. <span data-ttu-id="74ce5-139">Komut palet (Ctrl + Shift + P Windows, ⌘ + Shift + P macOS, Linux üzerinde Ctrl + Shift + P) kullanın ve aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="74ce5-139">Use the Command Palette (Ctrl+Shift+P on Windows, ⌘+Shift+P on macOS, Ctrl+Shift+P on Linux) and type the following:</span></span>

    ```
    >ext install Ionide
    ```

2. <span data-ttu-id="74ce5-140">"Ionide" için arama ve uzantıları simgesini tıklatın:</span><span class="sxs-lookup"><span data-stu-id="74ce5-140">Click the Extensions icon and search for "Ionide":</span></span>

    ![](media/getting-started-vscode/vscode-ext.png)

<span data-ttu-id="74ce5-141">F # Visual Studio Code desteklenmediği için gereken tek eklentisi [Ionide fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span><span class="sxs-lookup"><span data-stu-id="74ce5-141">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span>  <span data-ttu-id="74ce5-142">Ancak, aynı zamanda yükleyebilirsiniz [Ionide sahte](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) ve almak için [sahte](https://fake.build/) desteklemek ve [Ionide Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) almak için [Paket](https://fsprojects.github.io/Paket/) destekler.</span><span class="sxs-lookup"><span data-stu-id="74ce5-142">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) and to get [FAKE](https://fake.build/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span>  <span data-ttu-id="74ce5-143">SAHTE ve Paket projeleri oluşturmak ve bağımlılıkları, sırasıyla yönetmek için ilave F # topluluk araçları.</span><span class="sxs-lookup"><span data-stu-id="74ce5-143">FAKE and Paket are additonal F# community tools for building projects and managing dependencies, respectively.</span></span>

## <a name="creating-your-first-project-with-ionide"></a><span data-ttu-id="74ce5-144">Ionide ile ilk projenizi oluşturma</span><span class="sxs-lookup"><span data-stu-id="74ce5-144">Creating your first project with Ionide</span></span>

<span data-ttu-id="74ce5-145">Yeni bir F # projesi oluşturmak için Visual Studio Code yeni bir klasöre (örneğin, istediğiniz adı verebilirsiniz) açın.</span><span class="sxs-lookup"><span data-stu-id="74ce5-145">To create a new F# project, open Visual Studio Code in a new folder (you can name it whatever you like).</span></span>

![](media/getting-started-vscode/vscode-open-dir.png)

<span data-ttu-id="74ce5-146">Ardından, komut palet (Ctrl + Shift + P Windows, ⌘ + Shift + P macOS, Linux üzerinde Ctrl + Shift + P) açın ve aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="74ce5-146">Next, open the Command Palette (Ctrl+Shift+P on Windows, ⌘+Shift+P on macOS, Ctrl+Shift+P on Linux) and type the following:</span></span>

```
>f#: New Project
```

<span data-ttu-id="74ce5-147">Bu tarafından desteklenmektedir [FORGE](https://github.com/fsharp-editing/Forge) projesi.</span><span class="sxs-lookup"><span data-stu-id="74ce5-147">This is powered by the [FORGE](https://github.com/fsharp-editing/Forge) project.</span></span>  <span data-ttu-id="74ce5-148">Şöyle bir şey görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="74ce5-148">You should see something like this:</span></span>

![](media/getting-started-vscode/vscode-new-proj.png)

> [!NOTE]
<span data-ttu-id="74ce5-149">Yukarıdaki görmüyorsanız, komut Palette aşağıdaki komutu çalıştırarak şablonları yenilemeyi deneyin: `>F#: Refresh Project Templates`.</span><span class="sxs-lookup"><span data-stu-id="74ce5-149">If you don't see the above, try refreshing templates by running the following command in the Command Palette: `>F#: Refresh Project Templates`.</span></span>

<span data-ttu-id="74ce5-150">"F #: Yeni Proje" basarsa tarafından seçin **Enter**, hangi alır, bu adım için:</span><span class="sxs-lookup"><span data-stu-id="74ce5-150">Select "F#: New Project" by hitting **Enter**, which will take you to this step:</span></span>

![](media/getting-started-vscode/vscode-proj-type.png)

<span data-ttu-id="74ce5-151">Bu proje belirli bir tür için bir şablon seçecektir.</span><span class="sxs-lookup"><span data-stu-id="74ce5-151">This will select a template for a specific type of project.</span></span>  <span data-ttu-id="74ce5-152">Oldukça birkaç seçenek vardır burada gibi bir [FsLab](https://fslab.org) veri bilimi için şablonu veya [Suave](https://suave.io) Web programlama için şablon.</span><span class="sxs-lookup"><span data-stu-id="74ce5-152">There are quite a few options here, such as an [FsLab](https://fslab.org) template for Data Science or [Suave](https://suave.io) template for Web Programming.</span></span>  <span data-ttu-id="74ce5-153">Bu makalede kullanan `classlib` şablonu, bu nedenle, vurgulayın ve isabet **Enter**.</span><span class="sxs-lookup"><span data-stu-id="74ce5-153">This article uses the `classlib` template, so highlight that and hit **Enter**.</span></span>  <span data-ttu-id="74ce5-154">Ardından aşağıdaki adımı ulaşabileceği:</span><span class="sxs-lookup"><span data-stu-id="74ce5-154">You will then reach the following step:</span></span>

![](media/getting-started-vscode/vscode-new-dir.png)

<span data-ttu-id="74ce5-155">Bu, farklı bir dizinde isterseniz proje oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="74ce5-155">This lets you create the project in a different directory, if you like.</span></span>  <span data-ttu-id="74ce5-156">Boş şimdilik bırakın.</span><span class="sxs-lookup"><span data-stu-id="74ce5-156">Leave it blank for now.</span></span>  <span data-ttu-id="74ce5-157">Geçerli dizinde projesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="74ce5-157">It will create the project in the current directory.</span></span>  <span data-ttu-id="74ce5-158">Tuşuna sonra **Enter**, aşağıdaki adımı ulaşabileceği:</span><span class="sxs-lookup"><span data-stu-id="74ce5-158">Once you press **Enter**, you will reach the following step:</span></span>

![](media/getting-started-vscode/vscode-proj-name.png)

<span data-ttu-id="74ce5-159">Bu, projenizin adı sağlar.</span><span class="sxs-lookup"><span data-stu-id="74ce5-159">This lets you name your project.</span></span>  <span data-ttu-id="74ce5-160">F # kullanan [Pascal durumda](http://c2.com/cgi/wiki?PascalCase) proje adları için.</span><span class="sxs-lookup"><span data-stu-id="74ce5-160">F# uses [Pascal case](http://c2.com/cgi/wiki?PascalCase) for project names.</span></span>  <span data-ttu-id="74ce5-161">Bu makalede kullanan `ClassLibraryDemo` adı.</span><span class="sxs-lookup"><span data-stu-id="74ce5-161">This article uses `ClassLibraryDemo` as the name.</span></span>  <span data-ttu-id="74ce5-162">Projeniz için istediğiniz adı girdikten sonra isabet **Enter**.</span><span class="sxs-lookup"><span data-stu-id="74ce5-162">Once you've entered the name you want for your project, hit **Enter**.</span></span>

<span data-ttu-id="74ce5-163">Önceki adım adımları izlediyseniz, Visual Studio kod şöyle bir şey aramak için çalışma alanı sol taraftaki almanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="74ce5-163">If you followed the previous step steps, you should get the Visual Studio Code Workspace on the left-hand side to look something like this:</span></span>

![](media/getting-started-vscode/vscode-new-proj-explorer.png)

<span data-ttu-id="74ce5-164">Bu şablon, yararlı bulabilirsiniz birkaç oluşturur:</span><span class="sxs-lookup"><span data-stu-id="74ce5-164">This template generates a few things you'll find useful:</span></span>

1. <span data-ttu-id="74ce5-165">F # proje kendisini altındaki `ClassLibraryDemo` klasörü.</span><span class="sxs-lookup"><span data-stu-id="74ce5-165">The F# project itself, underneath the `ClassLibraryDemo` folder.</span></span>
2. <span data-ttu-id="74ce5-166">Paketleri yoluyla eklemek için doğru dizin yapısını [ `Paket` ](https://fsprojects.github.io/Paket/).</span><span class="sxs-lookup"><span data-stu-id="74ce5-166">The correct directory structure for adding packages via [`Paket`](https://fsprojects.github.io/Paket/).</span></span>
3. <span data-ttu-id="74ce5-167">Çapraz platform komut dosyasıyla yapı [ `FAKE` ](https://fake.build/).</span><span class="sxs-lookup"><span data-stu-id="74ce5-167">A cross-platform build script with [`FAKE`](https://fake.build/).</span></span>
4. <span data-ttu-id="74ce5-168">`paket.exe` Fetch paketleri ve sizin için bağımlılıklar çözümlenmeye çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="74ce5-168">The `paket.exe` executable which can fetch packages and resolve dependencies for you.</span></span>
5. <span data-ttu-id="74ce5-169">A `.gitignore` bu proje Git tabanlı bir kaynak denetimine eklemek isterseniz, dosya.</span><span class="sxs-lookup"><span data-stu-id="74ce5-169">A `.gitignore` file if you wish to add this project to Git-based source control.</span></span>

## <a name="writing-some-code"></a><span data-ttu-id="74ce5-170">Bazı kod yazma</span><span class="sxs-lookup"><span data-stu-id="74ce5-170">Writing some code</span></span>

<span data-ttu-id="74ce5-171">Açık *ClassLibraryDemo* klasör.</span><span class="sxs-lookup"><span data-stu-id="74ce5-171">Open the *ClassLibraryDemo* folder.</span></span>  <span data-ttu-id="74ce5-172">Aşağıdaki dosyalar görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="74ce5-172">You should see the following files:</span></span>

1. <span data-ttu-id="74ce5-173">`ClassLibraryDemo.fs`, F # uygulaması olan bir dosya tanımlı bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="74ce5-173">`ClassLibraryDemo.fs`, an F# implementation file with a class defined.</span></span>
2. <span data-ttu-id="74ce5-174">`CassLibraryDemo.fsproj`, bu proje oluşturmak için kullanılan bir F # proje dosyası.</span><span class="sxs-lookup"><span data-stu-id="74ce5-174">`CassLibraryDemo.fsproj`, an F# project file used to build this project.</span></span>
3. <span data-ttu-id="74ce5-175">`Script.fsx`, kaynak dosya yükleyen bir F # komut dosyası.</span><span class="sxs-lookup"><span data-stu-id="74ce5-175">`Script.fsx`, an F# script file which loads the source file.</span></span>
4. <span data-ttu-id="74ce5-176">`paket.references`, proje bağımlılıklarını belirten bir Paket dosyası.</span><span class="sxs-lookup"><span data-stu-id="74ce5-176">`paket.references`, a Paket file which specifies the project dependencies.</span></span>

<span data-ttu-id="74ce5-177">Açık `Script.fsx`ve sonunda, aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="74ce5-177">Open `Script.fsx`, and add the following code at the end of it:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

<span data-ttu-id="74ce5-178">Bu işlev bir sözcük bir forma dönüştürür [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span><span class="sxs-lookup"><span data-stu-id="74ce5-178">This function converts a word to a form of [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span></span>  <span data-ttu-id="74ce5-179">F # Etkileşimli (FSI) kullanarak değerlendirmek için sonraki adımda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="74ce5-179">The next step is to evaluate it using F# Interactive (FSI).</span></span>

<span data-ttu-id="74ce5-180">(11 satır uzunluğundaki olmalıdır) tüm işlevi vurgulayın.</span><span class="sxs-lookup"><span data-stu-id="74ce5-180">Highlight the entire function (it should be 11 lines long).</span></span>  <span data-ttu-id="74ce5-181">Vurgulanır sonra tutun **Alt** anahtarı ve isabet **Enter**.</span><span class="sxs-lookup"><span data-stu-id="74ce5-181">Once it is highlighted, hold the **Alt** key and hit **Enter**.</span></span>  <span data-ttu-id="74ce5-182">Aşağıdaki açılır pencere görürsünüz ve şöyle bir şey göstermesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="74ce5-182">You'll notice a window pop up below, and it should show something like this:</span></span>

![](media/getting-started-vscode/vscode-fsi.png)

<span data-ttu-id="74ce5-183">Üçünü yapar:</span><span class="sxs-lookup"><span data-stu-id="74ce5-183">This did three things:</span></span>

1. <span data-ttu-id="74ce5-184">FSI işlemi başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="74ce5-184">It started the FSI process.</span></span>
2. <span data-ttu-id="74ce5-185">Bu vurguladığınız kodun FSI işlemi gönderilir.</span><span class="sxs-lookup"><span data-stu-id="74ce5-185">It sent the code you highlighted over the FSI process.</span></span>
3. <span data-ttu-id="74ce5-186">FSI işlemi üzerinden gönderilen kodu değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="74ce5-186">The FSI process evaluated the code you sent over.</span></span>

<span data-ttu-id="74ce5-187">Üzerinden gönderilen olduğundan bir [işlevi](../language-reference/functions/index.md), o FSI işleviyle çağırabilirsiniz!</span><span class="sxs-lookup"><span data-stu-id="74ce5-187">Because what you sent over was a [function](../language-reference/functions/index.md), you can now call that function with FSI!</span></span>  <span data-ttu-id="74ce5-188">Etkileşimli penceresinde aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="74ce5-188">In the interactive window, type the following:</span></span>

```fsharp
toPigLatin "banana";;
```

<span data-ttu-id="74ce5-189">Aşağıdaki sonucu görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="74ce5-189">You should see the following result:</span></span>

```fsharp
val it : string = "ananabay"
```

<span data-ttu-id="74ce5-190">Şimdi, ilk harfi olarak sesli bir ile deneyelim.</span><span class="sxs-lookup"><span data-stu-id="74ce5-190">Now, let's try with a vowel as the first letter.</span></span> <span data-ttu-id="74ce5-191">Aşağıdakileri girin:</span><span class="sxs-lookup"><span data-stu-id="74ce5-191">Enter the following:</span></span>

```fsharp
toPigLatin "apple";;
```

<span data-ttu-id="74ce5-192">Aşağıdaki sonucu görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="74ce5-192">You should see the following result:</span></span>

```fsharp
val it : string = "appleyay"
```

<span data-ttu-id="74ce5-193">İşlev beklendiği gibi çalıştığını görünüyor.</span><span class="sxs-lookup"><span data-stu-id="74ce5-193">The function appears to be working as expected.</span></span>  <span data-ttu-id="74ce5-194">Tebrikler, yalnızca Visual Studio kodda ilk F # işlevinizi yazdı ve FSI ile değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="74ce5-194">Congratulations, you just wrote your first F# function in Visual Studio Code and evaluated it with FSI!</span></span>

>[!NOTE]
<span data-ttu-id="74ce5-195">Fark etmiş olabilirsiniz gibi FSI satırları ile sona erdirilir `;;`.</span><span class="sxs-lookup"><span data-stu-id="74ce5-195">As you may have noticed, the lines in FSI are terminated with `;;`.</span></span>  <span data-ttu-id="74ce5-196">FSI birden fazla satır girmenizi sağlayan olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="74ce5-196">This is because FSI allows you to enter multiple lines.</span></span>  <span data-ttu-id="74ce5-197">`;;` Sonunda kodu bittiği bilmeniz FSI olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="74ce5-197">The `;;` at the end lets FSI know when the code is finished.</span></span>

## <a name="explaining-the-code"></a><span data-ttu-id="74ce5-198">Kod açıklayan</span><span class="sxs-lookup"><span data-stu-id="74ce5-198">Explaining the code</span></span>

<span data-ttu-id="74ce5-199">Kod gerçekte yaptıklarını hakkında emin değilseniz, işte bir adım adım.</span><span class="sxs-lookup"><span data-stu-id="74ce5-199">If you're not sure about what the code is actually doing, here's a step-by-step.</span></span>

<span data-ttu-id="74ce5-200">Gördüğünüz gibi `toPigLatin` bir sözcük, girdi olarak alır ve bu word'ün bir Pig Latin gösterimine dönüştürür bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="74ce5-200">As you can see, `toPigLatin` is a function which takes a word as its input and converts it to a Pig-Latin representation of that word.</span></span>  <span data-ttu-id="74ce5-201">Bu kurallar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="74ce5-201">The rules for this are as follows:</span></span>

<span data-ttu-id="74ce5-202">İlk karakter bir sözcük, sesli bir harfle başlarsa, "yay" sözcüğü sonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="74ce5-202">If the first character in a word starts with a vowel, add "yay" to the end of the word.</span></span>  <span data-ttu-id="74ce5-203">Sesli bir harfle başlamazsa, bu ilk karakteri sözcüğün sonuna taşıyın ve "ay" ekleyin.</span><span class="sxs-lookup"><span data-stu-id="74ce5-203">If it doesn't start with a vowel, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="74ce5-204">FSI aşağıdakileri fark etmiş olabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="74ce5-204">You may have noticed the following in FSI:</span></span>

```
val toPigLatin : word:string -> string
```

<span data-ttu-id="74ce5-205">Bu bildiren `toPigLatin` alan, bir işlev değil bir `string` giriş olarak (adlı `word`) ve başka döndürür `string`.</span><span class="sxs-lookup"><span data-stu-id="74ce5-205">This states that `toPigLatin` is a function which takes in a `string` as input (called `word`), and returns another `string`.</span></span>  <span data-ttu-id="74ce5-206">Bu olarak bilinir [işlevinin türü imzası](https://fsharpforfunandprofit.com/posts/function-signatures/), temel bir F #'ın, F # kodunu anlamanın anahtarıdır.</span><span class="sxs-lookup"><span data-stu-id="74ce5-206">This is known as the [type signature of the function](https://fsharpforfunandprofit.com/posts/function-signatures/), a fundamental piece of F# that's key to understanding F# code.</span></span>  <span data-ttu-id="74ce5-207">Visual Studio Code işlevinde üzerine getirirseniz de bu fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="74ce5-207">You'll also notice this if you hover over the function in Visual Studio Code.</span></span>

<span data-ttu-id="74ce5-208">İşlev gövdesine iki ayrı bölümlere görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="74ce5-208">In the body of the function, you'll notice two distinct parts:</span></span>

1. <span data-ttu-id="74ce5-209">Adlı bir iç işlevi `isVowel`, belirli bir karakter varsa belirler (`c`) sağlanan desenleri biriyle eşleşiyorsa denetleyerek bir sesli olup [desen eşleştirme](../language-reference/pattern-matching.md):</span><span class="sxs-lookup"><span data-stu-id="74ce5-209">An inner function, called `isVowel`, which determines if a given character (`c`) is a vowel by checking if it matches one of the provided patterns via [Pattern Matching](../language-reference/pattern-matching.md):</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. <span data-ttu-id="74ce5-210">Bir [ `if..then..else` ](../language-reference/conditional-expressions-if-then-else.md) ifade ilk karakteri bir sesli ise ve dönüş değeri giriş karakter dışında yapıları hangi denetimleri ise ilk karakter tabanlı veya sesli bir oluştu:</span><span class="sxs-lookup"><span data-stu-id="74ce5-210">An [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expression which checks if the first character is a vowel, and constructs a return value out of the input characters based on if the first character was a vowel or not:</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

<span data-ttu-id="74ce5-211">Akışını `toPigLatin` böylece:</span><span class="sxs-lookup"><span data-stu-id="74ce5-211">The flow of `toPigLatin` is thus:</span></span>

<span data-ttu-id="74ce5-212">Giriş word ilk karakteri bir sesli olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="74ce5-212">Check if the first character of the input word is a vowel.</span></span>  <span data-ttu-id="74ce5-213">Bu durumda, "yay" sözcüğün sonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="74ce5-213">If it is, attach "yay" to the end of the word.</span></span>  <span data-ttu-id="74ce5-214">Aksi takdirde, bu ilk karakteri sözcüğün sonuna taşıyın ve "ay" ekleyin.</span><span class="sxs-lookup"><span data-stu-id="74ce5-214">Otherwise, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="74ce5-215">Bu konuda fark için son bir şey yok: birçok diğer diller ölçeklendiriyor aksine işlevi döndürmek için açık bir yönerge yoktur.</span><span class="sxs-lookup"><span data-stu-id="74ce5-215">There's one final thing to notice about this: there's no explicit instruction to return from the function, unlike many other languages out there.</span></span>  <span data-ttu-id="74ce5-216">F # ifade tabanlı, ve bir işlev gövdesine son deyim dönüş değeri olduğundan budur.</span><span class="sxs-lookup"><span data-stu-id="74ce5-216">This is because F# is Expression-based, and the last expression in the body of a function is the return value.</span></span>  <span data-ttu-id="74ce5-217">Çünkü `if..then..else` kendisi gövdesi bir ifade değildir `then` engelleme veya gövdesini `else` blok bağlı olarak giriş değeri döndürülecek.</span><span class="sxs-lookup"><span data-stu-id="74ce5-217">Because `if..then..else` is itself an expression, the body of the `then` block or the body of the `else` block will be returned depending on the input value.</span></span>

## <a name="moving-your-script-code-into-the-implementation-file"></a><span data-ttu-id="74ce5-218">Uygulama dosyasına betik kodunuzu taşıma</span><span class="sxs-lookup"><span data-stu-id="74ce5-218">Moving your script code into the implementation file</span></span>

<span data-ttu-id="74ce5-219">Bu makalede önceki bölümlerde gösterildiği F # kodu yazarken ortak bir ilk adım: bir başlangıç işlevi yazma ve etkileşimli olarak FSI ile çalıştırma.</span><span class="sxs-lookup"><span data-stu-id="74ce5-219">The previous sections in this article demonstrated a common first step in writing F# code: writing an initial function and executing it interactively with FSI.</span></span>  <span data-ttu-id="74ce5-220">Bu, burada REPL "Okuma değerlendirmek yazdırma döngü için" anlamına gelir, REPL güdümlü geliştirme olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="74ce5-220">This is known as REPL-driven development, where REPL stands for "Read-Evaluate-Print Loop".</span></span>  <span data-ttu-id="74ce5-221">Bir çalışma elde edene kadar işlevsellikle denemek için harika bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="74ce5-221">It's a great way to experiment with functionality until you have something working.</span></span>

<span data-ttu-id="74ce5-222">REPL güdümlü geliştirme sonraki adımda, bir F # uygulama dosyasına çalışan kodu taşımaktır.</span><span class="sxs-lookup"><span data-stu-id="74ce5-222">The next step in REPL-driven development is to move working code into an F# implementation file.</span></span>  <span data-ttu-id="74ce5-223">Ardından, yürütülebilir bir derlemeye F # derleyici tarafından olarak da derlenebilir.</span><span class="sxs-lookup"><span data-stu-id="74ce5-223">It can then be compiled by the F# compiler into an assembly which can be executed.</span></span>

<span data-ttu-id="74ce5-224">Başlamak için açın `ClassLibraryDemo.fs`.</span><span class="sxs-lookup"><span data-stu-id="74ce5-224">To begin, open `ClassLibraryDemo.fs`.</span></span>  <span data-ttu-id="74ce5-225">Bazı kodu zaten da olduğunu fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="74ce5-225">You'll notice that some code is already in there.</span></span>  <span data-ttu-id="74ce5-226">Devam edin ve sınıf tanımını silin, ancak bıraktığınızdan emin olun [ `namespace` ](../language-reference/namespaces.md) bildiriminin en üstünde.</span><span class="sxs-lookup"><span data-stu-id="74ce5-226">Go ahead and delete the class definition, but make sure to leave the [`namespace`](../language-reference/namespaces.md) declaration at the top.</span></span>

<span data-ttu-id="74ce5-227">Ardından, yeni bir oluşturun [ `module` ](../language-reference/modules.md) adlı `PigLatin` ve kopyalama `toPigLatin` şekilde işlevi içine:</span><span class="sxs-lookup"><span data-stu-id="74ce5-227">Next, create a new [`module`](../language-reference/modules.md) called `PigLatin` and copy the `toPigLatin` function into it as such:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

<span data-ttu-id="74ce5-228">Bu, ayrıca C# veya Visual Basic projeleri kodunuzun çağırması istiyorsanız, F # kodunda işlevler ve ortak bir yaklaşım düzenleyebilirsiniz birçok yolu biridir.</span><span class="sxs-lookup"><span data-stu-id="74ce5-228">This is one of the many ways you can organize functions in F# code, and a common approach if you also want to call your code from C# or Visual Basic projects.</span></span>

<span data-ttu-id="74ce5-229">Ardından, açık `Script.fsx` dosyasını yeniden ve tüm silme `toPigLatin` çalışır, ancak aşağıdaki iki satırı dosyasında sakladığınızdan emin olun:</span><span class="sxs-lookup"><span data-stu-id="74ce5-229">Next, open the `Script.fsx` file again, and delete the entire `toPigLatin` function, but make sure to keep the following two lines in the file:</span></span>

```
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

<span data-ttu-id="74ce5-230">İlk satırı FSI yüklemek için komut dosyası için gereken `ClassLibraryDemo.fs`.</span><span class="sxs-lookup"><span data-stu-id="74ce5-230">The first line is needed for FSI scripting to load `ClassLibraryDemo.fs`.</span></span>  <span data-ttu-id="74ce5-231">İkinci satır bir kolaylık bağlı: Bu atlama isteğe bağlıdır ancak yazmanız gerekir `open ClassLibraryDemo` getirmek isterseniz, bir FSI penceresinde `ToPigLatin` kapsam modüle.</span><span class="sxs-lookup"><span data-stu-id="74ce5-231">The second line is a convenience: omitting it is optional, but you will need to type `open ClassLibraryDemo` in an FSI window if you wish to bring the `ToPigLatin` module into scope.</span></span>

<span data-ttu-id="74ce5-232">Ardından, FSI penceresinde işlev çağrısı `PigLatin` daha önce tanımlanan Modülü:</span><span class="sxs-lookup"><span data-stu-id="74ce5-232">Next, in the FSI window, call the function with the `PigLatin` module that you defined earlier:</span></span>

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

<span data-ttu-id="74ce5-233">Başarılı!</span><span class="sxs-lookup"><span data-stu-id="74ce5-233">Success!</span></span>  <span data-ttu-id="74ce5-234">Önce aynı sonuçları alırsınız, ancak bir F # uygulaması dosyasından şimdi yüklendi.</span><span class="sxs-lookup"><span data-stu-id="74ce5-234">You get the same results as before, but now loaded from an F# implementation file.</span></span>  <span data-ttu-id="74ce5-235">Burada en önemli fark, F # kaynak dosyaları yalnızca FSI içinde herhangi bir yere, yürütülebilir derlemeler içine derlenen ' dir.</span><span class="sxs-lookup"><span data-stu-id="74ce5-235">The major difference here is that F# source files are compiled into assemblies which can be executed anywhere, not just in FSI.</span></span>

## <a name="summary"></a><span data-ttu-id="74ce5-236">Özet</span><span class="sxs-lookup"><span data-stu-id="74ce5-236">Summary</span></span>

<span data-ttu-id="74ce5-237">Bu makalede, öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="74ce5-237">In this article, you've learned:</span></span>

1. <span data-ttu-id="74ce5-238">Visual Studio kodu Ionide ile kurulur.</span><span class="sxs-lookup"><span data-stu-id="74ce5-238">How to set up Visual Studio Code with Ionide.</span></span>
2. <span data-ttu-id="74ce5-239">Ionide ile ilk F # projenizi oluşturma</span><span class="sxs-lookup"><span data-stu-id="74ce5-239">How to create your first F# project with Ionide.</span></span>
3. <span data-ttu-id="74ce5-240">F # komut dosyası yazma, ilk F # için nasıl kullanılacağını Ionide içinde işlev ve FSI içinde yürütün.</span><span class="sxs-lookup"><span data-stu-id="74ce5-240">How to use F# Scripting to write your first F# function in Ionide and then execute it in FSI.</span></span>
4. <span data-ttu-id="74ce5-241">Kodunuzu geçirmek nasıl F # kaynak kodu ve sonra bu kodu FSI çağırın.</span><span class="sxs-lookup"><span data-stu-id="74ce5-241">How to migrate your script code to F# source and then call that code from FSI.</span></span>

<span data-ttu-id="74ce5-242">Şimdi Visual Studio Code ile Ionide olan çok daha fazla F # kod yazmaya donatılmış.</span><span class="sxs-lookup"><span data-stu-id="74ce5-242">You're now equipped to write much more F# code using Visual Studio Code and Ionide.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="74ce5-243">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="74ce5-243">Troubleshooting</span></span>

<span data-ttu-id="74ce5-244">İçine çalışabilir belirli sorunları giderme birkaç şekilde şunlardır:</span><span class="sxs-lookup"><span data-stu-id="74ce5-244">Here are a few ways you can troubleshoot certain problems that you might run into:</span></span>

1. <span data-ttu-id="74ce5-245">Ionide özelliklerini düzenleme kod almak için F # dosyalarınızı diske ve Visual Studio Code çalışma alanında açık olan bir klasör içinde kaydedilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="74ce5-245">To get the code editing features of Ionide, your F# files need to be saved to disk and inside of a folder that is open in the Visual Studio Code workspace.</span></span>
2. <span data-ttu-id="74ce5-246">Sisteminizde değişiklik yapılan veya Visual Studio Code ile açık Ionide Önkoşullar yüklendi, Visual Studio Code yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="74ce5-246">If you've made changes to your system or installed Ionide prerequisites with Visual Studio Code open, restart Visual Studio Code.</span></span>
3. <span data-ttu-id="74ce5-247">F # derleyici ve F # Etkileşimli bir tam yol olmadan komut satırından kullanıp kullanmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="74ce5-247">Check that you can use the F# compiler and F# interactive from the command line without a fully-qualified path.</span></span>  <span data-ttu-id="74ce5-248">Yazarak yapabilirsiniz `fsc` F # derleyici, bir komut satırında ve `fsi` veya `fsharpi` Visual F # için Araçlar Windows ve Mac/Linux üzerinde Mono sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="74ce5-248">You can do so by typing `fsc` in a command line for the F# compiler, and `fsi` or `fsharpi` for the Visual F# tools on Windows and Mono on Mac/Linux, respectively.</span></span>
4. <span data-ttu-id="74ce5-249">Proje dizinlerinizi geçersiz karakterler varsa, Ionide çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="74ce5-249">If you have invalid characters in your project directories, Ionide might not work.</span></span>  <span data-ttu-id="74ce5-250">Bu durumda proje dizinlerinizi yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="74ce5-250">Rename your project directories if this is the case.</span></span>
5. <span data-ttu-id="74ce5-251">Ionide komutları hiçbiri çalışıyorsanız, denetleyin, [Visual Studio Code taşıyan](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) , bunları yanlışlıkla geçersiz kılma olmadığını görmek için.</span><span class="sxs-lookup"><span data-stu-id="74ce5-251">If none of the Ionide commands are working, check your [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) to see if you're overriding them by accident.</span></span>
6. <span data-ttu-id="74ce5-252">Ionide makinenizde bozuk ve Yukarıdakilerin hiçbiri sorununuzu düzeltti kaldırmayı deneyin `ionide-fsharp` makinenizde dizin ve eklenti paketi yeniden yükleyin.</span><span class="sxs-lookup"><span data-stu-id="74ce5-252">If Ionide is broken on your machine and none of the above has fixed your problem, try removing the `ionide-fsharp` directory on your machine and reinstall the plugin suite.</span></span>

<span data-ttu-id="74ce5-253">Ionide yerleşik ve F # topluluk üyeleri tarafından korunan bir açık kaynak projesidir.</span><span class="sxs-lookup"><span data-stu-id="74ce5-253">Ionide is an open source project built and maintained by members of the F# community.</span></span>  <span data-ttu-id="74ce5-254">Lütfen raporu sorunları ve adresindeki katkıda bulunmaktan çekinmeyin [Ionide VSCode: FSharp GitHub deposunu](https://github.com/ionide/ionide-vscode-fsharp).</span><span class="sxs-lookup"><span data-stu-id="74ce5-254">Please report issues and feel free to contribute at the [Ionide-VSCode: FSharp GitHub repository](https://github.com/ionide/ionide-vscode-fsharp).</span></span>

<span data-ttu-id="74ce5-255">Rapor için bir sorun varsa, lütfen izleyin [bir sorun raporlama yapılırken kullanılacak günlüklerini alma yönergeleri](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span><span class="sxs-lookup"><span data-stu-id="74ce5-255">If you have an issue to report, please follow [the instructions for getting logs to use when reporting an issue](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span></span>

<span data-ttu-id="74ce5-256">Daha fazla yardım için Ionide geliştiriciler ve F # topluluğuna sorabilirsiniz [Ionide Gitter kanal](https://gitter.im/ionide/ionide-project).</span><span class="sxs-lookup"><span data-stu-id="74ce5-256">You can also ask for further help from the Ionide developers and F# community in the [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span></span>

## <a name="next-steps"></a><span data-ttu-id="74ce5-257">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="74ce5-257">Next steps</span></span>

<span data-ttu-id="74ce5-258">F # ve dil özellikleri hakkında daha fazla bilgi için kullanıma [Tur, F #](../tour.md).</span><span class="sxs-lookup"><span data-stu-id="74ce5-258">To learn more about F# and the features of the language, check out [Tour of F#](../tour.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="74ce5-259">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74ce5-259">See also</span></span>

[<span data-ttu-id="74ce5-260">F# Turu</span><span class="sxs-lookup"><span data-stu-id="74ce5-260">Tour of F#</span></span>](../tour.md)

[<span data-ttu-id="74ce5-261">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="74ce5-261">F# Language Reference</span></span>](../language-reference/index.md)

[<span data-ttu-id="74ce5-262">İşlevler</span><span class="sxs-lookup"><span data-stu-id="74ce5-262">Functions</span></span>](../language-reference/functions/index.md)

[<span data-ttu-id="74ce5-263">Modüller</span><span class="sxs-lookup"><span data-stu-id="74ce5-263">Modules</span></span>](../language-reference/modules.md)

[<span data-ttu-id="74ce5-264">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="74ce5-264">Namespaces</span></span>](../language-reference/namespaces.md)

[<span data-ttu-id="74ce5-265">Ionide-VSCode: FSharp</span><span class="sxs-lookup"><span data-stu-id="74ce5-265">Ionide-VSCode: FSharp</span></span>](https://github.com/ionide/ionide-vscode-fsharp)
