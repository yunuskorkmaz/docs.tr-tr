---
title: Altyapı kalıcılık katmanını tasarlama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Altyapı kalıcılığı katmanının tasarımında depo modelini keşfet.
ms.date: 10/08/2018
ms.openlocfilehash: f1c5df1cc5672760374610a416ae22b45cd76c25
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73737930"
---
# <a name="design-the-infrastructure-persistence-layer"></a>Altyapı kalıcılığı katmanını tasarlama

Veri kalıcılığı bileşenleri, bir mikro hizmetin sınırları içinde (bir mikro hizmetin veritabanı) barındırılan verilere erişim sağlar. Bunlar, özel Entity Framework (EF) <xref:Microsoft.EntityFrameworkCore.DbContext> nesneleri gibi depolar ve [iş sınıfları birimi](https://martinfowler.com/eaaCatalog/unitOfWork.html) gibi bileşenlerin gerçek uygulamasını içerirler. EF DbContext, hem depoyu hem de çalışma birimi düzenlerini uygular.

## <a name="the-repository-pattern"></a>Depo deseninin

Depolar, veri kaynaklarına erişmek için gereken mantığı kapsülleyen sınıflardır veya bileşenlerdir. Daha iyi bakım sağlar ve etki alanı modeli katmanından veritabanlarına erişmek için kullanılan altyapıyı veya teknolojiyi ayırır. Entity Framework gibi bir nesne Ilişkisel Eşleyici (ORM) kullanıyorsanız, uygulanması gereken kod, LINQ ve güçlü yazma sayesinde basitleştirilmiştir. Bu, veri erişimi sıhhi tesisat yerine veri Kalıcılık mantığına odaklanmanızı sağlar.

Depo stili, bir veri kaynağıyla çalışma konusunda iyi belgelenmiş bir yoldur. [Kurumsal uygulama mimarisinin kitap desenlerinde](https://www.amazon.com/Patterns-Enterprise-Application-Architecture-Martin/dp/0321127420/), Marwler, bir depoyu aşağıda gösterildiği gibi açıklar:

> Bir depo, etki alanı modeli katmanları ve veri eşleme arasında bir aracı görevleri gerçekleştirerek, bellekteki bir etki alanı nesnesi kümesine benzer bir şekilde davranır. İstemci nesneleri bildirimli olarak sorgu oluşturma ve yanıtlar için depolara gönderme. Kavramsal olarak, bir depo veritabanında depolanan bir nesne kümesini ve bunlar üzerinde gerçekleştirilebilecek işlemleri, kalıcılık katmanına daha yakın bir şekilde sunar. Depolar, Ayrıca, iş etki alanı ve veri ayırma veya eşleme arasındaki bağımlılığı açıkça ve tek bir yönde ayırma amacını destekler.

### <a name="define-one-repository-per-aggregate"></a>Toplama başına bir depo tanımla

Her toplama veya toplama kökünde, bir depo sınıfı oluşturmalısınız. Etki alanı odaklı tasarım (DDD) desenlerine dayanan bir mikro hizmette, veritabanını güncelleştirmek için kullanmanız gereken tek kanal depolar olmalıdır. Bunun nedeni, toplamanın ıntürevlerini ve işlemsel tutarlılığını denetleyen toplam kökle bire bir ilişkiye sahip olmaleridir. Sorgular veritabanının durumunu değiştirmediğinden, veritabanını diğer kanallar aracılığıyla (CQRS yaklaşımını takip edebilirsiniz) sorgulamak çok normaldir. Ancak, işlem alanı (diğer bir deyişle, güncelleştirmeler) her zaman depolar ve toplam köklerle denetlenmelidir.

Temel olarak, bir depo, verileri etki alanı varlıkları biçimindeki veritabanından gelen bellekte doldurmanıza olanak sağlar. Varlıklar belleğe alındıktan sonra, bunlar değiştirilebilir ve sonra işlemler aracılığıyla veritabanına kalıcı olarak geri alınabilir.

Daha önce belirtildiği gibi, CQS/CQRS mimari modelini kullanıyorsanız, ilk sorgular, baber kullanılarak basit SQL deyimleriyle gerçekleştirilen, etki alanı modelinden yan sorgular tarafından gerçekleştirilir. İhtiyacınız olan tabloları sorgulayabilir ve birleştiremezsiniz ve bu sorgular toplamaların kuralları tarafından kısıtlanmadığından, bu yaklaşım depolardan çok daha esnektir. Bu veriler Sunu katmanına veya istemci uygulamasına gider.

Kullanıcı değişiklik yaptığında, görüntülenecek veriler istemci uygulamasından veya sunu katmanından uygulama katmanına (örneğin, bir Web API hizmeti) gönderilir. Komut işleyicisinde bir komut aldığınızda, veritabanından güncelleştirmek istediğiniz verileri almak için depoları kullanırsınız. Komutları ile geçilen verilerle birlikte güncelleştirir ve sonra bir işlem aracılığıyla veritabanındaki verileri (etki alanı varlıkları) eklersiniz veya güncelleyebilirsiniz.

Şekil 7-17 ' de gösterildiği gibi, her bir toplama kökü için yalnızca bir depoyu tanımlamanız gerektiğini bir kez daha vurgulamak önemlidir. Toplama içindeki tüm nesneler arasında işlem tutarlılığı sağlamak üzere toplama kökünün amacını elde etmek için, veritabanındaki her tablo için asla bir depo oluşturmanız gerekir.

![Etki alanı ve diğer altyapının ilişkilerini gösteren diyagram.](./media/infrastructure-persistence-layer-design/repository-aggregate-database-table-relationships.png)

**Şekil 7-17**. Depolar, Toplamalar ve veritabanı tabloları arasındaki ilişki

Yukarıdaki diyagramda, etki alanı ve altyapı katmanları arasındaki ilişkiler gösterilmektedir: alıcı toplamı, Ibuygurca ve sıra toplama, ıorderrepository arabirimlerine göre değişir, bu arabirimler altyapı katmanında uygulanır UnitOfWork 'e bağlı olan ilgili depolarda, veri katmanındaki tablolara erişen, orada de uygulanmış olan depolar.

### <a name="enforce-one-aggregate-root-per-repository"></a>Her depo için bir toplama kökünü zorla

Depo tasarımınızın, yalnızca toplam köklerin depolara sahip olması için kuralı zorunlu kıldığı şekilde uygulanması yararlı olabilir. `IAggregateRoot` işaretleyici arabirimine sahip olduklarından emin olmak için, çalıştığı varlıkların türünü kısıtlayan genel veya temel bir depo türü oluşturabilirsiniz.

Bu nedenle, altyapı katmanında uygulanan her depo sınıfı, aşağıdaki kodda gösterildiği gibi kendi sözleşmesini veya arabirimini uygular:

```csharp
namespace Microsoft.eShopOnContainers.Services.Ordering.Infrastructure.Repositories
{
    public class OrderRepository : IOrderRepository
    {
      // ...
    }
}
```

Her belirli depo arabirimi genel ırepository arabirimini uygular:

```csharp
public interface IOrderRepository : IRepository<Order>
{
    Order Add(Order order);
    // ...
}
```

Ancak, kodun her deponun tek bir toplama ile ilgili olduğunu bir şekilde zorlayacağından daha iyi bir yol, genel depo türünü uygulamaktır. Bu şekilde, belirli bir toplamı hedeflemek için bir depo kullandığınızı açıktır. Bu, aşağıdaki kodda olduğu gibi genel bir `IRepository` temel arabirimi uygulayarak kolayca yapılabilir:

```csharp
public interface IRepository<T> where T : IAggregateRoot
{
    //....
}
```

### <a name="the-repository-pattern-makes-it-easier-to-test-your-application-logic"></a>Depo deseninin test etme, Uygulama mantığınızı daha kolay hale getirir

Depo deseninin, uygulamanızı birim testlerle kolayca test etmenizi sağlar. Birim testlerinin altyapıyı değil yalnızca kodunuzu test eder, bu nedenle depo soyutlamaları bu amaca ulaşmak için daha kolay hale gelir.

Önceki bölümde belirtildiği gibi, Web API mikro hizmetiniz gibi uygulama katmanının, uyguladığınız altyapı katmanına doğrudan bağlı olmaması için, depo arabirimlerini etki alanı modeli katmanına tanımlamanız ve yerleştirmeniz önerilir gerçek depo sınıfları. Bunu yaparak ve Web API 'nizin denetleyicilerine bağımlılık ekleme işlemini kullanarak, veritabanından veri yerine sahte veriler döndüren sahte depolar uygulayabilirsiniz. Bu ayrılmış yaklaşım, veritabanına bağlantı gerektirmeden uygulamanızın mantığını odaklan birim testleri oluşturmanıza ve çalıştırmanıza olanak tanır.

Veritabanlarına bağlantılar başarısız olabilir ve daha da önemlisi, bir veritabanında yüzlerce testi çalıştırmak iki nedenden dolayı hatalı olur. İlk olarak, çok sayıda test yüzünden uzun zaman alabilir. İkincisi, veritabanı kayıtları, testlerin sonuçlarını değiştirebilir ve etkileyebilir, bu sayede tutarlı olmayabilir. Veritabanına karşı test etmek, bir tümleştirme testi değil, bir birim testi değildir. Hızlı bir şekilde çalışan çok sayıda birim testiniz olması gerekir, ancak veritabanlarına göre daha az tümleştirme testi olmalıdır.

Birim testleriyle ilgili sorunların ayrılması açısından, mantığınızın belleği içindeki etki alanı varlıkları üzerinde çalışır. Depo sınıfının bu şekilde teslim edildiğini varsayar. Mantığınızın etki alanı varlıklarını değiştirdiğine göre, depo sınıfının bunları doğru depolayabileceği varsayılır. Buradaki önemli nokta, etki alanı modelinize ve etki alanı mantığınıza göre birim testleri oluşturmaktır. Toplama kökleri, DDD 'daki ana tutarlılık sınırlardır.

EShopOnContainers 'da uygulanan depolar, değişiklik İzleyicisini kullanarak deponun ve Iş desenlerinin DbContext uygulamasını EF Core kullanır, bu nedenle bu işlevi yinelemeler.

### <a name="the-difference-between-the-repository-pattern-and-the-legacy-data-access-class-dal-class-pattern"></a>Depo deseninin ve eski veri erişim sınıfı (DAL sınıfı) deseninin farkı

Veri erişim nesnesi doğrudan depolamaya karşı veri erişimi ve Kalıcılık işlemleri gerçekleştirir. Bir depo, verileri iş nesnesi birimi (<xref:Microsoft.EntityFrameworkCore.DbContext> sınıfı kullanılırken EF olarak) bellekte gerçekleştirmek istediğiniz işlemlere işaret ediyor, ancak bu güncelleştirmeler veritabanına hemen yapılmaz.

Bir iş birimi, birden çok INSERT, Update veya delete işlemi içeren tek bir işlem olarak adlandırılır. Basit koşullarda, bir Web sitesindeki kayıt gibi belirli bir kullanıcı eyleminin, tüm ekleme, güncelleştirme ve silme işlemlerinin tek bir işlemde işlendiği anlamına gelir. Bu, birden çok veritabanı hareketini bir chattier şekilde işlemeye kıyasla daha etkilidir.

Bu birden çok kalıcılık işlemi daha sonra, uygulama katmanından kodunuz onu komutdaysa tek bir eylemde gerçekleştirilir. Gerçek veritabanı depolamasına bellek içi değişiklikleri uygulama kararı genellikle [iş deseninin birimi](https://martinfowler.com/eaaCatalog/unitOfWork.html)temel alınarak hesaplanır. EF 'de Iş deseninin birimi <xref:Microsoft.EntityFrameworkCore.DbContext>olarak uygulanır.

Çoğu durumda, bu model veya depolamaya yönelik işlemler uygulamanın yolu uygulama performansını artırabilir ve tutarsızlıklar olasılığını azaltabilir. Ayrıca, tüm amaçlanan işlemler bir işlemin parçası olarak yapıldığından veritabanı tablolarında işlem engellemeyi azaltır. Bu, veritabanında birçok yalıtılmış işlemi yürütmeye yönelik karşılaştırmada daha etkilidir. Bu nedenle, seçilen ORM birçok küçük ve ayrı işlem yürütmelerinin aksine, aynı işlem içinde birkaç güncelleştirme eylemini gruplandırarak veritabanına karşı yürütmeyi en iyileştirebilir.

### <a name="repositories-shouldnt-be-mandatory"></a>Depoların zorunlu olmaması gerekir

Özel depolar daha önce alıntı yapılan nedenlerle faydalıdır ve bu, eShopOnContainers 'da bir sıralama mikro hizmeti için yaklaşım olur. Ancak, bir DDD tasarımında veya genel .NET geliştirmede bile uygulamak için önemli bir model değildir.

Örneğin, cemy Bogard, bu kılavuz için doğrudan geri bildirim sağlarken, aşağıdakileri diyor:

> Büyük olasılıkla en büyük geri bildirimim olacaktır. Aslında depoların bir fanı değil, temel Kalıcılık mekanizmanın önemli ayrıntılarını gizlemiyor. Bu nedenle, komutları için de MediatR 'ye gitmem gerekir. Kalıcılık katmanının tam gücünü kullanabilir ve tüm etki alanı davranışlarını toplam köklerim halinde gönderebilirsiniz. Genellikle depolarımı hayata almak istemiyorum; yine de gerçek bir tümleştirme testinin olması gerekir. CQRS 'ye devam etmek, gerçekten de depolar için ihtiyaç duymadığımızdan geliyordu.

Depolar kullanışlı olabilir, ancak toplama deseninin ve zengin etki alanı modelinin olduğu şekilde DDD tasarımınız için kritik değildir. Bu nedenle, uygun gördüğünüz gibi depo düzenini kullanın. Yine de EF Core kullandığınızda depo deseninin kullanılması gerekir, ancak bu durumda depo tüm mikro hizmet veya sınırlanmış bağlamı kapsamaktadır.

## <a name="additional-resources"></a>Ek kaynaklar

### <a name="repository-pattern"></a>Depo stili

- **Depo deseninin** \
  <https://deviq.com/repository-pattern/>

- **Edward Hieatt ve Ramiz Me. Depo stili.** \
  <https://martinfowler.com/eaaCatalog/repository.html>

- **Depo deseninin** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/ff649690(v=pandp.10)>

- **Eric Evans. Etki alanı odaklı tasarım: yazılım Kalbunda karmaşıklık karmaşıklığı.** (Kitap; depo deseninin bir tartışmasını içerir) \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

### <a name="unit-of-work-pattern"></a>Çalışma birimi stili

- **Marwler. Çalışma birimi stili.** \
  <https://martinfowler.com/eaaCatalog/unitOfWork.html>

- **Bir ASP.NET MVC uygulamasında depo ve Iş deseni birimi uygulama** \
  <https://docs.microsoft.com/aspnet/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application>

>[!div class="step-by-step"]
>[Önceki](domain-events-design-implementation.md)
>[İleri](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
