---
title: .NET Çekirdek Komut satırı araçları mimarisi
description: .NET Core araç katmanları ve son sürümlerde nelerin değiştiği hakkında bilgi edinin.
ms.date: 03/06/2017
ms.openlocfilehash: fde1a0acb6af9dd65aa3466b4ea37473b2eab6fb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77092921"
---
# <a name="high-level-overview-of-changes-in-the-net-core-tools"></a>.NET Core araçlarındaki değişikliklere üst düzey genel bakış

Bu belge, .NET Core takımlama ve CLI komutlarının uygulanmasında yapılan değişiklikler hakkında bilgi içeren *project.json'dan* MSBuild'e ve *csproj* proje sisteminden taşınmayla ilişkili değişiklikleri açıklar. Bu değişiklikler 7 Mart 2017 tarihinde .NET Core SDK 1.0 ve Visual Studio 2017'nin yayınlanmasıyla meydana geldi [(duyuruya](https://devblogs.microsoft.com/dotnet/announcing-net-core-tools-1-0/)bakın) ancak başlangıçta .NET Core SDK Preview 3'ün yayınlanmasıyla uygulandı.

## <a name="moving-away-from-projectjson"></a>Project.json'dan uzaklaşmak

.NET Core için takımlamadaki en büyük değişiklik kesinlikle [project.json'dan proje sistemi olarak csproj'a taşınmaktır.](https://devblogs.microsoft.com/dotnet/changes-to-project-json/) Komut satırı araçlarının en son sürümleri *project.json* dosyalarını desteklemez. Bu, project.json tabanlı uygulamalar ve kitaplıklar oluşturmak, çalıştırmak veya yayımlamak için kullanılamayacağı anlamına gelir. Araçların bu sürümünü kullanmak için, varolan projelerinizi geçirin veya yenilerini başlatın.

Bu hareketin bir parçası olarak, project.json projeleri oluşturmak için geliştirilen özel yapı motoru [MSBuild](https://github.com/Microsoft/msbuild)adlı olgun ve tam yetenekli bir yapı motoru ile değiştirildi. MSBuild.NET topluluğunda tanınmış bir motordur. Platformun ilk sürümünden bu yana önemli bir teknoloji olmuştur. .NET Core uygulamaları oluşturması gerektiğinden, MSBuild .NET Core'a taşınabilir ve .NET Core'un çalıştığı herhangi bir platformda kullanılabilir. .NET Core'un ana vaatlerinden biri, platformlar arası geliştirme yığınıdır ve bu hamlenin bu sözü tutmamasını sağladık.

> [!TIP]
> EĞER MSBuild yeni ve bu konuda daha fazla bilgi edinmek istiyorsanız, [MSBuild kavramlar](/visualstudio/msbuild/msbuild-concepts) makale okuyarak başlayabilirsiniz.

## <a name="the-tooling-layers"></a>Takım katmanları

Yapı motorundaki değişiklik ve mevcut proje sisteminden uzaklaşmasıyla, bazı sorular doğal olarak takip eder. Bu değişikliklerden herhangi biri .NET Core araç ekosisteminin genel "katmanlama"sını değiştirir mi? Yeni bitler ve bileşenler var mı?

Aşağıdaki resimde gösterildiği gibi Önizleme 2 katmanında hızlı bir yenileme ile başlayalım:

![Önizleme 2 araçları üst düzey mimari](media/cli-msbuild-architecture/p2-arch.png)

Önizleme 2'deki araçların katmanlanması basittir. Altta, temel .NET Çekirdek CLI olduğunu. Visual Studio veya Visual Studio Code gibi diğer tüm üst düzey araçlar, projeler oluşturmak, bağımlılıkları geri yüklemek ve benzeri için CLI'ye bağlıdır ve bunlara güvenir. Örneğin, Visual Studio bir geri yükleme işlemi gerçekleştirmek istiyorsa, CLI'deki `dotnet restore` [(nota bakınız)](#dotnet-restore-note)komutuna çağrır.

Yeni proje sistemine geçicisiile, önceki diyagram değişir:

![.NET Core SDK 1.0.0 üst düzey mimari](media/cli-msbuild-architecture/p3-arch.png)

Temel fark, CLI artık temel tabaka değildir; bu rol artık "paylaşılan SDK bileşeni" tarafından doldurulur. Bu paylaşılan SDK bileşeni, kodu derlemekten, yayımlamaktan, NuGet paketlerini paketlemekten ve benzeri nedenlerden sorumlu hedefler ve ilişkili görevler kümesidir. .NET Core SDK açık kaynak kodludur ve [GitHub'da SDK repo'da](https://github.com/dotnet/sdk)mevcuttur.

> [!NOTE]
> "Hedef", MSBuild'in çağırabileceği adlandırılmış bir işlemi gösteren bir MSBuild terimidir. Genellikle hedef yapmak gerekiyordu bazı mantık yürütmek bir veya daha fazla görev ile birleştiğinde. MSBuild gibi `Copy` birçok hazır hedefleri `Execute`destekler; ayrıca, kullanıcıların yönetilen kodu kullanarak kendi görevlerini yazmalarına ve bu görevleri yürütmek için hedefleri tanımlamalarına da olanak tanır. Daha fazla bilgi için [MSBuild görevlerine](/visualstudio/msbuild/msbuild-tasks)bakın.

CLI dahil olmak üzere tüm araç kümeleri artık paylaşılan SDK bileşenini ve hedeflerini tüketmektedir. Örneğin, Visual Studio 2019 ,NET `dotnet restore` Core projelerinin bağımlılıklarını geri yüklemek için[(nota bakınız)](#dotnet-restore-note)komutunu aramaz. Bunun yerine, doğrudan "Geri Yükleme" hedefini kullanır. Bunlar MSBuild hedefleri olduğundan, [dotnet msbuild](dotnet-msbuild.md) komutunu kullanarak bunları yürütmek için ham MSBuild'i de kullanabilirsiniz.

### <a name="cli-commands"></a>CLI komutları

Paylaşılan SDK bileşeni, varolan CLI komutlarının çoğunun MSBuild görevleri ve hedefleri olarak yeniden uygulandığı anlamına gelir. Bu, CLI komutları ve araç setini kullanımınız için ne anlama geliyor?

Kullanım açısından bakıldığında, CLI'yi kullanma şeklinizi değiştirmez. CLI hala .NET Core 1.0 Önizleme 2 sürümünde var olan çekirdek komutları vardır:

- `new`
- `restore`
- `run`
- `build`
- `publish`
- `test`
- `pack`

Bu komutlar hala yapmalarını beklediğiniz şeyi yapar (bir projeyi yenileyin, oluşturun, yayımlayın, paketleyin, vb.). Davranışlarını tanımak için komutun yardım ekranına (kullanarak) `dotnet <command> --help`veya bu sitedeki belgelere danışabilirsiniz.

Yürütme açısından bakıldığında, CLI komutları parametrelerini alır ve gerekli özellikleri belirleyen ve istenen hedefi çalıştıran "ham" MSBuild'e bir çağrı oluşturur. Bunu daha iyi göstermek için aşağıdaki komutu göz önünde bulundurun:

   ```dotnetcli
   dotnet publish -o pub -c Release
   ```

Bu komut, "Release" `pub` yapılandırmasını kullanarak bir uygulamayı klasöre yayımlar. Dahili olarak, bu komut aşağıdaki MSBuild çağırmasına çevrilir:

   ```dotnetcli
   dotnet msbuild -t:Publish -p:OutputPath=pub -p:Configuration=Release
   ```

Bu kuralın önemli `new` istisnaları `run` ve komutlarıdır. Bunlar MSBuild hedefleri olarak uygulanmamıştır.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
