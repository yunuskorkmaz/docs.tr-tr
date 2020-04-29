---
title: C# ve Visual Studio Code kullanmaya başlama
description: Visual Studio Code kullanarak C# ' de ilk .NET Core uygulamanızı nasıl oluşturacağınızı ve hata ayıklacağınızı öğrenin.
author: kendrahavens
ms.date: 04/23/2020
ms.openlocfilehash: 3dd7c4602fbb27e29bad977f8d3df34b6061bc23
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82506924"
---
# <a name="get-started-with-c-and-visual-studio-code"></a><span data-ttu-id="54066-103">C# ve Visual Studio Code kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="54066-103">Get started with C# and Visual Studio Code</span></span>

<span data-ttu-id="54066-104">.NET Core, Windows, Linux ve macOS 'ta çalışan uygulamalar oluşturmaya yönelik hızlı ve modüler bir platform sağlar.</span><span class="sxs-lookup"><span data-stu-id="54066-104">.NET Core gives you a fast and modular platform for creating applications that run on Windows, Linux, and macOS.</span></span> <span data-ttu-id="54066-105">C# IntelliSense ile Visual Studio Code kullanın (akıllı kod tamamlama) ve hata ayıklama için tam destek sayesinde güçlü bir düzen deneyimi alın.</span><span class="sxs-lookup"><span data-stu-id="54066-105">Use Visual Studio Code with the C# extension to get a powerful editing experience with full support for C# IntelliSense (smart code completion) and debugging.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="54066-106">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="54066-106">Prerequisites</span></span>

