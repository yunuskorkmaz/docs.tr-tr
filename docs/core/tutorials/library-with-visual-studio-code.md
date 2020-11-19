---
title: Visual Studio Code kullanarak bir .NET sınıf kitaplığı oluşturma
description: Visual Studio Code kullanarak .NET sınıf kitaplığı oluşturmayı öğrenin.
ms.date: 11/18/2020
ms.openlocfilehash: 4daa077fc54da3de2f808d831e06ee5f9bb3bde7
ms.sourcegitcommit: 5114e7847e0ff8ddb8c266802d47af78567949cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94916097"
---
# <a name="tutorial-create-a-net-class-library-using-visual-studio-code"></a><span data-ttu-id="3304a-103">Öğretici: Visual Studio Code kullanarak .NET sınıf kitaplığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="3304a-103">Tutorial: Create a .NET class library using Visual Studio Code</span></span>

<span data-ttu-id="3304a-104">Bu öğreticide, tek bir dize işleme yöntemi içeren basit bir yardımcı program kitaplığı oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="3304a-104">In this tutorial, you create a simple utility library that contains a single string-handling method.</span></span>

<span data-ttu-id="3304a-105">Bir *sınıf kitaplığı* , bir uygulama tarafından çağrılan türleri ve yöntemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3304a-105">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="3304a-106">Kitaplık .NET Standard 2,0 hedefliyorsa, .NET Standard 2,0 ' yi destekleyen herhangi bir .NET uygulamasıyla (.NET Framework dahil) çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="3304a-106">If the library targets .NET Standard 2.0, it can be called by any .NET implementation (including .NET Framework) that supports .NET Standard 2.0.</span></span> <span data-ttu-id="3304a-107">Kitaplık .NET 5 ' i hedefliyorsa, .NET 5 ' i hedefleyen herhangi bir uygulama tarafından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="3304a-107">If the library targets .NET 5, it can be called by any application that targets .NET 5.</span></span> <span data-ttu-id="3304a-108">Bu öğreticide, .NET 5 ' in nasıl hedeflenecek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3304a-108">This tutorial shows how to target .NET 5.</span></span>

<span data-ttu-id="3304a-109">Bir sınıf kitaplığı oluşturduğunuzda, bir üçüncü taraf bileşen olarak veya bir veya daha fazla uygulamayla paketlenmiş bileşen olarak dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3304a-109">When you create a class library, you can distribute it as a third-party component or as a bundled component with one or more applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3304a-110">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="3304a-110">Prerequisites</span></span>

