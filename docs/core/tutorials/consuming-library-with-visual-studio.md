---
title: Visual Studio’da bir .NET Standard kitaplığını kullanma
description: Visual Studio 2019 ile başka bir sınıf kitaplığı üyelerini çağıran bir .NET Core uygulaması oluşturun.
ms.date: 12/20/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 4eb75f23359334ea483cba1498f1804c4b24c80c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920450"
---
# <a name="consume-a-net-standard-library-in-visual-studio"></a><span data-ttu-id="74e60-103">Visual Studio’da bir .NET Standard kitaplığını kullanma</span><span class="sxs-lookup"><span data-stu-id="74e60-103">Consume a .NET Standard library in Visual Studio</span></span>

<span data-ttu-id="74e60-104">Bir .NET Standart sınıf kitaplığı oluşturduktan, test ettikten ve kitaplığın sürüm sürümünü oluşturduktan sonra, bir sonraki adım arayanların kullanımına açmaktır.</span><span class="sxs-lookup"><span data-stu-id="74e60-104">Once you've created a .NET Standard class library, tested it, and built a release version of the library, the next step is to make it available to callers.</span></span> <span data-ttu-id="74e60-105">Bunu iki şekilde yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="74e60-105">You can do this in two ways:</span></span>

- <span data-ttu-id="74e60-106">Kitaplık tek bir çözüm tarafından kullanılacaksa (örneğin, tek bir büyük uygulamada bir bileşense), bunu çözüme proje olarak ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74e60-106">If the library will be used by a single solution (for example, if it's a component in a single large application), you can include it as a project in your solution.</span></span>
- <span data-ttu-id="74e60-107">Kitaplık herkese açık olacaksa, bunu NuGet paketi olarak dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74e60-107">If the library will be publicly available, you can distribute it as a NuGet package.</span></span>

<span data-ttu-id="74e60-108">Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:</span><span class="sxs-lookup"><span data-stu-id="74e60-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="74e60-109">Çözüme bir .NET Standart kitaplık projesine atıfta bulunulan bir konsol uygulaması ekleyin.</span><span class="sxs-lookup"><span data-stu-id="74e60-109">Add a console app to your solution that references a .NET Standard library project.</span></span>
> - <span data-ttu-id="74e60-110">.NET Standart kitaplık projesi içeren bir NuGet paketi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="74e60-110">Create a NuGet package that contains a .NET Standard library project.</span></span>

## <a name="add-a-console-app-to-your-solution"></a><span data-ttu-id="74e60-111">Çözümünüze konsol uygulaması ekleme</span><span class="sxs-lookup"><span data-stu-id="74e60-111">Add a console app to your solution</span></span>

