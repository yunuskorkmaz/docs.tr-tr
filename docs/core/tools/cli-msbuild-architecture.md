---
title: .NET Core komut satırı araçları mimarisi
description: .NET Core araç katmanları ve son sürümlerde nelerin değiştiğini öğrenin.
ms.date: 03/06/2017
ms.openlocfilehash: 0064e7354f073be618bcf6a79962ab495927fadd
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980216"
---
# <a name="high-level-overview-of-changes-in-the-net-core-tools"></a>.NET Core araçlarındaki değişikliklere yüksek düzeyde genel bakış

Bu belge, .NET Core araçları 'nın katmanlanmasında ve CLı komutlarının uygulanması üzerindeki değişikliklerle ilgili bilgilerle, *Project. JSON* 'dan MSBuild 'e ve *csproj* proje sistemine geçiş ile ilişkili değişiklikleri açıklamaktadır. Bu değişiklikler, 7 Mart 2017 ' de .NET Core SDK 1,0 ve Visual Studio 2017 sürümü ile oluştu, ancak başlangıçta .NET Core SDK [](https://devblogs.microsoft.com/dotnet/announcing-net-core-tools-1-0/)Preview 3 sürümü ile uygulandı.

## <a name="moving-away-from-projectjson"></a>Project. JSON öğesinden uzağa taşıma

.NET Core için araçdaki en büyük değişiklik, Project [. JSON 'dan csproj 'a](https://devblogs.microsoft.com/dotnet/changes-to-project-json/) proje sistemi olarak geçilendir. Komut satırı araçlarının en son sürümleri *Project. JSON* dosyalarını desteklemez. Bu, Project. JSON tabanlı uygulamaları ve kitaplıkları derlemek, çalıştırmak veya yayımlamak için kullanılamayan anlamına gelir. Araçların bu sürümünü kullanmak için, mevcut projelerinizi geçirin veya yenilerini başlatın.

Bu taşımanın bir parçası olarak, Project. JSON projelerini derlemek için geliştirilmiş olan özel derleme altyapısı, aynı şekilde [MSBuild](https://github.com/Microsoft/msbuild)adlı ve tam özellikli bir yapı altyapısı ile değiştirilmiştir. MSBuild, .NET Community 'de iyi bilinen bir altyapıdır. Platformun ilk sürümünden bu yana önemli bir teknoloji oldu. .NET Core uygulamaları oluşturması gerektiğinden, MSBuild .NET Core 'a eklenmiştir ve .NET Core 'un üzerinde çalıştığı tüm platformlarda kullanılabilir. .NET Core 'un asıl adedlerinden biri platformlar arası bir geliştirme yığınıdır ve bu taşımanın bu taahhüdünü bozmadığından emin yaptık.

> [!TIP]
> MSBuild 'e yeni başladıysanız ve bu konuda daha fazla bilgi edinmek istiyorsanız, [MSBuild kavramlarını](/visualstudio/msbuild/msbuild-concepts) okuyun makalesini okuyun.

## <a name="the-tooling-layers"></a>Araç katmanları

Var olan proje sisteminin yanı sıra altyapı anahtarları oluşturma ile, doğal olarak takip eden soru, bu değişikliklerden herhangi biri, tüm .NET Core araçları ekosisteminin genel "katmanlama" düzeyini değiştirir. Yeni BITS ve bileşenler var mı?

Aşağıdaki resimde gösterildiği gibi Önizleme 2 katmanlarındaki hızlı yenileyici ile başlayalım:

![Preview 2 araçları üst düzey mimari](media/cli-msbuild-architecture/p2-arch.png)

Araçların katmanlama işlemi oldukça basittir. En altta, temel .NET Core CLI. Visual Studio veya Visual Studio Code gibi diğer tüm diğer, daha üst düzey araçlar, projeleri oluşturmak, bağımlılıkları geri yüklemek vb. için CLı 'ye bağımlıdır. Örneğin, Visual Studio bir geri yükleme işlemi gerçekleştirmek istiyorsam, CLı 'daki `dotnet restore` ([bkz. Note](#dotnet-restore-note)) komutuna çağrı yapar.

Yeni proje sistemine taşıma ile önceki diyagramda değişiklik yapılır:

![.NET Core SDK 1.0.0 üst düzey mimari](media/cli-msbuild-architecture/p3-arch.png)

Temel fark, CLı 'nin temel katman olmadığı bir şekilde değildir; Bu rol artık "paylaşılan SDK bileşeni" tarafından doldurulmuştur. Bu paylaşılan SDK bileşeni, kod derlenirken, yayımlamaktan, NuGet paketlerinde paketlemesinden ve benzeri bir hedef ve ilişkili görev kümesidir. .NET Core SDK açık kaynaktır ve [SDK](https://github.com/dotnet/sdk)deposunda GitHub 'da kullanılabilir.

> [!NOTE]
> "Target", MSBuild 'in çağırabileceği adlandırılmış bir işlemi gösteren bir MSBuild terimidir. Genellikle hedefin yapması gereken bazı mantığı çalıştıran bir veya daha fazla görevle birlikte kullanılır. MSBuild, `Copy` veya `Execute`gibi çok sayıda kullanıma yönelik hedefi destekler; Ayrıca, kullanıcıların yönetilen kod kullanarak kendi görevlerini yazmasına ve bu görevleri yürütmek için hedefleri tanımlamasına olanak tanır. Daha fazla bilgi için bkz. [MSBuild görevleri](/visualstudio/msbuild/msbuild-tasks).

Tüm araç takımları 'ler artık paylaşılan SDK bileşenini ve bunların hedeflerini kullanır ve CLI dahildir. Örneğin, Visual Studio 2019, .NET Core projelerine yönelik bağımlılıkları geri yüklemek için `dotnet restore` ([bkz. Note](#dotnet-restore-note)) komutuna çağrı yapmaz. Bunun yerine, "Restore" hedefini doğrudan kullanır. Bunlar MSBuild hedefleri olduğundan, [DotNet MSBuild](dotnet-msbuild.md) komutunu kullanarak bunları yürütmek Için ham MSBuild 'i de kullanabilirsiniz.

### <a name="cli-commands"></a>CLı komutları

Paylaşılan SDK bileşeni, var olan CLı komutlarının büyük çoğunluğunun MSBuild görevi ve hedefleri olarak yeniden uygulandığı anlamına gelir. Bu, CLı komutları ve araç takımını kullanımınız için ne anlama geliyor?

Kullanım perspektifinden, CLı 'yı kullanma yöntemini değiştirmez. CLı hala .NET Core 1,0 Preview 2 sürümünde bulunan temel komutlara sahiptir:

- `new`
- `restore`
- `run`
- `build`
- `publish`
- `test`
- `pack`

Bu komutlar, bunların ne olduğunu beklediğinizi (bir proje oluşturun, oluşturun, yayımlayın, paketleyebilir, vb.) devam eder. Davranışlarıyla ilgili bilgi almak için komutun yardım ekranına (`dotnet <command> --help`kullanarak) veya bu sitedeki belgelere başvurabilirsiniz.

Bir yürütme perspektifinden, CLı komutları parametrelerini alır ve gerekli özellikleri ayarlayan ve istenen hedefi çalıştıran "RAW" MSBuild 'e bir çağrı oluşturur. Bunu daha iyi anlamak için aşağıdaki komutu göz önünde bulundurun:

   ```dotnetcli
   dotnet publish -o pub -c Release
   ```

Bu komut, bir uygulamayı bir `pub` klasörüne "Release" yapılandırmasını kullanarak yayımlar. Dahili olarak, bu komut aşağıdaki MSBuild çağrısına çevrilir:

   ```dotnetcli
   dotnet msbuild -t:Publish -p:OutputPath=pub -p:Configuration=Release
   ```

Bu kurala yönelik Notable özel durumları `new` ve `run` komutlardır. MSBuild hedefleri olarak uygulanmamış.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
