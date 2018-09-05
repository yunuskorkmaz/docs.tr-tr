---
title: C# ve Visual Studio Code - C# Kılavuzu ile çalışmaya başlama
description: Oluşturma ve C# Visual Studio Code kullanarak ilk .NET Core uygulamanızı hata ayıklama hakkında bilgi edinin.
author: kendrahavens
ms.author: mairaw
ms.date: 09/27/2017
ms.openlocfilehash: 321edcebdea141b7290fa57b47c8d9fc91d3521c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43538886"
---
# <a name="get-started-with-c-and-visual-studio-code"></a><span data-ttu-id="1de61-103">C# ve Visual Studio Code kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="1de61-103">Get Started with C# and Visual Studio Code</span></span>

<span data-ttu-id="1de61-104">.NET core Windows, Linux ve macOS üzerinde çalışan uygulamalar oluşturmak için hızlı ve modüler bir platform sunar.</span><span class="sxs-lookup"><span data-stu-id="1de61-104">.NET Core gives you a fast and modular platform for creating applications that run on Windows, Linux, and macOS.</span></span> <span data-ttu-id="1de61-105">Visual Studio Code C# uzantısı ile bir güçlü düzenleme deneyimi ile C# IntelliSense (Akıllı kod tamamlama) için tam destek ve hata ayıklama almak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="1de61-105">Use Visual Studio Code with the C# extension to get a powerful editing experience with full support for C# IntelliSense (smart code completion) and debugging.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1de61-106">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="1de61-106">Prerequisites</span></span>

