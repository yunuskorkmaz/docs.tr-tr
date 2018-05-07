---
title: Düzenleme ve projeleri .NET Core komut satırı ile test etme
description: Bu öğretici, düzenlemek ve .NET Core projeleri komut satırından test açıklanmaktadır.
author: cartermp
ms.author: mairaw
ms.date: 05/16/2017
ms.openlocfilehash: a49eb1d398ab80a4ece703b7889083ea967df862
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="organizing-and-testing-projects-with-the-net-core-command-line"></a>Düzenleme ve projeleri .NET Core komut satırı ile test etme

Bu öğretici izleyen [Windows/Linux/macOS komut satırını kullanarak .NET Çekirdeğinde ile çalışmaya başlama](using-with-xplat-cli.md), Gelişmiş ve iyi düzenlenmiş uygulamaları geliştirmek için bir basit bir konsol uygulaması oluşturma sürüyor. Klasörleri kodunuzu düzenlemek için nasıl kullanılacağını gösteren sonra Bu öğreticide, bir konsol uygulaması ile genişletmek nasıl gösterilir [xUnit](https://xunit.github.io/) framework test etme.

## <a name="using-folders-to-organize-code"></a>Kod düzenlemek için klasörler kullanma

Bir konsol uygulaması yeni türleri tanıtmak istiyorsanız, uygulama türleri içeren dosyaları ekleyerek yapabilirsiniz. İçeren dosyaları eklerseniz, örneğin `AccountInformation` ve `MonthlyReportRecords` türleri projeniz için proje dosya yapısı düz ve kolay gezinmek:

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

Ancak, bu yalnızca iyi projenizin boyutu nispeten küçük olduğunda çalışır. Ne olacağını düşünün projeye 20 türleri eklerseniz? Proje kesinlikle gidin ve ile projenin kök dizini doldurmak birçok dosyaları korumak kolay olmayacaktır.

Proje düzenlemek için yeni bir klasör oluşturun ve adlandırın *modelleri* tür dosyalarını tutmak için. Türü dosyalarıyla yerleştirin *modelleri* klasörü:

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

Mantıksal Grup dosyaları klasörlere gidin ve bakımını kolay projeleri. Sonraki bölümde, daha karmaşık bir örnek, klasörleri ve birim testi oluşturun.

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a>Düzenleme ve NewTypes Evcil Hayvanlar örneği kullanarak test etme

### <a name="building-the-sample"></a>Örnek oluşturma

Aşağıdaki adımlar için aşağıdakilerden birini kullanarak izleyebilirsiniz [NewTypes Evcil Hayvanlar örnek](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) veya dosya ve klasörlerinizi oluşturun. Türlerinin eklenmesi daha fazla türleri daha sonra izin veren bir klasör yapısı içinde mantıksal olarak düzenlenir ve testleri mantıksal olarak da daha fazla test daha sonra eklenmesi sorgulamasına klasörlerde yerleştirilir.

İki tür örnek içeriyor `Dog` ve `Cat`ve ortak bir arabirim uygulamalarına sahip `IPet`. İçin `NewTypes` , amacınız projedir evcil hayvan ilgili türler halinde düzenlemek için bir *Evcil Hayvanlar* klasör. Başka bir dizi türlerini sonradan, eklenirse *WildAnimals* Örneğin, bunlar içinde yerleştirilir *NewTypes* yanında klasörü *Evcil Hayvanlar* klasör. *WildAnimals* klasörü Evcil Hayvanlar, gibi olmayan hayvanlar türlerinde içerebilir `Squirrel` ve `Rabbit` türleri. Bu şekilde türleri eklendikçe proje iyi düzenli olarak kalır. 

Belirtilen dosya içerikle aşağıdaki klasör yapısını oluşturun:

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

Aşağıdaki komutları çalıştırın:

```console
dotnet run
```

Aşağıdaki çıkış alın:

```console
Woof!
Meow!
```

İsteğe bağlı alıştırma: yeni bir evcil hayvan türü gibi ekleyebileceğiniz bir `Bird`, bu proje genişletme tarafından. Kuşbakışı olun `TalkToOwner` yöntemi verin bir `Tweet!` sahibine. Uygulamayı yeniden çalıştırın. Çıktıyı içerir `Tweet!`

### <a name="testing-the-sample"></a>Örnek test etme

`NewTypes` Proje yerinde olduğundan ve bir klasörde Evcil Hayvanlar ilgili türler tutarak düzenlediğiniz. Ardından, test projenizi oluşturmak ve testleri ile yazmayı başlatır [xUnit](https://xunit.github.io/) test çerçevesi. Birim testi, bunların düzgün şekilde işletim olduğunu onaylamak için evcil hayvan türlerinizi bevahior otomatik olarak denetlemenizi sağlar.

Oluşturma bir *test* klasörüyle bir *NewTypesTests* klasörde. Bir komut isteminden adresindeki *NewTypesTests* klasörü, yürütme `dotnet new xunit`. Bu iki dosyaları oluşturur: *NewTypesTests.csproj* ve *UnitTest1.cs*.

Oluşturduğunuz test projesinin şu anda türler test edilemez `NewTypes` ve proje başvurusu gerektiren `NewTypes` projesi. Proje başvurusu eklemek için kullanın [ `dotnet add reference` ](../tools/dotnet-add-reference.md) komutu:

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

* Paket referansı `Microsoft.NET.Test.Sdk`, altyapı sınama .NET
* Paket referansı `xunit`, framework sınama xUnit
* Paket referansı `xunit.runner.visualstudio`, test Çalıştırıcısı
* Proje referansı `NewTypes`, test için kodu

Adını değiştirmek *UnitTest1.cs* için *PetTests.cs* ve dosyasındaki kodu aşağıdaki ile değiştirin:

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

İsteğe bağlı alıştırma: eklediyseniz bir `Bird` verir türü daha önce bir `Tweet!` sahibi için bir test yöntemine ekleyin *PetTests.cs* dosyası `BirdTalkToOwnerReturnsTweet`, denetlemek için `TalkToOwner` yöntemi doğru çalıştığı `Bird` türü.

> [!NOTE]
> Beklediğiniz ancak `expected` ve `actual` değerleri eşit, ilk onaylama ile `Assert.NotEqual` denetimleri belirtin olduklarından emin *eşit değil*. Her zaman ilk testlerinizi testleri mantığını denetlemek için bir kez başarısız oluşturun. Bu teste dayalı tasarım (TDD) Metodoloji önemli bir adımdır. Sınama başarısız onayladıktan sonra bunları geçmesine izin vermek için onayları ayarlayın.

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

Başlangıç *test/NewTypesTests* dizini. Oluşturduğunuz test projesinin ile geri [ `dotnet restore` ](../tools/dotnet-restore.md) komutu. Testler ile [ `dotnet test` ](../tools/dotnet-test.md) komutu. Bu komut proje dosyasında belirtilen test Çalıştırıcısı başlatır.

 [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

 
Beklendiği gibi başarısız olur ve konsol sınama aşağıdaki çıkış görüntüler:
 
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

Dan testlerinizi onaylar değiştirme `Assert.NotEqual` için `Assert.Equal`:

[!code-csharp[PetTests class](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/PetTests.cs)]

Testleri yeniden çalıştırın `dotnet test` komutunu ve aşağıdaki çıkış alın:

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

Geçişleri test etme. Evcil hayvan türleri yöntemleri sahibine konuşurken doğru değerleri döndürür.

Düzenleme ve xUnit kullanarak projeleri test teknikleri öğrendiniz. Bunları kendi projelerinde uygulayarak bu teknikler ile ileri gitmektedir. *Mutluluk kodlama!*

