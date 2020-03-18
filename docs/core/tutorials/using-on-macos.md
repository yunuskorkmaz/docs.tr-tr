---
title: "Öğretici: Visual Studio Code kullanarak macOS'ta bir .NET Core çözümü oluşturun"
description: Bu belge, Visual Studio Code kullanarak bir .NET Core Solution oluşturmak için adımlar ve iş akışı sağlar.
ms.date: 12/19/2019
ms.openlocfilehash: f5da16d413ddc25587ff35550fe9f308dc87f4bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156601"
---
# <a name="tutorial-create-a-net-core-solution-in-macos-using-visual-studio-code"></a>Öğretici: Visual Studio Code kullanarak macOS'ta bir .NET Core çözümü oluşturun

Bu belge, macOS için bir .NET Core çözümü oluşturmak için adımları ve iş akışını sağlar. [NuGet](https://www.nuget.org/)aracılığıyla proje oluşturmayı, birim testleri yapmayı, hata ayıklama araçlarını nasıl kullanacağınızı ve üçüncü taraf kitaplıklarını nasıl birleştirerek nasıl kullanacağınızı öğrenin.

> [!NOTE]
> Bu makalede, macOS'ta [Visual Studio Kodu](https://code.visualstudio.com) kullanılır.

## <a name="prerequisites"></a>Önkoşullar

[.NET Çekirdek SDK'yı](https://dotnet.microsoft.com/download)yükleyin. .NET Core SDK, .NET Core çerçevesinin ve çalışma zamanının en son sürümüne yer verilmiştir.

[Visual Studio Kodunu](https://code.visualstudio.com)Yükleyin. Bu makale nin seyri sırasında,.NET Core geliştirme deneyimini geliştiren Visual Studio Code uzantılarını da yüklersiniz.

Visual Studio Code Kodunu açarak ve Visual Studio Code paletini açmak için <kbd>Fn</kbd>+<kbd>F1</kbd> tuşuna basarak Visual Studio Code C# uzantısını yükleyin. Uzantıların listesini görmek için **ext yükleme** yazın. C# uzantısını seçin. Uzantıyı etkinleştirmek için Visual Studio Code'u yeniden başlatın. Daha fazla bilgi için [Visual Studio Code C# Extension belgelerine](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md)bakın.

## <a name="get-started"></a>Başlarken

Bu öğreticide, üç proje oluşturursunuz: bir kitaplık projesi, kitaplık projesi için testler ve kitaplığı kullanan bir konsol uygulaması. Bu [makalenin kaynağını](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) GitHub'daki dotnet/samples deposundan görüntüleyebilir veya indirebilirsiniz. İndirme talimatları için [Örnekler ve Öğreticiler'e](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)bakın.

Visual Studio Code'u başlatın. Visual Studio Code'da gömülü bir terminal açmak için <kbd>Ctrl</kbd> <kbd>\`</kbd> 'ye (backquote veya backtick karakteri) basın veya menüden**Terminali** **Görüntüle'yi** > seçin. Visual Studio Code dışında çalışmayı tercih ederseniz Explorer **Open in Command Prompt** komutu (macOS veya**Linux'ta Terminal'de açık)** ile harici bir kabuk açabilirsiniz.

Bir veya daha fazla .NET Core projesi için kapsayıcı görevi gören bir çözüm dosyası oluşturarak başlayın. Terminalde, golden [`dotnet new`](../tools/dotnet-new.md) adlı yeni bir klasör içinde yeni bir çözüm *golden* *golden.sln* oluşturmak için komutu çalıştırın:

```dotnetcli
dotnet new sln -o golden
```

Kitaplık klasöründe*library.csproj* ve *Class1.cs*olmak üzere iki dosya üreten bir kitaplık projesi *library* oluşturmak için yeni *altın* klasöre gidin ve aşağıdaki komutu çalıştırın:

```dotnetcli
dotnet new classlib -o library
```

Yeni [`dotnet sln`](../tools/dotnet-sln.md) oluşturulan *library.csproj* projesini çözüme eklemek için komutu uygulayın:

```dotnetcli
dotnet sln add library/library.csproj
```

*Library.csproj* dosyası aşağıdaki bilgileri içerir:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Kitaplık yöntemlerimiz json formatında nesneleri seri hale ve deserialize eder. JSON serileştirme ve deserialization desteklemek için `Newtonsoft.Json` NuGet paketine bir başvuru ekleyin. Komut, `dotnet add` projeye yeni öğeler ekler. NuGet paketine başvuru eklemek için [`dotnet add package`](../tools/dotnet-add-package.md) komutu kullanın ve paketin adını belirtin:

```dotnetcli
dotnet add library package Newtonsoft.Json
```

Bu, `Newtonsoft.Json` kitaplık projesine bağımlılıkları ve bağımlılıklarını ekler. Alternatif olarak, *library.csproj* dosyasını el ile edin ve aşağıdaki düğümü ekleyin:

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

Bağımlılıkları geri [`dotnet restore`](../tools/dotnet-restore.md)yükleyen ve içinde *project.assets.json* dosyası da dahil olmak üzere üç dosya içeren *kitaplık* içinde bir *obj* klasörü oluşturan Yürütme , ([bkz.](#dotnet-restore-note)

```dotnetcli
dotnet restore
```

*Kitaplık* klasöründe, dosyayı *Class1.cs* *Thing.cs'* e yeniden adlandırın. Kodu aşağıdakilerle değiştirin:

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

Sınıf, `Thing` iki sayının `Get`toplamını döndüren, ancak toplamı bir dize dönüştürüp sonra bir tamsayıya dönüştürerek bunu yapan bir ortak yöntem içerir. Bu, [ `using static` yönergeler,](../../csharp/language-reference/keywords/using-static.md) [ifade gövdeli üyeler](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members)ve [dize enterpolasyonu](../../csharp/language-reference/tokens/interpolated.md)gibi bir dizi modern C# özelliğinden yararlanır.

[`dotnet build`](../tools/dotnet-build.md) Komutla kitaplığı oluşturun. Bu *altın/kütüphane/bin/Debug/netstandard1.4*altında bir *library.dll* dosyası oluşturur:

```dotnetcli
dotnet build
```

## <a name="create-the-test-project"></a>Test projesini oluşturma

Kitaplık için bir test projesi oluşturun. *Altın* klasörden yeni bir test projesi oluşturun:

```dotnetcli
dotnet new xunit -o test-library
```

Test projesini çözüme ekleyin:

```dotnetcli
dotnet sln add test-library/test-library.csproj
```

Derleyicinin kitaplık projesini bulup kullanabilmesi için önceki bölümde oluşturduğunuz kitaplık bir proje başvurusu ekleyin. Komutu [`dotnet add reference`](../tools/dotnet-add-reference.md) kullanın:

```dotnetcli
dotnet add test-library/test-library.csproj reference library/library.csproj
```

Alternatif olarak, *test-library.csproj* dosyasını el ile edin ve aşağıdaki düğümü ekleyin:

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

Bağımlılıklar düzgün şekilde yapılandırıldığına göre, kitaplığınız için testleri oluşturun. *UnitTest1.cs* açın ve içeriğini aşağıdaki kodla değiştirin:

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

42 değerinin 19+23 'e (veya 42)'ye eşit olmadığını, birim`Assert.NotEqual`testini ilk oluşturduğunuzda (veya 42) başarısız olacağını unutmayın. Birim testleri oluşturmada önemli bir adım, testin mantığını doğrulamak için ilk önce başarısız olmasını sağlamaktır.

*Altın* klasörden aşağıdaki komutları uygulayın:

```dotnetcli
dotnet restore
dotnet test test-library/test-library.csproj
```

Bu komutlar, bağımlılıkları geri yüklemek, bunları oluşturmak ve testleri çalıştırmak için xUnit test koşucusunu etkinleştirmek için tüm projeleri özyinelemeli olarak bulur. Beklediğiniz gibi, tek bir test başarısız olur.

*UnitTest1.cs* dosyasını edin ve `Assert.NotEqual` iddiayı ' dan ' a `Assert.Equal`değiştirin Bu kez geçen testi yeniden çalıştırmak için *altın* klasörden aşağıdaki komutu çalıştırın:

```dotnetcli
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a>Konsol uygulamasını oluşturma

Aşağıdaki adımlar da oluşturduğunuz konsol uygulaması, daha önce oluşturduğunuz kitaplık projesine bağımlı hale getirir ve çalıştığında kitaplık yöntemini çağırır. Bu geliştirme modelini kullanarak, birden çok proje için yeniden kullanılabilir kitaplıklar oluşturmanın nasıl olduğunu görürsünüz.

*Altın* klasörden yeni bir konsol uygulaması oluşturun:

```dotnetcli
dotnet new console -o app
```

Konsol uygulaması projesini çözüme ekleyin:

```dotnetcli
dotnet sln add app/app.csproj
```

`dotnet add reference` Komutu çalıştırarak kitaplığa bağımlılık oluşturun:

```dotnetcli
dotnet add app/app.csproj reference library/library.csproj
```

Çözümdeki üç projenin bağımlılıklarını geri yüklemek için çalıştırın `dotnet restore` ([bkz. nota bakınız).](#dotnet-restore-note) *Program.cs* açın ve yöntemin `Main` içeriğini aşağıdaki satırla değiştirin:

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

Program.cs `using` dosyasının üst bölümüne *Program.cs* iki yönerge ekleyin:

```csharp
using static System.Console;
using Library;
```

Ana uygulama `dotnet run` için projeyi `-p` belirtebilme `dotnet run` seçeneğinin bulunduğu, yürütülebilir'i çalıştırmak için aşağıdaki komutu çalıştırın. Uygulama "Yanıt 42"dir dizesini üretir.

```dotnetcli
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a>Uygulamada hata ayıklama

`Main` Yöntemdeki deyimde `WriteLine` bir kesme noktası ayarlayın. İmleç `WriteLine` çizginin üzerindeyken <kbd>Fn</kbd>+<kbd>F9</kbd> tuşuna basarak veya kesme noktasını ayarlamak istediğiniz çizginin sol kenar boşluğundaki fareyi tıklatarak bunu yapın. Kod satırının yanındaki kenar boşluğunda kırmızı bir daire görüntülenir. Kesme noktasına ulaşıldığında, kesme noktası satırı yürütülmeden *önce* kod yürütme durdurulur.

Visual Studio Code araç çubuğundaki Hata Ayıklama simgesini seçerek, menü çubuğundan**Hata Ayıklama'yı** **Görüntüle'yi** > seçerek veya klavye kısayolu <kbd>&#8679;</kbd> <kbd>D</kbd> <kbd>&#8984;</kbd>kullanarak hata ayıklama sekmesini açın:

![Görsel Stüdyo Kodu Debugger](./media/using-on-macos/visual-studio-code-debugger.png)

Hata ayıklamanın altındaki uygulamayı başlatmak için Oynat düğmesine basın. Bu projede hem bir test projesi hem de bir uygulama oluşturdunuz. Hata ayıklayan hangi projeyi başlatmak istediğinizi sorar. "Uygulama" projesini seçin. Uygulama yürütmeye başlar ve kesme noktasına kadar çalışır ve burada durur. Yönteme `Get` adım atın ve doğru bağımsız değişkenleri geçtiğinden emin olun. Cevabın 42 olduğunu doğrulayın.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
