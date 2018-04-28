---
title: Kitaplıklarla platformu araçları arası geliştirme
description: .NET Core CLI araçlarını kullanarak .NET için kitaplıkları oluşturmayı öğrenin.
author: cartermp
ms.author: mairaw
ms.date: 05/01/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 6bdb5b11a54ce23c676d10ef6e440fa46ea12f72
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="developing-libraries-with-cross-platform-tools"></a>Kitaplıklarla platformu araçları arası geliştirme

Bu makale için platformlar arası CLI araçlarını kullanarak .NET kitaplıkları yazma alınmaktadır. CLI tüm desteklenen işletim Sistemleri arasında çalışan bir verimli ve alt düzey deneyimi sağlar. Visual Studio ile kitaplıklarını hala oluşturabilirsiniz ve bu tercih edilen deneyiminizi olursa [Visual Studio Kılavuzu'na bakın](libraries-with-vs.md).

## <a name="prerequisites"></a>Önkoşullar

Gereksinim duyduğunuz [CLI ve .NET Core SDK](https://www.microsoft.com/net/core) makinenize yüklü.

.NET Framework sürümleri bu belge postalarla bölümleri için gereksinim duyduğunuz [.NET Framework](http://getdotnet.azurewebsites.net/) bir Windows makinesinde yüklü.

Eski .NET Framework hedefleri desteklemek istiyorsanız, ek olarak, eski framework sürümlerini hedefleyen Geliştirici paketleri yüklemeniz gerekir [.NET Hedef platformlar sayfası](http://getdotnet.azurewebsites.net/target-dotnet-platforms.html). Bu tabloya bakın:

| .NET Framework Sürümü | Ne karşıdan yüklemek için                                       |
| ---------------------- | ------------------------------------------------------ |
| 4.6.1                  | .NET framework 4.6.1 hedefleme paketi                    |
| 4.6                    | .NET framework 4.6 hedefleme paketi                      |
| 4.5.2                  | .NET framework 4.5.2 Geliştirici paketi                    |
| 4.5.1                  | .NET framework 4.5.1 Geliştirici paketi                    |
| 4,5                    | Windows 8 için Windows Yazılım Geliştirme Seti         |
| 4.0                    | Windows 7 ve .NET Framework 4 için Windows SDK         |
| 2.0, 3.0 ve 3.5      | .NET framework 3.5 SP1 çalışma zamanı (veya Windows 8 + sürümü) |

## <a name="how-to-target-the-net-standard"></a>Hedef .NET standart nasıl

Standart .NET oldukça hakkında bilgi sahibi değilseniz, başvurmak [.NET standart](../../standard/net-standard.md) daha fazla bilgi için.

Bu makalede, çeşitli uygulamalar için .NET standart sürümleri eşleştiren bir tablo yok:

[!INCLUDE [net-standard-table](~/includes/net-standard-table.md)]

Bu tablo bir kitaplığı oluşturmak amacıyla anlamı şudur:

.NET, çekme standart sürümünü kolaylığını yeni API'lerine erişimi ve daha fazla .NET uygulamaları ve .NET standart sürümlerini hedefleyen olanağı arasında olacaktır. Bir sürümünü seçerek aralığını targetable platformları ve sürümleri kontrol `netstandardX.X` (burada `X.X` bir sürüm numarası) ve proje dosyanıza ekleme (`.csproj` veya `.fsproj`).

.NET standart, ihtiyaçlarınıza bağlı olarak hedeflerken üç birincil seçeneğiniz vardır.

1. .NET standart - şablonları tarafından sağlanan varsayılan sürümü kullanabilirsiniz `netstandard1.4` -e .NET standart çoğu API'leri hala UWP, .NET Framework 4.6.1 ve gelecek .NET standart 2.0 ile uyumlu devam ederken hangi erişmenizi.

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>netstandard1.4</TargetFramework>
      </PropertyGroup>
    </Project>
    ```

2. Bir veya daha küçük sürümü .NET standart değerini değiştirerek kullanabilirsiniz `TargetFramework` proje dosyanızın düğümü.
    
    Geriye dönük olarak uyumlu .NET standart sürümleri. Anlamına `netstandard1.0` kitaplıkları çalıştıracağınız `netstandard1.1` platformları ve daha yüksek. Ancak, ileriye dönük bir uyumluluk yoktur - alt .NET standart platformları yüksek olanları başvuramaz. Bunun anlamı `netstandard1.0` kitaplıkları olamaz başvuru hedefleyen kitaplıkları `netstandard1.1` ya da daha yüksek. API ve platform desteği gereksinimleriniz için doğru karışımını standart sürümü seçin. Öneririz `netstandard1.4` şimdilik.
    
3. .NET Framework sürüm 4.0 hedef istiyorsanız veya aşağıdaki veya kullanılabilir bir API kullanmak istediğiniz .NET Framework ancak .NET standart (örneğin, `System.Drawing`), aşağıdaki bölümleri okuyun ve bilgi multitarget nasıl.

## <a name="how-to-target-the-net-framework"></a>Hedef .NET Framework'ü nasıl

> [!NOTE]
> Bu yönergeler, makinenizde .NET Framework yüklü varsayalım. Başvurmak [Önkoşullar](#prerequisites) yüklü bağımlılıkları alınamıyor.

Burada kullanılan .NET Framework sürümleri bazıları artık desteği olan aklınızda bulundurun. Başvurmak [.NET Framework destek yaşam döngüsü ilkesi SSS](https://support.microsoft.com/gp/framework_faq/en-us) desteklenmeyen sürümleri hakkında.

Maksimum sayısını geliştiriciler ve projeleri erişmek isterseniz, .NET Framework 4.0 temel hedefi olarak kullanın. .NET Framework hedeflemek için desteklemek istediğiniz .NET Framework sürümüne karşılık gelen doğru hedef Framework bilinen ad (TFM) kullanarak başlayın gerekecektir.

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

Ardından bu TFM içine ekleme `TargetFramework` proje dosyanızı bölümü. Örneğin, işte .NET Framework 4.0 hedefleyen bir kitaplık nasıl yazarsınız:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

Ve bu kadar! Bu yalnızca .NET Framework 4 için derlenmiş rağmen .NET Framework'ün daha yeni sürümlerinde kitaplığını kullanabilirsiniz.

## <a name="how-to-multitarget"></a>Multitarget nasıl

> [!NOTE]
> Aşağıdaki yönergeler, makinenizde .NET Framework yüklü varsayalım. Başvurmak [Önkoşullar](#prerequisites) yüklemeniz gereken hangi bağımlılıkları ve bunları indirmek nereye öğrenmek için bölüm.

Projeniz .NET Framework ve .NET Core desteklediğinde .NET Framework'ün daha eski sürümlerini hedefleyen gerekebilir. Bu senaryoda, yeni API'ları ve dil yapıları için daha yeni hedefleri kullanmak istiyorsanız, kullanmak `#if` kodunuzda yönergeleri. Ayrıca farklı paketler ve bağımlılıklar her örneği için gereken farklı API'leri dahil etmek için hedefleme her platform için eklemeniz gerekebilir.

Örneğin, HTTP üzerinden ağ işlemlerini gerçekleştiren bir kitaplığınız varsayalım. .NET standart ve .NET Framework sürüm 4.5 veya üstü için kullanabileceğiniz `HttpClient` sınıfıyla `System.Net.Http` ad alanı. Ancak, .NET Framework'ün önceki sürümlerinde yok `HttpClient` kullanabileceğinizi nedenle `WebClient` sınıfıyla `System.Net` ad alanı olanlar için bunun yerine.

Proje dosyanızı şöyle:

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

1. `TargetFramework` Düğümü tarafından değiştirildi `TargetFrameworks`, ve üç TFMs içinde ifade edilir.
1. Var olan bir `<ItemGroup>` düğümü için `net40 ` bir .NET Framework başvurusundan çekme hedef.
1. Var olan bir `<ItemGroup>` düğümü için `net45` iki .NET Framework başvurularında çekme hedef.

Derleme Sistemi kullanılan aşağıdaki önişlemci simgelerin bilmez `#if` yönergeleri:

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

Koşullu derleme başına-hedef örnek yapmayı kullanımını şöyledir:

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
            string url = "http://www.dotnetfoundation.org/";

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
            string url = "http://www.dotnetfoundation.org/";

            // HttpClient is thread-safe, so no need to explicitly lock here
            var result = await _client.GetStringAsync(url);

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"dotnetfoundation.org mentions .NET {dotNetCount} times in its HTML!";
        }
#endif
    }
}
```

Bu proje ile yapı `dotnet build`, üç dizinlerde fark edeceksiniz `bin/` klasörü:

```
net40/
net45/
netstandard1.4/
```

Bunların her birini içeren `.dll` dosyaları her hedef için.

## <a name="how-to-test-libraries-on-net-core"></a>.NET Core üzerinde kitaplıkları test etme

Platformlar arası test edebilmek önemlidir. Kullanabilirsiniz [xUnit](http://xunit.github.io/) veya mstest'i kutuda dışında. Her ikisi de, mükemmel birim kitaplığınızı .NET Core testi için uygundur. Nasıl test projeleri çözümünüzle ayarlamanız bağlıdır [çözümünüzün yapısını](#structuring-a-solution). Aşağıdaki örnek, test ve kaynak dizinler aynı üst düzey dizinde Canlı varsayar.

> [!NOTE]
> Bu, bazı kullanır [.NET Core CLI komutları](../tools/index.md). Bkz: [dotnet yeni](../tools/dotnet-new.md) ve [dotnet sln](../tools/dotnet-sln.md) daha fazla bilgi için.

1. Çözümünüzü ayarlarken ayarlayın. Aşağıdaki komutlarla yapabilirsiniz:

   ```bash
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   Projeleri oluşturmak ve bunları bir çözümde birbirine bağlayabilirsiniz. Dizininiz için `SolutionWithSrcAndTest` aşağıdaki gibi görünmelidir:

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. Test projesinin dizinine gidin ve bir başvuru ekleyin `MyProject.Test` gelen `MyProject`.

   ```bash
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. Paketler geri ve projeleri oluşturun:

   ```bash
   dotnet restore
   dotnet build
   ```

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

1. Bu xUnit çalıştıran yürüterek doğrulayın `dotnet test` komutu. Mstest'i kullanmayı seçerseniz, mstest'i konsol Çalıştırıcısı yerine çalıştırmalısınız.
    
Ve bu kadar! Komut satırı araçlarını kullanarak tüm platformlarda kitaplığınızın artık test edebilirsiniz. Her şeyi sahip olduğunuza göre teste devam etmek için ayarlama, kitaplığınızın sınama çok basittir:

1. Değişiklikleri kitaplığınıza yapın.
1. Komut satırından test dizininize ile testleri `dotnet test` komutu.

Çağırdığınızda, kodunuzu otomatik olarak yeniden oluşturulacak `dotnet test` komutu.

## <a name="how-to-use-multiple-projects"></a>Birden çok proje kullanma

Bir ortak büyük kitaplıkları için farklı projelerde işlevselliği yerleştirmek için gerekiyor.

Kullanılan deyimsel C# ve F # içinde kullanılabilecek bir kitaplık oluşturmak istediğinizde düşünün. Bu, Tüketicileri kitaplığınızın bunları C# veya F # için doğal şekilde kullandığını anlamına gelir. Örneğin, C# dilinde, bu gibi kitaplık tüketebilir:

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

F #'ta, şuna benzeyebilir:

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

Tüketim senaryoları erişilen API'ları C# ve F # için farklı bir yapıya sahip olmanız bu ortalama ister.  Bu işlemi gerçekleştirmek için bir ortak tüm kitaplık mantığı, çekirdek projeye çağrı API katmanları tanımlama C# ve F # projeleri ile bir çekirdek projesine faktörü yaklaşımdır.  Bölümün geri kalanında aşağıdaki adları kullanır:

* **AwesomeLibrary.Core** -kitaplık için tüm mantığı içeren bir çekirdek projesi
* **AwesomeLibrary.CSharp** -C# kullanımına yönelik ortak API'ler sahip bir proje
* **AwesomeLibrary.FSharp** -F # tüketimini yönelik ortak API'ler sahip bir proje

Bu kılavuzda aynı yapısını oluşturmak üzere, terminalde aşağıdaki komutları çalıştırın:

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

Bu, yukarıdaki üç projeleri ve birbirine bağlayan bir çözüm dosyasını ekler. Çözüm dosyası oluşturma ve projeleri bağlama geri yüklemek ve bir üst düzey projelerden yapı olanak sağlar.

### <a name="project-to-project-referencing"></a>Proje projesine başvurma

Bir proje başvurusu için en iyi yolu, proje başvurusu eklemek için .NET Core CLI kullanmaktır. Gelen **AwesomeLibrary.CSharp** ve **AwesomeLibrary.FSharp** proje dizinler, aşağıdaki komutu çalıştırabilirsiniz:

```console
$ dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

Her ikisi için proje dosyalarını **AwesomeLibrary.CSharp** ve **AwesomeLibrary.FSharp** şimdi başvuru olacaktır **AwesomeLibrary.Core** olarak bir `ProjectReference` hedef.  Proje dosyalarını denetleyerek ve bunları aşağıdakileri görmesini doğrulayabilirsiniz:

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

.NET Core CLI kullanmayı tercih ederseniz, bu bölümde her proje dosyasına el ile ekleyebilirsiniz.

### <a name="structuring-a-solution"></a>Çözüm yapısı

Başka bir önemli özelliği birden çok proje çözümü, iyi bir genel proje yapı saptamaktır. Ancak, istediğiniz ve çözüm dosyanızla her proje bağlamak sürece kodu düzenleyebilirsiniz `dotnet sln add`, çalıştırmanız mümkün olacaktır `dotnet restore` ve `dotnet build` çözüm düzeyinde.
