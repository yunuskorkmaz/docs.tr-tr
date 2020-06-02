---
title: Visual Studio Code .NET Standard sınıf kitaplığı oluşturma
description: Visual Studio Code kullanarak .NET Standard sınıf kitaplığı oluşturmayı öğrenin.
ms.date: 05/29/2020
ms.openlocfilehash: 10c832f5817292b366dc816aebada2dfdab11396
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84292205"
---
# <a name="tutorial-create-a-net-standard-library-in-visual-studio-code"></a><span data-ttu-id="55ab7-103">Öğretici: Visual Studio Code .NET Standard kitaplığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="55ab7-103">Tutorial: Create a .NET Standard library in Visual Studio Code</span></span>

<span data-ttu-id="55ab7-104">Bir *sınıf kitaplığı* , bir uygulama tarafından çağrılan türleri ve yöntemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="55ab7-104">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="55ab7-105">.NET Standard 2,0 ' i hedefleyen bir sınıf kitaplığı, kitaplığınızın bu .NET Standard sürümünü destekleyen herhangi bir .NET uygulamasının çağrılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="55ab7-105">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span> <span data-ttu-id="55ab7-106">Sınıf kitaplığınızı bitirdiğinizde, bir NuGet paketi olarak dağıtmak mı yoksa bir veya daha fazla uygulamayla paketlenmiş bir bileşen olarak eklemek mi istediğinize karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55ab7-106">When you finish your class library, you can decide whether you want to distribute it as a NuGet package or include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="55ab7-107">.NET Standard sürümlerinin ve destekledikleri platformların listesi için bkz. [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="55ab7-107">For a list of .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="55ab7-108">Bu öğreticide, tek bir dize işleme yöntemi içeren basit bir yardımcı program kitaplığı oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="55ab7-108">In this tutorial, you create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="55ab7-109">Bunu, sınıfının bir üyesi gibi çağırabilmeniz için bir [genişletme yöntemi](../../csharp/programming-guide/classes-and-structs/extension-methods.md) olarak uygulamalısınız <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="55ab7-109">You implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="55ab7-110">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="55ab7-110">Prerequisites</span></span>

