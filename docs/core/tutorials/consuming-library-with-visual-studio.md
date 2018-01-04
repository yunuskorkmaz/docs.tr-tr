---
title: "Visual Studio 2017 .NET çekirdek ile bir sınıf kitaplığı kullanma"
description: "Visual Studio 2017 ile bir sınıf kitaplığı'nda üyeleri çağrı öğrenin."
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
ms.topic: article
ms.prod: .net-core
dev_langs:
- csharp
- vb
ms.workload: dotnetcore
ms.openlocfilehash: 1525bd3f9d249fe39fd65b53bc8d1e8eddb09ab9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="consuming-a-class-library-with-net-core-in-visual-studio-2017"></a><span data-ttu-id="99651-103">Visual Studio 2017 .NET çekirdek ile bir sınıf kitaplığı kullanma</span><span class="sxs-lookup"><span data-stu-id="99651-103">Consuming a class library with .NET Core in Visual Studio 2017</span></span>

<span data-ttu-id="99651-104">Bir sınıf kitaplığı'ndaki adımları izleyerek oluşturduktan sonra [bir Visual Studio 2017 .NET çekirdek ile C# sınıf kitaplığı oluşturma](./library-with-visual-studio.md) veya [bir Visual Basic sınıf kitaplığı ile Visual Studio 2017 .NET çekirdek oluşturma](vb-library-with-visual-studio.md), içinde test [Visual Studio 2017 içinde bir sınıf kitaplığı .NET Core ile test](testing-library-with-visual-studio.md), ve bir kitaplık sürümü oluşturulmuş, sonraki adıma arayanlara kullanılabilir hale getirmek için.</span><span class="sxs-lookup"><span data-stu-id="99651-104">Once you've created a class library by following the steps in [Building a C# class library with .NET Core in Visual Studio 2017](./library-with-visual-studio.md) or [Building a Visual Basic class library with .NET Core in Visual Studio 2017](vb-library-with-visual-studio.md), tested it in [Testing a class library with .NET Core in Visual Studio 2017](testing-library-with-visual-studio.md), and built a Release version of the library, the next step is to make it available to callers.</span></span> <span data-ttu-id="99651-105">Bunu iki şekilde yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="99651-105">You can do this in two ways:</span></span>

* <span data-ttu-id="99651-106">(Örneğin, bir bileşenin tek bir büyük uygulama ise) tek bir çözüm tarafından kullanılacak kitaplık, çözümünüz içinde bir proje olarak ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99651-106">If the library will be used by a single solution (for example, if it's a component in a single large application), you can include it as a project in your solution.</span></span>

* <span data-ttu-id="99651-107">Kitaplık genellikle erişilemese, bir NuGet paketi olarak dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99651-107">If the library will be generally accessible, you can distribute it as a NuGet package.</span></span>

## <a name="including-a-library-as-a-project-in-a-solution"></a><span data-ttu-id="99651-108">Bir kitaplık bir çözümdeki bir proje ile dahil olmak üzere</span><span class="sxs-lookup"><span data-stu-id="99651-108">Including a library as a project in a solution</span></span>

<span data-ttu-id="99651-109">Sınıf kitaplığı olarak aynı çözümde birim testleri dahil gibi uygulamanız bu çözümün parçası olarak dahil edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99651-109">Just as you included unit tests in the same solution as your class library, you can include your application as part of that solution.</span></span> <span data-ttu-id="99651-110">Örneğin, sınıf kitaplığınızda ilk karakter büyük olup bir dize ve raporları girmesini ister bir konsol uygulaması kullanarak şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="99651-110">For example, you can use your class library in a console application that prompts the user to enter a string and reports whether its first character is uppercase:</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="99651-111">C#</span><span class="sxs-lookup"><span data-stu-id="99651-111">C#</span></span>](#tab/csharp)
1. <span data-ttu-id="99651-112">Açık `ClassLibraryProjects` oluşturduğunuz çözüm [bir Visual Studio 2017 .NET çekirdek ile C# sınıf kitaplığı oluşturmak](./library-with-visual-studio.md) konu.</span><span class="sxs-lookup"><span data-stu-id="99651-112">Open the `ClassLibraryProjects` solution you created in the [Building a C# Class Library with .NET Core in Visual Studio 2017](./library-with-visual-studio.md) topic.</span></span> <span data-ttu-id="99651-113">İçinde **Çözüm Gezgini**, sağ **ClassLibraryProjects** çözümü ve select **Ekle** > **yeni proje** gelen bağlam menüsü.</span><span class="sxs-lookup"><span data-stu-id="99651-113">In **Solution Explorer**, right-click the **ClassLibraryProjects** solution and select **Add** > **New Project** from the context menu.</span></span>

1. <span data-ttu-id="99651-114">İçinde **Yeni Proje Ekle** iletişim kutusunda, genişletin **Visual C#** düğümü ve select **.NET Core** düğümünü ve ardından **konsol uygulaması (.NET Core)** Proje şablonu.</span><span class="sxs-lookup"><span data-stu-id="99651-114">In the **Add New Project** dialog, expand the **Visual C#** node and select the **.NET Core** node followed by the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="99651-115">İçinde **adı** metin kutusu, "Gösterimi" yazın ve seçin **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="99651-115">In the **Name** text box, type "ShowCase", and select the **OK** button.</span></span>

   ![Yeni Proje iletişim kutusu ekleme](./media/consuming-library-with-visual-studio/addnewproject.png)

1. <span data-ttu-id="99651-117">İçinde **Çözüm Gezgini**, sağ **gösterimi** proje ve seçin **başlangıç projesi olarak ayarla** bağlam menüsünde.</span><span class="sxs-lookup"><span data-stu-id="99651-117">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span> 

   ![Gösterimi bağlam menüsü](./media/consuming-library-with-visual-studio/setstartupproject.png)

1. <span data-ttu-id="99651-119">Başlangıçta, projenizin Sınıf Kitaplığı'na erişimi yok.</span><span class="sxs-lookup"><span data-stu-id="99651-119">Initially, your project doesn't have access to your class library.</span></span> <span data-ttu-id="99651-120">Sınıf Kitaplığı'nda yöntemlerini çağırmaya izin vermek için sınıf kitaplığına bir başvuru oluşturun.</span><span class="sxs-lookup"><span data-stu-id="99651-120">To allow it to call methods in your class library, you create a reference to the class library.</span></span> <span data-ttu-id="99651-121">İçinde **Çözüm Gezgini**, sağ `ShowCase` projenin **bağımlılıkları** düğümü ve select **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="99651-121">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node and select **Add Reference**.</span></span>

   ![Gösterimi bağımlılıkları bağlam menüsü](./media/consuming-library-with-visual-studio/addreference.png)

1. <span data-ttu-id="99651-123">İçinde **başvuru Yöneticisi** iletişim kutusunda **StringLibrary**, sınıf kitaplığı proje ve seçin **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="99651-123">In the **Reference Manager** dialog, select **StringLibrary**, your class library project, and select the **OK** button.</span></span>

   ![Başvuru Yöneticisi](./media/consuming-library-with-visual-studio/referencemanager.png)

1. <span data-ttu-id="99651-125">Kod penceresinde *Program.cs* dosya, tüm kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="99651-125">In the code window for the *Program.cs* file, replace all of the code with the following code:</span></span>

   [!CODE-csharp[UsingClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]

   <span data-ttu-id="99651-126">Kod kullanan [Console.WindowHeight](xref:System.Console.WindowHeight) konsol penceresinde satır sayısını belirlemek için özelliği.</span><span class="sxs-lookup"><span data-stu-id="99651-126">The code uses the [Console.WindowHeight](xref:System.Console.WindowHeight) property to determine the number of rows in the console window.</span></span> <span data-ttu-id="99651-127">Her [Console.CursorTop](xref:System.Console.CursorTop) özelliği büyüktür veya konsol penceresi satır sayısına eşit, kod konsol penceresini temizler ve kullanıcı için bir ileti görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="99651-127">Whenever the [Console.CursorTop](xref:System.Console.CursorTop) property is greater than or equal to the number of rows in the console window, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="99651-128">Program kullanıcının bir dize girmesini ister.</span><span class="sxs-lookup"><span data-stu-id="99651-128">The program prompts the user to enter a string.</span></span> <span data-ttu-id="99651-129">Bu dize bir büyük harf karakter ile başlayıp başlamadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="99651-129">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="99651-130">Kullanıcı, bir dize girmeden Enter tuşuna basarsa, uygulama sonlandırır ve konsol penceresi kapanır.</span><span class="sxs-lookup"><span data-stu-id="99651-130">If the user presses the Enter key without entering a string, the application terminates, and the console window closes.</span></span>

1. <span data-ttu-id="99651-131">Gerekirse, derleme için araç çubuğunda değiştirmek **hata ayıklama** sürümü, `ShowCase` projesi.</span><span class="sxs-lookup"><span data-stu-id="99651-131">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="99651-132">Derleme ve üzerinde yeşil ok seçerek program çalıştırma **gösterimi** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="99651-132">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![Görüntü](./media/consuming-library-with-visual-studio/toolbar.png)
# <a name="visual-basictabvisual-basic"></a>[<span data-ttu-id="99651-134">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="99651-134">Visual Basic</span></span>](#tab/visual-basic)
1. <span data-ttu-id="99651-135">Açık `ClassLibraryProjects` oluşturduğunuz çözüm [sınıfı Visual Basic ve Visual Studio 2017 .NET Core kitaplığı oluşturma](vb-library-with-visual-studio.md) konu.</span><span class="sxs-lookup"><span data-stu-id="99651-135">Open the `ClassLibraryProjects` solution you created in the [Building a class Library with Visual Basic and .NET Core in Visual Studio 2017](vb-library-with-visual-studio.md) topic.</span></span> <span data-ttu-id="99651-136">İçinde **Çözüm Gezgini**, sağ **ClassLibraryProjects** çözümü ve select **Ekle** > **yeni proje** gelen bağlam menüsü.</span><span class="sxs-lookup"><span data-stu-id="99651-136">In **Solution Explorer**, right-click the **ClassLibraryProjects** solution and select **Add** > **New Project** from the context menu.</span></span>

1. <span data-ttu-id="99651-137">İçinde **Yeni Proje Ekle** iletişim kutusunda, genişletin **Visual Basic** düğümü ve select **.NET Core** düğümünü ve ardından **konsol uygulaması (.NET Core)**proje şablonu.</span><span class="sxs-lookup"><span data-stu-id="99651-137">In the **Add New Project** dialog, expand the **Visual Basic** node and select the **.NET Core** node followed by the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="99651-138">İçinde **adı** metin kutusu, "Gösterimi" yazın ve seçin **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="99651-138">In the **Name** text box, type "ShowCase", and select the **OK** button.</span></span>

   ![Yeni Proje iletişim kutusu ekleme](./media/consuming-library-with-visual-studio/vb-addnewproject.png)

1. <span data-ttu-id="99651-140">İçinde **Çözüm Gezgini**, sağ **gösterimi** proje ve seçin **başlangıç projesi olarak ayarla** bağlam menüsünde.</span><span class="sxs-lookup"><span data-stu-id="99651-140">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span> 

   ![Gösterimi bağlam menüsü](./media/consuming-library-with-visual-studio/setstartupproject.png)

1. <span data-ttu-id="99651-142">Başlangıçta, projenizin Sınıf Kitaplığı'na erişimi yok.</span><span class="sxs-lookup"><span data-stu-id="99651-142">Initially, your project doesn't have access to your class library.</span></span> <span data-ttu-id="99651-143">Sınıf Kitaplığı'nda yöntemlerini çağırmaya izin vermek için sınıf kitaplığına bir başvuru oluşturun.</span><span class="sxs-lookup"><span data-stu-id="99651-143">To allow it to call methods in your class library, you create a reference to the class library.</span></span> <span data-ttu-id="99651-144">İçinde **Çözüm Gezgini**, sağ `ShowCase` projenin **bağımlılıkları** düğümü ve select **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="99651-144">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node and select **Add Reference**.</span></span>

   ![Gösterimi bağımlılıkları bağlam menüsü](./media/consuming-library-with-visual-studio/addreference.png)

1. <span data-ttu-id="99651-146">İçinde **başvuru Yöneticisi** iletişim kutusunda **StringLibrary**, sınıf kitaplığı proje ve seçin **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="99651-146">In the **Reference Manager** dialog, select **StringLibrary**, your class library project, and select the **OK** button.</span></span>

   ![Başvuru Yöneticisi](./media/consuming-library-with-visual-studio/referencemanager.png)

1. <span data-ttu-id="99651-148">Kod penceresinde *Program.vb* dosya, tüm kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="99651-148">In the code window for the *Program.vb* file, replace all of the code with the following code:</span></span>

    [!CODE-vb[UsingClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   <span data-ttu-id="99651-149">Kod kullanan [Console.WindowHeight](xref:System.Console.WindowHeight) konsol penceresinde satır sayısını belirlemek için özelliği.</span><span class="sxs-lookup"><span data-stu-id="99651-149">The code uses the [Console.WindowHeight](xref:System.Console.WindowHeight) property to determine the number of rows in the console window.</span></span> <span data-ttu-id="99651-150">Her [Console.CursorTop](xref:System.Console.CursorTop) özelliği büyüktür veya konsol penceresi satır sayısına eşit, kod konsol penceresini temizler ve kullanıcı için bir ileti görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="99651-150">Whenever the [Console.CursorTop](xref:System.Console.CursorTop) property is greater than or equal to the number of rows in the console window, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="99651-151">Program kullanıcının bir dize girmesini ister.</span><span class="sxs-lookup"><span data-stu-id="99651-151">The program prompts the user to enter a string.</span></span> <span data-ttu-id="99651-152">Bu dize bir büyük harf karakter ile başlayıp başlamadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="99651-152">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="99651-153">Kullanıcı, bir dize girmeden Enter tuşuna basarsa, uygulama sonlandırır ve konsol penceresi kapanır.</span><span class="sxs-lookup"><span data-stu-id="99651-153">If the user presses the Enter key without entering a string, the application terminates, and the console window closes.</span></span>

1. <span data-ttu-id="99651-154">Gerekirse, derleme için araç çubuğunda değiştirmek **hata ayıklama** sürümü, `ShowCase` projesi.</span><span class="sxs-lookup"><span data-stu-id="99651-154">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="99651-155">Derleme ve üzerinde yeşil ok seçerek program çalıştırma **gösterimi** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="99651-155">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![Görüntü](./media/consuming-library-with-visual-studio/toolbar.png)
---

<span data-ttu-id="99651-157">Hata ayıklama ve içindeki adımları izleyerek bu kitaplığı kullanan uygulama yayımlama [Hello World uygulamanızı Visual Studio 2017 ile hata ayıklama](debugging-with-visual-studio.md) ve [Hello World uygulamanızı Visual Studio ile yayımlama 2017](publishing-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="99651-157">You can debug and publish the application that uses this library by following the steps in [Debugging your Hello World application with Visual Studio 2017](debugging-with-visual-studio.md) and [Publishing your Hello World Application with Visual Studio 2017](publishing-with-visual-studio.md).</span></span>

## <a name="distributing-the-library-in-a-nuget-package"></a><span data-ttu-id="99651-158">Bir NuGet paketi kitaplıkta dağıtma</span><span class="sxs-lookup"><span data-stu-id="99651-158">Distributing the library in a NuGet package</span></span>

<span data-ttu-id="99651-159">Bir NuGet paketi olarak yayımlayarak, sınıf kitaplığı yaygın olarak kullanılabilir hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99651-159">You can make your class library widely available by publishing it as a NuGet package.</span></span> <span data-ttu-id="99651-160">Visual Studio NuGet paketlerini oluşturulmasını desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="99651-160">Visual Studio does not support the creation of NuGet packages.</span></span> <span data-ttu-id="99651-161">Oluşturmak için kullandığınız [ `dotnet` komut satırı yardımcı programı](../../core/tools/dotnet.md):</span><span class="sxs-lookup"><span data-stu-id="99651-161">To create one, you use the [`dotnet` command line utility](../../core/tools/dotnet.md):</span></span>

1. <span data-ttu-id="99651-162">Bir konsol penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="99651-162">Open a console window.</span></span> <span data-ttu-id="99651-163">Örneğin **herhangi bir şey sor** metin kutusunda Windows görev çubuğundaki, girin `Command Prompt` (veya `cmd` kısaca) ve seçerek bir konsol penceresi açın **komut istemi** masaüstü uygulaması veya arama sonuçlarında seçtiyseniz Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="99651-163">For example in the **Ask me anything** text box in the Windows taskbar, enter `Command Prompt` (or `cmd` for short), and open a console window by either selecting the **Command Prompt** desktop app or pressing Enter if it's selected in the search results.</span></span>

1. <span data-ttu-id="99651-164">Kitaplığınızın proje dizinine gidin.</span><span class="sxs-lookup"><span data-stu-id="99651-164">Navigate to your library's project directory.</span></span> <span data-ttu-id="99651-165">Tipik dosya konumunu yeniden sürece, konusu *Documents\Visual Studio 2017\Projects\ClassLibraryProjects\StringLibrary* dizini.</span><span class="sxs-lookup"><span data-stu-id="99651-165">Unless you've reconfigured the typical file location, it's in the *Documents\Visual Studio 2017\Projects\ClassLibraryProjects\StringLibrary* directory.</span></span> <span data-ttu-id="99651-166">Kaynak kodunuz ve bir proje dosyası dizini içeren *StringLibrary.csproj*.</span><span class="sxs-lookup"><span data-stu-id="99651-166">The directory contains your source code and a project file, *StringLibrary.csproj*.</span></span>

1. <span data-ttu-id="99651-167">Komutu Yürüt `dotnet pack --no-build`.</span><span class="sxs-lookup"><span data-stu-id="99651-167">Issue the command `dotnet pack --no-build`.</span></span> <span data-ttu-id="99651-168">`dotnet` Yardımcı olan bir paket oluşturur bir *.nupkg* uzantısı.</span><span class="sxs-lookup"><span data-stu-id="99651-168">The `dotnet` utility generates a package with a *.nupkg* extension.</span></span>

   > [!TIP]
   > <span data-ttu-id="99651-169">Dizin, içeriyorsa *dotnet.exe* olduğundan, YOLUNUZDA değil girerek konumunda bulabilirsiniz `where dotnet.exe` konsol penceresinde.</span><span class="sxs-lookup"><span data-stu-id="99651-169">If the directory that contains *dotnet.exe* is not in your PATH, you can find its location by entering `where dotnet.exe` in the console window.</span></span>

<span data-ttu-id="99651-170">NuGet paketleri oluşturma hakkında daha fazla bilgi için bkz: [Çapraz Platform araçları ile bir NuGet paketi oluşturmak nasıl](../../core/deploying/creating-nuget-packages.md).</span><span class="sxs-lookup"><span data-stu-id="99651-170">For more information on creating NuGet packages, see [How to Create a NuGet Package with Cross Platform Tools](../../core/deploying/creating-nuget-packages.md).</span></span>
