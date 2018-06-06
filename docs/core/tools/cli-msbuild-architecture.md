---
title: .NET core komut satırı araçları mimarisi
description: Katman ve son sürümlerde nelerin değiştiğini tooling .NET Core hakkında bilgi edinin.
author: blackdwarf
ms.date: 03/06/2017
ms.openlocfilehash: 1d96a0b1e19bf84af0ab645ebd104afc899ae656
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696549"
---
# <a name="high-level-overview-of-changes-in-the-net-core-tools"></a>.NET Core araçları değişiklikleri üst düzey genel bakış

Bu belgede taşıma ile ilişkili değişiklikler açıklanmaktadır *project.json* MSBuild ve *csproj* proje .NET Core araç katmanlarını değişiklikler hakkında bilgi içeren sistem ve CLI komutları uygulamasıdır. Bu değişiklikler 7 Mart 2017 üzerinde .NET Core SDK 1.0 ve Visual Studio 2017 sürümünden (bkz [duyuru](https://blogs.msdn.microsoft.com/dotnet/2017/03/07/announcing-net-core-tools-1-0/)) .NET Core SDK Preview 3 sürümü başlangıçta uygulanan ancak.

## <a name="moving-away-from-projectjson"></a>Project.JSON çıktığınızda taşıma
.NET Core araç en büyük değişiklik kesinlikle olan [project.json çıktığınızda csproj için taşıma](https://blogs.msdn.microsoft.com/dotnet/2016/05/23/changes-to-project-json/) proje sistemi olarak. Komut satırı araçlarını en son sürümlerini desteklemeyen *project.json* dosyaları. Bu yapı, çalıştırmak veya project.json tabanlı uygulamalar ve kitaplıklar yayımlamak için kullanılamaz anlamına gelir. Bu araçların sürümü kullanmak için varolan projelerinizi geçirmek veya yenilerini başlatmak gerekir. 

Bu taşıma işleminin bir parçası olarak, project.json projeleri oluşturmak üzere geliştirilmiştir özel yapı altyapısı adlı bir yetişkin ve tam özellikli yapı altyapısı ile değiştirilen [MSBuild](https://github.com/Microsoft/msbuild). Platformun ilk sürümünden bu yana bir anahtar teknolojisi edildiğinden MSBuild .NET topluluğundaki iyi bilinen bir altyapıdır. Elbette, .NET Core uygulamaları geliştirmek gerektiğinden MSBuild .NET Core bağlantı noktalı ve .NET Core üzerinde çalışan herhangi bir platformda kullanılabilir. .NET Core, ana öneriler, platformlar arası geliştirme yığınının biridir ve biz Bu taşıma o promise bozmadığından emin yaptınız.

> [!NOTE]
> MSBuild için yenidir ve hakkında daha fazla bilgi edinmek istiyorsanız okuyarak başlatabilirsiniz [MSBuild kavramları](/visualstudio/msbuild/msbuild-concepts) makalesi. 

## <a name="the-tooling-layers"></a>Araç katmanları
Var olan proje sistemi uzakta olan yanı sıra altyapısı anahtarları oluşturma ile bu değişiklikleri genel "katmanlarını" tüm .NET Core araç ekosistemi değiştirme doğal olarak izleyen soru mi? Yeni BITS ve bileşenleri bulunur?

Önizleme 2 katmanlama hızlı bir Yenileyici ile aşağıdaki resimde gösterildiği gibi başlayalım:

![Önizleme 2 araçları üst düzey mimarisi](media/cli-msbuild-architecture/p2-arch.png)

Araçlar katmanlama oldukça basittir. Sayfanın alt tarafında bir temel .NET Core komut satırı araçlarını sahibiz. Visual Studio veya Visual Studio Code bağlıdır ve projeler, derlemek için CLI kullanır gibi tüm diğer, üst düzey araçları bağımlılıkları vb. geri yükleyin. Bu geri yükleme işlemi gerçekleştirmek Visual Studio istediyseniz, örneğin, bunu içine çağırırdı, geliyordu `dotnet restore` ([bkz. Not](#dotnet-restore-note)) CLI komutu. 

Yeni Proje sistemine taşıma ile önceki diyagramda değiştirir: 

![.NET core SDK 1.0.0 üst düzey mimari](media/cli-msbuild-architecture/p3-arch.png)

İkisi arasındaki temel fark CLI temel katmanı artık olmamasıdır; Bu rol artık "paylaşılan SDK component" girilir. Bu paylaşılan SDK bileşeni hedefler ve kodunuzu derlerken yayımlamadan, NuGet paketleri vb. sevk için sorumlu olan ilişkili görevler kümesidir. SDK açık kaynaklıdır ve Github'da üzerinde kullanılabilir [SDK depodaki](https://github.com/dotnet/sdk). 

> [!NOTE]
> "Hedef" MSBuild çağırabileceği adlandırılmış bir işlemi belirten MSBuild bir terimdir. Bu, genellikle hedef yapmak için gereken bazı mantığı yürütmek bir veya daha fazla görevleri ile birleştirilmiştir. MSBuild destekleyen birçok hazır hedefleri gibi `Copy` veya `Execute`; Ayrıca kullanıcıların yönetilen kodu kullanarak kendi Görevler yazmak ve bu görevleri çalıştırmak için hedeflerini tanımlamak imkan tanır. Daha fazla bilgi için bkz: [MSBuild görevleri](/visualstudio/msbuild/msbuild-tasks). 

Tüm toolsets şimdi paylaşılan SDK bileşeni ve dahil CLI hedeflerine kullanabilir. Örneğin, Visual Studio'nun bir sonraki sürümünün içine çağırmayacaktır `dotnet restore` ([bkz. Not](#dotnet-restore-note)) .NET Core projeleri için bağımlılıkları geri yüklemek için komut, "Geri yükleme" hedef doğrudan kullanır. MSBuild hedefleri bunlar olduğundan, ayrıca ham MSBuild bunları yürütmek için kullanabileceğiniz kullanarak [dotnet msbuild](dotnet-msbuild.md) komutu. 

### <a name="cli-commands"></a>CLI komutları
Paylaşılan SDK bileşen mevcut CLI komutları çoğunluğu olduğunu yeniden uygulanan MSBuild görevleri ve hedefleri anlamına gelir. Bu ne CLI komutları ve araç takımı kullanımınızı için anlama geliyor? 

Kullanım açısından bakıldığında, CLI kullanımınızı değiştirmez. CLI hala Preview 2 sürümünde mevcut çekirdek komutlar vardır:

* `new`
* `restore`
* `run` 
* `build`
* `publish`
* `test`
* `pack` 

Bu komutlar hala kendisine (yeni bir projeyi, derleme, bu yayımlama, vb. paketi) beklediğiniz yapın. Seçenekleri çoğunluğu değiştirilmez ve hala vardır ve her iki komutları Yardım ekranları başvurabilirsiniz (kullanarak `dotnet <command> --help`) veya herhangi bir değişiklikle hakkında bilgi edinmek için bu sitesindeki belgeleri. 

Yürütme açısından bakıldığında, CLI komutları parametrelerini alın ve gerekli özellikleri ayarlayın ve istenen hedef Çalıştır "ham" MSBuild çağrısına oluşturun. Bu daha iyi anlamak için aşağıdaki komutu göz önünde bulundurun: 

   `dotnet publish -o pub -c Release`
    
Bu komut, bir uygulamayı yayımlama bir `pub` "Yayın" Yapılandırması'nı kullanarak klasör. Dahili olarak, bu komutu aşağıdaki MSBuild çağırma çevrilen: 

   `dotnet msbuild /t:Publish /p:OutputPath=pub /p:Configuration=Release`

Bu kural için önemli özel durumdur `new` ve `run` bunlar MSBuild hedefleri olarak henüz geliştirilmemiştir gibi komutları.

<a name="dotnet-restore-note"></a>  
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
