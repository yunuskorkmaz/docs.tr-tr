---
title: Düzenleme ve .NET Core komut satırı ile projeleri test etme
description: Bu öğreticide, düzenlemek ve test komut satırından .NET Core projeleri açıklanmaktadır.
author: cartermp
ms.author: mairaw
ms.date: 05/16/2017
ms.openlocfilehash: 5fdbdc115ea5cd6da54f7c43bec2aa6f82e71310
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43400289"
---
# <a name="organizing-and-testing-projects-with-the-net-core-command-line"></a>Düzenleme ve .NET Core komut satırı ile projeleri test etme

Bu öğreticide aşağıdaki [Windows/Linus/macos'ta komut satırını kullanarak .NET Core ile çalışmaya başlama](using-with-xplat-cli.md), Gelişmiş ve iyi düzenlenmiş uygulamalar geliştirmek için basit bir konsol uygulaması oluşturmayı sürüyor. Kodunuzu düzenlemek için klasörleri kullanmayı gösteren sonra Bu öğreticide, bir konsol uygulaması ile nasıl genişletileceğini gösterir [xUnit](https://xunit.github.io/) testi çerçevesi.

## <a name="using-folders-to-organize-code"></a>Kod düzenlemek için klasörleri'ni kullanarak

Bir konsol uygulamasına yeni türlerini tanıtır istiyorsanız, bunu uygulama türlerini içeren dosyaları ekleyerek yapabilirsiniz. Örneğin dosyaları içeren eklediğiniz `AccountInformation` ve `MonthlyReportRecords` türleri projeniz için proje dosya yapısı düz ve kolay gidin:

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

Ancak, bu yalnızca iyi projenizin boyutu nispeten küçük olduğunda çalışır. Ne olacağını düşünün projeye 20 türleri eklerseniz? Proje kesinlikle gidin ve ile çok sayıda dosya projenin kök dizinini doldurmak korumak kolay değildir.

Proje düzenlemek için yeni bir klasör oluşturun ve adlandırın *modelleri* tür dosyalarını tutacak. Türü dosyaları içine yerleştirebilir *modelleri* klasörü:

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

Mantıksal olarak klasörlere Grup dosyaları gidin ve korumak kolay projeleri. Sonraki bölümde, klasör ve birim testi ile daha karmaşık bir örnek oluşturun.

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a>Düzenleme ve NewTypes Evcil Hayvanlar örneğini kullanarak test etme

### <a name="building-the-sample"></a>Örnek oluşturma

Aşağıdaki adımları için aşağıdakilerden birini kullanarak izleyebilirsiniz [NewTypes Evcil Hayvanlar örnek](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) veya dosya ve klasörlerinizi oluşturun. Testler ayrıca mantıksal olarak klasörlere daha sonra ayrıca daha fazla test sorgulamasına yerleştirilir ve türlerini mantıksal olarak daha fazla türlerinin eklenmesi daha sonra izin veren bir klasör yapısına düzenlenir.

İki tür örnek içeren `Dog` ve `Cat`ve bunları ortak bir arabirim uygulamak `IPet`. İçin `NewTypes` amacınız projesidir evcil hayvan ilgili tür olarak düzenlemek için bir *Evcil Hayvanlar* klasör. Daha sonra başka bir dizi türleri eklenirse *WildAnimals* bunlar, örneğin, yerleştirilir *NewTypes* klasör yanı sıra *Evcil Hayvanlar* klasör. *WildAnimals* klasör hayvanlar gibi olmayan hayvanlar türleri içerebilir `Squirrel` ve `Rabbit` türleri. Bu şekilde türleri eklendikçe proje de düzenli olarak kalır. 

Aşağıdaki klasör yapısını, belirtilen dosya içeriği oluşturun:

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

*IPet.cs*:

[!code-csharp[IPet interface](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/IPet.cs)]

*Dog.cs*:

[!code-csharp[Dog class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Dog.cs)]

*Cat.cs*:

[!code-csharp[Cat class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Cat.cs)]

*Program.cs*:

[!code-csharp[Main](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Program.cs)]

*NewTypes.csproj*:

[!code-xml[NewTypes csproj](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/NewTypes.csproj)]

Aşağıdaki komutları yürütün:

```console
dotnet run
```

Aşağıdaki çıktıyı alın:

```console
Woof!
Meow!
```

İsteğe bağlı alıştırma: yeni bir evcil hayvan türü gibi ekleyebilirsiniz bir `Bird`, bu proje genişleterek. Kuşbakışı olun `TalkToOwner` yöntemi verin bir `Tweet!` sahibine. Uygulamayı yeniden çalıştırın. Çıkış içerir `Tweet!`

### <a name="testing-the-sample"></a>Örnek test etme

`NewTypes` Proje yerinde olduğundan ve bir klasörde Evcil Hayvanlar ilgili türleri tutarak düzenlediğiniz. Ardından, test projenizi oluşturmak ve testleri yazmaya [xUnit](https://xunit.github.io/) test çerçevesi. Birim testi, otomatik olarak bunlar düzgün şekilde çalıştıklarından olduğunu onaylamak için evcil hayvan türlerinin bevahior denetlemek sağlar.

Oluşturma bir *test* klasörüyle bir *NewTypesTests* içindeki klasör. Bir komut istemi'nden en *NewTypesTests* klasöründe yürütme `dotnet new xunit`. Bu iki dosya oluşturur: *NewTypesTests.csproj* ve *UnitTest1.cs*.

Test projesi türleri şu anda test edilemez `NewTypes` ve bir proje başvurusu gerektirir `NewTypes` proje. Bir proje başvurusu eklemek için [ `dotnet add reference` ](../tools/dotnet-add-reference.md) komutu:

```
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

El ile ekleyerek proje başvurusu ekleme seçeneğiniz de bir `<ItemGroup>` düğüme *NewTypesTests.csproj* dosyası:

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

*NewTypesTests.csproj*:

[!code-xml[NewTypesTests csproj](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/NewTypesTests.csproj)]

*NewTypesTests.csproj* dosyası şunları içerir:

* Başvuru paketi `Microsoft.NET.Test.Sdk`, altyapı test .NET
* Başvuru paketi `xunit`, xUnit testi çerçevesi
* Başvuru paketi `xunit.runner.visualstudio`, test Çalıştırıcısı
* Proje başvurusu `NewTypes`, kodu test etmek için

Adını değiştirmek *UnitTest1.cs* için *PetTests.cs* dosyasındaki kodu aşağıdakiyle değiştirin:

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

İsteğe bağlı alıştırma: eklediyseniz bir `Bird` verir türü daha önce bir `Tweet!` sahibine bir test yöntemine ekleyin *PetTests.cs* dosyası `BirdTalkToOwnerReturnsTweet`denetlemek için `TalkToOwner` yöntemi doğru çalıştığı `Bird` türü.

> [!NOTE]
> Beklediğiniz ancak `expected` ve `actual` değerler eşit olan ilk onaylama `Assert.NotEqual` denetimini, bu değerler olduğunu belirtir *eşit değil*. Her zaman başlangıçta test mantığını denetlemek için başarısız bir test oluşturun. Testin başarısız olduğunu onayladıktan sonra onaylama test geçmesine izin verecek şekilde ayarlayın.

Tam proje yapısını gösterir:

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

Başlangıç *test/NewTypesTests* dizin. Test projesi ile geri [ `dotnet restore` ](../tools/dotnet-restore.md) komutu. Testler ile [ `dotnet test` ](../tools/dotnet-test.md) komutu. Bu komut, proje dosyasında belirtilen test Çalıştırıcısı başlatır.

 [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

 
Test başarısız olur ve konsolu, beklendiği gibi aşağıdaki çıkışı görüntüler:
 
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

Testlerinizin onaylamaları değiştirme `Assert.NotEqual` için `Assert.Equal`:

[!code-csharp[PetTests class](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/PetTests.cs)]

Testleri yeniden çalıştırın `dotnet test` komutunu ve aşağıdaki çıktıyı alın:

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

Geçiş testi. Evcil hayvan türleri yöntemleri, sahibi konuşurken doğru değerleri döndürür.

Düzenleme ve xUnit kullanarak projeleri test teknikleri öğrendiniz. Bunları kendi projelerinde uygulayarak bu teknikler ile ileri gidin. *İyi Kodlamalar!*

