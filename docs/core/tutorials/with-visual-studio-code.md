---
title: C# ve Visual Studio Code kullanmaya başlama
description: Oluşturma ve C# Visual Studio Code kullanarak ilk .NET Core uygulamanızı hata ayıklama hakkında bilgi edinin.
author: kendrahavens
ms.date: 12/05/2018
ms.custom: seodec18
ms.openlocfilehash: d23f095454a24d67c2b9fb7a0f090fb08ff9e8bb
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59613453"
---
# <a name="get-started-with-c-and-visual-studio-code"></a><span data-ttu-id="c8d20-103">C# ve Visual Studio Code kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="c8d20-103">Get started with C# and Visual Studio Code</span></span>

<span data-ttu-id="c8d20-104">.NET core Windows, Linux ve macOS üzerinde çalışan uygulamalar oluşturmak için hızlı ve modüler bir platform sunar.</span><span class="sxs-lookup"><span data-stu-id="c8d20-104">.NET Core gives you a fast and modular platform for creating applications that run on Windows, Linux, and macOS.</span></span> <span data-ttu-id="c8d20-105">Visual Studio Code C# uzantısı ile bir güçlü düzenleme deneyimi ile C# IntelliSense (Akıllı kod tamamlama) için tam destek ve hata ayıklama almak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="c8d20-105">Use Visual Studio Code with the C# extension to get a powerful editing experience with full support for C# IntelliSense (smart code completion) and debugging.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c8d20-106">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="c8d20-106">Prerequisites</span></span>

