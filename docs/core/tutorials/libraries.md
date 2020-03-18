---
title: .NET Core CLI ile kütüphaneler geliştirin
description: .NET Core CLI'yi kullanarak .NET Core kitaplıklarını nasıl oluşturabilirsiniz öğrenin. Birden çok çerçeveyi destekleyen bir kitaplık oluşturursunuz.
author: cartermp
ms.date: 05/01/2017
ms.openlocfilehash: c23c1f027b4d6d09c50eb2257d34f72ec56302f4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503502"
---
# <a name="develop-libraries-with-the-net-core-cli"></a>.NET Core CLI ile kütüphaneler geliştirin

Bu makalede,.NET CLI'yi kullanarak .NET için kitaplıkların nasıl yazılalıyorum. CLI, desteklenen tüm işletim sistemi genelinde çalışan verimli ve düşük seviyeli bir deneyim sağlar. Visual Studio ile kitaplıklar oluşturmaya devam edebilirsiniz ve tercih ettiğiniz deneyim buysa [Visual Studio kılavuzuna bakın.](library-with-visual-studio.md)

## <a name="prerequisites"></a>Önkoşullar

Makinenize [.NET Core SDK ve CLI](https://dotnet.microsoft.com/download) yüklü olmanız gerekir.

Bu belgenin .NET Framework sürümleriyle ilgili bölümleri için bir Windows makinesine yüklü [.NET Framework](https://dotnet.microsoft.com) gerekir.

Ayrıca, eski .NET Framework hedeflerini desteklemek istiyorsanız, [.NET indirme arşivleri sayfasından](https://dotnet.microsoft.com/download/archives)hedefleme paketleri veya geliştirici paketleri yüklemeniz gerekir. Bu tabloya bakın:

| .NET Framework sürümü | Ne indirmek için                                       |
| ---------------------- | ------------------------------------------------------ |
| 4.6.1                  | .NET Framework 4.6.1 Hedefleme Paketi                    |
| 4.6                    | .NET Framework 4.6 Hedefleme Paketi                      |
| 4.5.2                  | .NET Framework 4.5.2 Geliştirici Paketi                    |
| 4.5.1                  | .NET Framework 4.5.1 Geliştirici Paketi                    |
| 4,5                    | Windows 8 için Windows Yazılım Geliştirme Seti         |
| 4.0                    | Windows 7 için Windows SDK ve .NET Framework 4         |
| 2.0, 3.0 ve 3.5      | .NET Framework 3.5 SP1 Çalışma Süresi (veya Windows 8+ sürümü) |

## <a name="how-to-target-the-net-standard"></a>.NET Standardı nasıl hedefilir?

.NET Standard'ı bilmiyorsanız, daha fazla bilgi edinmek için [.NET Standard'a](../../standard/net-standard.md) bakın.

Bu makalede, .NET Standart sürümlerini çeşitli uygulamalarla eşleyen bir tablo vardır:

[!INCLUDE [net-standard-table](../../../includes/net-standard-table.md)]

Bu tablo, kitaplık oluşturmak amacıyla şu anlama gelir:

Seçtiğiniz .NET Standard sürümü, en yeni API'lere erişim ile daha fazla .NET uygulaması ve .NET Standart sürümlerini hedefleme olanağı arasında bir denge olacaktır. Hedeflenen platformların ve sürümlerin `netstandardX.X` aralığını bir sürümünü `X.X` seçerek (sürüm numarası nın bulunduğu yer) `.fsproj`ve proje dosyanıza (veya)`.csproj` ekleyerek denetlersiniz.

İhtiyaçlarınıza bağlı olarak .NET Standard'ı hedef alırken üç ana seçeneğiniz vardır.

1. UWP, `netstandard1.4`.NET Framework 4.6.1 ve .NET Standard 2.0 ile uyumlu yken .NET Standardı'ndaki çoğu API'ye erişmenizi sağlayan şablonlar tarafından sağlanan .NET Standard'ın varsayılan sürümünü kullanabilirsiniz.

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>netstandard1.4</TargetFramework>
      </PropertyGroup>
    </Project>
    ```

2. Proje dosyanızın `TargetFramework` düğümündeki değeri değiştirerek .NET Standard'ın daha düşük veya daha yüksek bir sürümünü kullanabilirsiniz.

    .NET Standart sürümleri geriye dönük uyumludur. Bu, `netstandard1.0` kitaplıkların `netstandard1.1` platformlarda ve daha yüksek platformlarda çalıştırıldığı anlamına gelir. Ancak, ileri uyumluluk yoktur. Alt .NET Standart platformlar daha yüksek platformlara başvuruyapamaz. Bu, `netstandard1.0` kitaplıkların hedefleme `netstandard1.1` veya daha yüksek kitaplıkları referans veremeyeceği anlamına gelir. İhtiyaçlarınız için DOĞRU API ve platform desteği karışımına sahip Standart sürümü seçin. Şimdilik `netstandard1.4` tavsiye ediyoruz.

3. .NET Framework sürümleri4.0 veya altında hedeflemek istiyorsanız veya .NET Framework'de bulunan ancak .NET Standard'da `System.Drawing`(örneğin) bulunmayan bir API kullanmak istiyorsanız, aşağıdaki bölümleri okuyun ve nasıl çoklu hedef le hedeflenmeyeceğinizi öğrenin.

## <a name="how-to-target-net-framework"></a>.NET Framework nasıl hedefilir?

> [!NOTE]
> Bu talimatlar makinenizde .NET Framework yüklü olduğunuzu varsayar. Bağımlılıkları yüklemek için [Ön koşullara](#prerequisites) bakın.

Burada kullanılan .NET Framework sürümlerinden bazılarının artık desteklenmediğini unutmayın. Desteklenmeyen sürümler hakkında [.NET Framework Support Yaşam Döngüsü İlkesi SSS'sine](https://support.microsoft.com/gp/framework_faq/en-us) bakın.

Maksimum geliştirici ve proje sayısına ulaşmak istiyorsanız, temel hedefiniz olarak .NET Framework 4.0'ı kullanın. .NET Framework'ü hedeflemek için, desteklemek istediğiniz .NET Framework sürümüne karşılık gelen doğru Hedef Çerçeve Takma Adı (TFM) kullanarak başlayın.

| .NET Framework sürümü | Tfm      |
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

Daha sonra bu TFM'yi proje dosyanızın bölümüne `TargetFramework` eklersiniz. Örneğin, .NET Framework 4.0'ı hedefleyen bir kitaplığı şu şekilde yazarsınız:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

Hepsi bu! Bu yalnızca .NET Framework 4 için derlenmiş olsa da, .NET Framework'ün yeni sürümlerinde kitaplığı kullanabilirsiniz.

## <a name="how-to-multitarget"></a>Çoklu hedef nasıl

> [!NOTE]
> Aşağıdaki talimatlar makinenizde .NET Framework yüklü olduğunu varsayar. Hangi bağımlılıkları yüklemeniz gerektiğini ve bunları nereden indirmeniz gerektiğini öğrenmek için [Önkoşullar](#prerequisites) bölümüne bakın.

Projeniz hem .NET Framework'ü hem de .NET Core'u desteklediğinde .NET Framework'ün eski sürümlerini hedeflemeniz gerekebilir. Bu senaryoda, yeni hedefler için daha yeni API'ler ve dil `#if` yapıları kullanmak istiyorsanız, kodunuzda yönergeleri kullanın. Ayrıca, hedeflediğiniz her platform için her servis talebi için gereken farklı API'leri eklemek için farklı paketler ve bağımlılıklar eklemeniz gerekebilir.

Örneğin, http üzerinden ağ işlemleri gerçekleştiren bir kitaplığınız olduğunu varsayalım. .NET Standard ve .NET Framework sürümleri 4.5 veya `HttpClient` üzeri için `System.Net.Http` sınıfı ad alanından kullanabilirsiniz. Ancak, .NET Framework'ün önceki sürümlerinde `HttpClient` sınıf yoktur, bu `WebClient` nedenle `System.Net` sınıfı ad alanından kullanabilirsiniz.

Proje dosyanız şu şekilde görünebilir:

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

Burada üç büyük değişiklik fark edeceksiniz:

1. Düğüm `TargetFramework` , `TargetFrameworks`ve üç TFMs içinde ifade edilmiştir değiştirildi.
1. Bir .NET Framework `<ItemGroup>` `net40` referansını çeken hedef için bir düğüm vardır.
1. İki .NET Framework `<ItemGroup>` `net45` referansı çeken hedef için bir düğüm vardır.

Yapı sistemi, direktiflerde `#if` kullanılan aşağıdaki önişlemci sembollerinden haberdardır:

[!INCLUDE [Preprocessor symbols](../../../includes/preprocessor-symbols.md)]

Aşağıda, hedef başına koşullu derlemeden yararlanılanbir örnek verilmiştir:

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

Bu projeyi klasörün `dotnet build` `bin/` altında üç dizin le oluşturursanız:

```
net40/
net45/
netstandard1.4/
```

Bunların her biri, her hedef için `.dll` dosyaları içerir.

## <a name="how-to-test-libraries-on-net-core"></a>.NET Core'da kitaplıklar nasıl test edilebilir?

Platformlar arasında test edebilmek önemlidir. [XUnit](https://xunit.github.io/) veya MSTest'i kutunun dışında kullanabilirsiniz. Her ikisi de .NET Core'da kitaplığınızı test etmek için mükemmel bir şekilde uygundur. Çözümünüzü test projeleri ile nasıl ayarlayacağınız [çözümünuzun yapısına](#structuring-a-solution)bağlıdır. Aşağıdaki örnek, test ve kaynak dizinlerinin aynı üst düzey dizinde yaşadığını varsayar.

> [!NOTE]
> Bu bazı [.NET Core CLI](../tools/index.md) komutları kullanır. Daha fazla bilgi için [dotnet yeni](../tools/dotnet-new.md) ve [dotnet sln](../tools/dotnet-sln.md) bakın.

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

   Bu projeler oluşturmak ve bir çözüm onları birbirine bağlayacak. Dizin için `SolutionWithSrcAndTest` bu gibi görünmelidir:

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. Test projesinin dizinine gidin ve `MyProject.Test` 'den `MyProject`bir başvuru ekleyin.

   ```dotnetcli
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. Paketleri geri yükleyin ve projeler oluşturun:

   ```dotnetcli
   dotnet restore
   dotnet build
   ```

   [!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

1. `dotnet test` xUnit'in komutu çalıştırarak çalıştığını doğrulayın. MSTest'i kullanmayı seçtiyseniz, bunun yerine MSTest konsol koşucusu çalıştırılmalıdır.

Hepsi bu! Artık komut satırı araçlarını kullanarak kitaplığınızı tüm platformlarda test edebilirsiniz. Her şeyi ayarladığınızdasına göre sınamalara devam etmek için kitaplığınızı test etmek çok basittir:

1. Kitaplığınızda değişiklik yapın.
1. Komut satırından, test dizininizde komutla `dotnet test` testleri çalıştırın.

Komutu çağırdığınızda `dotnet test` kodunuz otomatik olarak yeniden oluşturulur.

## <a name="how-to-use-multiple-projects"></a>Birden çok proje nasıl kullanılır?

Daha büyük kitaplıklar için ortak bir ihtiyaç farklı projelerde işlevsellik yerleştirmektir.

Deyimsel C# ve F# olarak tüketilebilen bir kütüphane oluşturmak istediğinizi düşünün. Bu, kitaplığınızın tüketicilerinin bu kitabı C# veya F# açısından doğal şekillerde tükettiği anlamına gelir. Örneğin, C# kitaplığını şu şekilde tüketebilirsiniz:

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

F#'da şu şekilde görünebilir:

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

Bu gibi tüketim senaryoları, erişilen API'lerin C# ve F# için farklı bir yapıya sahip olması gerektiği anlamına gelir.  Bunu gerçekleştirmek için ortak bir yaklaşım, bir kitaplığın tüm mantığını, c# ve F# projeleri ile bu temel projeye çağrı yapan API katmanlarını tanımlayan bir çekirdek projeye dahil etmektir.  Bölümün geri kalanı aşağıdaki adları kullanır:

* **AwesomeLibrary.Core** - kütüphane için tüm mantığı içeren bir çekirdek proje
* **AwesomeLibrary.CSharp** - C tüketimi için tasarlanmış kamu API'leri ile bir proje #
* **AwesomeLibrary.FSharp** - F tüketimi için tasarlanmış kamu API'leri ile bir proje #

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

Bu, yukarıdaki üç projeyi ve onları birbirine bağlayan bir çözüm dosyasını ekler. Çözüm dosyası oluşturma ve projeleri bağlama, projeleri en üst düzeyden geri yüklemenize ve oluşturmanıza olanak sağlar.

### <a name="project-to-project-referencing"></a>Projeden projeye başvuru

Bir projeye başvurmanın en iyi yolu, bir proje başvurusu eklemek için .NET Core CLI'yi kullanmaktır. **AwesomeLibrary.CSharp** ve **AwesomeLibrary.FSharp** proje dizinleri, aşağıdaki komutu çalıştırabilirsiniz:

```dotnetcli
dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

**Hem AwesomeLibrary.CSharp** ve **AwesomeLibrary.FSharp** için proje dosyaları şimdi bir `ProjectReference` hedef olarak **AwesomeLibrary.Core** başvuruolacaktır.  Proje dosyalarını inceleyerek ve aşağıdakileri görerek bunu doğrulayabilirsiniz:

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

.NET Core CLI'yi kullanmamak isterseniz bu bölümü her proje dosyasına el ile ekleyebilirsiniz.

### <a name="structuring-a-solution"></a>Çözüm yapılandırma

Çok projeli çözümlerin bir diğer önemli yönü de iyi bir genel proje yapısı oluşturmaktır. Kodu istediğiniz gibi düzenleyebilirsiniz ve her projeyi çözüm dosyanıza `dotnet sln add`bağladiğiniz sürece, `dotnet restore` çalıştırabilirsiniz ve `dotnet build` çözüm düzeyinde.
