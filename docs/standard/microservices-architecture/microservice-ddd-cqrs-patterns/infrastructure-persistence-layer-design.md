---
title: "Altyapı saklama katmanını tasarlama"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Altyapı saklama katmanını tasarlama"
keywords: Docker, Microservices, ASP.NET, Container
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/08/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 76db5388c75d4eb3b5cc23c1e57cc391a15f2934
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="designing-the-infrastructure-persistence-layer"></a>Altyapı saklama katmanını tasarlama

Veri kalıcılığı bileşenleri mikro hizmet (diğer bir deyişle, bir mikro 's veritabanı) sınırları içinde barındırılan verilere erişim sağlar. Depoları gibi bileşenlerinin gerçek uygulamayı içerir ve [iş birimi](http://martinfowler.com/eaaCatalog/unitOfWork.html) özel EF DBContexts gibi sınıflara.

## <a name="the-repository-pattern"></a>Depo düzeni

Depoları sınıfları veya veri kaynaklarına erişmek için gerekli mantığı kapsülleyen bileşenler markalarıdır. Bunlar daha iyi bakım sağlayarak ve altyapı ya da etki alanı modeli katmandan veritabanlarına erişmek için kullanılan teknoloji kesilmesi ortak veri erişim işlevselliği, merkezileştirme. Entity Framework gibi bir ORM kullanırsanız, uygulanmalı kod, LINQ ve güçlü yazarak sayesinde basitleştirilmiştir. Bu erişmelerine tesisat veri kalıcılığı mantığı yerine veri odaklanmanıza olanak tanır.

Depo düzeni, veri kaynağı ile çalışmanın iyi belgelenmiş bir yoludur. Kitaptaki [Kurumsal uygulama mimarisi desenleri](https://www.amazon.com/Patterns-Enterprise-Application-Architecture-Martin/dp/0321127420/), Martin Fowler depo gibi açıklar:

Depo bir etki alanı nesneleri bellekte kümesi benzer bir şekilde davranan bir aracı veri eşleme ve etki alanı modeli katmanlar arasında görevleri gerçekleştirir. İstemci nesneleri bildirimli olarak sorgular oluşturmak ve bunları yanıtlar için depoları gönderir. Kavramsal olarak, bir depo veritabanı ve saklama katmanını daha yakın olan bir yol sağlayarak bunlar üzerinde gerçekleştirilen işlemler depolanan nesneler kümesini yalıtır. Depoları, ayrıca, iş etki alanı ve veri ayırma arasındaki bağımlılığı açıkça ve bir yönde ayırma veya eşlemesi amacını desteklemez.

### <a name="define-one-repository-per-aggregate"></a>Bir havuz başına toplam tanımlayın

Her toplama veya toplama kökü için bir depo sınıfına oluşturmanız gerekir. Etki alanı Odaklı Tasarım Desenleri esas alarak bir mikro içinde veritabanını güncelleştirmek için kullanması gereken yalnızca kanal depoları olmalıdır. Bire bir ilişki toplama 's invariants ve işlemsel tutarlılık denetimleri toplama köküne sahip olan olmasıdır. Diğer aracılığıyla veritabanını sorgulamak uygundur kanallar (CQRS yaklaşımı yapabilirsiniz gibi), sorguları veritabanının durumu değiştirmeyin çünkü. Ancak, işlem alanı — güncelleştirmeleri — her zaman depoları ve birleşik kökleri tarafından denetlenmesi gerekir.

Temel olarak, bir depo, etki alanı varlıklar biçiminde veritabanından gelen bellekte verilerini doldurmak sağlar. Varlıkları bellekte eklendiğinde bunlar değiştirilebilir ve işlemler üzerinden veritabanına kalıcı.

CQS/CQRS tasarım örüntüsü kullanıyorsanız, daha önce belirtildiği gibi ilk sorguları Dapper kullanarak basit SQL deyimleri tarafından gerçekleştirilen etki alanı modeli dışında yan sorgular tarafından gerçekleştirilir. Bu yaklaşım depoları daha esnek sorgu ve tablo birleştirme için gereken ve bu sorguların toplamalar kuralları tarafından sınırlı değildir çok daha fazladır. Bu verileri, sunu katmanı veya istemci uygulamaya gider.

Kullanıcı değişiklikler yaparsa, güncelleştirilmesi için verileri (örneğin, bir Web API hizmeti) uygulama katmanına istemci uygulaması ya da sunu katmanı gelecektir. Komut işleyicisinde bir komutla (veri) aldığınızda, veritabanından güncelleştirmek istediğiniz veri almak için depoları kullanın. Bellekte komutlarıyla geçirilen bilgileriyle güncelleştirmeniz ve ardından ekleyin veya bir işlem aracılığıyla veritabanındaki verileri (etki alanı varlıklar) güncelleştirin.

Bu yalnızca bir depo her toplama kökü için tanımlanmalıdır, Şekil 9-17'de gösterildiği gibi unutmayın. Toplama içindeki tüm nesneler arasında işlemsel tutarlılık sağlamak için birleşik kök hedefe ulaşmak için hiçbir zaman veritabanında her tablo için depo oluşturmanız gerekir.

![](./media/image18.png)

**Şekil 9-17**. Depoları, toplamları ve veritabanı tabloları arasındaki ilişki

### <a name="enforcing-one-aggregate-root-per-repository"></a>Havuz başına bir toplama kök zorlama

Yalnızca toplama kökleri depoları olmalıdır kural zorlar deposu tasarımınızı şekilde uygulamak için yararlı olabilir. IAggregateRoot işaret arabirimi sahip olduklarından emin olmak için birlikte çalıştığı varlık türünü kısıtlayan bir genel veya temel depo türü oluşturabilirsiniz.

Bu nedenle, altyapı katmanında uygulanan her depo sınıfına aşağıdaki kodda gösterildiği gibi kendi sözleşme veya arabirimini uygulayan:

```csharp
namespace Microsoft.eShopOnContainers.Services.Ordering.Infrastructure.Repositories
{
    public class OrderRepository : IOrderRepository
    {
```

Her özel depo arabirimi genel IRepository arabirimini uygulayan:

```csharp
public interface IOrderRepository : IRepository<Order>
{
    Order Add(Order order);
    // ...
}
```

Ancak, kuralı zorunlu kodu daha iyi bir yolu, bir depo belirli bir toplama hedeflemek için kullandığınız açık olacak şekilde bir genel depo türü uygulamak için her deposu için tek bir toplama ilgili emin olur. Bu, aşağıdaki kod olduğu gibi IRepository temel arabirim o genel uygulayarak kolayca gerçekleştirilebilir:

```csharp
  public interface IRepository<T> where T : IAggregateRoot
```

### <a name="the-repository-pattern-makes-it-easier-to-test-your-application-logic"></a>Depo düzeni, uygulamanızın mantığı test kolaylaştırır

Havuz deseni kolayca uygulamanız ile birim testleri test etmenizi sağlar. Depo soyutlamalar bu hedefe ulaşmak kolaylaştırmak için birim testleri yalnızca kodu, değil altyapı, test olduğunu unutmayın.

Bir önceki bölümünde belirtildiği gibi tanımlayın ve (örneğin, Web API mikro) uygulama katmanı altyapı katmanda doğrudan bağlı değildir şekilde deposu arabirimleri etki alanı modeli katmanında olduğu yerleştirin önerilir. Gerçek depo sınıflarını uygulanmadı. Bunun yapılması ve Web API denetleyicilerinin içinde bağımlılık ekleme kullanılarak veritabanından veri yerine sahte veriler döndürmek sahte depoları uygulayabilirsiniz. Ayrılmış bir yaklaşım oluşturmanıza olanak sağlar ve çalışma birim testleri yalnızca, uygulama mantığını veritabanı bağlantısı gerektirmeden test edebilirsiniz.

Veritabanı bağlantıları başarısız olabilir ve daha da önemlisi, bir veritabanına karşı testleri yüzlerce çalıştıran iki nedenden dolayı bozuk. İlk olarak, bu sayıda testleri nedeniyle çok zaman alabilir. İkinci olarak, veritabanı kayıtlarını bir değiştirebilir ve böylece bunlar tutarlı olmayabilir, test sonuçlarını etkileyebilir. Veritabanına karşı test bir birim testleri ancak bir tümleştirme test değil. Hızlı çalışan birçok birim testleri olmalıdır, ancak daha az tümleştirme veritabanları karşı sınar.

Birim testleri endişelerini ayrılması açısından, etki alanı varlıkları bellekte mantığınızı çalıştırır. Bu depo sınıfını olanlar teslim varsayar. Etki alanı varlıkları mantığınızı değiştirir sonra depo sınıfını bunları doğru depolayacak varsayar. Burada önemli olan nokta, etki alanı modeli ve kendi etki alanı mantığı karşı birim testleri oluşturmaktır. Birleşik kökleri GGG, ana tutarlılık sınırları değildir.

### <a name="the-difference-between-the-repository-pattern-and-the-legacy-data-access-class-dal-class-pattern"></a>Depo düzeni ve eski veri erişimi sınıfı (DAL sınıfı) düzeni arasındaki fark

Veri erişim nesnesi doğrudan depolama karşı veri erişimi ve sürdürme işlemleri gerçekleştirir. İş nesnesi (EF) DbContext kullanırken olduğu gibi ancak bu güncelleştirmeler birimi bellekte gerçekleştirmek istediğiniz işlem verilerle hemen gerçekleştirilen olmayan depo işaretler.

Bir iş birimine birden çok Ekle içeren tek bir işlem olarak güncelleştirme veya silme işlemleri için denir. Basitçe, belirli bir kullanıcı eylemi (örneğin, bir Web sitesinde kayıt), tüm INSERT, update ve delete işlemleri tek bir işlemde işlenme anlamına gelir. Bu, birden çok veritabanı işlemleri chattier şekilde işleme değerinden daha verimli olur.

Bu uygulama katmanı kodunuzdan komutlarını çalıştırırken bu birden çok Kalıcılık işlemleri daha sonra tek bir eylemle gerçekleştirilir. Asıl veritabanını depolama birimine bellek içi değişiklikleri uygulamadan hakkında karar genellikle dayanır [iş birimi düzeni](http://martinfowler.com/eaaCatalog/unitOfWork.html). EF içinde iş birimi düzeni DBContext uygulanır.

Çoğu durumda bu deseni veya depolama karşı işlemleri uygulamanın yolu uygulama performansını artırmak ve tutarsızlıklar olasılığını azaltmak. Ayrıca, tüm hedeflenen işlemleri bir işlemin bir parçası olarak kaydedilmiş olduğundan veritabanı tablolarında engelleme işlem azaltır. Bu veritabanında çok sayıda yalıtılmış işlemleri yürütülürken kıyasla daha verimli olur. Bu nedenle, seçili ORM çok sayıda küçük ve ayrı işlem yürütmeleri aksine aynı işlem içindeki birkaç güncelleştirme eylemleri gruplandırarak veritabanında yürütme iyileştirebilir.

### <a name="repositories-should-not-be-mandatory"></a>Depoları zorunlu olmamalıdır

Özel depoları daha önce bildirdi nedenlerle yararlıdır ve sıralama mikro hizmet eShopOnContainers içinde bir yaklaşım olmasıdır. Ancak, bir DDD tasarımı uygulamak ve hatta genel .NET geliştirme için temel bir desen değil.

Örneği için Jimmy bu kılavuz, doğrudan geribildirimi verirken Bogard aşağıda belirtilmektedir:

Bu büyük olasılıkla büyük bildirimimle olması. Çoğunlukla bunlar temel kalıcılığı mekanizmasının önemli ayrıntıları gizlemek için gerçekten, depolarının fan değilim. Buna ait neden MediatR için komutları için çok duruma. I saklama katmanını gücünü kullanın ve bu etki alanı davranışı toplama my kökleri gönderme. Genellikle my depoları mock istemiyorum – hala bu tümleştirmesine sahip istiyorum gerçek bir şey ile test. CQRS giderek biz gerçekten depoları gereksinimini daha olmadığına yönelikti anlamına gelir.

Biz depoları kullanışlı ancak toplama düzeni ve zengin etki alanı modeli şekilde, DDD kritik olmadıklarını bildiremedi. Bu nedenle, havuz deseni kullanıp, gördüğünüz gibi sığmayacak.

## <a name="the-specification-pattern"></a>Belirtimi düzeni

(Tam adını sorgu belirtimi düzeni olur) belirtimi Düzen burada bir sorgu tanımını sıralama ve mantıksal disk belleği isteğe bağlı koyabilirsiniz yer olarak tasarlanmış bir Domain-Driven tasarım deseni yöneliktir.

Belirtimi düzeni sorguda bir nesne tanımlar. Örneğin, bazı ürünler için arayan bir disk belleğine alınan sorgu kapsüllemek için gerekli giriş parametreleri (pageNumber, pageSize, filtre, vb.) alır PagedProduct belirtimi oluşturabilirsiniz. Sonra tüm depo yöntemi (genellikle bir List() aşırı) içinde bir ISpecification kabul ve o belirtimine göre beklenen sorgusunu çalıştırın.

Bu yaklaşımın birkaç avantaj vardır:

* Belirtimi hakkında tartışın bir ad (aksine, sadece bir grup LINQ ifadeleri) içeriyor.

* Belirtimi doğru olduğundan emin olmak için birim yalıtım modunda test olabilir. Benzer davranış ihtiyacınız varsa onu da kolayca yeniden kullanılabilir. Örneğin bir MVC görünümü eylem ve bir Web API eylemi yanı sıra çeşitli Hizmetleri'nde.

* Bir belirtimi döndürülecek veri şekli tanımlamak için de kullanılabilir, yalnızca verileri sorgular dönebilmek bunlar gerekli. Bu web uygulamaları (Bu, genellikle iyi bir fikir değil) geç yükleme gereksinimini ortadan kaldırır ve bu ayrıntılarla kalabalık haline gelen deposu uygulamaları tutar.

Bir genel belirtimi arabirimi, aşağıdaki kod örneğidir [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb ).

```csharp
// https://github.com/dotnet-architecture/eShopOnWeb 
public interface ISpecification<T>
{
    Expression<Func<T, bool>> Criteria { get; }
    List<Expression<Func<T, object>>> Includes { get; }
    List<string> IncludeStrings { get; }
}
```

Yaklaşan bölümlerde nasıl Entity Framework Çekirdek 2.0 belirtimi desenle uygulanacağını ve herhangi bir havuz sınıfın kullanma anlatılmıştır.

**Önemli Not:** belirtimi desen aşağıdaki ek kaynaklara olduğu gibi birçok farklı şekillerde uygulanabilir eski bir düzeni olduğunu. Bir desen/fikir eski yaklaşımlar iyi biliyorum, ancak LINQ ve ifadeler gibi modern dil özelliklerinden olmuyor eski uygulamalarının kaybolacağını unutmayın.

## <a name="additional-resources"></a>Ek kaynaklar

### <a name="the-repository-pattern"></a>Depo düzeni

-   **Edward Hieatt ve Ramiz bana. Depo düzeni. ** 
     [ *http://martinfowler.com/eaaCatalog/repository.html*](http://martinfowler.com/eaaCatalog/repository.html)

-   **Depo düzeni**
    [*https://msdn.microsoft.com/library/ff649690.aspx*](https://msdn.microsoft.com/library/ff649690.aspx)

-   **Depo düzeni: Bir veri Kalıcılık özeti**
    [*http://deviq.com/repository-pattern/*](http://deviq.com/repository-pattern/)

-   **Eric Evans. Etki alanı Odaklı Tasarım: Yazılım Kalp karmaşıklığı Tackling.** (Kitap; havuz deseni tartışması içerir) [ *https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

### <a name="unit-of-work-pattern"></a>Çalışma deseni birimi

-   **Martin Fowler. Çalışma deseni birimidir. ** 
     [ *http://martinfowler.com/eaaCatalog/unitOfWork.html*](http://martinfowler.com/eaaCatalog/unitOfWork.html)

<!-- -->

-   **Bir ASP.NET MVC uygulamasındaki depo ve iş desenleri ölçü uygulama**
    [*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/ implementing-the-Repository-and-Unit-of-Work-Patterns-in-an-ASP-NET-MVC-Application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)

### <a name="the-specification-pattern"></a>Belirtimi düzeni

-   **Belirtimi deseni. ** 
     [ *http://deviq.com/specification-pattern/*](http://deviq.com/specification-pattern/)

-   **Evans, Eric (2004). Tasarım güdümlü bir etki alanı. Addison-Wesley. p. 224.**

-   **Belirtimleri. Martin Fowler**
    [*https://www.martinfowler.com/apsupp/spec.pdf/*](https://www.martinfowler.com/apsupp/spec.pdf)

>[!div class="step-by-step"]
[Önceki] (etki alanı-olayları-design-implementation.md) [sonraki] (infrastructure-persistence-layer-implemenation-entity-framework-core.md)