1. <span data-ttu-id="c8d20-107">Yükleme [Visual Studio Code'u](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="c8d20-107">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
2. <span data-ttu-id="c8d20-108">Yükleme [.NET Core SDK'sı](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="c8d20-108">Install the [.NET Core SDK](https://www.microsoft.com/net/download/core).</span></span>
3. <span data-ttu-id="c8d20-109">Yükleme [C# uzantısı](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) Visual Studio Code için.</span><span class="sxs-lookup"><span data-stu-id="c8d20-109">Install the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) for Visual Studio Code.</span></span> <span data-ttu-id="c8d20-110">Visual Studio Code uzantılarını yükleme hakkında daha fazla bilgi için bkz. [VS Code uzantı Marketi](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="c8d20-110">For more information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>

## <a name="hello-world"></a><span data-ttu-id="c8d20-111">Merhaba Dünya</span><span class="sxs-lookup"><span data-stu-id="c8d20-111">Hello World</span></span>

<span data-ttu-id="c8d20-112">.NET Core üzerinde basit bir "Merhaba Dünya" programıyla Haydi başlayalım:</span><span class="sxs-lookup"><span data-stu-id="c8d20-112">Let's get started with a simple "Hello World" program on .NET Core:</span></span>

1. <span data-ttu-id="c8d20-113">Bir proje açın:</span><span class="sxs-lookup"><span data-stu-id="c8d20-113">Open a project:</span></span>

    * <span data-ttu-id="c8d20-114">Visual Studio Code'u açın.</span><span class="sxs-lookup"><span data-stu-id="c8d20-114">Open Visual Studio Code.</span></span>
    * <span data-ttu-id="c8d20-115">Soldaki menünün Gezgini simgesine tıklayın ve ardından **Klasör Aç**.</span><span class="sxs-lookup"><span data-stu-id="c8d20-115">Click on the Explorer icon on the left menu and then click **Open Folder**.</span></span>
    * <span data-ttu-id="c8d20-116">Seçin **dosya** > **klasörünü Aç** olması ve C# projenize istediğiniz klasörü açmak için ana menüden **Klasör Seç**.</span><span class="sxs-lookup"><span data-stu-id="c8d20-116">Select **File** > **Open Folder** from the main menu to open the folder you want your C# project to be in and click **Select Folder**.</span></span> <span data-ttu-id="c8d20-117">Bizim örneğimizde, Projemizin için adlı bir klasör oluşturmakta olduğumuz *HelloWorld*.</span><span class="sxs-lookup"><span data-stu-id="c8d20-117">For our example, we're creating a folder for our project named *HelloWorld*.</span></span>

      ![Visual Studio Code klasörü aç](media/with-visual-studio-code/vs-code-open-folder.png)

2. <span data-ttu-id="c8d20-119">Bir C# projesi başlatın:</span><span class="sxs-lookup"><span data-stu-id="c8d20-119">Initialize a C# project:</span></span>
    * <span data-ttu-id="c8d20-120">Seçerek Visual Studio Code'dan tümleşik Terminalini açın **görünümü** > **tümleşik Terminalini** ana menüden.</span><span class="sxs-lookup"><span data-stu-id="c8d20-120">Open the Integrated Terminal from Visual Studio Code by selecting **View** > **Integrated Terminal** from the main menu.</span></span>
    * <span data-ttu-id="c8d20-121">Terminal penceresinde şunu yazın `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="c8d20-121">In the terminal window, type `dotnet new console`.</span></span>
    * <span data-ttu-id="c8d20-122">Bu komut, oluşturur bir `Program.cs` önceden yazılmış, adlı bir C# proje dosyası ile birlikte basit "Merhaba Dünya" programıyla klasörünüzdeki dosya `HelloWorld.csproj`.</span><span class="sxs-lookup"><span data-stu-id="c8d20-122">This command creates a `Program.cs` file in your folder with a simple "Hello World" program already written, along with a C# project file named `HelloWorld.csproj`.</span></span>

      ![Dotnet yeni komutu](media/with-visual-studio-code/dotnet-new-command.png)

3. <span data-ttu-id="c8d20-124">Derleme varlıkları çözümlemeye:</span><span class="sxs-lookup"><span data-stu-id="c8d20-124">Resolve the build assets:</span></span>

    * <span data-ttu-id="c8d20-125">İçin **.NET Core 1.x**, türü `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="c8d20-125">For **.NET Core 1.x**, type `dotnet restore`.</span></span> <span data-ttu-id="c8d20-126">Çalışan `dotnet restore` projenizi yapılandırmak için gereken gerekli .NET Core paketleri erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8d20-126">Running `dotnet restore` gives you access to the  required .NET Core packages that are needed to build your project.</span></span>

      ![Dotnet restore komutu](media/with-visual-studio-code/dotnet-restore-command.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. <span data-ttu-id="c8d20-128">"Hello World" programı çalıştır:</span><span class="sxs-lookup"><span data-stu-id="c8d20-128">Run the "Hello World" program:</span></span>

    * <span data-ttu-id="c8d20-129">`dotnet run`yazın.</span><span class="sxs-lookup"><span data-stu-id="c8d20-129">Type `dotnet run`.</span></span>

      ![Dotnet komutu çalıştırın](media/with-visual-studio-code/dotnet-run-command.png)

<span data-ttu-id="c8d20-131">Üzerinde ek kurulum Yardım almak için kısa bir video öğreticisini izleyebilirsiniz [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS), veya [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span><span class="sxs-lookup"><span data-stu-id="c8d20-131">You can also watch a short video tutorial for further setup help on [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS), or [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span>

## <a name="debug"></a><span data-ttu-id="c8d20-132">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="c8d20-132">Debug</span></span>

1. <span data-ttu-id="c8d20-133">Açık *Program.cs* üzerine tıklayarak.</span><span class="sxs-lookup"><span data-stu-id="c8d20-133">Open *Program.cs* by clicking on it.</span></span> <span data-ttu-id="c8d20-134">Visual Studio Code'da bir C# dosyası açın ilk kez [OmniSharp](https://www.omnisharp.net/) düzenleyicide yükler.</span><span class="sxs-lookup"><span data-stu-id="c8d20-134">The first time you open a C# file in Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) loads in the editor.</span></span>

    ![Program.cs dosyasını açın](media/with-visual-studio-code/open-program-cs.png)

2. <span data-ttu-id="c8d20-136">Visual Studio Code, oluşturmak ve uygulamanızda hata ayıklama için eksik varlıkları eklemek isteyecektir.</span><span class="sxs-lookup"><span data-stu-id="c8d20-136">Visual Studio Code should prompt you to add the missing assets to build and debug your app.</span></span> <span data-ttu-id="c8d20-137">Seçin **Evet**.</span><span class="sxs-lookup"><span data-stu-id="c8d20-137">Select **Yes**.</span></span>

    ![Eksik varlıklar sor](media/with-visual-studio-code/missing-assets.png)

3. <span data-ttu-id="c8d20-139">Hata ayıklama görünümünü açmak için sol taraftaki menüde hata ayıklama simgesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c8d20-139">To open the Debug view, click on the Debugging icon on the left side menu.</span></span>

    ![Visual Studio Codee içinde hata ayıklama sekmesini açın](media/with-visual-studio-code/open-debug-tab.png)

4. <span data-ttu-id="c8d20-141">Yeşil ok Bölmenin üst kısmındaki bulun.</span><span class="sxs-lookup"><span data-stu-id="c8d20-141">Locate the green arrow at the top of the pane.</span></span> <span data-ttu-id="c8d20-142">Yanındaki açılan sahip olduğundan emin olun `.NET Core Launch (console)` seçili.</span><span class="sxs-lookup"><span data-stu-id="c8d20-142">Make sure the drop-down next to it has `.NET Core Launch (console)` selected.</span></span>

    ![.NET Core Visual Studio Code'da seçme](media/with-visual-studio-code/select-net-core.png)

5. <span data-ttu-id="c8d20-144">Tıklayarak bir kesme noktası projenize ekleyin **Düzenleyici kenar**, sol tarafında 9. satıra yanındaki düzenleyicide satır numaralarını alanı veya metin imleç 9. satırına Düzenleyicisi ve tuşuna üzerine <kbd>F9</kbd>.</span><span class="sxs-lookup"><span data-stu-id="c8d20-144">Add a breakpoint to your project by clicking on the **editor margin**, which is the space on the left of the line numbers in the editor, next to line 9, or move the text cursor onto line 9 in the editor and  press <kbd>F9</kbd>.</span></span>

    ![Bir kesme noktası ayarlama](media/with-visual-studio-code/set-breakpoint-vs-code.png)

6. <span data-ttu-id="c8d20-146">Hata ayıklamayı başlatmak için seçin <kbd>F5</kbd> veya yeşil oka.</span><span class="sxs-lookup"><span data-stu-id="c8d20-146">To start debugging, select <kbd>F5</kbd> or the green arrow.</span></span> <span data-ttu-id="c8d20-147">Önceki adımda ayarladığınız kesme noktasına ulaştığında hata ayıklayıcı, programınızın yürütülmesini durdurur.</span><span class="sxs-lookup"><span data-stu-id="c8d20-147">The debugger stops execution of your program when it reaches the breakpoint you set in the previous step.</span></span>
    * <span data-ttu-id="c8d20-148">Hata ayıklarken, üst sol bölmede, yerel değişkenleri görüntüleyebilir veya hata ayıklama konsolunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="c8d20-148">While debugging, you can view your local variables in the top left pane or use the debug console.</span></span>

7. <span data-ttu-id="c8d20-149">Hata ayıklamaya devam etmek için üstteki mavi oku seçin veya durdurmak için kırmızı kareyi üst seçin.</span><span class="sxs-lookup"><span data-stu-id="c8d20-149">Select the blue arrow at the top to continue debugging, or select the red square at the top to stop.</span></span>

    ![Çalıştırın ve Visual Studio Code'da Hata Ayıkla](media/with-visual-studio-code/run-debug-vs-code.png)

> [!TIP]
> <span data-ttu-id="c8d20-151">Daha fazla bilgi ve sorun giderme ipuçları, .NET Core ile OmniSharp Visual Studio code'da hata ayıklama için bkz: [.NET Core Hata Ayıklayıcısı ' ayarlamaya yönelik yönergeler](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span><span class="sxs-lookup"><span data-stu-id="c8d20-151">For more information and troubleshooting tips on .NET Core debugging with OmniSharp in Visual Studio Code, see [Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="add-a-class"></a><span data-ttu-id="c8d20-152">Bir sınıf ekleyin</span><span class="sxs-lookup"><span data-stu-id="c8d20-152">Add a class</span></span>

1. <span data-ttu-id="c8d20-153">Yeni bir sınıf sağ tıklatın VSCode Gezgini'nde ekleyin ve seçmek için **yeni dosya**.</span><span class="sxs-lookup"><span data-stu-id="c8d20-153">To add a new class right-click in the VSCode Explorer and select **New File**.</span></span> <span data-ttu-id="c8d20-154">Bu, VSCode içinde açtığınız klasöre yeni bir dosya ekler.</span><span class="sxs-lookup"><span data-stu-id="c8d20-154">This adds a new file to the folder you have open in VSCode.</span></span>
2. <span data-ttu-id="c8d20-155">Dosyanızın adı `MyClass.cs`.</span><span class="sxs-lookup"><span data-stu-id="c8d20-155">Name your file `MyClass.cs`.</span></span> <span data-ttu-id="c8d20-156">İle kaydetmelisiniz bir `.cs` uzantısı için bir csharp dosyası olarak tanınması için sonunda.</span><span class="sxs-lookup"><span data-stu-id="c8d20-156">You must save it with a `.cs` extension at the end for it to be recognized as a csharp file.</span></span>
3. <span data-ttu-id="c8d20-157">İlk sınıfınıza oluşturmak için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c8d20-157">Add the code below to create your first class.</span></span> <span data-ttu-id="c8d20-158">Buradan başvurabilmeniz için doğru ad alanını eklediğinizden emin olun, `Program.cs` dosya.</span><span class="sxs-lookup"><span data-stu-id="c8d20-158">Make sure to include the correct namespace so you can reference it from your `Program.cs` file.</span></span>

``` csharp
using System;

namespace HelloWorld
{
    public class MyClass
    {
        public string ReturnMessage()
        {
            return "Happy coding!";
        }
    }
}
```

4. <span data-ttu-id="c8d20-159">Yeni sınıfınıza ana yönteminiz çağırmanıza `Program.cs` aşağıdaki kodu ekleyerek.</span><span class="sxs-lookup"><span data-stu-id="c8d20-159">Call your new class from your main method in `Program.cs` by adding the code below.</span></span>

```csharp
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            MyClass c1 = new MyClass();
            Console.WriteLine($"Hello World! {c1.ReturnMessage()}");
        }
    }
}
```

5. <span data-ttu-id="c8d20-160">Yaptığınız değişiklikleri kaydedin ve programınızı tekrar çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c8d20-160">Save your changes and run your program again.</span></span> <span data-ttu-id="c8d20-161">Eklenen dize ile yeni iletinin görüntülenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="c8d20-161">The new message should appear with the appended string.</span></span>

```console
> dotnet run
Hello World! Happy coding!
```

## <a name="faq"></a><span data-ttu-id="c8d20-162">SSS</span><span class="sxs-lookup"><span data-stu-id="c8d20-162">FAQ</span></span>

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a><span data-ttu-id="c8d20-163">Ben oluşturmak ve C# Visual Studio code'da hata ayıklama için gerekli varlıkları eksik.</span><span class="sxs-lookup"><span data-stu-id="c8d20-163">I'm missing required assets to build and debug C# in Visual Studio Code.</span></span> <span data-ttu-id="c8d20-164">My hata ayıklayıcı "Yapılandırması yok." diyor.</span><span class="sxs-lookup"><span data-stu-id="c8d20-164">My debugger says "No Configuration."</span></span>

<span data-ttu-id="c8d20-165">Visual Studio kodu C# uzantısı oluşturun ve sizin için hata ayıklama için varlıklar oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="c8d20-165">The Visual Studio Code C# extension can generate assets to build and debug for you.</span></span> <span data-ttu-id="c8d20-166">Visual Studio Code bir C# projesi ilk kez açtığınızda, bu varlıkları oluşturmak isteyip istemediğinizi sorar.</span><span class="sxs-lookup"><span data-stu-id="c8d20-166">Visual Studio Code prompts you to generate these assets when you first open a C# project.</span></span> <span data-ttu-id="c8d20-167">Varlık oluşturma olmadı sonra komut paletini açıp bu komutu yine de çalıştırabilirsiniz, (**Görüntüle > komut paleti**) yazarak "> .NET: Varlık oluşturma ve hata ayıklama için oluşturma".</span><span class="sxs-lookup"><span data-stu-id="c8d20-167">If you didn't generate assets then, you can still run this command by opening the Command Palette (**View > Command Palette**) and typing ">.NET: Generate Assets for Build and Debug".</span></span> <span data-ttu-id="c8d20-168">Bu seçeneğin seçilmesi gereken .vscode launch.json ve tasks.json yapılandırma dosyalarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c8d20-168">Selecting this generates the .vscode, launch.json, and tasks.json configuration files that you need.</span></span>

## <a name="see-also"></a><span data-ttu-id="c8d20-169">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8d20-169">See also</span></span>

- [<span data-ttu-id="c8d20-170">Visual Studio Code ayarlama</span><span class="sxs-lookup"><span data-stu-id="c8d20-170">Setting up Visual Studio Code</span></span>](https://code.visualstudio.com/docs/setup/setup-overview)
- [<span data-ttu-id="c8d20-171">Visual Studio Code'da hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="c8d20-171">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/editor/debugging)
