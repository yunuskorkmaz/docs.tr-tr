---
title: Düzenleme ve .NET Core komut satırı ile projeleri test etme
description: Bu öğreticide, düzenlemek ve test komut satırından .NET Core projeleri açıklanmaktadır.
author: cartermp
ms.author: mairaw
ms.date: 05/16/2017
ms.openlocfilehash: 5fdbdc115ea5cd6da54f7c43bec2aa6f82e71310
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44185421"
---
# <a name="organizing-and-testing-projects-with-the-net-core-command-line"></a><span data-ttu-id="28315-103">Düzenleme ve .NET Core komut satırı ile projeleri test etme</span><span class="sxs-lookup"><span data-stu-id="28315-103">Organizing and testing projects with the .NET Core command line</span></span>

<span data-ttu-id="28315-104">Bu öğreticide aşağıdaki [Windows/Linus/macos'ta komut satırını kullanarak .NET Core ile çalışmaya başlama](using-with-xplat-cli.md), Gelişmiş ve iyi düzenlenmiş uygulamalar geliştirmek için basit bir konsol uygulaması oluşturmayı sürüyor.</span><span class="sxs-lookup"><span data-stu-id="28315-104">This tutorial follows [Getting started with .NET Core on Windows/Linux/macOS using the command line](using-with-xplat-cli.md), taking you beyond the creation of a simple console app to develop advanced and well-organized applications.</span></span> <span data-ttu-id="28315-105">Kodunuzu düzenlemek için klasörleri kullanmayı gösteren sonra Bu öğreticide, bir konsol uygulaması ile nasıl genişletileceğini gösterir [xUnit](https://xunit.github.io/) testi çerçevesi.</span><span class="sxs-lookup"><span data-stu-id="28315-105">After showing you how to use folders to organize your code, this tutorial shows you how to extend a console application with the [xUnit](https://xunit.github.io/) testing framework.</span></span>

## <a name="using-folders-to-organize-code"></a><span data-ttu-id="28315-106">Kod düzenlemek için klasörleri'ni kullanarak</span><span class="sxs-lookup"><span data-stu-id="28315-106">Using folders to organize code</span></span>

<span data-ttu-id="28315-107">Bir konsol uygulamasına yeni türlerini tanıtır istiyorsanız, bunu uygulama türlerini içeren dosyaları ekleyerek yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28315-107">If you want to introduce new types into a console app, you can do so by adding files containing the types to the app.</span></span> <span data-ttu-id="28315-108">Örneğin dosyaları içeren eklediğiniz `AccountInformation` ve `MonthlyReportRecords` türleri projeniz için proje dosya yapısı düz ve kolay gidin:</span><span class="sxs-lookup"><span data-stu-id="28315-108">For example if you add files containing `AccountInformation` and `MonthlyReportRecords` types to your project, the project file structure is flat and easy to navigate:</span></span>

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="28315-109">Ancak, bu yalnızca iyi projenizin boyutu nispeten küçük olduğunda çalışır.</span><span class="sxs-lookup"><span data-stu-id="28315-109">However, this only works well when the size of your project is relatively small.</span></span> <span data-ttu-id="28315-110">Ne olacağını düşünün projeye 20 türleri eklerseniz?</span><span class="sxs-lookup"><span data-stu-id="28315-110">Can you imagine what will happen if you add 20 types to the project?</span></span> <span data-ttu-id="28315-111">Proje kesinlikle gidin ve ile çok sayıda dosya projenin kök dizinini doldurmak korumak kolay değildir.</span><span class="sxs-lookup"><span data-stu-id="28315-111">The project definitely wouldn't be easy to navigate and maintain with that many files littering the project's root directory.</span></span>

<span data-ttu-id="28315-112">Proje düzenlemek için yeni bir klasör oluşturun ve adlandırın *modelleri* tür dosyalarını tutacak.</span><span class="sxs-lookup"><span data-stu-id="28315-112">To organize the project, create a new folder and name it *Models* to hold the type files.</span></span> <span data-ttu-id="28315-113">Türü dosyaları içine yerleştirebilir *modelleri* klasörü:</span><span class="sxs-lookup"><span data-stu-id="28315-113">Place the type files into the *Models* folder:</span></span>

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="28315-114">Mantıksal olarak klasörlere Grup dosyaları gidin ve korumak kolay projeleri.</span><span class="sxs-lookup"><span data-stu-id="28315-114">Projects that logically group files into folders are easy to navigate and maintain.</span></span> <span data-ttu-id="28315-115">Sonraki bölümde, klasör ve birim testi ile daha karmaşık bir örnek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="28315-115">In the next section, you create a more complex sample with folders and unit testing.</span></span>

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a><span data-ttu-id="28315-116">Düzenleme ve NewTypes Evcil Hayvanlar örneğini kullanarak test etme</span><span class="sxs-lookup"><span data-stu-id="28315-116">Organizing and testing using the NewTypes Pets Sample</span></span>

### <a name="building-the-sample"></a><span data-ttu-id="28315-117">Örnek oluşturma</span><span class="sxs-lookup"><span data-stu-id="28315-117">Building the sample</span></span>

<span data-ttu-id="28315-118">Aşağıdaki adımları için aşağıdakilerden birini kullanarak izleyebilirsiniz [NewTypes Evcil Hayvanlar örnek](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) veya dosya ve klasörlerinizi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="28315-118">For the following steps, you can either follow along using the [NewTypes Pets Sample](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) or create your own files and folders.</span></span> <span data-ttu-id="28315-119">Testler ayrıca mantıksal olarak klasörlere daha sonra ayrıca daha fazla test sorgulamasına yerleştirilir ve türlerini mantıksal olarak daha fazla türlerinin eklenmesi daha sonra izin veren bir klasör yapısına düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="28315-119">The types are logically organized into a folder structure that permits the addition of more types later, and tests are also logically placed in folders permitting the addition of more tests later.</span></span>

<span data-ttu-id="28315-120">İki tür örnek içeren `Dog` ve `Cat`ve bunları ortak bir arabirim uygulamak `IPet`.</span><span class="sxs-lookup"><span data-stu-id="28315-120">The sample contains two types, `Dog` and `Cat`, and has them implement a common interface, `IPet`.</span></span> <span data-ttu-id="28315-121">İçin `NewTypes` amacınız projesidir evcil hayvan ilgili tür olarak düzenlemek için bir *Evcil Hayvanlar* klasör.</span><span class="sxs-lookup"><span data-stu-id="28315-121">For the `NewTypes` project, your goal is to organize the pet-related types into a *Pets* folder.</span></span> <span data-ttu-id="28315-122">Daha sonra başka bir dizi türleri eklenirse *WildAnimals* bunlar, örneğin, yerleştirilir *NewTypes* klasör yanı sıra *Evcil Hayvanlar* klasör.</span><span class="sxs-lookup"><span data-stu-id="28315-122">If another set of types is added later, *WildAnimals* for example, they're placed in the *NewTypes* folder alongside the *Pets* folder.</span></span> <span data-ttu-id="28315-123">*WildAnimals* klasör hayvanlar gibi olmayan hayvanlar türleri içerebilir `Squirrel` ve `Rabbit` türleri.</span><span class="sxs-lookup"><span data-stu-id="28315-123">The *WildAnimals* folder may contain types for animals that aren't pets, such as `Squirrel` and `Rabbit` types.</span></span> <span data-ttu-id="28315-124">Bu şekilde türleri eklendikçe proje de düzenli olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="28315-124">In this way as types are added, the project remains well organized.</span></span> 

<span data-ttu-id="28315-125">Aşağıdaki klasör yapısını, belirtilen dosya içeriği oluşturun:</span><span class="sxs-lookup"><span data-stu-id="28315-125">Create the following folder structure with file content indicated:</span></span>

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

<span data-ttu-id="28315-126">*IPet.cs*:</span><span class="sxs-lookup"><span data-stu-id="28315-126">*IPet.cs*:</span></span>

[!code-csharp[IPet interface](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/IPet.cs)]

<span data-ttu-id="28315-127">*Dog.cs*:</span><span class="sxs-lookup"><span data-stu-id="28315-127">*Dog.cs*:</span></span>

[!code-csharp[Dog class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Dog.cs)]

<span data-ttu-id="28315-128">*Cat.cs*:</span><span class="sxs-lookup"><span data-stu-id="28315-128">*Cat.cs*:</span></span>

[!code-csharp[Cat class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Cat.cs)]

<span data-ttu-id="28315-129">*Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="28315-129">*Program.cs*:</span></span>

[!code-csharp[Main](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Program.cs)]

<span data-ttu-id="28315-130">*NewTypes.csproj*:</span><span class="sxs-lookup"><span data-stu-id="28315-130">*NewTypes.csproj*:</span></span>

[!code-xml[NewTypes csproj](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/NewTypes.csproj)]

<span data-ttu-id="28315-131">Aşağıdaki komutları yürütün:</span><span class="sxs-lookup"><span data-stu-id="28315-131">Execute the following commands:</span></span>

```console
dotnet run
```

<span data-ttu-id="28315-132">Aşağıdaki çıktıyı alın:</span><span class="sxs-lookup"><span data-stu-id="28315-132">Obtain the following output:</span></span>

```console
Woof!
Meow!
```

<span data-ttu-id="28315-133">İsteğe bağlı alıştırma: yeni bir evcil hayvan türü gibi ekleyebilirsiniz bir `Bird`, bu proje genişleterek.</span><span class="sxs-lookup"><span data-stu-id="28315-133">Optional exercise: You can add a new pet type, such as a `Bird`, by extending this project.</span></span> <span data-ttu-id="28315-134">Kuşbakışı olun `TalkToOwner` yöntemi verin bir `Tweet!` sahibine.</span><span class="sxs-lookup"><span data-stu-id="28315-134">Make the bird's `TalkToOwner` method give a `Tweet!` to the owner.</span></span> <span data-ttu-id="28315-135">Uygulamayı yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="28315-135">Run the app again.</span></span> <span data-ttu-id="28315-136">Çıkış içerir `Tweet!`</span><span class="sxs-lookup"><span data-stu-id="28315-136">The output will include `Tweet!`</span></span>

### <a name="testing-the-sample"></a><span data-ttu-id="28315-137">Örnek test etme</span><span class="sxs-lookup"><span data-stu-id="28315-137">Testing the sample</span></span>

<span data-ttu-id="28315-138">`NewTypes` Proje yerinde olduğundan ve bir klasörde Evcil Hayvanlar ilgili türleri tutarak düzenlediğiniz.</span><span class="sxs-lookup"><span data-stu-id="28315-138">The `NewTypes` project is in place, and you've organized it by keeping the pets-related types in a folder.</span></span> <span data-ttu-id="28315-139">Ardından, test projenizi oluşturmak ve testleri yazmaya [xUnit](https://xunit.github.io/) test çerçevesi.</span><span class="sxs-lookup"><span data-stu-id="28315-139">Next, create your test project and start writing tests with the [xUnit](https://xunit.github.io/) test framework.</span></span> <span data-ttu-id="28315-140">Birim testi, otomatik olarak bunlar düzgün şekilde çalıştıklarından olduğunu onaylamak için evcil hayvan türlerinin bevahior denetlemek sağlar.</span><span class="sxs-lookup"><span data-stu-id="28315-140">Unit testing allows you to automatically check the bevahior of your pet types to confirm that they're operating properly.</span></span>

<span data-ttu-id="28315-141">Oluşturma bir *test* klasörüyle bir *NewTypesTests* içindeki klasör.</span><span class="sxs-lookup"><span data-stu-id="28315-141">Create a *test* folder with a *NewTypesTests* folder within it.</span></span> <span data-ttu-id="28315-142">Bir komut istemi'nden en *NewTypesTests* klasöründe yürütme `dotnet new xunit`.</span><span class="sxs-lookup"><span data-stu-id="28315-142">At a command prompt from the *NewTypesTests* folder, execute `dotnet new xunit`.</span></span> <span data-ttu-id="28315-143">Bu iki dosya oluşturur: *NewTypesTests.csproj* ve *UnitTest1.cs*.</span><span class="sxs-lookup"><span data-stu-id="28315-143">This produces two files: *NewTypesTests.csproj* and *UnitTest1.cs*.</span></span>

<span data-ttu-id="28315-144">Test projesi türleri şu anda test edilemez `NewTypes` ve bir proje başvurusu gerektirir `NewTypes` proje.</span><span class="sxs-lookup"><span data-stu-id="28315-144">The test project cannot currently test the types in `NewTypes` and requires a project reference to the `NewTypes` project.</span></span> <span data-ttu-id="28315-145">Bir proje başvurusu eklemek için [ `dotnet add reference` ](../tools/dotnet-add-reference.md) komutu:</span><span class="sxs-lookup"><span data-stu-id="28315-145">To add a project reference, use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

<span data-ttu-id="28315-146">El ile ekleyerek proje başvurusu ekleme seçeneğiniz de bir `<ItemGroup>` düğüme *NewTypesTests.csproj* dosyası:</span><span class="sxs-lookup"><span data-stu-id="28315-146">You also have the option of manually adding the project reference by adding an `<ItemGroup>` node to the *NewTypesTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

<span data-ttu-id="28315-147">*NewTypesTests.csproj*:</span><span class="sxs-lookup"><span data-stu-id="28315-147">*NewTypesTests.csproj*:</span></span>

[!code-xml[NewTypesTests csproj](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/NewTypesTests.csproj)]

<span data-ttu-id="28315-148">*NewTypesTests.csproj* dosyası şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="28315-148">The *NewTypesTests.csproj* file contains the following:</span></span>

* <span data-ttu-id="28315-149">Başvuru paketi `Microsoft.NET.Test.Sdk`, altyapı test .NET</span><span class="sxs-lookup"><span data-stu-id="28315-149">Package reference to `Microsoft.NET.Test.Sdk`, the .NET testing infrastructure</span></span>
* <span data-ttu-id="28315-150">Başvuru paketi `xunit`, xUnit testi çerçevesi</span><span class="sxs-lookup"><span data-stu-id="28315-150">Package reference to `xunit`, the xUnit testing framework</span></span>
* <span data-ttu-id="28315-151">Başvuru paketi `xunit.runner.visualstudio`, test Çalıştırıcısı</span><span class="sxs-lookup"><span data-stu-id="28315-151">Package reference to `xunit.runner.visualstudio`, the test runner</span></span>
* <span data-ttu-id="28315-152">Proje başvurusu `NewTypes`, kodu test etmek için</span><span class="sxs-lookup"><span data-stu-id="28315-152">Project reference to `NewTypes`, the code to test</span></span>

<span data-ttu-id="28315-153">Adını değiştirmek *UnitTest1.cs* için *PetTests.cs* dosyasındaki kodu aşağıdakiyle değiştirin:</span><span class="sxs-lookup"><span data-stu-id="28315-153">Change the name of *UnitTest1.cs* to *PetTests.cs* and replace the code in the file with the following:</span></span>

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

<span data-ttu-id="28315-154">İsteğe bağlı alıştırma: eklediyseniz bir `Bird` verir türü daha önce bir `Tweet!` sahibine bir test yöntemine ekleyin *PetTests.cs* dosyası `BirdTalkToOwnerReturnsTweet`denetlemek için `TalkToOwner` yöntemi doğru çalıştığı `Bird` türü.</span><span class="sxs-lookup"><span data-stu-id="28315-154">Optional exercise: If you added a `Bird` type earlier that yields a `Tweet!` to the owner, add a test method to the *PetTests.cs* file, `BirdTalkToOwnerReturnsTweet`, to check that the `TalkToOwner` method works correctly for the `Bird` type.</span></span>

> [!NOTE]
> <span data-ttu-id="28315-155">Beklediğiniz ancak `expected` ve `actual` değerler eşit olan ilk onaylama `Assert.NotEqual` denetimini, bu değerler olduğunu belirtir *eşit değil*.</span><span class="sxs-lookup"><span data-stu-id="28315-155">Although you expect that the `expected` and `actual` values are equal, an initial assertion with the `Assert.NotEqual` check specifies that these values are *not equal*.</span></span> <span data-ttu-id="28315-156">Her zaman başlangıçta test mantığını denetlemek için başarısız bir test oluşturun.</span><span class="sxs-lookup"><span data-stu-id="28315-156">Always initially create a test to fail in order to check the logic of the test.</span></span> <span data-ttu-id="28315-157">Testin başarısız olduğunu onayladıktan sonra onaylama test geçmesine izin verecek şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="28315-157">After you confirm that the test fails, adjust the assertion to allow the test to pass.</span></span>

<span data-ttu-id="28315-158">Tam proje yapısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="28315-158">The following shows the complete project structure:</span></span>

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

<span data-ttu-id="28315-159">Başlangıç *test/NewTypesTests* dizin.</span><span class="sxs-lookup"><span data-stu-id="28315-159">Start in the *test/NewTypesTests* directory.</span></span> <span data-ttu-id="28315-160">Test projesi ile geri [ `dotnet restore` ](../tools/dotnet-restore.md) komutu.</span><span class="sxs-lookup"><span data-stu-id="28315-160">Restore the test project with the [`dotnet restore`](../tools/dotnet-restore.md) command.</span></span> <span data-ttu-id="28315-161">Testler ile [ `dotnet test` ](../tools/dotnet-test.md) komutu.</span><span class="sxs-lookup"><span data-stu-id="28315-161">Run the tests with the [`dotnet test`](../tools/dotnet-test.md) command.</span></span> <span data-ttu-id="28315-162">Bu komut, proje dosyasında belirtilen test Çalıştırıcısı başlatır.</span><span class="sxs-lookup"><span data-stu-id="28315-162">This command starts the test runner specified in the project file.</span></span>

 [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

 
<span data-ttu-id="28315-163">Test başarısız olur ve konsolu, beklendiği gibi aşağıdaki çıkışı görüntüler:</span><span class="sxs-lookup"><span data-stu-id="28315-163">As expected, testing fails, and the console displays the following output:</span></span>
 
```
Test run for C:\NewTypesMsBuild\test\NewTypesTests\bin\Debug\netcoreapp1.1\NewTypesTests.dll(.NETCoreApp,Version=v1.1)
Microsoft (R) Test Execution Command Line Tool Version 15.0.0.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
[xUnit.net 00:00:00.7271827]   Discovering: NewTypesTests
[xUnit.net 00:00:00.8258687]   Discovered:  NewTypesTests
[xUnit.net 00:00:00.8663545]   Starting:    NewTypesTests
[xUnit.net 00:00:01.0109236]     PetTests.CatTalkToOwnerReturnsMeow [FAIL]
[xUnit.net 00:00:01.0119107]       Assert.NotEqual() Failure
[xUnit.net 00:00:01.0120278]       Expected: Not "Meow!"
[xUnit.net 00:00:01.0120968]       Actual:   "Meow!"
[xUnit.net 00:00:01.0130500]       Stack Trace:
[xUnit.net 00:00:01.0141240]         C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs(22,0): at PetTests.CatTalkToOwnerReturnsMeow()
[xUnit.net 00:00:01.0272364]     PetTests.DogTalkToOwnerReturnsWoof [FAIL]
[xUnit.net 00:00:01.0273649]       Assert.NotEqual() Failure
[xUnit.net 00:00:01.0274166]       Expected: Not "Woof!"
[xUnit.net 00:00:01.0274690]       Actual:   "Woof!"
[xUnit.net 00:00:01.0275264]       Stack Trace:
[xUnit.net 00:00:01.0275960]         C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs(13,0): at PetTests.DogTalkToOwnerReturnsWoof()
[xUnit.net 00:00:01.0294509]   Finished:    NewTypesTests
Failed   PetTests.CatTalkToOwnerReturnsMeow
Error Message:
 Assert.NotEqual() Failure
Expected: Not "Meow!"
Actual:   "Meow!"
Stack Trace:
   at PetTests.CatTalkToOwnerReturnsMeow() in C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs:line 22
Failed   PetTests.DogTalkToOwnerReturnsWoof
Error Message:
 Assert.NotEqual() Failure
Expected: Not "Woof!"
Actual:   "Woof!"
Stack Trace:
   at PetTests.DogTalkToOwnerReturnsWoof() in C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs:line 13

Total tests: 2. Passed: 0. Failed: 2. Skipped: 0.
Test Run Failed.
Test execution time: 2.1371 Seconds
```

<span data-ttu-id="28315-164">Testlerinizin onaylamaları değiştirme `Assert.NotEqual` için `Assert.Equal`:</span><span class="sxs-lookup"><span data-stu-id="28315-164">Change the assertions of your tests from `Assert.NotEqual` to `Assert.Equal`:</span></span>

[!code-csharp[PetTests class](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/PetTests.cs)]

<span data-ttu-id="28315-165">Testleri yeniden çalıştırın `dotnet test` komutunu ve aşağıdaki çıktıyı alın:</span><span class="sxs-lookup"><span data-stu-id="28315-165">Re-run the tests with the `dotnet test` command and obtain the following output:</span></span>

```
Microsoft (R) Test Execution Command Line Tool Version 15.0.0.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
[xUnit.net 00:00:01.3882374]   Discovering: NewTypesTests
[xUnit.net 00:00:01.4767970]   Discovered:  NewTypesTests
[xUnit.net 00:00:01.5157667]   Starting:    NewTypesTests
[xUnit.net 00:00:01.6408870]   Finished:    NewTypesTests

Total tests: 2. Passed: 2. Failed: 0. Skipped: 0.
Test Run Successful.
Test execution time: 1.6634 Seconds
```

<span data-ttu-id="28315-166">Geçiş testi.</span><span class="sxs-lookup"><span data-stu-id="28315-166">Testing passes.</span></span> <span data-ttu-id="28315-167">Evcil hayvan türleri yöntemleri, sahibi konuşurken doğru değerleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="28315-167">The pet types' methods return the correct values when talking to the owner.</span></span>

<span data-ttu-id="28315-168">Düzenleme ve xUnit kullanarak projeleri test teknikleri öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="28315-168">You've learned techniques for organizing and testing projects using xUnit.</span></span> <span data-ttu-id="28315-169">Bunları kendi projelerinde uygulayarak bu teknikler ile ileri gidin.</span><span class="sxs-lookup"><span data-stu-id="28315-169">Go forward with these techniques applying them in your own projects.</span></span> <span data-ttu-id="28315-170">*İyi Kodlamalar!*</span><span class="sxs-lookup"><span data-stu-id="28315-170">*Happy coding!*</span></span>

