---
title: .NET Core komut satırı araçları mimarisi
description: .NET Core araç katmanları ve son sürümlerde nelerin değiştiğini öğrenin.
ms.date: 03/06/2017
ms.openlocfilehash: 05183a9edc26615e00d6383043fd10d8bec06f2b
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72521303"
---
# <a name="high-level-overview-of-changes-in-the-net-core-tools"></a>.NET Core araçlarındaki değişikliklere yüksek düzeyde genel bakış

Bu belge, .NET Core araçları 'nın katmanlanmasında ve CLı komutlarının uygulanması üzerindeki değişikliklerle ilgili bilgilerle, *Project. JSON* 'dan MSBuild 'e ve *csproj* proje sistemine geçiş ile ilişkili değişiklikleri açıklamaktadır. Bu değişiklikler, 7 Mart 2017 ' de .NET Core SDK 1,0 ve Visual Studio 2017 sürümü ile oluştu, ancak başlangıçta .NET Core SDK [](https://devblogs.microsoft.com/dotnet/announcing-net-core-tools-1-0/)Preview 3 sürümü ile uygulandı.

## <a name="moving-away-from-projectjson"></a>Project. JSON öğesinden uzağa taşıma

.NET Core için araçdaki en büyük değişiklik, Project [. JSON 'dan csproj 'a](https://devblogs.microsoft.com/dotnet/changes-to-project-json/) proje sistemi olarak geçilendir. Komut satırı araçlarının en son sürümleri *Project. JSON* dosyalarını desteklemez. Bu, Project. JSON tabanlı uygulamaları ve kitaplıkları derlemek, çalıştırmak veya yayımlamak için kullanılamayan anlamına gelir. Araçların bu sürümünü kullanabilmeniz için mevcut projelerinizi geçirmeniz veya yenilerini başlatmanız gerekir. 

Bu taşımanın bir parçası olarak, Project. JSON projelerini derlemek için geliştirilmiş olan özel derleme altyapısı, aynı şekilde [MSBuild](https://github.com/Microsoft/msbuild)adlı ve tam özellikli bir yapı altyapısı ile değiştirilmiştir. MSBuild, platformun ilk sürümünden bu yana önemli bir teknoloji olduğundan, .NET Community 'de iyi bilinen bir altyapıdır. Kuşkusuz, .NET Core uygulamaları oluşturması gerektiğinden, MSBuild .NET Core 'a eklenmiştir ve .NET Core 'un üzerinde çalıştığı tüm platformlarda kullanılabilir. .NET Core 'un asıl adedlerinden biri platformlar arası bir geliştirme yığınıdır ve bu taşımanın bu taahhüdünü bozmadığından emin yaptık.

> [!NOTE]
> MSBuild 'e yeni başladıysanız ve bu konuda daha fazla bilgi edinmek istiyorsanız, [MSBuild kavramlarını](/visualstudio/msbuild/msbuild-concepts) okuyun makalesini okuyun. 

## <a name="the-tooling-layers"></a>Araç katmanları

Var olan proje sisteminin yanı sıra altyapı anahtarları oluşturma ile, doğal olarak takip eden soru, bu değişikliklerden herhangi biri, tüm .NET Core araçları ekosisteminin genel "katmanlama" düzeyini değiştirir. Yeni BITS ve bileşenler var mı?

Aşağıdaki resimde gösterildiği gibi Önizleme 2 katmanlarındaki hızlı yenileyici ile başlayalım:

![Preview 2 araçları üst düzey mimari](media/cli-msbuild-architecture/p2-arch.png)

Araçların katmanlama işlemi oldukça basittir. En altta, temel olarak .NET Core komut satırı araçları vardır. Visual Studio veya Visual Studio Code gibi diğer tüm diğer, daha üst düzey araçlar, projeleri oluşturmak, bağımlılıkları geri yüklemek ve daha fazlasını yapmak için CLı 'ye bağımlıdır ve kullanır. Bu, örneğin, Visual Studio 'Nun geri yükleme işlemi gerçekleştirmesini istediği anlamına gelir. Bu, CLı 'daki `dotnet restore` (bkz.[Note](#dotnet-restore-note)) komutuna çağrı yapar. 

Yeni proje sistemine taşıma ile önceki diyagramda değişiklik yapılır: 

![.NET Core SDK 1.0.0 üst düzey mimari](media/cli-msbuild-architecture/p3-arch.png)

Temel fark, CLı 'nin temel katman olmadığı bir şekilde değildir; Bu rol artık "paylaşılan SDK bileşeni" tarafından doldurulmuştur. Bu paylaşılan SDK bileşeni, kodunuzun derlenmesi, yayımlanması, NuGet paketleri ve paketlemesinden sorumlu bir hedef ve ilişkili görev kümesidir. SDK 'nın kendisi açık kaynaktır ve [SDK](https://github.com/dotnet/sdk)deposunda GitHub 'da kullanılabilir. 

> [!NOTE]
> "Target", MSBuild 'in çağırabileceği adlandırılmış bir işlemi gösteren bir MSBuild terimidir. Genellikle hedefin yapması gereken bazı mantığı çalıştıran bir veya daha fazla görevle birlikte kullanılır. MSBuild, `Copy` veya `Execute` gibi çok sayıda kullanıma yönelik hedefi destekler; Ayrıca, kullanıcıların yönetilen kod kullanarak kendi görevlerini yazmasına ve bu görevleri yürütmek için hedefleri tanımlamasına olanak tanır. Daha fazla bilgi için bkz. [MSBuild görevleri](/visualstudio/msbuild/msbuild-tasks). 

Tüm araç takımları 'ler artık paylaşılan SDK bileşenini ve bunların hedeflerini kullanır ve CLI dahildir. Örneğin, Visual Studio 'nun bir sonraki sürümü, .NET Core projelerinin bağımlılıklarını geri yüklemek için `dotnet restore` ([bkz. Not](#dotnet-restore-note)) komutuna çağırmayacak, "Restore" hedefini doğrudan kullanacaktır. Bunlar MSBuild hedefleri olduğundan, [DotNet MSBuild](dotnet-msbuild.md) komutunu kullanarak bunları yürütmek Için ham MSBuild 'i de kullanabilirsiniz. 

### <a name="cli-commands"></a>CLı komutları
Paylaşılan SDK bileşeni, var olan CLı komutlarının büyük çoğunluğunun MSBuild görevi ve hedefleri olarak yeniden uygulandığı anlamına gelir. Bu, CLı komutları ve araç takımını kullanımınız için ne anlama geliyor? 

Kullanım perspektifinden, CLı 'yı kullanma yöntemini değiştirmez. CLı, Preview 2 sürümünde var olan temel komutlara hala sahiptir:

- `new`
- `restore`
- `run` 
- `build`
- `publish`
- `test`
- `pack` 

Bu komutlar, bunların ne olduğunu beklediğinizi (bir proje oluşturun, oluşturun, yayımlayın, bu şekilde paketleyebilir). Seçeneklerin büyük bölümü değiştirilmez ve hâlâ orada bulunur ve herhangi bir değişikliği öğrenmek için bu sitedeki komutlara (`dotnet <command> --help` kullanarak) ya da belgelere başvurabilirsiniz. 

Bir yürütme perspektifinden, CLı komutları parametrelerini alır ve gerekli özellikleri ayarlanacak ve istenen hedefi çalıştıran "RAW" MSBuild çağrısı oluşturacak. Bunu daha iyi anlamak için aşağıdaki komutu göz önünde bulundurun: 

   ```dotnetcli
   dotnet publish -o pub -c Release
   ```
    
Bu komut, bir uygulamayı bir `pub` klasöre yayımlarken "yayın" yapılandırması kullanılarak yapılır. Dahili olarak, bu komut aşağıdaki MSBuild çağrısına çevrilir: 

   ```dotnetcli
   dotnet msbuild -t:Publish -p:OutputPath=pub -p:Configuration=Release
   ```

Bu kuralın önemli özel durumu, MSBuild hedefleri olarak uygulanmadığından `new` ve `run` komutlardır.

<a name="dotnet-restore-note"></a>  
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
