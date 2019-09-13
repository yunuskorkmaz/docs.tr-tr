---
title: C#Sürüm oluşturma C# -kılavuz
description: Sürüm oluşturma 'nın ve .NET C# 'te nasıl çalıştığını anlama
ms.date: 01/08/2017
ms.assetid: aa8732d7-5cd0-46e1-994a-78017f20d861
ms.openlocfilehash: bfad7abe6b2b5c6a19324656963a79212a317110
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926588"
---
# <a name="versioning-in-c"></a>C 'de sürüm oluşturma\#

Bu öğreticide .NET 'teki sürüm oluşturmanın ne anlama geldiğini öğreneceksiniz. Ayrıca, kitaplığınızın sürümü oluşturulurken göz önünde bulundurmanız gereken faktörleri ve yeni bir kitaplık sürümüne yükseltmeyi öğreneceksiniz.

## <a name="authoring-libraries"></a>Yazma kitaplıkları

Genel kullanım için .NET kitaplıkları oluşturmuş olan bir geliştirici olarak, büyük olasılıkla yeni güncelleştirmeleri almanız gereken durumlarda olabilirsiniz. Bu süreç hakkında daha fazla bilgi için, var olan kodun kitaplığınızın yeni sürümüne sorunsuz bir şekilde geçişini sağlamak için ihtiyacınız olduğu için çok önemlidir. Yeni bir sürüm oluştururken göz önünde bulundurmanız gereken birkaç nokta vardır:

### <a name="semantic-versioning"></a>Anlamsal sürüm oluşturma

