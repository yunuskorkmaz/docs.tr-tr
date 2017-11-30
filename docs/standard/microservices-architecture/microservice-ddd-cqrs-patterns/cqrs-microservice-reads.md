---
title: "Uygulama okuma/CQRS mikro hizmet sorguları"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Uygulama okuma/CQRS mikro hizmet sorguları"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: e017aaaa701d8033110be8d6244d3e1120fc4fd9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-readsqueries-in-a-cqrs-microservice"></a>Uygulama okuma/CQRS mikro hizmet sorguları

Okuma/sorguları, sıralama mikro hizmet eShopOnContainers başvuru uygulamadan sorgularından bağımsız olarak DDD modelini ve işlem alanı uygular. Öncelikle taleplerini sorgular ve işlemler için önemli ölçüde farklı olduğu için bu gerçekleştirilir. Yazma etki alanı mantığı ile uyumlu olması gereken işlemleri yürütün. Sorguları, diğer yandan ıdempotent olan ve etki alanı kurallardan yinelenmeli.

Şekil 9-3'te gösterildiği gibi bir yaklaşım basittir. API Arabirimi (örneğin, bir mikro ORM Dapper gibi) herhangi bir altyapı kullanarak ve dinamik ViewModels UI uygulamaları gereksinimlerine bağlı olarak döndüren Web API denetleyicilerinin tarafından uygulanır.

![](./media/image3.png)

**Şekil 9-3**. CQRS mikro hizmet sorguları için en kolay yaklaşım

Bu mod sorguları için en basit olası yaklaşımdır. Sorgu tanımları veritabanını sorgulamak ve her sorgu için kolay bir şekilde yerleşik dinamik bir ViewModel döndürür. Sorguları ıdempotent olduğundan, bir sorgu çalıştırmadan kaç kez olsun verileri değiştirmez. Bu nedenle, işlem tarafındaki toplamalar ve diğer desenleri gibi kullanılan herhangi bir DDD modeliyle tarafından kısıtlanmış gerekmez ve sorguları işlem alanından ayrılmış neden. Yalnızca kullanıcı arabirimini gereken veriler için veritabanını sorgulamak ve statik olarak olması gerekmez dinamik bir ViewModel her yerden (sınıflar ViewModels için) dışındaki SQL deyimlerini kendilerini tanımlanan döndürür.

