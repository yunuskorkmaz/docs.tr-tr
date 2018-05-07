---
title: Etki alanı modeli katmanda doğrulamaları tasarlama
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Etki alanı modeli katmanda doğrulamaları tasarlama
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: ce3cb0c79cbd492224ce1d4ecb25cd02062f11cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="designing-validations-in-the-domain-model-layer"></a>Etki alanı modeli katmanda doğrulamaları tasarlama

GGG doğrulama kuralları invariants düşünülebilir. Ana bir toplama, toplama içinde tüm varlıklar için durum değişiklikleri arasında invariants zorlamak için sorumluluğundadır.

Etki alanı varlıkları her zaman geçerli varlıkları olması gerekir. Belirli bir sayıda invariants her zaman doğru olması gereken bir nesne için vardır. Örneğin, bir siparişi öğesi nesne her zaman, pozitif bir tamsayı ve bir makale adı olması ve fiyat gereken bir miktar sahip olması gerekir. Bu nedenle, invariants zorlama (özellikle kökünün toplama) etki alanı varlıkları sorumluluğundadır ve bir varlık nesnesinin geçerli olmadan mevcut olmamalıdır. Değişmez kuralları yalnızca sözleşmeleri ifade edilir ve bunlar ihlal edildiğinde özel durumları veya bildirimleri oluşturulur.

Bu arkasındaki mantığı, nesneler, hiçbir zaman içinde olması gereken bir durumda olduğundan birçok hatalar ortaya ' dir. Greg Young iyi bir açıklama verilmiştir bir [Çevrimiçi tartışma](http://jeffreypalermo.com/blog/the-fallacy-of-the-always-valid-entity/):

Şimdi bir USERPROFILE... nasıl biz adı null değil o hizmetinde basitleşir götürür SendUserCreationEmailService şimdi sahibiz önermek? Biz yeniden iade? Veya daha büyük bir olasılıkla... denetleyip "için en iyi umuyoruz" yalnızca rahatsız yok — birisi, göndermeden önce doğrulamak için rahatsız umuyoruz. Elbette, biz hata tetiklemelidir null bir ada sahip bir müşteri gönderebilirim durumunda yazma ilk testin TDD kullanma. Ancak bu tür testlerin tekrar tekrar yazma başladıktan sonra biz farkında olun... "biz olmasını adı hiçbir zaman izin veriyorsa bekleyin null tüm bu testleri sahibiz olmayacaktır"

## <a name="implementing-validations-in-the-domain-model-layer"></a>Etki alanı modeli katmanda doğrulamaları uygulama

Doğrulama, etki alanı varlık oluşturucuları veya varlık güncelleştirebilirsiniz yöntemleri genellikle uygulanır. Doğrulanıyor verileri ve doğrulama başarısız olursa yükseltmeyi özel durumlar gibi doğrulamaları uygulamak için birden çok yolu vardır. Ayrıca vardır doğrulamaların belirtimi desenini kullanarak gibi daha gelişmiş desenleri ve daha sonra giderebilmek yerine her doğrulama için bir özel durum döndürme hataları koleksiyonu döndürmek için bildirim düzeni.

### <a name="validating-conditions-and-throwing-exceptions"></a>Koşullar doğrulama ve özel durumları atma

Aşağıdaki kod örneği, en kolay yaklaşım doğrulama için bir özel durum yükselterek bir etki alanı varlığı gösterir. Bu bölümün sonunda başvuruları tablosundaki biz daha önce ele alınan düzenlerini esas alarak daha gelişmiş uygulamaları bağlantılar görebilirsiniz.

```csharp
public void SetAddress(Address address)
{
    _shippingAddress = address?? throw new ArgumentNullException(nameof(address));
}
```

Daha iyi bir örnek iç durum değiştirme veya bir yöntem için tüm mutations ortaya çıktığını sağlamak için gereken göstermek. Örneğin, aşağıdaki uygulama nesnesi geçersiz bir durumda bırakır:

```csharp
public void SetAddress(string line1, string line2,
    string city, string state, int zip)
{
    _shipingAddress.line1 = line1 ?? throw new ...
    _shippingAddress.line2 = line2;
    _shippingAddress.city = city ?? throw new ...
    _shippingAddress.state = (IsValid(state) ? state : throw new …);
}
```

Durum değeri geçersiz, ilk adres satırındaki ve şehir zaten değiştirildi. Bu adres geçersiz yapabilir.

Benzer bir yaklaşım oluşturulduktan sonra varlık geçerli olduğundan emin olmak için bir özel durum yükseltme varlığın oluşturucuda kullanılabilir.

### <a name="using-validation-attributes-in-the-model-based-on-data-annotations"></a>Üzerinde veri ek açıklamaları temel modelinde doğrulama öznitelikleri kullanma

Başka bir yaklaşım üzerinde veri ek açıklamaları temel doğrulama öznitelikleri kullanmaktır. Doğrulama öznitelikleri kavramsal olarak, veritabanı tablolarındaki alanlar doğrulama benzer model doğrulama yapılandırmak için bir yol sağlar. Bu, veri türleri veya gerekli alanları atama gibi kısıtlamaları içerir. Doğrulama diğer türleri gibi bir kredi kartı numarası, telefon numarası, iş kurallarını zorunlu tutmak için veri desenleri uygulamak dahil etmek veya e-posta adresi. Doğrulama öznitelikleri gereksinimleri zorlamak kolaylaştırır.

