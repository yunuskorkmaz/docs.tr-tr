---
title: "Öğretici: Visual Studio Code kullanarak macOS 'ta .NET Core çözümü oluşturma"
description: Bu belge, Visual Studio Code kullanarak bir .NET Core çözümü oluşturmak için adımlar ve iş akışı sağlar.
ms.date: 12/19/2019
ms.openlocfilehash: f5da16d413ddc25587ff35550fe9f308dc87f4bb
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156601"
---
# <a name="tutorial-create-a-net-core-solution-in-macos-using-visual-studio-code"></a>Öğretici: Visual Studio Code kullanarak macOS 'ta .NET Core çözümü oluşturma

Bu belge, macOS için .NET Core çözümü oluşturmaya yönelik adımları ve iş akışını sağlar. Projeler, birim testleri oluşturma, hata ayıklama araçlarını kullanma ve [NuGet](https://www.nuget.org/)aracılığıyla üçüncü taraf kitaplıklarını birleştirme hakkında bilgi edinin.

> [!NOTE]
> Bu makale macOS üzerinde [Visual Studio Code](https://code.visualstudio.com) kullanır.

## <a name="prerequisites"></a>Önkoşullar

[.NET Core SDK](https://dotnet.microsoft.com/download)'i yükler. .NET Core SDK .NET Core Framework ve çalışma zamanının en son sürümünü içerir.

[Visual Studio Code](https://code.visualstudio.com)'i yükler. Bu makalenin kursu sırasında, .NET Core geliştirme deneyimini geliştiren Visual Studio Code uzantıları da yüklersiniz.

Visual Studio Code açıp C# <kbd>FN</kbd>+<kbd>F1</kbd> tuşlarına basarak Visual Studio Code uzantısını yükleyip Visual Studio Code paleti açın. Uzantı listesini görmek için **EXT Install** yazın. C# Uzantıyı seçin. Uzantıyı etkinleştirmek için Visual Studio Code yeniden başlatın. Daha fazla bilgi için [ C# Visual Studio Code uzantısı belgelerine](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md)bakın.

## <a name="get-started"></a>başlarken

Bu öğreticide, üç proje oluşturursunuz: bir kitaplık projesi, bu kitaplık projesi için testler ve kitaplığı kullanan bir konsol uygulaması. Bu makalenin kaynağını GitHub 'daki DotNet/Samples deposunda [görüntüleyebilir veya indirebilirsiniz](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) . İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Visual Studio Code başlatın. Visual Studio Code yerleşik bir terminal açmak için <kbd>Ctrl</kbd> <kbd>\`</kbd> (backquote veya backtick karakteri) ya da menüden > **Terminal** **görüntüle** ' yi seçin. Visual Studio Code dışında çalışmayı tercih ediyorsanız, bir dış kabuğu, **komut istemi** komutunda aç (MacOS veya Linux 'ta**terminalde aç** ) ile açabilirsiniz.

Bir veya daha fazla .NET Core projesi için kapsayıcı görevi gören bir çözüm dosyası oluşturarak başlayın. Terminalde, *altın*adlı yeni bir klasörde *altın. sln* yeni bir çözüm oluşturmak için [`dotnet new`](../tools/dotnet-new.md) komutunu çalıştırın:

```dotnetcli
dotnet new sln -o golden
```

New *altın* klasörüne gidin ve Kitaplık klasöründe,*Library. csproj* ve *Class1.cs*olmak üzere iki dosya üreten *bir kitaplık projesi* oluşturmak için aşağıdaki komutu yürütün:

```dotnetcli
dotnet new classlib -o library
```

Yeni oluşturulan *Library. csproj* projesini çözüme eklemek için [`dotnet sln`](../tools/dotnet-sln.md) komutunu yürütün:

```dotnetcli
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

Kitaplık yöntemlerimiz JSON biçimindeki nesneleri serileştirmek ve serisini kaldıramıyor. JSON serileştirme ve serisini kaldırma desteği için `Newtonsoft.Json` NuGet paketine bir başvuru ekleyin. `dotnet add` komutu bir projeye yeni öğeler ekler. Bir NuGet paketine başvuru eklemek için, [`dotnet add package`](../tools/dotnet-add-package.md) komutunu kullanın ve paketin adını belirtin:

```dotnetcli
dotnet add library package Newtonsoft.Json
```

Bu, `Newtonsoft.Json` ve bağımlılıklarını kitaplık projesine ekler. Alternatif olarak, *Library. csproj* dosyasını el ile düzenleyin ve aşağıdaki düğümü ekleyin:

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

Bağımlılıkları geri yükleyen [`dotnet restore`](../tools/dotnet-restore.md)yürütün ([bkz. Note](#dotnet-restore-note)) ve içinde bir *Project. varlıklar. JSON* dosyası dahil olmak üzere üç dosya içeren *kitaplık* içinde bir *obj* klasörü oluşturur:

```dotnetcli
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

`Thing` sınıfı, iki sayının toplamını döndüren ve sonra toplamı bir dizeye dönüştürerek ve sonra bir tamsayı olarak seri durumdan çıkarmak için bir genel yöntem içerir, `Get`. C# Bu, [`using static` yönergeleri](../../csharp/language-reference/keywords/using-static.md), [ifade-Bodied Üyeler](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members)ve [dize ilişkilendirme](../../csharp/language-reference/tokens/interpolated.md)gibi birçok modern özelliği kullanır.

[`dotnet build`](../tools/dotnet-build.md) komutuyla kitaplığı oluşturun. Bu, *altın/Library/bin/Debug/Netstandard 1.4*altında bir *Library. dll* dosyası üretir:

```dotnetcli
dotnet build
```

## <a name="create-the-test-project"></a>Test projesi oluşturma

Kitaplık için bir test projesi oluşturun. *Altın* klasörden yeni bir test projesi oluşturun:

```dotnetcli
dotnet new xunit -o test-library
```

Çözüme test projesi ekleyin:

```dotnetcli
dotnet sln add test-library/test-library.csproj
```

Önceki bölümde oluşturduğunuz kitaplığa bir proje başvurusu ekleyerek derleyicinin kitaplık projesini bulup kullanmasını sağlayabilirsiniz. [`dotnet add reference`](../tools/dotnet-add-reference.md) komutunu kullanın:

```dotnetcli
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
        public void TestThing()
        {
            Assert.NotEqual(42, new Thing().Get(19, 23));
        }
    }
}
```

Birim testini (`Assert.NotEqual`) ilk oluşturduğunuzda 42 değerini 19 + 23 (veya 42) değerine eşit olduğunu unutmayın. Birim testlerini oluştururken önemli bir adım testi, öncelikle mantığını onaylamak için bir kez başarısız olacak şekilde oluşturmaktır.

*Altın* klasöründen aşağıdaki komutları yürütün:

```dotnetcli
dotnet restore
dotnet test test-library/test-library.csproj
```

Bu komutlar, bağımlılıkları geri yüklemek, onları derlemek ve testleri çalıştırmak için xUnit Test Çalıştırıcısı 'nı etkinleştirmek için tüm projeleri yinelemeli olarak bulur. Beklenen şekilde tek test başarısız olur.

*UnitTest1.cs* dosyasını düzenleyin ve onaylama `Assert.NotEqual` `Assert.Equal`olarak değiştirin. Bu saati geçen testi yeniden çalıştırmak için *altın* klasöründen aşağıdaki komutu yürütün:

```dotnetcli
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a>Konsol uygulaması oluşturma

Aşağıdaki adımlar üzerinden oluşturduğunuz konsol uygulaması, daha önce oluşturduğunuz kitaplık projesine bir bağımlılık alır ve çalıştırıldığında kitaplık yöntemini çağırır. Bu geliştirme modelini kullanarak birden çok proje için yeniden kullanılabilir kitaplıklar oluşturmayı görürsünüz.

*Altın* klasöründen yeni bir konsol uygulaması oluşturun:

```dotnetcli
dotnet new console -o app
```

Konsol uygulaması projesini çözüme ekleyin:

```dotnetcli
dotnet sln add app/app.csproj
```

`dotnet add reference` komutunu çalıştırarak kitaplıkta bağımlılığı oluşturun:

```dotnetcli
dotnet add app/app.csproj reference library/library.csproj
```

Çözümdeki üç projenin bağımlılıklarını geri yüklemek için `dotnet restore` ([bkz. Note](#dotnet-restore-note)) ' i çalıştırın. *Program.cs* ' i açın ve `Main` yönteminin içeriğini aşağıdaki satırla değiştirin:

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

*Program.cs* dosyasının en üstüne iki `using` yönergesi ekleyin:

```csharp
using static System.Console;
using Library;
```

Yürütülebilir dosyayı çalıştırmak için aşağıdaki `dotnet run` komutunu yürütün; burada, `dotnet run` `-p` seçeneği, ana uygulamanın projesini belirtir. Uygulama "Yanıt 42" dizesini üretir.

```dotnetcli
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a>Uygulamada hata ayıklama

`Main` yönteminde `WriteLine` bildiriminde bir kesme noktası ayarlayın. İmleç `WriteLine` çizginin üzerindeyken ya da kesme noktasını ayarlamak istediğiniz satırdaki sol kenar boşluğunda fareyle tıklanarak, <kbd>Fn</kbd>+<kbd>F9</kbd> tuşuna basarak bunu yapın. Kod satırının yanındaki kenar boşluğunda kırmızı bir daire görünür. Kesme noktasına ulaşıldığında, kesme noktası çizgisi yürütülmeden *önce* kod yürütme durur.

Visual Studio Code araç çubuğunda hata ayıklama simgesini seçerek hata ayıklayıcı sekmesini açın, menü çubuğundan >  **hata ayıklamayı** görüntüle ' yi seçin veya <kbd>&#8679;</kbd> <kbd>&#8984;</kbd> <kbd>klavye kısayolunu kullanın</kbd>:

![Visual Studio Code hata ayıklayıcı](./media/using-on-macos/visual-studio-code-debugger.png)

Uygulamayı hata ayıklayıcı altında başlatmak için Yürüt düğmesine basın. Bu projede hem bir test projesi hem de bir uygulama oluşturdunuz. Hata ayıklayıcı hangi projeyi başlatmak istediğinizi sorar. "Uygulama" projesini seçin. Uygulama yürütme işlemini başlatır ve kesme noktasında çalışır. `Get` yöntemine adımla ve doğru bağımsız değişkenleri geçirdiğinizden emin olun. Yanıtın 42 olduğunu doğrulayın.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
