---
title: Ortak Dil Çalışma Süresi (CLR) genel bakış - .NET Framework
ms.date: 04/02/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- compiling source code, runtime functionality
- code, execution
- managed data
- runtime
- common language runtime
- metadata, runtime functionality
- .NET Framework, common language runtime
- language compilers
- managed code
- source code execution
- code, runtime functionality
ms.assetid: 059a624e-f7db-4134-ba9f-08b676050482
ms.custom: updateeachrelease
ms.openlocfilehash: 6f9ad8aafc37039b55ae3bf6eb743e07ad8e2235
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74884416"
---
# <a name="common-language-runtime-clr-overview"></a>Ortak Dil Çalışma Süresi (CLR) genel bakış

.NET Framework, kodu çalıştıran ve geliştirme işlemini kolaylaştıran hizmetler sağlayan ortak dil çalışma zamanı adı verilen bir çalışma zamanı ortamı sağlar.

Derleyiciler ve araçlar ortak dil çalışma zamanının işlevselliğini ortaya çıkarır ve bu yönetilen yürütme ortamından yararlanan kod yazmanızı sağlar. Çalışma süresini hedefleyen bir dil derleyicisi ile geliştirdiğiniz koda yönetilen kod denir; diller arası tümleştirme, diller arası özel durum işleme, gelişmiş güvenlik, sürüm oluşturma ve dağıtım desteği, bileşen etkileşimi için basitleştirilmiş bir model ve hata ayıklama ve profil oluşturma hizmetleri gibi özelliklerden yararlanır.

