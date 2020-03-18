---
title: Etki alanı model katmanında doğrulamaları tasarlama
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | Etki alanı modeli doğrulamalarının temel kavramlarını anlayın.
ms.date: 10/08/2018
ms.openlocfilehash: 98ccc5df84c9f6f402ecbee83b077c806d6a76fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75899675"
---
# <a name="design-validations-in-the-domain-model-layer"></a>Etki alanı modeli katmanında tasarım doğrulamaları

DDD'de doğrulama kuralları değişmez olarak düşünülebilir. Bir agreganın temel sorumluluğu, bu toplamdaki tüm varlıklar için durum değişiklikleri arasında değişmezlikleri uygulamaktır.

Etki alanı varlıkları her zaman geçerli varlıklar olmalıdır. Her zaman doğru olması gereken bir nesne için belirli sayıda değişmez vardır. Örneğin, bir sipariş öğesi nesnesi her zaman pozitif tamsayı olması gereken bir miktar, artı bir makale adı ve fiyat olması gerekir. Bu nedenle, değişmezlerin uygulanması etki alanı varlıklarının (özellikle toplam kök) sorumluluğundadır ve bir varlık nesnesi geçerli olmadan var olmamalıdır. Değişmez kurallar yalnızca sözleşme olarak ifade edilir ve ihlal edildiklerinde özel durumlar veya bildirimler yükseltilir.

