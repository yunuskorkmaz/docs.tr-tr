---
title: Visual Studio Code kullanarak .NET Standard sınıf kitaplığı oluşturma
description: Visual Studio Code kullanarak .NET Standard sınıf kitaplığı oluşturmayı öğrenin.
ms.date: 06/08/2020
ms.openlocfilehash: d37e3c663146c90f4ae4188b25ea7e501501c93b
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465292"
---
# <a name="tutorial-create-a-net-standard-library-using-visual-studio-code"></a><span data-ttu-id="2ad20-103">Öğretici: Visual Studio Code kullanarak .NET Standard kitaplığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="2ad20-103">Tutorial: Create a .NET Standard library using Visual Studio Code</span></span>

<span data-ttu-id="2ad20-104">Bu öğreticide, tek bir dize işleme yöntemi içeren basit bir yardımcı program kitaplığı oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="2ad20-104">In this tutorial, you create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="2ad20-105">Bunu, sınıfının bir üyesi gibi çağırabilmeniz için bir [genişletme yöntemi](../../csharp/programming-guide/classes-and-structs/extension-methods.md) olarak uygulamalısınız <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="2ad20-105">You implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

<span data-ttu-id="2ad20-106">Bir *sınıf kitaplığı* , bir uygulama tarafından çağrılan türleri ve yöntemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2ad20-106">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="2ad20-107">.NET Standard 2,0 ' i hedefleyen bir sınıf kitaplığı, kitaplığınızın bu .NET Standard sürümünü destekleyen herhangi bir .NET uygulamasının çağrılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="2ad20-107">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span> <span data-ttu-id="2ad20-108">Sınıf kitaplığınızı bitirdiğinizde, bir üçüncü taraf bileşen olarak veya bir veya daha fazla uygulamayla paketlenmiş bileşen olarak dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2ad20-108">When you finish your class library, you can distribute it as a third-party component or as a bundled component with one or more applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2ad20-109">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="2ad20-109">Prerequisites</span></span>