1. <span data-ttu-id="55ab7-111">[C# uzantısı](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) yüklü [Visual Studio Code](https://code.visualstudio.com/) .</span><span class="sxs-lookup"><span data-stu-id="55ab7-111">[Visual Studio Code](https://code.visualstudio.com/) with the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) installed.</span></span> <span data-ttu-id="55ab7-112">Visual Studio Code uzantıları nasıl yükleyeceğiniz hakkında daha fazla bilgi için bkz. [vs Code uzantısı marketi](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="55ab7-112">For information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>
2. <span data-ttu-id="55ab7-113">[.NET Core 3,1 SDK veya üzeri](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="55ab7-113">The [.NET Core 3.1 SDK or later](https://dotnet.microsoft.com/download)</span></span>

## <a name="create-a-solution"></a><span data-ttu-id="55ab7-114">Çözüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="55ab7-114">Create a solution</span></span>

<span data-ttu-id="55ab7-115">' De Sınıf Kitaplığı projesini yerleştirmek için boş bir çözüm oluşturarak başlayın.</span><span class="sxs-lookup"><span data-stu-id="55ab7-115">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="55ab7-116">Bir çözüm, bir veya daha fazla proje için kapsayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="55ab7-116">A solution serves as a container for one or more projects.</span></span> <span data-ttu-id="55ab7-117">Aynı çözüme ek ve ilgili projeler ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="55ab7-117">You'll add additional, related projects to the same solution.</span></span>

1. <span data-ttu-id="55ab7-118">Visual Studio Code'u açın.</span><span class="sxs-lookup"><span data-stu-id="55ab7-118">Open Visual Studio Code.</span></span>

1. <span data-ttu-id="55ab7-119">**Dosya**  >  **Aç klasör**aç... ' ı seçin, / **Open...** ana menüden bir *classlibraryprojects* klasörü oluşturun ve klasör aç **Seç**' e tıklayın / **Open**.</span><span class="sxs-lookup"><span data-stu-id="55ab7-119">Select **File** > **Open Folder**/**Open...** from the main menu, create a *ClassLibraryProjects* folder, and click **Select Folder**/**Open**.</span></span>

1. <span data-ttu-id="55ab7-120">Ana menüden **Terminal görünümü ' nu** seçerek **View**Visual Studio Code açın  >  **Terminal** .</span><span class="sxs-lookup"><span data-stu-id="55ab7-120">Open the **Terminal** in Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>

   <span data-ttu-id="55ab7-121">**Terminal** , *classlibraryprojects* klasöründe komut istemiyle açılır.</span><span class="sxs-lookup"><span data-stu-id="55ab7-121">The **Terminal** opens with the command prompt in the *ClassLibraryProjects* folder.</span></span>

1. <span data-ttu-id="55ab7-122">**Terminalde**aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="55ab7-122">In the **Terminal**, enter the following command:</span></span>

   ```dotnetcli
   dotnet new sln
   ```

   <span data-ttu-id="55ab7-123">Terminal çıktısı aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="55ab7-123">The terminal output looks like the following example:</span></span>

   ```
   The template "Solution File" was created successfully.
   ```

## <a name="create-a-class-library-project"></a><span data-ttu-id="55ab7-124">Sınıf kitaplığı projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="55ab7-124">Create a class library project</span></span>

<span data-ttu-id="55ab7-125">Çözüme "StringLibrary" adlı yeni bir .NET Standard sınıf kitaplığı projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="55ab7-125">Add a new .NET Standard class library project named "StringLibrary" to the solution.</span></span>

1. <span data-ttu-id="55ab7-126">Terminalde, kitaplık projesini oluşturmak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="55ab7-126">In the terminal, run the following command to create the library project:</span></span>

   ```dotnetcli
   dotnet new classlib -o StringLibrary
   ```

   <span data-ttu-id="55ab7-127">Terminal çıktısı aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="55ab7-127">The terminal output looks like the following example:</span></span>

   ```
   The template "Class library" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on StringLibrary\StringLibrary.csproj...
     Determining projects to restore...
     Restore completed in 328.13 ms for C:\Projects\ClassLibraryProjects\StringLibrary\StringLibrary.csproj.
   Restore succeeded.
   ```

1. <span data-ttu-id="55ab7-128">Kitaplık projesini çözüme eklemek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="55ab7-128">Run the following command to add the library project to the solution:</span></span>

   ```dotnetcli
   dotnet sln add StringLibrary/StringLibrary.csproj
   ```

   <span data-ttu-id="55ab7-129">Terminal çıktısı aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="55ab7-129">The terminal output looks like the following example:</span></span>

   ```
   Project `StringLibrary\StringLibrary.csproj` added to the solution.
   ```

1. <span data-ttu-id="55ab7-130">Kitaplığın doğru .NET Standard sürümünü hedeflediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="55ab7-130">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="55ab7-131">**Gezgin**'de *StringLibrary/StringLibrary. csproj*öğesini açın.</span><span class="sxs-lookup"><span data-stu-id="55ab7-131">In **Explorer**, open *StringLibrary/StringLibrary.csproj*.</span></span>

   <span data-ttu-id="55ab7-132">`TargetFramework`Öğesi, projenin 2,0 .NET Standard hedeflediği gösterir.</span><span class="sxs-lookup"><span data-stu-id="55ab7-132">The `TargetFramework` element shows that the project targets .NET Standard 2.0.</span></span>

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">

     <PropertyGroup>
       <TargetFramework>netstandard2.0</TargetFramework>
     </PropertyGroup>

   </Project>
   ```

1. <span data-ttu-id="55ab7-133">*Class1.cs* ' i açın ve kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="55ab7-133">Open *Class1.cs* and replace the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

   <span data-ttu-id="55ab7-134">Sınıf kitaplığı, `UtilityLibraries.StringLibrary` adlı bir yöntemi içerir `StartsWithUpper` .</span><span class="sxs-lookup"><span data-stu-id="55ab7-134">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="55ab7-135">Bu yöntem <xref:System.Boolean> , geçerli dize örneğinin büyük harfli bir karakterle başlayıp başlamadığını belirten bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="55ab7-135">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="55ab7-136">Unicode standart, büyük harfli karakterleri küçük harfli karakterlerden ayırır.</span><span class="sxs-lookup"><span data-stu-id="55ab7-136">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="55ab7-137"><xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> `true` Bir karakter büyük harfli ise, yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="55ab7-137">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="55ab7-138">Dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="55ab7-138">Save the file.</span></span>

1. <span data-ttu-id="55ab7-139">Çözümü derlemek ve projenin hatasız derlendiğinden emin olmak için aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="55ab7-139">Run the following command to build the solution and verify that the project compiles without error.</span></span>

   ```dotnetcli
   dotnet build
   ```

   <span data-ttu-id="55ab7-140">Terminal çıktısı aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="55ab7-140">The terminal output looks like the following example:</span></span>

   ```
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

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="55ab7-141">Çözüme bir konsol uygulaması ekleme</span><span class="sxs-lookup"><span data-stu-id="55ab7-141">Add a console app to the solution</span></span>

<span data-ttu-id="55ab7-142">Sınıf kitaplığını kullanan bir konsol uygulaması ekleyin.</span><span class="sxs-lookup"><span data-stu-id="55ab7-142">Add a console application that uses the class library.</span></span> <span data-ttu-id="55ab7-143">Uygulama kullanıcıdan bir dize girmesini ister ve dizenin büyük harfli bir karakterle başlayıp başlamamadığını rapor eder.</span><span class="sxs-lookup"><span data-stu-id="55ab7-143">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="55ab7-144">Terminalde, kitaplık projesini oluşturmak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="55ab7-144">In the terminal, run the following command to create the library project:</span></span>

   ```dotnetcli
   dotnet new console -o ShowCase
   ```

   <span data-ttu-id="55ab7-145">Terminal çıktısı aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="55ab7-145">The terminal output looks like the following example:</span></span>

   ```
   The template "Console Application" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on ShowCase\ShowCase.csproj...  
     Determining projects to restore...
     Restore completed in 210.78 ms for C:\Projects\ClassLibraryProjects\ShowCase\ShowCase.csproj.
   Restore succeeded.
   ```

1. <span data-ttu-id="55ab7-146">Konsol uygulaması projesini çözüme eklemek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="55ab7-146">Run the following command to add the console app project to the solution:</span></span>

   ```dotnetcli
   dotnet sln add ShowCase/ShowCase.csproj
   ```

   <span data-ttu-id="55ab7-147">Terminal çıktısı aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="55ab7-147">The terminal output looks like the following example:</span></span>

   ```
   Project `ShowCase\ShowCase.csproj` added to the solution.
   ```

1. <span data-ttu-id="55ab7-148">Başlangıçta, yeni konsol uygulaması projesi sınıf kitaplığına erişemez.</span><span class="sxs-lookup"><span data-stu-id="55ab7-148">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="55ab7-149">Sınıf kitaplığındaki yöntemleri çağırmasına izin vermek için aşağıdaki komutu çalıştırarak sınıf kitaplığı projesine bir proje başvurusu oluşturun:</span><span class="sxs-lookup"><span data-stu-id="55ab7-149">To allow it to call methods in the class library, create a project reference to the class library project by running the following command:</span></span>

   ```dotnetcli
   dotnet add ShowCase/Showcase.csproj reference StringLibrary/StringLibrary.csproj
   ```

   <span data-ttu-id="55ab7-150">Terminal çıktısı aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="55ab7-150">The terminal output looks like the following example:</span></span>

   ```
   Reference `..\StringLibrary\StringLibrary.csproj` added to the project.
   ```

1. <span data-ttu-id="55ab7-151">*Gösterimi/program. cs* ' i açın ve kodun tümünü aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="55ab7-151">Open *ShowCase/Program.cs* and replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   <span data-ttu-id="55ab7-152">Kod, `row` konsol penceresine yazılan veri satırlarının sayısını korumak için değişkenini kullanır.</span><span class="sxs-lookup"><span data-stu-id="55ab7-152">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="55ab7-153">25 ' e eşit veya daha büyük olduğunda, kod konsol penceresini temizler ve kullanıcıya bir ileti görüntüler.</span><span class="sxs-lookup"><span data-stu-id="55ab7-153">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="55ab7-154">Program kullanıcıdan bir dize girmesini ister.</span><span class="sxs-lookup"><span data-stu-id="55ab7-154">The program prompts the user to enter a string.</span></span> <span data-ttu-id="55ab7-155">Dizenin büyük harfle başlatılıp başlatılmayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="55ab7-155">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="55ab7-156">Kullanıcı bir dize girmeden ENTER tuşuna basarsa, uygulama sonlanır ve konsol penceresi kapanır.</span><span class="sxs-lookup"><span data-stu-id="55ab7-156">If the user presses the Enter key without entering a string, the application ends, and the console window closes.</span></span>

1. <span data-ttu-id="55ab7-157">Yaptığınız değişiklikleri kaydedin.</span><span class="sxs-lookup"><span data-stu-id="55ab7-157">Save your changes.</span></span>

1. <span data-ttu-id="55ab7-158">Programı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="55ab7-158">Run the program.</span></span>

   ```dotnetcli
   dotnet run --project ShowCase/ShowCase.csproj
   ```

1. <span data-ttu-id="55ab7-159">Dizeleri girerek ve <kbd>ENTER</kbd>'a basarak programı deneyin ve çıkmak için <kbd>ENTER</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="55ab7-159">Try out the program by entering strings and pressing <kbd>Enter</kbd>, then press <kbd>Enter</kbd> to exit.</span></span>

   <span data-ttu-id="55ab7-160">Terminal çıktısı aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="55ab7-160">The terminal output looks like the following example:</span></span>

   ```
   Press <Enter> only to exit; otherwise, enter a string and press <Enter>:

   A string that starts with an uppercase letter
   Input: A string that starts with an uppercase letter
   Begins with uppercase? : Yes

   A string that starts with a lowercase letter
   Input: A string that starts with a lowercase letter
   Begins with uppercase? : Yes
   ```

## <a name="additional-resources"></a><span data-ttu-id="55ab7-161">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="55ab7-161">Additional resources</span></span>

* [<span data-ttu-id="55ab7-162">.NET Core CLI ile Kitaplıklar geliştirin</span><span class="sxs-lookup"><span data-stu-id="55ab7-162">Develop libraries with the .NET Core CLI</span></span>](libraries.md)

## <a name="next-steps"></a><span data-ttu-id="55ab7-163">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="55ab7-163">Next steps</span></span>

<span data-ttu-id="55ab7-164">Bu öğreticide, bir çözüm oluşturdunuz, bir kitaplık projesi eklediniz ve kitaplığı kullanan bir konsol uygulaması projesi ekledik.</span><span class="sxs-lookup"><span data-stu-id="55ab7-164">In this tutorial, you created a solution, added a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="55ab7-165">Sonraki öğreticide, çözüme bir birim testi projesi eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="55ab7-165">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="55ab7-166">.NET Standard kitaplığı Visual Studio Code .NET Core ile test etme</span><span class="sxs-lookup"><span data-stu-id="55ab7-166">Test a .NET Standard library with .NET Core in Visual Studio Code</span></span>](testing-library-with-visual-studio-code.md)
