---
title: MacOS üzerinde .NET Core kullanmaya başlama
description: Bu belge, Visual Studio Code kullanarak bir .NET Core çözümü oluşturmak için adımlar ve iş akışı sağlar.
author: bleroy
ms.date: 03/23/2017
ms.custom: seodec18
ms.openlocfilehash: f1cb9b45c0ed1b4315361846fc065209088b57f8
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2019
ms.locfileid: "70373783"
---
# <a name="get-started-with-net-core-on-macos"></a>MacOS üzerinde .NET Core kullanmaya başlama

Bu belge, macOS için .NET Core çözümü oluşturmaya yönelik adımları ve iş akışını sağlar. Projeler, birim testleri oluşturma, hata ayıklama araçlarını kullanma ve [NuGet](https://www.nuget.org/)aracılığıyla üçüncü taraf kitaplıklarını birleştirme hakkında bilgi edinin.

> [!NOTE]
> Bu makale macOS üzerinde [Visual Studio Code](https://code.visualstudio.com) kullanır.

## <a name="prerequisites"></a>Önkoşullar

[.NET Core SDK](https://www.microsoft.com/net/core)'i yükler. .NET Core SDK .NET Core Framework ve çalışma zamanının en son sürümünü içerir.

[Visual Studio Code](https://code.visualstudio.com)'i yükler. Bu makalenin kursu sırasında, .NET Core geliştirme deneyimini geliştiren Visual Studio Code uzantıları da yüklersiniz.

Visual Studio Code açıp C# <kbd>F1</kbd> tuşuna basarak Visual Studio Code uzantısını yükleyip Visual Studio Code paleti açın. Uzantı listesini görmek için **EXT Install** yazın. C# Uzantıyı seçin. Uzantıyı etkinleştirmek için Visual Studio Code yeniden başlatın. Daha fazla bilgi için [ C# Visual Studio Code uzantısı belgelerine](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md)bakın.

## <a name="get-started"></a>Kullanmaya başlayın

Bu öğreticide, üç proje oluşturursunuz: bir kitaplık projesi, bu kitaplık projesi için testler ve kitaplığı kullanan bir konsol uygulaması. Bu konunun kaynağını GitHub 'daki DotNet/Samples deposunda [görüntüleyebilir veya indirebilirsiniz](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) . İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Visual Studio Code başlatın. Visual Studio Code ' de gömülü bir terminal açmak için <kbd>CTRL</kbd> + <kbd>\`</kbd> tuşuna basın (backquote veya backtick karakteri) veya menüden **> tümleşik Terminal görüntüle** ' yi seçin. Visual Studio Code dışında çalışmayı tercih ediyorsanız, bir dış kabuğu Explorer **komut istemi** komutunda aç (Mac veya Linux 'ta**terminalde aç** ) ile açabilirsiniz.

Bir veya daha fazla .NET Core projesi için kapsayıcı görevi gören bir çözüm dosyası oluşturarak başlayın. Terminalde bir *altın* klasör oluşturun ve klasörü açın. Bu klasör çözümünüzün köküdür. Yeni bir çözüm oluşturmak için [komutunuçalıştırın,altın.`dotnet new`](../tools/dotnet-new.md) sln:

```console
dotnet new sln
```

*Altın* *klasöründen, Kitaplık klasöründe,* *Library. csproj* ve *Class1.cs*olmak üzere iki dosya üreten bir kitaplık projesi oluşturmak için aşağıdaki komutu yürütün:

```console
dotnet new classlib -o library
```

Yeni oluşturulan *Library. csproj* projesini çözüme eklemek için [komutunuyürütün:`dotnet sln`](../tools/dotnet-sln.md)

```console
dotnet sln add library/library.csproj
```

*Library. csproj* dosyası aşağıdaki bilgileri içerir:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Kitaplık yöntemlerimiz JSON biçimindeki nesneleri serileştirmek ve serisini kaldıramıyor. JSON serileştirme ve serisini kaldırma desteklemek için `Newtonsoft.Json` NuGet paketine bir başvuru ekleyin. Komut `dotnet add` , projeye yeni öğeler ekler. Bir NuGet paketine başvuru eklemek için [`dotnet add package`](../tools/dotnet-add-package.md) komutunu kullanın ve paketin adını belirtin:

```console
dotnet add library package Newtonsoft.Json
```

Bu, `Newtonsoft.Json` ve bağımlılıklarını kitaplık projesine ekler. Alternatif olarak, *Library. csproj* dosyasını el ile düzenleyin ve aşağıdaki düğümü ekleyin:

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

[](#dotnet-restore-note) Bağımlılıkları geri yükleyen (bkz. Note) ve bir Project. varlıklar. JSON dosyası dahil olmak üzere, içinde üç dosya içeren kitaplık içinde bir obj klasörü oluşturur: [`dotnet restore`](../tools/dotnet-restore.md)

```console
dotnet restore
```

*Kitaplık* klasöründe, *Class1.cs* dosyasını *Thing.cs*olarak yeniden adlandırın. Kodu aşağıdaki kodla değiştirin:

```csharp
using static Newtonsoft.Json.JsonConvert;

namespace Library
{
    public class Thing
    {
        public int Get(int left, int right) =>
            DeserializeObject<int>($"{left + right}");
    }
}
```

Sınıfı, iki sayının toplamını döndüren, `Get`ancak toplamı bir dizeye dönüştürerek ve sonra bir tamsayıya seri durumdan çıkarmak için bir genel yöntem içerir. `Thing` Bu, C# [ `using static` yönergeler](../../csharp/language-reference/keywords/using-static.md), [ifade-Bodied Üyeler](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members)ve [dize ilişkilendirme](../../csharp/language-reference/tokens/interpolated.md)gibi birçok modern özelliği kullanır.

[`dotnet build`](../tools/dotnet-build.md) Komutuyla kitaplığı oluşturun. Bu, *altın/Library/bin/Debug/Netstandard 1.4*altında bir *Library. dll* dosyası üretir:

```console
dotnet build
```

## <a name="create-the-test-project"></a>Test projesi oluşturma

Kitaplık için bir test projesi oluşturun. *Altın* klasörden yeni bir test projesi oluşturun:

```console
dotnet new xunit -o test-library
```

Çözüme test projesi ekleyin:

```console
dotnet sln add test-library/test-library.csproj
```

Önceki bölümde oluşturduğunuz kitaplığa bir proje başvurusu ekleyerek derleyicinin kitaplık projesini bulup kullanmasını sağlayabilirsiniz. [`dotnet add reference`](../tools/dotnet-add-reference.md) Şu komutu kullanın:

```console
dotnet add test-library/test-library.csproj reference library/library.csproj
```

Alternatif olarak, *Test-Library. csproj* dosyasını el ile düzenleyin ve aşağıdaki düğümü ekleyin:

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

Bağımlılıklar düzgün şekilde yapılandırıldığına göre, kitaplığınız için testler oluşturun. *UnitTest1.cs* açın ve içeriğini şu kodla değiştirin:

```csharp
using Library;
using Xunit;

namespace TestApp
{
    public class LibraryTests
    {
        [Fact]
        public void TestThing() {
            Assert.NotEqual(42, new Thing().Get(19, 23));
        }
    }
}
```

Birim testini (`Assert.NotEqual`) ilk oluşturduğunuzda 42 değerini 19 + 23 (veya 42) olarak, başarısız olacağını unutmayın. Birim testlerini oluştururken önemli bir adım testi, öncelikle mantığını onaylamak için bir kez başarısız olacak şekilde oluşturmaktır.

*Altın* klasöründen aşağıdaki komutları yürütün:

```console
dotnet restore 
dotnet test test-library/test-library.csproj
```

Bu komutlar, bağımlılıkları geri yüklemek, onları derlemek ve testleri çalıştırmak için xUnit Test Çalıştırıcısı 'nı etkinleştirmek için tüm projeleri yinelemeli olarak bulur. Beklenen şekilde tek test başarısız olur.

*UnitTest1.cs* dosyasını düzenleyin ve onaylama `Assert.NotEqual` öğesini olarak `Assert.Equal`değiştirin. Bu saati geçen testi yeniden çalıştırmak için *altın* klasöründen aşağıdaki komutu yürütün:

```console
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a>Konsol uygulaması oluşturma

Aşağıdaki adımlar üzerinden oluşturduğunuz konsol uygulaması, daha önce oluşturduğunuz kitaplık projesine bir bağımlılık alır ve çalıştırıldığında kitaplık yöntemini çağırır. Bu geliştirme modelini kullanarak birden çok proje için yeniden kullanılabilir kitaplıklar oluşturmayı görürsünüz.

*Altın* klasöründen yeni bir konsol uygulaması oluşturun:

```console
dotnet new console -o app
```

Konsol uygulaması projesini çözüme ekleyin:

```console
dotnet sln add app/app.csproj
```

Şu `dotnet add reference` komutu çalıştırarak kitaplıkta bağımlılığı oluşturun:

```console
dotnet add app/app.csproj reference library/library.csproj
```

Çözümdeki `dotnet restore` üç projenin bağımlılıklarını geri yüklemek için çalıştırın ([bkz. Note](#dotnet-restore-note)). *Program.cs* açın ve `Main` yönteminin içeriğini aşağıdaki satırla değiştirin:

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

Program.cs dosyasının `using` en üstüne iki yönergeler ekleyin:

```csharp
using static System.Console;
using Library;
```

Yürütülebilir dosyayı çalıştırmak `dotnet run` için aşağıdaki komutu yürütün; `-p` burada `dotnet run` , ana uygulamanın projesini belirtir. Uygulama "Yanıt 42" dizesini üretir.

```console
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a>Uygulamada hata ayıklama

`WriteLine` Yöntemindeki ifadede`Main` bir kesme noktası ayarlayın. İmleç `WriteLine` çizginin üzerindeyken <kbd>F9</kbd> tuşuna basarak veya kesme noktasını ayarlamak istediğiniz satırdaki sol kenar boşluğunda fareyle tıklanarak bunu yapın. Kod satırının yanındaki kenar boşluğunda kırmızı bir daire görünür. Kesme noktasına ulaşıldığında, kesme noktası çizgisi yürütülmeden *önce* kod yürütme durur.

Visual Studio Code araç çubuğunda hata ayıklama simgesini seçerek hata ayıklayıcı sekmesini açın, menü çubuğundan **> hata ayıklamayı görüntüle** ' yi seçin ya da <kbd>CTRL</kbd>+<kbd>+ SHIFT</kbd>+' klavye kısayolunu<kbd>kullanın:</kbd>

![Visual Studio Code hata ayıklayıcı](./media/using-on-macos/visual-studio-code-debugger.png)

Uygulamayı hata ayıklayıcı altında başlatmak için Yürüt düğmesine basın. Uygulama yürütme işlemini başlatır ve kesme noktasında çalışır. `Get` Yöntemine adımlayın ve doğru bağımsız değişkenleri geçirdiğinizden emin olun. Yanıtın 42 olduğunu doğrulayın.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