> [!NOTE]
> Derleyiciler ve araçlar, tür sistemi, meta verilerin biçimi ve çalışma zamanı ortamı (sanal yürütme sistemi) tümü genel bir standart olan ECMA Ortak Dili tarafından tanımlandığı için ortak dil çalışma zamanının tüketebileceği çıktıları üretebilirler. Altyapı belirtimi. Daha fazla bilgi için [ECMA C# ve Ortak Dil Altyapı Özellikleri'ne](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/)bakın.

Yönetilen koda hizmet sağlamak için çalışma zamanının etkin olmasını sağlamak için, dil derleyicilerinin kodunızdaki türleri, üyeleri ve başvuruları açıklayan meta veriler yontması gerekir. Meta veriler kodla birlikte depolanır; her yüklenebilir ortak dil çalışma süresi taşınabilir yürütülebilir (PE) dosyası meta veri içerir. Çalışma zamanı, sınıfları bulmak ve yüklemek, bellekte örnekleri düzenlemek, yöntem çağrılarını çözmek, yerel kod oluşturmak, güvenliği zorlamak ve çalışma zamanı bağlam ısınırlarını ayarlamak için meta verileri kullanır.

Çalışma zamanı nesne düzenini otomatik olarak işler ve nesnelere yapılan başvuruları yönetir ve artık kullanılmadıklarında serbest kalır. Yaşam ları bu şekilde yönetilen nesnelere yönetilen verilere yönetilen veriler denir. Çöp toplama bellek sızıntıları yanı sıra diğer bazı yaygın programlama hataları ortadan kaldırır. Kodunuz yönetilirse, .NET Framework uygulamanızda yönetilen verileri, yönetilmeyen verileri veya yönetilen ve yönetilmeyen verileri kullanabilirsiniz. Dil derleyicileri ilkel türler gibi kendi türlerini sağladığından, verilerinizin yönetilip yönetilmediğini her zaman bilmiyor (veya bilmesi gerekmeyebilir).

Ortak dil çalışma süresi, nesneleri diller arasında etkileşimedebilen bileşenler ve uygulamalar tasarlamayı kolaylaştırır. Farklı dillerde yazılmış nesneler birbirleriyle iletişim kurabilir ve davranışları sıkıca tümleştirilebilir. Örneğin, bir sınıf tanımlayabilir ve özgün sınıfınızdan bir sınıf türetmek veya özgün sınıfta bir yöntem çağırmak için farklı bir dil kullanabilirsiniz. Ayrıca, sınıf örneğini farklı bir dilde yazılmış bir sınıfın yöntemine geçirebilirsiniz. Bu diller arası tümleştirme, çalışma zamanı hedefleyen dil derleyicileri ve araçlarının çalışma zamanı tarafından tanımlanan ortak bir tür sistemi kullanması ve yeni türleri tanımlamanın yanı sıra oluşturma, kullanma, kalıcılık oluşturma ve türleri için bağlama.

Meta verilerinin bir parçası olarak, yönetilen tüm bileşenler, karşı inşa edildikleri bileşenler ve kaynaklar hakkında bilgi taşır. Çalışma süresi, bileşeninizin veya uygulamanızın ihtiyaç duyduğu her şeyin belirtilen sürümlerine sahip olduğundan emin olmak için bu bilgileri kullanır ve bu da karşılanmayan bazı bağımlılık nedeniyle kodunuzun kırılma olasılığını azaltır. Kayıt bilgileri ve durum verileri artık kayıt defterinde depolanamıyor ve bunların oluşturulması ve bakımı nın zor olduğu bir yerde. Bunun yerine, tanımladığınız türler (ve bunların bağımlılıkları) hakkındaki bilgiler kodla birlikte meta veri olarak depolanır ve bu da bileşen çoğaltma ve kaldırma görevlerini çok daha az karmaşık hale getirir.

Dil derleyicileri ve araçları, çalışma zamanının işlevselliğini geliştiriciler için yararlı ve sezgisel olması amaçlanan şekillerde ortaya çıkarır. Bu, çalışma zamanının bazı özelliklerinin bir ortamda diğerinden daha fazla fark edileebileceği anlamına gelir. Çalışma süresini nasıl deneyimlediğiniz, hangi dil derleyicilerini veya araçları kullandığınıza bağlıdır. Örneğin, Visual Basic geliştiricisiyseniz, ortak dil çalışma süresiyle Visual Basic dilinin öncekinden daha fazla nesne yönelimli özelliğe sahip olduğunu fark edebilirsiniz. Çalışma süresi aşağıdaki avantajları sağlar:

- Performans geliştirmeleri.

- Diğer dillerde geliştirilen bileşenleri kolayca kullanabilme yeteneği.

- Sınıf kitaplığı tarafından sağlanan genişletilebilir türleri.

- Nesne yönelimli programlama için devralma, arabirimler ve aşırı yükleme gibi dil özellikleri.

- Çok iş parçacığı, ölçeklenebilir uygulamaların oluşturulmasına olanak tanıyan açık serbest iş parçacığı desteği.

- Yapılandırılmış özel durum işleme desteği.

- Özel öznitelikler için destek.

- Çöp toplama.

- Artan tür güvenliği ve güvenliği için işlev işaretçileri yerine temsilci kullanımı. Temsilciler hakkında daha fazla bilgi için [Ortak Tür Sistemi'ne](../../docs/standard/base-types/common-type-system.md)bakın.

## <a name="clr-versions"></a>CLR sürümleri

.NET Framework sürüm numarası, içerdiği CLR'nin sürüm numarasıyla örtüşmez. .NET Framework sürümleri ve bunların karşılık gelen CLR sürümlerinin listesi için [bkz.](../framework/migration-guide/versions-and-dependencies.md) .NET Core sürümlerinin tek bir ürün sürümü vardır, yani ayrı bir CLR sürümü yoktur. .NET Core sürümlerinin listesi için [bkz.](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Yönetilen Yürütme İşlemi](managed-execution-process.md)|Ortak dil çalışma zamanından yararlanmak için gereken adımları açıklar.|
|[Otomatik Bellek Yönetimi](automatic-memory-management.md)|Çöp toplayıcısının belleği nasıl ayırdığını ve serbest bırakmasını açıklar.|
|[.NET Framework'e Genel Bakış](../framework/get-started/overview.md)|Ortak tür sistemi, diller arası birlikte çalışabilirlik, yönetilen yürütme, uygulama etki alanları ve derlemeler gibi anahtar .NET Framework kavramlarını açıklar.|
|[Ortak Tür Sistemi](./base-types/common-type-system.md)|Türler arası tümleştirmeyi desteklemek için çalışma zamanında türlerin nasıl beyan edilir, kullanıldığını ve yönetildiğini açıklar.|
