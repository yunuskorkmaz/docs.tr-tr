---
title: Ortak dil çalışma zamanı (CLR) genel bakış-.NET Framework
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
ms.openlocfilehash: 74421f79c18f32e121d51c47f3eb32f3c2ed71fd
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289252"
---
# <a name="common-language-runtime-clr-overview"></a>Ortak dil çalışma zamanı (CLR) genel bakış

.NET Framework, kodu çalıştıran ve geliştirme sürecini kolaylaştıran hizmetler sağlayan ortak dil çalışma zamanı adlı bir çalışma zamanı ortamı sağlar.

Derleyiciler ve araçlar ortak dil çalışma zamanının işlevselliğini sunar ve bu yönetilen yürütme ortamından faydalanan bir kod yazmanızı sağlar. Çalışma zamanını hedefleyen bir dil derleyicisi ile geliştirdiğiniz koda yönetilen kod denir; Diller arası tümleştirme, platformlar arası özel durum işleme, gelişmiş güvenlik, sürüm oluşturma ve dağıtım desteği, bileşen etkileşimi için basitleştirilmiş bir model ve hata ayıklama ve profil oluşturma hizmetleri gibi özelliklerden faydalanır.

> [!NOTE]
> Derleyiciler ve araçlar ortak dil çalışma zamanının tüketebileceği bir çıktı üretebilir, çünkü tür sistemi, meta veri biçimi ve çalışma zamanı ortamı (sanal yürütme sistemi), ECMA ortak dil altyapısı belirtimi olan genel bir standart tarafından tanımlanır. Daha fazla bilgi için bkz. [ecma C# ve ortak dil altyapısı belirtimleri](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/).

Çalışma zamanının yönetilen koda hizmet sağlamasına olanak tanımak için dil derleyicileri, kodunuzdaki türleri, üyeleri ve başvuruları açıklayan meta verileri yaymalıdır. Meta veriler, kodla depolanır; Her yüklenebilir ortak dil çalışma zamanı Taşınabilir çalıştırılabilir (PE) dosyası meta veriler içerir. Çalışma zamanı, sınıfları bulmak ve yüklemek, örnekleri bellekte düzenlemek, yöntem çağırmaları çözümlemek, yerel kod oluşturmak, güvenliği zorlamak ve çalışma zamanı bağlam sınırlarını ayarlamak için meta verileri kullanır.

Çalışma zamanı, nesne yerleşimini otomatik olarak işler ve nesneleri artık kullanılmadıklarında serbest bırakır ve nesneler için başvuruları yönetir. Ömürleri bu şekilde yönetilen nesneler yönetilen veriler olarak adlandırılır. Çöp toplama, diğer yaygın programlama hatalarının yanı sıra bellek sızıntılarını da ortadan kaldırır. Kodunuz yönetilmiyorsa yönetilen verileri, yönetilmeyen verileri veya .NET Framework uygulamanızda hem yönetilen hem de yönetilmeyen verileri kullanabilirsiniz. Dil derleyicileri, ilkel türler gibi kendi türlerini sağladığından, verilerinizin yönetilip yönetilmediğini her zaman bilmiyor olabilirsiniz (veya bilmeniz gerekmez).

Ortak dil çalışma zamanı, nesneleri diller arasında etkileşim kuran bileşenleri ve uygulamaları tasarlamayı kolaylaştırır. Farklı dillerde yazılan nesneler birbirleriyle iletişim kurabilir ve davranışları sıkı bir şekilde tümleştirilebilir. Örneğin, bir sınıfı tanımlayabilir, sonra özgün sınıfınızdan bir sınıf türetebilir veya orijinal sınıfta bir yöntemi çağırabilirsiniz. Ayrıca, bir sınıfın örneğini farklı bir dilde yazılmış bir sınıf yöntemine geçirebilirsiniz. Bu çapraz dil tümleştirmesi, çalışma zamanını hedef alan dil derleyicileri ve Araçları çalışma zamanı tarafından tanımlanan ortak bir tür sistemi kullandığından ve bu tür çalışma zamanının yeni türleri tanımlama ve oluşturma, kullanma, kalıcı ve türlerine bağlama için kuralları izledikleri için mümkündür.

Meta verilerinin bir parçası olarak, tüm yönetilen bileşenler, derlendikleri bileşenler ve kaynaklarla ilgili bilgiler taşır. Çalışma zamanı, bileşeninizin veya uygulamanızın gereken her şeyin belirtilen sürümlerine sahip olduğundan emin olmak için bu bilgileri kullanır. Bu, kodunuzun, bazı karşılanmayan bağımlılıktan dolayı daha az büyük olasılıkla kesintiye uğramasını sağlar. Kayıt bilgileri ve durum verileri artık, oluşturulması ve saklanması zor olabilecek kayıt defterinde depolanmaz. Bunun yerine, tanımladığınız türler (ve bağımlılıkları) hakkındaki bilgiler, kodla meta veri olarak depolanır, böylece bileşen çoğaltma ve kaldırma görevlerinin çok daha az karmaşıktır.

Dil derleyicileri ve araçları, çalışma zamanının işlevselliğini geliştiricilere yararlı ve sezgisel olması amaçlanan yollarla kullanıma sunar. Bu, çalışma zamanının bazı özelliklerinin bir ortamda diğerinden daha belirgin olabileceğini gösterir. Çalışma zamanına nasıl karşılaşabileceğiniz, kullandığınız dil derleyicilerini veya araçlarına bağlıdır. Örneğin, bir Visual Basic geliştiricisiyseniz, ortak dil çalışma zamanı ile Visual Basic dilinin daha önce daha fazla nesne yönelimli özelliği olduğunu fark edebilirsiniz. Çalışma zamanı aşağıdaki avantajları sağlar:

- Performans geliştirmeleri.

- Diğer dillerde geliştirilmiş bileşenleri kolayca kullanma özelliği.

- Sınıf kitaplığı tarafından sunulan Genişletilebilir türler.

- Nesne odaklı programlama için devralma, arabirimler ve aşırı yükleme gibi dil özellikleri.

- Çok iş parçacıklı, ölçeklenebilir uygulamalar oluşturulmasına izin veren açık ücretsiz iş parçacığı desteği.

- Yapılandırılmış özel durum işleme desteği.

- Özel öznitelikler için destek.

- Çöp toplama.

- Artırılmış tür güvenliği ve güvenlik için işlev işaretçileri yerine temsilcilerin kullanımı. Temsilciler hakkında daha fazla bilgi için bkz. [ortak tür sistemi](base-types/common-type-system.md).

## <a name="clr-versions"></a>CLR sürümleri

.NET Framework sürüm numarası, içerdiği CLR 'nin sürüm numarasına karşılık gelmez. .NET Framework sürümlerinin ve bunlara karşılık gelen CLR sürümlerinin listesi için, bkz. [.NET Framework sürümler ve bağımlılıklar](../framework/migration-guide/versions-and-dependencies.md). .NET Core sürümlerinin tek bir ürün sürümü vardır, diğer bir deyişle, ayrı bir CLR sürümü yoktur. .NET Core sürümlerinin listesi için bkz. [.NET Core 'U indirme](https://dotnet.microsoft.com/download/dotnet-core).

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Yönetilen yürütme Işlemi](managed-execution-process.md)|Ortak dil çalışma zamanının avantajlarından yararlanmak için gereken adımları açıklar.|
|[Otomatik bellek yönetimi](automatic-memory-management.md)|Çöp toplayıcısının belleği nasıl ayırdığı ve yayımlarsa açıklanmaktadır.|
|[.NET Framework'e Genel Bakış](../framework/get-started/overview.md)|Ortak tür sistemi, çapraz dil birlikte çalışabilirliği, yönetilen yürütme, uygulama etki alanları ve derlemeler gibi temel .NET Framework kavramları açıklar.|
|[Ortak tür sistemi](./base-types/common-type-system.md)|Türlerin, platformlar arası tümleştirme desteğiyle çalışma zamanında nasıl bildirildiği, kullanıldığı ve yönetildiğini açıklar.|
