---
title: C# ve Visual Studio Code kullanmaya başlama
description: Visual Studio Code'u kullanarak C#'daki ilk .NET Core uygulamanızı nasıl oluşturup hata ayıklayarak hata ayıklamayı öğrenin.
author: kendrahavens
ms.date: 12/05/2018
ms.openlocfilehash: 6722b97cee5ca3672c9dddece6e61f4d13de05a9
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805819"
---
# <a name="get-started-with-c-and-visual-studio-code"></a><span data-ttu-id="dacb8-103">C# ve Visual Studio Code kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="dacb8-103">Get started with C# and Visual Studio Code</span></span>

<span data-ttu-id="dacb8-104">.NET Core, Windows, Linux ve macOS'ta çalışan uygulamalar oluşturmak için size hızlı ve modüler bir platform sağlar.</span><span class="sxs-lookup"><span data-stu-id="dacb8-104">.NET Core gives you a fast and modular platform for creating applications that run on Windows, Linux, and macOS.</span></span> <span data-ttu-id="dacb8-105">C# IntelliSense (akıllı kod tamamlama) ve hata ayıklama için tam destek ile güçlü bir düzenleme deneyimi elde etmek için C# uzantısı ile Visual Studio Code kullanın.</span><span class="sxs-lookup"><span data-stu-id="dacb8-105">Use Visual Studio Code with the C# extension to get a powerful editing experience with full support for C# IntelliSense (smart code completion) and debugging.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dacb8-106">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="dacb8-106">Prerequisites</span></span>

