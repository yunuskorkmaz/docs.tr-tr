---
title: .NET CLı ile projeleri düzenleme ve test etme
description: Bu öğreticide, komut satırından .NET projelerinin nasıl düzenlenmesi ve test yapılacağı açıklanmaktadır.
author: cartermp
ms.date: 09/10/2018
ms.openlocfilehash: c668cff48a2418cc1bc34aef78ea26c863d9de6a
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872684"
---
# <a name="organizing-and-testing-projects-with-the-net-cli"></a>.NET CLı ile projeleri düzenleme ve test etme

Bu öğretici [öğretici: Visual Studio Code kullanarak .NET ile bir konsol uygulaması oluşturma](with-visual-studio-code.md), gelişmiş ve iyi düzenlenmiş uygulamalar geliştirmeye yönelik basit bir konsol uygulaması oluşturmayı aşarak. Kodunuzu düzenlemek için klasörleri nasıl kullanacağınızı gösterdikten sonra, bu öğreticide [xUnit](https://xunit.net/) test çerçevesiyle bir konsol uygulamasını nasıl genişletebileceğinizi gösterir.

## <a name="using-folders-to-organize-code"></a>Kodu düzenlemek için klasörleri kullanma

Konsol uygulamasına yeni türler eklemek istiyorsanız, türleri uygulamaya içeren dosyaları ekleyerek bunu yapabilirsiniz. Örneğin `AccountInformation` , projenize ve türlerini içeren dosyaları eklerseniz `MonthlyReportRecords` , proje dosya yapısı düz ve gezinmek kolaydır:

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

Ancak, bu yalnızca projenizin boyutu nispeten küçük olduğunda iyi bir şekilde geçerlidir. Projeye 20 tür eklerseniz ne olacağını anlaz edebilir misiniz? Projenin, bu birçok dosya üzerinde gezinilmesi ve projenin kök dizinini oluşturma konusunda kesinlikle kolay olması gerekmez.

Projeyi düzenlemek için yeni bir klasör oluşturun ve bunu tür dosyalarını tutacak şekilde *modelleyen* şekilde adlandırın. Tür dosyalarını *modeller* klasörüne yerleştirin:

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

Dosyaları klasörlere mantıksal olarak gruplandıran projeler arasında gezinmek ve bakım yapmak kolaydır. Sonraki bölümde, klasörler ve birim testi ile daha karmaşık bir örnek oluşturursunuz.

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a>NewTypes pets örneğini kullanarak düzenleme ve test etme

### <a name="prerequisites"></a>Önkoşullar

* [.Net 5,0 SDK](https://dotnet.microsoft.com/download) veya sonraki bir sürümü.

### <a name="building-the-sample"></a>Örnek oluşturma

Aşağıdaki adımlar için, [Newtypes pets örneğini](https://github.com/dotnet/samples/tree/main/core/console-apps/NewTypesMsBuild) kullanarak takip edebilir veya kendi dosya ve klasörlerinizi oluşturabilirsiniz. Türler, daha sonra daha fazla türden eklenmesine izin veren bir klasör yapısına mantıksal olarak düzenlenir ve testler daha sonra daha fazla test eklenmesine izin veren klasörlere de mantıksal olarak yerleştirilir.

Örnek iki tür içerir ve ve `Dog` `Cat` , ortak bir arabirim uygular `IPet` . Projeniz için `NewTypes` amacınız, Evcil hayvan ile ilgili türleri bir *pets* klasörü olarak düzenmaktır. Daha sonra başka bir tür kümesi eklenirse, *WildAnimals* Örneğin, *pets* klasörüyle birlikte *newtypes* klasörüne yerleştirilirler. *WildAnimals* klasörü, ve türleri gibi pets olmayan hayvanlar için türler içerebilir `Squirrel` `Rabbit` . Bu şekilde, türler eklendikçe, proje iyi organize edilmiş kalır.

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

*Ipet. cs*:

[!code-csharp[IPet interface](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/IPet.cs)]

*Köpek. cs*:

[!code-csharp[Dog class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/Dog.cs)]

*Kedi. cs*:

[!code-csharp[Cat class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/Cat.cs)]

*Program. cs*:

[!code-csharp[Main](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Program.cs)]

*Newtypes. csproj*:

[!code-xml[NewTypes csproj](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/NewTypes.csproj)]

Aşağıdaki komutu yürütün:

```dotnetcli
dotnet run
```

Aşağıdaki çıktıyı alın:

```console
Woof!
Meow!
```

İsteğe bağlı alıştırma: `Bird` Bu projeyi genişleterek, gibi yeni bir evcil hayvan türü ekleyebilirsiniz. Kuşın `TalkToOwner` yönteminin sahibine vermesini sağlayın `Tweet!` . Uygulamayı tekrar çalıştırın. Çıktıda şunlar yer alır `Tweet!`

### <a name="testing-the-sample"></a>Örneği test etme

`NewTypes`Proje yerinde ve pets ile ilgili türleri bir klasörde tutarak düzenlemiş olursunuz. Ardından, test projenizi oluşturun ve [xUnit](https://xunit.net/) test çerçevesi ile testleri yazmaya başlayın. Birim testi, sorunsuz şekilde çalıştığının nasıl yapılacağını onaylamak için evcil hayvan türlerinizi davranışını otomatik olarak denetlemenizi sağlar.

*Src* klasörüne geri gidin ve Içinde *newtypestests* klasörünü içeren bir *Test* klasörü oluşturun. *Newtypestests* klasöründen bir komut isteminde yürütün `dotnet new xunit` . Bu iki dosya üretir: *Newtypestests. csproj* ve *UnitTest1. cs*.

Test projesi şu anda içindeki türleri test edemez `NewTypes` ve projeye bir proje başvurusu gerektiriyor `NewTypes` . Bir proje başvurusu eklemek için [`dotnet add reference`](../tools/dotnet-add-reference.md) komutunu kullanın:

```dotnetcli
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

Ya da `<ItemGroup>` *Newtypestests. csproj* dosyasına bir düğüm ekleyerek proje başvurusunu el ile ekleme seçeneğiniz de vardır:

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

*Newtypestests. csproj*:

[!code-xml[NewTypesTests csproj](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/test/NewTypesTests/NewTypesTests.csproj)]

*Newtypestests. csproj* dosyası şunları içerir:

* `Microsoft.NET.Test.Sdk`.Net test altyapısına paket başvurusu
* Paket başvurusu `xunit` , xUnit test çerçevesi
* Test Çalıştırıcısı 'na paket başvurusu `xunit.runner.visualstudio`
* Proje başvurusu `NewTypes` , sınanacak kod

*UnitTest1. cs* adını *pettests. cs* olarak değiştirin ve dosyadaki kodu aşağıdaki kodla değiştirin:

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

İsteğe bağlı alıştırma: `Bird` daha önce sahibine veren bir tür eklediyseniz, `Tweet!` yöntemin tür için doğru çalışıp çalışmadığını denetlemek Için *pettests. cs* dosyasına bir test yöntemi ekleyin `BirdTalkToOwnerReturnsTweet` `TalkToOwner` `Bird` .

> [!NOTE]
> Ve değerlerinin eşit olmasını bekleseniz de, `expected` `actual` Check ile bir ilk onaylama, `Assert.NotEqual` Bu değerlerin *eşit* olmadığını belirtir. Testin mantığını denetlemek için her zaman ilk olarak bir test oluşturun. Testin başarısız olduğunu doğruladıktan sonra, testi geçirmeye izin verecek şekilde ayarlayın.

Aşağıda, tüm proje yapısı gösterilmektedir:

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

*Test/NewTypesTests* dizininde başlatın. Komutu ile testleri çalıştırın [`dotnet test`](../tools/dotnet-test.md) . Bu komut, proje dosyasında belirtilen Test Çalıştırıcısı 'nı başlatır.

Beklenen şekilde test başarısız olur ve konsolu aşağıdaki çıktıyı görüntüler:

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

Testlerinizin onaylamalarını şu `Assert.NotEqual` şekilde değiştirin `Assert.Equal` :

[!code-csharp[PetTests class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/test/NewTypesTests/PetTests.cs)]

Komutu ile testleri yeniden çalıştırın `dotnet test` ve aşağıdaki çıktıyı alın:

```output
Test run for C:\Source\dotnet\docs\samples\snippets\core\tutorials\testing-with-cli\csharp\test\NewTypesTests\bin\Debug\net5.0\NewTypesTests.dll (.NETCoreApp,Version=v5.0)
Microsoft (R) Test Execution Command Line Tool Version 16.8.1
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
A total of 1 test files matched the specified pattern.

Passed!  - Failed:     0, Passed:     2, Skipped:     0, Total:     2, Duration: 2 ms - NewTypesTests.dll (net5.0)
```

Test geçişleri. Evcil hayvan türleri ' yöntemleri, sahibiyle konuşurken doğru değerleri döndürür.

XUnit kullanarak projeleri düzenleme ve test etme tekniklerini öğrendiniz. Bunları kendi projelerinize uygulayarak bu tekniklerle ileri gidin. *Kodlarım kutlu olsun!*
