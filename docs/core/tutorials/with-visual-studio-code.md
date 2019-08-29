---
title: C# ve Visual Studio Code kullanmaya başlama
description: Visual Studio Code C# kullanarak Ilk .NET Core uygulamanızı nasıl oluşturacağınızı ve hata ayıklacağınızı öğrenin.
author: kendrahavens
ms.date: 12/05/2018
ms.custom: seodec18
ms.openlocfilehash: 910545a99f9d014ae572fbe95c93cdb44a69db99
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105100"
---
# <a name="get-started-with-c-and-visual-studio-code"></a><span data-ttu-id="e09e4-103">C# ve Visual Studio Code kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="e09e4-103">Get started with C# and Visual Studio Code</span></span>

<span data-ttu-id="e09e4-104">.NET Core, Windows, Linux ve macOS 'ta çalışan uygulamalar oluşturmaya yönelik hızlı ve modüler bir platform sağlar.</span><span class="sxs-lookup"><span data-stu-id="e09e4-104">.NET Core gives you a fast and modular platform for creating applications that run on Windows, Linux, and macOS.</span></span> <span data-ttu-id="e09e4-105">IntelliSense (akıllı kod C# tamamlama) ve hata ayıklama için C# tam desteğe sahip güçlü bir düzen deneyimi almak üzere uzantıya sahip Visual Studio Code kullanın.</span><span class="sxs-lookup"><span data-stu-id="e09e4-105">Use Visual Studio Code with the C# extension to get a powerful editing experience with full support for C# IntelliSense (smart code completion) and debugging.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e09e4-106">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="e09e4-106">Prerequisites</span></span>

