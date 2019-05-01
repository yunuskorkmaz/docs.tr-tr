---
title: Güvenliği Saydam Kod
ms.date: 03/30/2017
helpviewer_keywords:
- transparent code
- security-transparent code
ms.assetid: 4f3dd841-82f7-4659-aab0-6d2db2166c65
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5cb528bbb4f85cd4502b4e2efabbcf592ac6bd0c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61868751"
---
# <a name="security-transparent-code"></a>Güvenliği Saydam Kod

<a name="top"></a>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

Güvenlik, etkileşen üç parça içerir: korumalı alana alma, izinler ve zorlama. Korumalı alana alma, tam olarak güvenilir ve diğer kodların korumalı bir alanda izinlerle kısıtlanmış olduğu yere bazı kod yalıtılmış etki alanları oluşturma uygulaması anlamına gelir. Korumalı alan izin kümesi içinde çalışan uygulama kodu, saydam olarak kabul edilir; diğer bir deyişle, güvenliği etkileyen herhangi bir işlem gerçekleştirilemiyor. Korumalı alan kanıt tarafından belirlenir kodların (<xref:System.Security.Policy.Evidence> sınıfı). Kanıt, korumalı alanlar hangi belirli izinleri gerektirir ve hangi tür korumalı alanların oluşturulabileceğini oluşturulabilir tanımlar. Zorlama yalnızca kendi izin kümesinde yürütmek için saydam kodu anlamındadır.

> [!IMPORTANT]
> Güvenlik İlkesi, .NET Framework'ün önceki sürümlerinde anahtar bir öğe bulunamadı. İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], güvenlik ilkesi kullanılmıyor. Güvenlik İlkesi saydamlığından güvenlik farklıdır. Bu değişikliğin etkileri hakkında daha fazla bilgi için bkz. [kod erişimi güvenliği ilkesi uyumluluğu ve geçiş](../../../docs/framework/misc/code-access-security-policy-compatibility-and-migration.md).

Bu konuda, saydamlık modeli daha ayrıntılı açıklanmaktadır. Aşağıdaki bölümleri içerir:

