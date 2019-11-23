---
title: Etki alanı model katmanında doğrulamaları tasarlama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Etki alanı modeli doğrulamaları için temel kavramları anlayın.
ms.date: 10/08/2018
ms.openlocfilehash: 1d3196d2130df33969ed231bccfe0fc6f0af2ad8
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295964"
---
# <a name="design-validations-in-the-domain-model-layer"></a>Etki alanı model katmanında tasarım doğrulamaları

DDD 'da, doğrulama kuralları ınvarıant olarak düşünülebilir. Bir toplamanın ana sorumluluğu, bu toplamanın içindeki tüm varlıkların durum değişikliklerinde iç varyantları zorlayamalarıdır.

Etki alanı varlıkları her zaman geçerli varlıklar olmalıdır. Her zaman doğru olması gereken bir nesne için belirli sayıda ınvaryantlar vardır. Örneğin, bir order Item nesnesi her zaman pozitif bir tamsayı ve ayrıca bir makale adı ve fiyat olması gereken bir miktara sahip olmalıdır. Bu nedenle, ınvarıant zorlaması etki alanı varlıklarının sorumluluğundadır (özellikle toplama köküdür) ve bir varlık nesnesi geçerli olmadan mevcut olamaz. Sabit kurallar yalnızca sözleşmeler olarak ifade edilir ve ihlal edildiğinde özel durumlar veya bildirimler tetiklenir.

