---
title: .NET Standard
description: .NET Standard, sürümleri ve bunu destekleyen .NET uygulamaları hakkında bilgi edinin.
ms.date: 10/05/2020
ms.technology: dotnet-standard
ms.custom: updateeachrelease
ms.assetid: c044882c-af15-45f2-96d1-534557a5ee9b
ms.openlocfilehash: a4a59fea3ab1a6bc93a12e3f0aa13dea726d8121
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050409"
---
# <a name="net-standard"></a>.NET Standard

[.NET Standard](https://github.com/dotnet/standard) , .NET API 'lerinin çoklu .NET uygulamalarında bulunan resmi bir belirtimidir. .NET Standard arkasındaki mosyon, .NET ekosisteminde daha büyük bir birlik sağlamak idi. Ancak, .NET 5, farklı bir yaklaşım oluşturmak için farklı bir yaklaşım benimsemektedir ve bu yeni yaklaşım pek çok senaryoda .NET Standard gereksinimini ortadan kaldırır. Daha fazla bilgi için bu makalenin devamındaki [.NET 5 ve .NET Standard](#net-5-and-net-standard) bölümüne bakın.

## <a name="net-implementation-support"></a>.NET uygulama desteği

Çeşitli .NET uygulamaları .NET Standard belirli sürümlerini hedefleyin. Her .NET uygulama sürümü, desteklediği en yüksek .NET Standard sürümünü tanıtır, yani önceki sürümleri de destekler. Örneğin, .NET Framework 4,6 .NET Standard 1,3 ' i uygular, yani .NET Standard sürümler 1,0 içinde tanımlanan tüm API 'Leri 1,3 aracılığıyla gösterir. Benzer şekilde, .NET Framework 4.6.1 .NET Standard 1,4 uygular, ancak .NET 5,0 .NET Standard 2,1 uygular.

Aşağıdaki tabloda, her bir .NET Standard sürümünü destekleyen **En düşük** uygulama sürümleri listelenmektedir. Bu, listelenen bir uygulamanın sonraki sürümlerinin de karşılık gelen .NET Standard sürümünü desteklediği anlamına gelir. Örneğin, .NET Core 2,1 ve üzeri sürümler .NET Standard 2,0 ve önceki sürümleri destekler.

[!INCLUDE [net-standard-table](../../includes/net-standard-table.md)]

Hedeflenebilen .NET Standard en yüksek sürümünü bulmak için aşağıdaki adımları uygulayın:

1. Üzerinde çalışmak istediğiniz .NET uygulamasını gösteren satırı bulun.
1. Bu satırdaki, sürümünüzü sağdan sola başlayarak gösteren sütunu bulun.
1. Sütun üst bilgisi, hedefin desteklediği .NET Standard sürümünü belirtir. Ayrıca, daha düşük .NET Standard sürümleri de hedefleyebilirsiniz. Daha yüksek .NET Standard sürümler de Uygulamanızı destekleyecektir.
1. Hedeflemek istediğiniz her platform için bu işlemi tekrarlayın. Birden fazla hedef platformunuz varsa, bunların arasından daha küçük bir sürüm seçmeniz gerekir. Örneğin, .NET Framework 4,8 ve .NET 5,0 ' de çalıştırmak istiyorsanız kullanabileceğiniz en yüksek .NET Standard sürümü .NET Standard 2,0.

### <a name="which-net-standard-version-to-target"></a>Hedeflenecek .NET Standard sürümü

Hedeflenecek bir .NET Standard sürümünü seçerken, bu ticareti göz önünde bulundurun:

- Sürüm arttıkça, kitaplığınızın kodu için diğer API 'Ler kullanılabilir.
- Sürüm ne kadar düşükse, daha fazla uygulama ve kitaplık kitaplığınızı kullanabilir.

Mümkün olan *En düşük* sürümü .NET Standard hedeflemesini öneririz. Bu nedenle, hedeflenebilen en yüksek .NET Standard sürümünü bulduktan sonra aşağıdaki adımları izleyin:

1. .NET Standard sonraki alt sürümünü hedefleyin ve projenizi derleyin.
2. Projeniz başarıyla oluşturul, 1. adımı yineleyin. Aksi takdirde, sonraki daha yüksek sürüme yeniden hedefleyin ve kullanmanız gereken sürümdür.

Ancak, daha düşük .NET Standard sürümleri hedeflemek çok sayıda destek bağımlılığı sunar. Projeniz .NET Standard 1. x hedefliyorsa, ayrıca .NET Standard 2,0 ' i *de* hedeflediğiniz önerilir. Bu, kitaplığınızın .NET Standard 2,0 uyumlu uygulamalarda çalışan kullanıcıları için bağımlılık grafiğini basitleştirir ve İndirmeleri gereken paket sayısını azaltır.

### <a name="net-standard-versioning-rules"></a>.NET Standard sürüm oluşturma kuralları

İki birincil sürüm oluşturma kuralı vardır:

- Eklenebilir: .NET Standard sürümler mantıksal olarak eşmerkezli daireler: daha yüksek sürümler önceki sürümlerden tüm API 'Leri dahil. Sürümler arasında hiç Son değişiklik yok.
- Sabit: sevk edildiğinde .NET Standard sürümler dondurulur.

2,1 sonra yeni .NET Standard sürümler olmayacaktır. Daha fazla bilgi için bu makalenin devamındaki [.NET 5 ve .NET Standard](#net-5-and-net-standard) bölümüne bakın.

## <a name="specification"></a>Belirtim

.NET Standard belirtimi, standartlaştırılmış bir API kümesidir. Belirtim .NET uygulayıcılar tarafından, özellikle Microsoft (.NET Framework, .NET Core ve mono dahil) ve Unity tarafından korunur.

### <a name="official-artifacts"></a>Resmi yapılar

Resmi belirtimi, standart bir parçası olan API 'Leri tanımlayan bir *. cs* dosyası kümesidir. [DotNet/standart deposundaki](https://github.com/dotnet/standard) [ref dizini](https://github.com/dotnet/standard/tree/master/src/netstandard/ref) .NET Standard API 'leri tanımlar.

[Netstandard. Library](https://www.nuget.org/packages/NETStandard.Library) meta paketi ([kaynak](https://github.com/dotnet/standard/blob/master/src/netstandard/pkg/NETStandard.Library.dependencies.props)) bir veya daha fazla .NET Standard sürümünde tanımlayan kitaplıklar kümesini açıklar.

Şunun gibi belirli bir bileşen şunları `System.Runtime` açıklar:

- .NET Standard (yalnızca kapsamı) bir parçasıdır.
- Bu kapsam için birden çok .NET Standard sürümü.

Türetilmiş yapıtlar, daha kolay okunması ve belirli geliştirici senaryolarına olanak tanımak için sağlanır (örneğin, bir derleyici kullanarak).

- [Markın içindeki API listesi](https://github.com/dotnet/standard/tree/master/docs/versions)
- NuGet paketleri olarak dağıtılan ve [Netstandard. Library](https://www.nuget.org/packages/NETStandard.Library/) metapackage tarafından başvurulan başvuru derlemeleri.

### <a name="package-representation"></a>Paket temsili

.NET Standard başvuru derlemelerinin birincil dağıtım aracı NuGet paketlerdir. Uygulamalar, her .NET uygulaması için uygun olan çeşitli yollarla dağıtılır.

NuGet paketleri bir [veya daha fazla](frameworks.md)çerçeveyi hedeflemelidir. .NET Standard paketleri ".NET Standard" çerçevesini hedefleyin. `netstandard` [Compact tfı](frameworks.md) kullanarak .NET Standard çerçevesini hedefleyebilirsiniz (örneğin, `netstandard1.4` ). .NET 'in birden çok uygulamasında çalışması amaçlanan kitaplıkların bu çerçeveyi hedeflemesi gerekir. En geniş API kümesi için, `netstandard2.0` kullanılabilir API sayısı .NET Standard 1,6 ile 2,0 arasında iki katına çıkardığından hedefleyin.

[`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library/)Metapackage, .NET Standard tanımlayan tüm NuGet paketleri kümesine başvurur.  Hedefetmenin en yaygın yolu, `netstandard` Bu metapackage 'e başvurarak yapılır. Bu, .NET Standard tanımlayan ~ 40 .NET kitaplıklarına ve ilişkili API 'lere erişim sağlar. Ek API 'lere erişim sağlamak için, hedef olan ek paketlere başvurabilirsiniz `netstandard` .

### <a name="versioning"></a>Sürüm Oluşturma

Belirtim tekil değildir, ancak önceden sürümlü bir API kümesidir. Standart 'ın ilk sürümü bir temel API kümesi oluşturur. Sonraki sürümler, API 'Ler ekler ve önceki sürümler tarafından tanımlanan API 'Leri alırlar. Standart olmayan API 'Leri kaldırmak için bir sağlama yoktur.

.NET Standard herhangi bir .NET uygulamasına özgü değildir veya bu uygulamalardan herhangi birinin sürüm oluşturma şemasıyla eşleşmez.

Daha önce belirtildiği gibi, 2,1 sonrasında yeni .NET Standard sürümler olmayacaktır.

## <a name="target-net-standard"></a>Hedef .NET Standard

Framework ve metapackage birleşimini kullanarak [.NET Standard kitaplıkları](../core/tutorials/libraries.md) oluşturabilirsiniz `netstandard` `NETStandard.Library` .

## <a name="net-framework-compatibility-mode"></a>Uyumluluk modu .NET Framework

.NET Standard 2,0 ' den başlayarak .NET Framework uyumluluk modu sunuldu. Bu uyumluluk modu, .NET Standard projelerin .NET Standard için derlendikleri gibi .NET Framework kitaplıklarına başvurmasına olanak tanır. .NET Framework kitaplıklara başvurmak, Windows Presentation Foundation (WPF) API 'Leri kullanan kitaplıklar gibi tüm projeler için çalışmaz.

Daha fazla bilgi için bkz. [.NET Framework uyumluluk modu](../core/porting/third-party-deps.md#net-framework-compatibility-mode).

## <a name="net-standard-libraries-and-visual-studio"></a>.NET Standard kitaplıkları ve Visual Studio

Visual Studio 'da .NET Standard kitaplıklarını derlemek için, Windows 'da [Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya visual Studio 2017 sürüm 15,3 veya üzeri sürümünün yüklü olduğundan veya macos 'ta [Mac için Visual Studio sürüm 7,1](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) veya üzeri sürümlerin yüklü olduğundan emin olun.

Projelerinizde yalnızca .NET Standard 2,0 kitaplıklarını kullanmanız gerekiyorsa, bunu Visual Studio 2015 ' de de yapabilirsiniz. Ancak, NuGet Client 3,6 veya üzeri yüklü olmalıdır. [NuGet İndirmeleri](https://www.nuget.org/downloads) sayfasından Visual Studio 2015 için NuGet istemcisini indirebilirsiniz.

## <a name="net-5-and-net-standard"></a>.NET 5 ve .NET Standard

.NET 5, Microsoft 'un etkin bir şekilde geliştirdiği .NET uygulamasıdır. Bu, Windows Masaüstü uygulamaları ve platformlar arası konsol uygulamaları, bulut hizmetleri ve Web siteleri için kullanılabilen, tek bir ürün ve bir dizi özellik ve API 'yi içeren tek bir üründür. .NET 5,0 [Tfms](frameworks.md) , bu geniş senaryoları yansıtır:

* `net5.0`

  Bu TFA, her yerde çalışan kod içindir. Birkaç özel durum dışında, yalnızca platformlar arası çalışan teknolojiler içerir. .NET 5 kodu için `net5.0` hem hem de `netcoreapp` tfms 'nin yerini alır `netstandard` .

* `net5.0-windows`

  Bu, öğesine başvuran her şeye işletim sistemine özgü işlevsellik ekleyen bir [Işletim sistemine özgü TFMs](frameworks.md#net-5-os-specific-tfms) örneğidir `net5.0` .

### <a name="when-to-target-net50-vs-netstandard"></a>NET 5.0 ve Netstandard 'ın ne zaman hedeflenecek

Hedefleyen mevcut kod için `netstandard` tfd 'yi olarak değiştirmeniz gerekmez `net5.0` . .NET 5,0 .NET Standard 2,1 ve önceki sürümleri uygular. .NET Standard .NET 5,0 ' e yeniden hedeflemeniz için tek neden, daha fazla çalışma zamanı özelliğine, dil özelliklerine veya API 'lere erişim kazanmalıdır. Örneğin, C# 9 ' u kullanmak için, .NET 5,0 ' i hedeflemek gerekir. Daha yeni özelliklere erişim sağlamak ve kitaplığınızı hala diğer .NET uygulamalarında kullanılabilir olacak şekilde, .NET 5,0 ve .NET Standard çok hedefleyebilirsiniz.

.NET 5 için yeni kod için bazı yönergeler aşağıda verilmiştir:

* Uygulama bileşenleri

  Bir uygulamayı birkaç bileşene bölmek için kitaplıklar kullanıyorsanız, `net5.x` `5.x` uygulamanızın hedeflebildiği en erken .NET 5 sürümünün nerede olduğunu hedeflemenizi öneririz. Kolaylık olması için, uygulamanızı aynı .NET sürümünde oluşturan tüm projeleri tutmak en iyisidir. Daha sonra aynı BCL özelliklerinin her yerde olduğunu varsayabilirsiniz.

* Yeniden kullanılabilir kitaplıklar

  NuGet 'de teslim etmeyi planladığınız yeniden kullanılabilir kitaplıklar oluşturuyorsanız, ulaşma ve kullanılabilir özellik kümesi arasındaki dengelemeyi göz önünde bulundurun. .NET Standard 2,0, .NET Framework tarafından desteklenen en son sürümdür. bu nedenle, oldukça büyük bir özellik kümesiyle daha iyi bir erişim sağlar. .NET Standard 1. x ' i hedeflemeyi önermeyiz, ancak mevcut özellik kümesini, erişim için en az artışla sınırlandıracağız.

  .NET Framework desteklemeniz gerekmiyorsa, .NET Standard 2,1 veya .NET 5 ile gidebilirsiniz. .NET Standard 2,1 ' i atlayıp doğrudan .NET 5 ' e gitmeniz önerilir. En yaygın olarak kullanılan kitaplıklar, hem .NET Standard 2,0 hem de .NET 5 için çoklu hedeflemeyi sona erdirmek için kullanılır. 2,0 .NET Standard destekleyici, .NET 5 ' i desteklerken, zaten .NET 5 ' te olan müşteriler için en son Platform özelliklerinden yararlanmanızı sağlar.

### <a name="net-standard-problems"></a>.NET Standard sorunları

Aşağıda, .NET 5 ' in platformları ve iş yükleri arasında kodu paylaşmanın daha iyi bir yolu olduğunu açıklamaya yardımcı olan .NET Standard bazı sorunlar verilmiştir:

- Yeni API 'Ler eklemek için yavaşlık

  .NET Standard, tüm .NET uygulamalarının desteklemesi gereken bir API kümesi olarak oluşturulmuştur, bu nedenle yeni API 'Ler eklemek için teklifler için bir gözden geçirme işlemi vardı. Amaç yalnızca tüm geçerli ve gelecekteki .NET platformlarında uygulanabilen API 'Leri standartlaştırmaktır. Sonuç, bir özellik belirli bir sürümü kaçırdıysa, bir standart sürümüne eklenmeden önce birkaç yıl beklemeniz gerekebilir. Daha sonra, .NET Standard yeni sürümünün yaygın olarak desteklenmesine de daha uzun bir süre beklemeniz gerekir.

  **.NET 5 ' te çözüm:** Bir özellik uygulandığında, kod tabanı paylaşıldığından her .NET 5 uygulaması ve kitaplığı için zaten kullanılabilir. API belirtimi ve uygulamasının uygulanması arasında fark olmadığından, .NET Standard yeni özelliklerden çok daha hızlı bir şekilde yararlanabilirsiniz.

- Karmaşık sürüm oluşturma

  API belirtiminin uygulamalarından ayrılması, API belirtim sürümleri ve uygulama sürümleri arasında karmaşık eşlemeye neden olur. Bu karmaşıklık, bu makalenin önceki kısımlarında gösterilen tabloda ve bunu yorumlama yönergelerinden daha açık bir hale gelir.

  **.NET 5 ' te çözüm:** .NET 5. x API belirtimi ve uygulamasının uygulanması arasında ayrım yoktur. Sonuç basitleştirilmiş bir tfd düzenidir. Tüm iş yükleri için bir TFı öneki vardır: `net5.0` Kitaplıklar, konsol uygulamaları ve Web uygulamaları için kullanılır. Tek çeşitleme, gibi belirli bir platform için [platforma özgü API 'leri belirten bir sonektir](frameworks.md#net-5-os-specific-tfms) `net5.0-windows` . Bu tfd adlandırma kuralı sayesinde, belirli bir uygulamanın belirli bir kitaplığı kullanıp kullanamayacağını kolayca anlayabilirsiniz. .NET Standard için bir sürüm numarası eşdeğerleri tablosu gerekli değildir.

- Platform-çalışma zamanında desteklenmeyen özel durumlar

  .NET Standard platforma özgü API 'Leri kullanıma sunar. Kodunuz hata olmadan derleyebilir ve taşınabilir olmasa bile herhangi bir platforma taşınabilir. Belirli bir API için uygulamaya sahip olmayan bir platformda çalıştırıldığında, çalışma zamanı hataları alırsınız.

  **.NET 5 ' te çözüm:** .NET 5 SDK, varsayılan olarak etkinleştirilen kod Çözümleyicileri içerir. Platform uyumluluk Çözümleyicisi, çalıştırmayı planladığınız platformlarda desteklenmeyen API 'lerin yanlışlıkla kullanımını algılar. Daha fazla bilgi için bkz. [platform uyumluluğu Çözümleyicisi](analyzers/platform-compat-analyzer.md).

### <a name="net-standard-not-deprecated"></a>Kullanım dışı .NET Standard

.NET Standard, birden fazla .NET uygulaması tarafından kullanılabilen kitaplıklar için hala gereklidir. Aşağıdaki senaryolarda .NET Standard hedefini yapmanızı öneririz:

* `netstandard2.0`.NET Framework ve tüm diğer .NET uygulamaları arasında kod paylaşmak için kullanın.
* `netstandard2.1`Mono, Xamarin ve .NET Core 3. x arasında kod paylaşmak için kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Standard sürümleri (kaynak)](https://github.com/dotnet/standard/blob/master/docs/versions.md)
- [.NET Standard sürümleri (etkileşimli UI)](https://dotnet.microsoft.com/platform/dotnet-standard#versions)
- [.NET Standard kitaplığı oluşturma](../core/tutorials/library-with-visual-studio.md)
- [Platformlar arası hedefleme](./library-guidance/cross-platform-targeting.md)
