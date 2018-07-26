---
title: Altyapı Kalıcılık katmanını tasarlama
description: Altyapı Kalıcılık katmanını tasarlama konusunda bilgi edinin.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/28/2017
ms.openlocfilehash: a0fcaead363e41f0dd02ed1e2ddfc90afb8d0c57
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404479"
---
# <a name="designing-the-infrastructure-persistence-layer"></a>Altyapı Kalıcılık katmanını tasarlama

Veri kalıcılığı bileşenleri (diğer bir deyişle, bir mikro hizmet ait veritabanı) bir mikro hizmet sınırları içinde tutulan verilere erişim sağlar. Depoları gibi bileşenlerin gerçek uygulama içerdikleri ve [iş birimi](https://martinfowler.com/eaaCatalog/unitOfWork.html) sınıflar, özel Entity Framework (EF) gibi <xref:Microsoft.EntityFrameworkCore.DbContext> nesneleri.

## <a name="the-repository-pattern"></a>Depo düzeni

Depoları, sınıfları veya veri kaynaklarına erişmek için gerekli mantığı kapsülleyen bileşenler olabilir. Bunlar daha iyi sürdürülebilirliği sağlamak ve altyapı veya etki alanı modeli katmandan veritabanlarına erişmek için kullanılan teknoloji ayırma ortak veri erişimi işlevleri, tek bir merkezden yönetin. Entity Framework gibi bir nesne ilişkisel eşleme (ORM) kullanmanız durumunda uygulanması gereken kod, LINQ ve güçlü yazım, yazım sayesinde basitleştirilir. Bu erişim tesisat veri kalıcılığı mantığı yerine veri çubuğunda odaklanmanıza olanak tanır.

Depo düzeni, bir veri kaynağı ile çalışmanın iyi belgelendirilmiş bir yoludur. Kitaptaki [Kurumsal uygulama mimarisi desenleri](https://www.amazon.com/Patterns-Enterprise-Application-Architecture-Martin/dp/0321127420/), Martin Fowler bir depo gibi açıklar:

> Bir depo, bir etki alanı bir nesne bellekte benzer şekilde davranan bir aracı veri eşleme ve etki alanı modeli Katmanlar arasındaki görevleri gerçekleştirir. İstemci nesneleri bildirimli olarak sorgular oluşturabilir ve bunların yanıtlarını bulmak için de gönderebilirsiniz. Kavramsal olarak, bir depo sağlayarak Kalıcılık katman için daha yakın bir şekilde bunlar üzerinde gerçekleştirilen işlemleri ve veritabanı içinde depolanan nesneleri kümesini yalıtır. Depoları, ayrıca, amacı, açıkça ve tek yönlü iş etki alanı ve veri ayırma arasındaki bağımlılığı ayırma veya eşleme, destekler.

### <a name="define-one-repository-per-aggregate"></a>Bir havuz başına toplam tanımlama

Her toplama ya da toplama kökü için bir depo sınıfına oluşturmanız gerekir. Etki alanı Odaklı Tasarım (DDD) modellerini bir mikro hizmet içinde veritabanını güncellemek için kullanmalısınız yalnızca kanalı depoları olmalıdır. Toplam 's okuduğunuzda ve işlemsel tutarlılık denetimlerini toplama kök ile bire bir ilişki sahip oldukları budur. Diğer ile veritabanını sorgulamak uygundur kanallar (bir CQRS yaklaşımı yapabilirsiniz gibi), çünkü sorguları veritabanının durumu değişmez. Ancak, işlem alanı (diğer bir deyişle, güncelleştirmeleri) her zaman depolar ve toplama kökleri tarafından denetlenebilir.

Temel olarak, bir depo şeklinde etki alanı varlıklarının veritabanından gelen bellekteki verileri doldurmak sağlar. Varlıkları bellekte eklendiğinde bunlar değiştirilebilir ve ardından aracılığıyla işlemleri veritabanına kalıcı.

CQS/CQRS mimari deseni ifade kullanıyorsanız, daha önce belirtildiği gibi ilk sorgu yan sorguları dışında Dapper kullanarak basit SQL deyimleri tarafından gerçekleştirilen etki alanı modeli tarafından gerçekleştirilir. Bu yaklaşım depoları daha esnek olduğundan, sorgu ve tüm tabloları birleştirme gerekir ve bu sorguları kurallarıyla toplamlardan sınırlı olmayan çok daha fazla olur. Bu verileri, sunu katmanı veya istemci uygulamaya gider.

Kullanıcı değişiklikleri yaparsa, güncelleştirilecek veriler istemci uygulaması veya sunu katmanı uygulama katmanına (örneğin, bir Web API'si hizmeti) gelir. Komut işleyicisinde bir komutla veri aldığında, veritabanından güncelleştirmek istediğiniz veri almak için depoları kullanın. Bellekte komutlara geçirilen bilgileriyle güncelleştirmeniz ve sonra ekleyin veya bir işlem aracılığıyla veritabanındaki verilerle (etki alanı varlıklarının) güncelleştirin.

Bu yalnızca bir depoyu her toplama kök için tanımlanmalıdır, Şekil 9-17'de gösterildiği gibi unutmayın. Toplama içindeki tüm nesneler arasında işlem tutarlılığını korumak için toplama köküne hedefe ulaşmak için hiçbir zaman her tablo için bir depo veritabanında oluşturmanız gerekir.

![](./media/image18.png)

**Şekil 9-17**. Depoları, toplamlar ve veritabanı tabloları arasındaki ilişki

### <a name="enforcing-one-aggregate-root-per-repository"></a>Havuz başına bir toplama kök zorlama

Yalnızca toplama kökleri depoları olmalıdır kuralı zorlayan depo tasarımınızı şekilde uygulamak yararlı olabilir. Çalıştığını sahip olduklarından emin olmak için varlık türü kısıtlar bir genel veya taban depo türü oluşturabilirsiniz `IAggregateRoot` arabirim işaretçisi.

Bu nedenle, altyapı katmanında uygulanan her bir depo sınıfına aşağıdaki kodda gösterildiği gibi kendi sözleşme veya arabirim uygular:

```csharp
namespace Microsoft.eShopOnContainers.Services.Ordering.Infrastructure.Repositories
{
    public class OrderRepository : IOrderRepository
    {
      // ...
    }
}
```

Her depoyu arabirimi genel IRepository arabirim uygular:

```csharp
public interface IOrderRepository : IRepository<Order>
{
    Order Add(Order order);
    // ...
}
```

Ancak, daha iyi bir yolu kuralı uygulamak için aşağıdaki kod her depo için tek bir toplamada ilişkilidir genel depo türü uygulamaktır. Bu şekilde, belirli bir toplama hedeflemek için bir depo kullanmakta olduğunuz açıktır. Kolayca yapılabilir genel uygulayarak `IRepository` aşağıdaki kodda gösterildiği gibi temel arabirim:

```csharp
public interface IRepository<T> where T : IAggregateRoot
{
    //....
}
```

### <a name="the-repository-pattern-makes-it-easier-to-test-your-application-logic"></a>Depo düzeni uygulama mantığınızın test etmek kolaylaştırır

Depo düzeni kolayca birim testleriyle uygulamanızı test etmek sağlar. Depo soyutlama bu hedefe ulaşmak kolaylaştırmak için birim testleri yalnızca kod, altyapıya değil, test etmenizi unutmayın.

Bir önceki bölümde belirtildiği gibi tanımlamak ve gibi Web API'si mikro hizmet uygulama katmanı doğrudan altyapı katmana bağlı olmayan şekilde deposu arabirimleri etki alanı model katmanında burada uyguladık yerleştirmeniz önerilir Gerçek depoyu sınıflar. Bunun yapılması ve Web apı'nizin denetleyicileri bağımlılık ekleme kullanılarak veritabanından veri yerine sahte veriler döndürmek sahte depoları uygulayabilirsiniz. Ayrılmış bu yaklaşım, yalnızca mantıksal uygulamanızın veritabanı bağlantısını gerek kalmadan test birim testleri oluşturma ve çalıştırma olanak tanır.

Veritabanlarına bağlantı başarısız olabilir ve daha da önemlisi, testleri yüzlerce bir veritabanına yönelik olarak çalışan iki nedenden dolayı bozuk. İlk olarak, uygulamanın çok sayıda testler nedeniyle uzun sürebilir. İkinci olarak, veritabanı kayıtlarını bir değiştirme ve böylece bunlar tutarlı olmayabilir, testlerin sonuçları etkiler. Veritabanına karşı test etme, birim testi ancak bir tümleştirme testini değildir. Birçok birim testleri hızlı çalışıyor olması gerekir, ancak veritabanına göre daha az tümleştirme testleri.

Görev ayrımı nettir birim testleri için açısından, etki alanı varlıklarının bellekte mantığınızı çalışır. Bu depo sınıfına Bu teslim ettiğini varsayar. Etki alanı varlıklarının mantığınızı değiştirir sonra depo sınıfını bunları doğru bir şekilde depolar varsayar. Burada önemli olan nokta, etki alanı modeliniz ve kendi etki alanı mantığı karşı birim testleri oluşturmaktır. Toplama kökleri DDD, ana tutarlılık sınırlarıdır.

### <a name="the-difference-between-the-repository-pattern-and-the-legacy-data-access-class-dal-class-pattern"></a>Depo düzeni ve eski veri erişim sınıfı (DAL sınıfı) deseni arasındaki fark

Veri erişim nesnesi doğrudan depolama karşı veri erişimi ve Kalıcılık işlemleri gerçekleştirir. İş nesnesi birimi bellekte gerçekleştirmek istediğiniz işlemleri verileri bir depo işaretler (EF kullanırken olduğu gibi <xref:Microsoft.EntityFrameworkCore.DbContext> sınıfı), ancak bu güncelleştirmeleri hemen gerçekleştirilen değildir.

Bir iş birimi, birden çok ekleme içeren tek bir işlem olarak güncelleştirme veya silme işlemleri ifade edilir. Basit bir deyişle, bir Web sitesinde bir kayıt gibi belirli bir kullanıcı eylemi için tüm INSERT, update ve delete işlemleri tek bir işlemde işlenme anlamına gelir. Bu, birden çok veritabanı işlemleri chattier bir şekilde işleme değerinden daha verimli olur.

Bu uygulama katmanına kodunuzdan komutları kullanılırken bu birden çok Kalıcılık işlemleri daha sonra tek bir eylem içinde gerçekleştirilir. Asıl veritabanı depolama alanı için bellek içi değişikliklerini uygulama hakkında karar genellikle dayanır [iş birimi deseni](https://martinfowler.com/eaaCatalog/unitOfWork.html). EF, iş birimi deseni olarak uygulanan <xref:Microsoft.EntityFrameworkCore.DbContext>.

Çoğu durumda, bu desen veya depolama işlemleri uygulamanın yolu sağlayarak uygulama performansını artırıp tutarsızlıklar olasılığını azaltmak. Hedeflenen tüm işlemler bir işlemin bir parçası olarak kaydedilmiş olduğundan veritabanı tablolarında engelleme işlem de azaltır. Bu, birçok yalıtılmış işlemleri veritabanına karşı yürütme kıyasla daha verimli olur. Bu nedenle, seçili ORM, birçok küçük ve ayrı işlem yürütmeleri aksine, aynı işlem içinde birkaç güncelleştirme eylemleri gruplandırarak veritabanına karşı yürütme iyileştirebilirsiniz.

### <a name="repositories-shouldnt-be-mandatory"></a>Depoları zorunlu olmamalıdır

Özel depoları daha önce bahsedilen nedenlerle yararlıdır ve hizmetine sıralama mikro hizmet yaklaşımı olmasıdır. Ancak, bir DDD tasarım uygulayın ve hatta genel .NET geliştirme için temel bir desen değildir.

Örneğin, Jimmy bu kılavuz için doğrudan geri bildirim sağlanırken Bogard aşağıdaki söylenebilir:

> Bu, büyük olasılıkla büyük bildirimimi olacaktır. Çoğunlukla, temel alınan kalıcılığı mekanizmasının önemli ayrıntıları gizlemek için gerçekten bir sporseverseniz, depolarının değilim. Cihazın neden MediatR için komutlar için çok ederim. Ben Kalıcılık katman tam gücünden yararlanın ve bu etki alanı davranışını my toplama kökleri anında iletme. Genellikle my depoları sahte istemiyorum – miyim tümleştirme gereken gerçek bir şey ile test. CQRS devam ediyoruz gerçekten depoları gereksinimini artık yoktu, geliyordu.

Depoları yararlı olur, ancak bunlar toplama düzeni ve zengin bir etki alanı modeli uygun şekilde, DDD için kritik olmayan. Bu nedenle, depo deseni kullanıp, uygun şekilde.

## <a name="the-specification-pattern"></a>Belirtimi deseni

(Tam adını sorgu belirtimi deseni olacaktır) belirtimi burada bir sorgu tanımını sıralama ve mantıksal disk belleği isteğe bağlı koyabilirsiniz yer olarak tasarlanmış bir DDD deseni modelidir.

Belirtimi deseni bir sorgu bir nesneyi tanımlar. Örneğin, bazı ürünler için bir disk belleğine alınan sorgu kapsüllemek için oluşturabileceğiniz bir `PagedProduct` gerekli giriş parametrelerini gibi alan belirtimi `pageNumber`, `pageSize`, `filter`vb. Tüm depo yöntemi (genellikle bir List() aşırı yük) içinde daha sonra kabul bir `ISpecification` ve o belirtimine göre beklenen sorgusunu çalıştırın.

Bu yaklaşımın çeşitli avantajları vardır:

- Belirtimi hakkında tartışmak bir ad (aksine, sadece bir grup LINQ ifadesinin) sahiptir.

- Belirtimi, doğru olduğundan emin olmak için birim test yalıtım modunda olabilir. Benzer bir davranış ihtiyacınız varsa onu da bir kolayca yeniden kullanılabilir. Örneğin bir MVC görünümü eylem ve bir Web API eylemi yanı sıra çeşitli hizmetler.

- Belirtim döndürülecek veri şeklini tanımlamak için de kullanılabilir, sorgular yalnızca verileri geri dönebilmek bunlar gereklidir. Bu genellikle önerilmez, web uygulamalarında yavaş yükleme gereğini ortadan kaldırır ve bu ayrıntılarla dağınık hale gelen depo uygulamaları tutar.

Aşağıdaki kod, bir genel belirtimi arabirimi örnektir [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb).

```csharp
// https://github.com/dotnet-architecture/eShopOnWeb
public interface ISpecification<T>
{
    Expression<Func<T, bool>> Criteria { get; }
    List<Expression<Func<T, object>>> Includes { get; }
    List<string> IncludeStrings { get; }
}
```

Sonraki bölümlerde EF Core ile belirtimi düzeni nasıl uygulayacağınıza karar açıklayan 2.x ve herhangi bir depo sınıfın kullanma.

> [!IMPORTANT]
> Belirtimi desen aşağıdaki ek kaynaklara olduğu gibi birçok farklı yolla uygulanabilir eski bir desendir. Bir desen/fikir biliyorsanız, ancak LINQ ve ifadeler gibi modern dil özelliklerinden olmuyor eski uygulamaları dikkat eski yaklaşım uygundur.

## <a name="additional-resources"></a>Ek kaynaklar

### <a name="the-repository-pattern"></a>Depo düzeni

- **Depo düzeni**
  [https://deviq.com/repository-pattern/](https://deviq.com/repository-pattern/)

- **Edward Hieatt ve Rob bana. Depo deseni.**
  [_https://martinfowler.com/eaaCatalog/repository.html_](https://martinfowler.com/eaaCatalog/repository.html)

- **Depo düzeni**
  [_https://docs.microsoft.com/previous-versions/msp-n-p/ff649690(v=pandp.10)_](https://docs.microsoft.com/previous-versions/msp-n-p/ff649690(v=pandp.10))

- **Eric Evans. Etki alanı Odaklı Tasarım: Yazılım kalbi karmaşıklığı bağlayabileceğiniz.** (Kitap; depo düzeni hakkında ayrıntılı bilgi içerir) [_https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/_](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

### <a name="unit-of-work-pattern"></a>Çalışma deseni birimi

- **Martin Fowler. Çalışma deseni birimidir.**
  [_https://martinfowler.com/eaaCatalog/unitOfWork.html_](https://martinfowler.com/eaaCatalog/unitOfWork.html)

- **Bir ASP.NET MVC uygulamasındaki depo ve iş birimi desenleri uygulama**
  [_https://docs.microsoft.com/aspnet/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application_](https://docs.microsoft.com/aspnet/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)

### <a name="the-specification-pattern"></a>Belirtimi deseni

- **Belirtimi deseni.**
  [_https://deviq.com/specification-pattern/_](https://deviq.com/specification-pattern/)

- **Evans, Eric (2004). Etki alanı Odaklı Tasarım. Addison Wesley. p. 224.**

- **Belirtimleri. Martin Fowler**
  [_https://www.martinfowler.com/apsupp/spec.pdf/_](https://www.martinfowler.com/apsupp/spec.pdf)

>[!div class="step-by-step"]
[Önceki](domain-events-design-implementation.md)
[İleri](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
