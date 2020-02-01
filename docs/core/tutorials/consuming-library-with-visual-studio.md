---
title: Visual Studio’da bir .NET Standard kitaplığını kullanma
description: Visual Studio 2019 ile başka bir sınıf kitaplığının üyelerini çağıran bir .NET Core uygulaması oluşturun.
ms.date: 12/20/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 4eb75f23359334ea483cba1498f1804c4b24c80c
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920450"
---
# <a name="consume-a-net-standard-library-in-visual-studio"></a><span data-ttu-id="1ddc6-103">Visual Studio’da bir .NET Standard kitaplığını kullanma</span><span class="sxs-lookup"><span data-stu-id="1ddc6-103">Consume a .NET Standard library in Visual Studio</span></span>

<span data-ttu-id="1ddc6-104">Bir .NET Standard sınıf kitaplığı oluşturduktan, sınadıktan ve kitaplığın bir yayın sürümünü oluşturduktan sonra, bir sonraki adım, çağıranlar için kullanılabilir hale gelir.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-104">Once you've created a .NET Standard class library, tested it, and built a release version of the library, the next step is to make it available to callers.</span></span> <span data-ttu-id="1ddc6-105">Bunu iki şekilde yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1ddc6-105">You can do this in two ways:</span></span>

- <span data-ttu-id="1ddc6-106">Kitaplık tek bir çözüm tarafından kullanılacaksa (örneğin, tek bir büyük uygulamadaki bir bileşen ise) çözümünüze bir proje olarak dahil edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-106">If the library will be used by a single solution (for example, if it's a component in a single large application), you can include it as a project in your solution.</span></span>
- <span data-ttu-id="1ddc6-107">Kitaplık herkese açık hale gelir, bir NuGet paketi olarak dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-107">If the library will be publicly available, you can distribute it as a NuGet package.</span></span>

<span data-ttu-id="1ddc6-108">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="1ddc6-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="1ddc6-109">Çözümünüze bir .NET Standard kitaplığı projesine başvuran bir konsol uygulaması ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-109">Add a console app to your solution that references a .NET Standard library project.</span></span>
> - <span data-ttu-id="1ddc6-110">.NET Standard kitaplığı projesi içeren bir NuGet paketi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-110">Create a NuGet package that contains a .NET Standard library project.</span></span>

## <a name="add-a-console-app-to-your-solution"></a><span data-ttu-id="1ddc6-111">Çözümünüze bir konsol uygulaması ekleme</span><span class="sxs-lookup"><span data-stu-id="1ddc6-111">Add a console app to your solution</span></span>

