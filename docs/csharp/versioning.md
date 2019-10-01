---
title: C#Sürüm oluşturma C# -kılavuz
description: Sürüm oluşturma 'nın ve .NET C# 'te nasıl çalıştığını anlama
ms.date: 01/08/2017
ms.assetid: aa8732d7-5cd0-46e1-994a-78017f20d861
ms.openlocfilehash: 4c0d5b5c2ac40cb27c90b4908623dc75b26a80cc
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699916"
---
# <a name="versioning-in-c"></a>C @ no__t 'de sürüm oluşturma-0

Bu öğreticide .NET 'teki sürüm oluşturmanın ne anlama geldiğini öğreneceksiniz. Ayrıca, kitaplığınızın sürümü oluşturulurken göz önünde bulundurmanız gereken faktörleri ve yeni bir kitaplık sürümüne yükseltmeyi öğreneceksiniz.

## <a name="authoring-libraries"></a>Yazma kitaplıkları

Genel kullanım için .NET kitaplıkları oluşturmuş olan bir geliştirici olarak, büyük olasılıkla yeni güncelleştirmeleri almanız gereken durumlarda olabilirsiniz. Bu süreç hakkında daha fazla bilgi için, var olan kodun kitaplığınızın yeni sürümüne sorunsuz bir şekilde geçişini sağlamak için ihtiyacınız olduğu için çok önemlidir. Yeni bir sürüm oluştururken göz önünde bulundurmanız gereken birkaç nokta vardır:

### <a name="semantic-versioning"></a>Anlamsal sürüm oluşturma