1. <span data-ttu-id="3304a-111">[C# uzantısı](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) yüklü [Visual Studio Code](https://code.visualstudio.com/) .</span><span class="sxs-lookup"><span data-stu-id="3304a-111">[Visual Studio Code](https://code.visualstudio.com/) with the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) installed.</span></span> <span data-ttu-id="3304a-112">Visual Studio Code uzantıları nasıl yükleyeceğiniz hakkında daha fazla bilgi için bkz. [vs Code uzantısı marketi](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="3304a-112">For information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>
2. <span data-ttu-id="3304a-113">[.Net 5,0 SDK veya üzeri](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="3304a-113">The [.NET 5.0 SDK or later](https://dotnet.microsoft.com/download)</span></span>

## <a name="create-a-solution"></a><span data-ttu-id="3304a-114">Çözüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="3304a-114">Create a solution</span></span>

<span data-ttu-id="3304a-115">' De Sınıf Kitaplığı projesini yerleştirmek için boş bir çözüm oluşturarak başlayın.</span><span class="sxs-lookup"><span data-stu-id="3304a-115">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="3304a-116">Bir çözüm, bir veya daha fazla proje için kapsayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="3304a-116">A solution serves as a container for one or more projects.</span></span> <span data-ttu-id="3304a-117">Aynı çözüme ek ve ilgili projeler ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="3304a-117">You'll add additional, related projects to the same solution.</span></span>

1. <span data-ttu-id="3304a-118">Visual Studio Code’u başlatın.</span><span class="sxs-lookup"><span data-stu-id="3304a-118">Start Visual Studio Code.</span></span>

1. <span data-ttu-id="3304a-119">Ana menüden **Dosya**  >  **açma klasörünü** (MacOS üzerinde **Open...** ) seçin</span><span class="sxs-lookup"><span data-stu-id="3304a-119">Select **File** > **Open Folder** (**Open...** on macOS) from the main menu</span></span>

1. <span data-ttu-id="3304a-120">**Klasörü aç** iletişim kutusunda bir *classlibraryprojects* klasörü oluşturun ve **Klasör Seç** ' e tıklayın (MacOS üzerinde **açın** ).</span><span class="sxs-lookup"><span data-stu-id="3304a-120">In the **Open Folder** dialog, create a *ClassLibraryProjects* folder and click **Select Folder** (**Open** on macOS).</span></span>

1. <span data-ttu-id="3304a-121">Ana menüden **Terminal görünümü ' nu** seçerek **View** Visual Studio Code açın  >  **Terminal** .</span><span class="sxs-lookup"><span data-stu-id="3304a-121">Open the **Terminal** in Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>

   <span data-ttu-id="3304a-122">**Terminal** , *classlibraryprojects* klasöründe komut istemiyle açılır.</span><span class="sxs-lookup"><span data-stu-id="3304a-122">The **Terminal** opens with the command prompt in the *ClassLibraryProjects* folder.</span></span>

1. <span data-ttu-id="3304a-123">**Terminalde** aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="3304a-123">In the **Terminal**, enter the following command:</span></span>

   ```dotnetcli
   dotnet new sln
   ```

   <span data-ttu-id="3304a-124">Terminal çıktısı aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="3304a-124">The terminal output looks like the following example:</span></span>

   ```output
   The template "Solution File" was created successfully.
   ```

## <a name="create-a-class-library-project"></a><span data-ttu-id="3304a-125">Sınıf kitaplığı projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="3304a-125">Create a class library project</span></span>

<span data-ttu-id="3304a-126">Çözüme "StringLibrary" adlı yeni bir .NET sınıf kitaplığı projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3304a-126">Add a new .NET class library project named "StringLibrary" to the solution.</span></span>

1. <span data-ttu-id="3304a-127">Terminalde, kitaplık projesini oluşturmak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="3304a-127">In the terminal, run the following command to create the library project:</span></span>

   ```dotnetcli
   dotnet new classlib -o StringLibrary
   ```

   <span data-ttu-id="3304a-128">`-o`Or `--output` komutu oluşturulan çıkışın yerleştirileceği konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="3304a-128">The `-o` or `--output` command specifies the location to place the generated output.</span></span>

   <span data-ttu-id="3304a-129">Terminal çıktısı aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="3304a-129">The terminal output looks like the following example:</span></span>

   ```output
   The template "Class library" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on StringLibrary\StringLibrary.csproj...
     Determining projects to restore...
     Restored C:\Projects\ClassLibraryProjects\StringLibrary\StringLibrary.csproj (in 328 ms).
   Restore succeeded.
   ```

1. <span data-ttu-id="3304a-130">Kitaplık projesini çözüme eklemek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="3304a-130">Run the following command to add the library project to the solution:</span></span>

   ```dotnetcli
   dotnet sln add StringLibrary/StringLibrary.csproj
   ```

   <span data-ttu-id="3304a-131">Terminal çıktısı aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="3304a-131">The terminal output looks like the following example:</span></span>

   ```output
   Project `StringLibrary\StringLibrary.csproj` added to the solution.
   ```

1. <span data-ttu-id="3304a-132">Kitaplığın .NET 5 ' i hedeflediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="3304a-132">Check to make sure that the library targets .NET 5.</span></span> <span data-ttu-id="3304a-133">**Gezgin**'de *StringLibrary/StringLibrary. csproj* öğesini açın.</span><span class="sxs-lookup"><span data-stu-id="3304a-133">In **Explorer**, open *StringLibrary/StringLibrary.csproj*.</span></span>

   <span data-ttu-id="3304a-134">`TargetFramework`Öğesi, projenin .net 5,0 ' i hedeflediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3304a-134">The `TargetFramework` element shows that the project targets .NET 5.0.</span></span>

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">

     <PropertyGroup>
       <TargetFramework>net5.0</TargetFramework>
     </PropertyGroup>

   </Project>
   ```

1. <span data-ttu-id="3304a-135">*Class1.cs* ' i açın ve kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="3304a-135">Open *Class1.cs* and replace the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

   <span data-ttu-id="3304a-136">Sınıf kitaplığı, `UtilityLibraries.StringLibrary` adlı bir yöntemi içerir `StartsWithUpper` .</span><span class="sxs-lookup"><span data-stu-id="3304a-136">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="3304a-137">Bu yöntem <xref:System.Boolean> , geçerli dize örneğinin büyük harfli bir karakterle başlayıp başlamadığını belirten bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="3304a-137">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="3304a-138">Unicode standart, büyük harfli karakterleri küçük harfli karakterlerden ayırır.</span><span class="sxs-lookup"><span data-stu-id="3304a-138">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="3304a-139"><xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> `true` Bir karakter büyük harfli ise, yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="3304a-139">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="3304a-140">Dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="3304a-140">Save the file.</span></span>

1. <span data-ttu-id="3304a-141">Çözümü derlemek ve projenin hatasız derlendiğinden emin olmak için aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3304a-141">Run the following command to build the solution and verify that the project compiles without error.</span></span>

   ```dotnetcli
   dotnet build
   ```

   <span data-ttu-id="3304a-142">Terminal çıktısı aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="3304a-142">The terminal output looks like the following example:</span></span>

   ```output
   Microsoft (R) Build Engine version 16.7.0+b89cb5fde for .NET
   Copyright (C) Microsoft Corporation. All rights reserved.
     Determining projects to restore...
     All projects are up-to-date for restore.
     StringLibrary -> C:\Projects\ClassLibraryProjects\StringLibrary\bin\Debug\net5.0\StringLibrary.dll
   Build succeeded.
       0 Warning(s)
       0 Error(s)
   Time Elapsed 00:00:02.78
   ```

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="3304a-143">Çözüme bir konsol uygulaması ekleme</span><span class="sxs-lookup"><span data-stu-id="3304a-143">Add a console app to the solution</span></span>

<span data-ttu-id="3304a-144">Sınıf kitaplığını kullanan bir konsol uygulaması ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3304a-144">Add a console application that uses the class library.</span></span> <span data-ttu-id="3304a-145">Uygulama kullanıcıdan bir dize girmesini ister ve dizenin büyük harfli bir karakterle başlayıp başlamamadığını rapor eder.</span><span class="sxs-lookup"><span data-stu-id="3304a-145">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="3304a-146">Terminalde, konsol uygulama projesini oluşturmak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="3304a-146">In the terminal, run the following command to create the console app project:</span></span>

   ```dotnetcli
   dotnet new console -o ShowCase
   ```

   <span data-ttu-id="3304a-147">Terminal çıktısı aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="3304a-147">The terminal output looks like the following example:</span></span>

   ```output
   The template "Console Application" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on ShowCase\ShowCase.csproj...  
     Determining projects to restore...
     Restored C:\Projects\ClassLibraryProjects\ShowCase\ShowCase.csproj (in 210 ms).
   Restore succeeded.
   ```

1. <span data-ttu-id="3304a-148">Konsol uygulaması projesini çözüme eklemek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="3304a-148">Run the following command to add the console app project to the solution:</span></span>

   ```dotnetcli
   dotnet sln add ShowCase/ShowCase.csproj
   ```

   <span data-ttu-id="3304a-149">Terminal çıktısı aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="3304a-149">The terminal output looks like the following example:</span></span>

   ```output
   Project `ShowCase\ShowCase.csproj` added to the solution.
   ```

1. <span data-ttu-id="3304a-150">*Gösterimi/program. cs* ' i açın ve kodun tümünü aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="3304a-150">Open *ShowCase/Program.cs* and replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   <span data-ttu-id="3304a-151">Kod, `row` konsol penceresine yazılan veri satırlarının sayısını korumak için değişkenini kullanır.</span><span class="sxs-lookup"><span data-stu-id="3304a-151">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="3304a-152">25 ' e eşit veya daha büyük olduğunda, kod konsol penceresini temizler ve kullanıcıya bir ileti görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3304a-152">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="3304a-153">Program kullanıcıdan bir dize girmesini ister.</span><span class="sxs-lookup"><span data-stu-id="3304a-153">The program prompts the user to enter a string.</span></span> <span data-ttu-id="3304a-154">Dizenin büyük harfle başlatılıp başlatılmayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3304a-154">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="3304a-155">Kullanıcı bir dize girmeden <kbd>ENTER</kbd> tuşuna basarsa, uygulama sonlanır ve konsol penceresi kapanır.</span><span class="sxs-lookup"><span data-stu-id="3304a-155">If the user presses the <kbd>Enter</kbd> key without entering a string, the application ends, and the console window closes.</span></span>

1. <span data-ttu-id="3304a-156">Yaptığınız değişiklikleri kaydedin.</span><span class="sxs-lookup"><span data-stu-id="3304a-156">Save your changes.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="3304a-157">Proje başvurusu Ekle</span><span class="sxs-lookup"><span data-stu-id="3304a-157">Add a project reference</span></span>

<span data-ttu-id="3304a-158">Başlangıçta, yeni konsol uygulaması projesi sınıf kitaplığına erişemez.</span><span class="sxs-lookup"><span data-stu-id="3304a-158">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="3304a-159">Sınıf kitaplığındaki yöntemleri çağırmasına izin vermek için, sınıf kitaplığı projesine bir proje başvurusu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3304a-159">To allow it to call methods in the class library, create a project reference to the class library project.</span></span>

1. <span data-ttu-id="3304a-160">Şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="3304a-160">Run the following command:</span></span>

   ```dotnetcli
   dotnet add ShowCase/ShowCase.csproj reference StringLibrary/StringLibrary.csproj
   ```

   <span data-ttu-id="3304a-161">Terminal çıktısı aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="3304a-161">The terminal output looks like the following example:</span></span>

   ```output
   Reference `..\StringLibrary\StringLibrary.csproj` added to the project.
   ```

## <a name="run-the-app"></a><span data-ttu-id="3304a-162">Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="3304a-162">Run the app</span></span>

1. <span data-ttu-id="3304a-163">Terminalde aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="3304a-163">Run the following command in the terminal:</span></span>

   ```dotnetcli
   dotnet run --project ShowCase/ShowCase.csproj
   ```

1. <span data-ttu-id="3304a-164">Dizeleri girerek ve <kbd>ENTER</kbd>'a basarak programı deneyin ve çıkmak için <kbd>ENTER</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="3304a-164">Try out the program by entering strings and pressing <kbd>Enter</kbd>, then press <kbd>Enter</kbd> to exit.</span></span>

   <span data-ttu-id="3304a-165">Terminal çıktısı aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="3304a-165">The terminal output looks like the following example:</span></span>

   ```output
   Press <Enter> only to exit; otherwise, enter a string and press <Enter>:

   A string that starts with an uppercase letter
   Input: A string that starts with an uppercase letter
   Begins with uppercase? : Yes

   a string that starts with a lowercase letter
   Input: a string that starts with a lowercase letter
   Begins with uppercase? : No
   ```

## <a name="additional-resources"></a><span data-ttu-id="3304a-166">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="3304a-166">Additional resources</span></span>

* [<span data-ttu-id="3304a-167">.NET CLı ile Kitaplıklar geliştirme</span><span class="sxs-lookup"><span data-stu-id="3304a-167">Develop libraries with the .NET CLI</span></span>](libraries.md)

## <a name="next-steps"></a><span data-ttu-id="3304a-168">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="3304a-168">Next steps</span></span>

<span data-ttu-id="3304a-169">Bu öğreticide, bir çözüm oluşturdunuz, bir kitaplık projesi eklediniz ve kitaplığı kullanan bir konsol uygulaması projesi ekledik.</span><span class="sxs-lookup"><span data-stu-id="3304a-169">In this tutorial, you created a solution, added a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="3304a-170">Sonraki öğreticide, çözüme bir birim testi projesi eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="3304a-170">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3304a-171">.NET sınıf kitaplığı 'nı kullanarak .NET ile test Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="3304a-171">Test a .NET class library with .NET using Visual Studio Code</span></span>](testing-library-with-visual-studio-code.md)
