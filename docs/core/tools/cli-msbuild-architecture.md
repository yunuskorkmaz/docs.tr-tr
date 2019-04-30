---
title: .NET core komut satırı araçları mimarisi
description: Katmanlar ve en son sürümlerde nelerin değiştiğini .NET Core hakkında bilgi edinin.
ms.date: 03/06/2017
ms.openlocfilehash: e9226a314932eb73c6474c0fd17c77c87683e6db
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665526"
---
# <a name="high-level-overview-of-changes-in-the-net-core-tools"></a>.NET Core Araçları'nda değişiklikler üst düzey genel bakış

Bu belgede taşıma ile ilişkili değişiklikler açıklanmaktadır *project.json* MSBuild ve *csproj* proje sistemi ile .NET Core Araçları'nın katmanlarını değişiklikler hakkında bilgi ve CLI komutlarını uygulaması. Bu değişiklikler 7 Mart 2017'de .NET Core SDK'sı 1.0 ve Visual Studio 2017 sürümüyle (bkz [duyuru](https://devblogs.microsoft.com/dotnet/announcing-net-core-tools-1-0/)) .NET Core SDK Preview 3'ın yayınlanmasıyla birlikte başlangıçta uygulandığına ancak.

## <a name="moving-away-from-projectjson"></a>Project.JSON uzağa taşınması
Büyük .NET Core Araçları'nda kesinlikle değişikliktir [uzağa project.json csproj'a geçirilmesi taşıma](https://devblogs.microsoft.com/dotnet/changes-to-project-json/) proje sistemi olarak. Komut satırı araçlarının son sürümleri desteklemeyen *project.json* dosyaları. Bu, oluşturmak, çalıştırmak veya project.json tabanlı uygulamaları ve kitaplıkları yayımlamak için kullanılamaz anlamına gelir. Araçlar'ın bu sürümü kullanmak için mevcut projelerinizi geçirme veya yenilerini başlatmak gerekir. 

Bu taşıma işleminin bir parçası olarak, project.json projeleri derlemek için geliştirilmiş özel yapı altyapısı adlı bir yetişkin ve tam özellikli derleme altyapısıyla değiştirildi [MSBuild](https://github.com/Microsoft/msbuild). Platformun ilk sürümünden sonra anahtar teknoloji edildiğinden MSBuild .NET topluluğundaki iyi bilinen bir altyapısıdır. Elbette, .NET Core uygulamaları gerektiğinden, MSBuild .NET Core için unity'nin ve .NET Core üzerinde çalışan herhangi bir platformda kullanılabilir. .NET Core ana gösterir, platformlar arası geliştirme yığınını biridir ve yaptık Bu taşıma, promise bozmadığından emin.

> [!NOTE]
> MSBuild için yeni ve daha fazla bilgi edinmek istiyorsanız, okuyarak başlayabilirsiniz [MSBuild kavramları](/visualstudio/msbuild/msbuild-concepts) makalesi. 

## <a name="the-tooling-layers"></a>Araç katmanları
Mevcut proje sistemi uzağa taşıma ile sıra altyapısı anahtarları oluşturma ile bu değişikliklerin herhangi biri tüm .NET Core araçları ekosisteminin genel "katman" değiştirme doğal olarak aşağıdaki soru mi? Yeni güncelleştirmeleri ve bileşenler var mıdır?

Preview 2 katmanlama hızlı tazelemek aşağıdaki resimde gösterildiği gibi başlayalım:

![Önizleme 2 araçları üst düzey mimarisi](media/cli-msbuild-architecture/p2-arch.png)

Katman Araçları'nın oldukça basittir. Altta bir temel .NET Core komut satırı araçlarını sahibiz. Visual Studio veya Visual Studio Code, bağımlı ve projeleri oluşturmak için CLI kullanan gibi tüm üst düzey, diğer araçları bağımlılıkları vb. geri yükleyin. Bu Visual Studio geri yükleme işlemi gerçekleştirmek istiyorsanız, örneğin, bunu içine çağıracak, geliyordu `dotnet restore` ([bkz. Not](#dotnet-restore-note)) CLI komutu. 

Yeni Proje sistemi için taşıma ile önceki diyagramda değişiklikler: 

![.NET core SDK'sı 1.0.0 üst düzey mimarisi](media/cli-msbuild-architecture/p3-arch.png)

İkisi arasındaki temel fark CLI temel katman artık olmamasıdır; Bu rol artık "paylaşılan SDK'sı bileşeni" tarafından doldurulur. Bu paylaşılan SDK'sı bileşeni, hedef ve kodunuzu derlemek, yayımlamak, NuGet paketleri vb. paketleme sorumlu olan ilişkili görevleri kümesidir. SDK açık kaynaklıdır ve Github'da üzerinde kullanılabilir [SDK deposuna](https://github.com/dotnet/sdk). 

> [!NOTE]
> Bir "hedef" MSBuild çağırabilirsiniz adlandırılmış bir işlemi belirten MSBuild bir terimdir. Bu genellikle hedef yapmak için gereken bazı mantığı yürütülen bir veya daha fazla görevleri ile birleştirilmiştir. MSBuild destekleyen çok sayıda kullanıma hazır hedefleri gibi `Copy` veya `Execute`; Ayrıca kullanıcıların kendi görevlerini kullanarak yönetilen kod yazma ve bu görevlerin yürütülmek üzere hedef tanımlamanızı sağlar. Daha fazla bilgi için [MSBuild görevleri](/visualstudio/msbuild/msbuild-tasks). 

Tüm takımları artık paylaşılan SDK'sı bileşeni ve CLI dahil hedeflerine kullanır. Örneğin, Visual Studio'nun yeni sürümü içine beklenmeyeni çağırmaz `dotnet restore` ([bkz. Not](#dotnet-restore-note)) .NET Core projeleri için bağımlılıkları geri yüklemek için komut, "Geri" hedef doğrudan kullanır. Bu MSBuild hedefleri olduğundan, ayrıca ham MSBuild çalıştırmak için kullanabileceğiniz kullanarak [dotnet msbuild](dotnet-msbuild.md) komutu. 

### <a name="cli-commands"></a>CLI komutları
Paylaşılan SDK'sı bileşeni mevcut CLI komutları çoğunu olduğunu yeniden uygulanan MSBuild görevleri ve hedefleri anlamına gelir. Bu CLI komutlarına ve araç kullanım için anlamı nedir? 

Kullanım açısından bakıldığında, bunu CLI kullanma biçimini değiştirmez. CLI, Preview 2 sürümünde mevcut çekirdek komutları hala sahiptir:

* `new`
* `restore`
* `run` 
* `build`
* `publish`
* `test`
* `pack` 

Bu komutları hala bunları (yeni bir proje oluşturun, yayımlayın, vb. paketi için) beklediğiniz şeyi. Seçenekler çoğunluğu değiştirilmez ve halen oradadırlar ve ya da komutları Yardım ekranları başvurabilirsiniz (kullanarak `dotnet <command> --help`) veya herhangi bir değişiklik hakkında bilgi edinmek için bu sitede belgeleri. 

Yürütme açısından bakıldığında, CLI komutları, parametre ve gerekli özellikleri ayarlayın ve istediğiniz hedef Çalıştır "ham" MSBuild bir çağrı oluşturur. Bu daha iyi anlamak için aşağıdaki komutu göz önünde bulundurun: 

   `dotnet publish -o pub -c Release`
    
Bu komut, bir uygulamayı yayımlama bir `pub` klasörü "Sürüm" yapılandırmasını kullanarak. Dahili olarak, bu komutu aşağıdaki MSBuild çağrısına çevrilir: 

   `dotnet msbuild -t:Publish -p:OutputPath=pub -p:Configuration=Release`

Bu kural için önemli olan özel durumdur `new` ve `run` komutları gibi MSBuild hedefleri henüz geliştirilmemiştir.

<a name="dotnet-restore-note"></a>  
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