[Anlamsal sürüm oluşturma](https://semver.org/) (Short için semver), belirli kilometre taşı olaylarını belirtmek için kitaplığınızın sürümlerine uygulanan bir adlandırma kuralıdır.
İdeal olarak, kitaplığınıza verdiğiniz sürüm bilgileri, geliştiricilerin, aynı kitaplığın eski sürümlerini kullanan projelerle uyumluluğunu belirlemesine yardımcı olmalıdır.

SemVer 'e yönelik en temel yaklaşım, `MAJOR.MINOR.PATCH` olan 3 bileşen biçimidir, burada:

- uyumsuz API değişiklikleri yaptığınızda `MAJOR` artırılır
- `MINOR`, işlevselliği geriye doğru uyumlu bir şekilde eklediğinizde artırılır
- geriye dönük olarak uyumlu hata düzeltmeleri yaptığınızda `PATCH` artırılır

Sürüm bilgilerini .NET kitaplığınıza uygularken yayın öncesi sürümler gibi başka senaryolar da belirtmek için de çeşitli yollar vardır.

### <a name="backwards-compatibility"></a>Geriye dönük uyumluluk

Kitaplığınızın yeni sürümlerini serbest bırakmakta önceki sürümlerle geriye dönük uyumluluk, büyük ihtimalle önemli kaygılardan biri olacaktır.
Önceki sürüme bağımlı olan kodun yeniden derlenmesi sırasında, yeni sürümle birlikte çalışarak kitaplığınızın yeni bir sürümü önceki bir sürümle kaynak uyumludur. Eski sürüme bağımlı bir uygulama, yeniden derleme olmadan yeni sürümle birlikte çalışarak kitaplığınızın yeni bir sürümü ikili uyumludur.

Kitaplığınızın eski sürümleriyle geriye dönük uyumluluğu sürdürmeye çalışırken göz önünde bulundurmanız gereken bazı noktalar şunlardır:

- Sanal Yöntemler: sanal bir yöntemi yeni sürümünüzde sanal olmayan yaptığınızda, bu yöntemi geçersiz kılan projelerin güncelleştirilmesini sağlamak anlamına gelir. Bu çok büyük bir değişiklik ve kesinlikle önerilmez.
- Yöntem imzaları: bir yöntem davranışının güncelleştirilmesi için, imzasını da değiştirmeniz gerekir, bunun yerine bu yönteme çağrı yapan kodun çalışmaya devam etmesi için bir aşırı yükleme oluşturmanız gerekir.
Uygulamanın tutarlı kalması için yeni yöntem imzasını çağırmak üzere, eski yöntem imzasını her zaman değiştirebilirsiniz.
- [Artık kullanılmıyor özniteliği](programming-guide/concepts/attributes/common-attributes.md#Obsolete): Bu özniteliği kodunuzda kullanım dışı olan ve gelecekteki sürümlerde kaldırılacak olan sınıfları veya sınıf üyelerini belirtmek için kullanabilirsiniz. Bu, kitaplığınızı kullanan geliştiricilerin, son değişiklikler için daha iyi hazırlanmasını sağlar.
- İsteğe bağlı yöntem bağımsız değişkenleri: daha önce isteğe bağlı yöntem bağımsız değişkenlerini zorunlu yaptığınızda veya varsayılan değerlerini değiştirdiğinizde, bu bağımsız değişkenleri içermeyen tüm kodun güncellenmesi gerekecektir.

> [!NOTE]
> Zorunlu bağımsız değişkenleri isteğe bağlı hale getirmek, özellikle yöntemin davranışını değiştirmiyorsa çok az etkiye sahip olmalıdır.

Kullanıcılarınızın kitaplığınızın yeni sürümüne yükseltme yapmasını kolaylaştırır, daha önce yükseltebilecekleri büyük olasılıkla daha kolay olur.

### <a name="application-configuration-file"></a>Uygulama yapılandırma dosyası

Bir .NET geliştiricisi olarak çoğu proje türünde mevcut [`app.config` dosyası](../framework/configure-apps/file-schema/index.md) ile karşılaşmanız çok yüksek bir şansınız vardır.
Bu basit yapılandırma dosyası, yeni güncelleştirmelerin dağıtımını iyileştirmek için uzun bir yönteme gidebilirler. Genellikle kitaplıklarınızı düzenli olarak değişen bilgiler `app.config` dosyasında depolandığından, bu tür bilgiler güncelleştirilirken bu şekilde, eski sürümlerin yapılandırma dosyasının, yalnızca yeni bir dosya ile değiştirilmeleri gerekir. kitaplığın yeniden derlenmesi gerekiyor.

## <a name="consuming-libraries"></a>Kitaplıkları kullanma

Diğer geliştiriciler tarafından oluşturulan .NET kitaplıklarını tüketen bir geliştirici olarak, bir kitaplığın yeni bir sürümünün projenizle tamamen uyumlu olabileceğini ve genellikle kendi kodunuzu bu değişikliklerle çalışacak şekilde güncelleştirmek zorunda olduğunu fark edersiniz.

Sizin için Lucky ve C# .net ekosistemi, uygulamamızı, son değişiklikleri ortaya çıkaracak yeni kitaplıkların sürümleriyle çalışacak şekilde kolayca güncelleştirmenize imkan tanıyan özellikler ve teknikler sunar.

### <a name="assembly-binding-redirection"></a>Derleme bağlama yeniden yönlendirmesi

Uygulamanızın kullandığı bir kitaplığın sürümünü güncelleştirmek için *app. config* dosyasını kullanabilirsiniz. [*Bağlama yeniden yönlendirme*](../framework/configure-apps/redirect-assembly-versions.md)olarak adlandırılan öğesine ekleyerek, uygulamanızı yeniden derlemek zorunda kalmadan yeni kitaplık sürümünü kullanabilirsiniz. Aşağıdaki örnek, uygulamanızın *app. config* dosyasını, ilk olarak derlenmiş olan @no__t 3 sürümü yerine `ReferencedLibrary` ' nin `1.0.1` düzeltme eki sürümünü kullanacak şekilde nasıl güncelleşbileceğinizi gösterir.

```xml
<dependentAssembly>
    <assemblyIdentity name="ReferencedLibrary" publicKeyToken="32ab4ba45e0a69a1" culture="en-us" />
    <bindingRedirect oldVersion="1.0.0" newVersion="1.0.1" />
</dependentAssembly>
```

> [!NOTE]
> Bu yaklaşım yalnızca `ReferencedLibrary` ' ın yeni sürümü uygulamanız ile ikili dosya uyumluysa çalışır.
> Uyumluluk belirlenirken yapılan değişiklikler için yukarıdaki [geriye dönük uyumluluk](#backwards-compatibility) bölümüne bakın.

### <a name="new"></a>new

Bir temel sınıfın devralınan üyelerini gizlemek için `new` değiştiricisini kullanın. Bu, türetilmiş sınıfların temel sınıflarda güncelleştirmelere yanıt verebildiği bir yoldur.

Aşağıdaki örneği uygulayın:

[!code-csharp[Sample usage of the 'new' modifier](~/samples/csharp/versioning/new/Program.cs#sample)]

**Output**

```console
A base method
A derived method
```

Yukarıdaki örnekte, `DerivedClass` ' ın `BaseClass` ' de bulunan `MyMethod` yöntemini nasıl gizlediğini görebilirsiniz.
Bu, bir kitaplığın yeni sürümündeki bir temel sınıf türetilmiş sınıfınıza zaten mevcut olan bir üyeyi eklediğinde, temel sınıf üyesini gizlemek için yalnızca türetilmiş sınıf üyesinde `new` değiştiricisini kullanmanız gerektiğini gösterir.

@No__t-0 değiştiricisi belirtilmediğinde, türetilmiş bir sınıf varsayılan olarak bir temel sınıfta çakışan üyeleri gizleyecek, ancak derleyici uyarısı üretilse de kod derlenir. Bu, yalnızca varolan bir sınıfa yeni üye eklemek, kitaplığınızın bu yeni sürümünün hem kaynak hem de ikilinin buna bağlı kodla uyumlu olmasını sağlar.

### <a name="override"></a>override

@No__t-0 değiştiricisi, türetilmiş bir uygulamanın, bir temel sınıf üyesinin uygulamasını gizliyor yerine genişlettiği anlamına gelir. Temel sınıf üyesine `virtual` değiştiricisi uygulanmış olması gerekir.

[!code-csharp[Sample usage of the 'override' modifier](../../samples/csharp/versioning/override/Program.cs#sample)]

**Output**

```console
Base Method One: Method One
Derived Method One: Derived Method One
```

@No__t-0 değiştiricisi derleme zamanında değerlendirilir ve geçersiz kılmak için bir sanal üye bulamazsa derleyici bir hata oluşturur.

Ele alınan tekniklerin ve bunların hangi durumlardan hangilerinin kullanılacağını kavramanız, bir kitaplığın sürümleri arasında geçiş kolaylığı hızını artırmak için uzun bir yönteme gidecektir.
 
