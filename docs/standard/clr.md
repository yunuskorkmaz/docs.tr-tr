---
title: Ortak dil çalışma zamanı (CLR) genel bakış - .NET Framework
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
author: rpetrusha
ms.author: ronpet
ms.custom: updateeachrelease
ms.openlocfilehash: 798b3d29a13434511f64dfc358fb7690948cacfa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59972959"
---
# <a name="common-language-runtime-clr-overview"></a>Ortak dil çalışma zamanı (CLR) genel bakış

.NET Framework kodu çalıştırır ve geliştirme işlemini kolaylaştıran hizmetler sağlayan ortak dil çalışma zamanı adlı bir çalışma zamanı ortamı sağlar.

Derleyiciler ve Araçlar ortak dil çalışma zamanının işlevselliğini gösterir ve bu yönetilen yürütme ortamından faydalanan kod yazmanızı sağlar. Yönetilen kod çalışma zamanını hedefleyen bir dil derleyici ile geliştirdiğiniz kodu çağrılır diller arası tümleştirme, diller arası özel durum işleme, Gelişmiş güvenlik, sürüm oluşturma ve dağıtım desteği, bileşen etkileşimi ve hata ayıklama ve profil oluşturma hizmetleri için basitleştirilmiş bir model gibi özelliklerden faydalanır.