1. <span data-ttu-id="2ad20-110">[C# uzantısı](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) yüklü [Visual Studio Code](https://code.visualstudio.com/) .</span><span class="sxs-lookup"><span data-stu-id="2ad20-110">[Visual Studio Code](https://code.visualstudio.com/) with the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) installed.</span></span> <span data-ttu-id="2ad20-111">Visual Studio Code uzantıları nasıl yükleyeceğiniz hakkında daha fazla bilgi için bkz. [vs Code uzantısı marketi](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="2ad20-111">For information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>
2. <span data-ttu-id="2ad20-112">[.NET Core 3,1 SDK veya üzeri](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="2ad20-112">The [.NET Core 3.1 SDK or later](https://dotnet.microsoft.com/download)</span></span>

## <a name="create-a-solution"></a><span data-ttu-id="2ad20-113">Çözüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="2ad20-113">Create a solution</span></span>

<span data-ttu-id="2ad20-114">' De Sınıf Kitaplığı projesini yerleştirmek için boş bir çözüm oluşturarak başlayın.</span><span class="sxs-lookup"><span data-stu-id="2ad20-114">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="2ad20-115">Bir çözüm, bir veya daha fazla proje için kapsayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="2ad20-115">A solution serves as a container for one or more projects.</span></span> <span data-ttu-id="2ad20-116">Aynı çözüme ek ve ilgili projeler ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="2ad20-116">You'll add additional, related projects to the same solution.</span></span>

1. <span data-ttu-id="2ad20-117">Visual Studio Code’u başlatma.</span><span class="sxs-lookup"><span data-stu-id="2ad20-117">Start Visual Studio Code.</span></span>

1. <span data-ttu-id="2ad20-118">Ana menüden **Dosya**  >  **açma klasörünü** (MacOS üzerinde**Open...** ) seçin</span><span class="sxs-lookup"><span data-stu-id="2ad20-118">Select **File** > **Open Folder** (**Open...** on macOS) from the main menu</span></span>

1. <span data-ttu-id="2ad20-119">**Klasörü aç** iletişim kutusunda bir *classlibraryprojects* klasörü oluşturun ve **Klasör Seç** ' e tıklayın (MacOS üzerinde**açın** ).</span><span class="sxs-lookup"><span data-stu-id="2ad20-119">In the **Open Folder** dialog, create a *ClassLibraryProjects* folder and click **Select Folder** (**Open** on macOS).</span></span>

1. <span data-ttu-id="2ad20-120">Ana menüden **Terminal görünümü ' nu** seçerek **View**Visual Studio Code açın  >  **Terminal** .</span><span class="sxs-lookup"><span data-stu-id="2ad20-120">Open the **Terminal** in Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>

   <span data-ttu-id="2ad20-121">**Terminal** , *classlibraryprojects* klasöründe komut istemiyle açılır.</span><span class="sxs-lookup"><span data-stu-id="2ad20-121">The **Terminal** opens with the command prompt in the *ClassLibraryProjects* folder.</span></span>

1. <span data-ttu-id="2ad20-122">**Terminalde**aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="2ad20-122">In the **Terminal**, enter the following command:</span></span>

   ```dotnetcli
   dotnet new sln
   ```

   <span data-ttu-id="2ad20-123">Terminal çıktısı aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="2ad20-123">The terminal output looks like the following example:</span></span>

   ```output
   The template "Solution File" was created successfully.
   ```

## <a name="create-a-class-library-project"></a><span data-ttu-id="2ad20-124">Sınıf kitaplığı projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="2ad20-124">Create a class library project</span></span>

<span data-ttu-id="2ad20-125">Çözüme "StringLibrary" adlı yeni bir .NET Standard sınıf kitaplığı projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2ad20-125">Add a new .NET Standard class library project named "StringLibrary" to the solution.</span></span>

1. <span data-ttu-id="2ad20-126">Terminalde, kitaplık projesini oluşturmak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="2ad20-126">In the terminal, run the following command to create the library project:</span></span>

   ```dotnetcli
   dotnet new classlib -o StringLibrary
   ```

   <span data-ttu-id="2ad20-127">`-o`Or `--output` komutu oluşturulan çıkışın yerleştirileceği konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2ad20-127">The `-o` or `--output` command specifies the location to place the generated output.</span></span>

   <span data-ttu-id="2ad20-128">Terminal çıktısı aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="2ad20-128">The terminal output looks like the following example:</span></span>

   ```output
   The template "Class library" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on StringLibrary\StringLibrary.csproj...
     Determining projects to restore...
     Restore completed in 328.13 ms for C:\Projects\ClassLibraryProjects\StringLibrary\StringLibrary.csproj.
   Restore succeeded.
   ```

1. <span data-ttu-id="2ad20-129">Kitaplık projesini çözüme eklemek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="2ad20-129">Run the following command to add the library project to the solution:</span></span>

   ```dotnetcli
   dotnet sln add StringLibrary/StringLibrary.csproj
   ```

   <span data-ttu-id="2ad20-130">Terminal çıktısı aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="2ad20-130">The terminal output looks like the following example:</span></span>

   ```output
   Project `StringLibrary\StringLibrary.csproj` added to the solution.
   ```

1. <span data-ttu-id="2ad20-131">Kitaplığın doğru .NET Standard sürümünü hedeflediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="2ad20-131">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="2ad20-132">**Gezgin**'de *StringLibrary/StringLibrary. csproj*öğesini açın.</span><span class="sxs-lookup"><span data-stu-id="2ad20-132">In **Explorer**, open *StringLibrary/StringLibrary.csproj*.</span></span>

   <span data-ttu-id="2ad20-133">`TargetFramework`Öğesi, projenin 2,0 .NET Standard hedeflediği gösterir.</span><span class="sxs-lookup"><span data-stu-id="2ad20-133">The `TargetFramework` element shows that the project targets .NET Standard 2.0.</span></span>

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">

     <PropertyGroup>
       <TargetFramework>netstandard2.0</TargetFramework>
     </PropertyGroup>

   </Project>
   ```

1. <span data-ttu-id="2ad20-134">*Class1.cs* ' i açın ve kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="2ad20-134">Open *Class1.cs* and replace the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

   <span data-ttu-id="2ad20-135">Sınıf kitaplığı, `UtilityLibraries.StringLibrary` adlı bir yöntemi içerir `StartsWithUpper` .</span><span class="sxs-lookup"><span data-stu-id="2ad20-135">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="2ad20-136">Bu yöntem <xref:System.Boolean> , geçerli dize örneğinin büyük harfli bir karakterle başlayıp başlamadığını belirten bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="2ad20-136">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="2ad20-137">Unicode standart, büyük harfli karakterleri küçük harfli karakterlerden ayırır.</span><span class="sxs-lookup"><span data-stu-id="2ad20-137">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="2ad20-138"><xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> `true` Bir karakter büyük harfli ise, yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="2ad20-138">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="2ad20-139">Dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="2ad20-139">Save the file.</span></span>

1. <span data-ttu-id="2ad20-140">Çözümü derlemek ve projenin hatasız derlendiğinden emin olmak için aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2ad20-140">Run the following command to build the solution and verify that the project compiles without error.</span></span>

   ```dotnetcli
   dotnet build
   ```

   <span data-ttu-id="2ad20-141">Terminal çıktısı aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="2ad20-141">The terminal output looks like the following example:</span></span>

   ```output
   Microsoft (R) Build Engine version 16.6.0 for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.
     Determining projects to restore...
     All projects are up-to-date for restore.
     You are using a preview version of .NET Core. See: https://aka.ms/dotnet-core-preview
     StringLibrary -> C:\Projects\ClassLibraryProjects\StringLibrary\bin\Debug\netstandard2.0\StringLibrary.dll
   Build succeeded.
       0 Warning(s)
       0 Error(s)
   Time Elapsed 00:00:02.78
   ```

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="2ad20-142">Çözüme bir konsol uygulaması ekleme</span><span class="sxs-lookup"><span data-stu-id="2ad20-142">Add a console app to the solution</span></span>

<span data-ttu-id="2ad20-143">Sınıf kitaplığını kullanan bir konsol uygulaması ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2ad20-143">Add a console application that uses the class library.</span></span> <span data-ttu-id="2ad20-144">Uygulama kullanıcıdan bir dize girmesini ister ve dizenin büyük harfli bir karakterle başlayıp başlamamadığını rapor eder.</span><span class="sxs-lookup"><span data-stu-id="2ad20-144">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="2ad20-145">Terminalde, konsol uygulama projesini oluşturmak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="2ad20-145">In the terminal, run the following command to create the console app project:</span></span>

   ```dotnetcli
   dotnet new console -o ShowCase
   ```

   <span data-ttu-id="2ad20-146">Terminal çıktısı aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="2ad20-146">The terminal output looks like the following example:</span></span>

   ```output
   The template "Console Application" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on ShowCase\ShowCase.csproj...  
     Determining projects to restore...
     Restore completed in 210.78 ms for C:\Projects\ClassLibraryProjects\ShowCase\ShowCase.csproj.
   Restore succeeded.
   ```

1. <span data-ttu-id="2ad20-147">Konsol uygulaması projesini çözüme eklemek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="2ad20-147">Run the following command to add the console app project to the solution:</span></span>

   ```dotnetcli
   dotnet sln add ShowCase/ShowCase.csproj
   ```

   <span data-ttu-id="2ad20-148">Terminal çıktısı aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="2ad20-148">The terminal output looks like the following example:</span></span>

   ```output
   Project `ShowCase\ShowCase.csproj` added to the solution.
   ```

1. <span data-ttu-id="2ad20-149">*Gösterimi/program. cs* ' i açın ve kodun tümünü aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="2ad20-149">Open *ShowCase/Program.cs* and replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   <span data-ttu-id="2ad20-150">Kod, `row` konsol penceresine yazılan veri satırlarının sayısını korumak için değişkenini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2ad20-150">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="2ad20-151">25 ' e eşit veya daha büyük olduğunda, kod konsol penceresini temizler ve kullanıcıya bir ileti görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2ad20-151">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="2ad20-152">Program kullanıcıdan bir dize girmesini ister.</span><span class="sxs-lookup"><span data-stu-id="2ad20-152">The program prompts the user to enter a string.</span></span> <span data-ttu-id="2ad20-153">Dizenin büyük harfle başlatılıp başlatılmayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2ad20-153">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="2ad20-154">Kullanıcı bir dize girmeden <kbd>ENTER</kbd> tuşuna basarsa, uygulama sonlanır ve konsol penceresi kapanır.</span><span class="sxs-lookup"><span data-stu-id="2ad20-154">If the user presses the <kbd>Enter</kbd> key without entering a string, the application ends, and the console window closes.</span></span>

1. <span data-ttu-id="2ad20-155">Yaptığınız değişiklikleri kaydedin.</span><span class="sxs-lookup"><span data-stu-id="2ad20-155">Save your changes.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="2ad20-156">Proje başvurusu Ekle</span><span class="sxs-lookup"><span data-stu-id="2ad20-156">Add a project reference</span></span>

<span data-ttu-id="2ad20-157">Başlangıçta, yeni konsol uygulaması projesi sınıf kitaplığına erişemez.</span><span class="sxs-lookup"><span data-stu-id="2ad20-157">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="2ad20-158">Sınıf kitaplığındaki yöntemleri çağırmasına izin vermek için, sınıf kitaplığı projesine bir proje başvurusu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2ad20-158">To allow it to call methods in the class library, create a project reference to the class library project.</span></span>

1. <span data-ttu-id="2ad20-159">Şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="2ad20-159">Run the following command:</span></span>

   ```dotnetcli
   dotnet add ShowCase/ShowCase.csproj reference StringLibrary/StringLibrary.csproj
   ```

   <span data-ttu-id="2ad20-160">Terminal çıktısı aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="2ad20-160">The terminal output looks like the following example:</span></span>

   ```output
   Reference `..\StringLibrary\StringLibrary.csproj` added to the project.
   ```

## <a name="run-the-app"></a><span data-ttu-id="2ad20-161">Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="2ad20-161">Run the app</span></span>

1. <span data-ttu-id="2ad20-162">Terminalde aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="2ad20-162">Run the following command in the terminal:</span></span>

   ```dotnetcli
   dotnet run --project ShowCase/ShowCase.csproj
   ```

1. <span data-ttu-id="2ad20-163">Dizeleri girerek ve <kbd>ENTER</kbd>'a basarak programı deneyin ve çıkmak için <kbd>ENTER</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="2ad20-163">Try out the program by entering strings and pressing <kbd>Enter</kbd>, then press <kbd>Enter</kbd> to exit.</span></span>

   <span data-ttu-id="2ad20-164">Terminal çıktısı aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="2ad20-164">The terminal output looks like the following example:</span></span>

   ```output
   Press <Enter> only to exit; otherwise, enter a string and press <Enter>:

   A string that starts with an uppercase letter
   Input: A string that starts with an uppercase letter
   Begins with uppercase? : Yes

   a string that starts with a lowercase letter
   Input: a string that starts with a lowercase letter
   Begins with uppercase? : No
   ```

## <a name="additional-resources"></a><span data-ttu-id="2ad20-165">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="2ad20-165">Additional resources</span></span>

* [<span data-ttu-id="2ad20-166">.NET Core CLI ile Kitaplıklar geliştirin</span><span class="sxs-lookup"><span data-stu-id="2ad20-166">Develop libraries with the .NET Core CLI</span></span>](libraries.md)
* <span data-ttu-id="2ad20-167">[.NET Standard sürümleri ve destekledikleri platformlar](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="2ad20-167">[.NET Standard versions and the platforms they support](../../standard/net-standard.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="2ad20-168">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="2ad20-168">Next steps</span></span>

<span data-ttu-id="2ad20-169">Bu öğreticide, bir çözüm oluşturdunuz, bir kitaplık projesi eklediniz ve kitaplığı kullanan bir konsol uygulaması projesi ekledik.</span><span class="sxs-lookup"><span data-stu-id="2ad20-169">In this tutorial, you created a solution, added a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="2ad20-170">Sonraki öğreticide, çözüme bir birim testi projesi eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="2ad20-170">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2ad20-171">Visual Studio Code kullanarak .NET Core ile .NET Standard kitaplığı test etme</span><span class="sxs-lookup"><span data-stu-id="2ad20-171">Test a .NET Standard library with .NET Core using Visual Studio Code</span></span>](testing-library-with-visual-studio-code.md)
