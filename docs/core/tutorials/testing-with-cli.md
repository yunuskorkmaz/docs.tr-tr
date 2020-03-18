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
# <a name="organizing-and-testing-projects-with-the-net-core-cli"></a>.NET Core CLI ile projelerin düzenlenmesi ve test edilmesi

Bu öğretici, gelişmiş ve iyi organize edilmiş uygulamalar geliştirmek için basit bir konsol uygulaması oluşturmanın ötesine geçerek [komut satırını kullanarak Windows/Linux/macOS'ta .NET Core ile başlayın.](cli-create-console-app.md) Kodunuzu düzenlemek için klasörleri nasıl kullanacağınızı gösterdikten sonra, bu öğretici, [xUnit](https://xunit.github.io/) test çerçevesi ile bir konsol uygulamasını nasıl genişletisiniz gösterir.

## <a name="using-folders-to-organize-code"></a>Kodu düzenlemek için klasörleri kullanma

Bir konsol uygulamasına yeni türler eklemek istiyorsanız, bunu uygulamaya türleri içeren dosyalar ekleyerek yapabilirsiniz. Örneğin, projenize dosya `AccountInformation` `MonthlyReportRecords` içeren dosyalar ve türler eklerseniz, proje dosyası yapısı düz dür ve gezinmesi kolaydır:

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

Ancak, bu yalnızca projenizin boyutu nispeten küçük olduğunda iyi çalışır. Projeye 20 çeşit eklerseniz neler olacağını hayal edebiliyor musunuz? Proje kesinlikle gezinmek ve projenin kök dizini çöp bu kadar çok dosya ile korumak kolay olmaz.

Projeyi düzenlemek için yeni bir klasör oluşturun ve tür dosyalarını tutmak için *modellere* ad vereb.' Tür dosyalarını *Modeller* klasörüne yerleştirin:

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

Dosyaları mantıksal olarak klasörlere gruplandıran projelerde gezinmek ve bakımı kolaydır. Sonraki bölümde, klasörler ve birim sınayıile daha karmaşık bir örnek oluşturursunuz.

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a>NewTypes Evcil Hayvan Örneği'ni kullanarak düzenleme ve test etme

### <a name="building-the-sample"></a>Örneği oluşturma

Aşağıdaki adımlar için, [NewTypes Evcil Hayvanlar Örneği'ni](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) kullanarak takip edebilir veya kendi dosya ve klasörlerinizi oluşturabilirsiniz. Türler mantıksal olarak daha sonra daha fazla tür eklenmesine izin veren bir klasör yapısına düzenlenir ve testler daha sonra daha fazla test eklenmesine izin veren klasörlere de mantıksal olarak yerleştirilir.

Örnek iki tür `Dog` içerir `Cat`ve , ve onları `IPet`ortak bir arayüz uygulamak vardır. Proje `NewTypes` için amacınız evcil hayvan ile ilgili türleri Evcil *Hayvanlar* klasöründe düzenlemektir. Daha sonra başka bir tür kümesi eklenirse, örneğin *WildAnimals,* *Evcil Hayvanlar* klasörünün yanında *NewTypes* klasörüne yerleştirilir. *WildAnimals* klasörü, evcil hayvan olmayan hayvanlar için `Squirrel` türler `Rabbit` içerebilir. Bu şekilde türleri eklendikçe, proje iyi organize olmaya devam eder.

Belirtilen dosya içeriğiyle aşağıdaki klasör yapısını oluşturun:

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

[!code-csharp[IPet interface](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/IPet.cs)]

*Dog.cs*:

[!code-csharp[Dog class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/Dog.cs)]

*Cat.cs*:

[!code-csharp[Cat class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/Cat.cs)]

*Program.cs*:

[!code-csharp[Main](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Program.cs)]

*NewTypes.csproj*:

[!code-xml[NewTypes csproj](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/NewTypes.csproj)]

Aşağıdaki komutu yürütün:

```dotnetcli
dotnet run
```

Aşağıdaki çıktıyı edinin:

```console
Woof!
Meow!
```

İsteğe bağlı egzersiz: Bu projeyi genişleterek yeni bir `Bird`evcil hayvan türü ekleyebilirsiniz. Kuşun `TalkToOwner` yöntemi sahibine bir `Tweet!` vermek olun. Uygulamayı tekrar çalıştırın. Çıktı,`Tweet!`

### <a name="testing-the-sample"></a>Numuneyi test etme

Proje `NewTypes` yerindedir ve evcil hayvanlarla ilgili türleri bir klasörde tutarak düzenlediniz. Ardından, test projenizi oluşturun ve [xUnit](https://xunit.github.io/) test çerçevesi ile testler yazmaya başlayın. Birim testi, evcil hayvan tiplerinizin düzgün çalıştığını doğrulamak için evcil hayvan tiplerinizin davranışını otomatik olarak kontrol etmenizi sağlar.

*src* klasörüne geri gidin ve içinde *NewTypesTests* klasörü bulunan bir *test* klasörü oluşturun. *NewTypesTests* klasöründen bir komut `dotnet new xunit`istemi, çalıştırın. Bu iki dosya üretir: *NewTypesTests.csproj* ve *UnitTest1.cs.*

Test projesi şu anda `NewTypes` türleri sınayamıyor ve `NewTypes` projeye bir proje başvurusu gerektiriyor. Proje başvurusu eklemek için [`dotnet add reference`](../tools/dotnet-add-reference.md) aşağıdaki komutu kullanın:

```dotnetcli
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

Veya, `<ItemGroup>` *NewTypesTests.csproj* dosyasına bir düğüm ekleyerek proje başvurularını el ile ekleme seçeneğiniz de vardır:

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

*NewTypesTests.csproj*:

[!code-xml[NewTypesTests csproj](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/test/NewTypesTests/NewTypesTests.csproj)]

*NewTypesTests.csproj* dosyası aşağıdakileri içerir:

* Paket `Microsoft.NET.Test.Sdk`referansı , .NET test altyapısı
* Paket `xunit`referansı , xUnit test çerçevesi
* Paket referans `xunit.runner.visualstudio`, test runner
* Proje başvurusu `NewTypes`, test etmek için kod

*PetTests.cs* için *UnitTest1.cs* adını değiştirin ve dosyadaki kodu aşağıdakilerle değiştirin:

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

İsteğe bağlı alıştırma: `Bird` Sahibine `Tweet!` a veren bir tür daha önce *PetTests.cs* eklediyseniz, `BirdTalkToOwnerReturnsTweet`yöntemin `TalkToOwner` `Bird` tür için doğru çalışıp çalışmadığını denetlemek için PetTests.cs dosyasına bir test yöntemi ekleyin.

> [!NOTE]
> Her ne kadar `expected` `actual` ve değerlerin eşit olmasını beklerseniz `Assert.NotEqual` de, çekle birlikte ilk iddia bu değerlerin eşit *olmadığını*belirtir. Her zaman başlangıçta testin mantığını denetlemek için başarısız olmak için bir test oluşturun. Testin başarısız olduğunu onayladıktan sonra, testin geçmesine izin verecek şekilde taslağı ayarlayın.

Aşağıdaki proje yapısının tamamını gösterir:

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

*Test/NewTypesTests* dizininde başlayın. Komutu ile test [`dotnet restore`](../tools/dotnet-restore.md) projesini geri yükleyin. Testleri komutla [`dotnet test`](../tools/dotnet-test.md) çalıştırın. Bu komut, proje dosyasında belirtilen test runner'ını başlatır.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Beklendiği gibi, sınama başarısız olur ve konsol aşağıdaki çıktıyı görüntüler:

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

Testlerinizin iddialarını şu `Assert.NotEqual` `Assert.Equal`şekilde değiştirin:

[!code-csharp[PetTests class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/test/NewTypesTests/PetTests.cs)]

Testleri `dotnet test` komutla yeniden çalıştırın ve aşağıdaki çıktıyı alın:

```output
Test run for c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\bin\Debug\netcoreapp2.1\NewTypesTests.dll(.NETCoreApp,Version=v2.1)
Microsoft (R) Test Execution Command Line Tool Version 15.8.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...

Total tests: 2. Passed: 2. Failed: 0. Skipped: 0.
Test Run Successful.
Test execution time: 1.6029 Seconds
```

Test geçer. Evcil hayvan türlerinin yöntemleri, sahibiyle konuşurken doğru değerleri döndürür.

XUnit kullanarak projeleri düzenleme ve test etme tekniklerini öğrendiniz. Kendi projelerinizde bunları uygulayarak bu teknikleri ile devam edin. *Mutlu kodlama!*