1. <span data-ttu-id="dacb8-107">[Visual Studio Kodunu](https://code.visualstudio.com/)Yükleyin.</span><span class="sxs-lookup"><span data-stu-id="dacb8-107">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
2. <span data-ttu-id="dacb8-108">[.NET Çekirdek SDK'yı](https://dotnet.microsoft.com/download)yükleyin.</span><span class="sxs-lookup"><span data-stu-id="dacb8-108">Install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>
3. <span data-ttu-id="dacb8-109">Visual Studio Code için [C# uzantısını](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) yükleyin.</span><span class="sxs-lookup"><span data-stu-id="dacb8-109">Install the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) for Visual Studio Code.</span></span> <span data-ttu-id="dacb8-110">Visual Studio Code uzantılarının nasıl yüklenir hakkında daha fazla bilgi için [VS Code Extension Marketplace'e](https://code.visualstudio.com/docs/editor/extension-gallery)bakın.</span><span class="sxs-lookup"><span data-stu-id="dacb8-110">For more information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>

## <a name="hello-world"></a><span data-ttu-id="dacb8-111">Hello World</span><span class="sxs-lookup"><span data-stu-id="dacb8-111">Hello World</span></span>

<span data-ttu-id="dacb8-112">.NET Core'da basit bir "Hello World" programı ile başlayalım:</span><span class="sxs-lookup"><span data-stu-id="dacb8-112">Let's get started with a simple "Hello World" program on .NET Core:</span></span>

1. <span data-ttu-id="dacb8-113">Bir proje açın:</span><span class="sxs-lookup"><span data-stu-id="dacb8-113">Open a project:</span></span>

    - <span data-ttu-id="dacb8-114">Visual Studio Code'u açın.</span><span class="sxs-lookup"><span data-stu-id="dacb8-114">Open Visual Studio Code.</span></span>
    - <span data-ttu-id="dacb8-115">Sol menüdeki Explorer simgesine tıklayın ve ardından **Klasörü Aç'ı**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="dacb8-115">Click on the Explorer icon on the left menu and then click **Open Folder**.</span></span>
    - <span data-ttu-id="dacb8-116">C# projenizin içinde olmasını istediğiniz klasörü açmak için ana menüden **Dosya** > **Aç Klasörünü** seçin ve **Klasörseç'e**tıklayın.</span><span class="sxs-lookup"><span data-stu-id="dacb8-116">Select **File** > **Open Folder** from the main menu to open the folder you want your C# project to be in and click **Select Folder**.</span></span> <span data-ttu-id="dacb8-117">Örneğin, *HelloWorld*adlı projemiz için bir klasör oluşturuyoruz.</span><span class="sxs-lookup"><span data-stu-id="dacb8-117">For our example, we're creating a folder for our project named *HelloWorld*.</span></span>

      ![Visual Studio Code açık klasör](media/with-visual-studio-code/vs-code-open-folder.png)

2. <span data-ttu-id="dacb8-119">Bir C# projesini başlatma:</span><span class="sxs-lookup"><span data-stu-id="dacb8-119">Initialize a C# project:</span></span>

    - <span data-ttu-id="dacb8-120">Ana menüden **View** > Terminalini seçerek Visual Studio Kodu'ndan**Terminal'i** açın.</span><span class="sxs-lookup"><span data-stu-id="dacb8-120">Open the Terminal from Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>
    - <span data-ttu-id="dacb8-121">Terminal penceresinde, `dotnet new console`yazın.</span><span class="sxs-lookup"><span data-stu-id="dacb8-121">In the terminal window, type `dotnet new console`.</span></span>
    - <span data-ttu-id="dacb8-122">Bu komut, zaten yazılmış basit bir "Hello World" programı ile klasörünüzde *bir Program.cs* dosyası oluşturur, *HelloWorld.csproj*adlı bir C# proje dosyası ile birlikte.</span><span class="sxs-lookup"><span data-stu-id="dacb8-122">This command creates a *Program.cs* file in your folder with a simple "Hello World" program already written, along with a C# project file named *HelloWorld.csproj*.</span></span>

      ![Dotnet yeni komutu](media/with-visual-studio-code/dotnet-new-command.png)

3. <span data-ttu-id="dacb8-124">Yapı varlıklarını çözümle:</span><span class="sxs-lookup"><span data-stu-id="dacb8-124">Resolve the build assets:</span></span>

    - <span data-ttu-id="dacb8-125">**.NET Core 1.x** `dotnet restore`, türü için .</span><span class="sxs-lookup"><span data-stu-id="dacb8-125">For **.NET Core 1.x**, type `dotnet restore`.</span></span> <span data-ttu-id="dacb8-126">Çalışan, `dotnet restore` projenizi oluşturmak için gereken .NET Core paketlerine erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="dacb8-126">Running `dotnet restore` gives you access to the  required .NET Core packages that are needed to build your project.</span></span>

      ![Dotnet geri yükleme komutu](media/with-visual-studio-code/dotnet-restore-command.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. <span data-ttu-id="dacb8-128">"Hello World" programını çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="dacb8-128">Run the "Hello World" program:</span></span>

    - <span data-ttu-id="dacb8-129">`dotnet run` yazın.</span><span class="sxs-lookup"><span data-stu-id="dacb8-129">Type `dotnet run`.</span></span>

      ![Dotnet çalıştır komutu](media/with-visual-studio-code/dotnet-run-command.png)

<span data-ttu-id="dacb8-131">Ayrıca [Windows,](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core) [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS)veya [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu)daha fazla kurulum yardım için kısa bir video öğretici izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dacb8-131">You can also watch a short video tutorial for further setup help on [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS), or [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span>

## <a name="debug"></a><span data-ttu-id="dacb8-132">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="dacb8-132">Debug</span></span>

1. <span data-ttu-id="dacb8-133">Üzerine tıklayarak *Program.cs* açın.</span><span class="sxs-lookup"><span data-stu-id="dacb8-133">Open *Program.cs* by clicking on it.</span></span> <span data-ttu-id="dacb8-134">Visual Studio Code'da c# dosyasını ilk açtığınızda, [OmniSharp](https://www.omnisharp.net/) editöre yüklenir.</span><span class="sxs-lookup"><span data-stu-id="dacb8-134">The first time you open a C# file in Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) loads in the editor.</span></span>

    ![Program.cs dosyasını açma](media/with-visual-studio-code/open-program-cs.png)

2. <span data-ttu-id="dacb8-136">Visual Studio Code, uygulamanızı oluşturmak ve hata ayıklamak için eksik varlıkları eklemenizi ister.</span><span class="sxs-lookup"><span data-stu-id="dacb8-136">Visual Studio Code should prompt you to add the missing assets to build and debug your app.</span></span> <span data-ttu-id="dacb8-137">**Evet'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="dacb8-137">Select **Yes**.</span></span>

    ![Eksik varlıklar için komut istemi](media/with-visual-studio-code/missing-assets.png)

3. <span data-ttu-id="dacb8-139">Hata Ayıklama görünümünü açmak için sol taraftaki menüdeki Hata Ayıklama simgesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="dacb8-139">To open the Debug view, click on the Debugging icon on the left side menu.</span></span>

    ![Visual Studio Code'da Hata Ayıklama sekmesini açma](media/with-visual-studio-code/open-debug-tab.png)

4. <span data-ttu-id="dacb8-141">Bölmenin üst kısmındayeşil oku bulun.</span><span class="sxs-lookup"><span data-stu-id="dacb8-141">Locate the green arrow at the top of the pane.</span></span> <span data-ttu-id="dacb8-142">Yanındaki açılır bırakmanın **.NET Core Launch (konsol)** seçildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="dacb8-142">Make sure the drop-down next to it has **.NET Core Launch (console)** selected.</span></span>

    ![Visual Studio Code'da .NET Core'un seçilmesi](media/with-visual-studio-code/select-net-core.png)

5. <span data-ttu-id="dacb8-144">**Düzenleyici kenar boşluğuna**tıklayarak projenize bir kesme noktası ekleyin , editördeki satır numaralarının solundaki boşluk, satır 9'un yanında, veya metin imlecini düzenleyicideki 9 satıra taşıyın ve <kbd>F9</kbd>tuşuna basın .</span><span class="sxs-lookup"><span data-stu-id="dacb8-144">Add a breakpoint to your project by clicking on the **editor margin**, which is the space on the left of the line numbers in the editor, next to line 9, or move the text cursor onto line 9 in the editor and  press <kbd>F9</kbd>.</span></span>

    ![Kesme Noktası Ayarlama](media/with-visual-studio-code/set-breakpoint-vs-code.png)

6. <span data-ttu-id="dacb8-146">Hata ayıklamaya başlamak için <kbd>F5</kbd> tuşuna basın veya yeşil oku seçin.</span><span class="sxs-lookup"><span data-stu-id="dacb8-146">To start debugging, press <kbd>F5</kbd> or select the green arrow.</span></span> <span data-ttu-id="dacb8-147">Hata ayıklama, önceki adımda ayarladığınız kesme noktasına ulaştığında programınızın yürütülmesini durdurur.</span><span class="sxs-lookup"><span data-stu-id="dacb8-147">The debugger stops execution of your program when it reaches the breakpoint you set in the previous step.</span></span>
    - <span data-ttu-id="dacb8-148">Hata ayıklama sırasında, yerel değişkenlerinizi sol üst bölmede görüntüleyebilir veya hata ayıklama konsolunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dacb8-148">While debugging, you can view your local variables in the top-left pane or use the debug console.</span></span>

7. <span data-ttu-id="dacb8-149">Hata ayıklama devam etmek için üstteki mavi oku seçin veya durdurmak için üstteki kırmızı kareyi seçin.</span><span class="sxs-lookup"><span data-stu-id="dacb8-149">Select the blue arrow at the top to continue debugging, or select the red square at the top to stop.</span></span>

    ![Visual Studio Code'da Çalıştır ve Hata Ayıklama](media/with-visual-studio-code/run-debug-vs-code.png)

> [!TIP]
> <span data-ttu-id="dacb8-151">Visual Studio Code'da OmniSharp ile .NET Core hata ayıklama hakkında daha fazla bilgi ve sorun giderme ipuçları için [.NET Core hata ayıklayıcısını ayarlama yönergelerine](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="dacb8-151">For more information and troubleshooting tips on .NET Core debugging with OmniSharp in Visual Studio Code, see [Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="add-a-class"></a><span data-ttu-id="dacb8-152">Sınıf ekleme</span><span class="sxs-lookup"><span data-stu-id="dacb8-152">Add a class</span></span>

1. <span data-ttu-id="dacb8-153">Yeni bir sınıf eklemek için VSCode Explorer'a sağ tıklayın ve **Yeni Dosya'yı**seçin.</span><span class="sxs-lookup"><span data-stu-id="dacb8-153">To add a new class, right-click in the VSCode Explorer and select **New File**.</span></span> <span data-ttu-id="dacb8-154">Bu, VSCode'da açtığınız klasöre yeni bir dosya ekler.</span><span class="sxs-lookup"><span data-stu-id="dacb8-154">This adds a new file to the folder you have open in VSCode.</span></span>
2. <span data-ttu-id="dacb8-155">Dosyanızı *MyClass.cs.*</span><span class="sxs-lookup"><span data-stu-id="dacb8-155">Name your file *MyClass.cs*.</span></span> <span data-ttu-id="dacb8-156">Bir csharp dosyası `.cs` olarak tanınması için sonunda bir uzantısı ile kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="dacb8-156">You must save it with a `.cs` extension at the end for it to be recognized as a csharp file.</span></span>
3. <span data-ttu-id="dacb8-157">Birinci sınıf oluşturmak için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="dacb8-157">Add the code below to create your first class.</span></span> <span data-ttu-id="dacb8-158">*Program.cs* dosyanızdan başvuruda bulunabilmek için doğru ad alanını eklediğinizden emin olun:</span><span class="sxs-lookup"><span data-stu-id="dacb8-158">Make sure to include the correct namespace so you can reference it from your *Program.cs* file:</span></span>

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

4. <span data-ttu-id="dacb8-159">Aşağıdaki kodu ekleyerek *Program.cs* ana yönteminizden yeni sınıfınızı arayın:</span><span class="sxs-lookup"><span data-stu-id="dacb8-159">Call your new class from your main method in *Program.cs* by adding the code below:</span></span>

    ```csharp
    using System;

    namespace HelloWorld
    {
        class Program
        {
            static void Main(string[] args)
            {
                var c1 = new MyClass();
                Console.WriteLine($"Hello World! {c1.ReturnMessage()}");
            }
        }
    }
    ```

5. <span data-ttu-id="dacb8-160">Değişikliklerinizi kaydedin ve programınızı yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="dacb8-160">Save your changes and run your program again.</span></span> <span data-ttu-id="dacb8-161">Yeni ileti eklenen dize ile görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="dacb8-161">The new message should appear with the appended string.</span></span>

    ```dotnetcli
    dotnet run
    ```

    <span data-ttu-id="dacb8-162">Aşağıdaki çıkışı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="dacb8-162">You get the following output:</span></span>

    ```console
    Hello World! Happy coding!
    ```

## <a name="faq"></a><span data-ttu-id="dacb8-163">SSS</span><span class="sxs-lookup"><span data-stu-id="dacb8-163">FAQ</span></span>

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a><span data-ttu-id="dacb8-164">Visual Studio Code'da C# inşa etmek ve hata ayıklamak için gerekli varlıkları kaçırıyorum.</span><span class="sxs-lookup"><span data-stu-id="dacb8-164">I'm missing required assets to build and debug C# in Visual Studio Code.</span></span> <span data-ttu-id="dacb8-165">Hata ayıklamam "Yapılandırma Yok" diyor.</span><span class="sxs-lookup"><span data-stu-id="dacb8-165">My debugger says "No Configuration."</span></span>

<span data-ttu-id="dacb8-166">Visual Studio Code C# uzantısı, sizin için oluşturmak ve hata ayıklamak için varlıklar oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="dacb8-166">The Visual Studio Code C# extension can generate assets to build and debug for you.</span></span> <span data-ttu-id="dacb8-167">Visual Studio Code, bir C# projesini ilk açtığınızda bu varlıkları oluşturmanızı ister.</span><span class="sxs-lookup"><span data-stu-id="dacb8-167">Visual Studio Code prompts you to generate these assets when you first open a C# project.</span></span> <span data-ttu-id="dacb8-168">O zaman varlık oluşturmadıysanız, komut paletini açarak **(komut paletini görüntüle >)** ve ">.NET: Oluşturma ve Hata Ayıklama için Varlıklar Oluştur" yazarak bu komutu çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dacb8-168">If you didn't generate assets then, you can still run this command by opening the Command Palette (**View > Command Palette**) and typing ">.NET: Generate Assets for Build and Debug".</span></span> <span data-ttu-id="dacb8-169">Bunu seçmek, *.vscode*, *launch.json*ve *tasks.json* yapılandırma dosyaları için ihtiyacınız olan dosyaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dacb8-169">Selecting this generates the *.vscode*, *launch.json*, and *tasks.json* configuration files that you need.</span></span>

## <a name="see-also"></a><span data-ttu-id="dacb8-170">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dacb8-170">See also</span></span>

- [<span data-ttu-id="dacb8-171">Görsel Stüdyo Kodu Ayarlama</span><span class="sxs-lookup"><span data-stu-id="dacb8-171">Setting up Visual Studio Code</span></span>](https://code.visualstudio.com/docs/setup/setup-overview)
- [<span data-ttu-id="dacb8-172">Visual Studio Code'da Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="dacb8-172">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/editor/debugging)
