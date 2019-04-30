---
title: C# sürüm oluşturma - C# Kılavuzu
description: Sürüm oluşturma, C# ve .NET dillerinde nasıl çalıştığını anlamak
ms.date: 01/08/2017
ms.assetid: aa8732d7-5cd0-46e1-994a-78017f20d861
ms.openlocfilehash: 9ba18f82ad83749d5333628bf4431a0282b0964f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706162"
---
# <a name="versioning-in-c"></a>C sürüm oluşturma\#

Bu öğreticide, hangi sürüm anlamına gelir. NET'te öğreneceksiniz. Ayrıca dikkat edilecek Etkenler öğreneceksiniz sürüm kitaplığınızı yanı sıra bir Kitaplığı'nın yeni bir sürüme yükseltme.

## <a name="authoring-libraries"></a>Geliştirme kitaplıkları

Genel kullanım için .NET kitaplıklarını oluşturan bir geliştirici olarak, seçtiğiniz en yeni güncelleştirmeleri almak için sahip olduğu durumlarda büyük olasılıkla bırakıldı. Sorunsuz geçiş kitaplığınızın yeni sürümü için mevcut kod olduğundan emin olmak gereken bu işlem hakkında nasıl gittiğiniz çok önemli. Yeni bir yayın oluştururken dikkate alınması gereken birkaç nokta şunlardır:

### <a name="semantic-versioning"></a>Semantic Versioning

