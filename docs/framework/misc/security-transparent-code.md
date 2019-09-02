---
title: Güvenliği Saydam Kod
ms.date: 03/30/2017
helpviewer_keywords:
- transparent code
- security-transparent code
ms.assetid: 4f3dd841-82f7-4659-aab0-6d2db2166c65
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4e4e472185b3b2ba39393c029bca3966fb5ec4b3
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70206060"
---
# <a name="security-transparent-code"></a>Güvenliği Saydam Kod

<a name="top"></a>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

Güvenlik üç etkileşen parçadan oluşur: korumalı alana alma, izinler ve zorlama. Korumalı alana alma, bazı kodların tamamen güvenilir olarak işlendiği ve diğer kodun, korumalı alan için izin kümesindeki izinlerle kısıtlandığı yalıtılmış etki alanları oluşturma uygulaması anlamına gelir. Korumalı alanın izin kümesi içinde çalışan uygulama kodu saydam olarak kabul edilir; diğer bir deyişle, güvenliği etkileyebilecek herhangi bir işlem gerçekleştiremez. Korumalı alan için izin kümesi kanıt (<xref:System.Security.Policy.Evidence> sınıf) tarafından belirlenir. Kanıt, korumalı alanlar için hangi belirli izinlerin gerekli olduğunu ve ne tür bir sanal alanının oluşturulabileceğini belirler. Zorlama, saydam kodun yalnızca kendi izin kümesi içinde yürütülmesine izin vermeyi ifade eder.

> [!IMPORTANT]
> Güvenlik ilkesi, önceki .NET Framework sürümlerindeki bir anahtar öğesidir. .NET Framework 4 ' te başlayarak güvenlik ilkesi artık kullanılmıyor. Güvenlik ilkesinin Eleme işlemi güvenlik saydamlığına göre ayrıdır. Bu değişikliğin etkileri hakkında daha fazla bilgi için bkz. [kod erişimi güvenlik Ilkesi uyumluluğu ve geçişi](code-access-security-policy-compatibility-and-migration.md).

Bu konu başlığı altında saydamlık modeli daha ayrıntılı olarak açıklanmaktadır. Aşağıdaki bölümleri içerir:

- [Saydamlık modelinin amacı](#purpose)

- [Saydamlık düzeyini belirtme](#level)

- [Saydamlık zorlaması](#enforcement)

<a name="purpose"></a>

## <a name="purpose-of-the-transparency-model"></a>Saydamlık Modelinin Amacı

Saydamlık, altyapının bir parçası olarak çalışan koddan uygulamanın bir parçası olarak çalışan kodu ayıran bir zorlama mekanizmasıdır. Saydamlık, yerel kodu çağırma gibi ayrıcalıklı şeyler (kritik kod) ve (saydam kod) olmayan kod arasında, kod arasında bir engel çizer. Saydam kod, komutları üzerinde çalıştığı izin kümesi sınırları içinde yürütebilir, ancak kritik kodu yürütülemez, onlardan türetemez veya içeremez.

Saydamlık zorlamasının birincil amacı, farklı kod gruplarını ayrıcalığa göre yalıtmak için basit ve etkili bir mekanizma sağlamaktır. Korumalı alana alma modelinin bağlamı içinde, bu ayrıcalık grupları tamamen güvenilir (yani, sınırlı değil) veya kısmen güvenilir (yani, korumalı alana verilen izin kümesiyle kısıtlıdır).

> [!IMPORTANT]
> Saydamlık modeli kod erişim güvenliğini geri sarar. Saydamlık, tam zamanında derleyici tarafından zorlanır ve tam güven dahil olmak üzere derleme için izin kümesine bakılmaksızın geçerli olmaya devam eder.

Saydamlık, güvenlik modelini basitleştirmek ve güvenli kitaplık ve uygulama yazmayı ve dağıtmayı kolaylaştırmak için .NET Framework sürüm 2,0 ' de tanıtılmıştı. Saydam kod ayrıca, kısmen güvenilen uygulamaların geliştirilmesini basitleştirmek için Microsoft Silverlight 'ta de kullanılır.

> [!NOTE]
> Kısmen güvenilen bir uygulama geliştirdiğinizde, hedef konaklarınızın izin gereksinimlerini bilmeniz gerekir. Bazı konaklar tarafından izin verilmeyen kaynakları kullanan bir uygulama geliştirebilirsiniz. Bu uygulama hata olmadan derlenir, ancak barındırılan ortama yüklendiğinde başarısız olur. Uygulamanızı Visual Studio kullanarak geliştirdiyseniz, kısmi güvende veya geliştirme ortamından kısıtlı bir izin kümesinde hata ayıklamayı etkinleştirebilirsiniz. Daha fazla bilgi için [nasıl yapılır: Kısıtlanmış Izinlerle](/visualstudio/deployment/how-to-debug-a-clickonce-application-with-restricted-permissions)ClickOnce uygulamasında hata ayıklayın. ClickOnce uygulamaları için sağlanan Izinleri hesapla özelliği, kısmen güvenilen bir uygulama için de kullanılabilir.

[Başa dön](#top)

<a name="level"></a>

## <a name="specifying-the-transparency-level"></a>Saydamlık Düzeyini Belirtme

Derleme düzeyi <xref:System.Security.SecurityRulesAttribute> özniteliği, derlemenin takip olacağı <xref:System.Security.SecurityRuleSet> kuralları açıkça seçer. Kurallar sayısal düzey bir sistem altında düzenlenir ve daha yüksek düzeyler güvenlik kurallarının daha sıkı bir şekilde zorlanmasını demektir.

Düzeyler şunlardır:

- Düzey 2 (<xref:System.Security.SecurityRuleSet.Level2>) – .NET Framework 4 Saydamlık kuralları.

- Düzey 1 (<xref:System.Security.SecurityRuleSet.Level1>) – .NET Framework 2,0 saydamlık kuralları.

İki saydamlık düzeyi arasındaki birincil fark, düzey 1 ' in, derleme dışından yapılan çağrılar için saydamlık kurallarını zorlayamadığını ve yalnızca uyumluluk için tasarlanmıştır.

> [!IMPORTANT]
> Düzey 1 saydamlığı yalnızca uyumluluk için belirtmelisiniz; diğer bir deyişle, yalnızca düzey 1 ' i yalnızca <xref:System.Security.AllowPartiallyTrustedCallersAttribute> özniteliği kullanan veya saydamlık modelini kullanmayan .NET Framework 3,5 veya önceki bir sürümüyle geliştirilmiş kod için belirtin. Örneğin, kısmen güvenilen çağıranların (APTCA) çağrılara izin veren .NET Framework 2,0 derlemeleri için düzey 1 saydamlığı kullanın. .NET Framework 4 için geliştirilen kod için her zaman düzey 2 saydamlığı kullanın.

### <a name="level-2-transparency"></a>Düzey 2 saydamlık

Düzey 2 saydamlık .NET Framework 4 ' te tanıtılmıştı. Bu modelin üç listesi saydam kod, güvenli güvenlik açısından kritik kod ve güvenlik açısından kritik koddur.

- Saydam kod, verilen izinlerden bağımsız olarak (tam güven dahil), yalnızca diğer saydam kodu veya güvenlik açısından güvenli kritik kodu çağırabilir. Kod kısmen güvenilirse, yalnızca etki alanının izin kümesi tarafından izin verilen eylemleri gerçekleştirebilir. Saydam kod şunları yapılamıyor:

  - Bir <xref:System.Security.CodeAccessPermission.Assert%2A> işlem veya ayrıcalık yükselmesi gerçekleştirin.

  - Güvenli olmayan veya doğrulanamayan kod içeriyor.

  - Kritik kodu doğrudan çağırın.

  - <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> Özniteliği olan yerel kodu veya kodu çağırın.

  - Tarafından korunan bir üyeyi çağırın <xref:System.Security.Permissions.SecurityAction.LinkDemand>.

  - Kritik türlerden devralma.

    Ayrıca, saydam Yöntemler kritik sanal yöntemleri geçersiz kılamaz veya kritik arabirim yöntemleri uygulayamaz.

- Güvenli kritik kod, tamamen güvenilirdir ancak saydam kod tarafından çağrılabilir. Tam güven kodu sınırlı bir yüzey alanı sunar. Güvenli kritik kodda doğruluk ve güvenlik doğrulamaları meydana gelir.

- Güvenlik açısından kritik kod herhangi bir kodu çağırabilir ve tamamen güvenilirdir, ancak saydam kod tarafından çağrılamaz.

### <a name="level-1-transparency"></a>Düzey 1 Saydamlık

Düzey 1 saydamlık modeli, geliştiricilerin bir güvenlik denetimine tabi olan kod miktarını azaltmasını sağlamak için .NET Framework sürüm 2,0 ' de tanıtılmıştır. Düzey 1 saydamlığın sürümü 2,0 ' de herkese açık olmasına rağmen, bu, öncelikli olarak yalnızca Microsoft 'un güvenlik denetimi amaçlarıyla kullanılmıştı. Ek açıklamalar aracılığıyla, geliştiriciler hangi türlerin ve üyelerin güvenlik yükseltmeleri ve diğer güvenilir eylemleri (güvenlik açısından kritik) gerçekleştirebilmesini ve hangilerinin (güvenlik açısından saydam) gerçekleştirebilmesini bildirebilirler. Saydam olarak tanımlanan kod, yüksek derecede güvenlik denetimi gerektirmez. Düzey 1 saydamlık, saydamlık zorlamasının derleme dahilinde sınırlı olduğunu belirtir. Diğer bir deyişle, güvenlik açısından kritik olarak tanımlanan genel türler veya Üyeler yalnızca derleme içinde güvenlik açısından kritik öneme sahiptir. Bu türler ve Üyeler, derleme dışından çağrıldığında güvenliği zorlamak istiyorsanız, tam güven için bağlantı taleplerini kullanmanız gerekir. Aksi takdirde, herkese açık güvenlik açısından kritik türler ve Üyeler güvenlik açısından kritik olarak değerlendirilir ve derleme dışında kısmen güvenilen kod tarafından çağrılabilir.

Düzey 1 saydamlık modeli aşağıdaki sınırlamalara sahiptir:

- Güvenlik açısından kritik türler ve ortak olan üyelere güvenlik açısından saydam koddan erişilebilir.

- Saydamlık ek açıklamaları yalnızca bir bütünleştirilmiş kod içinde zorlanır.

- Güvenlik açısından kritik türler ve üyelerin, derleme dışından çağrılar için güvenliği zorlamak üzere bağlantı taleplerini kullanması gerekir.

- Devralma kuralları zorlanmaz.

- Bu olası, tam güvende çalıştırıldığında zararlı işlemler yapmak için saydam kod vardır.

[Başa dön](#top)

<a name="enforcement"></a>

## <a name="transparency-enforcement"></a>Saydamlığı Zorlama

Saydamlık kuralları, saydamlık hesaplanana kadar zorlanmaz. Bu sırada, bir saydamlık <xref:System.InvalidOperationException> kuralı ihlal edilirse bir oluşturulur. Saydamlığın hesaplandığı zaman, birden fazla etkene bağlıdır ve tahmin edilemez. Mümkün olduğunca geç hesaplanır. .NET Framework 4 ' te, derleme düzeyi saydamlık hesaplaması, .NET Framework 2,0 ' de bulunandan daha erken gerçekleşir. Tek garanti, saydamlık hesaplamasının gerekli olduğu zamana göre gerçekleşeceğdir. Bu, Just-In-Time (JıT) derleyicisinin bir yöntem derlendiğinde ve bu yöntemdeki herhangi bir hata algılandığında noktayı değiştireme yöntemine benzer. Kodunuzda saydamlık hatası yoksa saydamlık hesaplaması görünmez.

## <a name="see-also"></a>Ayrıca bkz.

- [Güvenliği saydam kod, düzey 1](security-transparent-code-level-1.md)
- [Güvenliği saydam kod, düzey 2](security-transparent-code-level-2.md)