<span data-ttu-id="74e60-112">[Visual Studio'daki Test a .NET Standart kitaplığında](testing-library-with-visual-studio.md)sınıf kitaplığınız ile aynı çözüme birim testleri eklediğiniz gibi, uygulamanızı da bu çözümün bir parçası olarak ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74e60-112">Just as you included unit tests in the same solution as your class library in [Test a .NET Standard library in Visual Studio](testing-library-with-visual-studio.md), you can include your application as part of that solution.</span></span> <span data-ttu-id="74e60-113">Örneğin, sınıf kitaplığınızı, kullanıcıdan bir dize girmesini gerektiren ve ilk karakterinin büyük harf olup olmadığını bildiren bir konsol uygulamasında kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="74e60-113">For example, you can use your class library in a console application that prompts the user to enter a string and reports whether its first character is uppercase:</span></span>

1. <span data-ttu-id="74e60-114">Visual `ClassLibraryProjects` Studio makalesinde [Bir .NET Standart kitaplığı oluştur'da](library-with-visual-studio.md) oluşturduğunuz çözümü açın.</span><span class="sxs-lookup"><span data-stu-id="74e60-114">Open the `ClassLibraryProjects` solution you created in the [Build a .NET Standard library in Visual Studio](library-with-visual-studio.md) article.</span></span>

1. <span data-ttu-id="74e60-115">Çözüme "ShowCase" adlı yeni bir .NET Core konsol uygulaması ekleyin.</span><span class="sxs-lookup"><span data-stu-id="74e60-115">Add a new .NET Core console application named "ShowCase" to the solution.</span></span>

   1. <span data-ttu-id="74e60-116">**Solution Explorer'da** çözüme sağ tıklayın ve**Yeni proje** **Ekle'yi** > seçin.</span><span class="sxs-lookup"><span data-stu-id="74e60-116">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="74e60-117">Yeni **proje** ekle sayfasında, arama kutusuna **konsolgirin.**</span><span class="sxs-lookup"><span data-stu-id="74e60-117">On the **Add a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="74e60-118">Dil listesinden **C#** veya **Visual Basic'i** seçin ve ardından Platform listesindeki **tüm platformları** seçin.</span><span class="sxs-lookup"><span data-stu-id="74e60-118">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="74e60-119">Konsol **Uygulaması (.NET Core)** şablonunu seçin ve ardından **İleri'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="74e60-119">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="74e60-120">Yeni **proje sayfanızı Yapılandır'da** Proje **adı** kutusuna **ShowCase'i** girin.</span><span class="sxs-lookup"><span data-stu-id="74e60-120">On the **Configure your new project** page, enter **ShowCase** in the **Project name** box.</span></span> <span data-ttu-id="74e60-121">Ardından **Oluştur'u**seçin.</span><span class="sxs-lookup"><span data-stu-id="74e60-121">Then, choose **Create**.</span></span>

1. <span data-ttu-id="74e60-122">**Solution**Explorer'da, **ShowCase** projesini sağ tıklatın ve bağlam menüsünde **Başlangıç Projesi olarak ayarla'yı** seçin.</span><span class="sxs-lookup"><span data-stu-id="74e60-122">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span>

   ![Başlangıç projesini ayarlamak için Visual Studio proje bağlam menüsü](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="74e60-124">Başlangıçta, projenizin sınıf kitaplığınıza erişimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="74e60-124">Initially, your project doesn't have access to your class library.</span></span> <span data-ttu-id="74e60-125">Sınıf kitaplığınızda yöntemleri aramasına izin vermek için sınıf kitaplığına bir başvuru oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="74e60-125">To allow it to call methods in your class library, you create a reference to the class library.</span></span> <span data-ttu-id="74e60-126">**Çözüm Gezgini'nde,** `ShowCase` projenin **Bağımlılıklar** düğümünü sağ tıklatın ve **Başvuru Ekle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="74e60-126">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node and select **Add Reference**.</span></span>

   ![Visual Studio'da referans bağlam menüsü ekleme](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="74e60-128">Başvuru **Yöneticisi** iletişim kutusunda **StringLibrary'yi,** sınıf kitaplığı projenizi seçin ve **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="74e60-128">In the **Reference Manager** dialog, select **StringLibrary**, your class library project, and select the **OK** button.</span></span>

   ![StringLibrary seçili Başvuru Yöneticisi iletişim kutusu](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. <span data-ttu-id="74e60-130">*Program.cs* veya *Program.vb* dosyasının kod penceresinde, kodun tümünün yerine aşağıdaki kod la değiştirin:</span><span class="sxs-lookup"><span data-stu-id="74e60-130">In the code window for the *Program.cs* or *Program.vb* file, replace all of the code with the following code:</span></span>

   [!code-csharp[UsingClassLib#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]
   [!code-vb[UsingClassLib#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   <span data-ttu-id="74e60-131">Kod, konsol `row` penceresine yazılan veri satırlarının sayısını korumak için değişkeni kullanır.</span><span class="sxs-lookup"><span data-stu-id="74e60-131">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="74e60-132">25'ten büyük veya eşit olduğunda, kod konsol penceresini temizler ve kullanıcıya bir ileti görüntüler.</span><span class="sxs-lookup"><span data-stu-id="74e60-132">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="74e60-133">Program, kullanıcıdan bir dize girmesini ister.</span><span class="sxs-lookup"><span data-stu-id="74e60-133">The program prompts the user to enter a string.</span></span> <span data-ttu-id="74e60-134">Dize bir büyük harf karakteri ile başlayıp başlamadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="74e60-134">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="74e60-135">Kullanıcı dize girmeden Enter tuşuna basarsa, uygulama biter ve konsol penceresi kapanır.</span><span class="sxs-lookup"><span data-stu-id="74e60-135">If the user presses the Enter key without entering a string, the application ends, and the console window closes.</span></span>

1. <span data-ttu-id="74e60-136">Gerekirse, projenin **Hata Ayıklama** yayınını derlemek `ShowCase` için araç çubuğunu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="74e60-136">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="74e60-137">**ShowCase** düğmesindeki yeşil oku seçerek programı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="74e60-137">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![Hata Ayıklama düğmesini gösteren Visual Studio proje araç çubuğu](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)

<span data-ttu-id="74e60-139">[Visual Studio'yu kullanarak C# veya Visual Basic .NET Core Hello World uygulamanızı hata ayıklama](debugging-with-visual-studio.md) adımlarını izleyerek bu kitaplığı kullanan uygulamayı hata ayıklayabilir ve yayımlayabilir ve [.NET Core Hello World uygulamanızı Visual Studio ile](publishing-with-visual-studio.md)yayınlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74e60-139">You can debug and publish the application that uses this library by following the steps in [Debug your C# or Visual Basic .NET Core Hello World application using Visual Studio](debugging-with-visual-studio.md) and [Publish your .NET Core Hello World application with Visual Studio](publishing-with-visual-studio.md).</span></span>

## <a name="create-a-nuget-package"></a><span data-ttu-id="74e60-140">NuGet paketi oluşturma</span><span class="sxs-lookup"><span data-stu-id="74e60-140">Create a NuGet package</span></span>

<span data-ttu-id="74e60-141">Sınıf kitaplığınızı NuGet paketi olarak yayımlayarak yaygın olarak kullanılabilir hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74e60-141">You can make your class library widely available by publishing it as a NuGet package.</span></span> <span data-ttu-id="74e60-142">Visual Studio, NuGet paketlerinin oluşturulmasını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="74e60-142">Visual Studio doesn't support the creation of NuGet packages.</span></span> <span data-ttu-id="74e60-143">Bir tane oluşturmak için .NET Core CLI komutlarını kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="74e60-143">To create one, you need to use the .NET Core CLI commands:</span></span>

1. <span data-ttu-id="74e60-144">Konsol pencereyi açın.</span><span class="sxs-lookup"><span data-stu-id="74e60-144">Open a console window.</span></span>

   <span data-ttu-id="74e60-145">Örneğin, Windows görev çubuğundaki arama kutusuna **Komut İstemi** girin.</span><span class="sxs-lookup"><span data-stu-id="74e60-145">For example, enter **Command Prompt** in the search box on the Windows task bar.</span></span> <span data-ttu-id="74e60-146">Komut **İstem** masaüstü uygulamasını seçin veya arama sonuçlarında zaten seçiliyse **Enter** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="74e60-146">Select the **Command Prompt** desktop app or press **Enter** if it's already selected in the search results.</span></span>

1. <span data-ttu-id="74e60-147">Kitaplığınızın proje dizinine gidin.</span><span class="sxs-lookup"><span data-stu-id="74e60-147">Navigate to your library's project directory.</span></span> <span data-ttu-id="74e60-148">Dizin kaynak kodunuzu ve bir proje dosyası, *StringLibrary.csproj* veya *StringLibrary.vbproj*içerir.</span><span class="sxs-lookup"><span data-stu-id="74e60-148">The directory contains your source code and a project file, *StringLibrary.csproj* or *StringLibrary.vbproj*.</span></span>

1. <span data-ttu-id="74e60-149">*.nupkg* uzantılı bir paket oluşturmak için [dotnet paketi](../tools/dotnet-pack.md) komutunu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="74e60-149">Run the [dotnet pack](../tools/dotnet-pack.md) command to generate a package with a *.nupkg* extension:</span></span>

   ```dotnetcli
   dotnet pack --no-build
   ```

   > [!TIP]
   > <span data-ttu-id="74e60-150">*dotnet.exe* içeren dizin PATH'inizde değilse, konsol penceresine girerek `where dotnet.exe` konumunu bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74e60-150">If the directory that contains *dotnet.exe* is not in your PATH, you can find its location by entering `where dotnet.exe` in the console window.</span></span>

<span data-ttu-id="74e60-151">NuGet paketleri oluşturma hakkında daha fazla bilgi için [.NET Core CLI ile NuGet paketi nasıl oluşturulur.](../deploying/creating-nuget-packages.md)</span><span class="sxs-lookup"><span data-stu-id="74e60-151">For more information on creating NuGet packages, see [How to create a NuGet package with the .NET Core CLI](../deploying/creating-nuget-packages.md).</span></span>