Bunun arkasındaki nedenler birçok hatanın meydana gelir çünkü nesneler hiçbir zaman bir durumda olmamalıdır. Aşağıda, bir [çevrimiçi tartışmadaki](https://jeffreypalermo.com/2009/05/the-fallacy-of-the-always-valid-entity/)Greg başak 'dan iyi bir açıklama verilmiştir:

Şimdi de bir kullanıcı profili alan bir SendUserCreationEmailService sunuyoruz... Bu hizmette adı null olmayan bir şekilde nasıl korkutuz? Yeniden denetliyoruz mi? Veya daha olası olabilir... "sizin için en iyi" onay ve "umuyoruz" gibi bir göz atın. size göndermeden önce birisinin bothered doğrulaması gerektiğini umuyoruz. Tabii ki, bir hatayı oluşturması gereken null bir ada sahip bir müşteriyi gönderdiğimde, yazılması gereken ilk testlerin bir kısmını kullanma. Ancak, bu tür testleri yeniden yazmaya başladığımızda bir kez daha... "adın null olmasına izin verdiğimiz takdirde bu testlerin tümüne sahip olmadığımızda bekleyin"

## <a name="implement-validations-in-the-domain-model-layer"></a>Etki alanı model katmanında doğrulamaları uygulama

Doğrulamalar genellikle etki alanı varlık oluşturucularında veya varlığı güncelleştirebilme metotlarında uygulanır. Doğrulama işleminin başarısız olması durumunda, verileri doğrulama ve özel durum oluşturma gibi doğrulamaları uygulamak için birden çok yol vardır. Ayrıca, doğrulamalar için belirtim desenini kullanma gibi daha gelişmiş desenler ve her doğrulama için bir özel durum döndürmek yerine bir hata koleksiyonu döndürmek için bildirim deseni de vardır.

### <a name="validate-conditions-and-throw-exceptions"></a>Koşulları doğrulama ve özel durum throw

Aşağıdaki kod örneğinde bir özel durum oluşturarak bir etki alanı varlığındaki doğrulamaya yönelik en basit yaklaşım gösterilmektedir. Bu bölümün sonundaki başvurular tablosunda, daha önce ele aldığımız desenleri temel alarak daha gelişmiş uygulamaların bağlantılarını görebilirsiniz.

```csharp
public void SetAddress(Address address)
{
    _shippingAddress = address?? throw new ArgumentNullException(nameof(address));
}
```

Daha iyi bir örnek, iç durumun değişmediğinden ya da bir yöntemin tüm mutasyonun gerçekleşmediğinden emin olmak için gerekli olduğunu gösterir. Örneğin, aşağıdaki uygulama nesneyi geçersiz bir durumda bırakır:

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

Durumun değeri geçersizse, ilk adres satırı ve şehir zaten değiştirilmiştir. Bu durum, adresi geçersiz hale getirir.

Varlığın oluşturucusunda benzer bir yaklaşım kullanılabilir ve varlığın oluşturulduktan sonra geçerli olduğundan emin olmak için bir özel durum oluşturabilir.

### <a name="use-validation-attributes-in-the-model-based-on-data-annotations"></a>Veri ek açıklamalarına göre modelde doğrulama özniteliklerini kullanma

Gerekli veya MaxLength öznitelikleri gibi veri ek açıklamaları, [Tablo eşleme](infrastructure-persistence-layer-implemenation-entity-framework-core.md#table-mapping) bölümünde ayrıntılı olarak açıklandığı gibi EF Core veritabanı alanı özelliklerini yapılandırmak için kullanılabilir, ancak [artık EF Core varlık doğrulaması için](https://github.com/aspnet/EntityFrameworkCore/issues/3680) (<xref:System.ComponentModel.DataAnnotations.IValidatableObject.Validate%2A?displayProperty=nameWithType> yöntemi değil), .NET Framework içinde EF 4. x bu yana gerçekleştirdikleri şekilde,

Veri ek açıklamaları ve <xref:System.ComponentModel.DataAnnotations.IValidatableObject> arabirimi, model bağlama sırasında, denetleyicinin her zamanki gibi işlem yapılmadan önce model doğrulama için de kullanılabilir, ancak bu modelin bir ViewModel veya DTO olması amaçlanmıştır ve bir etki alanı modeli sorunu olmadığı bir MVC veya API.

Kavramsal farkı açık hale getirdiğiniz, eylemleriniz bir varlık sınıfı nesne parametresi alıyorsa, doğrulama için varlık sınıfında veri ek açıklamalarını ve `IValidatableObject` kullanmaya devam edebilirsiniz, ancak bu önerilmez. Bu durumda, işlem model bağlama sonrasında, eylem çağırmadan önce oluşur ve denetleyicinin ModelState. IsValid özelliğini denetleyerek sonucu denetleyebilir, ancak daha sonra yeniden, bu durum DbContext, EF 4. x bu yana yapıldığı gibi.

DbContext 'in SaveChanges metodunu geçersiz kılarak veri açıklamalarını ve `IValidatableObject.Validate` yöntemini kullanarak varlık sınıfında özel doğrulama uygulayabilirsiniz.

[GitHub 'da bu açıklamada](https://github.com/aspnet/EntityFrameworkCore/issues/3680#issuecomment-155502539)`IValidatableObject` varlıkları doğrulamak için örnek bir uygulama görebilirsiniz. Bu örnek, öznitelik tabanlı doğrulamalar yapmaz, ancak aynı geçersiz kılmada yansıma kullanarak uygulanması kolay olmalıdır.

Bununla birlikte, bir DDD görünümünde, etki alanı modeli, varlıklarınızın davranış yöntemlerinde özel durumların kullanımı ile veya doğrulama kurallarını zorlamak için belirtim ve bildirim desenleri uygulayarak en iyi şekilde korunur.

Veri açıklamalarını, Kullanıcı arabirimi katmanında model doğrulamaya izin vermek için girişi kabul edecek şekilde, ViewModel sınıflarında (etki alanı varlıkları yerine) uygulama katmanında kullanmak mantıklı olabilir. Ancak, bu, etki alanı modeli içinde doğrulamanın dışlamasıyla yapılmamalıdır.

### <a name="validate-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a>Belirtim modelini ve bildirim modelini uygulayarak varlıkları doğrulama

Son olarak, etki alanı modelinde doğrulamaları uygulamaya yönelik daha ayrıntılı bir yaklaşım, daha sonra listelenen ek kaynaklarda açıklandığı gibi belirtim deseninin bildirim düzeniyle birlikte uygulanmasıyla yapılır.

Bu modellerden yalnızca birini de kullanabilirsiniz. Örneğin, denetim deyimleriyle el ile doğrulama, ancak yığın için bildirim desenini kullanma ve doğrulama hatalarının bir listesini döndürme.

### <a name="use-deferred-validation-in-the-domain"></a>Etki alanında Ertelenmiş doğrulama kullan

Etki alanındaki ertelenmiş doğrulamalarla uğraşmak için çeşitli yaklaşımlar vardır. [Etki alanı odaklı tasarımı uygulayan](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577)kitapta, Vaughn verunbu, doğrulama konusundaki bölümünde ele alınmaktadır.

### <a name="two-step-validation"></a>İki aşamalı doğrulama

Ayrıca iki aşamalı doğrulamayı de göz önünde bulundurun. Komut Veri Aktarımı nesneleri (DTOs) ve varlıklarınızdaki etki alanı düzeyinde doğrulama üzerinde alan düzeyinde doğrulama kullanın. Doğrulama hatalarıyla daha kolay hale getirmek için özel durumlar yerine bir sonuç nesnesi döndürerek bunu yapabilirsiniz.

Veri açıklamaları ile alan doğrulamayı kullanma örneğin, doğrulama tanımını çoğaltmayın. Ancak yürütme, DTOs (örneğin, komut ve ViewModel) durumunda sunucu tarafı ve istemci tarafı olabilir.

## <a name="additional-resources"></a>Ek kaynaklar

- **Oychel Appel. ASP.NET Core MVC 'de model doğrulamasına giriş** \
  <https://docs.microsoft.com/aspnet/core/mvc/models/validation>

- **Rick Anderson. Doğrulama \ ekleniyor**
  <https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation>

- **Marwler. Doğrulamalardaki özel durumları bildirim ile değiştirme** \
  <https://martinfowler.com/articles/replaceThrowWithNotification.html>

- **Belirtim ve bildirim desenleri** \
  <https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns>

- **Lev Gorodinski. Etki alanı odaklı tasarımda doğrulama (DDD)**  \
  <http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/>

- **Colın jakı. Etki alanı modeli doğrulama** \
  <https://colinjack.blogspot.com/2008/03/domain-model-validation.html>

- **Jimmy Bogard. DDD dünyasında doğrulama** \
  <https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/>

> [!div class="step-by-step"]
> [Önceki](enumeration-classes-over-enum-types.md)
> [İleri](client-side-validation.md)
