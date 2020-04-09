---
title: Altyapı kalıcılık katmanını tasarlama
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | Altyapı kalıcılık katmanının tasarımındaki depo deseni keşfedin.
ms.date: 10/08/2018
ms.openlocfilehash: 1b2665e81ade60affa84563121c04bca08537f07
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988485"
---
# <a name="design-the-infrastructure-persistence-layer"></a>Altyapı kalıcılık katmanını tasarlama

Veri kalıcılığı bileşenleri, bir microservice(microservice veritabanı) sınırları içinde barındırılan verilere erişim sağlar. Bunlar, özel Entity Framework (EF) <xref:Microsoft.EntityFrameworkCore.DbContext> nesneleri gibi depolar ve Çalışma Birimi sınıfları gibi [bileşenlerin](https://martinfowler.com/eaaCatalog/unitOfWork.html) gerçek uygulamasını içerir. EF DbContext, Depo ve Çalışma Birimi kalıplarını her ikisini de uygular.

## <a name="the-repository-pattern"></a>Depo deseni

Depolar, veri kaynaklarına erişmek için gereken mantığı kapsülleyen sınıflar veya bileşenlerdir. Ortak veri erişim işlevselliğini merkezileştirerek daha iyi sürdürülebilirlik sağlar ve etki alanı modeli katmanından veritabanlarına erişmek için kullanılan altyapı veya teknolojiyi ayrışturarak. Varlık Çerçevesi gibi bir Nesne İlişkisel Haritalayıcı (ORM) kullanıyorsanız, LINQ ve güçlü yazma sayesinde uygulanması gereken kod basitleştirilmiştir. Bu, veri erişim tesisatı yerine veri kalıcılığı mantığına odaklanmanızı sağlar.

Depo deseni, bir veri kaynağıyla çalışmanın iyi belgelenmiş bir yoludur. [Kitap Patterns kurumsal Uygulama Mimarisi,](https://www.amazon.com/Patterns-Enterprise-Application-Architecture-Martin/dp/0321127420/)Martin Fowler aşağıdaki gibi bir depo açıklar:

> Depo, etki alanı modeli katmanları ve veri eşleme arasında bir aracının görevlerini gerçekleştirir ve bellekteki etki alanı nesneleri kümesine benzer şekilde hareket eder. İstemci nesneleri bildirimsel olarak sorgular oluşturur ve bunları yanıtlar için depolara gönderir. Kavramsal olarak, bir depo veritabanında depolanan bir nesne kümesini ve bunlar üzerinde gerçekleştirilebilecek işlemleri kapsülleyerek kalıcılık katmanına daha yakın bir yol sağlar. Depolar, aynı zamanda, açıkça ve tek bir yönde, iş etki alanı ve veri ayırma veya eşleme arasındaki bağımlılığı ayırma amacını destekler.

### <a name="define-one-repository-per-aggregate"></a>Toplam başına bir depo tanımlama

Her bir toplu veya toplam kök için bir depo sınıfı oluşturmanız gerekir. Etki Alanı Tabanlı Tasarım (DDD) desenlerine dayalı bir mikro hizmette, veritabanını güncelleştirmek için kullanmanız gereken tek kanal depolar olmalıdır. Bunun nedeni, agreganın değişmezlerini ve işlem tutarlılığını kontrol eden toplam kökle bire bir ilişki içinde olmalarıdır. Sorgular veritabanının durumunu değiştirmedığından, veritabanını diğer kanallar (CQRS yaklaşımını izleyerek yapabileceğiniz gibi) sorgulayabilir. Ancak, işlem alanı (diğer bir başkası güncelleştirmeler) her zaman depolar ve toplam kökler tarafından denetlenmelidir.

Temel olarak, bir depo etki alanı varlıkları şeklinde veritabanından gelen bellekte veri doldurmak için izin verir. Varlıklar bellekte bir kez, değiştirilebilir ve daha sonra işlemler yoluyla veritabanına geri kalıcı.

Daha önce de belirtildiği gibi, CQS/CQRS mimari deseni kullanıyorsanız, ilk sorgular etki alanı modelinin dışında yan sorgularla gerçekleştirilir ve Dapper kullanılarak basit SQL deyimleri tarafından gerçekleştirilir. Bu yaklaşım, gereksinim duyduğunuz tabloları sorgulayıp birleştirebileceğinizden ve bu sorguların toplamlardan gelen kurallarla sınırlandırılamadığından, depolardan çok daha esnektir. Bu veriler sunu katmanına veya istemci uygulamasına gider.

Kullanıcı değişiklik yaparsa, güncellenecek veriler istemci uygulamasından veya uygulama katmanına sunu katmanından (Web API hizmeti gibi) gelir. Komut işleyicisi bir komut aldığınızda, veritabanından güncelleştirmek istediğiniz verileri almak için depoları kullanırsınız. Komutlarla geçirilen verilerle bellekte güncellersiniz ve ardından bir işlem aracılığıyla veritabanındaki verileri (etki alanı varlıkları) ekler veya güncellersiniz.

Şekil 7-17'de gösterildiği gibi, her bir toplam kök için yalnızca bir depo tanımlamanız gerektiğini tekrar vurgulamak önemlidir. Toplam kök hedefine ulaşmak için, toplamdaki tüm nesneler arasında işlem tutarlılığını korumak için, veritabanındaki her tablo için hiçbir zaman bir depo oluşturmamalısınız.

![Etki alanı ve diğer altyapı ilişkilerini gösteren diyagram.](./media/infrastructure-persistence-layer-design/repository-aggregate-database-table-relationships.png)

**Şekil 7-17**. Depolar, toplamlar ve veritabanı tabloları arasındaki ilişki

Yukarıdaki diyagram Etki Alanı ve Altyapı katmanları arasındaki ilişkileri gösterir: Alıcı Toplam IBuyerRepository bağlıdır ve Sipariş Toplam IOrderRepository arabirimleri bağlıdır, bu arabirimler UnitOfWork bağlı ilgili depolar tarafından Altyapı katmanında uygulanır, ayrıca orada uygulanan, Veri katmanında tablolar erişir.

### <a name="enforce-one-aggregate-root-per-repository"></a>Depo başına bir toplam kök uygulayın

Depo tasarımınızı, yalnızca toplu köklerin depoları olması gerektiği kuralını zorlar gibi uygulamak değerli olabilir. `IAggregateRoot` İşaretçi arabirimine sahip olduğundan emin olmak için birlikte çalıştığı varlıkların türünü kısıtlayan genel veya temel depo türü oluşturabilirsiniz.

Böylece, altyapı katmanında uygulanan her depo sınıfı, aşağıdaki kodda gösterildiği gibi kendi sözleşmesini veya arabirimini uygular:

```csharp
namespace Microsoft.eShopOnContainers.Services.Ordering.Infrastructure.Repositories
{
    public class OrderRepository : IOrderRepository
    {
      // ...
    }
}
```

Her özel depo arabirimi genel IRepository arabirimini uygular:

```csharp
public interface IOrderRepository : IRepository<Order>
{
    Order Add(Order order);
    // ...
}
```

Ancak, kodun her deponun tek bir toplamla ilişkili olduğu kuralı zorlamasının daha iyi bir yolu genel bir depo türü uygulamaktır. Bu şekilde, belirli bir toplamı hedeflemek için bir depo kullandığınız açıktır. Bu, aşağıdaki kodda olduğu `IRepository` gibi genel bir temel arabirim uygulanarak kolayca yapılabilir:

```csharp
public interface IRepository<T> where T : IAggregateRoot
{
    //....
}
```

### <a name="the-repository-pattern-makes-it-easier-to-test-your-application-logic"></a>Depo deseni, uygulama mantığınızı test etmeyi kolaylaştırır

Depo deseni, ünite testleri ile uygulamanızı kolayca test etmenizi sağlar. Birim testlerinin altyapıyı değil, yalnızca kodunuzu sınadığını unutmayın, böylece depo soyutlamaları bu amaca ulaşmayı kolaylaştırır.

Daha önceki bir bölümde belirtildiği gibi, web API mikro hizmetiniz gibi uygulama katmanının gerçek depo sınıflarını uyguladığınız altyapı katmanına doğrudan bağlı olmaması için depo arabirimlerini etki alanı modeli katmanına tanımlamanız ve yerleştirmeniz önerilir. Bunu yaparak ve Web API'nızın denetleyicilerinde Bağımlılık Enjeksiyonu'nu kullanarak, veritabanından veri yerine sahte veri döndüren sahte depolar uygulayabilirsiniz. Bu ayrılmış yaklaşım, veritabanına bağlantı gerektirmeden uygulamanızın mantığını odaklayan birim testleri oluşturmanıza ve çalıştırmanıza olanak tanır.

Veritabanlarına bağlantılar başarısız olabilir ve daha da önemlisi, bir veritabanına karşı yüzlerce test çalıştırmak iki nedenden dolayı kötüdür. İlk olarak, testlerin çok sayıda nedeniyle uzun bir zaman alabilir. İkinci olarak, veritabanı kayıtları değişebilir ve testlerinizin sonuçlarını etkileyebilir, böylece tutarlı olmayabilirler. Veritabanına karşı sınama bir birim testi değil, bir tümleştirme testidir. Hızlı çalışan birçok birim testleri, ancak veritabanlarına karşı daha az tümleştirme testleri olmalıdır.

Birim testleri için endişelerin ayrılması açısından, mantığınız bellekteki etki alanı varlıklarında çalışır. Depo sınıfının bunları teslim ettiği varsayar. Mantığınız etki alanı varlıklarını modifiye ettikten sonra, depo sınıfının bunları doğru şekilde depolaacağını varsayar. Burada önemli nokta etki alanı modeli ve etki alanı mantığı karşı birim testleri oluşturmaktır. Toplam kökler DDD'deki ana tutarlılık sınırlarıdır.

eShopOnContainers'da uygulanan depolar, ef core'un değişim izleyicisini kullanarak Depo ve İş Birimi desenlerinin DbContext uygulamasına dayanır, bu nedenle bu işlevselliği yinelemiyorlar.

### <a name="the-difference-between-the-repository-pattern-and-the-legacy-data-access-class-dal-class-pattern"></a>Depo deseni ile eski Veri Erişimi sınıfı (DAL sınıfı) deseni arasındaki fark

Veri erişim nesnesi doğrudan depolamaya karşı veri erişimi ve kalıcılık işlemleri gerçekleştirir. Depo, verileri bir çalışma nesnesi biriminin belleğinde gerçekleştirmek istediğiniz işlemlerle <xref:Microsoft.EntityFrameworkCore.DbContext> (sınıfı kullanırken EF'de olduğu gibi) işaretler, ancak bu güncelleştirmeler hemen veritabanına gerçekleştirilmez.

Çalışma birimi, birden çok ekleme, güncelleştirme veya silme işlemi içeren tek bir işlem olarak adlandırılır. Basit bir ifadeyle, web sitesindeki bir kayıt gibi belirli bir kullanıcı eylemi için, tüm ekleme, güncelleştirme ve silme işlemleri tek bir işlemde işlendiği anlamına gelir. Bu, birden çok veritabanı işlemini chattier bir şekilde işlemekten daha verimlidir.

Bu çoklu kalıcılık işlemleri, uygulama katmanındaki kodunuz bunu emrettiğinde daha sonra tek bir eylemde gerçekleştirilir. Bellek içi değişiklikleri gerçek veritabanı depolamasına uygulama kararı genellikle Çalışma [Birimi deseni'ne](https://martinfowler.com/eaaCatalog/unitOfWork.html)dayanır. EF'de, Çalışma Birimi deseni <xref:Microsoft.EntityFrameworkCore.DbContext>.

Çoğu durumda, bu desen veya depolamaya karşı işlem uygulama şekli uygulama performansını artırabilir ve tutarsızlık olasılığını azaltabilir. Tüm amaçlanan işlemler tek bir işlemin parçası olarak işlendiğinden, veritabanı tablolarında işlem engellemeyi de azaltır. Bu, veritabanına karşı birçok yalıtılmış işlemi yürütmeye kıyasla daha etkilidir. Bu nedenle, seçili ORM, birçok küçük ve ayrı işlem yürütmesi yerine, aynı işlem içinde birkaç güncelleştirme eylemi gruplayarak veritabanına karşı yürütme optimize edebilirsiniz.

### <a name="repositories-shouldnt-be-mandatory"></a>Depolar zorunlu olmamalıdır

Özel depolar daha önce belirtilen nedenlerle yararlıdır ve bu eShopOnContainers sipariş microservice için bir yaklaşımdır. Ancak, bir DDD tasarımında ve hatta genel olarak .NET geliştirmede uygulanması gereken önemli bir desen değildir.

Örneğin, Jimmy Bogard, bu kılavuz için doğrudan geribildirim sağlarken, şunları söyledi:

> Bu muhtemelen benim en büyük geribildirim olacak. Ben gerçekten depoları hayranı değilim, esas olarak altta yatan kalıcılık mekanizmasının önemli ayrıntılarını gizlemek çünkü. Bu yüzden ben de komutlar için MediatR'a gidiyorum. Kalıcılık katmanının tüm gücünü kullanabilir ve tüm bu etki alanı davranışını toplu köklerime itebilirim. Ben genellikle benim depoları alay etmek istemiyorum - Ben hala gerçek bir şey ile entegrasyon testi olması gerekir. CQRS'nin olması, artık depolara ihtiyacımız olmadığı anlamına geliyordu.

Depolar yararlı olabilir, ancak Toplam desen ve zengin etki alanı modeli gibi, DDD tasarım için kritik değildir. Bu nedenle, uygun gördüğünüz gibi Depo deseni kullanın veya kullanmayın. Her neyse, bu durumda, depo tüm microservice veya sınırlı bağlam kapsar rağmen, bu durumda, EF Core kullandığınızda depo deseni kullanıyor olacaksınız.

## <a name="additional-resources"></a>Ek kaynaklar

### <a name="repository-pattern"></a>Depo deseni

- **Edward Hieatt ve Rob beni. Depo deseni.** \
  <https://martinfowler.com/eaaCatalog/repository.html>

- **Depo deseni** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/ff649690(v=pandp.10)>

- **Eric Evans' ı. Etki Alanı Odaklı Tasarım: Yazılımın Kalbinde Karmaşıklıkla Mücadele.** (Kitap; Depo deseni bir tartışma içerir) \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

### <a name="unit-of-work-pattern"></a>Çalışma deseni Birimi

- **Martin Fowler' ı. İş deseni birimi.** \
  <https://martinfowler.com/eaaCatalog/unitOfWork.html>

- **ASP.NET MVC Uygulamasında Çalışma Düzenlerinin Depo ve Biriminin Uygulanması** \
  <https://docs.microsoft.com/aspnet/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application>

>[!div class="step-by-step"]
>[Önceki](domain-events-design-implementation.md)
>[Sonraki](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