MVC denetleyicilerinden çağırmalısınız Microsoft.AspNetCore.Mvc.ModelState arasında ModelState.IsValid üzerinde bir bağımlılık geçen olduğundan ancak, aşağıdaki kodda gösterildiği gibi bu yaklaşım DDD modelinde, çok zorlayıcı olabilir. Model doğrulama çağrılan her denetleyici eylemi önce gerçekleşir ve onu çağıran ModelState.IsValid sonucunu inceleyin ve uygun şekilde tepki denetleyici yöntemin sorumluluğundadır. Kullanmaya karar bağlıdır sıkı şekilde bağlı model, altyapı ile olmasını istiyor.

```csharp
using System.ComponentModel.DataAnnotations;
// Other using statements ...
// Entity is a custom base class which has the ID
public class Product : Entity
{
    [Required]
    [StringLength(100)]
    public string Title { get; private set; }

    [Required]
    [Range(0, 999.99)]
    public decimal Price { get; private set; }

    [Required]
    [VintageProduct(1970)]
    [DataType(DataType.Date)]
    public DateTime ReleaseDate { get; private set; }

    [Required]
    [StringLength(1000)]
    public string Description { get; private set; }

    // Constructor...
    // Additional methods for entity logic and constructor...
}
```

Ancak, bir DDD açısından bakıldığında, etki alanı modeli en iyi, varlığın davranışını yöntemleri veya doğrulama kurallarını zorunlu tutmak için belirtimi ve bildirim desenleri uygulama özel durumları kullanımı ile yalın tutulur. ASP.NET Core veri ek açıklamalar gibi doğrulama çerçeveleri veya herhangi bir doğrulama çerçeve FluentValidation gibi uygulama çerçevesi çağırmak için bir gereksinim taşır. Örneğin, ModelState.IsValid yöntemi içinde veri ek açıklamaları çağrılırken, ASP.NET denetleyicileri çağırma gerekir.

Veri ek açıklamaları model doğrulama UI katman içinde izin vermek için giriş kabul ViewModel sınıflarında (yerine etki alanı varlıklar) uygulama katmanında kullanmak için anlamlı yapabilirsiniz. Ancak, bu etki alanı modeli içindeki doğrulama dışlama adresindeki yapılmalıdır değil.

### <a name="validating-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a>Varlıkları belirtimi düzeni ve bildirim düzeni uygulayarak doğrulanıyor

Son olarak, etki alanı modelinde doğrulamaları uygulamak için bir daha karmaşık bildirim düzeni ile birlikte belirtimi düzeni uygulayarak daha sonra listelenen ek kaynaklar bazıları açıklandığı gibi bir yaklaşımdır.

Bu, aynı zamanda bu düzenlere yalnızca biri kullanabileceğiniz tümleştirilmediği de unutulmamalıdır — Örneğin, el ile denetim ifadeleri doğrulama, ancak uyarı desenini kullanarak yığın ve doğrulama hatalarının listesini döndürür.

### <a name="using-deferred-validation-in-the-domain"></a>Ertelenmiş doğrulama etki alanında kullanma

Etki alanındaki ertelenmiş doğrulamaları uğraşmanız çeşitli yaklaşım vardır. Kendi kitaptaki [Implementing Domain-Driven tasarım](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon bu bölümdeki doğrulamasını açıklanır.

### <a name="two-step-validation"></a>İki aşamalı doğrulama

Ayrıca, iki aşamalı doğrulama göz önünde bulundurun. Alan düzeyindeki doğrulama komutu veri aktarım nesneleri (DTOs) ve etki alanı düzeyi doğrulama varlıklarınızı içinde kullanın. Sonuç nesnesi bunun yerine özel durumları doğrulama hatalarla ilgilenir kolaylaştırmak için döndürerek bunu yapabilirsiniz.

Alan doğrulama ile veri ek açıklamaları kullanılarak, örneğin, doğrulama yinelenen tanımı değil. Yürütme rağmen sunucu tarafı ve istemci tarafı DTOs durumunda olabilir (komutlar ve ViewModels, örneğin).

## <a name="additional-resources"></a>Ek kaynaklar

-   **Rachel Appel. Model doğrulama ASP.NET Core mvc'de giriş**
    [*https://docs.microsoft.com/aspnet/core/mvc/models/validation*](https://docs.microsoft.com/aspnet/core/mvc/models/validation)

-   **Rick Anderson. Doğrulama ekleme**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)

-   **Martin Fowler. Doğrulama içinde bildirim özel durumları atma değiştirme**
    [*https://martinfowler.com/articles/replaceThrowWithNotification.html*](https://martinfowler.com/articles/replaceThrowWithNotification.html)

-   **Belirtimi ve bildirim desenleri**
    [*https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns*](https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns)

-   **Levası Gorodinski. Etki alanı Odaklı Tasarım (DDD) doğrulama**
    [*http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/*](http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/)

-   **Colin prizine. Etki alanı Model doğrulama**
    [*http://colinjack.blogspot.com/2008/03/domain-model-validation.html*](http://colinjack.blogspot.com/2008/03/domain-model-validation.html)

-   **Jimmy Bogard. DDD dünyada doğrulama**
    [*https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/*](https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/)


>[!div class="step-by-step"]
[Önceki] (numaralandırması-sınıfları-üzerinden-enum-types.md) [sonraki] (istemci-tarafı-validation.md)
