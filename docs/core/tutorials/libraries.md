---
title: Platformlar Arası Araçlarla Kitaplık Geliştirme
description: .NET Core CLI araçlarını kullanarak .NET Core kitaplıkları oluşturmayı öğrenin. Çoklu çerçeveleri destekleyen bir kitaplık oluşturacaksınız.
author: cartermp
ms.date: 05/01/2017
ms.custom: seodec18
ms.openlocfilehash: 536319bc02b45e7948c89ae67988e821a55a842d
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117419"
---
# <a name="developing-libraries-with-cross-platform-tools"></a>Platformlar Arası Araçlarla Kitaplık Geliştirme

Bu makalede, platformlar arası CLı araçları kullanılarak .NET için kitaplıkların nasıl yazılacağı ele alınmaktadır. CLı, desteklenen tüm işletim sistemlerinde çalışacak etkili ve düşük düzeyde bir deneyim sağlar. Visual Studio ile Kitaplıklar oluşturmaya devam edebilirsiniz ve tercih ettiğiniz deneyim [Visual Studio kılavuzuna başvurur](libraries-with-vs.md).

## <a name="prerequisites"></a>Önkoşullar

Makinenizde yüklü [.NET Core SDK ve CLI](https://dotnet.microsoft.com/download) olması gerekir.

Bu belgenin .NET Framework sürümleriyle ilgili bölümlerinde, bir Windows makinesine [.NET Framework](https://dotnet.microsoft.com) yüklenmesi gerekir.

Ayrıca, eski .NET Framework hedeflerini desteklemek istiyorsanız, [.net indirme arşivleri sayfasından](https://dotnet.microsoft.com/download/archives)eski Framework sürümleri için hedefleme/geliştirici paketleri yüklemeniz gerekir. Bu tabloya başvurun:

| .NET Framework Sürümü | İndirileceği                                       |
| ---------------------- | ------------------------------------------------------ |
| 4.6.1                  | .NET Framework 4.6.1 hedefleme paketi                    |
| 4.6                    | .NET Framework 4,6 hedefleme paketi                      |
| 4.5.2                  | .NET Framework 4.5.2 Geliştirici paketi                    |
| 4.5.1                  | .NET Framework 4.5.1 Geliştirici paketi                    |
| 4,5                    | Windows 8 için Windows Yazılım Geliştirme Seti         |
| 4.0                    | Windows 7 ve .NET Framework 4 için Windows SDK         |
| 2,0, 3,0 ve 3,5      | .NET Framework 3,5 SP1 çalışma zamanı (veya Windows 8 + sürüm) |

## <a name="how-to-target-the-net-standard"></a>.NET Standard nasıl hedeflenecek

.NET Standard hakkında tam bilginiz yoksa daha fazla bilgi edinmek için [.NET Standard](../../standard/net-standard.md) başvurun.

Bu makalede, .NET Standard sürümlerini çeşitli uygulamalarla eşleyen bir tablo vardır:

[!INCLUDE [net-standard-table](../../../includes/net-standard-table.md)]

Bu tabloda kitaplık oluşturma amaçları için ne olacağı açıklanmaktadır:

Seçtiğiniz .NET Standard sürümü, en yeni API 'lere erişim ve daha fazla .NET uygulaması ve .NET Standard sürümlerini hedefleyebilme arasında bir zorunluluğunu getirir olacaktır. Bir sürümünü `netstandardX.X` `.csproj` (sürüm numarası) seçerek ve proje dosyanıza (veya `.fsproj`) ekleyerek hedeflenebilir platformlarının ve sürümlerinin aralığını kontrol edersiniz. `X.X`

Gereksinimlerinize bağlı olarak .NET Standard hedeflenirken üç birincil seçeneğiniz vardır.

1. Şablonlar `netstandard1.4` tarafından sağlanan .NET Standard varsayılan sürümünü kullanabilirsiniz. Bu, .NET Standard her API 'ye hala UWP, .NET Framework 4.6.1 ve forthın .NET Standard 2,0 ile uyumlu olmaya yönelik olarak erişim sağlar.

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>netstandard1.4</TargetFramework>
      </PropertyGroup>
    </Project>
    ```

2. Proje dosyanızın `TargetFramework` düğümündeki değeri değiştirerek .NET Standard daha düşük veya daha yüksek bir sürümünü kullanabilirsiniz.

    .NET Standard sürümler geriye dönük olarak uyumludur. Bu, `netstandard1.0` kitaplıkların platformlar ve daha `netstandard1.1` yükseği üzerinde çalıştığı anlamına gelir. Ancak, ileri bir uyumluluk yoktur .NET Standard platformlar daha yüksek bir değere başvuramaz. Bu, `netstandard1.0` kitaplıkların, `netstandard1.1` veya üzeri kitaplıklara başvurmayacağı anlamına gelir. Gereksinimlerinize uygun API 'lerin ve platform desteğinin doğru karışımına sahip standart sürümü seçin. Şimdilik önerilir `netstandard1.4` .

3. 4,0 veya sonraki .NET Framework sürümlerini hedeflemek istiyorsanız veya .NET Framework (örneğin, `System.Drawing`) .NET Standard değil, bir API kullanmak istiyorsanız, aşağıdaki bölümleri okuyun ve çoklu hedef hakkında bilgi edinin.

## <a name="how-to-target-the-net-framework"></a>.NET Framework nasıl hedeflenecek

> [!NOTE]
> Bu yönergeler makinenizde .NET Framework yüklü olduğunu varsayar. Bağımlılıkları yüklemek için [önkoşulları](#prerequisites) inceleyin.

Burada kullanılan .NET Framework sürümlerinden bazılarının artık desteğe göz önünde bulundurun. Desteklenmeyen sürümler hakkında [sss .NET Framework destek yaşam döngüsü ilkesi hakkında SSS](https://support.microsoft.com/gp/framework_faq/en-us) bölümüne bakın.

En fazla geliştirici ve proje sayısına ulaşmak isterseniz, taban çizgisi hedefi olarak 4,0 .NET Framework kullanın. .NET Framework hedeflemek için, desteklemek istediğiniz .NET Framework sürümüne karşılık gelen doğru hedef Framework bilinen adını (tfd) kullanarak başlamanız gerekir.

| .NET Framework sürümü | TFM      |
| ---------------------- | -------- |
| .NET Framework 2.0     | `net20`  |
| .NET Framework 3.0     | `net30`  |
| .NET Framework 3.5     | `net35`  |
| .NET Framework 4,0     | `net40`  |
| .NET Framework 4.5     | `net45`  |
| .NET Framework 4.5.1   | `net451` |
| .NET Framework 4.5.2   | `net452` |
| .NET Framework 4.6     | `net46`  |
| .NET Framework 4.6.1   | `net461` |
| .NET Framework 4.6.2   | `net462` |
| .NET framework 4.7     | `net47`  |
| .NET Framework 4,8     | `net48`  |

Daha sonra bu tfd `TargetFramework` 'yi proje dosyanızın bölümüne eklersiniz. Örneğin, .NET Framework 4,0 ' i hedefleyen bir kitaplığı nasıl yazacağınız aşağıda verilmiştir:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

İşte bu kadar! Bu yalnızca .NET Framework 4 için derlense de, kitaplığı .NET Framework daha yeni sürümlerinde kullanabilirsiniz.

## <a name="how-to-multitarget"></a>Çoklu hedef

> [!NOTE]
> Aşağıdaki yönergelerde .NET Framework makinenizde yüklü olduğunu varsaymaktadır. Yüklemeniz gereken bağımlılıkları ve bunların nereden indirileceği hakkında bilgi edinmek için [Önkoşullar](#prerequisites) bölümüne bakın.

Projeniz hem .NET Framework hem de .NET Core ' u desteklediğinde, .NET Framework eski sürümlerini hedefleyebilirsiniz. Bu senaryoda, daha yeni hedefler için daha yeni API 'ler ve dil yapıları kullanmak istiyorsanız, kodunuzda yönergeleri kullanın `#if` . Ayrıca, hedeflediğiniz her platform için, her bir durum için gereken farklı API 'Leri dahil etmek için farklı paketler ve bağımlılıklar eklemeniz gerekebilir.

Örneğin, HTTP üzerinden ağ işlemleri gerçekleştiren bir kitaplığınız olduğunu varsayalım. .NET Standard ve .NET Framework sürümleri 4,5 veya üzeri için, `HttpClient` `System.Net.Http` ad alanından sınıfını kullanabilirsiniz. Ancak, .NET Framework önceki sürümleri `HttpClient` sınıfına sahip değildir, bu nedenle bunun yerine `System.Net` ad alanından `WebClient` sınıfını kullanabilirsiniz.

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

1. `TargetFramework` Düğüm ile`TargetFrameworks`değiştirilmiştir ve üç tfms içinde belirtilir.
1. Bir .NET Framework başvurusunda `<ItemGroup>` `net40` hedef çekme için bir düğüm vardır.
1. İki .NET Framework başvuru `<ItemGroup>` halinde `net45` hedef çekme için bir düğüm vardır.

Yapı sistemi, `#if` yönergelerden kullanılan aşağıdaki Önişlemci simgelerinden haberdar olur:

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

Bu projeyi ile `dotnet build`oluşturursanız, `bin/` klasörün altında üç dizin olduğunu fark edeceksiniz:

```
net40/
net45/
netstandard1.4/
```

Bunların her biri, `.dll` her bir hedef için dosyaları içerir.

## <a name="how-to-test-libraries-on-net-core"></a>.NET Core 'da kitaplıkları test etme

Platformlar arasında test etmek önemlidir. Kutusundan [xUnit](https://xunit.github.io/) veya mstest kullanabilirsiniz. Her ikisi de kitaplığınızın .NET Core 'da birim testi için uygundur. Çözümünüzü Test projeleri ile nasıl [ayarlayacağınıza çözümünüzün yapısına](#structuring-a-solution)göre değişiklik gösterir. Aşağıdaki örnek, test ve kaynak dizinlerinin aynı en üst düzey dizinde canlı olduğunu varsayar.

> [!NOTE]
> Bu, bazı [.NET Core CLI komutlarını](../tools/index.md)kullanır. Daha fazla bilgi için bkz. [DotNet New](../tools/dotnet-new.md) ve [DotNet sln](../tools/dotnet-sln.md) .

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

   Bu, projeler oluşturur ve bunları bir çözümde birbirine bağlar. Dizininiz `SolutionWithSrcAndTest` şuna benzemelidir:

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. Test projesinin dizinine gidin ve öğesinden `MyProject.Test` `MyProject`öğesine bir başvuru ekleyin.

   ```bash
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. Paketleri geri yükle ve projeleri oluştur:

   ```dotnetcli
   dotnet restore
   dotnet build
   ```

   [!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

1. `dotnet test` Komutunu yürüterek xUnit 'in çalıştığını doğrulayın. MSTest kullanmayı seçerseniz, bunun yerine MSTest konsol Çalıştırıcısı çalıştırılmalıdır.

İşte bu kadar! Artık, komut satırı araçlarını kullanarak kitaplığınızı tüm platformlarda test edebilirsiniz. Artık her şeyi ayarlamış olduğunuza göre teste devam etmek için, kitaplığınızı test etmek çok basittir:

1. Kitaplığınızda değişiklik yapın.
1. Testleri komut satırından, test dizininizde `dotnet test` , komutuyla çalıştırın.

Komut çağırdığınızda `dotnet test` kodunuz otomatik olarak yeniden oluşturulur.

## <a name="how-to-use-multiple-projects"></a>Birden çok proje kullanma

Daha büyük kitaplıkların yaygın olması, işlevselliği farklı projelere yerleştirbir yerdir.

I, C# ve ' de tüketilen bir kitaplık oluşturmak için çok daha F#fazla düşünün. Bu, kitaplığınızın tüketicilerinin bunları veya C# F#için doğal olan yollarla tükettiği anlamına gelir. Örneğin, içinde C# kitaplığı şu şekilde kullanabilirsiniz:

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

' F#De, aşağıdaki gibi görünebilir:

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

Buna benzer tüketim senaryoları, erişildiği API 'Lerin ve C# F#için farklı bir yapıya sahip olması gerektiği anlamına gelir.  Bunu gerçekleştirmeye yönelik yaygın bir yaklaşım, bir kitaplığın tüm mantığını temel bir projeye, ile C# ve F# bu temel projeye çağrı yapan API katmanlarını tanımlayan projelere katmaya yönelik bir yaklaşımdır.  Bölümün geri kalanı aşağıdaki adları kullanır:

* **Awesomelibrary. Core** -kitaplık için tüm mantığı içeren bir çekirdek proje
* **Awesomelibrary. CSharp** -ortak API 'ler, içinde tüketim için tasarlanan bir projeC#
* **Awesomelibrary. FSharp** -' de tüketim için tasarlanan ortak API 'ler içeren bir projeF#

Bu kılavuzla aynı yapıyı oluşturmak için terminalinizde aşağıdaki komutları çalıştırabilirsiniz:

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

Bu, yukarıya üç projeyi ve bunları birbirine bağlayan bir çözüm dosyasını ekler. Çözüm dosyası ve bağlama projeleri oluşturmak, projeleri en üst düzeyden geri yüklemenize ve oluşturmanıza olanak sağlayacak.

### <a name="project-to-project-referencing"></a>Projeden projeye başvuru

Bir projeye başvurmak için en iyi yöntem .NET Core CLI bir proje başvurusu eklemek için kullanmaktır. **Awesomelibrary. CSharp** ve **Awesomelibrary. FSharp** proje dizinlerinde aşağıdaki komutu çalıştırabilirsiniz:

```dotnetcli
dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

Hem **awesomelibrary. CSharp** hem de **awesomelibrary. FSharp** için proje dosyaları artık bir `ProjectReference` hedef olarak **awesomelibrary. Core** 'a başvuracaktır.  Bunu, proje dosyalarını inceleyerek ve içinde aşağıdakileri görerek doğrulayabilirsiniz:

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

.NET Core CLI kullanmayı tercih ediyorsanız, bu bölümü her proje dosyasına el ile ekleyebilirsiniz.

### <a name="structuring-a-solution"></a>Çözüm yapılandırma

Çok projeli çözümlerin diğer önemli bir yönü de iyi bir genel proje yapısı oluşturma. İsterseniz kodu düzenleyebilir, ve her bir projeyi çözüm dosyanıza `dotnet sln add`bağladığınızda, çözüm düzeyinde ve `dotnet build` ' yi çalıştıracaksınız `dotnet restore` .
