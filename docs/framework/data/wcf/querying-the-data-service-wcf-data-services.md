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
ms.openlocfilehash: e37a1654bdc62937bbb27c293a110293c9928645
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975162"
---
# <a name="querying-the-data-service-wcf-data-services"></a>Veri hizmetini sorgulama (WCF Veri Hizmetleri)

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemci kitaplığı, dil ile tümleşik sorgu (LINQ) ile birlikte tanıdık .NET Framework programlama düzenlerini kullanarak bir veri hizmetine karşı sorgu yürütmenize olanak sağlar. İstemci kitaplığı, istemcide bir HTTP GET isteği iletisine <xref:System.Data.Services.Client.DataServiceQuery%601> sınıfının bir örneği olarak tanımlanan bir sorguyu çevirir. Kitaplık, yanıt iletisini alır ve bunu istemci veri hizmeti sınıfları örneklerine dönüştürür. Bu sınıflar, <xref:System.Data.Services.Client.DataServiceQuery%601> ait olduğu <xref:System.Data.Services.Client.DataServiceContext> izlenir.

## <a name="data-service-queries"></a>Veri hizmeti sorguları

<xref:System.Data.Services.Client.DataServiceQuery%601> genel sınıfı, sıfır veya daha fazla varlık türü örneği koleksiyonunu döndüren bir sorguyu temsil eder. Veri hizmeti sorgusu her zaman mevcut bir veri hizmeti bağlamına aittir. Bu bağlam, sorguyu oluşturmak ve yürütmek için gereken hizmet URI 'sini ve meta veri bilgilerini korur.

Bir veri hizmetini .NET Framework tabanlı bir istemci uygulamasına eklemek için **hizmet başvurusu Ekle** iletişim kutusunu kullandığınızda, <xref:System.Data.Services.Client.DataServiceContext> sınıfından devralan bir varlık kapsayıcı sınıfı oluşturulur. Bu sınıf, yazılan <xref:System.Data.Services.Client.DataServiceQuery%601> örnekleri döndüren özellikleri içerir. Veri hizmetinin sunduğu her bir varlık kümesi için bir özellik vardır. Bu özellikler, türü belirlenmiş bir <xref:System.Data.Services.Client.DataServiceQuery%601>örneğini oluşturmayı kolaylaştırır.

Aşağıdaki senaryolarda bir sorgu yürütülür:

