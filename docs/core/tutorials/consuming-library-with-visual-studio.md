---
title: Visual Studio 2017'de bir .NET Standard kitaplığı kullanma
description: Visual Studio 2017 ile bir sınıf kitaplığı'nda üyeleri çağırma hakkında bilgi edinin.
author: BillWagner
ms.author: wiwagn
ms.date: 06/05/2018
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 52ec46c23bb928b49f034270ed1d510d1acf992e
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45518171"
---
# <a name="consuming-a-net-standard-library-in-visual-studio-2017"></a><span data-ttu-id="a1347-103">Visual Studio 2017'de bir .NET Standard kitaplığı kullanma</span><span class="sxs-lookup"><span data-stu-id="a1347-103">Consuming a .NET Standard library in Visual Studio 2017</span></span>

<span data-ttu-id="a1347-104">İçindeki adımları izleyerek bir .NET Standard sınıf kitaplığı oluşturduktan sonra [bir Visual Studio 2017'de .NET Core ile C# sınıf kitaplığı oluşturma](./library-with-visual-studio.md) veya [Visual Studio 2017'de .NET Core ile bir Visual Basic sınıf kitaplığı oluşturma ](vb-library-with-visual-studio.md), içinde test [Visual Studio 2017'de .NET Core ile bir sınıf kitaplığını test](testing-library-with-visual-studio.md), ve kitaplığı sürümü oluşturulan arayanlar için kullanılabilir hale getirmek için sonraki adım içerir.</span><span class="sxs-lookup"><span data-stu-id="a1347-104">Once you've created a .NET Standard class library by following the steps in [Building a C# class library with .NET Core in Visual Studio 2017](./library-with-visual-studio.md) or [Building a Visual Basic class library with .NET Core in Visual Studio 2017](vb-library-with-visual-studio.md), tested it in [Testing a class library with .NET Core in Visual Studio 2017](testing-library-with-visual-studio.md), and built a Release version of the library, the next step is to make it available to callers.</span></span> <span data-ttu-id="a1347-105">Bunu iki şekilde yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a1347-105">You can do this in two ways:</span></span>

* <span data-ttu-id="a1347-106">(Örneğin, bir tek büyük bir uygulama bileşeni ise) tek bir çözüm tarafından kullanılacak kitaplık, çözümünüze bir proje olarak içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a1347-106">If the library will be used by a single solution (for example, if it's a component in a single large application), you can include it as a project in your solution.</span></span>

* <span data-ttu-id="a1347-107">Kitaplığa Genel olarak erişilebilir olacaksa, bir NuGet paketi olarak dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1347-107">If the library will be generally accessible, you can distribute it as a NuGet package.</span></span>

## <a name="including-a-library-as-a-project-in-a-solution"></a><span data-ttu-id="a1347-108">Bir çözümde bir proje olarak kitaplığı dahil olmak üzere</span><span class="sxs-lookup"><span data-stu-id="a1347-108">Including a library as a project in a solution</span></span>

<span data-ttu-id="a1347-109">Sınıf kitaplığınıza aynı çözümde birim testlerini dahil olarak, uygulamanızı bu çözümün parçası olarak dahil edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1347-109">Just as you included unit tests in the same solution as your class library, you can include your application as part of that solution.</span></span> <span data-ttu-id="a1347-110">Örneğin, bir dize ve raporları, ilk karakterin büyük harf olup olmadığını girmesini isteyen bir konsol uygulamasında, sınıf kitaplığı kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a1347-110">For example, you can use your class library in a console application that prompts the user to enter a string and reports whether its first character is uppercase:</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="a1347-111">C#</span><span class="sxs-lookup"><span data-stu-id="a1347-111">C#</span></span>](#tab/csharp)
1. <span data-ttu-id="a1347-112">Açık `ClassLibraryProjects` oluşturduğunuz çözüm [bir Visual Studio 2017'de .NET Core ile C# sınıf kitaplığı oluşturma](./library-with-visual-studio.md) konu.</span><span class="sxs-lookup"><span data-stu-id="a1347-112">Open the `ClassLibraryProjects` solution you created in the [Building a C# Class Library with .NET Core in Visual Studio 2017](./library-with-visual-studio.md) topic.</span></span> <span data-ttu-id="a1347-113">İçinde **Çözüm Gezgini**, sağ **ClassLibraryProjects** çözüm ve select **Ekle** > **yeni proje** gelen bağlam menüsü.</span><span class="sxs-lookup"><span data-stu-id="a1347-113">In **Solution Explorer**, right-click the **ClassLibraryProjects** solution and select **Add** > **New Project** from the context menu.</span></span>

1. <span data-ttu-id="a1347-114">İçinde **Yeni Proje Ekle** iletişim kutusunda genişletin **Visual C#** düğümünü seçip alt **.NET Core** düğümünü ve ardından **konsol uygulaması (.NET Core)** Proje şablonu.</span><span class="sxs-lookup"><span data-stu-id="a1347-114">In the **Add New Project** dialog, expand the **Visual C#** node and select the **.NET Core** node followed by the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="a1347-115">İçinde **adı** metin kutusuna "Gösterimi" yazın ve seçin **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="a1347-115">In the **Name** text box, type "ShowCase", and select the **OK** button.</span></span>

   ![Yeni Proje iletişim kutusu Ekle](./media/consuming-library-with-visual-studio/addnewproject.png)

1. <span data-ttu-id="a1347-117">İçinde **Çözüm Gezgini**, sağ **gösterimi** seçin ve proje **başlangıç projesi olarak ayarla** bağlam menüsünde.</span><span class="sxs-lookup"><span data-stu-id="a1347-117">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span> 

   ![ShowCase bağlam menüsü](./media/consuming-library-with-visual-studio/setstartupproject.png)

1. <span data-ttu-id="a1347-119">Başlangıçta, projenize Sınıf Kitaplığı'na erişimi yok.</span><span class="sxs-lookup"><span data-stu-id="a1347-119">Initially, your project doesn't have access to your class library.</span></span> <span data-ttu-id="a1347-120">Sınıf kitaplığınıza yöntemlerini çağırmaya izin vermek için bir başvuru sınıf kitaplığı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a1347-120">To allow it to call methods in your class library, you create a reference to the class library.</span></span> <span data-ttu-id="a1347-121">İçinde **Çözüm Gezgini**, sağ `ShowCase` projenin **bağımlılıkları** düğümünü seçip alt **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="a1347-121">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node and select **Add Reference**.</span></span>

   ![ShowCase bağımlılıkları bağlam menüsü](./media/consuming-library-with-visual-studio/addreference.png)

1. <span data-ttu-id="a1347-123">İçinde **başvuru Yöneticisi** iletişim kutusunda **StringLibrary**, sınıf kitaplığı projesi ve seçin **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="a1347-123">In the **Reference Manager** dialog, select **StringLibrary**, your class library project, and select the **OK** button.</span></span>

   ![Başvuru Yöneticisi](./media/consuming-library-with-visual-studio/referencemanager.png)

1. <span data-ttu-id="a1347-125">Kod penceresinde *Program.cs* dosya, tüm kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="a1347-125">In the code window for the *Program.cs* file, replace all of the code with the following code:</span></span>

   [!CODE-csharp[UsingClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]

   <span data-ttu-id="a1347-126">Kod `row` konsol penceresine yazılan veri satırı sayısını korumak için değişkeni.</span><span class="sxs-lookup"><span data-stu-id="a1347-126">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="a1347-127">Büyüktür veya eşittir 25 olduğunda, kod konsol penceresini temizler ve kullanıcıya bir ileti görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a1347-127">Whenever it is greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="a1347-128">Program bir dize girmesini ister.</span><span class="sxs-lookup"><span data-stu-id="a1347-128">The program prompts the user to enter a string.</span></span> <span data-ttu-id="a1347-129">Dizeyi büyük harfli bir karakterle başlayıp başlamadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a1347-129">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="a1347-130">Kullanıcı, bir dize girmeden Enter tuşuna bastığında, uygulama sonlandırır ve konsol penceresini kapatır.</span><span class="sxs-lookup"><span data-stu-id="a1347-130">If the user presses the Enter key without entering a string, the application terminates, and the console window closes.</span></span>

1. <span data-ttu-id="a1347-131">Gerekirse, derleme için araç çubuğunda değiştirin **hata ayıklama** sürüm `ShowCase` proje.</span><span class="sxs-lookup"><span data-stu-id="a1347-131">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="a1347-132">Derleme ve yeşil bir ok seçerek programı çalıştırın **gösterimi** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="a1347-132">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![Görüntü](./media/consuming-library-with-visual-studio/toolbar.png)
# <a name="visual-basictabvisual-basic"></a>[<span data-ttu-id="a1347-134">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a1347-134">Visual Basic</span></span>](#tab/visual-basic)
1. <span data-ttu-id="a1347-135">Açık `ClassLibraryProjects` oluşturduğunuz çözüm [bir sınıf kitaplığı Visual Basic ve Visual Studio 2017'de .NET Core ile oluşturmaya](vb-library-with-visual-studio.md) konu.</span><span class="sxs-lookup"><span data-stu-id="a1347-135">Open the `ClassLibraryProjects` solution you created in the [Building a class Library with Visual Basic and .NET Core in Visual Studio 2017](vb-library-with-visual-studio.md) topic.</span></span> <span data-ttu-id="a1347-136">İçinde **Çözüm Gezgini**, sağ **ClassLibraryProjects** çözüm ve select **Ekle** > **yeni proje** gelen bağlam menüsü.</span><span class="sxs-lookup"><span data-stu-id="a1347-136">In **Solution Explorer**, right-click the **ClassLibraryProjects** solution and select **Add** > **New Project** from the context menu.</span></span>

1. <span data-ttu-id="a1347-137">İçinde **Yeni Proje Ekle** iletişim kutusunda genişletin **Visual Basic** düğümünü seçip alt **.NET Core** düğümünü ve ardından **konsol uygulaması (.NET Core)** proje şablonu.</span><span class="sxs-lookup"><span data-stu-id="a1347-137">In the **Add New Project** dialog, expand the **Visual Basic** node and select the **.NET Core** node followed by the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="a1347-138">İçinde **adı** metin kutusuna "Gösterimi" yazın ve seçin **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="a1347-138">In the **Name** text box, type "ShowCase", and select the **OK** button.</span></span>

   ![Yeni Proje iletişim kutusu Ekle](./media/consuming-library-with-visual-studio/vb-addnewproject.png)

1. <span data-ttu-id="a1347-140">İçinde **Çözüm Gezgini**, sağ **gösterimi** seçin ve proje **başlangıç projesi olarak ayarla** bağlam menüsünde.</span><span class="sxs-lookup"><span data-stu-id="a1347-140">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span> 

   ![ShowCase bağlam menüsü](./media/consuming-library-with-visual-studio/setstartupproject.png)

1. <span data-ttu-id="a1347-142">Başlangıçta, projenize Sınıf Kitaplığı'na erişimi yok.</span><span class="sxs-lookup"><span data-stu-id="a1347-142">Initially, your project doesn't have access to your class library.</span></span> <span data-ttu-id="a1347-143">Sınıf kitaplığınıza yöntemlerini çağırmaya izin vermek için bir başvuru sınıf kitaplığı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a1347-143">To allow it to call methods in your class library, you create a reference to the class library.</span></span> <span data-ttu-id="a1347-144">İçinde **Çözüm Gezgini**, sağ `ShowCase` projenin **bağımlılıkları** düğümünü seçip alt **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="a1347-144">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node and select **Add Reference**.</span></span>

   ![ShowCase bağımlılıkları bağlam menüsü](./media/consuming-library-with-visual-studio/addreference.png)

1. <span data-ttu-id="a1347-146">İçinde **başvuru Yöneticisi** iletişim kutusunda **StringLibrary**, sınıf kitaplığı projesi ve seçin **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="a1347-146">In the **Reference Manager** dialog, select **StringLibrary**, your class library project, and select the **OK** button.</span></span>

   ![Başvuru Yöneticisi](./media/consuming-library-with-visual-studio/referencemanager.png)

1. <span data-ttu-id="a1347-148">Kod penceresinde *Program.vb* dosya, tüm kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="a1347-148">In the code window for the *Program.vb* file, replace all of the code with the following code:</span></span>

    [!CODE-vb[UsingClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   <span data-ttu-id="a1347-149">Kod `row` konsol penceresine yazılan veri satırı sayısını korumak için değişkeni.</span><span class="sxs-lookup"><span data-stu-id="a1347-149">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="a1347-150">Büyüktür veya eşittir 25 olduğunda, kod konsol penceresini temizler ve kullanıcıya bir ileti görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a1347-150">Whenever it is greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="a1347-151">Program bir dize girmesini ister.</span><span class="sxs-lookup"><span data-stu-id="a1347-151">The program prompts the user to enter a string.</span></span> <span data-ttu-id="a1347-152">Dizeyi büyük harfli bir karakterle başlayıp başlamadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a1347-152">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="a1347-153">Kullanıcı, bir dize girmeden Enter tuşuna bastığında, uygulama sonlandırır ve konsol penceresini kapatır.</span><span class="sxs-lookup"><span data-stu-id="a1347-153">If the user presses the Enter key without entering a string, the application terminates, and the console window closes.</span></span>

1. <span data-ttu-id="a1347-154">Gerekirse, derleme için araç çubuğunda değiştirin **hata ayıklama** sürüm `ShowCase` proje.</span><span class="sxs-lookup"><span data-stu-id="a1347-154">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="a1347-155">Derleme ve yeşil bir ok seçerek programı çalıştırın **gösterimi** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="a1347-155">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![Görüntü](./media/consuming-library-with-visual-studio/toolbar.png)
---

<span data-ttu-id="a1347-157">Hata ayıklama ve yayımlama adımları izleyerek bu kitaplığı kullanan uygulama [Merhaba Dünya uygulamanızı Visual Studio 2017 ile hata ayıklama](debugging-with-visual-studio.md) ve [Hello World uygulamanızı Visual Studio ile yayımlama 2017](publishing-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="a1347-157">You can debug and publish the application that uses this library by following the steps in [Debugging your Hello World application with Visual Studio 2017](debugging-with-visual-studio.md) and [Publishing your Hello World Application with Visual Studio 2017](publishing-with-visual-studio.md).</span></span>

## <a name="distributing-the-library-in-a-nuget-package"></a><span data-ttu-id="a1347-158">Bir NuGet paketi kitaplıkta dağıtma</span><span class="sxs-lookup"><span data-stu-id="a1347-158">Distributing the library in a NuGet package</span></span>

<span data-ttu-id="a1347-159">Bir NuGet paketi olarak yayımlayarak, sınıf kitaplığı yaygın olarak kullanılabilir hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1347-159">You can make your class library widely available by publishing it as a NuGet package.</span></span> <span data-ttu-id="a1347-160">Visual Studio, NuGet paketlerini oluşturulmasını desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="a1347-160">Visual Studio does not support the creation of NuGet packages.</span></span> <span data-ttu-id="a1347-161">Oluşturmak için kullandığınız [ `dotnet` komut satırı yardımcı programını](../../core/tools/dotnet.md):</span><span class="sxs-lookup"><span data-stu-id="a1347-161">To create one, you use the [`dotnet` command line utility](../../core/tools/dotnet.md):</span></span>

1. <span data-ttu-id="a1347-162">Bir konsol penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="a1347-162">Open a console window.</span></span> <span data-ttu-id="a1347-163">Örneğin **bana istediğini Sorabilirsin** metin kutusunda Windows görev çubuğunda, girin `Command Prompt` (veya `cmd` kısaca) ve seçerek bir konsol penceresi açıyor **komut istemi** masaüstü uygulaması veya arama sonuçlarında seçtiyseniz Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a1347-163">For example in the **Ask me anything** text box in the Windows taskbar, enter `Command Prompt` (or `cmd` for short), and open a console window by either selecting the **Command Prompt** desktop app or pressing Enter if it's selected in the search results.</span></span>

1. <span data-ttu-id="a1347-164">Kitaplığınızın proje dizinine gidin.</span><span class="sxs-lookup"><span data-stu-id="a1347-164">Navigate to your library's project directory.</span></span> <span data-ttu-id="a1347-165">Tipik dosya konumunu yeniden sürece, konusu *Documents\Visual Studio 2017\Projects\ClassLibraryProjects\StringLibrary* dizin.</span><span class="sxs-lookup"><span data-stu-id="a1347-165">Unless you've reconfigured the typical file location, it's in the *Documents\Visual Studio 2017\Projects\ClassLibraryProjects\StringLibrary* directory.</span></span> <span data-ttu-id="a1347-166">Kaynak kodunuzu ve bir proje dosyası dizini içeriyor *StringLibrary.csproj*.</span><span class="sxs-lookup"><span data-stu-id="a1347-166">The directory contains your source code and a project file, *StringLibrary.csproj*.</span></span>

1. <span data-ttu-id="a1347-167">Komutu Yürüt `dotnet pack --no-build`.</span><span class="sxs-lookup"><span data-stu-id="a1347-167">Issue the command `dotnet pack --no-build`.</span></span> <span data-ttu-id="a1347-168">`dotnet` Yardımcı olan bir paket oluşturur bir *.nupkg* uzantısı.</span><span class="sxs-lookup"><span data-stu-id="a1347-168">The `dotnet` utility generates a package with a *.nupkg* extension.</span></span>

   > [!TIP]
   > <span data-ttu-id="a1347-169">Dizin, içerip içermediğini *dotnet.exe* olduğu değil, yolu girerek konumunda bulabilirsiniz `where dotnet.exe` konsol penceresinde.</span><span class="sxs-lookup"><span data-stu-id="a1347-169">If the directory that contains *dotnet.exe* is not in your PATH, you can find its location by entering `where dotnet.exe` in the console window.</span></span>

<span data-ttu-id="a1347-170">NuGet paketleri oluşturma hakkında daha fazla bilgi için bkz: [Çapraz Platform araçları ile bir NuGet paketi oluşturma](../../core/deploying/creating-nuget-packages.md).</span><span class="sxs-lookup"><span data-stu-id="a1347-170">For more information on creating NuGet packages, see [How to Create a NuGet Package with Cross Platform Tools](../../core/deploying/creating-nuget-packages.md).</span></span>