1. <span data-ttu-id="1de61-107">Yükleme [Visual Studio Code'u](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="1de61-107">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
2. <span data-ttu-id="1de61-108">Yükleme [.NET Core SDK'sı](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="1de61-108">Install the [.NET Core SDK](https://www.microsoft.com/net/download/core).</span></span>
3. <span data-ttu-id="1de61-109">Yükleme [C# uzantısı](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) Visual Studio Code için.</span><span class="sxs-lookup"><span data-stu-id="1de61-109">Install the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) for Visual Studio Code.</span></span> <span data-ttu-id="1de61-110">Visual Studio Code uzantılarını yükleme hakkında daha fazla bilgi için bkz. [VS Code uzantı Marketi](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="1de61-110">For more information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>

## <a name="hello-world"></a><span data-ttu-id="1de61-111">Merhaba Dünya</span><span class="sxs-lookup"><span data-stu-id="1de61-111">Hello World</span></span>

<span data-ttu-id="1de61-112">.NET Core üzerinde basit bir "Merhaba Dünya" programıyla Haydi başlayalım:</span><span class="sxs-lookup"><span data-stu-id="1de61-112">Let's get started with a simple "Hello World" program on .NET Core:</span></span>

1. <span data-ttu-id="1de61-113">Bir proje açın:</span><span class="sxs-lookup"><span data-stu-id="1de61-113">Open a project:</span></span>

    * <span data-ttu-id="1de61-114">Visual Studio Code'u açın.</span><span class="sxs-lookup"><span data-stu-id="1de61-114">Open Visual Studio Code.</span></span>
    * <span data-ttu-id="1de61-115">Soldaki menünün Gezgini simgesine tıklayın ve ardından **Klasör Aç**.</span><span class="sxs-lookup"><span data-stu-id="1de61-115">Click on the Explorer icon on the left menu and then click **Open Folder**.</span></span>
    * <span data-ttu-id="1de61-116">Seçin **dosya** > **klasörünü Aç** olması ve C# projenize istediğiniz klasörü açmak için ana menüden **Klasör Seç**.</span><span class="sxs-lookup"><span data-stu-id="1de61-116">Select **File** > **Open Folder** from the main menu to open the folder you want your C# project to be in and click **Select Folder**.</span></span> <span data-ttu-id="1de61-117">Bizim örneğimizde, Projemizin için adlı bir klasör oluşturmakta olduğumuz *HelloWorld*.</span><span class="sxs-lookup"><span data-stu-id="1de61-117">For our example, we're creating a folder for our project named *HelloWorld*.</span></span>

      ![VSCodeOpenFolder](media/with-visual-studio-code/vscodeopenfolder.png)

2. <span data-ttu-id="1de61-119">Bir C# projesi başlatın:</span><span class="sxs-lookup"><span data-stu-id="1de61-119">Initialize a C# project:</span></span>
    * <span data-ttu-id="1de61-120">Seçerek Visual Studio Code'dan tümleşik Terminalini açın **görünümü** > **tümleşik Terminalini** ana menüden.</span><span class="sxs-lookup"><span data-stu-id="1de61-120">Open the Integrated Terminal from Visual Studio Code by selecting **View** > **Integrated Terminal** from the main menu.</span></span>
    * <span data-ttu-id="1de61-121">Terminal penceresinde şunu yazın `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="1de61-121">In the terminal window, type `dotnet new console`.</span></span>
    * <span data-ttu-id="1de61-122">Bu komut, oluşturur bir `Program.cs` önceden yazılmış, adlı bir C# proje dosyası ile birlikte basit "Merhaba Dünya" programıyla klasörünüzdeki dosya `HelloWorld.csproj`.</span><span class="sxs-lookup"><span data-stu-id="1de61-122">This command creates a `Program.cs` file in your folder with a simple "Hello World" program already written, along with a C# project file named `HelloWorld.csproj`.</span></span>

      ![Dotnet yeni komutu](media/with-visual-studio-code/dotnetnew.png)

3. <span data-ttu-id="1de61-124">Derleme varlıkları çözümlemeye:</span><span class="sxs-lookup"><span data-stu-id="1de61-124">Resolve the build assets:</span></span>

    * <span data-ttu-id="1de61-125">İçin **.NET Core 1.x**, türü `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="1de61-125">For **.NET Core 1.x**, type `dotnet restore`.</span></span> <span data-ttu-id="1de61-126">Çalışan `dotnet restore` projenizi yapılandırmak için gereken gerekli .NET Core paketleri erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="1de61-126">Running `dotnet restore` gives you access to the  required .NET Core packages that are needed to build your project.</span></span>

      ![Dotnet restore komutu](media/with-visual-studio-code/dotnetrestore.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. <span data-ttu-id="1de61-128">"Hello World" programı çalıştır:</span><span class="sxs-lookup"><span data-stu-id="1de61-128">Run the "Hello World" program:</span></span>

    * <span data-ttu-id="1de61-129">Tür `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="1de61-129">Type `dotnet run`.</span></span>

      ![Dotnet komutu çalıştırın](media/with-visual-studio-code/dotnetrun.png)

<span data-ttu-id="1de61-131">Üzerinde ek kurulum Yardım almak için kısa bir video öğreticisini izleyebilirsiniz [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS), veya [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span><span class="sxs-lookup"><span data-stu-id="1de61-131">You can also watch a short video tutorial for further setup help on [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS), or [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span>

## <a name="debug"></a><span data-ttu-id="1de61-132">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="1de61-132">Debug</span></span>

1. <span data-ttu-id="1de61-133">Açık *Program.cs* üzerine tıklayarak.</span><span class="sxs-lookup"><span data-stu-id="1de61-133">Open *Program.cs* by clicking on it.</span></span> <span data-ttu-id="1de61-134">Visual Studio Code'da bir C# dosyası açın ilk kez [OmniSharp](http://www.omnisharp.net/) düzenleyicide yükler.</span><span class="sxs-lookup"><span data-stu-id="1de61-134">The first time you open a C# file in Visual Studio Code, [OmniSharp](http://www.omnisharp.net/) loads in the editor.</span></span>

    ![Program.cs dosyasını açın](media/with-visual-studio-code/opencs.png)

2. <span data-ttu-id="1de61-136">Visual Studio Code, oluşturmak ve uygulamanızda hata ayıklama için eksik varlıkları eklemek isteyecektir.</span><span class="sxs-lookup"><span data-stu-id="1de61-136">Visual Studio Code should prompt you to add the missing assets to build and debug your app.</span></span> <span data-ttu-id="1de61-137">Seçin **Evet**.</span><span class="sxs-lookup"><span data-stu-id="1de61-137">Select **Yes**.</span></span>

    ![Eksik varlıklar sor](media/with-visual-studio-code/missing-assets.png)

3. <span data-ttu-id="1de61-139">Hata ayıklama görünümünü açmak için sol taraftaki menüde hata ayıklama simgesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1de61-139">To open the Debug view, click on the Debugging icon on the left side menu.</span></span>

    ![Hata ayıklama sekmesini açın.](media/with-visual-studio-code/opendebug.png)

4. <span data-ttu-id="1de61-141">Yeşil ok Bölmenin üst kısmındaki bulun.</span><span class="sxs-lookup"><span data-stu-id="1de61-141">Locate the green arrow at the top of the pane.</span></span> <span data-ttu-id="1de61-142">Yanındaki açılan sahip olduğundan emin olun `.NET Core Launch (console)` seçili.</span><span class="sxs-lookup"><span data-stu-id="1de61-142">Make sure the drop-down next to it has `.NET Core Launch (console)` selected.</span></span>

    ![.NET Core seçme](media/with-visual-studio-code/selectcore.png)

5. <span data-ttu-id="1de61-144">Tıklayarak bir kesme noktası projenize ekleyin **Düzenleyici kenar**, sol tarafında 9. satıra yanındaki düzenleyicide satır numaralarını alanı veya metin imleç 9. satırına Düzenleyicisi ve tuşuna üzerine <kbd>F9</kbd>.</span><span class="sxs-lookup"><span data-stu-id="1de61-144">Add a breakpoint to your project by clicking on the **editor margin**, which is the space on the left of the line numbers in the editor, next to line 9, or move the text cursor onto line 9 in the editor and  press <kbd>F9</kbd>.</span></span>

    ![Bir kesme noktası ayarlama](media/with-visual-studio-code/setbreakpoint.png)

6. <span data-ttu-id="1de61-146">Hata ayıklamayı başlatmak için seçin <kbd>F5</kbd> veya yeşil oka.</span><span class="sxs-lookup"><span data-stu-id="1de61-146">To start debugging, select <kbd>F5</kbd> or the green arrow.</span></span> <span data-ttu-id="1de61-147">Önceki adımda ayarladığınız kesme noktasına ulaştığında hata ayıklayıcı, programınızın yürütülmesini durdurur.</span><span class="sxs-lookup"><span data-stu-id="1de61-147">The debugger stops execution of your program when it reaches the breakpoint you set in the previous step.</span></span>
    * <span data-ttu-id="1de61-148">Hata ayıklarken, üst sol bölmede, yerel değişkenleri görüntüleyebilir veya hata ayıklama konsolunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="1de61-148">While debugging, you can view your local variables in the top left pane or use the debug console.</span></span>

    ![Çalıştırma ve hata ayıklama](media/with-visual-studio-code/rundebug.png)

7. <span data-ttu-id="1de61-150">Yeşil ok hata ayıklamaya devam etmek için üstteki seçin veya durdurmak için kırmızı kareyi üst seçin.</span><span class="sxs-lookup"><span data-stu-id="1de61-150">Select the green arrow at the top to continue debugging, or select the red square at the top to stop.</span></span>

> [!TIP]
> <span data-ttu-id="1de61-151">Daha fazla bilgi ve sorun giderme ipuçları, .NET Core ile OmniSharp Visual Studio code'da hata ayıklama için bkz: [.NET Core Hata Ayıklayıcısı ' ayarlamaya yönelik yönergeler](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span><span class="sxs-lookup"><span data-stu-id="1de61-151">For more information and troubleshooting tips on .NET Core debugging with OmniSharp in Visual Studio Code, see [Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="faq"></a><span data-ttu-id="1de61-152">SSS</span><span class="sxs-lookup"><span data-stu-id="1de61-152">FAQ</span></span>

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a><span data-ttu-id="1de61-153">Ben oluşturmak ve C# Visual Studio code'da hata ayıklama için gerekli varlıkları eksik.</span><span class="sxs-lookup"><span data-stu-id="1de61-153">I'm missing required assets to build and debug C# in Visual Studio Code.</span></span> <span data-ttu-id="1de61-154">My hata ayıklayıcı "Yapılandırması yok." diyor.</span><span class="sxs-lookup"><span data-stu-id="1de61-154">My debugger says "No Configuration."</span></span>

<span data-ttu-id="1de61-155">Visual Studio kodu C# uzantısı oluşturun ve sizin için hata ayıklama için varlıklar oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="1de61-155">The Visual Studio Code C# extension can generate assets to build and debug for you.</span></span> <span data-ttu-id="1de61-156">Visual Studio Code bir C# projesi ilk kez açtığınızda, bu varlıkları oluşturmak isteyip istemediğinizi sorar.</span><span class="sxs-lookup"><span data-stu-id="1de61-156">Visual Studio Code prompts you to generate these assets when you first open a C# project.</span></span> <span data-ttu-id="1de61-157">Varlık oluşturma olmadı sonra komut paletini açıp bu komutu yine de çalıştırabilirsiniz, (**Görüntüle > komut paleti**) yazarak "> .NET: derleme ve hata ayıklama için varlık oluşturma".</span><span class="sxs-lookup"><span data-stu-id="1de61-157">If you didn't generate assets then, you can still run this command by opening the Command Palette (**View > Command Palette**) and typing ">.NET: Generate Assets for Build and Debug".</span></span> <span data-ttu-id="1de61-158">Bu seçeneğin seçilmesi gereken .vscode launch.json ve tasks.json yapılandırma dosyalarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1de61-158">Selecting this generates the .vscode, launch.json, and tasks.json configuration files that you need.</span></span>

## <a name="see-also"></a><span data-ttu-id="1de61-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1de61-159">See also</span></span>

* [<span data-ttu-id="1de61-160">Visual Studio Code ayarlama</span><span class="sxs-lookup"><span data-stu-id="1de61-160">Setting up Visual Studio Code</span></span>](https://code.visualstudio.com/docs/setup/setup-overview)
* [<span data-ttu-id="1de61-161">Visual Studio Code'da hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="1de61-161">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/editor/debugging)
