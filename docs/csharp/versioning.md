---
title: C#Sürüm oluşturma C# -kılavuz
description: Sürüm oluşturma 'nın ve .NET C# 'te nasıl çalıştığını anlama
ms.date: 01/08/2017
ms.technology: csharp-advanced-concepts
ms.assetid: aa8732d7-5cd0-46e1-994a-78017f20d861
ms.openlocfilehash: ee123893ac8baa0a55bdf69ce49fb6fcb87601b4
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240008"
---
# <a name="versioning-in-c"></a>C\# sürümünde sürüm oluşturma

Bu öğreticide .NET 'teki sürüm oluşturmanın ne anlama geldiğini öğreneceksiniz. Ayrıca, kitaplığınızın sürümü oluşturulurken göz önünde bulundurmanız gereken faktörleri ve yeni bir kitaplık sürümüne yükseltmeyi öğreneceksiniz.

## <a name="authoring-libraries"></a>Yazma kitaplıkları

Genel kullanım için .NET kitaplıkları oluşturmuş olan bir geliştirici olarak, büyük olasılıkla yeni güncelleştirmeleri almanız gereken durumlarda olabilirsiniz. Bu süreç hakkında daha fazla bilgi için, var olan kodun kitaplığınızın yeni sürümüne sorunsuz bir şekilde geçişini sağlamak için ihtiyacınız olduğu için çok önemlidir. Yeni bir sürüm oluştururken göz önünde bulundurmanız gereken birkaç nokta vardır:

### <a name="semantic-versioning"></a>Anlamsal sürüm oluşturma

[Anlamsal sürüm oluşturma](https://semver.org/) (Short için semver), belirli kilometre taşı olaylarını belirtmek için kitaplığınızın sürümlerine uygulanan bir adlandırma kuralıdır.
İdeal olarak, kitaplığınıza verdiğiniz sürüm bilgileri, geliştiricilerin, aynı kitaplığın eski sürümlerini kullanan projelerle uyumluluğunu belirlemesine yardımcı olmalıdır.

SemVer 'e en temel yaklaşım, 3 bileşen biçimi `MAJOR.MINOR.PATCH`, burada:

- uyumsuz API değişiklikleri yaptığınızda `MAJOR` artırılır
- `MINOR`, geriye doğru uyumlu bir şekilde işlevsellik eklediğinizde artırılır
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

Bir .NET geliştiricisi olarak çoğu proje türünde bulunan [`app.config` dosyası](../framework/configure-apps/file-schema/index.md) ile karşılaşmanız çok yüksek bir şansınız vardır.
Bu basit yapılandırma dosyası, yeni güncelleştirmelerin dağıtımını iyileştirmek için uzun bir yönteme gidebilirler. Genellikle kitaplıklarınızı düzenli olarak değişen bilgiler `app.config` dosyasında depolandığından, bu tür bilgiler güncelleştirilirken, daha eski sürümlerin yapılandırma dosyasının, kitaplığın yeniden derlenmesi gerekmeden yeni bir dosya ile değiştirilmesi gerekir, ancak bu şekilde kitaplıkları tasarlamış olmanız gerekir.

## <a name="consuming-libraries"></a>Kitaplıkları kullanma

Diğer geliştiriciler tarafından oluşturulan .NET kitaplıklarını tüketen bir geliştirici olarak, bir kitaplığın yeni bir sürümünün projenizle tamamen uyumlu olabileceğini ve genellikle kendi kodunuzu bu değişikliklerle çalışacak şekilde güncelleştirmek zorunda olduğunu fark edersiniz.

Sizin için Lucky ve C# .net ekosistemi, uygulamamızı, son değişiklikleri ortaya çıkaracak yeni kitaplıkların sürümleriyle çalışacak şekilde kolayca güncelleştirmenize imkan tanıyan özellikler ve teknikler sunar.

### <a name="assembly-binding-redirection"></a>Derleme bağlama yeniden yönlendirmesi

Uygulamanızın kullandığı bir kitaplığın sürümünü güncelleştirmek için *app. config* dosyasını kullanabilirsiniz. [*Bağlama yeniden yönlendirme*](../framework/configure-apps/redirect-assembly-versions.md)olarak adlandırılan öğesine ekleyerek, uygulamanızı yeniden derlemek zorunda kalmadan yeni kitaplık sürümünü kullanabilirsiniz. Aşağıdaki örnek, uygulamanızın *app. config* dosyasını, ilk olarak derlenmiş olan `1.0.0` sürümü yerine `ReferencedLibrary` `1.0.1` Patch sürümünü kullanacak şekilde nasıl güncelleşbileceğinizi gösterir.

```xml
<dependentAssembly>
    <assemblyIdentity name="ReferencedLibrary" publicKeyToken="32ab4ba45e0a69a1" culture="en-us" />
    <bindingRedirect oldVersion="1.0.0" newVersion="1.0.1" />
</dependentAssembly>
```

> [!NOTE]
> Bu yaklaşım yalnızca `ReferencedLibrary` yeni sürümü uygulamanız ile ikili dosya uyumluysa çalışır.
> Uyumluluk belirlenirken yapılan değişiklikler için yukarıdaki [geriye dönük uyumluluk](#backwards-compatibility) bölümüne bakın.

### <a name="new"></a>new

Bir temel sınıfın devralınan üyelerini gizlemek için `new` değiştiricisini kullanırsınız. Bu, türetilmiş sınıfların temel sınıflarda güncelleştirmelere yanıt verebildiği bir yoldur.

Aşağıdaki örneği uygulayın:

[!code-csharp[Sample usage of the 'new' modifier](~/samples/snippets/csharp/versioning/new/Program.cs#sample)]

**Output**

```console
A base method
A derived method
```

Yukarıdaki örnekte, `BaseClass``DerivedClass` `MyMethod` metodunu nasıl gizlediğini görebilirsiniz.
Bu, bir kitaplığın yeni sürümündeki bir temel sınıf, türetilmiş sınıfınıza zaten mevcut olan bir üyeyi eklediğinde, temel sınıf üyesini gizlemek için yalnızca türetilmiş sınıf üyeinizdeki `new` değiştiricisini kullanmanız gerektiğini gösterir.

`new` değiştirici belirtilmediğinde, türetilmiş bir sınıf varsayılan olarak bir temel sınıfta çakışan üyeleri gizleyecek, ancak derleyici uyarısı üretilse de kod derlenmeye devam eder. Bu, yalnızca varolan bir sınıfa yeni üye eklemek, kitaplığınızın bu yeni sürümünün hem kaynak hem de ikilinin buna bağlı kodla uyumlu olmasını sağlar.

### <a name="override"></a>override

`override` değiştirici, türetilmiş bir uygulamanın, bir temel sınıf üyesinin uygulamasını gizliyor yerine genişlettiği anlamına gelir. Temel sınıf üyesine `virtual` değiştiricisine uygulanmış olması gerekir.

[!code-csharp[Sample usage of the 'override' modifier](../../samples/snippets/csharp/versioning/override/Program.cs#sample)]

**Output**

```console
Base Method One: Method One
Derived Method One: Derived Method One
```

`override` değiştiricisi derleme zamanında değerlendirilir ve geçersiz kılmak için bir sanal üye bulamazsa derleyici bir hata oluşturur.

Ele alınan teknikler ve bunların kullanılacağı durumlar hakkında bilginiz varsa, bir kitaplığın sürümleri arasındaki geçişin hızını kolaylaştırmak için uzun bir yol olacaktır.