1. <span data-ttu-id="e09e4-107">[Visual Studio Code](https://code.visualstudio.com/)'i yükler.</span><span class="sxs-lookup"><span data-stu-id="e09e4-107">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
2. <span data-ttu-id="e09e4-108">[.NET Core SDK](https://www.microsoft.com/net/download/core)'i yükler.</span><span class="sxs-lookup"><span data-stu-id="e09e4-108">Install the [.NET Core SDK](https://www.microsoft.com/net/download/core).</span></span>
3. <span data-ttu-id="e09e4-109">Visual Studio Code [ C# uzantısını](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) yükler.</span><span class="sxs-lookup"><span data-stu-id="e09e4-109">Install the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) for Visual Studio Code.</span></span> <span data-ttu-id="e09e4-110">Visual Studio Code uzantıları nasıl yükleyeceğiniz hakkında daha fazla bilgi için bkz. [vs Code uzantısı marketi](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="e09e4-110">For more information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>

## <a name="hello-world"></a><span data-ttu-id="e09e4-111">Merhaba Dünya</span><span class="sxs-lookup"><span data-stu-id="e09e4-111">Hello World</span></span>

<span data-ttu-id="e09e4-112">.NET Core üzerinde basit bir "Merhaba Dünya" programı kullanmaya başlayalım:</span><span class="sxs-lookup"><span data-stu-id="e09e4-112">Let's get started with a simple "Hello World" program on .NET Core:</span></span>

1. <span data-ttu-id="e09e4-113">Bir proje açın:</span><span class="sxs-lookup"><span data-stu-id="e09e4-113">Open a project:</span></span>

    - <span data-ttu-id="e09e4-114">Visual Studio Code'u açın.</span><span class="sxs-lookup"><span data-stu-id="e09e4-114">Open Visual Studio Code.</span></span>
    - <span data-ttu-id="e09e4-115">Sol menüdeki gezgin simgesine ve ardından **klasörü aç**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e09e4-115">Click on the Explorer icon on the left menu and then click **Open Folder**.</span></span>
    - <span data-ttu-id="e09e4-116">Ana menüden **Dosya** > **Aç klasörünü** seçerek C# projenizin içinde olmasını istediğiniz klasörü açın ve **Klasör Seç**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e09e4-116">Select **File** > **Open Folder** from the main menu to open the folder you want your C# project to be in and click **Select Folder**.</span></span> <span data-ttu-id="e09e4-117">Bizim örneğimizde *HelloWorld*adlı projemiz için bir klasör oluşturuluyoruz.</span><span class="sxs-lookup"><span data-stu-id="e09e4-117">For our example, we're creating a folder for our project named *HelloWorld*.</span></span>

      ![Visual Studio Code klasörü aç](media/with-visual-studio-code/vs-code-open-folder.png)

2. <span data-ttu-id="e09e4-119">C# Projeyi Başlat:</span><span class="sxs-lookup"><span data-stu-id="e09e4-119">Initialize a C# project:</span></span>
    - <span data-ttu-id="e09e4-120">Ana menüden**Tümleşik Terminal** 'yi **görüntüle** > ' ye tıklayarak tümleşik terminalden Visual Studio Code açın.</span><span class="sxs-lookup"><span data-stu-id="e09e4-120">Open the Integrated Terminal from Visual Studio Code by selecting **View** > **Integrated Terminal** from the main menu.</span></span>
    - <span data-ttu-id="e09e4-121">Terminal penceresinde, yazın `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="e09e4-121">In the terminal window, type `dotnet new console`.</span></span>
    - <span data-ttu-id="e09e4-122">Bu komut, klasörünüzde `Program.cs` zaten yazılmış olan ve adında C# `HelloWorld.csproj`bir proje dosyası olan basit bir "Merhaba Dünya" programı olan bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e09e4-122">This command creates a `Program.cs` file in your folder with a simple "Hello World" program already written, along with a C# project file named `HelloWorld.csproj`.</span></span>

      ![DotNet yeni komutu](media/with-visual-studio-code/dotnet-new-command.png)

3. <span data-ttu-id="e09e4-124">Derleme varlıklarını çözümleyin:</span><span class="sxs-lookup"><span data-stu-id="e09e4-124">Resolve the build assets:</span></span>

    - <span data-ttu-id="e09e4-125">**.NET Core 1. x**için yazın `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="e09e4-125">For **.NET Core 1.x**, type `dotnet restore`.</span></span> <span data-ttu-id="e09e4-126">Çalışıyor `dotnet restore` , projenizi derlemek için gereken gerekli .NET Core paketlerine erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e09e4-126">Running `dotnet restore` gives you access to the  required .NET Core packages that are needed to build your project.</span></span>

      ![dotnet restore komutu](media/with-visual-studio-code/dotnet-restore-command.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. <span data-ttu-id="e09e4-128">"Merhaba Dünya" programını çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="e09e4-128">Run the "Hello World" program:</span></span>

    - <span data-ttu-id="e09e4-129">`dotnet run`yazın.</span><span class="sxs-lookup"><span data-stu-id="e09e4-129">Type `dotnet run`.</span></span>

      ![DotNet Run komutu](media/with-visual-studio-code/dotnet-run-command.png)

<span data-ttu-id="e09e4-131">Ayrıca, [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [MacOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS)veya [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu)hakkında daha fazla kurulum yardımı için kısa bir video öğreticisini izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e09e4-131">You can also watch a short video tutorial for further setup help on [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS), or [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span>

## <a name="debug"></a><span data-ttu-id="e09e4-132">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="e09e4-132">Debug</span></span>

1. <span data-ttu-id="e09e4-133">Üzerine tıklayarak *program.cs* açın.</span><span class="sxs-lookup"><span data-stu-id="e09e4-133">Open *Program.cs* by clicking on it.</span></span> <span data-ttu-id="e09e4-134">Visual Studio Code bir C# dosyayı ilk açışınızda, [Omnisharp](https://www.omnisharp.net/) , düzenleyicide yüklenir.</span><span class="sxs-lookup"><span data-stu-id="e09e4-134">The first time you open a C# file in Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) loads in the editor.</span></span>

    ![Program.cs dosyasını açın](media/with-visual-studio-code/open-program-cs.png)

2. <span data-ttu-id="e09e4-136">Visual Studio Code, uygulamanızda derlemek ve hata ayıklamak için eksik varlıkları eklemenizi ister.</span><span class="sxs-lookup"><span data-stu-id="e09e4-136">Visual Studio Code should prompt you to add the missing assets to build and debug your app.</span></span> <span data-ttu-id="e09e4-137">**Evet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="e09e4-137">Select **Yes**.</span></span>

    ![Eksik varlıklar için istem](media/with-visual-studio-code/missing-assets.png)

3. <span data-ttu-id="e09e4-139">Hata ayıklama görünümünü açmak için sol taraftaki menüdeki hata ayıklama simgesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e09e4-139">To open the Debug view, click on the Debugging icon on the left side menu.</span></span>

    ![Visual Studio Code hata ayıkla sekmesini açın](media/with-visual-studio-code/open-debug-tab.png)

4. <span data-ttu-id="e09e4-141">Bölmenin en üstündeki yeşil oku bulun.</span><span class="sxs-lookup"><span data-stu-id="e09e4-141">Locate the green arrow at the top of the pane.</span></span> <span data-ttu-id="e09e4-142">Yanındaki açılan eklentinin `.NET Core Launch (console)` seçili olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="e09e4-142">Make sure the drop-down next to it has `.NET Core Launch (console)` selected.</span></span>

    ![Visual Studio Code .NET Core seçme](media/with-visual-studio-code/select-net-core.png)

5. <span data-ttu-id="e09e4-144">Düzenleyicide satır numaralarının solundaki boşluk olan **Düzenleyici kenar boşluğuna**, 9. satırın yanında bir kesme noktası ekleyin veya metin imlecini düzenleyicide 9. satıra taşıyın ve <kbd>F9</kbd>tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e09e4-144">Add a breakpoint to your project by clicking on the **editor margin**, which is the space on the left of the line numbers in the editor, next to line 9, or move the text cursor onto line 9 in the editor and  press <kbd>F9</kbd>.</span></span>

    ![Kesme noktası ayarlama](media/with-visual-studio-code/set-breakpoint-vs-code.png)

6. <span data-ttu-id="e09e4-146">Hata ayıklamayı başlatmak için <kbd>F5</kbd> veya yeşil ok ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="e09e4-146">To start debugging, select <kbd>F5</kbd> or the green arrow.</span></span> <span data-ttu-id="e09e4-147">Hata ayıklayıcı, önceki adımda ayarladığınız kesme noktasına ulaştığında programınızın yürütülmesini durduruyor.</span><span class="sxs-lookup"><span data-stu-id="e09e4-147">The debugger stops execution of your program when it reaches the breakpoint you set in the previous step.</span></span>
    - <span data-ttu-id="e09e4-148">Hata ayıklarken, sol üst bölmedeki yerel değişkenlerinizi görüntüleyebilir veya hata ayıklama konsolunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e09e4-148">While debugging, you can view your local variables in the top left pane or use the debug console.</span></span>

7. <span data-ttu-id="e09e4-149">Hata ayıklamaya devam etmek için üstteki mavi oku seçin ya da durdurmak için üstteki kırmızı kareyi seçin.</span><span class="sxs-lookup"><span data-stu-id="e09e4-149">Select the blue arrow at the top to continue debugging, or select the red square at the top to stop.</span></span>

    ![Visual Studio Code Çalıştır ve hata ayıkla](media/with-visual-studio-code/run-debug-vs-code.png)

> [!TIP]
> <span data-ttu-id="e09e4-151">.NET Core hata ayıklama hakkında daha fazla bilgi ve Visual Studio Code ile ilgili sorun giderme ipuçları için, [.NET Core hata ayıklayıcısını ayarlama yönergelerine](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="e09e4-151">For more information and troubleshooting tips on .NET Core debugging with OmniSharp in Visual Studio Code, see [Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="add-a-class"></a><span data-ttu-id="e09e4-152">Sınıf ekleme</span><span class="sxs-lookup"><span data-stu-id="e09e4-152">Add a class</span></span>

1. <span data-ttu-id="e09e4-153">Yeni bir sınıf eklemek için VSCode Gezgininde sağ tıklayıp **yeni dosya**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="e09e4-153">To add a new class right-click in the VSCode Explorer and select **New File**.</span></span> <span data-ttu-id="e09e4-154">Bu, VSCode 'da açtığınız klasöre yeni bir dosya ekler.</span><span class="sxs-lookup"><span data-stu-id="e09e4-154">This adds a new file to the folder you have open in VSCode.</span></span>
2. <span data-ttu-id="e09e4-155">Dosyanızı `MyClass.cs`adlandırın.</span><span class="sxs-lookup"><span data-stu-id="e09e4-155">Name your file `MyClass.cs`.</span></span> <span data-ttu-id="e09e4-156">Bir CSharp dosyası olarak tanınabilmesi `.cs` için onu sonda bir uzantıyla kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="e09e4-156">You must save it with a `.cs` extension at the end for it to be recognized as a csharp file.</span></span>
3. <span data-ttu-id="e09e4-157">İlk sınıfınızı oluşturmak için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e09e4-157">Add the code below to create your first class.</span></span> <span data-ttu-id="e09e4-158">`Program.cs` Dosyanıza başvurabilmeniz için doğru ad alanını eklediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="e09e4-158">Make sure to include the correct namespace so you can reference it from your `Program.cs` file.</span></span>

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

4. <span data-ttu-id="e09e4-159">Aşağıdaki kodu ekleyerek, içindeki `Program.cs` Main yönteinizden yeni sınıfınızı çağırın.</span><span class="sxs-lookup"><span data-stu-id="e09e4-159">Call your new class from your main method in `Program.cs` by adding the code below.</span></span>

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

5. <span data-ttu-id="e09e4-160">Değişikliklerinizi kaydedin ve programınızı yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e09e4-160">Save your changes and run your program again.</span></span> <span data-ttu-id="e09e4-161">Yeni ileti, eklenen dizeyle birlikte görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="e09e4-161">The new message should appear with the appended string.</span></span>

    ```console
    > dotnet run
    Hello World! Happy coding!
    ```

## <a name="faq"></a><span data-ttu-id="e09e4-162">SSS</span><span class="sxs-lookup"><span data-stu-id="e09e4-162">FAQ</span></span>

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a><span data-ttu-id="e09e4-163">Visual Studio Code derlemek ve hata ayıklamak C# için gerekli varlıkların yok.</span><span class="sxs-lookup"><span data-stu-id="e09e4-163">I'm missing required assets to build and debug C# in Visual Studio Code.</span></span> <span data-ttu-id="e09e4-164">Hata ayıklayıcı "yapılandırma yok" diyor.</span><span class="sxs-lookup"><span data-stu-id="e09e4-164">My debugger says "No Configuration."</span></span>

<span data-ttu-id="e09e4-165">Visual Studio Code C# uzantısı sizin için derlemek ve hata ayıklamak üzere varlık oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="e09e4-165">The Visual Studio Code C# extension can generate assets to build and debug for you.</span></span> <span data-ttu-id="e09e4-166">Visual Studio Code, bir C# projeyi ilk açtığınızda bu varlıkları oluşturmanız istenir.</span><span class="sxs-lookup"><span data-stu-id="e09e4-166">Visual Studio Code prompts you to generate these assets when you first open a C# project.</span></span> <span data-ttu-id="e09e4-167">Daha sonra varlık oluşturmadıysanız, komut paletini açıp ( **> komut paletini görüntüle**) ve "> .net" yazarak bu komutu çalıştırmaya devam edebilirsiniz. Derleme ve hata ayıklama için varlık oluşturma ".</span><span class="sxs-lookup"><span data-stu-id="e09e4-167">If you didn't generate assets then, you can still run this command by opening the Command Palette (**View > Command Palette**) and typing ">.NET: Generate Assets for Build and Debug".</span></span> <span data-ttu-id="e09e4-168">Bunu seçtiğinizde, ihtiyacınız olan. vscode, Launch. JSON ve Tasks. JSON yapılandırma dosyaları oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e09e4-168">Selecting this generates the .vscode, launch.json, and tasks.json configuration files that you need.</span></span>

## <a name="see-also"></a><span data-ttu-id="e09e4-169">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e09e4-169">See also</span></span>

- [<span data-ttu-id="e09e4-170">Visual Studio Code ayarlama</span><span class="sxs-lookup"><span data-stu-id="e09e4-170">Setting up Visual Studio Code</span></span>](https://code.visualstudio.com/docs/setup/setup-overview)
- [<span data-ttu-id="e09e4-171">Visual Studio Code 'de hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="e09e4-171">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/editor/debugging)