- Sonuçlar örtük olarak numaralandırıldıktan sonra:

  - <xref:System.Data.Services.Client.DataServiceContext> bir özellik, ve varlık kümesini temsil eden bir `foreach` (C#) veya `For Each` (Visual Basic) döngüsü sırasında numaralandırılır.

  - Sorgu bir `List` koleksiyonuna atandığında.

- <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> veya <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> yöntemi açıkça çağrıldığında.

- <xref:System.Linq.Enumerable.First%2A> veya <xref:System.Linq.Enumerable.Single%2A> gibi bir LINQ sorgu yürütme işleci çağrıldığında.

Aşağıdaki sorgu yürütüldüğünde, Northwind Data Service 'teki tüm `Customers` varlıkları döndürür:

[!code-csharp[Astoria Northwind Client#GetAllCustomersSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getallcustomersspecific)]
[!code-vb[Astoria Northwind Client#GetAllCustomersSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getallcustomersspecific)]

Daha fazla bilgi için bkz. [nasıl yapılır: veri hizmeti sorgularını yürütme](how-to-execute-data-service-queries-wcf-data-services.md).

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemcisi, içindeki C# *dinamik* türü kullanırken olduğu gibi, geç bağlantılı nesneler için sorguları destekler. Bununla birlikte, performans nedenleriyle, veri hizmetine yönelik kesin olarak belirlenmiş sorguları her zaman oluşturmanız gerekir. <xref:System.Tuple> türü ve dinamik nesneler istemci tarafından desteklenmez.

## <a name="linq-queries"></a>LINQ Sorguları

<xref:System.Data.Services.Client.DataServiceQuery%601> sınıfı LINQ tarafından tanımlanan <xref:System.Linq.IQueryable%601> arabirimini gerçekleştirdiğinden [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemci kitaplığı, LINQ sorgularını, bir veri hizmeti kaynağına göre değerlendirilen bir sorgu ifadesini temsil eden bir URI 'ye yönelik varlık kümesi verilerine dönüştürebilir. Aşağıdaki örnek, $30 'den daha büyük bir navlun maliyetine sahip `Orders` döndüren ve sonuçları navlun maliyetine göre sipariş eden bir önceki <xref:System.Data.Services.Client.DataServiceQuery%601> eşdeğer bir LINQ sorgusudur:

[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqspecific)]
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqspecific)]

Bu LINQ sorgusu, Northwind tabanlı [hızlı başlangıç](quickstart-wcf-data-services.md) veri hizmeti 'ne karşı yürütülen AŞAĞıDAKI sorgu URI 'sine çevrilir:

```http
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30
```

> [!NOTE]
> LINQ sözdiziminde ifade edilen sorgu kümesi, veri Hizmetleri tarafından kullanılan temsili durum aktarımı (REST) tabanlı URI sözdiziminde etkinleştirilenlerden daha yavaştır. Sorgu hedef veri hizmetindeki bir URI ile eşleştirilemez bir <xref:System.NotSupportedException> tetiklenir.

Daha fazla bilgi için bkz. [LINQ hususları](linq-considerations-wcf-data-services.md).

## <a name="adding-query-options"></a>Sorgu seçenekleri ekleme

Veri hizmeti sorguları, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]tarafından sağlanan tüm sorgu seçeneklerini destekler. Sorgu seçeneklerini bir <xref:System.Data.Services.Client.DataServiceQuery%601> örneğine eklemek için <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> yöntemini çağırın. <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A>, özgün sorguya eşit olan ancak yeni sorgu seçeneği ayarlanmış yeni bir <xref:System.Data.Services.Client.DataServiceQuery%601> örneği döndürür. Aşağıdaki sorgu yürütüldüğünde, `Freight` değerine göre filtrelenen ve `OrderID`tarafından sıralanan `Orders` döndürür:

[!code-csharp[Astoria Northwind Client#AddQueryOptionsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionsspecific)]
[!code-vb[Astoria Northwind Client#AddQueryOptionsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionsspecific)]

Aşağıdaki örnekte, `Freight` özelliğinin değerine göre döndürülen `Orders` nesnelerini filtreleyen ve sipariş eden aşağıdaki örnekte olduğu gibi, bir sorguyu tek bir özelliğe göre sıralamak ve filtrelemek için `$orderby` sorgu seçeneğini kullanabilirsiniz:

[!code-csharp[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#orderwithfilter)]
[!code-vb[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#orderwithfilter)]

Karmaşık sorgu ifadeleri oluşturmak için <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> yöntemini arka arkaya çağırabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: veri hizmeti sorgusuna sorgu seçenekleri ekleme](how-to-add-query-options-to-a-data-service-query-wcf-data-services.md).

Sorgu seçenekleri bir LINQ sorgusunun sözdizimsel bileşenlerini ifade etmek için size başka bir yol sağlar. Daha fazla bilgi için bkz. [LINQ hususları](linq-considerations-wcf-data-services.md).

> [!NOTE]
> `$select` sorgu seçeneği, <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> yöntemi kullanılarak sorgu URI 'sine eklenemez. İstemcinin istek URI 'sinde `$select` sorgu seçeneğini oluşturması için LINQ <xref:System.Linq.Enumerable.Select%2A> yöntemini kullanmanızı öneririz.

<a name="executingQueries"></a>

## <a name="client-versus-server-execution"></a>İstemci sunucu yürütmeye karşı

İstemci iki bölümden bir sorgu yürütür. Mümkün olduğunda, bir sorgudaki ifadeler öncelikle istemcide değerlendirilir ve ardından, bir URI tabanlı sorgu oluşturulup hizmette verilere göre değerlendirme için veri hizmetine gönderilir. Aşağıdaki LINQ sorgusunu göz önünde bulundurun:

[!code-csharp[Astoria Northwind Client#LinqQueryClientEvalSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqqueryclientevalspecific)]
[!code-vb[Astoria Northwind Client#LinqQueryClientEvalSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqqueryclientevalspecific)]

Bu örnekte, `(basePrice – (basePrice * discount))` ifade istemci üzerinde değerlendirilir. Bu nedenle, veri hizmetine gönderilen gerçek sorgu URI 'SI `http://localhost:12345/northwind.svc/Products()?$filter=(UnitPrice gt 90.00M) and substringof('bike',ProductName)`, filtre yan tümcesindeki `90` zaten hesaplanmış ondalık değerini içerir. Filtre ifadesinin alt dize ifadesi de dahil diğer bölümleri veri hizmeti tarafından değerlendirilir. İstemci üzerinde değerlendirilen ifadeler ortak dil çalışma zamanı (CLR) semantiğini izler, veri hizmetine gönderilen ifadeler OData protokolünün veri hizmeti uygulamasını kullanır. Ayrıca, her iki istemci ve hizmet farklı saat dilimlerinde zamana dayalı değerlendirmeler gerçekleştirmede olduğu gibi, bu ayrı değerlendirmenin beklenmedik sonuçlara neden olabileceği senaryolara dikkat etmeniz gerekir.

## <a name="query-responses"></a>Sorgu yanıtları

Yürütüldüğünde, <xref:System.Data.Services.Client.DataServiceQuery%601> istenen varlık türünün bir <xref:System.Collections.Generic.IEnumerable%601> döndürür. Bu sorgu sonucu, aşağıdaki örnekte olduğu gibi <xref:System.Data.Services.Client.QueryOperationResponse%601> nesnesine dönüşebilir:

[!code-csharp[Astoria Northwind Client#GetResponseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getresponsespecific)]
[!code-vb[Astoria Northwind Client#GetResponseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getresponsespecific)]

Veri hizmetindeki varlıkları temsil eden varlık türü örnekleri, istemci üzerinde nesne materialization adlı bir işlem tarafından oluşturulur. Daha fazla bilgi için bkz. [nesne materialization](object-materialization-wcf-data-services.md). <xref:System.Data.Services.Client.QueryOperationResponse%601> nesnesi sorgunun sonuçlarına erişim sağlamak için <xref:System.Collections.Generic.IEnumerable%601> uygular.

<xref:System.Data.Services.Client.QueryOperationResponse%601> Ayrıca, bir sorgu sonucuyla ilgili ek bilgilere erişmenizi sağlayan aşağıdaki üyelere sahiptir:

- <xref:System.Data.Services.Client.OperationResponse.Error%2A>-varsa, işlem tarafından oluşan bir hata alır.

- <xref:System.Data.Services.Client.OperationResponse.Headers%2A>-sorgu yanıtıyla ilişkili HTTP yanıt üst bilgileri koleksiyonunu içerir.

- <xref:System.Data.Services.Client.QueryOperationResponse.Query%2A>-<xref:System.Data.Services.Client.QueryOperationResponse%601>oluşturan özgün <xref:System.Data.Services.Client.DataServiceQuery%601> alır.

- <xref:System.Data.Services.Client.OperationResponse.StatusCode%2A>-sorgu yanıtının HTTP yanıt kodunu alır.

- <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A>-<xref:System.Data.Services.Client.DataServiceQuery%601><xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> yöntemi çağrıldığında varlık kümesindeki toplam varlık sayısını alır.

- <xref:System.Data.Services.Client.QueryOperationResponse.GetContinuation%2A>-bir sonraki sonuç sayfasının URI 'sini içeren bir <xref:System.Data.Services.Client.DataServiceQueryContinuation> nesnesi döndürür.

Varsayılan olarak, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] yalnızca sorgu URI 'SI tarafından açıkça seçilen verileri döndürür. Bu, gerektiğinde veri hizmetinden ek verileri açıkça yükleme seçeneği sunar. Veri hizmetinden verileri her açık şekilde yüklediğinizde veri hizmetine bir istek gönderilir. Açık şekilde yüklenebilen veriler ilgili varlıkları, disk belleğine alınan yanıt verilerini ve ikili veri akışlarını içerir.

> [!NOTE]
> Bir veri hizmeti disk belleğine alınmış bir yanıt döndürebileceğinden, uygulamanızın disk belleğine alınmış bir veri hizmeti yanıtını işlemek için programlama modelini kullanmasını öneririz. Daha fazla bilgi için bkz. [ertelenmiş Içerik yükleme](loading-deferred-content-wcf-data-services.md).

Bir sorgu tarafından döndürülen veri miktarı, bir varlığın yalnızca belirli özelliklerinin yanıt olarak döndürüleceğini belirtilerek de azaltılabilir. Daha fazla bilgi için bkz. [sorgu tahminleri](query-projections-wcf-data-services.md).

## <a name="getting-a-count-of-the-total-number-of-entities-in-the-set"></a>Küme içindeki toplam varlık sayısının sayısını alma

Bazı senaryolarda, yalnızca sorgu tarafından döndürülen sayıyı değil, bir varlık kümesindeki toplam varlık sayısını bilmek yararlıdır. Küme içindeki bu toplam varlık sayısının sorgu sonucuyla birlikte dahil edilmesini istemek için <xref:System.Data.Services.Client.DataServiceQuery%601> <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> yöntemi çağırın. Bu durumda, döndürülen <xref:System.Data.Services.Client.QueryOperationResponse%601> <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> özelliği, kümesindeki toplam varlık sayısını döndürür.

Ayrıca, sırasıyla <xref:System.Linq.Enumerable.Count%2A> veya <xref:System.Linq.Enumerable.LongCount%2A> yöntemlerini çağırarak, küme içindeki varlıkların toplam sayısını bir <xref:System.Int32> veya <xref:System.Int64> değeri olarak da alabilirsiniz. Bu Yöntemler çağrıldığında <xref:System.Data.Services.Client.QueryOperationResponse%601> döndürülmez; yalnızca Count değeri döndürülür. Daha fazla bilgi için bkz. [nasıl yapılır: bir sorgu tarafından döndürülen varlıkların sayısını belirleme](number-of-entities-returned-by-a-query-wcf.md).

## <a name="in-this-section"></a>Bu Bölümde

- [Sorgu Projeksiyonları](query-projections-wcf-data-services.md)

- [Nesne Gerçekleştirme](object-materialization-wcf-data-services.md)

- [LINQ Konuları](linq-considerations-wcf-data-services.md)

- [Nasıl yapılır: Veri Hizmeti Sorguları Yürütme](how-to-execute-data-service-queries-wcf-data-services.md)

- [Nasıl yapılır: Veri Hizmeti Sorgusuna Sorgu Seçenekleri Ekleme](how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)

- [Nasıl yapılır: Sorgu Tarafından Döndürülen Varlık Sayısını Belirleme](number-of-entities-returned-by-a-query-wcf.md)

- [Nasıl yapılır: Veri Hizmeti İsteği için İstemci Kimlik Bilgileri Belirtme](specify-client-creds-for-a-data-service-request-wcf.md)

- [Nasıl yapılır: İstemci İsteğinde Üst Bilgileri Ayarlama](how-to-set-headers-in-the-client-request-wcf-data-services.md)

- [Nasıl Yapılır: Sorgu Sonuçlarını Yansıtma](how-to-project-query-results-wcf-data-services.md)

## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