1. <span data-ttu-id="54066-107">[Visual Studio Code](https://code.visualstudio.com/)'i yükler.</span><span class="sxs-lookup"><span data-stu-id="54066-107">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
2. <span data-ttu-id="54066-108">[.NET Core SDK](https://dotnet.microsoft.com/download)'i yükler.</span><span class="sxs-lookup"><span data-stu-id="54066-108">Install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>
3. <span data-ttu-id="54066-109">Visual Studio Code için [C# uzantısını](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) yükler.</span><span class="sxs-lookup"><span data-stu-id="54066-109">Install the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) for Visual Studio Code.</span></span> <span data-ttu-id="54066-110">Visual Studio Code uzantıları nasıl yükleyeceğiniz hakkında daha fazla bilgi için bkz. [vs Code uzantısı marketi](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="54066-110">For more information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>

## <a name="hello-world"></a><span data-ttu-id="54066-111">Hello World</span><span class="sxs-lookup"><span data-stu-id="54066-111">Hello World</span></span>

<span data-ttu-id="54066-112">.NET Core üzerinde basit bir "Merhaba Dünya" programı ile çalışmaya başlayın:</span><span class="sxs-lookup"><span data-stu-id="54066-112">Get started with a simple "Hello World" program on .NET Core:</span></span>

1. <span data-ttu-id="54066-113">Bir proje açın:</span><span class="sxs-lookup"><span data-stu-id="54066-113">Open a project:</span></span>

    - <span data-ttu-id="54066-114">Visual Studio Code'u açın.</span><span class="sxs-lookup"><span data-stu-id="54066-114">Open Visual Studio Code.</span></span>
    - <span data-ttu-id="54066-115">Ana menüden **Dosya** > **Aç klasörünü** seçin.</span><span class="sxs-lookup"><span data-stu-id="54066-115">Select **File** > **Open Folder** from the main menu.</span></span>
    - <span data-ttu-id="54066-116">*HelloWorld*adlı bir klasör oluşturun ve **Klasör Seç**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="54066-116">Create a folder named *HelloWorld*, and click **Select Folder**.</span></span> <span data-ttu-id="54066-117">Klasör adı, varsayılan olarak proje adı ve ad alanı adı olur.</span><span class="sxs-lookup"><span data-stu-id="54066-117">The folder name becomes the project name and the namespace name by default.</span></span> <span data-ttu-id="54066-118">Daha sonra, proje ad alanının olduğunu `HelloWorld`varsayan öğreticide kod ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="54066-118">You'll add code later in the tutorial that assumes the project namespace is `HelloWorld`.</span></span>

1. <span data-ttu-id="54066-119">C# projesi Başlat:</span><span class="sxs-lookup"><span data-stu-id="54066-119">Initialize a C# project:</span></span>

    - <span data-ttu-id="54066-120">Ana menüden **Görünüm** > **terminali** ' i seçerek Visual Studio Code terminalden açın.</span><span class="sxs-lookup"><span data-stu-id="54066-120">Open the Terminal from Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>
    - <span data-ttu-id="54066-121">Terminal penceresinde, girin `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="54066-121">In the terminal window, enter `dotnet new console`.</span></span>

      <span data-ttu-id="54066-122">Bu komut, klasörünüzde zaten yazılmış olan basit bir "Merhaba Dünya" programı ile birlikte *HelloWorld. csproj*adlı bir C# proje dosyası içeren bir *program.cs* dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="54066-122">This command creates a *Program.cs* file in your folder with a simple "Hello World" program already written, along with a C# project file named *HelloWorld.csproj*.</span></span>

      ![DotNet yeni komutu](media/with-visual-studio-code/dotnet-new-command.png)

1. <span data-ttu-id="54066-124">"Merhaba Dünya" programını çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="54066-124">Run the "Hello World" program:</span></span>

    - <span data-ttu-id="54066-125">Terminal penceresinde, girin `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="54066-125">In the terminal window, enter `dotnet run`.</span></span>

      ![DotNet Run komutu](media/with-visual-studio-code/dotnet-run-command.png)

## <a name="debug"></a><span data-ttu-id="54066-127">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="54066-127">Debug</span></span>

1. <span data-ttu-id="54066-128">Üzerine tıklayarak *program.cs* açın.</span><span class="sxs-lookup"><span data-stu-id="54066-128">Open *Program.cs* by clicking on it.</span></span> <span data-ttu-id="54066-129">Visual Studio Code bir C# dosyasını ilk açışınızda, [Omnisharp](https://www.omnisharp.net/) düzenleyicide yüklenir.</span><span class="sxs-lookup"><span data-stu-id="54066-129">The first time you open a C# file in Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) loads in the editor.</span></span>

    ![Program.cs dosyasını açın](media/with-visual-studio-code/open-program-cs.png)

1. <span data-ttu-id="54066-131">Visual Studio Code, uygulamanızda derleme ve hata ayıklama için eksik varlıkları eklemenizi ister.</span><span class="sxs-lookup"><span data-stu-id="54066-131">Visual Studio Code prompts you to add the missing assets to build and debug your app.</span></span> <span data-ttu-id="54066-132">**Evet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="54066-132">Select **Yes**.</span></span>

    ![Eksik varlıklar için istem](media/with-visual-studio-code/missing-assets.png)

1. <span data-ttu-id="54066-134">Hata ayıklama görünümünü açmak için sol taraftaki menüdeki hata ayıklama simgesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="54066-134">To open the Debug view, click on the Debugging icon on the left side menu.</span></span>

    ![Visual Studio Code hata ayıkla sekmesini açın](media/with-visual-studio-code/open-debug-tab.png)

1. <span data-ttu-id="54066-136">Bölmenin en üstündeki yeşil oku bulun.</span><span class="sxs-lookup"><span data-stu-id="54066-136">Locate the green arrow at the top of the pane.</span></span> <span data-ttu-id="54066-137">' In yanındaki açılan kutuda **.NET Core başlatma (konsol)** seçili olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="54066-137">Make sure the drop-down next to it has **.NET Core Launch (console)** selected.</span></span>

    ![Visual Studio Code .NET Core seçme](media/with-visual-studio-code/select-net-core.png)

1. <span data-ttu-id="54066-139">Düzenleyicide satır numaralarının solundaki boşluk olan **Düzenleyici kenar boşluğuna**, 9. satırın yanında bir kesme noktası ekleyin veya metin imlecini düzenleyicide 9. satıra taşıyın ve <kbd>F9</kbd>tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="54066-139">Add a breakpoint to your project by clicking on the **editor margin**, which is the space on the left of the line numbers in the editor, next to line 9, or move the text cursor onto line 9 in the editor and  press <kbd>F9</kbd>.</span></span>

    ![Kesme noktası ayarlama](media/with-visual-studio-code/set-breakpoint-vs-code.png)

1. <span data-ttu-id="54066-141">Hata ayıklamayı başlatmak için <kbd>F5</kbd> 'e basın veya yeşil oku seçin.</span><span class="sxs-lookup"><span data-stu-id="54066-141">To start debugging, press <kbd>F5</kbd> or select the green arrow.</span></span> <span data-ttu-id="54066-142">Hata ayıklayıcı, önceki adımda ayarladığınız kesme noktasına ulaştığında programınızın yürütülmesini durduruyor.</span><span class="sxs-lookup"><span data-stu-id="54066-142">The debugger stops execution of your program when it reaches the breakpoint you set in the previous step.</span></span>
    - <span data-ttu-id="54066-143">Hata ayıklarken, sol üst bölmedeki yerel değişkenlerinizi görüntüleyebilir veya hata ayıklama konsolunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54066-143">While debugging, you can view your local variables in the top-left pane or use the debug console.</span></span>

1. <span data-ttu-id="54066-144">Hata ayıklamaya devam etmek için üstteki mavi oku seçin ya da durdurmak için üstteki kırmızı kareyi seçin.</span><span class="sxs-lookup"><span data-stu-id="54066-144">Select the blue arrow at the top to continue debugging, or select the red square at the top to stop.</span></span>

    ![Visual Studio Code Çalıştır ve hata ayıkla](media/with-visual-studio-code/run-debug-vs-code.png)

> [!TIP]
> <span data-ttu-id="54066-146">.NET Core hata ayıklama hakkında daha fazla bilgi ve Visual Studio Code ile ilgili sorun giderme ipuçları için, [.NET Core hata ayıklayıcısını ayarlama yönergelerine](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="54066-146">For more information and troubleshooting tips on .NET Core debugging with OmniSharp in Visual Studio Code, see [Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="add-a-class"></a><span data-ttu-id="54066-147">Sınıf ekleme</span><span class="sxs-lookup"><span data-stu-id="54066-147">Add a class</span></span>

1. <span data-ttu-id="54066-148">Yeni bir sınıf eklemek için, *program.cs* aşağıdaki vscode Explorer ' a sağ tıklayıp **yeni dosya**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="54066-148">To add a new class, right-click in the VSCode Explorer below *Program.cs* and select **New File**.</span></span> <span data-ttu-id="54066-149">Bu, VSCode 'da açtığınız klasöre yeni bir dosya ekler.</span><span class="sxs-lookup"><span data-stu-id="54066-149">This adds a new file to the folder you have open in VSCode.</span></span>
1. <span data-ttu-id="54066-150">Dosyanızı *MyClass.cs*olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="54066-150">Name your file *MyClass.cs*.</span></span> <span data-ttu-id="54066-151">Bir CSharp dosyası olarak tanınabilmesi `.cs` için onu sonda bir uzantıyla kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="54066-151">You must save it with a `.cs` extension at the end for it to be recognized as a csharp file.</span></span>
1. <span data-ttu-id="54066-152">İlk sınıfınızı oluşturmak için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="54066-152">Add the following code to create your first class.</span></span>

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

1. <span data-ttu-id="54066-153">Program.cs içindeki kodu aşağıdaki kodla değiştirerek `Main` , yönteinizden yeni sınıfınızı çağırın *Program.cs* :</span><span class="sxs-lookup"><span data-stu-id="54066-153">Call your new class from your `Main` method by replacing the code in *Program.cs* with the following code:</span></span>

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

1. <span data-ttu-id="54066-154">Yaptığınız değişiklikleri kaydedin.</span><span class="sxs-lookup"><span data-stu-id="54066-154">Save your changes.</span></span>

1. <span data-ttu-id="54066-155">Programı yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="54066-155">Run the program again.</span></span>

    ```dotnetcli
    dotnet run
    ```

    <span data-ttu-id="54066-156">Yeni ileti eklenmiş dize ile görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="54066-156">The new message appears with the appended string.</span></span>

    ```console
    Hello World! Happy coding!
    ```

## <a name="faq"></a><span data-ttu-id="54066-157">SSS</span><span class="sxs-lookup"><span data-stu-id="54066-157">FAQ</span></span>

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a><span data-ttu-id="54066-158">Visual Studio Code C# derlemek ve hatalarını ayıklamak için gerekli varlıkların yok.</span><span class="sxs-lookup"><span data-stu-id="54066-158">I'm missing required assets to build and debug C# in Visual Studio Code.</span></span> <span data-ttu-id="54066-159">Hata ayıklayıcı "yapılandırma yok" diyor.</span><span class="sxs-lookup"><span data-stu-id="54066-159">My debugger says "No Configuration."</span></span>

<span data-ttu-id="54066-160">Visual Studio Code C# uzantısı sizin için derlemek ve hata ayıklamak için varlıklar oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="54066-160">The Visual Studio Code C# extension can generate assets to build and debug for you.</span></span> <span data-ttu-id="54066-161">Visual Studio Code, ilk olarak bir C# projesi açtığınızda bu varlıkları oluşturmanızı ister.</span><span class="sxs-lookup"><span data-stu-id="54066-161">Visual Studio Code prompts you to generate these assets when you first open a C# project.</span></span> <span data-ttu-id="54066-162">Daha sonra varlık oluşturmadıysanız, bu komutu yine de komut paletini açıp **>**(derleme ve hata ayıklama Için varlık oluştur) "> .net: varlıkları oluşturma ve hata ayıklama" yazarak çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54066-162">If you didn't generate assets then, you can still run this command by opening the Command Palette (**View > Command Palette**) and typing ">.NET: Generate Assets for Build and Debug".</span></span> <span data-ttu-id="54066-163">Bunu seçtiğinizde, ihtiyacınız olan *. vscode*, *Launch. JSON*ve *Tasks. JSON* yapılandırma dosyaları oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="54066-163">Selecting this generates the *.vscode*, *launch.json*, and *tasks.json* configuration files that you need.</span></span>

## <a name="see-also"></a><span data-ttu-id="54066-164">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54066-164">See also</span></span>

- [<span data-ttu-id="54066-165">Visual Studio Code ayarlama</span><span class="sxs-lookup"><span data-stu-id="54066-165">Setting up Visual Studio Code</span></span>](https://code.visualstudio.com/docs/setup/setup-overview)
- [<span data-ttu-id="54066-166">Visual Studio Code 'de hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="54066-166">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/editor/debugging)
