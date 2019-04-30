---
title: Platformlar arası araçlarla kitaplıkları ile geliştirme
description: .NET Core CLI araçları ile .NET Core kitaplıkları oluşturmayı öğrenin. Birden çok çerçevelerini destekleyen bir kitaplık oluşturmayı öğreneceksiniz.
author: cartermp
ms.date: 05/01/2017
ms.custom: seodec18
ms.openlocfilehash: 9dd1d8477f8e34e79ff521463972e26a21ad1dfd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61647339"
---
# <a name="developing-libraries-with-cross-platform-tools"></a>Platformlar arası araçlarla kitaplıkları ile geliştirme

Bu makale için platformlar arası CLI araçları ile .NET kitaplıkları yazma kapsar. CLI'yı tüm desteklenen işletim Sistemleri üzerinde çalışan bir verimli ve alt düzey deneyimi sağlar. Visual Studio ile kitaplıkları yine de oluşturabilir ve bu tercih edilen deneyiminiz olduğu [Visual Studio Kılavuzu'na bakın](libraries-with-vs.md).

## <a name="prerequisites"></a>Önkoşullar

Gereksinim duyduğunuz [CLI ve .NET Core SDK'sı](https://www.microsoft.com/net/core) makinenizde yüklü.

Bu belge uğraşmanızı .NET Framework sürümleri için bölümlere gereksinim [.NET Framework](https://dotnet.microsoft.com) bir Windows makinede yüklü.

Eski .NET Framework hedefleri desteklemek isterseniz, ayrıca, daha eski framework sürümlerini hedefleme Geliştirici paketleri yüklemeniz gerekir [.NET indirme sayfası arşivleri](https://dotnet.microsoft.com/download/archives). Bu tabloya bakın:

| .NET Framework Sürümü | Ne yüklemek için                                       |
| ---------------------- | ------------------------------------------------------ |
| 4.6.1                  | .NET framework 4.6.1 Targeting Pack                    |
| 4.6                    | .NET framework 4.6 Targeting Pack                      |
| 4.5.2                  | .NET framework 4.5.2 Geliştirici paketi                    |
| 4.5.1                  | .NET framework 4.5.1 Geliştirici paketi                    |
| 4,5                    | Windows 8 için Windows Yazılım Geliştirme Seti         |
| 4.0                    | Windows Windows 7 ve .NET Framework 4 için SDK'sı         |
| 2.0, 3.0 ve 3.5      | .NET framework 3.5 SP1 çalışma zamanı (veya Windows 8 + sürümü) |

## <a name="how-to-target-the-net-standard"></a>Hedef .NET Standard hakkında

.NET Standard ile oldukça bilgi sahibi değilseniz başvurmak [.NET Standard](../../standard/net-standard.md) daha fazla bilgi için.

Bu makalede, çeşitli uygulamalar için .NET Standard sürümleri eşleyen bir tablo vardır:

[!INCLUDE [net-standard-table](../../../includes/net-standard-table.md)]

Bu tabloda bir kitaplık oluşturmak amacıyla anlamı aşağıda verilmiştir:

Bu sürümü .NET standart, çekme en yeni API'ler için erişim ve daha fazla .NET uygulamaları ve .NET Standard sürümlerini hedefleme olanağınız arasında bir denge olacaktır. Bir sürümünü seçerek hedeflenebilir platformlara ve sürümlere aralığı kontrol `netstandardX.X` (burada `X.X` bir sürüm numarası) ve proje dosyanıza ekleyerek (`.csproj` veya `.fsproj`).

.NET Standard, ihtiyaçlarınıza bağlı olarak hedeflenirken üç birincil seçeneğiniz vardır.

1. .NET standart - şablonları tarafından sağlanan varsayılan sürümünü kullanabilirsiniz `netstandard1.4` -.NET standart, çoğu API'ları için hala UWP, .NET Framework 4.6.1 ve gelecek .NET Standard 2.0 ile uyumlu olmanın yanı sıra hangi erişmenizi.

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>netstandard1.4</TargetFramework>
      </PropertyGroup>
    </Project>
    ```

2. .NET Standard'ın daha düşük veya üzeri bir sürüm değeri değiştirerek kullanabilirsiniz `TargetFramework` proje dosyanızın düğümü.

    .NET standard sürümleri geriye dönük olarak uyumludur. Bu anlamına `netstandard1.0` kitaplıkları çalıştıracağınız `netstandard1.1` platformları ve daha yüksek. Ancak, hiçbir ileriye dönük bir uyumluluk yoktur - daha düşük bir .NET Standard platformları daha yüksek olanları başvuramaz. Diğer bir deyişle `netstandard1.0` kitaplıkları olamaz başvuru hedefleyen kitaplıkları `netstandard1.1` veya üzeri. API ve platform desteğiyle gereksinimleriniz için doğru karışımını standart sürümü seçin. Öneririz `netstandard1.4` şimdilik.

3. .NET Framework sürüm 4.0 hedeflemek istiyorsanız veya aşağıdaki veya kullanılabilir bir API kullanmak istediğiniz .NET Framework ancak .NET Standard (örneğin, `System.Drawing`), aşağıdaki bölümleri okuyun ve öğrenin multitarget nasıl.

## <a name="how-to-target-the-net-framework"></a>.NET Framework'ü hedefleyen nasıl

> [!NOTE]
> Bu yönergeler, makinenizde .NET Framework yüklü varsayar. Başvurmak [önkoşulları](#prerequisites) yüklü bağımlılıkları almak için.

Bazı burada kullanılan .NET Framework sürümleri artık desteği olan aklınızda bulundurun. Başvurmak [.NET Framework desteği yaşam döngüsü ilkesi SSS](https://support.microsoft.com/gp/framework_faq/en-us) desteklenmeyen sürümleri hakkında.

Geliştiriciler ve projelerle sayısı ulaşmak istiyorsanız, .NET Framework 4.0, temel hedefi olarak kullanın. .NET Framework'ü hedeflemek için desteklemek istediğiniz .NET Framework sürümüne karşılık gelen doğru hedef çerçeve adı (TFM) kullanarak başlarsanız gerekecektir.

```
.NET Framework 2.0   --> net20
.NET Framework 3.0   --> net30
.NET Framework 3.5   --> net35
.NET Framework 4.0   --> net40
.NET Framework 4.5   --> net45
.NET Framework 4.5.1 --> net451
.NET Framework 4.5.2 --> net452
.NET Framework 4.6   --> net46
.NET Framework 4.6.1 --> net461
.NET Framework 4.6.2 --> net462
.NET Framework 4.7   --> net47
```

Ardından bu TFM içine Ekle `TargetFramework` proje dosyanızın bölümü. Örneğin, işte .NET Framework 4.0 hedefleyen bir kitaplığı nasıl yazmalısınız:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

Ve İşte bu kadar! Bu yalnızca .NET Framework 4 için derlenmiş olsa da, .NET Framework'ün daha yeni sürümlerinde kitaplığını kullanabilirsiniz.

## <a name="how-to-multitarget"></a>Nasıl yapılır Multitarget

> [!NOTE]
> Aşağıdaki yönergeler, .NET Framework'ün makinenizde yüklü olduğu varsayılır. Başvurmak [önkoşulları](#prerequisites) bölümü hangi bağımlılıkları yüklemeniz gerekir ve bunları nereden öğrenin.

.NET Framework ve .NET Core projenizi destekliyorsa, .NET Framework'ün eski sürümlerini hedefleyen gerekebilir. Yeni API'ler ve dil yapıları yeni hedeflerini kullanmak istiyorsanız, bu senaryoda kullanma `#if` kodunuzda yönergeleri. Farklı bir paket ve bağımlılıkların her çalışması için gereken farklı API'leri dahil etmek için hedeflediğiniz her platform için eklemeniz gerekebilir.

Örneğin, HTTP üzerinden ağ işlemleri gerçekleştiren bir kitaplığınız varsayalım. .NET Standard ve .NET Framework sürüm 4.5 veya üstü için kullanabileceğiniz `HttpClient` gelen sınıfı `System.Net.Http` ad alanı. Ancak, .NET Framework'ün önceki sürümlerini yok `HttpClient` kullanabilirsiniz, böylece sınıf `WebClient` gelen sınıfı `System.Net` ad alanı olanlar için bunun yerine.

Proje dosyanız şöyle görünebilir:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>

  <!-- Need to conditionally bring in references for the .NET Framework 4.0 target -->
  <ItemGroup Condition="'$(TargetFramework)' == 'net40'">
    <Reference Include="System.Net" />
  </ItemGroup>

  <!-- Need to conditionally bring in references for the .NET Framework 4.5 target -->
  <ItemGroup Condition="'$(TargetFramework)' == 'net45'">
    <Reference Include="System.Net.Http" />
    <Reference Include="System.Threading.Tasks" />
  </ItemGroup>
</Project>
```

Burada üç önemli değişiklikler fark edeceksiniz:

1. `TargetFramework` Düğümü tarafından değiştirilmiştir `TargetFrameworks`, ve üç Tfm'ler içindeki ifade edilir.
1. Var olan bir `<ItemGroup>` düğümü için `net40` hedef bir .NET Framework başvuru çekmek.
1. Var olan bir `<ItemGroup>` düğümü için `net45` iki .NET Framework başvurularını çekme hedef.

Derleme Sistemi kullanılan aşağıdaki önişlemci sembolleri farkında `#if` yönergeleri:

[!INCLUDE [Preprocessor symbols](../../../includes/preprocessor-symbols.md)]

Koşullu derleme başına-hedef örnek yapmayı kullanımını aşağıda verilmiştir:

```csharp
using System;
using System.Text.RegularExpressions;
#if NET40
// This only compiles for the .NET Framework 4 targets
using System.Net;
#else
 // This compiles for all other targets
using System.Net.Http;
using System.Threading.Tasks;
#endif

namespace MultitargetLib
{
    public class Library
    {
#if NET40
        private readonly WebClient _client = new WebClient();
        private readonly object _locker = new object();
#else
        private readonly HttpClient _client = new HttpClient();
#endif

#if NET40
        // .NET Framework 4.0 does not have async/await
        public string GetDotNetCount()
        {
            string url = "https://www.dotnetfoundation.org/";

            var uri = new Uri(url);

            string result = "";

            // Lock here to provide thread-safety.
            lock(_locker)
            {
                result = _client.DownloadString(uri);
            }

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"Dotnet Foundation mentions .NET {dotNetCount} times!";
        }
#else
        // .NET 4.5+ can use async/await!
        public async Task<string> GetDotNetCountAsync()
        {
            string url = "https://www.dotnetfoundation.org/";

            // HttpClient is thread-safe, so no need to explicitly lock here
            var result = await _client.GetStringAsync(url);

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"dotnetfoundation.org mentions .NET {dotNetCount} times in its HTML!";
        }
#endif
    }
}
```

Bu proje ile derleme yaparsanız `dotnet build`, üç dizin altında fark edeceksiniz `bin/` klasörü:

```
net40/
net45/
netstandard1.4/
```

Her birini içeren `.dll` her hedef için dosyaları.

## <a name="how-to-test-libraries-on-net-core"></a>.NET Core üzerinde kitaplıkları test etme

Platformlar arasında test edebilmek önemlidir. Kullanabilirsiniz [xUnit](https://xunit.github.io/) veya MSTest hazır. Her ikisi de, tam birim testi .NET Core kitaplığınızı için uygundur. Nasıl çözümünüzü test projeleriyle ayarlayabilirsiniz bağlı olacaktır [çözümünüzün yapısını](#structuring-a-solution). Aşağıdaki örnek, test ve kaynak dizinleri aynı üst düzey dizininde Canlı varsayar.

> [!NOTE]
> Bu bazı kullanır [.NET Core CLI komutları](../tools/index.md). Bkz: [yeni dotnet](../tools/dotnet-new.md) ve [dotnet sln](../tools/dotnet-sln.md) daha fazla bilgi için.

1. Çözümünüzü ayarlayın. Bunu aşağıdaki komutlarla yapabilirsiniz:

   ```bash
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   Projeleri oluşturmak ve bunları bir çözümde birbirine bağlayabilirsiniz. Dizininiz için `SolutionWithSrcAndTest` şöyle görünmelidir:

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. Test projesinin dizine gidin ve bir başvuru ekleyin `MyProject.Test` gelen `MyProject`.

   ```bash
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. Paketleri geri yükle ve projelerinizi oluşturun:

   ```bash
   dotnet restore
   dotnet build
   ```

   [!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

1. Bu xUnit çalıştığını yürüterek doğrulama `dotnet test` komutu. MSTest kullanmayı seçerseniz, MSTest konsol Çalıştırıcısı yerine çalıştırmalısınız.

Ve İşte bu kadar! Artık kitaplığınızı komut satırı araçlarını kullanarak tüm platformlarda test edebilirsiniz. Artık her şeyi sahip olduğunuza göre teste devam etmek için ayarlama, kitaplığınıza test çok basittir:

1. Kitaplığınıza değişiklikler yapın.
1. Komut satırından test dizininizde ile testler `dotnet test` komutu.

Çağırdığınızda, kodunuzu otomatik olarak yeniden derlenecek `dotnet test` komutu.

## <a name="how-to-use-multiple-projects"></a>Birden çok proje kullanma

Daha büyük kitaplıkları için ortak bir gereksinimi, farklı projelerde işlevselliği yerleştirmektir.

İçinde kullanılan deyimsel tüketilebilecek kitaplık oluşturmak, onlardan Imagine C# ve F#. Anlamına kitaplığınızı kullanan Tüketiciler, bunları olduğu için doğal bir şekilde kullandığını C# veya F#. Örneğin, C# Kitaplığı gibi bu tükettiğiniz:

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

İçinde F#, şuna benzeyebilir:

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

Erişilen API'leri için farklı bir yapıya sahip olması bu anlama gelir gibi tüketim senaryolar C# ve F#.  Tüm kitaplık mantığı ile bir çekirdek projeye etkimesi için bu işlemi gerçekleştirmek için yaygın bir yaklaşım olan C# ve F# API tanımlama projeleri Katmanlar bu çağrı, core projesi.  Bölümün geri kalanında, aşağıdaki adlarını kullanır:

* **AwesomeLibrary.Core** -kitaplığının tüm mantığı içeren bir temel proje
* **AwesomeLibrary.CSharp** -C# tüketim yönelik ortak API'ler ile bir proje
* **AwesomeLibrary.FSharp** -ortak sahip bir proje tüketimini API'leri yönelikF#

Bu kılavuzda aynı yapısını oluşturmak için terminalde aşağıdaki komutları çalıştırabilirsiniz:

```console
mkdir AwesomeLibrary && cd AwesomeLibrary
dotnet new sln
mkdir AwesomeLibrary.Core && cd AwesomeLibrary.Core && dotnet new classlib
cd ..
mkdir AwesomeLibrary.CSharp && cd AwesomeLibrary.CSharp && dotnet new classlib
cd ..
mkdir AwesomeLibrary.FSharp && cd AwesomeLibrary.FSharp && dotnet new classlib -lang F#
cd ..
dotnet sln add AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
dotnet sln add AwesomeLibrary.CSharp/AwesomeLibrary.CSharp.csproj
dotnet sln add AwesomeLibrary.FSharp/AwesomeLibrary.FSharp.fsproj
```

Bu, yukarıdaki üç projeleri ve bunları birbirine bağlayan bir çözüm dosyası ekler. Çözüm dosyası oluşturma ve bağlama projeleri geri yükleme ve en üst düzey bir proje oluşturmak sağlayacak.

### <a name="project-to-project-referencing"></a>Projeden projeye başvuru

Bir proje başvurusu için en iyi yolu, bir proje başvurusu eklemek için .NET Core CLI kullanmaktır. Gelen **AwesomeLibrary.CSharp** ve **AwesomeLibrary.FSharp** proje dizinleri, aşağıdaki komutu çalıştırabilirsiniz:

```console
dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

Her ikisi için proje dosyaları **AwesomeLibrary.CSharp** ve **AwesomeLibrary.FSharp** artık başvuru olacak **AwesomeLibrary.Core** olarak bir `ProjectReference` hedef.  Proje dosyalarını incelemek ve bunları aşağıdaki görmeye doğrulayabilirsiniz:

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

.NET Core CLI'yı kullanmayı tercih ederseniz bu bölümde her proje dosyasına el ile ekleyebilirsiniz.

### <a name="structuring-a-solution"></a>Bir çözüm yapılandırma

Birden çok proje çözümü başka bir önemli yönüyle iyi bir genel proje yapısı oluşturabilirsiniz. Ancak, istediğiniz ve her proje, Çözüm dosyasıyla bağlantı sürece kod düzenleyebilirsiniz `dotnet sln add`, çalıştırmak mümkün olacaktır `dotnet restore` ve `dotnet build` çözüm düzeyinde.
