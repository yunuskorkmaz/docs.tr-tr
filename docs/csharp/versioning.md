---
title: C# Versioning - C# Kılavuzu
description: C# ve .NET'te sürümlemenin nasıl çalıştığını anlama
ms.date: 01/08/2017
ms.technology: csharp-advanced-concepts
ms.assetid: aa8732d7-5cd0-46e1-994a-78017f20d861
ms.openlocfilehash: 124cce51865f04a555bc121fb6ce18cc95591bdc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156473"
---
# <a name="versioning-in-c"></a>C sürümü\#

Bu eğitimde .NET'te sürümlemenin ne anlama geldiğini öğreneceksiniz. Ayrıca kitaplığınızı sürüm yaparken ve kitaplığın yeni bir sürümüne yükseltme yaparken göz önünde bulundurmanız gereken faktörleri de öğreneceksiniz.

## <a name="authoring-libraries"></a>Kitaplık Yazma

Genel kullanım için .NET kitaplıkları oluşturmuş bir geliştirici olarak, büyük olasılıkla yeni güncelleştirmeler sunması gereken durumlarda bulunuyorsunuz. Varolan kodun kitaplığınuzun yeni sürümüne sorunsuz bir şekilde geçiş olduğundan emin olmak için bu işlemi nasıl gerçekleştirebilirsiniz çok önemlidir. Yeni bir sürüm oluştururken göz önünde bulundurulması gereken birkaç şey şunlardır:

### <a name="semantic-versioning"></a>Anlamsal Versiyon