> [!NOTE]
> Derleyiciler ve Araçlar tür sistemi, meta veri biçimi ve çalışma zamanı ortamı (sanal yürütme sistemi) tüm ortak standardına göre ECMA ortak dil tanımlı olduğundan, ortak dil çalışma zamanının tüketebileceği bir çıktı üretebilir. Altyapı belirtimi. Daha fazla bilgi için [ECMA C# ve ortak dil altyapısı belirtimleri](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/).

Çalışma zamanının yönetilen koda hizmet sağlamak üzere etkinleştirmek için dil derleyicileri, türleri, üyeleri ve kodunuzdaki başvuruları açıklayan meta verileri yaymalıdır. Meta veriler kodla birlikte depolanır; Her yüklenebilir ortak dil çalışma zamanı taşınabilir yürütülebilir (PE) dosya meta verileri içerir. Çalışma zamanı meta verileri bulun ve sınıfları yükleme örnekleri yerleştirme yöntem çağrılarını çözümlemek yerel kod üret güvenliği zorlamak ve çalışma zamanı bağlam sınırlarını ayarlamak için kullanır.

Otomatik olarak çalışma zamanı nesne düzenini işler ve artık kullanıldığı sırada bırakmadan nesnelere başvurular yönetir. Yaşam süreleri bu şekilde yönetilen nesnelere, yönetilen veri adı verilir. Çöp toplama, bellek sızıntıları ve bunun yanı sıra bazı diğer genel programlama hatalarını ortadan kaldırır. Kodunuz yönetiliyorsa, .NET Framework uygulamanızda yönetilen verileri, yönetilmeyen verileri veya hem yönetilen hem de yönetilmeyen verileri kullanabilirsiniz. Dil derleyicileri gibi ilkel türler, kendi türleri sağlamak için her zaman biliyorsanız (veya bilmeniz gereken) mı yönetiliyor.

Ortak dil çalışma zamanı, tasarım bileşenleri ve uygulamaları, nesneleri diller arasında etkileşim kuran kolaylaştırır. Farklı dillerde yazılan nesneler birbiriyle iletişim kurabilir ve davranışları sıkı bir şekilde tümleştirilebilir. Örneğin, bir sınıf tanımlayın ve ardından orijinal sınıfınızdan bir sınıf türetmek veya orijinal sınıfta bir yöntem çağırmak için farklı bir dil kullanın. Bir sınıfın bir örneği farklı bir dilde yazılmış bir sınıfın bir yönteme de geçirebilirsiniz. Bu diller arası tümleştirme nedeni, dil derleyiciler ve çalışma zamanını hedefleyen Araçlar çalışma zamanı tarafından tanımlanan bir ortak tür sistemi kullanın ve bunların çalışma zamanının yeni türleri tanımlama yanı sıra oluşturma, kullanma, kalıcı, kurallarına mümkündür ve bağlama türleri için.

Meta verilerinin bir parçası olarak, tüm yönetilen bileşenler oluşturuldukları kaynakları ve bileşenleri hakkında bilgi getirir. Çalışma zamanı bu bilgileri kullanarak bileşen veya uygulamanızın ihtiyaç duyduğu her şeyin belirtilen sürümlerine kodunuzun karşılaşılmamış bir bağımlılık nedeniyle sonu olma olasılığını getiren olduğundan emin olmak için kullanır. Kayıt bilgileri ve durum verileri nerede bunlar oluşturulmasının ve korunmasının zor olabilir kayıt defterinde artık depolanmaz. Bunun yerine, tanımladığınız türler (ve bunların bağımlılıklarını) hakkında bilgi kodla görevlerini bileşenlerin çoğaltılması ve kaldırılması çok daha az karmaşık hale meta veri depolanır.

Dil derleyicileri ve araçları, kullanışlı ve geliştiriciler için kullanımı kolay olacak şekilde tasarlanmıştır yollarla çalışma zamanının işlevselliğini kullanıma sunar. Başka bir deyişle çalışma zamanının bazı özellikleri, başka bir ortamda daha belirgin olması olabilir. Nasıl, çalışma zamanı deneyiminiz hangi dil derleyicilerini veya araçlarını kullandığınıza bağlıdır. Örneğin, Visual Basic geliştiricisiyseniz, ortak dil çalışma zamanı ile daha fazla nesne yönelimli özelliği daha önce Visual Basic dili olduğunu fark edebilirsiniz. Çalışma zamanı, aşağıdaki avantajları sağlar:

- Performans geliştirmeleri.

- Bileşenleri kolayca kullanma yeteneği, diğer dillerde geliştirilen.

- Bir sınıf kitaplığı tarafından sağlanan Genişletilebilir türler.

- Devralma, arabirimler ve nesne yönelimli programlama için aşırı yükleme gibi dil özellikleri.

- Çok iş parçacıklı ve ölçeklenebilir uygulamaların oluşturulmasını sağlayan açık serbest iş parçacığı oluşturma desteği.

- Yapılandırılmış özel durum işleme desteği.

- Özel öznitelikler için destek.

- Çöp toplama.

- Artan tür güvenliği ve emniyeti için işlev işaretçileri yerine delegeler kullanın. Temsilciler hakkında daha fazla bilgi için bkz. [ortak tür sistemi](../../docs/standard/base-types/common-type-system.md).

## <a name="clr-versions"></a>CLR sürümleri

.NET Framework sürüm numarasını mutlaka içerdiği CLR sürüm numarasını gelmiyor. Aşağıdaki tabloda, iki sürüm numarasının nasıl ilişkilendirmek gösterilmektedir:

|.NET Framework sürümü|CLR sürümünü içerir.|
|----------------------------|--------------------------|
|1.0|1.0|
|1.1|1.1|
|2,0|2,0|
|3.0|2,0|
|3.5|2,0|
|4|4|
|4.5 (4.5.1 ve 4.5.2'yi dahil)|4|
|4.6 (4.6.1 ve 4.6.2 dahil)|4|
|4.7 (4.7.1 ve 4.7.2 dahil)|4|
|4.8|4|

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Yönetilen Yürütme İşlemi](managed-execution-process.md)|Ortak dil çalışma zamanı yararlanmak için gereken adımları açıklar.|
|[Otomatik Bellek Yönetimi](automatic-memory-management.md)|Atık toplayıcı'nın ayırır ve belleği serbest bırakır nasıl açıklanmaktadır.|
|[.NET Framework'ün genel bakış](../framework/get-started/overview.md)|Ortak tür sistemi, çapraz dil birlikte çalışabilirliği, yönetilen yürütme, uygulama etki alanları ve derlemeler gibi temel .NET Framework kavramlarını açıklar.|
|[Ortak Tür Sistemi](./base-types/common-type-system.md)|Nasıl türleri bildirilen kullanılan ve yönetilen diller arası tümleştirme desteğinde çalışma zamanında açıklar.|

## <a name="see-also"></a>Ayrıca bkz.

- [Sürümler ve Bağımlılıklar](../framework/migration-guide/versions-and-dependencies.md)