[Semantic versioning](https://semver.org/) olduğu belirli aşama olayları belirtmek için kitaplık sürümleri için uygulanan bir adlandırma kuralı (kısaca SemVer).
Kitaplığınızı size sürüm bilgilerini geliştiriciler bu eski sürümleri aynı kullanan projelerini uyumluluğunu belirlemek ideal olarak, yardımcı kitaplık.

En temel SemVer 3 bileşeni biçimi yaklaşımdır `MAJOR.MINOR.PATCH`burada:

* `MAJOR` uyumsuz API değişiklik yaptığınızda artırılır
* `MINOR` Geriye dönük uyumlu bir biçimde işlevselliği eklediğinizde artırılır
* `PATCH` Geriye dönük uyumlu hata düzeltmeleri yaptığınızda artırılır

Sürüm bilgileri .NET Kitaplığı'na uygularken yayın öncesi sürümleri vb. gibi diğer senaryoları belirtmek için yol vardır.

### <a name="backwards-compatibility"></a>Geriye dönük uyumluluk

Kitaplığınızın yeni sürümlerini yayınlama, geriye doğru önceki sürümlerle uyumluluk büyük olasılıkla önemli kaygılarınızdan olacaktır.
Yeni bir sürüm kitaplığınızın yeni sürümle yeniden derlenen, önceki sürümünde bağlı olan kod işe önceki bir sürümü ile uyumlu kaynağıdır. Kitaplığınızı yeni bir sürümü eski bir sürümüne bağımlı olan bir uygulama yeniden derleme, yeni sürümle birlikte çalışabilir ikili uyumlu ise.

Geriye dönük kitaplığınızın önceki sürümlerle uyumluluk sağlamak çalışırken dikkat etmeniz gerekenler şunlardır:

* Sanal yöntemler: Sanal bir yöntem, yeni sürümde sanal olmayan yaptığınızda bu yöntemi yok sayın projeleri güncelleştirilmesi gerektiği anlamına gelir. Bu büyük bir değişiklik olup kesinlikle önerilmez.
* Yöntem imzaları: Yöntemi davranışı güncelleştirme imzası de değiştirmenizi gerektirir, böylece bu yönteme çağırma kod çalışmaya devam eder, bunun yerine bir aşırı oluşturmanız gerekir.
Her zaman uygulama tutarlı kalması yeni yöntem imzasının çağırmak için eski yöntem imzası clı'yle de işleyebilirsiniz.
* [Geçersiz öznitelik](programming-guide/concepts/attributes/common-attributes.md#Obsolete): Kodunuzda bu öznitelik, sınıfları veya kullanım dışı ve büyük olasılıkla olmasını sınıf üyeleri gelecek sürümleri kaldırıldı belirtmek için kullanabilirsiniz.
Bu, kitaplığı kullanan geliştiriciler önemli değişiklikler için daha iyi hazırlıklı olmalarını sağlar.
* İsteğe bağlı yöntem bağımsız değişkenleri: Ne zaman daha önce isteğe bağlı bir yöntem bağımsız değişkenleri zorunlu yapmak veya bu bağımsız değişken sağlamıyor tüm kod güncelleştirilmesi gereken sonra varsayılan değeri değiştirin.
> [!NOTE]
> Özellikle yöntemin davranışı değişmez gerekiyorsa zorunlu bağımsız değişkenler isteğe bağlı yapmak çok az etkisi olması gerekir.

Kolay bir şekilde, kullanıcılarınızın erken yükseltecek yeni sürüme kitaplığınızın, daha büyük olasılıkla yükseltme yapmanız gerekir.

### <a name="application-configuration-file"></a>Uygulama yapılandırma dosyası

Çok yüksek kaybedilebilir önce karşılaştığınız bir .NET geliştiricisi olarak [ `app.config` dosya](../framework/configure-apps/file-schema/index.md) çoğu proje türlerinde mevcut.
Bu basit bir yapılandırma dosyası, yeni güncelleştirme dağıtımı geliştirme içine uzun yol gidebilirsiniz. Genellikle Kitaplıklarınızı düzenli olarak değiştirmek büyük olasılıkla bilgiler depolanır şekilde tasarlamanız gerekir, `app.config` , böylece tür bilgileri güncelleştirilirken dosya eski sürümlerinin yapılandırma dosyası yalnızca yeni bir tane ile değiştirilmesi gerekiyor Kitaplığı yeniden derleniyor gerek olmadan.

## <a name="consuming-libraries"></a>Kitaplıkları kullanma

Diğer geliştiriciler tarafından oluşturulan .NET kitaplıklarını tüketen bir geliştirici olarak büyük olasılıkla farkında kitaplığa yeni bir sürümü projenizle tam olarak uyumlu olmayabilir ve çoğunlukla kendinizi bu değişikliklerle çalışması için kodunuzu güncelleştirin gerek kalmadan bulabilirsiniz.

Şans sizin için C# ve .NET ekosisteminin gelir özellikleri ve uygulamamızı bozucu değişiklik yapabilecek kitaplıklarının yeni sürümleri ile çalışmak için kolayca güncelleştirmek bize izin teknikleri.

### <a name="assembly-binding-redirection"></a>Derleme bağlama yeniden yönlendirmesi

Kullanabileceğiniz `app.config` dosya bir kitaplığı sürümünü güncelleştirmek için uygulama kullanır. Ne çağrılır ekleyerek bir [ *bağlama yeniden yönlendirmesi* ](../framework/configure-apps/redirect-assembly-versions.md) uygulamanızı yeniden derlemenize gerek kalmadan yeni kitaplığı sürümünü kullanabilirsiniz. Aşağıdaki örnek, uygulamanızın nasıl güncelleştiririz gösterir `app.config` kullanılacak dosyasını `1.0.1` düzeltme eki sürümü `ReferencedLibrary` yerine `1.0.0` , başlangıçta derlendiği sürümü.

```xml
<dependentAssembly>
    <assemblyIdentity name="ReferencedLibrary" publicKeyToken="32ab4ba45e0a69a1" culture="en-us" />
    <bindingRedirect oldVersion="1.0.0" newVersion="1.0.1" />
</dependentAssembly>
```

> [!NOTE]
> Bu yaklaşım, yalnızca iş yeni sürümünü `ReferencedLibrary` uygulamanız ile ikili uyumlu değildir.
> Bkz: [geriye dönük uyumluluk](#backwards-compatibility) değişikliklerin için uyumluluk belirlerken dikkat için bölüm yukarıda.

### <a name="new"></a>new

Kullandığınız `new` değiştiricisi devralınan bir temel sınıf üyelerinin gizlemek için. Bu şekilde türetilmiş sınıflar temel sınıflar güncelleştirmeleri yanıt verebilir biridir.

Aşağıdaki örnek uygulayın:

[!code-csharp[Sample usage of the 'new' modifier](../../samples/csharp/versioning/new/Program.cs#sample)]

**Output**

```
A base method
A derived method
```

Yukarıdaki örnekte gördüğünüz nasıl `DerivedClass` gizler `MyMethod` yöntemi mevcut `BaseClass`.
Bu bir temel sınıf kitaplığı'nın yeni sürümünde, türetilen bir sınıfta zaten bir üye eklediğinde, yalnızca kullanabileceğiniz anlamına gelir `new` temel sınıf üyeyi gizlemek için türetilmiş sınıf üye değiştiricisi.

Hiçbir `new` değiştiricisi belirtilirse, türetilmiş bir sınıf taban sınıfında çakışan üyeleri varsayılan olarak gizler, bir derleyici uyarısı oluşturulur ancak yine de kod derlenir. Bu yalnızca yeni üyeler için varolan bir sınıf eklemek bu yeni sürüme kitaplığınızın aklınızdan anlamına gelir. hem kaynak hem de bağımlı kod ile uyumlu ikili.

### <a name="override"></a>override

`override` Değiştiricisi türetilen uygulamaya bir temel sınıf üyesinin uygulamayı yaygınlaştırır yerine onu gizliyor anlamına gelir. Temel sınıf üyesi olması gerekiyorsa `virtual` uygulanmış değiştiricisi.

[!code-csharp[Sample usage of the 'override' modifier](../../samples/csharp/versioning/override/Program.cs#sample)]

**Output**

```
Base Method One: Method One
Derived Method One: Derived Method One
```

`override` Değiştiricisi, derleme zamanında değerlendirilir ve geçersiz kılmak için bir sanal üye bulamazsa, derleyici bir hata atar.

Bir kitaplık sürümleri arasında geçişin bir kolayca artırma konusunda uzun bir yol ele alındığı teknik bilginizi yanı sıra bunları kullanmak için hangi durumlarda Anlayışınızı geçer.
