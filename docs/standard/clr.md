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
ms.openlocfilehash: 6f9ad8aafc37039b55ae3bf6eb743e07ad8e2235
ms.sourcegitcommit: 68a4b28242da50e1d25aab597c632767713a6f81
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/06/2019
ms.locfileid: "74884416"
---
# <a name="common-language-runtime-clr-overview"></a>Ortak dil çalışma zamanı (CLR) genel bakış

.NET Framework, kodu çalıştıran ve geliştirme işlemini kolaylaştıran hizmetler sağlayan, ortak dil çalışma zamanı adlı bir çalışma zamanı ortamı sağlar.

Derleyiciler ve araçlar ortak dil çalışma zamanının işlevselliğini gösterir ve bu yönetilen yürütme ortamından faydalanan bir kod yazmanızı sağlar. Çalışma zamanını hedefleyen bir dil derleyici ile geliştirdiğiniz koda yönetilen kod adı verilir; bu kod diller arası tümleştirme, diller arası özel durumunun ele alınması, artırılmış güvenlik, sürüm oluşturma ve dağıtım desteği, bileşen etkileşimi için basitleştirilmiş bir model ve hata ayıklama ve profil oluşturma hizmetleri için gibi özelliklerden faydalanır.

> [!NOTE]
> Derleyiciler ve araçlar ortak dil çalışma zamanının tüketebileceği bir çıktı üretebilir çünkü tür sistemi, meta veri biçimi ve çalışma zamanı ortamı (sanal yürütme sistemi) ECMA Ortak Dil Altyapı özelliği ortak standardına göre belirlenir. Daha fazla bilgi için bkz [. C# ECMA ve ortak dil altyapısı belirtimleri](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/).

Çalışma zamanının yönetilen koda hizmet sağlamasına olanak vermek için dil derleyicileri, kodunuzdaki başvuruları, üyeleri ve türleri açıklayan meta verileri yaymalıdır. Meta veriler kodla birlikte depolanır; her yüklenebilir ortak dil çalışma zamanı taşınabilir yürütülebilir (PE) dosyası meta verileri içerir. Çalışma zamanı, sınıfları bulmak ve yüklemek, bellekteki örnekleri açığa çıkarmak, yöntem çağrılarını çözümlemek, yerel kod oluşturmak, güvenlik sağlamak ve çalışma zamanı bağlam sınırlarını ayarlamak için meta verileri kullanır.

Çalışma zamanı, nesne düzenini otomatik olarak işler, nesne referanslarını yönetir ve onları artık kullanılmadıklarında serbest bırakır. Yaşam süreleri bu şekilde yönetilen nesnelere, yönetilen veri adı verilir. Çöp toplama, bellek sızıntılarını ve bazı diğer genel programlama hatalarını ortadan kaldırır. Kodunuz yönetiliyorsa, NET Framework uygulamanızda yönetilen verileri, yönetilmeyen verileri veya yönetilen ve yönetilmeyen verileri kullanabilirsiniz. Temel öğe türleri gibi dil oluşturucular kendi türlerini sağladığından verinizin yönetilip yönetilmediği her zaman bilmeyebilirsiniz (veya bilmeniz gerekmez).

Ortak dil çalışma zamanı, nesneleri diller arasında etkileşim kuran bileşenler ve uygulamalar tasarlanmasını kolaylaştırır. Farklı dillerde yazılan nesneler birbiriyle iletişim kurabilir ve davranışları sıkı bir şekilde tümleştirilebilir. Örneğin, bir sınıf tanımlayabilir ve ardından orijinal sınıfınızdan bir sınıf türetmek veya orijinal sınıfta bir yöntem çağırmak için farklı bir dil kullanabilirsiniz. Ayrıca sınıfın bir örneğini farklı dilde yazılmış bir sınıfın yöntemine iletebilirsiniz. Diller arası tümleştirme, dil derleyiciler ve çalışma zamanını hedefleyen araçlar çalışma zamanı tarafından tanımlanan ortak bir tür sistemi kullandığı ve çalışma zamanının yeni türleri tanımlama kurallarını, bunun yanı sıra türleri oluşturma, onları sürdürme ve onlara bağlama kurallarını izlediği için mümkündür.

Meta verilerinin bir bölümü olarak, tüm yönetilen bileşenler karşıt olarak oluşturuldukları bileşen ve kaynaklar hakkında bilgi taşırlar. Çalışma zamanı, bu bilgileri kullanarak bileşen veya uygulamanızın ihtiyaç duyduğu her şeyin belirtilen sürümlerine sahip olduğundan emin olur ve bu da kodunuzun karşılaşılmamış bir bağımlılık nedeniyle kırılma olasılığını azaltır. Kayıt bilgileri ve durum verileri, oluşturulmasının ve korunmasının zor olabileceği kayıt defterinde artık depolanmaz. Bunun yerine, tanımladığınız türler (ve bunların bağımlılıkları) hakkındaki bilgiler kod meta data olacak şekilde depolanır, böylece bileşenlerin çoğaltılması ve kaldırılması çok daha az karmaşık olur.

Dil derleyicileri ve araçları, çalışma zamanının işlevselliğini geliştiriciler için yararlı ve ilham verici olacak biçimlerde sağlar. Başka bir deyişle, çalışma zamanının bazı özellikleri bir ortamda diğerine kıyasla daha fazla dikkat çekebilir. Çalışma zamanı deneyiminiz hangi dil derleyicilerini veya araçlarını kullandığınıza bağlıdır. Örneğin, Visual Basic geliştiricisiyseniz, ortak dil çalışma zamanıyla Visual Basic dilinin eskiye göre daha fazla nesne yönelimli özelliği olduğunu görebilirsiniz. Çalışma zamanı, aşağıdaki avantajları sağlar:

- Performans geliştirmeleri.

- Diğer dillerde geliştirilen bileşenleri kolayca kullanma yeteneği.

- Sınıf kitaplığı tarafından sağlanan genişletilebilir türler.

- Devralma, arabirimler ve nesne tabanlı programlama için aşırı yükleme gibi dil özellikleri.

- Çok iş parçacıklı ve ölçeklenebilir uygulamaların oluşturulmasını sağlayan açık ve serbest iş parçacığı oluşturma desteği.

- Yapılandırılmış özel durum işleme desteği.

- Özel öznitelikler için destek.

- Çöp toplama.

- Artan tür güvenliği ve emniyeti için işlev işaretçileri yerine delegeler kullanın. Temsilciler hakkında daha fazla bilgi için bkz. [ortak tür sistemi](../../docs/standard/base-types/common-type-system.md).

## <a name="clr-versions"></a>CLR sürümleri

.NET Framework sürüm numarası, içerdiği CLR 'nin sürüm numarasına karşılık gelmez. .NET Framework sürümlerinin ve bunlara karşılık gelen CLR sürümlerinin listesi için, bkz. [.NET Framework sürümler ve bağımlılıklar](../framework/migration-guide/versions-and-dependencies.md). .NET Core sürümlerinin tek bir ürün sürümü vardır, diğer bir deyişle, ayrı bir CLR sürümü yoktur. .NET Core sürümlerinin listesi için bkz. [.NET Core 'U indirme](https://dotnet.microsoft.com/download/dotnet-core).

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Yönetilen Yürütme İşlemi](managed-execution-process.md)|Ortak dil çalışma zamanından yararlanmak için gereken adımları açıklar.|
|[Otomatik Bellek Yönetimi](automatic-memory-management.md)|Çöp toplayıcının belleği nasıl bölüştürdüğünü ve bıraktığını açıklar.|
|[.NET Framework genel bakış](../framework/get-started/overview.md)|Ortak tür sistemi, çapraz dil birlikte çalışabilirliği, yönetilen yürütme, uygulama etki alanları ve derlemeler gibi temel .NET Framework kavramlarını açıklar.|
|[Ortak Tür Sistemi](./base-types/common-type-system.md)|Diller arası tümleştirme desteğinde çalışma zamanında türlerin nasıl belirlendiğini, kullanıldığını ve yönetildiğini açıklar.|
