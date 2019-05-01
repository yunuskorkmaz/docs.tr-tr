---
title: Etki alanı model katmanında doğrulamaları tasarlama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Etki alanı modeli doğrulamaları temel kavramlarını anlama.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: ae1252f4544f184a5f63ef02ba898da9b4373e17
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62020003"
---
# <a name="design-validations-in-the-domain-model-layer"></a>Etki alanı model katmanında doğrulamaları tasarlama

DDD içinde doğrulama kuralları okuduğunuzda düşünülebilir. Ana toplama, toplam içindeki tüm varlıklar için durum değişikliklerini okuduğunuzda sağlamak için sorumluluğundadır.

Etki alanı varlıklar her zaman geçerli varlık olmalıdır. Okuduğunuzda her zaman true olması gereken bir nesne için belirli bir sayıda vardır. Örneğin, bir sipariş öğesi nesne her zaman bir makale adı yanı sıra bir pozitif tamsayı olmalıdır ve Fiyat miktarı sahip olması gerekir. Bu nedenle, okuduğunuzda zorlama (özellikle, toplama kök) etki alanı varlıklarının sorumluluğundadır ve bir varlık nesnesine geçerli olmadan mevcut olmamalıdır. Sabit kuralları yalnızca sözleşmeleri ifade edilir ve özel durumlar veya bildirimleri, ihlal edildiğinde oluşturulur.