- [Saydamlık modelinin amacı](#purpose)

- [Saydamlık düzeyini belirtme](#level)

- [Saydamlığı zorlama](#enforcement)

<a name="purpose"></a>

## <a name="purpose-of-the-transparency-model"></a>Saydamlık Modelinin Amacı

Saydamlık altyapısının bir parçası çalışan kodu uygulamadan bir parçası olarak çalışan koddan ayıran zorlama mekanizmasıdır. Saydamlık arama yerel kodu gibi ayrıcalıklı işler (kritik kod) yapmak için kodu ve kod (saydam kod) olamaz arasında bir engel çizer. Saydam kod komutları, çalışan bir izin kümesi sınırları içinde ancak olamaz yürütün, öğesinden türetilen veya kritik kod içeriyor.

Saydamlık uygulatma işleminin birincil amacı, farklı ayrıcalık tabanlı kod gruplarını yalıtmak için basit ve etkili bir mekanizma sağlamaktır. Korumalı alana alma modeli bağlamında, bu ayrıcalık gruplarına ya da olan tam güvenilir (yani değil sınırlıdır) veya kısmen güvenilir (diğer bir deyişle, izin verilen korumalı alan kümesini sınırlı).

> [!IMPORTANT]
> Saydamlık modeli, kod erişim güvenliğini aşıyor. Saydamlık tam zamanında derleyici tarafından zorlanır ve tam güven de dahil olmak üzere bir derleme için ayarlanmış vermeler bağımsız olarak yürürlükte kalır.

Saydamlık, .NET Framework 2.0 sürümünde güvenlik modelini basitleştirmek ve yazma ve güvenli kitaplıkları ve uygulamaları dağıtma daha kolay hale getirmek için kullanılmaya başlandı. Saydam kod kısmen güvenilir uygulamaların geliştirilmesini basitleştirmek için Microsoft Silverlight uygulamasında da kullanılır.

> [!NOTE]
> Kısmen güvenilen bir uygulama geliştirirken, hedef ana bilgisayarlarınızın izin gereksinimleri bilmeniz gerekir. Bazı ana bilgisayarlar tarafından izin verilmeyen kaynakları kullanan bir uygulama geliştirebilirsiniz. Bu uygulama hatasız derlenir, ancak barındırılan ortama yüklendiğinde başarısız olur. Visual Studio kullanarak uygulama geliştirdiyseniz, geliştirme ortamından ayarlanan sınırlı izin kümesinde veya kısmi güvende hata ayıklamayı etkinleştirebilirsiniz. Daha fazla bilgi için [nasıl yapılır: Sınırlı izinler ile ClickOnce uygulamasında hata ayıklama](/visualstudio/deployment/how-to-debug-a-clickonce-application-with-restricted-permissions). ClickOnce uygulamaları için sağlanan hesaplama izinleri özelliği kısmen güvenilen uygulamalar için de kullanılabilir.

[Başa dön](#top)

<a name="level"></a>

## <a name="specifying-the-transparency-level"></a>Saydamlık Düzeyini Belirtme

Derleme düzeyi <xref:System.Security.SecurityRulesAttribute> öznitelik açıkça seçer <xref:System.Security.SecurityRuleSet> derlemenin izleyeceği kuralları. Kuralları nerede yüksek düzeyler güvenlik kurallarının daha sıkı zorlama ortalama bir sayısal düzey sistemi altında düzenlenir.

Düzeyler şunlardır:

- 2. düzey (<xref:System.Security.SecurityRuleSet.Level2>) – [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] saydamlık kuralları.

- Düzey 1 (<xref:System.Security.SecurityRuleSet.Level1>) – .NET Framework 2.0 saydamlık kuralları.

İki saydamlık düzeyi arasındaki başlıca fark, düzey 1'ın derlemenin dışından çağrılar için saydamlık kuralları uygulamaması ve yalnızca uyumluluk için tasarlanmış olan.

> [!IMPORTANT]
> Yalnızca uyumluluk için düzey 1 saydamlığını belirtmelisiniz; diğer bir deyişle, kullandığı .NET Framework 3.5 veya daha önce geliştirilmiştir yalnızca kod için düzey 1 belirtin <xref:System.Security.AllowPartiallyTrustedCallersAttribute> özniteliği veya saydamlık modeli kullanmayan. Örneğin, kısmen güvenilmeyen çağrıcılara (APTCA) gelen çağrıları izin veren .NET Framework 2.0 derlemeleri için seviye 1 saydamlık kullanın. İçin geliştirilmiş kod için [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], her zaman Düzey 2 Asetatını kullanın.

### <a name="level-2-transparency"></a>Düzey 2 saydamlık

Düzey 2 saydamlık öğesinde tanıtılmıştır [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Bu modelin üç İlkesi saydam kod güvenlik güvenli kritik kod ve güvenlik açısından kritik kod ' dir.

- (Tam güven dahil), verilen izinleri bakılmaksızın saydam kod, yalnızca diğer saydam kodu veya güvenli-kritik kodu çağırabilir. Kod kısmen güvenilen ise, yalnızca etki alanı izin kümesi tarafından izin verilen eylemleri gerçekleştirebilir. Saydam kod aşağıdaki işlemleri yapamaz:

  - Gerçekleştirmek bir <xref:System.Security.CodeAccessPermission.Assert%2A> işlemi veya ayrıcalık yükseltme.

  - Güvenli olmayan veya doğrulanamaz kod içerir.

  - Doğrudan kritik kodu çağırın.

  - Sahip kodu veya yerel koda çağrı <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> özniteliği.

  - Tarafından korunan üyeyi çağırın bir <xref:System.Security.Permissions.SecurityAction.LinkDemand>.

  - Kritik türlerden devral

    Ayrıca, saydam yöntemleri kritik sanal yöntemleri geçersiz kılmaz veya kritik arabirim yöntemlerini uygulamaz.

- Güvenlik-güvenli-kritik kodu tam olarak güvenilirdir ancak saydam kod tarafından çağrılabilir. Bu, tam güven kodu sınırlı yüzey alanı sunar. Düzeltmeler ve güvenlik doğrulamaları güvenli kritik kodda olur.

- Güvenlik açısından kritik kod, herhangi bir kodu çağırabilir ve tam olarak güvenilirdir ancak saydam kod tarafından çağrılamaz.

### <a name="level-1-transparency"></a>Düzey 1 Saydamlık

Düzey 1 saydamlık modeli, geliştiricilerin bir güvenlik denetimine tâbi kod miktarını azaltmak için .NET Framework sürüm 2.0 kullanılmaya başlandı. Düzey 1 saydamlık, 2.0 sürümünde genel olarak kullanılabilir olmasına rağmen güvenlik denetimi amacıyla yalnızca Microsoft'ta öncelikli olarak kullanıldığı. Ek açıklamalar aracılığıyla, geliştiriciler hangi türlerin ve üyelerin güvenlik yükseltmeleri ve diğer güvenilir eylemleri (güvenlik açısından kritik) gerçekleştirebileceği hangi (güvenlik açısından saydam) gerçekleştiremeyeceğini. Saydam olarak tanımlanan kod, yüksek derecede güvenlik denetimi, gerektirmez. Düzey 1 saydamlık, saydamlık zorlamanın derleme içinde sınırlı olduğunu belirtir. Diğer bir deyişle, herhangi bir genel türler ve güvenlik açısından kritik olarak tanımlanan üyeleri yalnızca derleme içinde güvenlik açısından kritik. Bunlar gelen derlemenin dışından çağrıldığında bu türler ve üyeler için güvenliği zorlamak istiyorsanız, tam güven için bağlantı isteklerini kullanmanız gerekir. Bunu yapmazsanız, herkese görünür kritik güvenlik türleri ve üyeleri güvenlik-güvenli-kritik olarak kabul edilir ve derleme dışından kısmen güvenilen kod tarafından çağrılabilir.

Düzey 1 saydamlık modelinde aşağıdaki sınırlamalar bulunmaktadır:

- Kritik güvenlik türleri ve genel olan üyelere güvenlik açısından saydam koddan erişilebilir.

- Saydamlık ek açıklamaları yalnızca bir derlemenin içinde uygulanır.

- Güvenlik açısından kritik türler ve üyeler derlemenin dışından çağrılar için güvenliği zorlamak için bağlantı talepleri kullanmanız gerekir.

- Devralma kuralları zorunlu kılınmaz.

- Saydam kod tam güvende çalıştırıldığında zararlı işlemler yapma olasılığı vardır.

[Başa dön](#top)

<a name="enforcement"></a>

## <a name="transparency-enforcement"></a>Saydamlığı Zorlama

Saydamlık kuralları saydamlık hesaplanana kadar zorlanmaz. O zaman bir <xref:System.InvalidOperationException> saydamlık kuralı ihlal edilirse oluşturulur. Saydamlığın hesaplandığı zaman pek çok unsura bağlıdır ve tahmin edilemez. En geç hesaplanır. İçinde [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], montaj düzeyi saydamlık hesaplaması .NET Framework 2.0 sürümünde vermiyor daha çabuk ortaya çıkar. Tek garanti, saydamlık hesaplama gerekli olduğu zamana göre gerçekleşmesidir. Bu, nasıl just-ın-time (JIT) derleyici noktası bir yöntem derlendiğinde ve bu yöntemde herhangi bir hata algılandığında değiştirmesine benzer. Saydamlık hesaplama kodunuzu saydamlık hatası yoksa görünmez durumdadır.

## <a name="see-also"></a>Ayrıca bkz.

- [Güvenliği saydam kod, düzey 1](../../../docs/framework/misc/security-transparent-code-level-1.md)
- [Güvenliği saydam kod, Düzey 2](../../../docs/framework/misc/security-transparent-code-level-2.md)
