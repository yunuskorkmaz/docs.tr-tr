---
title: Veri hizmetini sorgulama (WCF Veri Hizmetleri)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: 823e9444-27aa-4f1f-be8e-0486d67f54c0
ms.openlocfilehash: 50dc56a3c4c87bf9ac197b127c036c41ac833a88
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931131"
---
# <a name="querying-the-data-service-wcf-data-services"></a>Veri hizmetini sorgulama (WCF Veri Hizmetleri)

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] İstemci kitaplığı, dil ile tümleşik sorgu (LINQ) ile birlikte tanıdık .NET Framework programlama düzenlerini kullanarak bir veri hizmetine karşı sorgu yürütmenize olanak sağlar. İstemci kitaplığı, istemcide bir http get isteği iletisine bir <xref:System.Data.Services.Client.DataServiceQuery%601> sınıf örneği olarak tanımlanan bir sorguyu çevirir. Kitaplık, yanıt iletisini alır ve bunu istemci veri hizmeti sınıfları örneklerine dönüştürür. Bu sınıflar, <xref:System.Data.Services.Client.DataServiceContext> <xref:System.Data.Services.Client.DataServiceQuery%601> ait olduğu öğesine göre izlenir.

## <a name="data-service-queries"></a>Veri hizmeti sorguları

Genel <xref:System.Data.Services.Client.DataServiceQuery%601> sınıf, sıfır veya daha fazla varlık türü örneklerinin bir koleksiyonunu döndüren bir sorguyu temsil eder. Veri hizmeti sorgusu her zaman mevcut bir veri hizmeti bağlamına aittir. Bu bağlam, sorguyu oluşturmak ve yürütmek için gereken hizmet URI 'sini ve meta veri bilgilerini korur.

Bir veri hizmetini .NET Framework tabanlı bir istemci uygulamasına eklemek için **hizmet başvurusu Ekle** iletişim kutusunu kullandığınızda, <xref:System.Data.Services.Client.DataServiceContext> sınıfından devralan bir varlık kapsayıcı sınıfı oluşturulur. Bu sınıf, yazılı <xref:System.Data.Services.Client.DataServiceQuery%601> örnekleri döndüren özellikleri içerir. Veri hizmetinin sunduğu her bir varlık kümesi için bir özellik vardır. Bu özellikler, türü belirlenmiş <xref:System.Data.Services.Client.DataServiceQuery%601>bir örneğini oluşturmayı kolaylaştırır.

Aşağıdaki senaryolarda bir sorgu yürütülür:

