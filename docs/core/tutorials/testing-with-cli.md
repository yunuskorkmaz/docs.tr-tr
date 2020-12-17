---
title: .NET CLı ile projeleri düzenleme ve test etme
description: Bu öğreticide, komut satırından .NET projelerinin nasıl düzenlenmesi ve test yapılacağı açıklanmaktadır.
author: cartermp
ms.date: 09/10/2018
ms.openlocfilehash: 263eaf15beac008de8bb353a385b8f3588a7fefc
ms.sourcegitcommit: 635a0ff775d2447a81ef7233a599b8f88b162e5d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97633643"
---
# <a name="organizing-and-testing-projects-with-the-net-cli"></a><span data-ttu-id="71bd5-103">.NET CLı ile projeleri düzenleme ve test etme</span><span class="sxs-lookup"><span data-stu-id="71bd5-103">Organizing and testing projects with the .NET CLI</span></span>

<span data-ttu-id="71bd5-104">Bu öğretici [öğretici: Visual Studio Code kullanarak .NET ile bir konsol uygulaması oluşturma](with-visual-studio-code.md), gelişmiş ve iyi düzenlenmiş uygulamalar geliştirmeye yönelik basit bir konsol uygulaması oluşturmayı aşarak.</span><span class="sxs-lookup"><span data-stu-id="71bd5-104">This tutorial follows [Tutorial: Create a console application with .NET using Visual Studio Code](with-visual-studio-code.md), taking you beyond the creation of a simple console app to develop advanced and well-organized applications.</span></span> <span data-ttu-id="71bd5-105">Kodunuzu düzenlemek için klasörleri nasıl kullanacağınızı gösterdikten sonra, bu öğreticide [xUnit](https://xunit.net/) test çerçevesiyle bir konsol uygulamasını nasıl genişletebileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="71bd5-105">After showing you how to use folders to organize your code, this tutorial shows you how to extend a console application with the [xUnit](https://xunit.net/) testing framework.</span></span>

## <a name="using-folders-to-organize-code"></a><span data-ttu-id="71bd5-106">Kodu düzenlemek için klasörleri kullanma</span><span class="sxs-lookup"><span data-stu-id="71bd5-106">Using folders to organize code</span></span>

<span data-ttu-id="71bd5-107">Konsol uygulamasına yeni türler eklemek istiyorsanız, türleri uygulamaya içeren dosyaları ekleyerek bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="71bd5-107">If you want to introduce new types into a console app, you can do so by adding files containing the types to the app.</span></span> <span data-ttu-id="71bd5-108">Örneğin `AccountInformation` , projenize ve türlerini içeren dosyaları eklerseniz `MonthlyReportRecords` , proje dosya yapısı düz ve gezinmek kolaydır:</span><span class="sxs-lookup"><span data-stu-id="71bd5-108">For example if you add files containing `AccountInformation` and `MonthlyReportRecords` types to your project, the project file structure is flat and easy to navigate:</span></span>

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="71bd5-109">Ancak, bu yalnızca projenizin boyutu nispeten küçük olduğunda iyi bir şekilde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="71bd5-109">However, this only works well when the size of your project is relatively small.</span></span> <span data-ttu-id="71bd5-110">Projeye 20 tür eklerseniz ne olacağını anlaz edebilir misiniz?</span><span class="sxs-lookup"><span data-stu-id="71bd5-110">Can you imagine what will happen if you add 20 types to the project?</span></span> <span data-ttu-id="71bd5-111">Projenin, bu birçok dosya üzerinde gezinilmesi ve projenin kök dizinini oluşturma konusunda kesinlikle kolay olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="71bd5-111">The project definitely wouldn't be easy to navigate and maintain with that many files littering the project's root directory.</span></span>

<span data-ttu-id="71bd5-112">Projeyi düzenlemek için yeni bir klasör oluşturun ve bunu tür dosyalarını tutacak şekilde *modelleyen* şekilde adlandırın.</span><span class="sxs-lookup"><span data-stu-id="71bd5-112">To organize the project, create a new folder and name it *Models* to hold the type files.</span></span> <span data-ttu-id="71bd5-113">Tür dosyalarını *modeller* klasörüne yerleştirin:</span><span class="sxs-lookup"><span data-stu-id="71bd5-113">Place the type files into the *Models* folder:</span></span>

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="71bd5-114">Dosyaları klasörlere mantıksal olarak gruplandıran projeler arasında gezinmek ve bakım yapmak kolaydır.</span><span class="sxs-lookup"><span data-stu-id="71bd5-114">Projects that logically group files into folders are easy to navigate and maintain.</span></span> <span data-ttu-id="71bd5-115">Sonraki bölümde, klasörler ve birim testi ile daha karmaşık bir örnek oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="71bd5-115">In the next section, you create a more complex sample with folders and unit testing.</span></span>

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a><span data-ttu-id="71bd5-116">NewTypes pets örneğini kullanarak düzenleme ve test etme</span><span class="sxs-lookup"><span data-stu-id="71bd5-116">Organizing and testing using the NewTypes Pets Sample</span></span>

### <a name="prerequisites"></a><span data-ttu-id="71bd5-117">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="71bd5-117">Prerequisites</span></span>

* <span data-ttu-id="71bd5-118">[.Net 5,0 SDK](https://dotnet.microsoft.com/download) veya sonraki bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="71bd5-118">[.NET 5.0 SDK](https://dotnet.microsoft.com/download) or a later version.</span></span>

### <a name="building-the-sample"></a><span data-ttu-id="71bd5-119">Örnek oluşturma</span><span class="sxs-lookup"><span data-stu-id="71bd5-119">Building the sample</span></span>

<span data-ttu-id="71bd5-120">Aşağıdaki adımlar için, [Newtypes pets örneğini](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) kullanarak takip edebilir veya kendi dosya ve klasörlerinizi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="71bd5-120">For the following steps, you can either follow along using the [NewTypes Pets Sample](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) or create your own files and folders.</span></span> <span data-ttu-id="71bd5-121">Türler, daha sonra daha fazla türden eklenmesine izin veren bir klasör yapısına mantıksal olarak düzenlenir ve testler daha sonra daha fazla test eklenmesine izin veren klasörlere de mantıksal olarak yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="71bd5-121">The types are logically organized into a folder structure that permits the addition of more types later, and tests are also logically placed in folders permitting the addition of more tests later.</span></span>

<span data-ttu-id="71bd5-122">Örnek iki tür içerir ve ve `Dog` `Cat` , ortak bir arabirim uygular `IPet` .</span><span class="sxs-lookup"><span data-stu-id="71bd5-122">The sample contains two types, `Dog` and `Cat`, and has them implement a common interface, `IPet`.</span></span> <span data-ttu-id="71bd5-123">Projeniz için `NewTypes` amacınız, Evcil hayvan ile ilgili türleri bir *pets* klasörü olarak düzenmaktır.</span><span class="sxs-lookup"><span data-stu-id="71bd5-123">For the `NewTypes` project, your goal is to organize the pet-related types into a *Pets* folder.</span></span> <span data-ttu-id="71bd5-124">Daha sonra başka bir tür kümesi eklenirse, *WildAnimals* Örneğin, *pets* klasörüyle birlikte *newtypes* klasörüne yerleştirilirler.</span><span class="sxs-lookup"><span data-stu-id="71bd5-124">If another set of types is added later, *WildAnimals* for example, they're placed in the *NewTypes* folder alongside the *Pets* folder.</span></span> <span data-ttu-id="71bd5-125">*WildAnimals* klasörü, ve türleri gibi pets olmayan hayvanlar için türler içerebilir `Squirrel` `Rabbit` .</span><span class="sxs-lookup"><span data-stu-id="71bd5-125">The *WildAnimals* folder may contain types for animals that aren't pets, such as `Squirrel` and `Rabbit` types.</span></span> <span data-ttu-id="71bd5-126">Bu şekilde, türler eklendikçe, proje iyi organize edilmiş kalır.</span><span class="sxs-lookup"><span data-stu-id="71bd5-126">In this way as types are added, the project remains well organized.</span></span>

<span data-ttu-id="71bd5-127">Belirtilen dosya içeriğiyle aşağıdaki klasör yapısını oluşturun:</span><span class="sxs-lookup"><span data-stu-id="71bd5-127">Create the following folder structure with file content indicated:</span></span>

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

<span data-ttu-id="71bd5-128">*IPet.cs*:</span><span class="sxs-lookup"><span data-stu-id="71bd5-128">*IPet.cs*:</span></span>

[!code-csharp[IPet interface](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/IPet.cs)]

<span data-ttu-id="71bd5-129">*Dog.cs*:</span><span class="sxs-lookup"><span data-stu-id="71bd5-129">*Dog.cs*:</span></span>

[!code-csharp[Dog class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/Dog.cs)]

<span data-ttu-id="71bd5-130">*Cat.cs*:</span><span class="sxs-lookup"><span data-stu-id="71bd5-130">*Cat.cs*:</span></span>

[!code-csharp[Cat class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/Cat.cs)]

<span data-ttu-id="71bd5-131">*Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="71bd5-131">*Program.cs*:</span></span>

[!code-csharp[Main](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Program.cs)]

<span data-ttu-id="71bd5-132">*Newtypes. csproj*:</span><span class="sxs-lookup"><span data-stu-id="71bd5-132">*NewTypes.csproj*:</span></span>

[!code-xml[NewTypes csproj](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/NewTypes.csproj)]

<span data-ttu-id="71bd5-133">Aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="71bd5-133">Execute the following command:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="71bd5-134">Aşağıdaki çıktıyı alın:</span><span class="sxs-lookup"><span data-stu-id="71bd5-134">Obtain the following output:</span></span>

```console
Woof!
Meow!
```

<span data-ttu-id="71bd5-135">İsteğe bağlı alıştırma: `Bird` Bu projeyi genişleterek, gibi yeni bir evcil hayvan türü ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="71bd5-135">Optional exercise: You can add a new pet type, such as a `Bird`, by extending this project.</span></span> <span data-ttu-id="71bd5-136">Kuşın `TalkToOwner` yönteminin sahibine vermesini sağlayın `Tweet!` .</span><span class="sxs-lookup"><span data-stu-id="71bd5-136">Make the bird's `TalkToOwner` method give a `Tweet!` to the owner.</span></span> <span data-ttu-id="71bd5-137">Uygulamayı tekrar çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="71bd5-137">Run the app again.</span></span> <span data-ttu-id="71bd5-138">Çıktıda şunlar yer alır `Tweet!`</span><span class="sxs-lookup"><span data-stu-id="71bd5-138">The output will include `Tweet!`</span></span>

### <a name="testing-the-sample"></a><span data-ttu-id="71bd5-139">Örneği test etme</span><span class="sxs-lookup"><span data-stu-id="71bd5-139">Testing the sample</span></span>

<span data-ttu-id="71bd5-140">`NewTypes`Proje yerinde ve pets ile ilgili türleri bir klasörde tutarak düzenlemiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="71bd5-140">The `NewTypes` project is in place, and you've organized it by keeping the pets-related types in a folder.</span></span> <span data-ttu-id="71bd5-141">Ardından, test projenizi oluşturun ve [xUnit](https://xunit.net/) test çerçevesi ile testleri yazmaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="71bd5-141">Next, create your test project and start writing tests with the [xUnit](https://xunit.net/) test framework.</span></span> <span data-ttu-id="71bd5-142">Birim testi, sorunsuz şekilde çalıştığının nasıl yapılacağını onaylamak için evcil hayvan türlerinizi davranışını otomatik olarak denetlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="71bd5-142">Unit testing allows you to automatically check the behavior of your pet types to confirm that they're operating properly.</span></span>

<span data-ttu-id="71bd5-143">*Src* klasörüne geri gidin ve Içinde *newtypestests* klasörünü içeren bir *Test* klasörü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="71bd5-143">Navigate back to the *src* folder and create a *test* folder with a *NewTypesTests* folder within it.</span></span> <span data-ttu-id="71bd5-144">*Newtypestests* klasöründen bir komut isteminde yürütün `dotnet new xunit` .</span><span class="sxs-lookup"><span data-stu-id="71bd5-144">At a command prompt from the *NewTypesTests* folder, execute `dotnet new xunit`.</span></span> <span data-ttu-id="71bd5-145">Bu iki dosya üretir: *Newtypestests. csproj* ve *UnitTest1.cs*.</span><span class="sxs-lookup"><span data-stu-id="71bd5-145">This produces two files: *NewTypesTests.csproj* and *UnitTest1.cs*.</span></span>

<span data-ttu-id="71bd5-146">Test projesi şu anda içindeki türleri test edemez `NewTypes` ve projeye bir proje başvurusu gerektiriyor `NewTypes` .</span><span class="sxs-lookup"><span data-stu-id="71bd5-146">The test project cannot currently test the types in `NewTypes` and requires a project reference to the `NewTypes` project.</span></span> <span data-ttu-id="71bd5-147">Bir proje başvurusu eklemek için [`dotnet add reference`](../tools/dotnet-add-reference.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="71bd5-147">To add a project reference, use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

<span data-ttu-id="71bd5-148">Ya da `<ItemGroup>` *Newtypestests. csproj* dosyasına bir düğüm ekleyerek proje başvurusunu el ile ekleme seçeneğiniz de vardır:</span><span class="sxs-lookup"><span data-stu-id="71bd5-148">Or, you also have the option of manually adding the project reference by adding an `<ItemGroup>` node to the *NewTypesTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

<span data-ttu-id="71bd5-149">*Newtypestests. csproj*:</span><span class="sxs-lookup"><span data-stu-id="71bd5-149">*NewTypesTests.csproj*:</span></span>

[!code-xml[NewTypesTests csproj](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/test/NewTypesTests/NewTypesTests.csproj)]

<span data-ttu-id="71bd5-150">*Newtypestests. csproj* dosyası şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="71bd5-150">The *NewTypesTests.csproj* file contains the following:</span></span>

* <span data-ttu-id="71bd5-151">`Microsoft.NET.Test.Sdk`.Net test altyapısına paket başvurusu</span><span class="sxs-lookup"><span data-stu-id="71bd5-151">Package reference to `Microsoft.NET.Test.Sdk`, the .NET testing infrastructure</span></span>
* <span data-ttu-id="71bd5-152">Paket başvurusu `xunit` , xUnit test çerçevesi</span><span class="sxs-lookup"><span data-stu-id="71bd5-152">Package reference to `xunit`, the xUnit testing framework</span></span>
* <span data-ttu-id="71bd5-153">Test Çalıştırıcısı 'na paket başvurusu `xunit.runner.visualstudio`</span><span class="sxs-lookup"><span data-stu-id="71bd5-153">Package reference to `xunit.runner.visualstudio`, the test runner</span></span>
* <span data-ttu-id="71bd5-154">Proje başvurusu `NewTypes` , sınanacak kod</span><span class="sxs-lookup"><span data-stu-id="71bd5-154">Project reference to `NewTypes`, the code to test</span></span>

<span data-ttu-id="71bd5-155">*UnitTest1.cs* adını *PetTests.cs* olarak değiştirin ve dosyadaki kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="71bd5-155">Change the name of *UnitTest1.cs* to *PetTests.cs* and replace the code in the file with the following:</span></span>

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

<span data-ttu-id="71bd5-156">İsteğe bağlı alıştırma: `Bird` daha önce sahibine veren bir tür eklediyseniz, `Tweet!`  `BirdTalkToOwnerReturnsTweet` `TalkToOwner` yöntemin tür için doğru çalışıp çalışmadığını denetlemek için PetTests.cs dosyasına bir test yöntemi ekleyin `Bird` .</span><span class="sxs-lookup"><span data-stu-id="71bd5-156">Optional exercise: If you added a `Bird` type earlier that yields a `Tweet!` to the owner, add a test method to the *PetTests.cs* file, `BirdTalkToOwnerReturnsTweet`, to check that the `TalkToOwner` method works correctly for the `Bird` type.</span></span>

> [!NOTE]
> <span data-ttu-id="71bd5-157">Ve değerlerinin eşit olmasını bekleseniz de, `expected` `actual` Check ile bir ilk onaylama, `Assert.NotEqual` Bu değerlerin *eşit* olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="71bd5-157">Although you expect that the `expected` and `actual` values are equal, an initial assertion with the `Assert.NotEqual` check specifies that these values are *not equal*.</span></span> <span data-ttu-id="71bd5-158">Testin mantığını denetlemek için her zaman ilk olarak bir test oluşturun.</span><span class="sxs-lookup"><span data-stu-id="71bd5-158">Always initially create a test to fail in order to check the logic of the test.</span></span> <span data-ttu-id="71bd5-159">Testin başarısız olduğunu doğruladıktan sonra, testi geçirmeye izin verecek şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="71bd5-159">After you confirm that the test fails, adjust the assertion to allow the test to pass.</span></span>

<span data-ttu-id="71bd5-160">Aşağıda, tüm proje yapısı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="71bd5-160">The following shows the complete project structure:</span></span>

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

<span data-ttu-id="71bd5-161">*Test/NewTypesTests* dizininde başlatın.</span><span class="sxs-lookup"><span data-stu-id="71bd5-161">Start in the *test/NewTypesTests* directory.</span></span> <span data-ttu-id="71bd5-162">Komutu ile testleri çalıştırın [`dotnet test`](../tools/dotnet-test.md) .</span><span class="sxs-lookup"><span data-stu-id="71bd5-162">Run the tests with the [`dotnet test`](../tools/dotnet-test.md) command.</span></span> <span data-ttu-id="71bd5-163">Bu komut, proje dosyasında belirtilen Test Çalıştırıcısı 'nı başlatır.</span><span class="sxs-lookup"><span data-stu-id="71bd5-163">This command starts the test runner specified in the project file.</span></span>

<span data-ttu-id="71bd5-164">Beklenen şekilde test başarısız olur ve konsolu aşağıdaki çıktıyı görüntüler:</span><span class="sxs-lookup"><span data-stu-id="71bd5-164">As expected, testing fails, and the console displays the following output:</span></span>

```output
Test run for C:\Source\dotnet\docs\samples\snippets\core\tutorials\testing-with-cli\csharp\test\NewTypesTests\bin\Debug\net5.0\NewTypesTests.dll (.NETCoreApp,Version=v5.0)
Microsoft (R) Test Execution Command Line Tool Version 16.8.1
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
A total of 1 test files matched the specified pattern.
[xUnit.net 00:00:00.50]     PetTests.DogTalkToOwnerReturnsWoof [FAIL]
  Failed PetTests.DogTalkToOwnerReturnsWoof [6 ms]
  Error Message:
   Assert.NotEqual() Failure
Expected: Not "Woof!"
Actual:   "Woof!"
  Stack Trace:
     at PetTests.DogTalkToOwnerReturnsWoof() in C:\Source\dotnet\docs\samples\snippets\core\tutorials\testing-with-cli\csharp\test\NewTypesTests\PetTests.cs:line 13

Failed!  - Failed:     1, Passed:     1, Skipped:     0, Total:     2, Duration: 8 ms - NewTypesTests.dll (net5.0)
```

<span data-ttu-id="71bd5-165">Testlerinizin onaylamalarını şu `Assert.NotEqual` şekilde değiştirin `Assert.Equal` :</span><span class="sxs-lookup"><span data-stu-id="71bd5-165">Change the assertions of your tests from `Assert.NotEqual` to `Assert.Equal`:</span></span>

[!code-csharp[PetTests class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/test/NewTypesTests/PetTests.cs)]

<span data-ttu-id="71bd5-166">Komutu ile testleri yeniden çalıştırın `dotnet test` ve aşağıdaki çıktıyı alın:</span><span class="sxs-lookup"><span data-stu-id="71bd5-166">Re-run the tests with the `dotnet test` command and obtain the following output:</span></span>

```output
Test run for C:\Source\dotnet\docs\samples\snippets\core\tutorials\testing-with-cli\csharp\test\NewTypesTests\bin\Debug\net5.0\NewTypesTests.dll (.NETCoreApp,Version=v5.0)
Microsoft (R) Test Execution Command Line Tool Version 16.8.1
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
A total of 1 test files matched the specified pattern.

Passed!  - Failed:     0, Passed:     2, Skipped:     0, Total:     2, Duration: 2 ms - NewTypesTests.dll (net5.0)
```

<span data-ttu-id="71bd5-167">Test geçişleri.</span><span class="sxs-lookup"><span data-stu-id="71bd5-167">Testing passes.</span></span> <span data-ttu-id="71bd5-168">Evcil hayvan türleri ' yöntemleri, sahibiyle konuşurken doğru değerleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="71bd5-168">The pet types' methods return the correct values when talking to the owner.</span></span>

<span data-ttu-id="71bd5-169">XUnit kullanarak projeleri düzenleme ve test etme tekniklerini öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="71bd5-169">You've learned techniques for organizing and testing projects using xUnit.</span></span> <span data-ttu-id="71bd5-170">Bunları kendi projelerinize uygulayarak bu tekniklerle ileri gidin.</span><span class="sxs-lookup"><span data-stu-id="71bd5-170">Go forward with these techniques applying them in your own projects.</span></span> <span data-ttu-id="71bd5-171">*Kodlarım kutlu olsun!*</span><span class="sxs-lookup"><span data-stu-id="71bd5-171">*Happy coding!*</span></span>