Bu basit bir yaklaşım olduğuna göre sorguları tarafı için gerekli kod (ORM gibi bir mikro kullanarak kod gibi [Dapper](https://github.com/StackExchange/Dapper)) uygulanabilir [aynı Web API projesi içinde](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs). Şekil 9-4 bu gösterir. Sorguları tanımlanan **Ordering.API** eShopOnContainers çözümünde mikro hizmet projesi.

![](./media/image4.png)

**Şekil 9-4**. Sıralama mikro hizmet eShopOnContainers içinde sorguları

## <a name="using-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a>İstemci uygulamaları, etki alanı modeli kısıtlamaları bağımsız için özellikle yapılan ViewModels kullanma

İstemci uygulamaları tarafından gereken verileri almak için sorgular gerçekleştirilen olduğundan, döndürülen tür özellikle sorguları tarafından döndürülen verileri temel alan istemciler için yapılabilir. Bu modeller ya da veri aktarım nesneleri (DTOs) ViewModels denir.

Döndürülen veriler (ViewModel) birden çok varlık veya tablo verileri veritabanında veya bile işlem alanı için etki alanı modelinde tanımlanan birden çok toplamalar arasında birleştirme sonucu olabilir. Bu durumda, sorguları etki alanı modeli bağımsız oluşturmakta olduğunuz çünkü toplamalar sınırları ve kısıtlamaları tamamen yoksayılır ve tüm tablo ve sütun gereksinim duyabileceğiniz sorgu boş. Bu yaklaşım, oluşturma veya güncelleştirme sorguları geliştiriciler için büyük esneklik ve verimlilik sağlar.

ViewModels sınıflarda tanımlanan statik türler olabilir. Ya da yöneticiler geliştiricileri için çok Çevik olduğu (sıralama mikro hizmet içinde uygulanan gibi) gerçekleştirilecek sorgularına göre dinamik olarak oluşturulabilir.

## <a name="using-dapper-as-a-micro-orm-to-perform-queries"></a>Sorguları gerçekleştirmek için Dapper mikro ORM kullanma 

Tüm mikro ORM, Entity Framework Çekirdek ya da bile düz ADO.NET sorgulamak için kullanabilirsiniz. Örnek uygulama için popüler bir mikro ORM iyi bir örnek olarak eShopOnContainers içinde sıralama mikro Dapper seçili. Çok açık bir çerçeve olduğu için harika performans ile düz SQL sorguları çalıştırabilirsiniz. Dapper kullanarak, erişebilir ve birden çok tabloyu birleştirme bir SQL sorgu yazabilirsiniz.

Dapper açık kaynaklı proje (Sam Saffron tarafından oluşturulan özgün) ve kullanılan yapı taşları parçası [yığın taşması](https://stackoverflow.com/). Dapper kullanmak için aracılığıyla yüklemeniz yeterlidir [Dapper NuGet paketi](https://www.nuget.org/packages/Dapper), aşağıdaki çizimde gösterildiği gibi.

![](./media/image5.png)

Ayrıca kullanarak bir eklemeniz gerekir, kodunuzu Dapper genişletme yöntemleri erişimi şekilde deyimi.

Kodunuzda Dapper kullandığınızda, doğrudan System.Data.SqlClient ad alanında kullanılabilir SqlClient sınıfı kullanın. QueryAsync yöntemi ve SqlClient sınıfını genişleten diğer genişletme yöntemleri aracılığıyla, sorguları yalnızca basit ve kullanıcı şekilde çalıştırabilirsiniz.

## <a name="dynamic-and-static-viewmodels"></a>Dinamik ve statik ViewModels

Aşağıdaki kodu sıralama mikro hizmet ile gösterildiği gibi sorguları tarafından döndürülen ViewModels çoğunu olarak uygulanan *dinamik*. Döndürülecek öznitelik alt sorguyu temel alan anlamına gelir. Birleştirme ve sorgu için yeni bir sütun eklerseniz, bu verileri döndürülen ViewModel dinamik olarak eklenir. Bu yaklaşım, bu tasarım yaklaşımı daha esnek ve gelecekteki değişiklikler dayanıklı hale veri modeli, güncelleştirmelerinin yanıta sorgularda değiştirmek için gereksinimini azaltır.

```csharp
using Dapper;
using Microsoft.Extensions.Configuration;
using System.Data.SqlClient;
using System.Threading.Tasks;
using System.Dynamic;
using System.Collections.Generic;

public class OrderQueries : IOrderQueries
{
    public async Task<IEnumerable<dynamic>> GetOrdersAsync()
    {
        using (var connection = new SqlConnection(_connectionString))
        {
            connection.Open();
            return await connection.QueryAsync<dynamic>(
@"SELECT o.[Id] as ordernumber,
o.[OrderDate] as [date],os.[Name] as [status],
SUM(oi.units*oi.unitprice) as total
FROM [ordering].[Orders] o
LEFT JOIN[ordering].[orderitems] oi ON o.Id = oi.orderid
LEFT JOIN[ordering].[orderstatus] os on o.OrderStatusId = os.Id
GROUP BY o.[Id], o.[OrderDate], os.[Name]");
        }
  }
}
```

Dinamik tür kullanarak, döndürülen verilerin toplanmasını dinamik olarak ViewModel birleştirilen, önemli noktasıdır.

Sorguların çoğu için kolay ve verimli hale getirir bunları kodlama bir DTO veya ViewModel sınıfı önceden gerekmez. Ancak, sözleşmeleri olarak daha kısıtlı bir tanımıyla ViewModels sahip olmak istiyorsanız (örneğin, önceden tanımlanmış DTOs) ViewModels önceden belirleyebilirsiniz.

#### <a name="additional-resources"></a>Ek kaynaklar

-   **Dapper**
    [*https://github.com/StackExchange/dapper-dot-net*](https://github.com/StackExchange/dapper-dot-net)

-   **Julie Lerman. Veri noktaları - Dapper, Entity Framework ve karma uygulamalar (MSDN Mag. makalesi)**

    *https://msdn.microsoft.com/en-us/Magazine/mt703432.aspx*


>[!div class="step-by-step"]
[Önceki] (eshoponcontainers-cqrs-bbb-microservice.md) [sonraki] (bbb-yönelimli-microservice.md)