Bunun ardındaki mantık nesneler içinde hiçbir zaman olmalıydı bir durumda olduğundan çok fazla hata meydana ' dir. Greg Young ' iyi bir açıklama aşağıda verilmektedir bir [Çevrimiçi tartışma](https://jeffreypalermo.com/2009/05/the-fallacy-of-the-always-valid-entity/):

Şimdi artık sahip olduğumuz bir UserProfile... nasıl biz adı null değil, hizmette basitleşir alan SendUserCreationEmailService önerilsin mi? Biz bunu yeniden kontrol edebilirim? Veya daha büyük olasılıkla... denetleyip "için en iyi umuyoruz" yalnızca rahatsız değildir — birisi için göndermeden önce doğrulamak için rahatsız umuyoruz. Elbette, biz hata tetiklemelidir null bir ada sahip bir müşteri gönderebilirim durumunda yazma ilk testin TDD kullanma. Ancak, bu tür testlerin tekrar tekrar yazma başlattıktan sonra biz fark... "biz adı olacak hiçbir zaman izin veriliyorsa bekleyin null tüm bu testleri sahibiz mıydı"

## <a name="implement-validations-in-the-domain-model-layer"></a>Uygulama etki alanı model katmanında doğrulamaları

Doğrulama, etki alanı varlığı oluşturucular veya varlık güncelleştirebilirsiniz yöntemleri genellikle uygulanır. Doğrulamaları, doğrulanıyor veri ve doğrulama başarısız olursa, yükseltmeyi özel durumlar gibi uygulamak için birden çok yolu vardır. Ayrıca vardır doğrulamaların belirtimi deseni kullanma gibi daha gelişmiş düzenleri ve bu gerçekleştiği sırada her doğrulama için bir özel durum döndüren yerine hataları koleksiyonu döndürülecek bildirim düzeni.

### <a name="validate-conditions-and-throw-exceptions"></a>Koşulları doğrulayın ve özel durumlar

Aşağıdaki kod örneği, bir özel durum oluşturularak, bir etki alanı varlığı içinde doğrulama için en kolay yaklaşım gösterilmektedir. Bu bölümün sonunda başvuruları tablodaki bağlantılar daha gelişmiş uygulamalar daha önce ele almıştık düzenlerini esas alarak görebilirsiniz.

```csharp
public void SetAddress(Address address)
{
    _shippingAddress = address?? throw new ArgumentNullException(nameof(address));
}
```

Daha iyi bir örneği, iç durumu değişmedi ya da yöntem için tüm mutations oluştuğunu sağlama gereksinimi göstermek. Örneğin, aşağıdaki uygulama nesnesi geçersiz bir durumda bırakın:

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

Durum değeri geçersizse, ilk adres satırı ve şehir zaten değiştirildi. Bu adres geçersiz hale getirebilirsiniz.

Benzer bir yaklaşım oluşturulduktan sonra varlık geçerli olduğundan emin olmak için bir özel durum oluşturma varlığın oluşturucuda kullanılabilir.

### <a name="use-validation-attributes-in-the-model-based-on-data-annotations"></a>Veri ek açıklamalarını dayalı modeli doğrulama öznitelikleri kullanma

Veri ek açıklamaları, ister gerekli veya MaxLength öznitelikleri kullanılabilir EF Core veritabanı alanı özelliklerini yapılandırmak için ayrıntılı olarak açıklandığı gibi [Tablo eşleme](infrastructure-persistence-layer-implemenation-entity-framework-core.md#table-mapping) bölümünde, ancak [varlık için artık çalıştıkları EF Core doğrulama](https://github.com/aspnet/EntityFrameworkCore/issues/3680) (diğerinden mu <xref:System.ComponentModel.DataAnnotations.IValidatableObject.Validate%2A?displayProperty=nameWithType> yöntemi), bunlar bu yana EF yaptığınız gibi .NET Framework 4.x.

Veri ek açıklamaları ve <xref:System.ComponentModel.DataAnnotations.IValidatableObject> arabirimi hala kullanılabilir modeli, önce denetleyicinin eylemleri çağırma zamanki, bağlama sırasında model doğrulama için ancak, model ViewModel veya DTO olacak şekilde tasarlanmıştır ve bir MVC veya API önemli bir etki alanı modeli sorun.

Temizle kavramsal fark yapılan veri ek açıklamaları kullanmaya devam edebilirsiniz ve `IValidatableObject` varlık sınıfında eylemlerinizi önerilmez bir varlık sınıfı nesne parametresi alırsanız doğrulama. Bu durumda, doğrulama, model bağlama, eylem çağırmadan önce bağlı gerçekleşir ve sonuç denetlemek için denetleyicinin ModelState.IsValid özelliğini kontrol edebilirsiniz ancak daha sonra tekrar önce varlık nesnesinde kalıcı değil denetleyicideki olur DbContext, olarak Bitti beri EF 4.x.

Veri ek açıklamalarını kullanma varlık sınıfında özel doğrulama yine de uygulayabilir ve `IValidatableObject.Validate` DbContext'ın SaveChanges yöntemini geçersiz kılma yöntemi,.

Doğrulamak için bir örnek uygulamada gördüğünüz `IValidatableObject` varlıklarda [github'da bu açıklamayı](https://github.com/aspnet/EntityFrameworkCore/issues/3680#issuecomment-155502539). Bu örnek bir öznitelik tabanlı doğrulamaları işe yaramaz, ancak aynı geçersiz kılma seçeneğinde yansıma kullanarak uygulamak kolay olmalıdır.

Ancak, bir DDD açısından bakıldığında, etki alanı modeli en iyi, varlığın davranış yöntemlerini veya doğrulama kuralları uygulamak ve bildirim belirtim desenleri uygulayarak özel durumların kullanımını yalın tutulur.

Bu giriş, izin vermek için kullanıcı Arabirimi katman içinde model doğrulama kabul eder (yerine etki alanı varlıklarının) ViewModel sınıfları uygulama katmanında veri ek açıklamalarını kullanma anlamlı olabilir. Ancak, bu etki alanı modeli içinde doğrulama dışlama adresindeki yapılmalıdır değil.

### <a name="validate-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a>Varlıkları belirtimi desen ve bildirim deseni uygulayarak doğrula

Son olarak, etki alanı modeli içinde doğrulamaları uygulama bir daha ayrıntılı bildirim düzeni ile birlikte belirtimi desenini uygulama tarafından daha sonra listelenen ek kaynaklardan bazıları açıklandığı gibi yaklaşımdır.

Ayrıca bu modelleri yalnızca biri kullanabileceğiniz bahseden değer olduğu — Örneğin, Denetim ifadeleri ile el ile doğrulama, ancak bildirim desenini kullanarak, yığın ve doğrulama hatalarının listesini döndürmek için.

### <a name="use-deferred-validation-in-the-domain"></a>Ertelenmiş doğrulama etki alanında kullanma

Etki alanındaki ertelenmiş doğrulamaları uğraşmanız çeşitli yaklaşımlar vardır. Kendi kitaptaki [Implementing Domain-Driven tasarım](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon bu bölümdeki doğrulamasını açıklar.

### <a name="two-step-validation"></a>İki aşamalı doğrulama

Ayrıca, iki aşamalı doğrulama göz önünde bulundurun. Alan düzeyindeki doğrulama komut veri aktarımı nesneleri (Dto) ve etki alanı düzeyinde doğrulama varlıklarınızı içinde kullanabilirsiniz. Sonuç nesnesi yerine özel durumlar doğrulama hatalarla uğraşmak daha kolay hale getirmek için döndürerek bunu yapabilirsiniz.

Alan doğrulama ile veri ek açıklamaları kullanarak, örneğin, doğrulama tanımı yinelenen değil. Yürütme hem sunucu tarafı ve istemci tarafı Dto'lar söz konusu olduğunda yine de olabilir (komutlar ve Viewmodel'lar, örneği için).

## <a name="additional-resources"></a>Ek kaynaklar

- **Rachel Appel. ASP.NET Core MVC model doğrulama giriş** \
  <https://docs.microsoft.com/aspnet/core/mvc/models/validation>

- **Rick Anderson. Doğrulama ekleme** \
  <https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation>

- **Martin Fowler. Doğrulamaları bildirimiyle özel durumları atma değiştirme** \
  <https://martinfowler.com/articles/replaceThrowWithNotification.html>

- **Belirtimi ve bildirim desenleri** \
  <https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns>

- **Levası Gorodinski. Etki alanı Odaklı Tasarım (DDD) doğrulama** \
  <http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/>

- **Colin Jack. Etki alanı Model doğrulama** \
  <https://colinjack.blogspot.com/2008/03/domain-model-validation.html>

- **Jimmy Bogard. DDD dünyasında doğrulama** \
  <https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/>

> [!div class="step-by-step"]
> [Önceki](enumeration-classes-over-enum-types.md)
> [İleri](client-side-validation.md)