[Anlamsal sürüm](https://semver.org/) (kısaca SemVer), belirli kilometre taşı olaylarını belirtmek için kitaplığınızın sürümlerine uygulanan bir adlandırma kuralıdır.
İdeal olarak, kitaplığınıza verdiğiniz sürüm bilgileri, geliştiricilerin aynı kitaplığın eski sürümlerinden yararlanan projeleriile uyumluluğu belirlemelerine yardımcı olmalıdır.

SemVer için en temel yaklaşım 3 `MAJOR.MINOR.PATCH`bileşen biçimi, nerede:

- `MAJOR`uyumsuz API değişiklikleri yaptığınızda artımlı
- `MINOR`işlevselliği geriye doğru uyumlu bir şekilde eklediğinizde artırılır
- `PATCH`geriye uyumlu hata düzeltmeleri yaptığınızda artımlı

.NET kitaplığınıza sürüm bilgilerini uygularken ön sürüm sürümleri vb. gibi diğer senaryoları belirtmenin yolları da vardır.

### <a name="backwards-compatibility"></a>Geriye Dönük Uyumluluk

Kitaplığınızın yeni sürümlerini serbest bıraktırken, önceki sürümlerle geriye dönük uyumluluk büyük olasılıkla başlıca endişelerinizden biri olacaktır.
Kitaplığınız yeni bir sürümü kaynak önceki sürüme bağlı kod, yeniden derlendiğinde, yeni sürümü ile çalışabilir bağlı ise ile uyumludur.
Eski sürüme bağlı bir uygulama, yeniden derleme olmadan yeni sürümle çalışabiliyorsa, kitaplığınızın yeni bir sürümü ikili uyumludur.

Kitaplığınızın eski sürümleriyle geriye doğru uyumluluğu korumaya çalışırken göz önünde bulundurmanız gereken bazı şeyler şunlardır:

- Sanal yöntemler: Yeni sürümde sanal olmayan bir sanal yöntem yaptığınızda, bu yöntemi geçersiz kılan projelerin güncellenmesi gerekir. Bu büyük bir kırılma değişim ve şiddetle cesareti olduğunu.
- Yöntem imzaları: Bir yöntem davranışını güncelleştirmek imzasını da değiştirmenizi gerektiriyorsa, bunun yerine, bu yönteme çağıran kodun çalışmaya devam etmesi için aşırı yükleme oluşturmanız gerekir.
Uygulamanın tutarlı kalması için eski yöntem imzasını her zaman yeni yöntem imzasına çağırmak için değiştirebilirsiniz.
- [Eski öznitelik](programming-guide/concepts/attributes/common-attributes.md#Obsolete): Bu özniteliği, amortismana kaldırılmış ve gelecek sürümlerde kaldırılma olasılığı olan sınıfları veya sınıf üyelerini belirtmek için kodunuzdaki bu özelliği kullanabilirsiniz. Bu, kitaplığınızı kullanan geliştiricilerin değişiklikleri kırmaya daha iyi hazır olmasını sağlar.
- İsteğe Bağlı Yöntem Bağımsız Değişkenleri: Daha önce isteğe bağlı yöntem bağımsız değişkenlerini zorunlu hale getirdiğinizde veya varsayılan değerlerini değiştirdiğinizde, bu bağımsız değişkenleri sağlamayan tüm kodun güncelleştirilmesi gerekir.

> [!NOTE]
> Zorunlu bağımsız değişkenleri isteğe bağlı hale getirmek, özellikle yöntemin davranışını değiştirmezse çok az etkiye sahip olmalıdır.

Kullanıcılarınızın kitaplığınızın yeni sürümüne yükseltmesini ne kadar kolay hale getirirseniz, daha erken yükseltme yapma olasılıkları o kadar artar.

### <a name="application-configuration-file"></a>Uygulama Yapılandırma Dosyası

Bir .NET geliştiricisi olarak, çoğu proje türünde [dosya `app.config` ](../framework/configure-apps/file-schema/index.md) nın bulunma olasılığı çok yüksektür.
Bu basit yapılandırma dosyası, yeni güncelleştirmelerin kullanıma sunulmasını iyileştirmek için uzun bir yol kat edebilir. Kitaplıklarınızı genellikle düzenli olarak değişmesi muhtemel bilgilerin `app.config` dosyada depolanacak şekilde tasarlamanız gerekir, bu şekilde bu tür bilgiler güncelleştirildiğinde, eski sürümlerin config dosyasının kitaplığın yeniden derlenmesine gerek kalmadan yenisiyle değiştirilmesi gerekir.

## <a name="consuming-libraries"></a>Tüketen Kütüphaneler

Diğer geliştiriciler tarafından oluşturulmuş .NET kitaplıklarını tüketen bir geliştirici olarak, büyük olasılıkla kitaplığın yeni bir sürümünün projenizle tam olarak uyumlu olmayabileceğinin farkındasınızdır ve genellikle bu değişikliklerle çalışmak için kodunuzu güncelleştirmek zorunda kalacaksınız.

Şanslısınız ki, C# ve .NET ekosistemi, çığır açan değişikliklere neden olabilecek kitaplıkların yeni sürümleriyle çalışmak üzere uygulamamızı kolayca güncellememize olanak tanıyan özellikler ve tekniklerle birlikte gelir.

### <a name="assembly-binding-redirection"></a>Derleme Bağlama Yeniden Yönlendirme

Uygulamanızın kullandığı kitaplığın sürümünü güncelleştirmek için *app.config* dosyasını kullanabilirsiniz. [*Bağlayıcı yönlendirme*](../framework/configure-apps/redirect-assembly-versions.md)olarak adlandırılan bir yönlendirme ekleyerek, uygulamanızı yeniden derlemek zorunda kalmadan yeni kitaplık sürümünü kullanabilirsiniz. Aşağıdaki örnek, uygulamanızın *app.config* dosyasını ilk derlenen `1.0.1` `1.0.0` sürümüyerine `ReferencedLibrary` yama sürümünü kullanmak üzere nasıl güncelleştireceğinizgösterilmektedir.

```xml
<dependentAssembly>
    <assemblyIdentity name="ReferencedLibrary" publicKeyToken="32ab4ba45e0a69a1" culture="en-us" />
    <bindingRedirect oldVersion="1.0.0" newVersion="1.0.1" />
</dependentAssembly>
```

> [!NOTE]
> Bu yaklaşım yalnızca yeni sürümü `ReferencedLibrary` uygulamanızla ikili olarak uyumluysa çalışır.
> Uyumluluğu belirlerken dikkat etmesi gereken değişiklikler için yukarıdaki [Geriye Dönük Uyumluluk](#backwards-compatibility) bölümüne bakın.

### <a name="new"></a>new

Bir taban `new` sınıfın devralınan üyelerini gizlemek için değiştirici kullanırsınız. Bu, türetilmiş sınıfların temel sınıflardaki güncelleştirmelere yanıt verebileceği yollardan biridir.

Aşağıdaki örneği ele alalım:

[!code-csharp[Sample usage of the 'new' modifier](~/samples/snippets/csharp/versioning/new/Program.cs#sample)]

**Çıktı**

```console
A base method
A derived method
```

Yukarıdaki örnekten, 'de `DerivedClass` `BaseClass`bulunan `MyMethod` yöntemi nasıl gizlediğini görebilirsiniz.
Bu, kitaplığın yeni sürümündeki bir taban sınıf, türemiş sınıfınızda zaten var olan `new` bir üye eklendiğinde, taban sınıf üyesini gizlemek için türemiş sınıf üyenizdeki değiştiriciyi kullanabilirsiniz.

Değiştirici `new` belirtilmediğinde, türetilmiş bir sınıf varsayılan olarak bir taban sınıfta çakışan üyeleri gizler, ancak derleyici uyarısı oluşturulacak olsa da kod yine de derlenir. Bu, yalnızca varolan bir sınıfa yeni üyeler eklemenin, kitaplığınızın yeni sürümünü hem kaynak hem de ikili olarak bağlı olan kodla uyumlu hale getirir.

### <a name="override"></a>override

Değiştirici, `override` türetilmiş bir uygulamanın, bir taban sınıf üyesinin uygulanmasını gizlemek yerine genişletir anlamına gelir. Taban sınıf üyesinin değiştiricinin `virtual` bu uygulamaya uygulanması gerekir.

[!code-csharp[Sample usage of the 'override' modifier](../../samples/snippets/csharp/versioning/override/Program.cs#sample)]

**Çıktı**

```console
Base Method One: Method One
Derived Method One: Derived Method One
```

`override` Değiştirici derleme zamanında değerlendirilir ve derleyici geçersiz kılacak sanal bir üye bulamazsa hata atar.

Tartışılan teknikler hakkındaki bilginiz ve bunları kullanacağınız durumlar hakkındaki anlayışınız, bir kütüphanenin sürümleri arasındaki geçişi kolaylaştırmaya yönelik uzun bir yol kat edecektir.