<span data-ttu-id="1ddc6-112">Birim testlerini, [Visual Studio 'da bir .NET Standard kitaplığı test](testing-library-with-visual-studio.md)etme bölümünde yer alan sınıf kitaplısınız ile aynı çözümde bulundurmadığınız gibi, uygulamanızı bu çözümün bir parçası olarak dahil edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-112">Just as you included unit tests in the same solution as your class library in [Test a .NET Standard library in Visual Studio](testing-library-with-visual-studio.md), you can include your application as part of that solution.</span></span> <span data-ttu-id="1ddc6-113">Örneğin, sınıf kitaplığınızı, kullanıcıdan ilk karakterinin büyük harf olup olmadığını belirten bir dize ve rapor girmesini isteyen bir konsol uygulamasında kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1ddc6-113">For example, you can use your class library in a console application that prompts the user to enter a string and reports whether its first character is uppercase:</span></span>

1. <span data-ttu-id="1ddc6-114">[Visual Studio 'da bir .NET Standard kitaplığı oluşturun](library-with-visual-studio.md) makalesindeki oluşturduğunuz `ClassLibraryProjects` çözümünü açın.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-114">Open the `ClassLibraryProjects` solution you created in the [Build a .NET Standard library in Visual Studio](library-with-visual-studio.md) article.</span></span>

1. <span data-ttu-id="1ddc6-115">Çözüme "gösterimi" adlı yeni bir .NET Core konsol uygulaması ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-115">Add a new .NET Core console application named "ShowCase" to the solution.</span></span>

   1. <span data-ttu-id="1ddc6-116">**Çözüm Gezgini** çözüme sağ tıklayın ve > **Yeni proje** **Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-116">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="1ddc6-117">**Yeni Proje Ekle** sayfasında, arama kutusuna **konsol** girin.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-117">On the **Add a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="1ddc6-118">Dil **C#** listesinden seçin veya **Visual Basic** ve ardından platform listesinden **tüm platformlar** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-118">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="1ddc6-119">**Konsol uygulaması (.NET Core)** şablonunu seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-119">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="1ddc6-120">**Yeni projenizi yapılandırın** sayfasında, **Proje adı** kutusuna **gösterimi** girin.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-120">On the **Configure your new project** page, enter **ShowCase** in the **Project name** box.</span></span> <span data-ttu-id="1ddc6-121">Ardından **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-121">Then, choose **Create**.</span></span>

1. <span data-ttu-id="1ddc6-122">**Çözüm Gezgini** **, Gösterim projesine sağ** tıklayın ve bağlam menüsünde **Başlangıç projesi olarak ayarla** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-122">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span>

   ![Başlangıç projesini ayarlamak için Visual Studio proje bağlam menüsü](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="1ddc6-124">Başlangıçta, projenizin sınıf kitaplığınıza erişimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-124">Initially, your project doesn't have access to your class library.</span></span> <span data-ttu-id="1ddc6-125">Sınıf kitaplığınızdaki yöntemleri çağırmasına izin vermek için, sınıf kitaplığına bir başvuru oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-125">To allow it to call methods in your class library, you create a reference to the class library.</span></span> <span data-ttu-id="1ddc6-126">**Çözüm Gezgini**, `ShowCase` projenin **Bağımlılıklar** düğümüne sağ tıklayın ve **Başvuru Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-126">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node and select **Add Reference**.</span></span>

   ![Visual Studio 'da başvuru bağlam menüsü Ekle](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="1ddc6-128">**Başvuru Yöneticisi** Iletişim kutusunda **StringLibrary**, sınıf kitaplığı projeniz ' i seçin ve **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-128">In the **Reference Manager** dialog, select **StringLibrary**, your class library project, and select the **OK** button.</span></span>

   ![StringLibrary seçiliyken başvuru Yöneticisi iletişim kutusu](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. <span data-ttu-id="1ddc6-130">*Program.cs* veya *program. vb* dosyasının kod penceresinde, tüm kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="1ddc6-130">In the code window for the *Program.cs* or *Program.vb* file, replace all of the code with the following code:</span></span>

   [!code-csharp[UsingClassLib#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]
   [!code-vb[UsingClassLib#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   <span data-ttu-id="1ddc6-131">Kod, konsol penceresine yazılan veri satırlarının sayısını korumak için `row` değişkenini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-131">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="1ddc6-132">25 ' e eşit veya daha büyük olduğunda, kod konsol penceresini temizler ve kullanıcıya bir ileti görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-132">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="1ddc6-133">Program kullanıcıdan bir dize girmesini ister.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-133">The program prompts the user to enter a string.</span></span> <span data-ttu-id="1ddc6-134">Dizenin büyük harfle başlatılıp başlatılmayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-134">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="1ddc6-135">Kullanıcı bir dize girmeden ENTER tuşuna basarsa, uygulama sonlanır ve konsol penceresi kapanır.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-135">If the user presses the Enter key without entering a string, the application ends, and the console window closes.</span></span>

1. <span data-ttu-id="1ddc6-136">Gerekirse, `ShowCase` projesinin **hata ayıklama** sürümünü derlemek için araç çubuğunu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-136">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="1ddc6-137">**Gösterimi** düğmesindeki yeşil oku seçerek programı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-137">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![Hata ayıklama düğmesini gösteren Visual Studio proje araç çubuğu](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)

<span data-ttu-id="1ddc6-139">[Visual Studio 'yu kullanarak C# veya Visual Basic .NET Core Merhaba Dünya uygulamanızda hata ayıklama](debugging-with-visual-studio.md) ve [.NET Core Merhaba Dünya uygulamanızı Visual Studio ile yayımlama](publishing-with-visual-studio.md)bölümündeki adımları izleyerek, bu kitaplığı kullanan uygulamayı ayıklayabilir ve yayımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-139">You can debug and publish the application that uses this library by following the steps in [Debug your C# or Visual Basic .NET Core Hello World application using Visual Studio](debugging-with-visual-studio.md) and [Publish your .NET Core Hello World application with Visual Studio](publishing-with-visual-studio.md).</span></span>

## <a name="create-a-nuget-package"></a><span data-ttu-id="1ddc6-140">NuGet paketi oluşturma</span><span class="sxs-lookup"><span data-stu-id="1ddc6-140">Create a NuGet package</span></span>

<span data-ttu-id="1ddc6-141">Sınıf kitaplığınızı, bir NuGet paketi olarak yayımlayarak geniş oranda kullanılabilir hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-141">You can make your class library widely available by publishing it as a NuGet package.</span></span> <span data-ttu-id="1ddc6-142">Visual Studio, NuGet paketlerinin oluşturulmasını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-142">Visual Studio doesn't support the creation of NuGet packages.</span></span> <span data-ttu-id="1ddc6-143">Bir tane oluşturmak için .NET Core CLI komutlarını kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="1ddc6-143">To create one, you need to use the .NET Core CLI commands:</span></span>

1. <span data-ttu-id="1ddc6-144">Bir konsol penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-144">Open a console window.</span></span>

   <span data-ttu-id="1ddc6-145">Örneğin, Windows görev çubuğundaki arama kutusuna **komut istemi** yazın.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-145">For example, enter **Command Prompt** in the search box on the Windows task bar.</span></span> <span data-ttu-id="1ddc6-146">**Komut istemi** masaüstü uygulamasını seçin veya arama sonuçlarında zaten seçiliyse **ENTER** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-146">Select the **Command Prompt** desktop app or press **Enter** if it's already selected in the search results.</span></span>

1. <span data-ttu-id="1ddc6-147">Kitaplığınızın proje dizinine gidin.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-147">Navigate to your library's project directory.</span></span> <span data-ttu-id="1ddc6-148">Dizin, kaynak kodunuzu ve *StringLibrary. csproj* veya *StringLibrary. vbproj*proje dosyasını içerir.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-148">The directory contains your source code and a project file, *StringLibrary.csproj* or *StringLibrary.vbproj*.</span></span>

1. <span data-ttu-id="1ddc6-149">*. Nupkg* uzantılı bir paket oluşturmak için [DotNet Pack](../tools/dotnet-pack.md) komutunu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="1ddc6-149">Run the [dotnet pack](../tools/dotnet-pack.md) command to generate a package with a *.nupkg* extension:</span></span>

   ```dotnetcli
   dotnet pack --no-build
   ```

   > [!TIP]
   > <span data-ttu-id="1ddc6-150">*DotNet. exe* IÇEREN Dizin yolunuzda değilse, konsol penceresine `where dotnet.exe` girerek konumunu bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-150">If the directory that contains *dotnet.exe* is not in your PATH, you can find its location by entering `where dotnet.exe` in the console window.</span></span>

<span data-ttu-id="1ddc6-151">NuGet paketleri oluşturma hakkında daha fazla bilgi için bkz. [.NET Core CLI bir NuGet paketi oluşturma](../deploying/creating-nuget-packages.md).</span><span class="sxs-lookup"><span data-stu-id="1ddc6-151">For more information on creating NuGet packages, see [How to create a NuGet package with the .NET Core CLI](../deploying/creating-nuget-packages.md).</span></span>
