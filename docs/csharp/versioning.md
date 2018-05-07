---
title: C# sürüm oluşturma - C# Kılavuzu
description: C# ve .NET sürüm nasıl çalıştığını anlamak
ms.date: 01/08/2017
ms.assetid: aa8732d7-5cd0-46e1-994a-78017f20d861
ms.openlocfilehash: 4dc8e7e521bf209d6ca69a84534d277fb8a93ea8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="versioning-in-c"></a>C# sürüm oluşturma #

Bu öğreticide, .NET içinde hangi sürüm oluşturma anlamına gelir öğreneceksiniz. Dikkate almanız gereken faktörler bilgi edineceksiniz sürüm kitaplığınızın yanı sıra yeni bir sürümüne yükseltme kitaplığı.

## <a name="authoring-libraries"></a>Geliştirme kitaplıkları

.NET kitaplıklarına genel kullanım için oluşturan bir geliştirici olarak seçtiğiniz en yeni güncelleştirmeleri almak için sahip olduğu durumlarda büyük olasılıkla bırakıldı. Varolan kod kitaplığınızın yeni sürüme sorunsuz bir geçiş olduğundan emin olmak gereksinim duyduğunuz bu işlem hakkında nasıl gittiğiniz çok önemlidir. Yeni bir sürüm oluştururken dikkate alınması gereken birkaç nokta şunlardır:

### <a name="semantic-versioning"></a>Anlamsal sürüm oluşturma