Bunun arkasındaki mantık, nesnelerin asla içinde olmaması gereken bir durumda olması nedeniyle birçok hatanın oluşmasıdır. Aşağıdaki greg Young bir [online tartışma](https://jeffreypalermo.com/2009/05/the-fallacy-of-the-always-valid-entity/)iyi bir açıklama:

Şimdi bir UserProfile alır SendUserCreationEmailService var önerelim ... Adın null olmadığını bu hizmette nasıl rasyonalize edebiliriz? Tekrar kontrol ediyor muyum? Ya da daha büyük olasılıkla ... sadece kontrol etmek için rahatsız etmeyin ve "en iyi" için umut-birinin size göndermeden önce doğrulamak için rahatsız umuyoruz. Tabii ki, TDD kullanarak biz yazmalı gereken ilk testlerden biri eğer bir hata yükseltmek gerektiğini bir null adı ile bir müşteri göndermek olduğunu. Ama bir kez tekrar tekrar bu tür testler yazmaya başlamak biz fark ... "Eğer ismin geçersiz olmasına izin vermeseydik, bu testlerin hepsine sahip olamazdık"

## <a name="implement-validations-in-the-domain-model-layer"></a>Etki alanı modeli katmanında doğrulamaları uygulama

Doğrulamalar genellikle etki alanı varlık oluşturucuları veya varlığı güncelleştirebilecek yöntemlerde uygulanır. Doğrulama başarısız olursa, verileri doğrulama ve özel durumları artırma gibi doğrulamaları uygulamanın birden çok yolu vardır. Ayrıca, doğrulamalar için Belirtim deseni ve bildirim deseni, oluştukça her doğrulama için bir özel durum döndürmek yerine bir hata koleksiyonunu döndürmek gibi daha gelişmiş desenler de vardır.

### <a name="validate-conditions-and-throw-exceptions"></a>Koşulları doğrulayın ve özel durumlar atın

Aşağıdaki kod örneği, bir özel durum oluşturarak bir etki alanı varlığında doğrulamaya en basit yaklaşımı gösterir. Bu bölümün sonundaki başvurular tablosunda, daha önce tartıştığımız desenlere dayalı olarak daha gelişmiş uygulamalara bağlantılar görebilirsiniz.

```csharp
public void SetAddress(Address address)
{
    _shippingAddress = address?? throw new ArgumentNullException(nameof(address));
}
```

Daha iyi bir örnek, iç durumunun değişmediğinden veya bir yöntemiçin tüm mutasyonların meydana geldiğini sağlama gereğini ortaya koymaktadır. Örneğin, aşağıdaki uygulama nesneyi geçersiz bir durumda bırakır:

```csharp
public void SetAddress(string line1, string line2,
    string city, string state, int zip)
{
    _shippingAddress.line1 = line1 ?? throw new ...
    _shippingAddress.line2 = line2;
    _shippingAddress.city = city ?? throw new ...
    _shippingAddress.state = (IsValid(state) ? state : throw new …);
}
```

Devletin değeri geçersizse, ilk adres satırı ve şehir zaten değiştirildi. Bu adresi geçersiz kılabilecek.

Benzer bir yaklaşım varlığın oluşturucusunda da kullanılabilir ve oluşturulduktan sonra varlığın geçerli olduğundan emin olmak için bir özel durum oluşturur.

### <a name="use-validation-attributes-in-the-model-based-on-data-annotations"></a>Veri ek açıklamalarını temel alan modelde doğrulama öznitelikleri kullanma

Gerekli veya MaxLength öznitelikleri gibi veri ek açıklamaları, [Tablo eşleme](infrastructure-persistence-layer-implemenation-entity-framework-core.md#table-mapping) bölümünde ayrıntılı olarak açıklandığı gibi EF Core veritabanı alanı özelliklerini yapılandırmak için kullanılabilir, <xref:System.ComponentModel.DataAnnotations.IValidatableObject.Validate%2A?displayProperty=nameWithType> ancak artık EF [Core'da varlık doğrulaması için çalışmaz](https://github.com/dotnet/efcore/issues/3680) (yöntem de yok), .NET Framework'deki EF 4.x'ten beri yaptıkları gibi.

Veri ek açıklamaları <xref:System.ComponentModel.DataAnnotations.IValidatableObject> ve arabirim hala model bağlama sırasında model doğrulama için kullanılabilir, her zamanki gibi denetleyicinin eylemleri çağırma önce, ama bu model bir ViewModel veya DTO olması gerekiyordu ve bir MVC veya API endişe değil bir etki alanı modeli endişe.

Kavramsal farkı net hale getirdikten sonra, eylemleriniz `IValidatableObject` önerilmeyen bir varlık sınıfı nesnesi parametresi alıyorsa, veri ek açıklamalarını ve varlık sınıfında doğrulama için kullanmaya devam edebilirsiniz. Bu durumda, doğrulama modeli bağlama üzerine, hemen eylem çağıran önce oluşur ve sonucu kontrol etmek için denetleyicinin ModelState.IsValid özelliğini kontrol edebilirsiniz, ama sonra tekrar, denetleyici olur, varlık nesnesi devam etmeden önce değil DbContext, EF 4.x'ten beri yaptığı gibi.

DbContext'ın SaveChanges yöntemini geçersiz kılarak, `IValidatableObject.Validate` veri ek açıklamalarını ve yöntemi kullanarak varlık sınıfında özel doğrulama yı yine de uygulayabilirsiniz.

`IValidatableObject` [GitHub'daki bu yorumda](https://github.com/dotnet/efcore/issues/3680#issuecomment-155502539)varlıkları doğrulamak için örnek bir uygulama görebilirsiniz. Bu örnek öznitelik tabanlı doğrulamalar yapmaz, ancak aynı geçersiz kılma yansıması kullanarak uygulamak kolay olmalıdır.

Ancak, DDD bakış açısından, etki alanı modeli en iyi varlık davranış yöntemleri özel durumlar kullanımı ile yalın tutulur veya doğrulama kuralları zorlamak için Belirtim ve Bildirim desenleri uygulanarak.

Kullanıcı Arabirimi katmanında model doğrulamasına izin vermek için girişi kabul edecek ViewModel sınıflarında (etki alanı varlıkları yerine) uygulama katmanında veri ek açıklamaları kullanmak mantıklı olabilir. Ancak, bu etki alanı modeli içinde doğrulama hariç yapılmalıdır.

### <a name="validate-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a>Belirtim deseni ve Bildirim deseni uygulayarak varlıkları doğrulayın

Son olarak, etki alanı modelinde doğrulamaları uygulamak için daha ayrıntılı bir yaklaşım, daha sonra listelenen ek kaynakların bazılarında açıklandığı gibi, Bildirim deseni ile birlikte Belirtim deseni uygulayarak olur.

Bu desenlerden yalnızca birini de kullanabileceğinizi belirtmekte yarar vardır(örneğin, denetim deyimleriyle el ile doğrulama, ancak doğrulama hatalarının listesini yığını ve döndürebilir için Bildirim deseni kullanılır.

### <a name="use-deferred-validation-in-the-domain"></a>Etki alanında ertelenmiş doğrulama kullanma

Etki alanında ertelenmiş doğrulamaları ele almak için çeşitli yaklaşımlar vardır. [Kitabında Etki Alanı Odaklı Tasarım Uygulama](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon doğrulama bölümünde bu tartışıyor.

### <a name="two-step-validation"></a>İki adımlı doğrulama

Ayrıca iki adımlı doğrulama düşünün. Komutveri aktarım nesnelerinde (DTO'lar) alan düzeyinde doğrulama yı ve varlıklarınız içinde etki alanı düzeyinde doğrulamayı kullanın. Doğrulama hatalarıyla başa çıkmanın daha kolay olabilmesi için bunu özel durumlar yerine bir sonuç nesnesi döndürerek yapabilirsiniz.

Örneğin, veri ek açıklamalarıyla alan doğrulaması kullanarak doğrulama tanımını yinelemezsiniz. Ancak yürütme, DT'ler (örneğin komutlar ve Görünüm Modelleri) durumunda hem sunucu tarafı hem de istemci tarafı olabilir.

## <a name="additional-resources"></a>Ek kaynaklar

- **Rachel Appel. Core MVC'de model doğrulamaya giriş ASP.NET** \
  <https://docs.microsoft.com/aspnet/core/mvc/models/validation>

- **Rick Anderson' ı. Doğrulama ekleme** \
  <https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation>

- **Martin Fowler' ı. Doğrulamalarda Bildirimle Özel Durumlar Atma nın Değiştirilmesi** \
  <https://martinfowler.com/articles/replaceThrowWithNotification.html>

- **Şartname ve Bildirim Desenleri** \
  <https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns>

- **Lev Gorodinski. Etki Alanı Odaklı Tasarımda Doğrulama (DDD)** \
  <http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/>

- **Colin Jack' i. Etki Alanı Modeli Doğrulama** \
  <https://colinjack.blogspot.com/2008/03/domain-model-validation.html>

- **Jimmy Bogard' ı. DDD dünyasında doğrulama** \
  <https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/>

> [!div class="step-by-step"]
> [Önceki](enumeration-classes-over-enum-types.md)
> [Sonraki](client-side-validation.md)