[Anlamsal sürüm oluşturma](https://semver.org/) (Short için SemVer), belirli kilometre taşı olaylarını belirtmek için kitaplığınızın sürümlerine uygulanan bir adlandırma kuralıdır.
İdeal olarak, kitaplığınıza verdiğiniz sürüm bilgileri, geliştiricilerin, aynı kitaplığın eski sürümlerini kullanan projelerle uyumluluğunu belirlemesine yardımcı olmalıdır.

Semver 'e en temel yaklaşım, burada 3 bileşen biçimidir `MAJOR.MINOR.PATCH`:

* `MAJOR`uyumsuz API değişiklikleri yaptığınızda artırılır
* `MINOR`işlevselliği geriye dönük olarak uyumlu bir şekilde eklediğinizde artırılır
* `PATCH`, geriye dönük olarak uyumlu hata düzeltmeleri yaptığınızda artırılır

Sürüm bilgilerini .NET kitaplığınıza uygularken yayın öncesi sürümler gibi başka senaryolar da belirtmek için de çeşitli yollar vardır.

### <a name="backwards-compatibility"></a>Geriye dönük uyumluluk

Kitaplığınızın yeni sürümlerini serbest bırakmakta önceki sürümlerle geriye dönük uyumluluk, büyük ihtimalle önemli kaygılardan biri olacaktır.
Önceki sürüme bağımlı olan kodun yeniden derlenmesi sırasında, yeni sürümle birlikte çalışarak kitaplığınızın yeni bir sürümü önceki bir sürümle kaynak uyumludur. Eski sürüme bağımlı bir uygulama, yeniden derleme olmadan yeni sürümle birlikte çalışarak kitaplığınızın yeni bir sürümü ikili uyumludur.

Kitaplığınızın eski sürümleriyle geriye dönük uyumluluğu sürdürmeye çalışırken göz önünde bulundurmanız gereken bazı noktalar şunlardır:

* Sanal Yöntemler: Yeni sürümünüzde sanal olmayan bir sanal yöntem yaptığınızda, bu yöntemi geçersiz kılan projelerin güncelleştirilmesini sağlamak anlamına gelir. Bu çok büyük bir değişiklik ve kesinlikle önerilmez.
* Yöntem imzaları: Bir yöntem davranışını güncelleştirirken, onun imzasını da değiştirmeniz gerekir, bunun yerine bu yönteme çağrı yapan kodun çalışmaya devam etmesi için bir aşırı yükleme oluşturmanız gerekir.
Uygulamanın tutarlı kalması için yeni yöntem imzasını çağırmak üzere, eski yöntem imzasını her zaman değiştirebilirsiniz.
* [Eski öznitelik](programming-guide/concepts/attributes/common-attributes.md#Obsolete): Bu özniteliği kodunuzda bu özniteliği kullanarak kullanım dışı olan sınıfları veya sınıf üyelerini, gelecekteki sürümlerde de kaldırılmasını belirtebilirsiniz. Bu, kitaplığınızı kullanan geliştiricilerin, son değişiklikler için daha iyi hazırlanmasını sağlar.
* İsteğe bağlı yöntem bağımsız değişkenleri: Daha önce isteğe bağlı yöntem bağımsız değişkenlerini zorunlu yaptığınızda veya varsayılan değerlerini değiştirirseniz, bu bağımsız değişkenleri sağlamadan tüm kodun güncellenmesi gerekecektir.

> [!NOTE]
> Zorunlu bağımsız değişkenleri isteğe bağlı hale getirmek, özellikle yöntemin davranışını değiştirmiyorsa çok az etkiye sahip olmalıdır.

Kullanıcılarınızın kitaplığınızın yeni sürümüne yükseltme yapmasını kolaylaştırır, daha önce yükseltebilecekleri büyük olasılıkla daha kolay olur.

### <a name="application-configuration-file"></a>Uygulama yapılandırma dosyası

Bir .net geliştiricisi olarak çoğu proje türünde mevcut olan [ `app.config` dosyayla](../framework/configure-apps/file-schema/index.md) karşılaşmanız çok yüksek bir şansınız vardır.
Bu basit yapılandırma dosyası, yeni güncelleştirmelerin dağıtımını iyileştirmek için uzun bir yönteme gidebilirler. Genellikle kitaplıklarınızı düzenli olarak değişen bilgiler `app.config` dosyada depolandığından, bu şekilde, bu bilgilerin daha eski sürümlerin yapılandırma dosyası güncelleştiriliyorsa yalnızca yeni bir sürüm ile değiştirilmeleri gerekir. Kitaplığı yeniden derlemek zorunda kalmadan.

## <a name="consuming-libraries"></a>Kitaplıkları kullanma

Diğer geliştiriciler tarafından oluşturulan .NET kitaplıklarını tüketen bir geliştirici olarak, bir kitaplığın yeni bir sürümünün projenizle tamamen uyumlu olabileceğini ve genellikle kendi kodunuzu bu değişikliklerle çalışacak şekilde güncelleştirmek zorunda olduğunu fark edersiniz.

Sizin C# için Lucky ve .net ekosistemi, uygulamamızı, son değişiklikleri ortaya çıkaracak yeni kitaplıkların sürümleriyle çalışacak şekilde kolayca güncelleştirmenize imkan tanıyan özellikler ve teknikler sunar.

### <a name="assembly-binding-redirection"></a>Derleme bağlama yeniden yönlendirmesi

Uygulamanızın kullandığı bir kitaplığın `app.config` sürümünü güncelleştirmek için dosyasını kullanabilirsiniz. [*Bağlama yeniden yönlendirme*](../framework/configure-apps/redirect-assembly-versions.md) olarak adlandırılan öğesine ekleyerek, uygulamanızı yeniden derlemek zorunda kalmadan yeni kitaplık sürümünü kullanabilirsiniz. Aşağıdaki örnek, uygulamasının ilk `app.config` olarak derlenmiş `1.0.0` sürümü `ReferencedLibrary` yerine `1.0.1` düzeltme eki sürümünü kullanmak için uygulamanızın dosyasını nasıl güncelleşbileceğinizi gösterir.

```xml
<dependentAssembly>
    <assemblyIdentity name="ReferencedLibrary" publicKeyToken="32ab4ba45e0a69a1" culture="en-us" />
    <bindingRedirect oldVersion="1.0.0" newVersion="1.0.1" />
</dependentAssembly>
```

> [!NOTE]
> Bu yaklaşım, yalnızca yeni sürümü `ReferencedLibrary` uygulamanız ile uyumluysa çalışır.
> Uyumluluk belirlenirken yapılan değişiklikler için yukarıdaki [geriye dönük uyumluluk](#backwards-compatibility) bölümüne bakın.

### <a name="new"></a>new

Bir temel sınıfın `new` devralınan üyelerini gizlemek için değiştiricisini kullanın. Bu, türetilmiş sınıfların temel sınıflarda güncelleştirmelere yanıt verebildiği bir yoldur.

Aşağıdaki örneği uygulayın:

[!code-csharp[Sample usage of the 'new' modifier](../../samples/csharp/versioning/new/Program.cs#sample)]

**Output**

```
A base method
A derived method
```

Yukarıdaki örnekte, ' de `DerivedClass` `BaseClass`bulunan `MyMethod` yöntemin nasıl gizlediğini görebilirsiniz.
Bu, bir kitaplığın yeni sürümündeki bir temel sınıf, türetilmiş sınıfınıza zaten mevcut olan bir üyeyi eklediğinde, taban sınıf üyesini gizlemek için yalnızca türetilmiş sınıf üyeinizdeki `new` değiştiriciyi kullanmanız gerektiğini gösterir.

`new` Değiştirici belirtilmediğinde, türetilmiş bir sınıf varsayılan olarak bir temel sınıfta çakışan üyeleri gizleyecek, ancak derleyici uyarısı üretilse de kod derlenmeye devam eder. Bu, yalnızca varolan bir sınıfa yeni üye eklemek, kitaplığınızın bu yeni sürümünün hem kaynak hem de ikilinin buna bağlı kodla uyumlu olmasını sağlar.

### <a name="override"></a>override

`override` Değiştirici türetilmiş bir uygulamanın, bir temel sınıf üyesinin uygulamasını gizliyor yerine genişlettiği anlamına gelir. Temel sınıf üyesine `virtual` değiştiriciye uygulanmış olması gerekir.

[!code-csharp[Sample usage of the 'override' modifier](../../samples/csharp/versioning/override/Program.cs#sample)]

**Output**

```
Base Method One: Method One
Derived Method One: Derived Method One
```

`override` Değiştirici derleme zamanında değerlendirilir ve geçersiz kılmak için bir sanal üye bulamazsa derleyici bir hata oluşturur.

Ele alınan tekniklerin ve bunların hangi durumlardan hangilerinin kullanılacağını kavramanız, bir kitaplığın sürümleri arasında geçiş kolaylığı hızını artırmak için uzun bir yönteme gidecektir.
 