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
# <a name="tutorial-create-a-net-class-library-using-visual-studio-code"></a>Öğretici: Visual Studio Code kullanarak .NET sınıf kitaplığı oluşturma

Bu öğreticide, tek bir dize işleme yöntemi içeren basit bir yardımcı program kitaplığı oluşturacaksınız.

Bir *sınıf kitaplığı* , bir uygulama tarafından çağrılan türleri ve yöntemleri tanımlar. Kitaplık .NET Standard 2,0 hedefliyorsa, .NET Standard 2,0 ' yi destekleyen herhangi bir .NET uygulamasıyla (.NET Framework dahil) çağrılabilir. Kitaplık .NET 5 ' i hedefliyorsa, .NET 5 ' i hedefleyen herhangi bir uygulama tarafından çağrılabilir. Bu öğreticide, .NET 5 ' in nasıl hedeflenecek gösterilmektedir.

Bir sınıf kitaplığı oluşturduğunuzda, bir üçüncü taraf bileşen olarak veya bir veya daha fazla uygulamayla paketlenmiş bileşen olarak dağıtabilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

1. [C# uzantısı](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) yüklü [Visual Studio Code](https://code.visualstudio.com/) . Visual Studio Code uzantıları nasıl yükleyeceğiniz hakkında daha fazla bilgi için bkz. [vs Code uzantısı marketi](https://code.visualstudio.com/docs/editor/extension-gallery).
2. [.Net 5,0 SDK veya üzeri](https://dotnet.microsoft.com/download)

## <a name="create-a-solution"></a>Çözüm oluşturma

' De Sınıf Kitaplığı projesini yerleştirmek için boş bir çözüm oluşturarak başlayın. Bir çözüm, bir veya daha fazla proje için kapsayıcı görevi görür. Aynı çözüme ek ve ilgili projeler ekleyeceksiniz.

1. Visual Studio Code’u başlatın.

1. Ana menüden **Dosya**  >  **açma klasörünü** (MacOS üzerinde **Open...** ) seçin

1. **Klasörü aç** iletişim kutusunda bir *classlibraryprojects* klasörü oluşturun ve **Klasör Seç** ' e tıklayın (MacOS üzerinde **açın** ).

1. Ana menüden **Terminal görünümü ' nu** seçerek **View** Visual Studio Code açın  >  **Terminal** .

   **Terminal** , *classlibraryprojects* klasöründe komut istemiyle açılır.

1. **Terminalde** aşağıdaki komutu girin:

   ```dotnetcli
   dotnet new sln
   ```

   Terminal çıktısı aşağıdaki örneğe benzer şekilde görünür:

   ```output
   The template "Solution File" was created successfully.
   ```

## <a name="create-a-class-library-project"></a>Sınıf kitaplığı projesi oluşturma

Çözüme "StringLibrary" adlı yeni bir .NET sınıf kitaplığı projesi ekleyin.

1. Terminalde, kitaplık projesini oluşturmak için aşağıdaki komutu çalıştırın:

   ```dotnetcli
   dotnet new classlib -o StringLibrary
   ```

   `-o`Or `--output` komutu oluşturulan çıkışın yerleştirileceği konumu belirtir.

   Terminal çıktısı aşağıdaki örneğe benzer şekilde görünür:

   ```output
   The template "Class library" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on StringLibrary\StringLibrary.csproj...
     Determining projects to restore...
     Restored C:\Projects\ClassLibraryProjects\StringLibrary\StringLibrary.csproj (in 328 ms).
   Restore succeeded.
   ```

1. Kitaplık projesini çözüme eklemek için aşağıdaki komutu çalıştırın:

   ```dotnetcli
   dotnet sln add StringLibrary/StringLibrary.csproj
   ```

   Terminal çıktısı aşağıdaki örneğe benzer şekilde görünür:

   ```output
   Project `StringLibrary\StringLibrary.csproj` added to the solution.
   ```

1. Kitaplığın .NET 5 ' i hedeflediğinden emin olun. **Gezgin**'de *StringLibrary/StringLibrary. csproj* öğesini açın.

   `TargetFramework`Öğesi, projenin .net 5,0 ' i hedeflediğini gösterir.

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">

     <PropertyGroup>
       <TargetFramework>net5.0</TargetFramework>
     </PropertyGroup>

   </Project>
   ```

1. *Class1.cs* ' i açın ve kodu aşağıdaki kodla değiştirin.

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

   Sınıf kitaplığı, `UtilityLibraries.StringLibrary` adlı bir yöntemi içerir `StartsWithUpper` . Bu yöntem <xref:System.Boolean> , geçerli dize örneğinin büyük harfli bir karakterle başlayıp başlamadığını belirten bir değer döndürür. Unicode standart, büyük harfli karakterleri küçük harfli karakterlerden ayırır. <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> `true` Bir karakter büyük harfli ise, yöntemi döndürür.

1. Dosyayı kaydedin.

1. Çözümü derlemek ve projenin hatasız derlendiğinden emin olmak için aşağıdaki komutu çalıştırın.

   ```dotnetcli
   dotnet build
   ```

   Terminal çıktısı aşağıdaki örneğe benzer şekilde görünür:

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

## <a name="add-a-console-app-to-the-solution"></a>Çözüme bir konsol uygulaması ekleme

Sınıf kitaplığını kullanan bir konsol uygulaması ekleyin. Uygulama kullanıcıdan bir dize girmesini ister ve dizenin büyük harfli bir karakterle başlayıp başlamamadığını rapor eder.

1. Terminalde, konsol uygulama projesini oluşturmak için aşağıdaki komutu çalıştırın:

   ```dotnetcli
   dotnet new console -o ShowCase
   ```

   Terminal çıktısı aşağıdaki örneğe benzer şekilde görünür:

   ```output
   The template "Console Application" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on ShowCase\ShowCase.csproj...  
     Determining projects to restore...
     Restored C:\Projects\ClassLibraryProjects\ShowCase\ShowCase.csproj (in 210 ms).
   Restore succeeded.
   ```

1. Konsol uygulaması projesini çözüme eklemek için aşağıdaki komutu çalıştırın:

   ```dotnetcli
   dotnet sln add ShowCase/ShowCase.csproj
   ```

   Terminal çıktısı aşağıdaki örneğe benzer şekilde görünür:

   ```output
   Project `ShowCase\ShowCase.csproj` added to the solution.
   ```

1. *Gösterimi/program. cs* ' i açın ve kodun tümünü aşağıdaki kodla değiştirin.

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   Kod, `row` konsol penceresine yazılan veri satırlarının sayısını korumak için değişkenini kullanır. 25 ' e eşit veya daha büyük olduğunda, kod konsol penceresini temizler ve kullanıcıya bir ileti görüntüler.

   Program kullanıcıdan bir dize girmesini ister. Dizenin büyük harfle başlatılıp başlatılmayacağını gösterir. Kullanıcı bir dize girmeden <kbd>ENTER</kbd> tuşuna basarsa, uygulama sonlanır ve konsol penceresi kapanır.

1. Yaptığınız değişiklikleri kaydedin.

## <a name="add-a-project-reference"></a>Proje başvurusu Ekle

Başlangıçta, yeni konsol uygulaması projesi sınıf kitaplığına erişemez. Sınıf kitaplığındaki yöntemleri çağırmasına izin vermek için, sınıf kitaplığı projesine bir proje başvurusu oluşturun.

1. Şu komutu çalıştırın:

   ```dotnetcli
   dotnet add ShowCase/ShowCase.csproj reference StringLibrary/StringLibrary.csproj
   ```

   Terminal çıktısı aşağıdaki örneğe benzer şekilde görünür:

   ```output
   Reference `..\StringLibrary\StringLibrary.csproj` added to the project.
   ```

## <a name="run-the-app"></a>Uygulamayı çalıştırma

1. Terminalde aşağıdaki komutu çalıştırın:

   ```dotnetcli
   dotnet run --project ShowCase/ShowCase.csproj
   ```

1. Dizeleri girerek ve <kbd>ENTER</kbd>'a basarak programı deneyin ve çıkmak için <kbd>ENTER</kbd> tuşuna basın.

   Terminal çıktısı aşağıdaki örneğe benzer şekilde görünür:

   ```output
   Press <Enter> only to exit; otherwise, enter a string and press <Enter>:

   A string that starts with an uppercase letter
   Input: A string that starts with an uppercase letter
   Begins with uppercase? : Yes

   a string that starts with a lowercase letter
   Input: a string that starts with a lowercase letter
   Begins with uppercase? : No
   ```

## <a name="additional-resources"></a>Ek kaynaklar

* [.NET CLı ile Kitaplıklar geliştirme](libraries.md)

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, bir çözüm oluşturdunuz, bir kitaplık projesi eklediniz ve kitaplığı kullanan bir konsol uygulaması projesi ekledik. Sonraki öğreticide, çözüme bir birim testi projesi eklersiniz.

> [!div class="nextstepaction"]
> [.NET sınıf kitaplığı 'nı kullanarak .NET ile test Visual Studio Code](testing-library-with-visual-studio-code.md)
