---
title: .NET Core CLI ile Kitaplıklar geliştirin
description: .NET Core CLI kullanarak .NET Core kitaplıkları oluşturmayı öğrenin. Çoklu çerçeveleri destekleyen bir kitaplık oluşturacaksınız.
author: cartermp
ms.topic: how-to
ms.date: 05/01/2017
ms.openlocfilehash: 7aadaf7bf7819d52a57c3a137beff46d924d8cb0
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396210"
---
# <a name="develop-libraries-with-the-net-core-cli"></a>.NET Core CLI ile Kitaplıklar geliştirin

Bu makalede, .NET Core CLI kullanarak .NET için kitaplıkların nasıl yazılacağı ele alınmaktadır. CLı, desteklenen tüm işletim sistemlerinde çalışacak etkili ve düşük düzeyde bir deneyim sağlar. Visual Studio ile Kitaplıklar oluşturmaya devam edebilirsiniz ve tercih ettiğiniz deneyim [Visual Studio kılavuzuna başvurur](library-with-visual-studio.md).

## <a name="prerequisites"></a>Ön koşullar

Makinenizde yüklü [.NET Core SDK ve CLI](https://dotnet.microsoft.com/download) olması gerekir.

Bu belgenin .NET Framework sürümleriyle ilgili bölümlerinde, bir Windows makinesine [.NET Framework](https://dotnet.microsoft.com) yüklenmesi gerekir.

Ayrıca, eski .NET Framework hedeflerini desteklemek istiyorsanız, [.net indirme arşivleri sayfasından](https://dotnet.microsoft.com/download/archives)hedefleme paketlerini veya geliştirici paketlerini yüklemeniz gerekir. Bu tabloya başvurun:

| .NET Framework sürümü | İndirileceği                                       |
| ---------------------- | ------------------------------------------------------ |
| 4.6.1                  | .NET Framework 4.6.1 hedefleme paketi                    |
| 4.6                    | .NET Framework 4,6 hedefleme paketi                      |
| 4.5.2                  | .NET Framework 4.5.2 Geliştirici paketi                    |
| 4.5.1                  | .NET Framework 4.5.1 Geliştirici paketi                    |
| 4,5                    | Windows 8 için Windows Yazılım Geliştirme Seti         |
| 4.0                    | Windows 7 ve .NET Framework 4 için Windows SDK         |
| 2,0, 3,0 ve 3,5      | .NET Framework 3,5 SP1 çalışma zamanı (veya Windows 8 + sürüm) |

## <a name="how-to-target-the-net-standard"></a>.NET Standard nasıl hedeflenecek

.NET Standard hakkında bilginiz yoksa daha fazla bilgi edinmek için [.NET Standard](../../standard/net-standard.md) başvurun.

Bu makalede, .NET Standard sürümlerini çeşitli uygulamalarla eşleyen bir tablo vardır:

[!INCLUDE [net-standard-table](../../../includes/net-standard-table.md)]

Bu tabloda kitaplık oluşturma amaçları için ne olacağı açıklanmaktadır:

Seçtiğiniz .NET Standard sürümü, en yeni API 'lere erişim ve daha fazla .NET uygulaması ve .NET Standard sürümlerini hedefleyebilme arasında bir zorunluluğunu getirir olacaktır. Bir sürümünü `netstandardX.X` ( `X.X` sürüm numarası) seçerek ve proje dosyanıza (veya) ekleyerek hedeflenebilir platformlarının ve sürümlerinin aralığını kontrol edersiniz `.csproj` `.fsproj` .

Gereksinimlerinize bağlı olarak .NET Standard hedeflemek için üç birincil seçeneğiniz vardır.

1. `netstandard1.4`.NET Standard ' de UWP, .NET Framework 4.6.1 ve .NET Standard 2,0 ile uyumlu olmaya devam ederken birçok API 'ye erişmenizi sağlayan şablonlar tarafından sağlanan .NET Standard varsayılan sürümünü kullanabilirsiniz.

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>netstandard1.4</TargetFramework>
      </PropertyGroup>
    </Project>
    ```

2. .NET Standard daha düşük veya daha yüksek bir sürümünü, `TargetFramework` proje dosyanızın düğümündeki değeri değiştirerek kullanabilirsiniz.

    .NET Standard sürümler geriye dönük olarak uyumludur. Bu, `netstandard1.0` kitaplıkların `netstandard1.1` platformlar ve daha yükseği üzerinde çalıştığı anlamına gelir. Ancak, ileri bir uyumluluk yoktur. Daha düşük .NET Standard platformlar daha fazla başvuramaz. Bu, `netstandard1.0` kitaplıkların, veya üzeri kitaplıklara başvurmayacağı anlamına gelir `netstandard1.1` . Gereksinimlerinize uygun API 'lerin ve platform desteğinin doğru karışımına sahip standart sürümü seçin. Şimdilik önerilir `netstandard1.4` .

3. .NET Framework sürümleri 4,0 veya sonraki bir sürümü hedeflemek istiyorsanız veya .NET Framework ' de kullanılabilir ancak .NET Standard (örneğin,) bir API kullanmak istiyorsanız, `System.Drawing` aşağıdaki bölümleri okuyun ve çoklu hedef hakkında bilgi edinin.

## <a name="how-to-target-net-framework"></a>Nasıl hedeflenecek .NET Framework

> [!NOTE]
> Bu yönergeler makinenizde .NET Framework yüklü olduğunu varsayar. Bağımlılıkları yüklemek için [önkoşulları](#prerequisites) inceleyin.

Burada kullanılan .NET Framework sürümlerinden bazılarının artık desteklenmediğini aklınızda bulundurun. Desteklenmeyen sürümler hakkında [sss .NET Framework destek yaşam döngüsü ilkesi hakkında SSS](https://support.microsoft.com/gp/framework_faq/en-us) bölümüne bakın.

En fazla geliştirici ve proje sayısına ulaşmak isterseniz, taban çizgisi hedefi olarak .NET Framework 4,0 kullanın. .NET Framework hedeflemek için, desteklemek istediğiniz .NET Framework sürümüne karşılık gelen doğru hedef Framework bilinen adını (tfd) kullanarak başlayın.

| .NET Framework sürümü | TFM      |
| ---------------------- | -------- |
| .NET Framework 2.0     | `net20`  |
| .NET Framework 3.0     | `net30`  |
| .NET Framework 3.5     | `net35`  |
| .NET Framework 4.0     | `net40`  |
| .NET Framework 4.5     | `net45`  |
| .NET Framework 4.5.1   | `net451` |
| .NET Framework 4.5.2   | `net452` |
| .NET Framework 4.6     | `net46`  |
| .NET Framework 4.6.1   | `net461` |
| .NET Framework 4.6.2   | `net462` |
|  .NET Framework 4.7     | `net47`  |
|  .NET Framework 4.8     | `net48`  |

Daha sonra bu tfd 'yi `TargetFramework` proje dosyanızın bölümüne eklersiniz. Örneğin, .NET Framework 4,0 ' i hedefleyen bir kitaplığı nasıl yazacağınız aşağıda verilmiştir:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

Hepsi bu! Bu yalnızca .NET Framework 4 için derlense de, kitaplığı .NET Framework daha yeni sürümlerinde kullanabilirsiniz.

## <a name="how-to-multitarget"></a>Çoklu hedef

> [!NOTE]
> Aşağıdaki yönergelerde .NET Framework makinenizde yüklü olduğunu varsaymaktadır. Yüklemeniz gereken bağımlılıkları ve bunların nereden indirileceği hakkında bilgi edinmek için [Önkoşullar](#prerequisites) bölümüne bakın.

Projeniz hem .NET Framework hem de .NET Core ' u desteklediğinde, .NET Framework eski sürümlerini hedefleyebilirsiniz. Bu senaryoda, daha yeni hedefler için daha yeni API 'Ler ve dil yapıları kullanmak istiyorsanız, `#if` kodunuzda yönergeleri kullanın. Ayrıca, hedeflediğiniz her platform için, her bir durum için gereken farklı API 'Leri dahil etmek için farklı paketler ve bağımlılıklar eklemeniz gerekebilir.

Örneğin, HTTP üzerinden ağ işlemleri gerçekleştiren bir kitaplığınız olduğunu varsayalım. .NET Standard ve .NET Framework sürümleri 4,5 veya üzeri için, `HttpClient` ad alanından sınıfını kullanabilirsiniz `System.Net.Http` . Ancak, .NET Framework önceki sürümleri sınıfına sahip değildir `HttpClient` , `WebClient` Bu nedenle `System.Net` bunun yerine ad alanından sınıfını kullanabilirsiniz.

Proje dosyanız şuna benzeyebilir:

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

Burada üç önemli değişiklik fark edeceksiniz:

1. `TargetFramework`Düğüm ile değiştirilmiştir `TargetFrameworks` ve üç tfms içinde belirtilir.
1. `<ItemGroup>` `net40` Bir .NET Framework başvurusunda hedef çekme için bir düğüm vardır.
1. `<ItemGroup>` `net45` İki .NET Framework başvuru halinde hedef çekme için bir düğüm vardır.

Yapı sistemi, yönergelerden kullanılan aşağıdaki Önişlemci simgelerinden haberdar olur `#if` :

[!INCLUDE [Preprocessor symbols](../../../includes/preprocessor-symbols.md)]

Hedefe göre koşullu derleme kullanan bir örnek aşağıda verilmiştir:

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

Bu projeyi ile oluşturursanız `dotnet build` , klasörün altında üç dizin olduğunu fark edeceksiniz `bin/` :

```
net40/
net45/
netstandard1.4/
```

Bunların her biri, `.dll` her bir hedef için dosyaları içerir.

## <a name="how-to-test-libraries-on-net-core"></a>.NET Core 'da kitaplıkları test etme

Platformlar arasında test etmek önemlidir. Kutusundan [xUnit](https://xunit.github.io/) veya mstest kullanabilirsiniz. Her ikisi de kitaplığınızın .NET Core 'da birim testi için uygundur. Çözümünüzü Test projeleri ile nasıl [ayarlayacağınıza çözümünüzün yapısına](#structuring-a-solution)göre değişiklik gösterir. Aşağıdaki örnek, test ve kaynak dizinlerinin aynı en üst düzey dizinde canlı olduğunu varsayar.

> [!NOTE]
> Bu, bazı [.NET Core CLI](../tools/index.md) komutlarını kullanır. Daha fazla bilgi için bkz. [DotNet New](../tools/dotnet-new.md) ve [DotNet sln](../tools/dotnet-sln.md) .

1. Çözümünüzü ayarlayın. Bunu aşağıdaki komutlarla yapabilirsiniz:

   ```dotnetcli
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   Bu, projeler oluşturur ve bunları bir çözümde birbirine bağlar. Dizininiz şuna `SolutionWithSrcAndTest` benzemelidir:

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. Test projesinin dizinine gidin ve öğesinden öğesine bir başvuru ekleyin `MyProject.Test` `MyProject` .

   ```dotnetcli
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. Paketleri geri yükle ve projeleri oluştur:

   ```dotnetcli
   dotnet restore
   dotnet build
   ```

   [!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

1. Komutunu yürüterek xUnit 'in çalıştığını doğrulayın `dotnet test` . MSTest kullanmayı seçerseniz, bunun yerine MSTest konsol Çalıştırıcısı çalıştırılmalıdır.

Hepsi bu! Artık, komut satırı araçlarını kullanarak kitaplığınızı tüm platformlarda test edebilirsiniz. Artık her şeyi ayarlamış olduğunuza göre teste devam etmek için, kitaplığınızı test etmek çok basittir:

1. Kitaplığınızda değişiklik yapın.
1. Testleri komut satırından, test dizininizde, `dotnet test` komutuyla çalıştırın.

Komut çağırdığınızda kodunuz otomatik olarak yeniden oluşturulur `dotnet test` .

## <a name="how-to-use-multiple-projects"></a>Birden çok proje kullanma

Daha büyük kitaplıkların yaygın olması, işlevselliği farklı projelere yerleştirbir yerdir.

Idimatik C# ve F # içinde tüketilen bir kitaplık oluşturmak istediğinizi düşünün. Bu, kitaplığınızın tüketicilerinin C# veya F # için doğal olan yollarla tükettiği anlamına gelir. Örneğin, C# ' de, kitaplığı şu şekilde kullanabilirsiniz:

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

F # ' da aşağıdaki gibi görünebilir:

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

Bu gibi tüketim senaryoları, erişildiği API 'Lerin C# ve F # için farklı bir yapıya sahip olması gerektiği anlamına gelir.  Bunu gerçekleştirmeye yönelik yaygın bir yaklaşım, bu temel projeye çağrı yapan API katmanlarını tanımlayan C# ve F # projeleri içeren bir kitaplığın tüm mantığını temel bir projeye katmasıdır.  Bölümün geri kalanı aşağıdaki adları kullanır:

* **Awesomelibrary. Core** -kitaplık için tüm mantığı içeren bir çekirdek proje
* **Awesomelibrary. CSharp** -C 'de tüketim için tasarlanan ortak API 'ler içeren bir proje #
* **Awesomelibrary. FSharp** -F 'de tüketim için tasarlanan ortak API 'ler içeren bir proje #

Bu kılavuzla aynı yapıyı oluşturmak için terminalinizde aşağıdaki komutları çalıştırabilirsiniz:

```dotnetcli
mkdir AwesomeLibrary && cd AwesomeLibrary
dotnet new sln
mkdir AwesomeLibrary.Core && cd AwesomeLibrary.Core && dotnet new classlib
cd ..
mkdir AwesomeLibrary.CSharp && cd AwesomeLibrary.CSharp && dotnet new classlib
cd ..
mkdir AwesomeLibrary.FSharp && cd AwesomeLibrary.FSharp && dotnet new classlib -lang "F#"
cd ..
dotnet sln add AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
dotnet sln add AwesomeLibrary.CSharp/AwesomeLibrary.CSharp.csproj
dotnet sln add AwesomeLibrary.FSharp/AwesomeLibrary.FSharp.fsproj
```

Bu, yukarıdaki üç projeyi ve bunları birbirine bağlayan bir çözüm dosyasını ekleyecek. Çözüm dosyası ve bağlantı projelerinin oluşturulması, projeleri en üst düzeyden geri yüklemenize ve oluşturmanıza imkan tanır.

### <a name="project-to-project-referencing"></a>Projeden projeye başvuru

Bir projeye başvurmak için en iyi yöntem .NET Core CLI bir proje başvurusu eklemek için kullanmaktır. **Awesomelibrary. CSharp** ve **Awesomelibrary. FSharp** proje dizinlerinde aşağıdaki komutu çalıştırabilirsiniz:

```dotnetcli
dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

Hem **Awesomelibrary. CSharp** hem de **Awesomelibrary. FSharp** için proje dosyaları artık bir hedef olarak **Awesomelibrary. Core** 'a başvuracaktır `ProjectReference` .  Bunu, proje dosyalarını inceleyerek ve içinde aşağıdakileri görerek doğrulayabilirsiniz:

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

.NET Core CLI kullanmayı tercih ediyorsanız, bu bölümü her proje dosyasına el ile ekleyebilirsiniz.

### <a name="structuring-a-solution"></a>Çözüm yapılandırma

Çok projeli çözümlerin diğer önemli bir yönü de iyi bir genel proje yapısı oluşturma. İsterseniz kodu düzenleyebilir, ve her bir projeyi çözüm dosyanıza bağladığınızda `dotnet sln add` , `dotnet restore` Çözüm düzeyinde ve ' yi çalıştıracaksınız `dotnet build` .
