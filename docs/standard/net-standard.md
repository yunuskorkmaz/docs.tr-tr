---
title: .NET Standard
description: .NET Standard, sürümleri ve onu destekleyen .NET uygulamaları hakkında bilgi edinin.
ms.date: 02/13/2020
ms.technology: dotnet-standard
ms.custom: updateeachrelease
ms.assetid: c044882c-af15-45f2-96d1-534557a5ee9b
ms.openlocfilehash: e6e573056132c25b912ff1eb76b9b055f6e47cfe
ms.sourcegitcommit: 2ff49dcf9ddf107d139b4055534681052febad62
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/31/2020
ms.locfileid: "80438213"
---
# <a name="net-standard"></a>.NET Standard

[.NET Standardı,](https://github.com/dotnet/standard) .NET'in tüm uygulamalarında bulunması amaçlanan .NET API'lerinin resmi bir belirtimidir. .NET Standard'ın arkasındaki motivasyon,.NET ekosisteminde daha fazla tekdüzelik oluşturmaktır. [ECMA 335](https://github.com/dotnet/runtime/blob/master/docs/project/dotnet-standards.md) .NET uygulama davranışı için tekdüzelik oluşturmaya devam ediyor ve ECMA 335 küçük bir standart kitaplık kümesi belirtirken, .NET Standart belirtimi daha geniş bir .NET API'sini kapsar.

.NET Standard aşağıdaki anahtar senaryoları sağlar:

- İş yükünden bağımsız olarak uygulanacak tüm .NET uygulamaları için tek tip BCL API'ları tanımlar.
- Geliştiricilerin aynı API kümesini kullanarak .NET uygulamalarında kullanılabilir taşınabilir kitaplıklar oluşturmasına olanak tanır.
- Sadece OS API'leri için .NET API'leri nedeniyle paylaşılan kaynağın koşullu derlemesini azaltır veya ortadan kaldırır.

Çeşitli .NET uygulamaları .NET Standard'ın belirli sürümlerini hedeflemaktadır. Her .NET uygulama sürümü, desteklediği en yüksek .NET Standart sürümünün reklamını, önceki sürümleri de desteklediği anlamına gelen bir bildirimdir. Örneğin, .NET Framework 4.6 .NET Standart 1.3'u uygular, bu da .NET Standart sürümleri 1.0 ile 1.3 arasında tanımlanan tüm API'leri ortaya çıkardığı anlamına gelir. Benzer şekilde,.NET Framework 4.6.1 .NET Standard 1.4'u uygularken.NET Core 1.0 .NET Standard 1.6'yı uygular.

## <a name="net-implementation-support"></a>.NET uygulama desteği

Aşağıdaki tabloda, her .NET Standart sürümünü destekleyen **minimum** platform sürümleri listeleilmektedir. Bu, listelenen bir platformun sonraki sürümlerinin ilgili .NET Standart sürümünü de desteklediği anlamına gelir. Örneğin, .NET Core 2.2 .NET Standard 2.0 ve daha önce destekler.

[!INCLUDE [net-standard-table](../../includes/net-standard-table.md)]

.NET Standard'ın hedeflediğiniz en yüksek sürümünü bulmak için aşağıdaki adımları yapın:

1. Çalıştırmak istediğiniz .NET uygulamasını gösteren satırı bulun.
2. Sağdan sola başlayarak sürümünüzü gösteren bu satırdaki sütunu bulun.
3. Sütun üstbilgi, hedefinizin desteklediği .NET Standart sürümünü gösterir. Ayrıca daha düşük .NET Standart sürümünü de hedefabilirsiniz. Daha yüksek .NET Standart sürümleri de uygulamanızı destekleyecektir.
4. Hedeflemek istediğiniz her platform için bu işlemi tekrarlayın. Birden fazla hedef platformunuz varsa, aralarındaki daha küçük sürümü seçmelisiniz. Örneğin, .NET Framework 4.5 ve .NET Core 1.0 üzerinde çalışmak istiyorsanız, kullanabileceğiniz en yüksek .NET Standart sürümü .NET Standart 1.1'dir.

### <a name="which-net-standard-version-to-target"></a>Hangi .NET Standart sürümü hedef

.NET Standart sürümünü seçerken, şu değiş tokuşu göz önünde bulundurmalısınız:

- Sürüm ne kadar yüksekse, o kadar çok API kullanılabilir.
- Sürüm ne kadar düşükse, o kadar çok platform uygular.

Genel olarak, .NET Standard'ın mümkün olan *en düşük* sürümünü hedeflemenizi öneririz. Bu nedenle, hedeflenebildiğiniz en yüksek .NET Standart sürümünü bulduktan sonra aşağıdaki adımları izleyin:

1. .NET Standard'ın bir sonraki alt sürümünü hedefle ve projenizi oluşturun.
2. Projeniz başarıyla inşa edilirse, adım 1'i yineleyin. Aksi takdirde, bir sonraki yüksek sürüme yeniden hedeflemek ve kullanmanız gereken sürüm bu.

Ancak, daha düşük .NET Standart sürümlerini hedeflemek bir dizi destek bağımlılığı sunar. Projeniz .NET Standart 1.x'i hedefliyorsa, .NET Standart 2.0'ı *da* hedeflemenizi öneririz. Bu, .NET Standart 2.0 uyumlu çerçevelerde çalışan kitaplığınızın kullanıcıları için bağımlılık grafiğini basitleştirir ve karşıdan yüklemeleri gereken paket sayısını azaltır.

### <a name="net-standard-versioning-rules"></a>.NET Standart sürüm kuralları

İki temel sürüm kuralı vardır:

- Katkı: .NET Standart sürümleri mantıksal olarak eşmerkezli dairelerdir: daha yüksek sürümler önceki sürümlerden tüm API'leri içerir. Sürümler arasında herhangi bir kırılma değişiklik yoktur.
- Değişmez: Sevk edildikten sonra ,NET Standart sürümleri dondurulur. Yeni API'ler ilk olarak .NET Core gibi belirli .NET uygulamalarında kullanılabilir hale gelir. .NET Standard inceleme kurulu, yeni API'lerin tüm .NET uygulamaları için kullanılabilir olması gerektiğine inanıyorsa, bunlar yeni bir .NET Standart sürümüne eklenir.

## <a name="specification"></a>Belirtim

.NET Standart belirtimi standartlaştırılmış bir API kümesidir. Belirtim ,NET uygulayıcıları, özellikle Microsoft (.NET Framework, .NET Core ve Mono içerir) ve Unity tarafından korunur. Ortak geri bildirim [işlemi, GitHub](https://github.com/dotnet/standard)üzerinden yeni .NET Standart sürümlerioluşturmanın bir parçası olarak kullanılır.

### <a name="official-artifacts"></a>Resmi eserler

Resmi belirtim, standardın bir parçası olan API'leri tanımlayan bir .cs dosyaları kümesidir. [Dotnet/standart deposundaki](https://github.com/dotnet/standard) [ref dizini](https://github.com/dotnet/standard/tree/master/src/netstandard/ref) .NET Standart API'leri tanımlar.

[NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) metapackage[(kaynak)](https://github.com/dotnet/standard/blob/master/src/netstandard/pkg/NETStandard.Library.dependencies.props)(kısmen) bir veya daha fazla .NET Standart sürümleri tanımlayan kitaplıkkümesi açıklar.

Belirli bir bileşen, gibi `System.Runtime`, açıklar:

- .NET Standard'ın bir parçası (sadece kapsamı).
- Bu kapsam için .NET Standard'ın birden çok sürümü.

Türev yapılar daha rahat okuma sağlamak ve belirli geliştirici senaryoları (örneğin, bir derleyici kullanarak) etkinleştirmek için sağlanır.

- [İşaretledeki API listesi](https://github.com/dotnet/standard/tree/master/docs/versions)
- [NuGet paketleri](../core/packages.md) olarak dağıtılan ve [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library/) meta paketi tarafından başvurulan referans derlemeleri.

### <a name="package-representation"></a>Paket gösterimi

.NET Standart referans montajları için birincil dağıtım aracı [NuGet paketleridir.](../core/packages.md) Uygulamalar, her .NET uygulaması için uygun çeşitli şekillerde teslim edilir.

NuGet paketleri bir veya daha fazla [çerçeveyi hedefalır.](frameworks.md) .NET Standart paketleri ".NET Standard" çerçevesini hedeflemektedir. .NET Standart çerçevesini kompakt `netstandard` [TFM'yi](frameworks.md) kullanarak `netstandard1.4`(örneğin) hedefleyebilirsiniz. Birden çok çalışma zamanında çalışması amaçlanan kitaplıklar bu çerçeveyi hedeflemelidir. En geniş API kümesi için, mevcut API sayısı .NET Standart 1.6 ve 2.0 arasında iki kattan fazla olduğundan hedef. `netstandard2.0`

Meta [`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library/) paket, .NET Standard'ı tanımlayan NuGet paketlerinin tamamına başvurur.  Hedeflemenin `netstandard` en yaygın yolu bu meta pakete başvurmaktır. ~40 .NET kitaplıklarını ve .NET Standardını tanımlayan ilişkili API'leri açıklar ve bunlara erişim sağlar. Ek API'lere `netstandard` erişmek için hedefleyen ek paketlere başvurulayabilirsiniz.

### <a name="versioning"></a>Sürüm Oluşturma

Belirtim tekil değil, artımlı olarak büyüyen ve doğrusal olarak sürümlenmiş API'ler kümesidir. Standardın ilk sürümü, bir temel API kümesi belirler. Sonraki sürümler API'ler ekler ve önceki sürümler tarafından tanımlanan API'leri devralır. API'lerin standarttan kaldırılması için belirlenmiş bir hüküm yoktur.

.NET Standardı herhangi bir .NET uygulamasına özgü değildir ve bu çalışma sürelerinden herhangi birinin sürüm şemasıyla eşleşmiyor.

Uygulamalardan herhangi biri (.NET Framework, .NET Core ve Mono gibi) eklenen API'ler, özellikle doğada temel oldukları düşünülse, şartnameye eklenecek aday lar olarak kabul edilebilir. [.NET Standard'ın](https://github.com/dotnet/standard/blob/master/docs/versions.md) yeni sürümleri .NET uygulama sürümlerine göre oluşturulur ve böylece yeni API'leri .NET Standart PCL'den hedeflemenize olanak sağlar. Sürüm mekaniği [.NET Çekirdek Sürüm'de](../core/versions/index.md)daha ayrıntılı olarak açıklanmıştır.

.NET Standart sürüm kullanımı için önemlidir. Bir .NET Standart sürümü göz önüne alındığında, aynı veya daha düşük sürümü hedefleyen kitaplıkları kullanabilirsiniz. Aşağıdaki yaklaşım, .NET Standart hedeflemesine özgü .NET Standart PCL'leri kullanmak için iş akışını açıklar.

- PCL'niz için kullanmak üzere bir .NET Standart sürümü seçin.
- Aynı .NET Standart sürümüne veya daha düşük olan kitaplıkları kullanın.
- Daha yüksek bir .NET Standart sürümüne bağlı bir kitaplık bulursanız, aynı sürümü benimsemeniz veya bu kitaplığı kullanmamaya karar vermeniz gerekir.

## <a name="target-net-standard"></a>Hedef .NET Standardı

[.NET Standart Kitaplıklar](../core/tutorials/libraries.md) çerçeve ve `netstandard` NETStandard.Library metapaketinin bir birleşimini kullanarak oluşturabilirsiniz. [.NET Core araçları ile .NET Standard hedefleme](../core/packages.md)örneklerini görebilirsiniz.

## <a name="net-framework-compatibility-mode"></a>.NET Framework uyumluluk modu

.NET Standard 2.0 ile başlayarak .NET Framework uyumluluk modu tanıtıldı. Bu uyumluluk modu ,NET Standard projelerinin .NET Framework kitaplıklarına .NET Standard için derlenmiş gibi başvurmalarını sağlar. .NET Framework kitaplıklarına başvurmak, Windows Sunu Temeli (WPF) API'lerini kullanan kitaplıklar gibi tüm projelerde işe yaramaz.

Daha fazla bilgi için [.NET Framework uyumluluk moduna](../core/porting/third-party-deps.md#net-framework-compatibility-mode)bakın.

## <a name="net-standard-libraries-and-visual-studio"></a>.NET Standart kütüphaneler ve Görsel Stüdyo

Visual Studio'da .NET Standard kitaplıkları oluşturmak için Visual [Studio 2017 sürüm 15.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) veya daha sonra Windows'da veya [Mac sürüm 7.1 için Visual Studio](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) veya daha sonra macOS'ta yüklü olduğundan emin olun.

Projelerinizde .NET Standard 2.0 kitaplıklarını yalnızca tüketmeniz gerekiyorsa, bunu Visual Studio 2015'te de yapabilirsiniz. Ancak, NuGet istemci3.6 veya daha yüksek yüklü gerekir. Visual Studio 2015 için NuGet istemcisini [NuGet indirme sayfasından](https://www.nuget.org/downloads) indirebilirsiniz.

## <a name="comparison-to-portable-class-libraries"></a>Taşınabilir Sınıf Kitaplıkları ile karşılaştırma

.NET Standardı, [Taşınabilir Sınıf Kitaplıkları 'nın (PCL)](./cross-platform/cross-platform-development-with-the-portable-class-library.md)yerini alır. .NET Standard, standart bir BCL'yi küratörlük ederek ve sonuç olarak .NET uygulamalarında daha fazla tekdüzelik oluşturarak taşınabilir kitaplıklar oluşturma deneyimini geliştirir. .NET Standard'ı hedefleyen bir kitaplık BIR PCL veya ".NET Standart tabanlı PCL"dir. Mevcut PCL'ler "profil tabanlı PCL'lerdir".

.NET Standart ve PCL profilleri benzer amaçlariçin oluşturulmuştur, ancak aynı zamanda önemli şekillerde farklılık gösterir.

Benzerlik:

- İkili kod paylaşımı için kullanılabilecek API'leri tanımlayın.

Farklılık -lar:

- .NET Standard, PCL profilleri varolan platformların kesişmelerle tanımlanırken, seçilmiş bir API kümesidir.
- .NET Standart doğrusal sürümler, PCL profilleri ise yok.
- PCL profilleri Microsoft platformlarını temsil ederken .NET Standard platform-agnostiktir.

### <a name="pcl-compatibility"></a>PCL uyumluluğu

.NET Standard, PCL profillerinin bir alt kümesiyle uyumludur. .NET Standart 1.0, 1.1 ve 1.2 her PCL profilleri bir dizi çakışıyor. Bu çakışma iki nedenden dolayı oluşturuldu:

- Profil tabanlı PCL'lere başvurmak için .NET Standart tabanlı PCL'leri etkinleştirin.
- Profil tabanlı PCL'lerin .NET Standart tabanlı PCL'ler olarak paketlemesini etkinleştirin.

Profil tabanlı PCL uyumluluğu [Microsoft.NETCore.Portable.Compatibility](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) NuGet paketi tarafından sağlanır. Profil tabanlı PCL'ler içeren NuGet paketlerine başvururken bu bağımlılık gereklidir.

Genellikle paketlenmiş profil tabanlı PCL'lere göre daha kolay olarak paketlenmiş `netstandard` profil tabanlı PCL'ler. `netstandard`ambalajı mevcut kullanıcılarla uyumludur.

.NET Standardı ile uyumlu PCL profilleri kümesini görebilirsiniz:

| PCL Profil | .NET Standard | PCL Platformları
|:-----------:|:-------------:|------------------------------------------------------------------------------
| Profil7    | 1.1           | .NET Framework 4.5, Windows 8
| Profil31   | 1.0           | Windows 8.1, Windows Phone Silverlight 8.1
| Profil32   | 1.2           | Windows 8.1, Windows Phone 8.1
| Profil44   | 1.2           | .NET Framework 4.5.1, Windows 8.1
| Profil49   | 1.0           | .NET Framework 4.5, Windows Phone Silverlight 8
| Profil78   | 1.0           | .NET Framework 4.5, Windows 8, Windows Phone Silverlight 8
| Profil84   | 1.0           | Windows Phone 8.1, Windows Phone Silverlight 8.1
| Profil111  | 1.1           | .NET Framework 4.5, Windows 8, Windows Phone 8.1
| Profil151  | 1.2           | .NET Framework 4.5.1, Windows 8.1, Windows Phone 8.1
| Profil157  | 1.0           | Windows 8.1, Windows Phone 8.1, Windows Phone Silverlight 8.1
| Profil259  | 1.0           | .NET Framework 4.5, Windows 8, Windows Phone 8.1, Windows Phone Silverlight 8

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Standart Versiyonları](https://github.com/dotnet/standard/blob/master/docs/versions.md)
- [Bir .NET Standart kitaplığı oluşturma](../core/tutorials/library-with-visual-studio.md)
- [Platformlar arası hedefleme](./library-guidance/cross-platform-targeting.md)
