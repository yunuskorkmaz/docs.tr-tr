---
title: .NET Core CLI ile projelerin düzenlenmesi ve test edilmesi
description: Bu öğretici, .NET Core projelerinin komut satırından nasıl düzenleneği ve test edilebildiğini açıklar.
author: cartermp
ms.date: 09/10/2018
ms.openlocfilehash: 0d61e0fc004cfcb6d78c49475c7b7f0f523aad2c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78239917"
---
# <a name="organizing-and-testing-projects-with-the-net-core-cli"></a><span data-ttu-id="a60e3-103">.NET Core CLI ile projelerin düzenlenmesi ve test edilmesi</span><span class="sxs-lookup"><span data-stu-id="a60e3-103">Organizing and testing projects with the .NET Core CLI</span></span>

<span data-ttu-id="a60e3-104">Bu öğretici, gelişmiş ve iyi organize edilmiş uygulamalar geliştirmek için basit bir konsol uygulaması oluşturmanın ötesine geçerek [komut satırını kullanarak Windows/Linux/macOS'ta .NET Core ile başlayın.](cli-create-console-app.md)</span><span class="sxs-lookup"><span data-stu-id="a60e3-104">This tutorial follows [Get started with .NET Core on Windows/Linux/macOS using the command line](cli-create-console-app.md), taking you beyond the creation of a simple console app to develop advanced and well-organized applications.</span></span> <span data-ttu-id="a60e3-105">Kodunuzu düzenlemek için klasörleri nasıl kullanacağınızı gösterdikten sonra, bu öğretici, [xUnit](https://xunit.github.io/) test çerçevesi ile bir konsol uygulamasını nasıl genişletisiniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="a60e3-105">After showing you how to use folders to organize your code, this tutorial shows you how to extend a console application with the [xUnit](https://xunit.github.io/) testing framework.</span></span>

## <a name="using-folders-to-organize-code"></a><span data-ttu-id="a60e3-106">Kodu düzenlemek için klasörleri kullanma</span><span class="sxs-lookup"><span data-stu-id="a60e3-106">Using folders to organize code</span></span>

<span data-ttu-id="a60e3-107">Bir konsol uygulamasına yeni türler eklemek istiyorsanız, bunu uygulamaya türleri içeren dosyalar ekleyerek yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a60e3-107">If you want to introduce new types into a console app, you can do so by adding files containing the types to the app.</span></span> <span data-ttu-id="a60e3-108">Örneğin, projenize dosya `AccountInformation` `MonthlyReportRecords` içeren dosyalar ve türler eklerseniz, proje dosyası yapısı düz dür ve gezinmesi kolaydır:</span><span class="sxs-lookup"><span data-stu-id="a60e3-108">For example if you add files containing `AccountInformation` and `MonthlyReportRecords` types to your project, the project file structure is flat and easy to navigate:</span></span>

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="a60e3-109">Ancak, bu yalnızca projenizin boyutu nispeten küçük olduğunda iyi çalışır.</span><span class="sxs-lookup"><span data-stu-id="a60e3-109">However, this only works well when the size of your project is relatively small.</span></span> <span data-ttu-id="a60e3-110">Projeye 20 çeşit eklerseniz neler olacağını hayal edebiliyor musunuz?</span><span class="sxs-lookup"><span data-stu-id="a60e3-110">Can you imagine what will happen if you add 20 types to the project?</span></span> <span data-ttu-id="a60e3-111">Proje kesinlikle gezinmek ve projenin kök dizini çöp bu kadar çok dosya ile korumak kolay olmaz.</span><span class="sxs-lookup"><span data-stu-id="a60e3-111">The project definitely wouldn't be easy to navigate and maintain with that many files littering the project's root directory.</span></span>

<span data-ttu-id="a60e3-112">Projeyi düzenlemek için yeni bir klasör oluşturun ve tür dosyalarını tutmak için *modellere* ad vereb.'</span><span class="sxs-lookup"><span data-stu-id="a60e3-112">To organize the project, create a new folder and name it *Models* to hold the type files.</span></span> <span data-ttu-id="a60e3-113">Tür dosyalarını *Modeller* klasörüne yerleştirin:</span><span class="sxs-lookup"><span data-stu-id="a60e3-113">Place the type files into the *Models* folder:</span></span>

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="a60e3-114">Dosyaları mantıksal olarak klasörlere gruplandıran projelerde gezinmek ve bakımı kolaydır.</span><span class="sxs-lookup"><span data-stu-id="a60e3-114">Projects that logically group files into folders are easy to navigate and maintain.</span></span> <span data-ttu-id="a60e3-115">Sonraki bölümde, klasörler ve birim sınayıile daha karmaşık bir örnek oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="a60e3-115">In the next section, you create a more complex sample with folders and unit testing.</span></span>

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a><span data-ttu-id="a60e3-116">NewTypes Evcil Hayvan Örneği'ni kullanarak düzenleme ve test etme</span><span class="sxs-lookup"><span data-stu-id="a60e3-116">Organizing and testing using the NewTypes Pets Sample</span></span>

### <a name="building-the-sample"></a><span data-ttu-id="a60e3-117">Örneği oluşturma</span><span class="sxs-lookup"><span data-stu-id="a60e3-117">Building the sample</span></span>

<span data-ttu-id="a60e3-118">Aşağıdaki adımlar için, [NewTypes Evcil Hayvanlar Örneği'ni](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) kullanarak takip edebilir veya kendi dosya ve klasörlerinizi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a60e3-118">For the following steps, you can either follow along using the [NewTypes Pets Sample](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) or create your own files and folders.</span></span> <span data-ttu-id="a60e3-119">Türler mantıksal olarak daha sonra daha fazla tür eklenmesine izin veren bir klasör yapısına düzenlenir ve testler daha sonra daha fazla test eklenmesine izin veren klasörlere de mantıksal olarak yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a60e3-119">The types are logically organized into a folder structure that permits the addition of more types later, and tests are also logically placed in folders permitting the addition of more tests later.</span></span>

<span data-ttu-id="a60e3-120">Örnek iki tür `Dog` içerir `Cat`ve , ve onları `IPet`ortak bir arayüz uygulamak vardır.</span><span class="sxs-lookup"><span data-stu-id="a60e3-120">The sample contains two types, `Dog` and `Cat`, and has them implement a common interface, `IPet`.</span></span> <span data-ttu-id="a60e3-121">Proje `NewTypes` için amacınız evcil hayvan ile ilgili türleri Evcil *Hayvanlar* klasöründe düzenlemektir.</span><span class="sxs-lookup"><span data-stu-id="a60e3-121">For the `NewTypes` project, your goal is to organize the pet-related types into a *Pets* folder.</span></span> <span data-ttu-id="a60e3-122">Daha sonra başka bir tür kümesi eklenirse, örneğin *WildAnimals,* *Evcil Hayvanlar* klasörünün yanında *NewTypes* klasörüne yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a60e3-122">If another set of types is added later, *WildAnimals* for example, they're placed in the *NewTypes* folder alongside the *Pets* folder.</span></span> <span data-ttu-id="a60e3-123">*WildAnimals* klasörü, evcil hayvan olmayan hayvanlar için `Squirrel` türler `Rabbit` içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a60e3-123">The *WildAnimals* folder may contain types for animals that aren't pets, such as `Squirrel` and `Rabbit` types.</span></span> <span data-ttu-id="a60e3-124">Bu şekilde türleri eklendikçe, proje iyi organize olmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="a60e3-124">In this way as types are added, the project remains well organized.</span></span>

<span data-ttu-id="a60e3-125">Belirtilen dosya içeriğiyle aşağıdaki klasör yapısını oluşturun:</span><span class="sxs-lookup"><span data-stu-id="a60e3-125">Create the following folder structure with file content indicated:</span></span>

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

<span data-ttu-id="a60e3-126">*IPet.cs*:</span><span class="sxs-lookup"><span data-stu-id="a60e3-126">*IPet.cs*:</span></span>

[!code-csharp[IPet interface](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/IPet.cs)]

<span data-ttu-id="a60e3-127">*Dog.cs*:</span><span class="sxs-lookup"><span data-stu-id="a60e3-127">*Dog.cs*:</span></span>

[!code-csharp[Dog class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/Dog.cs)]

<span data-ttu-id="a60e3-128">*Cat.cs*:</span><span class="sxs-lookup"><span data-stu-id="a60e3-128">*Cat.cs*:</span></span>

[!code-csharp[Cat class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/Cat.cs)]

<span data-ttu-id="a60e3-129">*Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="a60e3-129">*Program.cs*:</span></span>

[!code-csharp[Main](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Program.cs)]

<span data-ttu-id="a60e3-130">*NewTypes.csproj*:</span><span class="sxs-lookup"><span data-stu-id="a60e3-130">*NewTypes.csproj*:</span></span>

[!code-xml[NewTypes csproj](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/NewTypes.csproj)]

<span data-ttu-id="a60e3-131">Aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="a60e3-131">Execute the following command:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="a60e3-132">Aşağıdaki çıktıyı edinin:</span><span class="sxs-lookup"><span data-stu-id="a60e3-132">Obtain the following output:</span></span>

```console
Woof!
Meow!
```

<span data-ttu-id="a60e3-133">İsteğe bağlı egzersiz: Bu projeyi genişleterek yeni bir `Bird`evcil hayvan türü ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a60e3-133">Optional exercise: You can add a new pet type, such as a `Bird`, by extending this project.</span></span> <span data-ttu-id="a60e3-134">Kuşun `TalkToOwner` yöntemi sahibine bir `Tweet!` vermek olun.</span><span class="sxs-lookup"><span data-stu-id="a60e3-134">Make the bird's `TalkToOwner` method give a `Tweet!` to the owner.</span></span> <span data-ttu-id="a60e3-135">Uygulamayı tekrar çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a60e3-135">Run the app again.</span></span> <span data-ttu-id="a60e3-136">Çıktı,`Tweet!`</span><span class="sxs-lookup"><span data-stu-id="a60e3-136">The output will include `Tweet!`</span></span>

### <a name="testing-the-sample"></a><span data-ttu-id="a60e3-137">Numuneyi test etme</span><span class="sxs-lookup"><span data-stu-id="a60e3-137">Testing the sample</span></span>

<span data-ttu-id="a60e3-138">Proje `NewTypes` yerindedir ve evcil hayvanlarla ilgili türleri bir klasörde tutarak düzenlediniz.</span><span class="sxs-lookup"><span data-stu-id="a60e3-138">The `NewTypes` project is in place, and you've organized it by keeping the pets-related types in a folder.</span></span> <span data-ttu-id="a60e3-139">Ardından, test projenizi oluşturun ve [xUnit](https://xunit.github.io/) test çerçevesi ile testler yazmaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="a60e3-139">Next, create your test project and start writing tests with the [xUnit](https://xunit.github.io/) test framework.</span></span> <span data-ttu-id="a60e3-140">Birim testi, evcil hayvan tiplerinizin düzgün çalıştığını doğrulamak için evcil hayvan tiplerinizin davranışını otomatik olarak kontrol etmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a60e3-140">Unit testing allows you to automatically check the behavior of your pet types to confirm that they're operating properly.</span></span>

<span data-ttu-id="a60e3-141">*src* klasörüne geri gidin ve içinde *NewTypesTests* klasörü bulunan bir *test* klasörü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a60e3-141">Navigate back to the *src* folder and create a *test* folder with a *NewTypesTests* folder within it.</span></span> <span data-ttu-id="a60e3-142">*NewTypesTests* klasöründen bir komut `dotnet new xunit`istemi, çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a60e3-142">At a command prompt from the *NewTypesTests* folder, execute `dotnet new xunit`.</span></span> <span data-ttu-id="a60e3-143">Bu iki dosya üretir: *NewTypesTests.csproj* ve *UnitTest1.cs.*</span><span class="sxs-lookup"><span data-stu-id="a60e3-143">This produces two files: *NewTypesTests.csproj* and *UnitTest1.cs*.</span></span>

<span data-ttu-id="a60e3-144">Test projesi şu anda `NewTypes` türleri sınayamıyor ve `NewTypes` projeye bir proje başvurusu gerektiriyor.</span><span class="sxs-lookup"><span data-stu-id="a60e3-144">The test project cannot currently test the types in `NewTypes` and requires a project reference to the `NewTypes` project.</span></span> <span data-ttu-id="a60e3-145">Proje başvurusu eklemek için [`dotnet add reference`](../tools/dotnet-add-reference.md) aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="a60e3-145">To add a project reference, use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

<span data-ttu-id="a60e3-146">Veya, `<ItemGroup>` *NewTypesTests.csproj* dosyasına bir düğüm ekleyerek proje başvurularını el ile ekleme seçeneğiniz de vardır:</span><span class="sxs-lookup"><span data-stu-id="a60e3-146">Or, you also have the option of manually adding the project reference by adding an `<ItemGroup>` node to the *NewTypesTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

<span data-ttu-id="a60e3-147">*NewTypesTests.csproj*:</span><span class="sxs-lookup"><span data-stu-id="a60e3-147">*NewTypesTests.csproj*:</span></span>

[!code-xml[NewTypesTests csproj](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/test/NewTypesTests/NewTypesTests.csproj)]

<span data-ttu-id="a60e3-148">*NewTypesTests.csproj* dosyası aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="a60e3-148">The *NewTypesTests.csproj* file contains the following:</span></span>

* <span data-ttu-id="a60e3-149">Paket `Microsoft.NET.Test.Sdk`referansı , .NET test altyapısı</span><span class="sxs-lookup"><span data-stu-id="a60e3-149">Package reference to `Microsoft.NET.Test.Sdk`, the .NET testing infrastructure</span></span>
* <span data-ttu-id="a60e3-150">Paket `xunit`referansı , xUnit test çerçevesi</span><span class="sxs-lookup"><span data-stu-id="a60e3-150">Package reference to `xunit`, the xUnit testing framework</span></span>
* <span data-ttu-id="a60e3-151">Paket referans `xunit.runner.visualstudio`, test runner</span><span class="sxs-lookup"><span data-stu-id="a60e3-151">Package reference to `xunit.runner.visualstudio`, the test runner</span></span>
* <span data-ttu-id="a60e3-152">Proje başvurusu `NewTypes`, test etmek için kod</span><span class="sxs-lookup"><span data-stu-id="a60e3-152">Project reference to `NewTypes`, the code to test</span></span>

<span data-ttu-id="a60e3-153">*PetTests.cs* için *UnitTest1.cs* adını değiştirin ve dosyadaki kodu aşağıdakilerle değiştirin:</span><span class="sxs-lookup"><span data-stu-id="a60e3-153">Change the name of *UnitTest1.cs* to *PetTests.cs* and replace the code in the file with the following:</span></span>

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

<span data-ttu-id="a60e3-154">İsteğe bağlı alıştırma: `Bird` Sahibine `Tweet!` a veren bir tür daha önce *PetTests.cs* eklediyseniz, `BirdTalkToOwnerReturnsTweet`yöntemin `TalkToOwner` `Bird` tür için doğru çalışıp çalışmadığını denetlemek için PetTests.cs dosyasına bir test yöntemi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a60e3-154">Optional exercise: If you added a `Bird` type earlier that yields a `Tweet!` to the owner, add a test method to the *PetTests.cs* file, `BirdTalkToOwnerReturnsTweet`, to check that the `TalkToOwner` method works correctly for the `Bird` type.</span></span>

> [!NOTE]
> <span data-ttu-id="a60e3-155">Her ne kadar `expected` `actual` ve değerlerin eşit olmasını beklerseniz `Assert.NotEqual` de, çekle birlikte ilk iddia bu değerlerin eşit *olmadığını*belirtir.</span><span class="sxs-lookup"><span data-stu-id="a60e3-155">Although you expect that the `expected` and `actual` values are equal, an initial assertion with the `Assert.NotEqual` check specifies that these values are *not equal*.</span></span> <span data-ttu-id="a60e3-156">Her zaman başlangıçta testin mantığını denetlemek için başarısız olmak için bir test oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a60e3-156">Always initially create a test to fail in order to check the logic of the test.</span></span> <span data-ttu-id="a60e3-157">Testin başarısız olduğunu onayladıktan sonra, testin geçmesine izin verecek şekilde taslağı ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a60e3-157">After you confirm that the test fails, adjust the assertion to allow the test to pass.</span></span>

<span data-ttu-id="a60e3-158">Aşağıdaki proje yapısının tamamını gösterir:</span><span class="sxs-lookup"><span data-stu-id="a60e3-158">The following shows the complete project structure:</span></span>

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

<span data-ttu-id="a60e3-159">*Test/NewTypesTests* dizininde başlayın.</span><span class="sxs-lookup"><span data-stu-id="a60e3-159">Start in the *test/NewTypesTests* directory.</span></span> <span data-ttu-id="a60e3-160">Komutu ile test [`dotnet restore`](../tools/dotnet-restore.md) projesini geri yükleyin.</span><span class="sxs-lookup"><span data-stu-id="a60e3-160">Restore the test project with the [`dotnet restore`](../tools/dotnet-restore.md) command.</span></span> <span data-ttu-id="a60e3-161">Testleri komutla [`dotnet test`](../tools/dotnet-test.md) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a60e3-161">Run the tests with the [`dotnet test`](../tools/dotnet-test.md) command.</span></span> <span data-ttu-id="a60e3-162">Bu komut, proje dosyasında belirtilen test runner'ını başlatır.</span><span class="sxs-lookup"><span data-stu-id="a60e3-162">This command starts the test runner specified in the project file.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="a60e3-163">Beklendiği gibi, sınama başarısız olur ve konsol aşağıdaki çıktıyı görüntüler:</span><span class="sxs-lookup"><span data-stu-id="a60e3-163">As expected, testing fails, and the console displays the following output:</span></span>

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

<span data-ttu-id="a60e3-164">Testlerinizin iddialarını şu `Assert.NotEqual` `Assert.Equal`şekilde değiştirin:</span><span class="sxs-lookup"><span data-stu-id="a60e3-164">Change the assertions of your tests from `Assert.NotEqual` to `Assert.Equal`:</span></span>

[!code-csharp[PetTests class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/test/NewTypesTests/PetTests.cs)]

<span data-ttu-id="a60e3-165">Testleri `dotnet test` komutla yeniden çalıştırın ve aşağıdaki çıktıyı alın:</span><span class="sxs-lookup"><span data-stu-id="a60e3-165">Re-run the tests with the `dotnet test` command and obtain the following output:</span></span>

```output
Test run for c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\bin\Debug\netcoreapp2.1\NewTypesTests.dll(.NETCoreApp,Version=v2.1)
Microsoft (R) Test Execution Command Line Tool Version 15.8.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...

Total tests: 2. Passed: 2. Failed: 0. Skipped: 0.
Test Run Successful.
Test execution time: 1.6029 Seconds
```

<span data-ttu-id="a60e3-166">Test geçer.</span><span class="sxs-lookup"><span data-stu-id="a60e3-166">Testing passes.</span></span> <span data-ttu-id="a60e3-167">Evcil hayvan türlerinin yöntemleri, sahibiyle konuşurken doğru değerleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="a60e3-167">The pet types' methods return the correct values when talking to the owner.</span></span>

<span data-ttu-id="a60e3-168">XUnit kullanarak projeleri düzenleme ve test etme tekniklerini öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="a60e3-168">You've learned techniques for organizing and testing projects using xUnit.</span></span> <span data-ttu-id="a60e3-169">Kendi projelerinizde bunları uygulayarak bu teknikleri ile devam edin.</span><span class="sxs-lookup"><span data-stu-id="a60e3-169">Go forward with these techniques applying them in your own projects.</span></span> <span data-ttu-id="a60e3-170">*Mutlu kodlama!*</span><span class="sxs-lookup"><span data-stu-id="a60e3-170">*Happy coding!*</span></span>