- Sonuçlar örtük olarak numaralandırıldıktan sonra:

  - İçindeki bir özellik <xref:System.Data.Services.Client.DataServiceContext> ve varlık kümesi bir `foreach` (C#) veya `For Each` (Visual Basic) döngüsü sırasında numaralandırılır.

  - Sorgu bir `List` koleksiyona atandığında.

- <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> Ya<xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> da yöntemi açıkça çağrıldığında.

- <xref:System.Linq.Enumerable.First%2A> Ya<xref:System.Linq.Enumerable.Single%2A> da gibi bir LINQ sorgu yürütme işleci olduğunda.

Aşağıdaki sorgu yürütüldüğünde, Northwind Data Service 'teki tüm `Customers` varlıkları döndürür:

[!code-csharp[Astoria Northwind Client#GetAllCustomersSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getallcustomersspecific)]
[!code-vb[Astoria Northwind Client#GetAllCustomersSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getallcustomersspecific)]

Daha fazla bilgi için [nasıl yapılır: Veri hizmeti sorgularını](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)yürütün.

İstemci, içindeki C#dinamik türü kullanırken olduğu gibi, geç bağlantılı nesneler için sorguları destekler. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Bununla birlikte, performans nedenleriyle, veri hizmetine yönelik kesin olarak belirlenmiş sorguları her zaman oluşturmanız gerekir. <xref:System.Tuple> Tür ve dinamik nesneler istemci tarafından desteklenmez.

## <a name="linq-queries"></a>LINQ Sorguları

Sınıfı LINQ <xref:System.Linq.IQueryable%601> tarafından[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] tanımlanan arabirimi uyguladığından, istemci kitaplığı, LINQ sorgularını varlık kümesi verilerine karşı veri hizmetine göre değerlendirilen bir sorgu ifadesini temsil eden bir URI 'ye dönüştürebilir <xref:System.Data.Services.Client.DataServiceQuery%601> Kaynak. Aşağıdaki örnek, $30 'den daha fazla nakliye maliyeti olan ve sonuçları navlun <xref:System.Data.Services.Client.DataServiceQuery%601> maliyetine göre `Orders` sipariş eden geri dönüşe denk olan bir LINQ sorgusudur.

[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqspecific)]
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqspecific)]

Bu LINQ sorgusu, Northwind tabanlı [hızlı başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) veri hizmeti 'ne karşı yürütülen AŞAĞıDAKI sorgu URI 'sine çevrilir:

```
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30
```

> [!NOTE]
> LINQ sözdiziminde ifade edilen sorgu kümesi, veri Hizmetleri tarafından kullanılan temsili durum aktarımı (REST) tabanlı URI sözdiziminde etkinleştirilenlerden daha yavaştır. <xref:System.NotSupportedException> Sorgu, hedef veri hizmetindeki bir URI ile eşleştirilemez olduğunda tetiklenir.

Daha fazla bilgi için bkz. [LINQ hususları](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md).

## <a name="adding-query-options"></a>Sorgu seçenekleri ekleme

Veri hizmeti sorguları, s tarafından [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]sağlanan tüm sorgu seçeneklerini destekler. Sorgu seçeneklerini bir <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> <xref:System.Data.Services.Client.DataServiceQuery%601> örneğe eklemek için yöntemini çağırın. <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A>özgün sorguya eşit <xref:System.Data.Services.Client.DataServiceQuery%601> olan, ancak yeni sorgu seçeneği ayarlanmış yeni bir örnek döndürür. Aşağıdaki sorgu yürütüldüğünde, `Orders` `Freight` değere göre filtrelenen ve azalan düzende sıralanan döndürür:`OrderID`

[!code-csharp[Astoria Northwind Client#AddQueryOptionsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionsspecific)]
[!code-vb[Astoria Northwind Client#AddQueryOptionsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionsspecific)]

`$orderby` Sorgu seçeneğini, döndürülen `Orders` nesneleri, `Freight` özelliğin değerine göre filtreleyen ve sipariş eden aşağıdaki örnekte olduğu gibi tek bir özelliğe göre sıralamak ve filtrelemek için kullanabilirsiniz:

[!code-csharp[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#orderwithfilter)]
[!code-vb[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#orderwithfilter)]

Karmaşık sorgu ifadeleri oluşturmak <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> için yöntemi arka arkaya çağırabilirsiniz. Daha fazla bilgi için [nasıl yapılır: Bir veri hizmeti sorgusuna](../../../../docs/framework/data/wcf/how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)sorgu seçenekleri ekleyin.

Sorgu seçenekleri bir LINQ sorgusunun sözdizimsel bileşenlerini ifade etmek için size başka bir yol sağlar. Daha fazla bilgi için bkz. [LINQ hususları](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md).

> [!NOTE]
> Sorgu seçeneği, <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> yöntemi kullanılarak sorgu URI 'sine eklenemez. `$select` İstemcinin istek URI 'sinde <xref:System.Linq.Enumerable.Select%2A> `$select` sorgu seçeneğini oluşturması için LINQ metodunu kullanmanızı öneririz.

<a name="executingQueries"></a>

## <a name="client-versus-server-execution"></a>İstemci sunucu yürütmeye karşı

İstemci iki bölümden bir sorgu yürütür. Mümkün olduğunda, bir sorgudaki ifadeler öncelikle istemcide değerlendirilir ve ardından, bir URI tabanlı sorgu oluşturulup hizmette verilere göre değerlendirme için veri hizmetine gönderilir. Aşağıdaki LINQ sorgusunu göz önünde bulundurun:

[!code-csharp[Astoria Northwind Client#LinqQueryClientEvalSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqqueryclientevalspecific)]
[!code-vb[Astoria Northwind Client#LinqQueryClientEvalSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqqueryclientevalspecific)]

Bu örnekte, ifadesi `(basePrice – (basePrice * discount))` istemcisinde değerlendirilir. Bu nedenle, veri hizmetine gönderilen gerçek sorgu `http://localhost:12345/northwind.svc/Products()?$filter=(UnitPrice gt 90.00M) and substringof('bike',ProductName)` URI 'si, filtre yan tümcesinde zaten hesaplanmış olan `90` ondalık değerini içerir. Filtre ifadesinin alt dize ifadesi de dahil diğer bölümleri veri hizmeti tarafından değerlendirilir. İstemci üzerinde değerlendirilen ifadeler ortak dil çalışma zamanı (CLR) semantiğini izler, veri hizmetine gönderilen ifadeler [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokolün veri hizmeti uygulamasına bağlıdır. Ayrıca, her iki istemci ve hizmet farklı saat dilimlerinde zamana dayalı değerlendirmeler gerçekleştirmede olduğu gibi, bu ayrı değerlendirmenin beklenmedik sonuçlara neden olabileceği senaryolara dikkat etmeniz gerekir.

## <a name="query-responses"></a>Sorgu yanıtları

Yürütüldüğünde <xref:System.Data.Services.Client.DataServiceQuery%601> , istenen varlık türünün bir <xref:System.Collections.Generic.IEnumerable%601> örneğini döndürür. Bu sorgu sonucu, aşağıdaki örnekte olduğu gibi <xref:System.Data.Services.Client.QueryOperationResponse%601> bir nesneye alınabilir:

[!code-csharp[Astoria Northwind Client#GetResponseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getresponsespecific)]
[!code-vb[Astoria Northwind Client#GetResponseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getresponsespecific)]

Veri hizmetindeki varlıkları temsil eden varlık türü örnekleri, istemci üzerinde nesne materialization adlı bir işlem tarafından oluşturulur. Daha fazla bilgi için bkz. [nesne materialization](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md). Nesnesi, sorgunun sonuçlarına erişim sağlamak için uygular <xref:System.Collections.Generic.IEnumerable%601>. <xref:System.Data.Services.Client.QueryOperationResponse%601>

Ayrıca <xref:System.Data.Services.Client.QueryOperationResponse%601> , bir sorgu sonucuyla ilgili ek bilgilere erişmenizi sağlayan aşağıdaki üyelere sahiptir:

- <xref:System.Data.Services.Client.OperationResponse.Error%2A>-varsa, işlem tarafından oluşturulan bir hata alır.

- <xref:System.Data.Services.Client.OperationResponse.Headers%2A>-sorgu yanıtıyla ilişkili HTTP yanıt üst bilgileri koleksiyonunu içerir.

- <xref:System.Data.Services.Client.QueryOperationResponse.Query%2A>-tarafından <xref:System.Data.Services.Client.DataServiceQuery%601> <xref:System.Data.Services.Client.QueryOperationResponse%601>oluşturulan orijinali alır.

- <xref:System.Data.Services.Client.OperationResponse.StatusCode%2A>-sorgu yanıtının HTTP yanıt kodunu alır.

- <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A>- <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> Yöntem<xref:System.Data.Services.Client.DataServiceQuery%601>üzerinde çağrıldığında varlık kümesindeki toplam varlık sayısını alır.

- <xref:System.Data.Services.Client.QueryOperationResponse.GetContinuation%2A>-bir sonraki <xref:System.Data.Services.Client.DataServiceQueryContinuation> sonuç sayfasının URI 'sini içeren bir nesne döndürür.

Varsayılan olarak, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] yalnızca sorgu URI 'si tarafından açıkça seçilen verileri döndürür. Bu, gerektiğinde veri hizmetinden ek verileri açıkça yükleme seçeneği sunar. Veri hizmetinden verileri her açık şekilde yüklediğinizde veri hizmetine bir istek gönderilir. Açık şekilde yüklenebilen veriler ilgili varlıkları, disk belleğine alınan yanıt verilerini ve ikili veri akışlarını içerir.

> [!NOTE]
> Bir veri hizmeti disk belleğine alınmış bir yanıt döndürebileceğinden, uygulamanızın disk belleğine alınmış bir veri hizmeti yanıtını işlemek için programlama modelini kullanmasını öneririz. Daha fazla bilgi için bkz. [ertelenmiş Içerik yükleme](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).

Bir sorgu tarafından döndürülen veri miktarı, bir varlığın yalnızca belirli özelliklerinin yanıt olarak döndürüleceğini belirtilerek de azaltılabilir. Daha fazla bilgi için bkz. [sorgu tahminleri](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md).

## <a name="getting-a-count-of-the-total-number-of-entities-in-the-set"></a>Küme içindeki toplam varlık sayısının sayısını alma

Bazı senaryolarda, yalnızca sorgu tarafından döndürülen sayıyı değil, bir varlık kümesindeki toplam varlık sayısını bilmek yararlıdır. Kümesindeki bu toplam varlık sayısının <xref:System.Data.Services.Client.DataServiceQuery%601> sorgu sonucuna dahil edilmesini istemek için öğesinde yönteminiçağırın.<xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> Bu durumda, <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> döndürülen <xref:System.Data.Services.Client.QueryOperationResponse%601> öğesinin özelliği, küme içindeki toplam varlık sayısını döndürür.

Ayrıca, <xref:System.Int32> sırasıyla veya <xref:System.Linq.Enumerable.Count%2A> <xref:System.Int64> yöntemleriniçağırarak,kümeiçindekivarlıklarıntoplamsayısınıyadadeğeriolarakdaalabilirsiniz.<xref:System.Linq.Enumerable.LongCount%2A> Bu Yöntemler çağrıldığında, bir <xref:System.Data.Services.Client.QueryOperationResponse%601> döndürülmez; yalnızca Count değeri döndürülür. Daha fazla bilgi için [nasıl yapılır: Bir sorgu](../../../../docs/framework/data/wcf/number-of-entities-returned-by-a-query-wcf.md)tarafından döndürülen varlıkların sayısını belirleme.

## <a name="in-this-section"></a>Bu Bölümde

- [Sorgu Projeksiyonları](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)

- [Nesne Gerçekleştirme](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)

- [LINQ Konuları](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)

- [Nasıl yapılır: Veri hizmeti sorgularını yürütme](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)

- [Nasıl yapılır: Veri hizmeti sorgusuna sorgu seçenekleri ekleme](../../../../docs/framework/data/wcf/how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)

- [Nasıl yapılır: Bir sorgu tarafından döndürülen varlıkların sayısını belirleme](../../../../docs/framework/data/wcf/number-of-entities-returned-by-a-query-wcf.md)

- [Nasıl yapılır: Veri hizmeti Isteği için Istemci kimlik bilgilerini belirtin](../../../../docs/framework/data/wcf/specify-client-creds-for-a-data-service-request-wcf.md)

- [Nasıl yapılır: Istemci Isteğindeki üst bilgileri ayarla](../../../../docs/framework/data/wcf/how-to-set-headers-in-the-client-request-wcf-data-services.md)

- [Nasıl yapılır: Proje sorgu sonuçları](../../../../docs/framework/data/wcf/how-to-project-query-results-wcf-data-services.md)

## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