[Anlamsal sürüm oluşturma](http://semver.org/) (kısaca SemVer) olan belirli aşama olayları belirtmek için kitaplık sürümleri için uygulanan bir adlandırma kuralı.
İdeal olarak, kitaplığınızın size sürüm bilgilerini geliştiriciler, eski sürümleri aynı kullanan projelerini uyumluluğunu belirlemek yardımcı olmalıdır kitaplığı.

SemVer en temel yaklaşım 3 bileşeni biçimidir `MAJOR.MINOR.PATCH`, burada:
 
* `MAJOR` uyumsuz API değişiklikler yaptığınızda artırılır
* `MINOR` Geriye dönük olarak uyumlu bir biçimde işlevselliği eklediğinizde artırılır
* `PATCH` Geriye dönük olarak uyumlu hata düzeltmeleri yaptığınızda artırılır

Sürüm bilgileri .NET Kitaplığı'na uygularken yayın öncesi sürümleri vb. gibi diğer senaryolar belirtmek için yolları da vardır.

### <a name="backwards-compatibility"></a>Geriye dönük uyumluluk

Yeni sürümler kitaplığınızın yayım, geriye doğru önceki sürümleriyle uyumluluğunu büyük olasılıkla önemli kaygılarınızdan biri olacaktır.
Yeni bir sürüm kitaplığınızın önceki sürüme bağlıdır kodu yeniden derlenmesi, yeni sürümle birlikte çalışabilir önceki bir sürümüyle uyumlu kaynağıdır. Yeni bir sürüm kitaplığınızın eski sürümüne bağımlı olduğu bir uygulamayı yeniden derlenmek yeni sürümü ile çalışabilir ikili uyumlu ise.

Geriye dönük kitaplığınızın eski sürümleriyle uyumluluğunu korumak çalışırken göz önünde bulundurmanız gereken bazı şeyler şunlardır:

* Sanal yöntemler: yaptığınızda sanal bir yöntem sürümünüzde anlamına gelir bu yöntemi yok sayın projeleri güncelleştirilmesi gerekecek yeni sanal olmayan. Bu büyük önemli bir değişiklik ve kesinlikle önerilmez.
* Yöntem imzaları: yöntemi davranışa güncelleştirme imzası da değiştirmenizi gerektirdiğinde, böylece bu yönteme çağırma kodu çalışmaya devam eder, bunun yerine bir aşırı oluşturmanız gerekir.
Uygulama tutarlı kalmayacak şekilde yeni yöntemi imzaya çağırmak için eski yöntemi imza her zaman yönetebilirsiniz.
* [Geçersiz öznitelik](programming-guide/concepts/attributes/common-attributes.md#Obsolete): sınıfları veya kullanım dışı bırakılmıştır sınıf üyeleri belirtmek için bu öznitelik, kodunuzda kullanabilirsiniz ve olması olası gelecek sürümlerinde kaldırıldı.
Bu kitaplık kullanan geliştiriciler, daha iyi önemli değişiklikler için hazırlanır sağlar.
* İsteğe bağlı yöntemi bağımsız değişkenler: Güncelleştirilmesi zaman daha önce isteğe bağlı yöntem bağımsız değişkenleri zorunlu yapmanız veya varsayılan değerlerine sonra bu bağımsız değişkenlerden sağlamıyor tüm kodu değiştirmeniz gerekir.
> [!NOTE]
> Özellikle yöntemin davranışları değiştirmez gerekiyorsa zorunlu bağımsız değişkenler isteğe bağlı yapmak çok az etkisi olması gerekir.

Daha kolay, erken yükseltecek yeni kitaplığınızın, büyük olasılıkla'sürümüne yükseltmek, kullanıcılarınızın olun.

### <a name="application-configuration-file"></a>Uygulama yapılandırma dosyası

Çok yüksek olasılığı yüksektir karşılaştı .NET geliştiricisi olarak [ `app.config` dosya](https://msdn.microsoft.com/library/1fk1t1t0(v=vs.110).aspx) çoğu proje türleri de mevcut.
Bu basit yapılandırma dosyası depoladıysanız yeni güncelleştirmeler sunum geliştirme içine gidebilirsiniz. Genellikle Kitaplıklarınızı düzenli olarak değiştirmek büyük olasılıkla bilgiler saklanır şekilde tasarlamanız gerekir, `app.config` , böylece gibi bilgileri güncelleştirildiğinde dosya eski sürümlerinin yapılandırma dosyası yalnızca yeni bir bağlantıyla değiştirilmesi gerekiyor Kitaplığı yeniden derlenmek gerek olmadan.

## <a name="consuming-libraries"></a>Kitaplıkları kullanma

.NET kitaplıklarına diğer geliştiriciler tarafından oluşturulmuş tüketen geliştirici olarak kitaplığa yeni bir sürümü projenizi ile tamamen uyumlu olmayabilir ve genellikle kendinizi kodunuzu bu değişikliklerle çalışması için update gerek kalmadan bulabilirsiniz büyük olasılıkla aklınızda bulundurun.

Sizin için şanslı C# ve .NET ekosistemi ile birlikte gelen özellikleri ve bize uygulamamıza önemli değişiklikler yapabilecek kitaplıkları yeni sürümleri ile çalışmak için kolayca güncelleştirmeye izin teknikler.

### <a name="assembly-binding-redirection"></a>Derleme bağlaması yeniden yönlendirme

Kullanabileceğiniz `app.config` dosya bir kitaplık sürümünü güncelleştirmek için uygulama kullanır. Ne adlı ekleyerek bir [ *bağlama yeniden yönlendirmesinin* ](https://msdn.microsoft.com/library/7wd6ex19(v=vs.110).aspx) , yeni kitaplık sürümü, uygulamanızın yeniden derlemenize gerek kalmadan kullanabilirsiniz. Aşağıdaki örnek, uygulamanızın nasıl güncelleştirecektir gösterir `app.config` kullanmak üzere bir dosya `1.0.1` düzeltme eki sürümü `ReferencedLibrary` yerine `1.0.0` , ilk olarak derlenmiş ile sürümü.

```xml
<dependentAssembly>
    <assemblyIdentity name="ReferencedLibrary" publicKeyToken="32ab4ba45e0a69a1" culture="en-us" />
    <bindingRedirect oldVersion="1.0.0" newVersion="1.0.1" />
</dependentAssembly>
```

> [!NOTE]
> Bu yaklaşım, yalnızca işe yeni sürümünü `ReferencedLibrary` uygulamanız ile ikili uyumlu.
> Bkz: [geriye dönük uyumluluk](#backwards-compatibility) değişikliklerin uyumluluk belirlerken arayın için bölüm üstünde.

### <a name="new"></a>new

Kullandığınız `new` devralınan bir taban sınıfı üyeleri gizlemek için değiştiricisi. Bu şekilde türetilmiş sınıflar temel sınıflar güncelleştirmelerinde yanıt vermesini sağlayabilirsiniz biridir.

Aşağıdaki örnek alın:

[!code-csharp[Sample usage of the 'new' modifier](../../samples/csharp/versioning/new/Program.cs#sample)]

**Output**

```
A base method
A derived method
```

Yukarıdaki örnekte gördüğünüz nasıl `DerivedClass` gizler `MyMethod` yöntemi mevcut `BaseClass`.
Bu bir taban sınıf kitaplığı'nın yeni sürümünde türetilen sınıfta zaten bir üye eklediğinde, yalnızca kullanabileceğiniz anlamına gelir `new` temel sınıf üyesi gizlemek için türetilmiş sınıf üyesi değiştiricisi.

Durumlarda `new` değiştiricisi belirtilirse, türetilmiş bir sınıf bir taban sınıf çakışan üyelerinde varsayılan olarak gizlenir, kod derleyici uyarısı oluşturulur ancak hala derlenir. Bu yalnızca varolan bir sınıfa yeni üye ekleme kitaplığınızın yeni sürümünün yapar anlamına gelir hem kaynak hem de ikili bağımlı kod ile uyumlu.

### <a name="override"></a>override

`override` Türetilmiş uygulamasına bir temel sınıf üyesi uyarlamasını genişletir yerine gizler değiştiricisi anlamına gelir. Taban sınıf üyesi olması gerekiyorsa `virtual` uygulanan değiştiricisi.

[!code-csharp[Sample usage of the 'override' modifier](../../samples/csharp/versioning/override/Program.cs#sample)]

**Output**

```
Base Method One: Method One
Derived Method One: Derived Method One
```

`override` Değiştiricisi derleme zamanında değerlendirilir ve geçersiz kılmak için sanal üyesi bulamazsa derleyici bir hata özel durum oluşturacak.

Bir kitaplık sürümleri arasında geçiş kolaylığı artırmak için uzun bir yol bilginiz ele teknikleri ve aynı zamanda bunları kullanmak için hangi durumlarda Anlayışınızı geçer.
