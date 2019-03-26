---
title: MacOS üzerinde .NET Core ile çalışmaya başlama
description: Bu belge, Visual Studio Code'u kullanarak bir .NET Core çözümü oluşturmak için iş akışı ve adımları sağlar.
author: bleroy
ms.date: 03/23/2017
ms.custom: seodec18
ms.openlocfilehash: e5ac6fa04a2a5001146936de56acafeec7dd895d
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409503"
---
# <a name="get-started-with-net-core-on-macos"></a>MacOS üzerinde .NET Core ile çalışmaya başlama

Bu belge, macOS için .NET Core çözüm oluşturmak için iş akışı ve adımları sağlar. Projeleri, birim testleri oluşturma, hata ayıklama araçlarını kullanın ve aracılığıyla üçüncü taraf kitaplıklarını birleştirebilir öğrenin [NuGet](https://www.nuget.org/).

> [!NOTE]
> Bu makalede [Visual Studio Code](https://code.visualstudio.com) macOS üzerinde.

## <a name="prerequisites"></a>Önkoşullar

Yükleme [.NET Core SDK'sı](https://www.microsoft.com/net/core). .NET Core SDK'sı, çalışma zamanı ve .NET Core framework en son sürümünü içerir.

Yükleme [Visual Studio Code'u](https://code.visualstudio.com). Bu makalede Kurs sırasında Visual Studio Code, .NET Core geliştirme artıran uzantıları deneyimi de yükleyin.

Visual Studio kodu açma ve basarak Visual Studio kodu C# uzantısı yükleme <kbd>F1</kbd> Visual Studio Code paletini açın. Tür **ext yükleme** uzantılarının listesini görmek için. C# uzantısı'nı seçin. Uzantıyı etkinleştirmek için Visual Studio Code'u yeniden başlatın. Daha fazla bilgi için [Visual Studio Code C# uzantısı belgeleri](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).

## <a name="get-started"></a>Kullanmaya başlayın

Bu öğreticide, üç proje oluştur: bir kitaplığı projesini test Bu kitaplık projesi ve bir konsol uygulaması yapar kitaplığını kullanın. Yapabilecekleriniz [görüntüleme veya indirme kaynağını](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) dotnet/samples deposunda github'da Bu konu. Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Visual Studio Code'u başlatın. Tuşuna <kbd>Ctrl</kbd> + <kbd> \` </kbd> (vurgulamasını belirtir ya da ters tırnak karakteri) veya **Görüntüle > tümleşik Terminalini** katıştırılmış açmak için menüden Visual Studio code'da Terminal. Dış bir kabuk ile Gezgini'nde hala açabilirsiniz **komut istemi açın** komut (**terminalde açın** Mac veya Linux), Visual Studio Code dışında çalışmayı tercih ederseniz.

Bir veya daha fazla .NET Core projeleri için kapsayıcı görevi gören bir çözüm dosyası oluşturarak başlayın. Terminalde, oluşturun bir *altın* klasörü ve klasörünü açın. Bu klasör çözümünüzü köküdür. Çalıştırma [ `dotnet new` ](../tools/dotnet-new.md) yeni bir çözüm oluşturmak için komut *golden.sln*:

```console
dotnet new sln
```

Gelen *altın* klasörü, iki dosya oluşturur, bir kitaplık projesi oluşturmak için aşağıdaki komutu yürütün*library.csproj* ve *Class1.cs*, içinde*Kitaplığı* klasörü:

```console
dotnet new classlib -o library
```

Yürütme [ `dotnet sln` ](../tools/dotnet-sln.md) yeni oluşturulan eklenecek komut *library.csproj* çözüme:

```console
dotnet sln add library/library.csproj
```

*Library.csproj* dosyası, aşağıdaki bilgileri içerir:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard1.4</TargetFramework>
  </PropertyGroup>

</Project>
```

Bizim kitaplığı yöntemleri seri hale getrime ve JSON biçimindeki nesneleri. JSON seri hale getirme ve seri durumundan çıkarma desteklemek için bir başvuru ekleyin. `Newtonsoft.Json` NuGet paketi. `dotnet add` Komutu, bir projeye yeni öğeler ekler. Bir NuGet paketine başvuru eklemek için [ `dotnet add package` ](../tools/dotnet-add-package.md) komut ve paketinin adını belirtin:

```console
dotnet add library package Newtonsoft.Json
```

Bu ekler `Newtonsoft.Json` ve bağımlılıklarını kitaplığı projesi. Alternatif olarak, el ile düzenleyebilirsiniz *library.csproj* dosyasını açıp aşağıdaki düğüm ekleyin:

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="10.0.1" />
</ItemGroup>
```

Yürütme [ `dotnet restore` ](../tools/dotnet-restore.md), ([bkz. Not](#dotnet-restore-note)) bağımlılıkları yükler ve oluşturur bir *obj* klasörün içine *Kitaplığı* üç içindeki dosyaların dahil olmak üzere bir *project.assets.json* dosyası:

```console
dotnet restore
```

İçinde *Kitaplığı* klasör, dosya yeniden adlandırma *Class1.cs* için *Thing.cs*. Kodu aşağıdakiyle değiştirin:

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

`Thing` Sınıfı içeren bir genel yöntem `Get`, iki toplamı sayı ancak toplamı bir dizeye dönüştürmek ve sonra da bir tamsayıya seri durumdan çıkarılırken yazılabilmesine döndürür. Bu kullanır modern C# özellikleri, bir dizi gibi [ `using static` yönergeleri](../../csharp/language-reference/keywords/using-static.md), [ifade gövdeli üyeler](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members), ve [dize ilişkilendirme](../../csharp/language-reference/tokens/interpolated.md).

Kitaplığı ile derleme [ `dotnet build` ](../tools/dotnet-build.md) komutu. Bu üreten bir *library.dll* altında dosya *golden/library/bin/Debug/netstandard1.4*:

```console
dotnet build
```

## <a name="create-the-test-project"></a>Test projesi oluşturma

Kitaplık için bir test projesi oluşturun. Gelen *altın* klasöründe yeni bir test projesi oluşturun:

```console
dotnet new xunit -o test-library
```

Test projesi çözüme ekleyin:

```console
dotnet sln add test-library/test-library.csproj
```

Derleyici, bulma ve kitaplık projesi kullanın önceki bölümde oluşturduğunuz kitaplık proje başvurusu ekleyin. Kullanım [ `dotnet add reference` ](../tools/dotnet-add-reference.md) komutu:

```console
dotnet add test-library/test-library.csproj reference library/library.csproj
```

Alternatif olarak, el ile düzenleyebilirsiniz *test library.csproj* dosyasını açıp aşağıdaki düğüm ekleyin:

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

Bağımlılıkları doğru şekilde yapılandırdığınızdan, yönelik testler oluşturun. Açık *UnitTest1.cs* ve içeriğini aşağıdaki kodla değiştirin:

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

' % S'değeri 42 19 + 23'ın (veya 42) eşit değil assert unutmayın ilk oluşturduğunuzda, birim testi (`Assert.NotEqual`), hangi başarısız olur. Birim testleri oluşturmanın önemli bir adım mantığını onaylamak ilk kez başarısız test oluşturmaktır.

Gelen *altın* klasöründe aşağıdaki komutları yürütün:

```console
dotnet restore 
dotnet test test-library/test-library.csproj
```

Bu komutlar bağımlılıklarını geri yükleme, bunları derlemek ve xUnit etkinleştirmek için tüm projeleri test Çalıştırıcısı testleri çalıştırmak için özyinelemeli bulma olur. Beklediğiniz gibi tek bir test başarısız olur.

Düzen *UnitTest1.cs* dosya ve onaylama gelen değiştirme `Assert.NotEqual` için `Assert.Equal`. Aşağıdaki komutu yürütün *altın* bu süre geçtikten testi yeniden çalıştırmak için klasör:

```console
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a>Konsol uygulaması oluşturma

Aşağıdaki deyime oluşturduğunuz konsol uygulaması daha önce oluşturduğunuz ve yürütüldüğünde, kitaplık yöntemini çağırır. kitaplık projesi üzerinde bir bağımlılık alır. Bu geliştirme desenini kullanarak, birden çok proje için yeniden kullanılabilir kitaplıklar oluşturma bakın.

Yeni bir konsol uygulamasından oluşturma *altın* klasörü:

```console
dotnet new console -o app
```

Konsol uygulaması projesi çözüme ekleyin:

```console
dotnet sln add app/app.csproj
```

Bağımlılık çalıştırarak kitaplık oluşturma `dotnet add reference` komutu:

```console
dotnet add app/app.csproj reference library/library.csproj
```

Çalıştırma `dotnet restore` ([bkz. Not](#dotnet-restore-note)) üç projeyi de çözümde bağımlılıklarını geri yüklemek için. Açık *Program.cs* ve içeriklerini `Main` yöntemine aşağıdaki satırı ile:

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

İki ekleme `using` yönergeleri üstüne *Program.cs* dosyası:

```csharp
using static System.Console;
using Library;
```

Aşağıdakileri yürütün `dotnet run` yürütülebilir, nerede çalıştırmak için komutu `-p` seçeneğini `dotnet run` ana uygulama için proje belirtir. Uygulama, "42 yanıttır" dizesi oluşturur.

```console
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a>Uygulamada hata ayıklama

Bir kesme noktasında ayarlamak `WriteLine` deyiminde `Main` yöntemi. Her iki basarak bunu <kbd>F9</kbd> tuşu imleci bittiğinde `WriteLine` fareyi kesme noktası ayarlamak istediğiniz satırda sol kenar boşluğunda tıklayabilir veya satır. Kenar kod satırının yanında kırmızı bir daire görünür. Kesme noktasına ulaşıldığında, yürütmeyi durdurur *önce* kesme noktası satırını yürütülür.

Visual Studio Code araç çubuğunda, hata ayıklama simgesini seçerek hata ayıklayıcı sekmesini açın seçerek **Görüntüle > hata ayıklama** menü çubuğu veya klavye kısayolunu kullanarak <kbd>CTRL</kbd> + <kbd> SHIFT</kbd>+<kbd>D</kbd>:

![Visual Studio Code hata ayıklayıcısı](./media/using-on-macos/visual-studio-code-debugger.png)

Hata ayıklayıcısı altında uygulamayı başlatmak için YÜRÜT düğmesine basın. Uygulamayı yürütmeyi başlatır ve burada durdurur kesme noktasına çalıştırır. Adımlama `Get` yöntemi ve doğru bağımsız değişken geçirilen emin olun. Yanıt 42 olduğunu doğrulayın.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]