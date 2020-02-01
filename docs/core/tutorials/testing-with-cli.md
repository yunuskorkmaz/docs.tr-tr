---
title: .NET Core CLI projeleri düzenleme ve test etme
description: Bu öğreticide, .NET Core projelerini komut satırından düzenleme ve test etme işlemleri açıklanmaktadır.
author: cartermp
ms.date: 09/10/2018
ms.openlocfilehash: 11d13ad1d74c69cdfe0626bda8823dd0609da85f
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920416"
---
# <a name="organizing-and-testing-projects-with-the-net-core-cli"></a><span data-ttu-id="a3514-103">.NET Core CLI projeleri düzenleme ve test etme</span><span class="sxs-lookup"><span data-stu-id="a3514-103">Organizing and testing projects with the .NET Core CLI</span></span>

<span data-ttu-id="a3514-104">Bu öğretici, [komut satırını kullanarak Windows/Linux/macOS 'ta .NET Core ile çalışmaya başlama](cli-create-console-app.md), gelişmiş ve iyi düzenlenmiş uygulamalar geliştirmeye yönelik basit bir konsol uygulaması oluşturma aşamasından daha fazla yararlanılarak.</span><span class="sxs-lookup"><span data-stu-id="a3514-104">This tutorial follows [Get started with .NET Core on Windows/Linux/macOS using the command line](cli-create-console-app.md), taking you beyond the creation of a simple console app to develop advanced and well-organized applications.</span></span> <span data-ttu-id="a3514-105">Kodunuzu düzenlemek için klasörleri nasıl kullanacağınızı gösterdikten sonra, bu öğreticide [xUnit](https://xunit.github.io/) test çerçevesiyle bir konsol uygulamasını nasıl genişletebileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="a3514-105">After showing you how to use folders to organize your code, this tutorial shows you how to extend a console application with the [xUnit](https://xunit.github.io/) testing framework.</span></span>

## <a name="using-folders-to-organize-code"></a><span data-ttu-id="a3514-106">Kodu düzenlemek için klasörleri kullanma</span><span class="sxs-lookup"><span data-stu-id="a3514-106">Using folders to organize code</span></span>

<span data-ttu-id="a3514-107">Konsol uygulamasına yeni türler eklemek istiyorsanız, türleri uygulamaya içeren dosyaları ekleyerek bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a3514-107">If you want to introduce new types into a console app, you can do so by adding files containing the types to the app.</span></span> <span data-ttu-id="a3514-108">Örneğin, projenize `AccountInformation` ve `MonthlyReportRecords` türlerini içeren dosyalar eklerseniz, proje dosya yapısı düz ve gezinmek kolaydır:</span><span class="sxs-lookup"><span data-stu-id="a3514-108">For example if you add files containing `AccountInformation` and `MonthlyReportRecords` types to your project, the project file structure is flat and easy to navigate:</span></span>

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="a3514-109">Ancak, bu yalnızca projenizin boyutu nispeten küçük olduğunda iyi bir şekilde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a3514-109">However, this only works well when the size of your project is relatively small.</span></span> <span data-ttu-id="a3514-110">Projeye 20 tür eklerseniz ne olacağını anlaz edebilir misiniz?</span><span class="sxs-lookup"><span data-stu-id="a3514-110">Can you imagine what will happen if you add 20 types to the project?</span></span> <span data-ttu-id="a3514-111">Projenin, bu birçok dosya üzerinde gezinilmesi ve projenin kök dizinini oluşturma konusunda kesinlikle kolay olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a3514-111">The project definitely wouldn't be easy to navigate and maintain with that many files littering the project's root directory.</span></span>

<span data-ttu-id="a3514-112">Projeyi düzenlemek için yeni bir klasör oluşturun ve bunu tür dosyalarını tutacak şekilde *modelleyen* şekilde adlandırın.</span><span class="sxs-lookup"><span data-stu-id="a3514-112">To organize the project, create a new folder and name it *Models* to hold the type files.</span></span> <span data-ttu-id="a3514-113">Tür dosyalarını *modeller* klasörüne yerleştirin:</span><span class="sxs-lookup"><span data-stu-id="a3514-113">Place the type files into the *Models* folder:</span></span>

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="a3514-114">Dosyaları klasörlere mantıksal olarak gruplandıran projeler arasında gezinmek ve bakım yapmak kolaydır.</span><span class="sxs-lookup"><span data-stu-id="a3514-114">Projects that logically group files into folders are easy to navigate and maintain.</span></span> <span data-ttu-id="a3514-115">Sonraki bölümde, klasörler ve birim testi ile daha karmaşık bir örnek oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="a3514-115">In the next section, you create a more complex sample with folders and unit testing.</span></span>

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a><span data-ttu-id="a3514-116">NewTypes pets örneğini kullanarak düzenleme ve test etme</span><span class="sxs-lookup"><span data-stu-id="a3514-116">Organizing and testing using the NewTypes Pets Sample</span></span>

### <a name="building-the-sample"></a><span data-ttu-id="a3514-117">Örnek oluşturma</span><span class="sxs-lookup"><span data-stu-id="a3514-117">Building the sample</span></span>

<span data-ttu-id="a3514-118">Aşağıdaki adımlar için, [Newtypes pets örneğini](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) kullanarak takip edebilir veya kendi dosya ve klasörlerinizi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a3514-118">For the following steps, you can either follow along using the [NewTypes Pets Sample](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) or create your own files and folders.</span></span> <span data-ttu-id="a3514-119">Türler, daha sonra daha fazla türden eklenmesine izin veren bir klasör yapısına mantıksal olarak düzenlenir ve testler daha sonra daha fazla test eklenmesine izin veren klasörlere de mantıksal olarak yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a3514-119">The types are logically organized into a folder structure that permits the addition of more types later, and tests are also logically placed in folders permitting the addition of more tests later.</span></span>

<span data-ttu-id="a3514-120">Örnek, `Dog` ve `Cat`iki tür içerir ve bunlar `IPet`ortak bir arabirim uygular.</span><span class="sxs-lookup"><span data-stu-id="a3514-120">The sample contains two types, `Dog` and `Cat`, and has them implement a common interface, `IPet`.</span></span> <span data-ttu-id="a3514-121">`NewTypes` projesi için amacınız, Evcil hayvan ile ilgili türleri bir *pets* klasörü olarak düzenmaktır.</span><span class="sxs-lookup"><span data-stu-id="a3514-121">For the `NewTypes` project, your goal is to organize the pet-related types into a *Pets* folder.</span></span> <span data-ttu-id="a3514-122">Daha sonra başka bir tür kümesi eklenirse, *WildAnimals* Örneğin, *pets* klasörüyle birlikte *newtypes* klasörüne yerleştirilirler.</span><span class="sxs-lookup"><span data-stu-id="a3514-122">If another set of types is added later, *WildAnimals* for example, they're placed in the *NewTypes* folder alongside the *Pets* folder.</span></span> <span data-ttu-id="a3514-123">*WildAnimals* klasörü, `Squirrel` ve `Rabbit` türleri gibi pets olmayan hayvanlar türleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a3514-123">The *WildAnimals* folder may contain types for animals that aren't pets, such as `Squirrel` and `Rabbit` types.</span></span> <span data-ttu-id="a3514-124">Bu şekilde, türler eklendikçe, proje iyi organize edilmiş kalır.</span><span class="sxs-lookup"><span data-stu-id="a3514-124">In this way as types are added, the project remains well organized.</span></span>

<span data-ttu-id="a3514-125">Belirtilen dosya içeriğiyle aşağıdaki klasör yapısını oluşturun:</span><span class="sxs-lookup"><span data-stu-id="a3514-125">Create the following folder structure with file content indicated:</span></span>

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__NewTypes.csproj
```

<span data-ttu-id="a3514-126">*IPet.cs*:</span><span class="sxs-lookup"><span data-stu-id="a3514-126">*IPet.cs*:</span></span>

[!code-csharp[IPet interface](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/IPet.cs)]

<span data-ttu-id="a3514-127">*Dog.cs*:</span><span class="sxs-lookup"><span data-stu-id="a3514-127">*Dog.cs*:</span></span>

[!code-csharp[Dog class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Dog.cs)]

<span data-ttu-id="a3514-128">*Cat.cs*:</span><span class="sxs-lookup"><span data-stu-id="a3514-128">*Cat.cs*:</span></span>

[!code-csharp[Cat class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Cat.cs)]

<span data-ttu-id="a3514-129">*Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="a3514-129">*Program.cs*:</span></span>

[!code-csharp[Main](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Program.cs)]

<span data-ttu-id="a3514-130">*NewTypes.csproj*:</span><span class="sxs-lookup"><span data-stu-id="a3514-130">*NewTypes.csproj*:</span></span>

[!code-xml[NewTypes csproj](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/NewTypes.csproj)]

<span data-ttu-id="a3514-131">Aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="a3514-131">Execute the following command:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="a3514-132">Aşağıdaki çıktıyı alın:</span><span class="sxs-lookup"><span data-stu-id="a3514-132">Obtain the following output:</span></span>

```console
Woof!
Meow!
```

<span data-ttu-id="a3514-133">İsteğe bağlı alıştırma: Bu projeyi genişleterek `Bird`gibi yeni bir evcil hayvan türü ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a3514-133">Optional exercise: You can add a new pet type, such as a `Bird`, by extending this project.</span></span> <span data-ttu-id="a3514-134">Kuş`TalkToOwner` yönteminin Sahibe bir `Tweet!` vermesini sağlayın.</span><span class="sxs-lookup"><span data-stu-id="a3514-134">Make the bird's `TalkToOwner` method give a `Tweet!` to the owner.</span></span> <span data-ttu-id="a3514-135">Uygulamayı yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a3514-135">Run the app again.</span></span> <span data-ttu-id="a3514-136">Çıktı `Tweet!` içerecektir</span><span class="sxs-lookup"><span data-stu-id="a3514-136">The output will include `Tweet!`</span></span>

### <a name="testing-the-sample"></a><span data-ttu-id="a3514-137">Örneği test etme</span><span class="sxs-lookup"><span data-stu-id="a3514-137">Testing the sample</span></span>

<span data-ttu-id="a3514-138">`NewTypes` projesi yerinde olduğundan, pets ile ilgili türleri bir klasörde tutarak düzenlemiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="a3514-138">The `NewTypes` project is in place, and you've organized it by keeping the pets-related types in a folder.</span></span> <span data-ttu-id="a3514-139">Ardından, test projenizi oluşturun ve [xUnit](https://xunit.github.io/) test çerçevesi ile testleri yazmaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="a3514-139">Next, create your test project and start writing tests with the [xUnit](https://xunit.github.io/) test framework.</span></span> <span data-ttu-id="a3514-140">Birim testi, sorunsuz şekilde çalıştığının nasıl yapılacağını onaylamak için evcil hayvan türlerinizi davranışını otomatik olarak denetlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a3514-140">Unit testing allows you to automatically check the behavior of your pet types to confirm that they're operating properly.</span></span>

<span data-ttu-id="a3514-141">*Src* klasörüne geri gidin ve Içinde *newtypestests* klasörünü içeren bir *Test* klasörü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a3514-141">Navigate back to the *src* folder and create a *test* folder with a *NewTypesTests* folder within it.</span></span> <span data-ttu-id="a3514-142">*Newtypestests* klasöründen bir komut isteminde `dotnet new xunit`yürütün.</span><span class="sxs-lookup"><span data-stu-id="a3514-142">At a command prompt from the *NewTypesTests* folder, execute `dotnet new xunit`.</span></span> <span data-ttu-id="a3514-143">Bu iki dosya üretir: *Newtypestests. csproj* ve *UnitTest1.cs*.</span><span class="sxs-lookup"><span data-stu-id="a3514-143">This produces two files: *NewTypesTests.csproj* and *UnitTest1.cs*.</span></span>

<span data-ttu-id="a3514-144">Test projesi şu anda `NewTypes` türlerini test edemez ve `NewTypes` projesine bir proje başvurusu gerektiriyor.</span><span class="sxs-lookup"><span data-stu-id="a3514-144">The test project cannot currently test the types in `NewTypes` and requires a project reference to the `NewTypes` project.</span></span> <span data-ttu-id="a3514-145">Bir proje başvurusu eklemek için [`dotnet add reference`](../tools/dotnet-add-reference.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="a3514-145">To add a project reference, use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

<span data-ttu-id="a3514-146">Ayrıca, *Newtypestests. csproj* dosyasına bir `<ItemGroup>` düğümü ekleyerek proje başvurusunu el ile ekleme seçeneğiniz de vardır:</span><span class="sxs-lookup"><span data-stu-id="a3514-146">Or, you also have the option of manually adding the project reference by adding an `<ItemGroup>` node to the *NewTypesTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

<span data-ttu-id="a3514-147">*NewTypesTests.csproj*:</span><span class="sxs-lookup"><span data-stu-id="a3514-147">*NewTypesTests.csproj*:</span></span>

[!code-xml[NewTypesTests csproj](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/NewTypesTests.csproj)]

<span data-ttu-id="a3514-148">*Newtypestests. csproj* dosyası şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="a3514-148">The *NewTypesTests.csproj* file contains the following:</span></span>

* <span data-ttu-id="a3514-149">.NET test altyapısı `Microsoft.NET.Test.Sdk`için paket başvurusu</span><span class="sxs-lookup"><span data-stu-id="a3514-149">Package reference to `Microsoft.NET.Test.Sdk`, the .NET testing infrastructure</span></span>
* <span data-ttu-id="a3514-150">`xunit`, xUnit test çerçevesini paket başvurusu</span><span class="sxs-lookup"><span data-stu-id="a3514-150">Package reference to `xunit`, the xUnit testing framework</span></span>
* <span data-ttu-id="a3514-151">Test Çalıştırıcısı `xunit.runner.visualstudio`paket başvurusu</span><span class="sxs-lookup"><span data-stu-id="a3514-151">Package reference to `xunit.runner.visualstudio`, the test runner</span></span>
* <span data-ttu-id="a3514-152">`NewTypes`proje başvurusu, sınanacak kod</span><span class="sxs-lookup"><span data-stu-id="a3514-152">Project reference to `NewTypes`, the code to test</span></span>

<span data-ttu-id="a3514-153">*UnitTest1.cs* adını *PetTests.cs* olarak değiştirin ve dosyadaki kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="a3514-153">Change the name of *UnitTest1.cs* to *PetTests.cs* and replace the code in the file with the following:</span></span>

```csharp
using System;
using Xunit;
using Pets;

public class PetTests
{
    [Fact]
    public void DogTalkToOwnerReturnsWoof()
    {
        string expected = "Woof!";
        string actual = new Dog().TalkToOwner();

        Assert.NotEqual(expected, actual);
    }

    [Fact]
    public void CatTalkToOwnerReturnsMeow()
    {
        string expected = "Meow!";
        string actual = new Cat().TalkToOwner();

        Assert.NotEqual(expected, actual);
    }
}
```

<span data-ttu-id="a3514-154">İsteğe bağlı alıştırma: daha önce sahibine bir `Tweet!` veren bir `Bird` türü eklediyseniz, `TalkToOwner` yönteminin `Bird` türü için doğru şekilde çalışıp çalışmadığını denetlemek için, `BirdTalkToOwnerReturnsTweet`, *PetTests.cs* dosyasına bir test yöntemi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a3514-154">Optional exercise: If you added a `Bird` type earlier that yields a `Tweet!` to the owner, add a test method to the *PetTests.cs* file, `BirdTalkToOwnerReturnsTweet`, to check that the `TalkToOwner` method works correctly for the `Bird` type.</span></span>

> [!NOTE]
> <span data-ttu-id="a3514-155">`expected` ve `actual` değerlerinin eşit olmasını bekleseniz de, `Assert.NotEqual` denetimine sahip bir ilk onaylama, bu değerlerin *eşit*olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a3514-155">Although you expect that the `expected` and `actual` values are equal, an initial assertion with the `Assert.NotEqual` check specifies that these values are *not equal*.</span></span> <span data-ttu-id="a3514-156">Testin mantığını denetlemek için her zaman ilk olarak bir test oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a3514-156">Always initially create a test to fail in order to check the logic of the test.</span></span> <span data-ttu-id="a3514-157">Testin başarısız olduğunu doğruladıktan sonra, testi geçirmeye izin verecek şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a3514-157">After you confirm that the test fails, adjust the assertion to allow the test to pass.</span></span>

<span data-ttu-id="a3514-158">Aşağıda, tüm proje yapısı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="a3514-158">The following shows the complete project structure:</span></span>

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__NewTypes.csproj
|__/test
   |__NewTypesTests
      |__PetTests.cs
      |__NewTypesTests.csproj
```

<span data-ttu-id="a3514-159">*Test/NewTypesTests* dizininde başlatın.</span><span class="sxs-lookup"><span data-stu-id="a3514-159">Start in the *test/NewTypesTests* directory.</span></span> <span data-ttu-id="a3514-160">[`dotnet restore`](../tools/dotnet-restore.md) komutuyla test projesini geri yükleyin.</span><span class="sxs-lookup"><span data-stu-id="a3514-160">Restore the test project with the [`dotnet restore`](../tools/dotnet-restore.md) command.</span></span> <span data-ttu-id="a3514-161">Testleri [`dotnet test`](../tools/dotnet-test.md) komutuyla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a3514-161">Run the tests with the [`dotnet test`](../tools/dotnet-test.md) command.</span></span> <span data-ttu-id="a3514-162">Bu komut, proje dosyasında belirtilen Test Çalıştırıcısı 'nı başlatır.</span><span class="sxs-lookup"><span data-stu-id="a3514-162">This command starts the test runner specified in the project file.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="a3514-163">Beklenen şekilde test başarısız olur ve konsolu aşağıdaki çıktıyı görüntüler:</span><span class="sxs-lookup"><span data-stu-id="a3514-163">As expected, testing fails, and the console displays the following output:</span></span>

```output
Test run for c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\bin\Debug\netcoreapp2.1\NewTypesTests.dll(.NETCoreApp,Version=v2.1)
Microsoft (R) Test Execution Command Line Tool Version 15.8.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
[xUnit.net 00:00:00.77]     PetTests.DogTalkToOwnerReturnsWoof [FAIL]
[xUnit.net 00:00:00.78]     PetTests.CatTalkToOwnerReturnsMeow [FAIL]
Failed   PetTests.DogTalkToOwnerReturnsWoof
Error Message:
 Assert.NotEqual() Failure
Expected: Not "Woof!"
Actual:   "Woof!"
Stack Trace:
   at PetTests.DogTalkToOwnerReturnsWoof() in c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\PetTests.cs:line 13
Failed   PetTests.CatTalkToOwnerReturnsMeow
Error Message:
 Assert.NotEqual() Failure
Expected: Not "Meow!"
Actual:   "Meow!"
Stack Trace:
   at PetTests.CatTalkToOwnerReturnsMeow() in c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\PetTests.cs:line 22

Total tests: 2. Passed: 0. Failed: 2. Skipped: 0.
Test Run Failed.
Test execution time: 1.7000 Seconds
```

<span data-ttu-id="a3514-164">Testlerinizin `Assert.NotEqual` `Assert.Equal`' e kadar olan onayları değiştirin:</span><span class="sxs-lookup"><span data-stu-id="a3514-164">Change the assertions of your tests from `Assert.NotEqual` to `Assert.Equal`:</span></span>

[!code-csharp[PetTests class](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/PetTests.cs)]

<span data-ttu-id="a3514-165">`dotnet test` komutuyla testleri yeniden çalıştırın ve aşağıdaki çıktıyı alın:</span><span class="sxs-lookup"><span data-stu-id="a3514-165">Re-run the tests with the `dotnet test` command and obtain the following output:</span></span>

```output
Test run for c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\bin\Debug\netcoreapp2.1\NewTypesTests.dll(.NETCoreApp,Version=v2.1)
Microsoft (R) Test Execution Command Line Tool Version 15.8.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...

Total tests: 2. Passed: 2. Failed: 0. Skipped: 0.
Test Run Successful.
Test execution time: 1.6029 Seconds
```

<span data-ttu-id="a3514-166">Test geçişleri.</span><span class="sxs-lookup"><span data-stu-id="a3514-166">Testing passes.</span></span> <span data-ttu-id="a3514-167">Evcil hayvan türleri ' yöntemleri, sahibiyle konuşurken doğru değerleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="a3514-167">The pet types' methods return the correct values when talking to the owner.</span></span>

<span data-ttu-id="a3514-168">XUnit kullanarak projeleri düzenleme ve test etme tekniklerini öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="a3514-168">You've learned techniques for organizing and testing projects using xUnit.</span></span> <span data-ttu-id="a3514-169">Bunları kendi projelerinize uygulayarak bu tekniklerle ileri gidin.</span><span class="sxs-lookup"><span data-stu-id="a3514-169">Go forward with these techniques applying them in your own projects.</span></span> <span data-ttu-id="a3514-170">*Kodlarım kutlu olsun!*</span><span class="sxs-lookup"><span data-stu-id="a3514-170">*Happy coding!*</span></span>
