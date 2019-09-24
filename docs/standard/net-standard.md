---
title: .NET Standard
description: .NET Standard, sürümleri ve bunu destekleyen .NET uygulamaları hakkında bilgi edinin.
author: mairaw
ms.author: mairaw
ms.date: 09/23/2019
ms.technology: dotnet-standard
ms.custom: updateeachrelease
ms.assetid: c044882c-af15-45f2-96d1-534557a5ee9b
ms.openlocfilehash: 026224ca2941e7694fc1b80939e6d283d75db32e
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214443"
---
# <a name="net-standard"></a>.NET Standard

[.NET Standard](https://github.com/dotnet/standard) , tüm .NET uygulamalarında kullanılabilmesi amaçlanan .NET API 'lerinin resmi bir belirtimidir. .NET Standard arkasındaki mosyon, .NET ekosisteminde daha büyük bir birlik oluşturur. [ECMA 335](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md) , .NET uygulama davranışı için birlik özelliği oluşturmaya devam etmektedir, ancak .NET kitaplığı uygulamalarına yönelik .net temel sınıf KITAPLıKLARı (BCL) için benzer bir belirtim yoktur.

.NET Standard aşağıdaki temel senaryolara izin vermez:

- İş yüküyle bağımsız olarak uygulanacak tüm .NET uygulamaları için tek bir BCL API kümesini tanımlar.
- Geliştiricilerin aynı API kümesi kullanılarak .NET uygulamalarında kullanılabilir olan taşınabilir kitaplıklar oluşturmasını sağlar.
- .NET API 'leri, yalnızca OS API 'Leri için, paylaşılan kaynağın koşullu derlemesini azaltır veya ortadan kaldırır.

Çeşitli .NET uygulamaları .NET Standard belirli sürümlerini hedefleyin. Her .NET uygulama sürümü, desteklediği en yüksek .NET Standard sürümünü tanıtır, yani önceki sürümleri de destekler. Örneğin .NET Framework 4,6, .NET Standard 1,3 ' i uygular, yani .NET Standard sürümler 1,0 içinde tanımlanan tüm API 'Leri 1,3 aracılığıyla gösterir. Benzer şekilde, .NET Framework 4.6.1 .NET Standard 1,4 uygular, ancak .NET Core 1,0 .NET Standard 1,6 uygular.

## <a name="net-implementation-support"></a>.NET uygulama desteği

Aşağıdaki tabloda, her bir .NET Standard sürümünü destekleyen **En düşük** platform sürümleri listelenmektedir. Diğer bir deyişle, listelenen bir platformun sonraki sürümlerinin de karşılık gelen .NET Standard sürümü destekleyeceği anlamına gelir. Örneğin, .NET Core 2,2 .NET Standard 2,0 ve öncesini destekler.

[!INCLUDE [net-standard-table](../../includes/net-standard-table.md)]

Hedeflenebilen .NET Standard en yüksek sürümünü bulmak için aşağıdaki adımları uygulayın:

1. Üzerinde çalışmak istediğiniz .NET uygulamasını gösteren satırı bulun.
2. Bu satırdaki, sürümünüzü sağdan sola başlayarak gösteren sütunu bulun.
3. Sütun üst bilgisi, hedefin desteklediği .NET Standard sürümünü belirtir. Ayrıca, daha düşük .NET Standard sürümleri de hedefleyebilirsiniz. Daha yüksek .NET Standard sürümler de Uygulamanızı destekleyecektir.
4. Hedeflemek istediğiniz her platform için bu işlemi tekrarlayın. Birden fazla hedef platformunuz varsa, bunların arasından daha küçük bir sürüm seçmeniz gerekir. Örneğin, .NET Framework 4,5 ve .NET Core 1,0 ' de çalıştırmak istiyorsanız kullanabileceğiniz en yüksek .NET Standard sürümü .NET Standard 1,1.

### <a name="which-net-standard-version-to-target"></a>Hedeflenecek .NET Standard sürümü

.NET Standard bir sürüm seçerken, bu ticareti göz önünde bulundurmanız gerekir:

- Sürüm arttıkça, diğer API 'Ler sizin için de kullanılabilir.
- Sürüm ne kadar düşükse, o kadar çok platform bunu uygular.

Genel olarak, mümkün olan *En düşük* sürümü .NET Standard hedeflemesini öneririz. Bu nedenle, hedeflenebilen en yüksek .NET Standard sürümünü bulduktan sonra aşağıdaki adımları izleyin:

1. .NET Standard sonraki alt sürümünü hedefleyin ve projenizi derleyin.
2. Projeniz başarıyla oluşturul, 1. adımı yineleyin. Aksi takdirde, sonraki daha yüksek sürüme yeniden hedefleyin ve kullanmanız gereken sürümdür.

Ancak, daha düşük .NET Standard sürümleri hedeflemek çok sayıda destek bağımlılığı sunar. Projeniz .NET Standard 1. x hedefliyorsa, ayrıca .NET Standard 2,0 ' i *de* hedeflediğiniz önerilir. Bu, kitaplığınızın .NET Standard 2,0 uyumlu çerçeveler üzerinde çalışan kullanıcıları için bağımlılık grafiğini basitleştirir ve İndirmeleri gereken paket sayısını azaltır.

### <a name="net-standard-versioning-rules"></a>.NET Standard sürüm oluşturma kuralları

İki birincil sürüm oluşturma kuralı vardır:

- Eklenebilir: .NET Standard sürümler mantıksal olarak eşmerkezli daireler: daha yüksek sürümler önceki sürümlerden tüm API 'Leri dahil. Sürümler arasında hiç Son değişiklik yok.
- Değişmez Sevk edildiğinde .NET Standard sürümler dondurulur. Yeni API 'Ler öncelikle .NET Core gibi belirli .NET uygulamalarında kullanılabilir hale gelir. .NET Standard gözden geçirme panosu, tüm .NET uygulamalarında yeni API 'Lerin kullanılabilir olması gerektiğini düşünürsa, yeni bir .NET Standard sürümüne eklenir.

## <a name="specification"></a>Min

.NET Standard belirtimi, standartlaştırılmış bir API kümesidir. Belirtim .NET uygulayıcılar tarafından, özellikle Microsoft (.NET Framework, .NET Core ve mono dahil) ve Unity tarafından korunur. [GitHub](https://github.com/dotnet/standard)aracılığıyla yeni .NET Standard sürümlerini oluşturma işleminin parçası olarak genel geri bildirim işlemi kullanılır.

### <a name="official-artifacts"></a>Resmi yapılar

Resmi belirtimi, standart bir parçası olan API 'Leri tanımlayan bir. cs dosyası kümesidir. [DotNet/standart deposundaki](https://github.com/dotnet/standard) [ref dizini](https://github.com/dotnet/standard/tree/master/src/netstandard/ref) .NET Standard API 'leri tanımlar.

[Netstandard. Library](https://www.nuget.org/packages/NETStandard.Library) meta paketi ([kaynak](https://github.com/dotnet/standard/blob/master/src/netstandard/pkg/NETStandard.Library.dependencies.props)) bir veya daha fazla .NET Standard sürümünde tanımlayan kitaplıklar kümesini açıklar.

Şunun gibi `System.Runtime`belirli bir bileşen şunları açıklar:

- .NET Standard (yalnızca kapsamı) bir parçasıdır.
- Bu kapsam için birden çok .NET Standard sürümü.

Türetilmiş yapıtlar, daha kolay okunması ve belirli geliştirici senaryolarına olanak tanımak için sağlanır (örneğin, bir derleyici kullanarak).

- [Markın içindeki API listesi](https://github.com/dotnet/standard/tree/master/docs/versions)
- [NuGet paketleri](../core/packages.md) olarak dağıtılan ve [Netstandard. Library](https://www.nuget.org/packages/NETStandard.Library/) metapackage tarafından başvurulan başvuru derlemeleri.

### <a name="package-representation"></a>Paket temsili

.NET Standard başvuru derlemelerinin birincil dağıtım aracı [NuGet paketlerdir](../core/packages.md). Uygulamalar, her .NET uygulaması için uygun olan çeşitli yollarla dağıtılır.

NuGet paketleri bir [veya daha fazla](frameworks.md)çerçeveyi hedeflemelidir. .NET Standard paketleri ".NET Standard" çerçevesini hedefleyin. `netstandard` [Compact TFI](frameworks.md) kullanarak .NET Standard çerçevesini hedefleyebilirsiniz (örneğin, `netstandard1.4`). Birden çok çalışma zamanında çalıştırılması amaçlanan kitaplıkların bu çerçeveyi hedeflemesi gerekir. En geniş API kümesi için, kullanılabilir API `netstandard2.0` sayısı .NET Standard 1,6 ile 2,0 arasında iki katına çıkardığından hedefleyin.

Metapackage, [`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library/) .NET Standard tanımlayan tüm NuGet paketleri kümesine başvurur.  Hedefetmenin `netstandard` en yaygın yolu, bu metapackage 'e başvurarak yapılır. Bu, .NET Standard tanımlayan ~ 40 .NET kitaplıklarına ve ilişkili API 'lere erişim sağlar. Ek API 'lere erişim sağlamak için, `netstandard` hedef olan ek paketlere başvurabilirsiniz.

### <a name="versioning"></a>Sürüm Oluşturma

Belirtim tekil değildir, ancak artımlı olarak büyüyen ve önceden oluşturulmuş bir API kümesidir. Standart 'ın ilk sürümü bir temel API kümesi oluşturur. Sonraki sürümler, API 'Ler ekler ve önceki sürümler tarafından tanımlanan API 'Leri alırlar. Standart olmayan API 'Leri kaldırmak için bir sağlama yoktur.

.NET Standard herhangi bir .NET uygulamasına özgü değildir ve bu çalışma zamanlarının herhangi birinin sürüm oluşturma şemasıyla eşleşmez.

Uygulamalardan birine eklenen API 'Ler (örneğin, .NET Framework, .NET Core ve mono), özellikle de temel olarak düşünüldüler halinde, belirtime eklenecek aday olarak kabul edilebilir. [.NET Standard yeni sürümleri](https://github.com/dotnet/standard/blob/master/docs/versions.md) , .NET uygulama sürümleri temel alınarak oluşturulur ve bu sayede yeni apı 'LERI .NET Standard PCL 'den hedeflemenize olanak tanır. Sürüm oluşturma mekanizması, [.NET Core sürümü oluşturma](../core/versions/index.md)bölümünde daha ayrıntılı olarak açıklanmıştır.

Kullanım için .NET Standard sürümü oluşturma önemlidir. .NET Standard sürüm verildiğinde, aynı veya daha düşük sürümü hedefleyen kitaplıkları kullanabilirsiniz. Aşağıdaki yaklaşım, .NET Standard hedefleme öğesine özgü .NET Standard PCLs kullanma iş akışını açıklar.

- PCL 'niz için kullanılacak bir .NET Standard sürümü seçin.
- Aynı .NET Standard sürümüne veya daha düşük bir sürüme bağlı olan kitaplıkları kullanın.
- Daha yüksek .NET Standard sürüme bağlı bir kitaplık bulursanız, bu sürümü benimsemeniz veya bu kitaplığı kullanmamaya karar vermeniz gerekir.

## <a name="targeting-net-standard"></a>Hedefleme .NET Standard

`netstandard` Framework ve Netstandard. Library meta paketinin bir birleşimini kullanarak [.NET Standard kitaplıkları](../core/tutorials/libraries.md) oluşturabilirsiniz. [.NET Core araçları ile .NET Standard hedefleme](../core/packages.md)örneklerini görebilirsiniz.

## <a name="net-framework-compatibility-mode"></a>Uyumluluk modu .NET Framework

.NET Standard 2,0 ' den başlayarak .NET Framework uyumluluk modu sunuldu. Bu uyumluluk modu, .NET Standard projelerin .NET Standard için derlendikleri gibi .NET Framework kitaplıklarına başvurmasına olanak tanır. .NET Framework kitaplıklara başvurmak, Windows Presentation Foundation (WPF) API 'Leri kullanan kitaplıklar gibi tüm projeler için çalışmaz.

Daha fazla bilgi için bkz. [.NET Framework uyumluluk modu](../core/porting/third-party-deps.md#net-framework-compatibility-mode).

## <a name="net-standard-libraries-and-visual-studio"></a>.NET Standard kitaplıkları ve Visual Studio

Visual Studio 'da .NET Standard kitaplıklarını derlemek için Windows üzerinde [Visual Studio 2017 sürüm 15,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) veya sonraki bir sürümün yüklü olduğundan veya macos 'ta [Mac için Visual Studio sürüm 7,1](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) veya üzeri sürümlerde yüklü olduğundan emin olun.

Projelerinizde yalnızca .NET Standard 2,0 kitaplıklarını kullanmanız gerekiyorsa, bunu Visual Studio 2015 ' de de yapabilirsiniz. Ancak, NuGet Client 3,6 veya üzeri yüklü olmalıdır. [NuGet İndirmeleri](https://www.nuget.org/downloads) sayfasından Visual Studio 2015 için NuGet istemcisini indirebilirsiniz.

## <a name="comparison-to-portable-class-libraries"></a>Taşınabilir sınıf kitaplıklarına karşılaştırma

.NET Standard, [taşınabilir sınıf kitaplıklarının (PCL)](./cross-platform/cross-platform-development-with-the-portable-class-library.md)yerini alır. .NET Standard, standart bir BCL seçerek ve bir sonuç olarak .NET uygulamalarında daha fazla esneklik kurarak taşınabilir kitaplıklar oluşturma deneyiminden gelişir. .NET Standard hedefleyen bir kitaplık, PCL veya ".NET Standard tabanlı bir PCL" dir. Mevcut PCLs 'ler "profil tabanlı PCLs" şeklindedir.

.NET Standard ve PCL profilleri benzer amaçlar için oluşturulmuştur, ancak önemli yollarla da farklılık gösterir.

Benzerlikler

- İkili kod paylaşımı için kullanılabilecek API 'Leri tanımlayın.

Fark

- .NET Standard, PCL profilleri mevcut platformların Kesişimleriyle tanımlandığında, seçkin bir API kümesidir.
- .NET Standard linerken sürümler, PCL profilleri değildir.
- PCL profilleri, .NET Standard platform belirsiz olduğu sürece Microsoft platformlarını temsil eder.

### <a name="pcl-compatibility"></a>PCL uyumluluğu

.NET Standard, PCL profillerinin bir alt kümesiyle uyumludur. .NET Standard 1,0, 1,1 ve 1,2 her biri bir PCL profilleri kümesiyle örtüşüyor. Bu çakışma iki nedenden dolayı oluşturulmuştur:

- Profil tabanlı PCLs 'e başvurmak için .NET Standard tabanlı PCLs 'yi etkinleştirin.
- Profil tabanlı PCLs 'Leri .NET Standard tabanlı PCLs olarak paketlenebilecek şekilde etkinleştirin.

Profil tabanlı PCL uyumluluğu, [Microsoft. NETCore. Portable. Compatibility](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) NuGet paketi tarafından sağlanır. Profil tabanlı PCLs 'Leri içeren NuGet paketlerine başvururken bu bağımlılık gereklidir.

Profil tabanlı PCLS `netstandard` 'ler, genellikle paketlenmiş profil tabanlı PCLS 'dan daha kolay tüketilecektir. `netstandard`Paketleme, mevcut kullanıcılarla uyumludur.

.NET Standard uyumlu olan PCL profillerinin kümesini görebilirsiniz:

| PCL profili | .NET Standard | PCL platformları
|:-----------:|:-------------:|------------------------------------------------------------------------------
| Profile7    | 1.1           | .NET Framework 4,5, Windows 8
| Profile31   | 1.0           | Windows 8.1 Windows Phone Silverlight 8,1
| Profile32   | 1.2           | Windows 8.1, Windows Phone 8,1
| Profile44   | 1.2           | .NET Framework 4.5.1, Windows 8.1
| Profile49   | 1.0           | .NET Framework 4,5, Windows Phone Silverlight 8
| Profile78   | 1.0           | .NET Framework 4,5, Windows 8 Windows Phone Silverlight 8
| Profile84   | 1.0           | Windows Phone 8,1, Windows Phone Silverlight 8,1
| Profile111  | 1.1           | .NET Framework 4,5, Windows 8, Windows Phone 8,1
| Profile151  | 1.2           | .NET Framework 4.5.1, Windows 8.1, Windows Phone 8,1
| Profile157  | 1.0           | Windows 8.1, Windows Phone 8,1, Windows Phone Silverlight 8,1
| Profile259  | 1.0           | .NET Framework 4,5, Windows 8, Windows Phone 8,1, Windows Phone Silverlight 8

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Standard sürümleri](https://github.com/dotnet/standard/blob/master/docs/versions.md)
