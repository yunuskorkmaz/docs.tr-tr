---
title: MacOS üzerinde .NET Core'u kullanmaya başlama
description: Bu belge, .NET Core Visual Studio kod kullanarak bir çözüm oluşturmak için iş akışı ve adımları sağlar.
keywords: .NET, .NET core, Mac, macOS, Visual Studio Code
author: bleroy
ms.author: mairaw
ms.date: 03/23/2017
ms.topic: get-started-article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 8ad82148-dac8-4b31-9128-b0e9610f4d9b
ms.workload:
- dotnetcore
ms.openlocfilehash: d130ef34961d19c450dd7142c8a5996c83465646
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="getting-started-with-net-core-on-macos"></a>MacOS üzerinde .NET Core'u kullanmaya başlama

Bu belge macOS .NET Core çözüm oluşturmak için iş akışı ve adımları sağlar. Projeleri, birim testleri oluşturma, hata ayıklama araçlarını kullanın ve üçüncü taraf kitaplıkları aracılığıyla dahil öğrenin [NuGet](https://www.nuget.org/).

> [!NOTE]
> Bu makalede kullanan [Visual Studio Code](http://code.visualstudio.com) macOS üzerinde.

## <a name="prerequisites"></a>Önkoşullar

Yükleme [.NET Core SDK](https://www.microsoft.com/net/core). .NET Core SDK .NET Core framework ve çalışma zamanı en son sürümünü içerir.

Yükleme [Visual Studio Code](http://code.visualstudio.com). Bu makalede sürecinde, Visual Studio .NET Core geliştirme geliştirmek uzantıları deneyimi kodu da yükleyin.

Visual Studio Code açarak ve tuşuna basarak Visual Studio kod C# uzantısını yüklemeniz <kbd>F1</kbd> Visual Studio Code paletini açmak için. Tür **ext yüklemek** uzantılarının listesini görmek için. C# uzantıyı seçin. Uzantıyı etkinleştirmek için Visual Studio Code yeniden başlatın. Daha fazla bilgi için bkz: [Visual Studio kod C# uzantısı belgelerine](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).

## <a name="getting-started"></a>Başlarken

Bu öğreticide, üç projeleri oluşturma: bir kitaplık projesine testleri kitaplığı proje ve bir konsol uygulaması yapar kitaplığını kullanın. Yapabilecekleriniz [görüntülemek veya kaynak indirme](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) github'da dotnet/samples deposunda Bu konu için. Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Visual Studio Code başlatın. Tuşuna <kbd>Ctrl</kbd> + <kbd> \` </kbd> (ters tırnak veya backtick karakter) ya da seçin **Görünüm > tümleşik Terminal** katıştırılmış açmak için menüden Visual Studio Code terminale. Dış bir kabuk Gezgini ile yine de açabilirsiniz **bir komut istemi açın** komutu (**içinde Terminali açın** Mac veya Linux) dışında Visual Studio Code çalışmayı tercih ederseniz.

Bir veya daha fazla .NET Core projeleri için kapsayıcı görevi gören bir çözüm dosyası oluşturarak başlayın. Terminale oluşturma bir *altın* klasörü ve klasörünü açın. Bu klasör çözümünüzü köküdür. Çalıştırma [ `dotnet new` ](../tools/dotnet-new.md) yeni bir çözüm oluşturmak için komutu *golden.sln*:

```console
dotnet new sln
```

Gelen *altın* klasörü, iki dosyalar oluşturur, bir kitaplık projesi oluşturmak için aşağıdaki komutu yürütün*library.csproj* ve *Class1.cs*, içinde*Kitaplığı* klasörü:

```console
dotnet new classlib -o library
```

Yürütme [ `dotnet sln` ](../tools/dotnet-sln.md) yeni oluşturulan eklemek için komutu *library.csproj* çözüme proje:

```console
dotnet sln add library/library.csproj
```

*Library.csproj* dosya, aşağıdaki bilgileri içerir:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard1.4</TargetFramework>
  </PropertyGroup>

</Project>
```

Bizim kitaplığı yöntemleri seri hale getirmek ve nesneleri JSON biçiminde seri durumdan. JSON seri hale getirme ve seri durumdan çıkarma desteklemek için bir başvuru ekleyin `Newtonsoft.Json` NuGet paketi. `dotnet add` Komut bir projesine yeni öğe ekler. NuGet paketine başvuru eklemek için kullanın [ `dotnet add package` ](../tools/dotnet-add-package.md) komut ve paketinin adını belirtin:

```console
dotnet add library package Newtonsoft.Json
```

Bu ekler `Newtonsoft.Json` ve bağımlılıklarını kitaplığı projesine. Alternatif olarak, el ile düzenleme *library.csproj* dosya ve aşağıdaki düğüm ekleyin:

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="10.0.1" />
</ItemGroup>
```

Yürütme [ `dotnet restore` ](../tools/dotnet-restore.md), ([nota bakın](#dotnet-restore-note)) bağımlılıkları yükler ve oluşturur bir *obj* klasöre *Kitaplığı* üç dahil olmak üzere, dosyaları bir *project.assets.json* dosyası:

```console
dotnet restore
```

İçinde *Kitaplığı* klasörü, dosyayı yeniden adlandırın *Class1.cs* için *Thing.cs*. Kod aşağıdakiyle değiştirin:

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

`Thing` Sınıfı içeren bir genel yöntem `Get`, iki toplamını numaraları ancak bunu toplamı bir dizeye dönüştürme ve tamsayı seri durumdan desteklemez döndürür. Bu kullanır modern C# özellikleri, bir dizi gibi [ `using static` yönergeleri](../../csharp/language-reference/keywords/using-static.md), [ifade bodied üyeleri](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members), ve [dize ilişkilendirme](../../csharp/language-reference/tokens/interpolated.md).

Kitaplıkla yapı [ `dotnet build` ](../tools/dotnet-build.md) komutu. Bu üreten bir *library.dll* altında dosya *golden/library/bin/Debug/netstandard1.4*:

```console
dotnet build
```

## <a name="create-the-test-project"></a>Testi projesi oluşturma

Kitaplık için bir test projesi oluşturun. Gelen *altın* klasörü, yeni bir test projesi oluşturun:

```console
dotnet new xunit -o test-library
```

Oluşturduğunuz test projesinin çözüme ekleyin:

```console
dotnet sln add test-library/test-library.csproj
```

Böylece derleyici bulmak ve kitaplığı projesi kullanın, önceki bölümde oluşturduğunuz kitaplığı proje başvurusu ekleyin. Kullanım [ `dotnet add reference` ](../tools/dotnet-add-reference.md) komutu:

```console
dotnet add test-library/test-library.csproj reference library/library.csproj
```

Alternatif olarak, el ile düzenleme *test library.csproj* dosya ve aşağıdaki düğüm ekleyin:

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

Bağımlılıkları düzgün yapılandırılmadığından, kitaplık için testleri oluşturun. Açık *UnitTest1.cs* ve içeriğini aşağıdaki kodla değiştirin:

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

Değerin 42 19 + 23 (ya da 42) eşit değil assert Not ilk oluşturduğunuzda birim testi (`Assert.NotEqual`), hangi başarısız olur. Birim testleri oluşturmanın önemli bir adım, mantığını onaylamak ilk kez başarısız test oluşturmaktır.

Gelen *altın* klasörü, aşağıdaki komutları çalıştırın:

```console
dotnet restore 
dotnet test test-library/test-library.csproj
```

Bu komutlar bağımlılıkları geri yükleme, bunları oluşturmak ve xUnit etkinleştirmek için tüm projeleri test Çalıştırıcısı testleri çalıştırmak için özyinelemeli bulma olur. Beklediğiniz gibi tek bir test başarısız olur.

Düzen *UnitTest1.cs* dosya ve gelen onaylama değiştirme `Assert.NotEqual` için `Assert.Equal`. Aşağıdaki komutu yürütün *altın* klasör bu süre geçtikten testi yeniden çalıştırmak için:

```console
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a>Konsol uygulaması oluşturma

Aşağıdaki adımlar üzerinde oluşturduğunuz konsol uygulaması bir bağımlılık kitaplığı projeye daha önce oluşturduğunuz ve çalıştırıldığında, kendi kitaplığı yöntemini çağırır alır. Bu geliştirme desenini kullanarak, birden çok proje için yeniden kullanılabilir kitaplıkları oluşturma bakın.

Yeni bir konsol uygulamasından oluşturma *altın* klasörü:

```console
dotnet new console -o app
```

Konsol uygulama projesi ekleyin:

```console
dotnet sln add app/app.csproj
```

Kitaplıkta çalıştırarak bağımlılığa yol `dotnet add reference` komutu:

```console
dotnet add app/app.csproj reference library/library.csproj
```

Çalıştırma `dotnet restore` ([bkz. Not](#dotnet-restore-note)) çözümde üç proje bağımlılıkları geri yüklemek için. Açık *Program.cs* ve içeriğini değiştirme `Main` aşağıdaki satırı yöntemiyle:

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

İki eklemek `using` üst kısmındaki yönergeleri *Program.cs* dosyası:

```csharp
using static System.Console;
using Library;
```

Aşağıdaki yürütme `dotnet run` yürütülebilir, where çalıştırılacak komutu `-p` için seçenek `dotnet run` ana uygulaması için projeyi belirtir. Uygulama "yanıt 42 olduğu" dize oluşturur.

```console
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a>Uygulamada hata ayıklama

Konumunda bir kesme noktası belirleyerek `WriteLine` deyiminde `Main` yöntemi. Her iki basarak bunu <kbd>F9</kbd> anahtar İmleç üzerinden olduğunda `WriteLine` satır veya fareyi kesme noktası ayarlamak istediğiniz sol kenar boşluğunda satırında tıklayarak. Kırmızı bir daire kod satırı kenar görünür. Kod yürütmeyi kesme ulaşıldığında durdurur *önce* kesme çizgi yürütülür.

Visual Studio Code araç çubuğunda, hata ayıklama simgesini seçerek hata ayıklayıcı sekmesini açın seçme **Görünüm > hata ayıklama** menü çubuğunda veya klavye kısayolunu kullanarak <kbd>CTRL</kbd> + <kbd> SHIFT</kbd>+<kbd>D</kbd>:

![Visual Studio Code Debugger](./media/using-on-macos/vscodedebugger.png)

Hata ayıklayıcı altında uygulamayı başlatmak için YÜRÜT düğmesine basın. Uygulama yürütme başlar ve burada durdurur kesme noktasına çalışır. Adımla `Get` yöntemi ve doğru bağımsız değişken geçirilen emin olun. Yanıt 42 olduğunu doğrulayın.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]