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
ms.openlocfilehash: 8ae4b4b9938f72f4f4fc011e180cd69440ec3dd9
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201752"
---
# <a name="querying-the-data-service-wcf-data-services"></a>Veri hizmetini sorgulama (WCF Veri Hizmetleri)

WCF Veri Hizmetleri istemci kitaplığı, dil ile tümleşik sorgu (LINQ) ile birlikte tanıdık .NET Framework programlama düzenlerini kullanarak bir veri hizmetine karşı sorgu yürütmenize olanak sağlar. İstemci kitaplığı, istemcide bir <xref:System.Data.Services.Client.DataServiceQuery%601> http get isteği iletisine bir sınıf örneği olarak tanımlanan bir sorguyu çevirir. Kitaplık, yanıt iletisini alır ve bunu istemci veri hizmeti sınıfları örneklerine dönüştürür. Bu sınıflar, <xref:System.Data.Services.Client.DataServiceContext> ait olduğu öğesine göre izlenir <xref:System.Data.Services.Client.DataServiceQuery%601> .

## <a name="data-service-queries"></a>Veri hizmeti sorguları

<xref:System.Data.Services.Client.DataServiceQuery%601>Genel sınıf, sıfır veya daha fazla varlık türü örneklerinin bir koleksiyonunu döndüren bir sorguyu temsil eder. Veri hizmeti sorgusu her zaman mevcut bir veri hizmeti bağlamına aittir. Bu bağlam, sorguyu oluşturmak ve yürütmek için gereken hizmet URI 'sini ve meta veri bilgilerini korur.

Bir veri hizmetini .NET Framework tabanlı bir istemci uygulamasına eklemek için **hizmet başvurusu Ekle** iletişim kutusunu kullandığınızda, sınıfından devralan bir varlık kapsayıcı sınıfı oluşturulur <xref:System.Data.Services.Client.DataServiceContext> . Bu sınıf, yazılı örnekleri döndüren özellikleri içerir <xref:System.Data.Services.Client.DataServiceQuery%601> . Veri hizmetinin sunduğu her bir varlık kümesi için bir özellik vardır. Bu özellikler, türü belirlenmiş bir örneğini oluşturmayı kolaylaştırır <xref:System.Data.Services.Client.DataServiceQuery%601> .

Aşağıdaki senaryolarda bir sorgu yürütülür:

- Sonuçlar örtük olarak numaralandırıldıktan sonra:

  - İçindeki bir özelliği <xref:System.Data.Services.Client.DataServiceContext> ve varlık kümesini temsil edildiğinde (örneğin, bir `foreach` (C#) veya `For Each` (Visual Basic) döngüsü).

  - Sorgu bir `List` koleksiyona atandığında.

- Ya da <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> yöntemi açıkça çağrıldığında.

- Ya da gibi bir LINQ sorgu yürütme işleci olduğunda <xref:System.Linq.Enumerable.First%2A> <xref:System.Linq.Enumerable.Single%2A> .

Aşağıdaki sorgu yürütüldüğünde, `Customers` Northwind Data Service 'teki tüm varlıkları döndürür:

[!code-csharp[Astoria Northwind Client#GetAllCustomersSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getallcustomersspecific)]
[!code-vb[Astoria Northwind Client#GetAllCustomersSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getallcustomersspecific)]

Daha fazla bilgi için bkz. [nasıl yapılır: veri hizmeti sorgularını yürütme](how-to-execute-data-service-queries-wcf-data-services.md).

WCF Veri Hizmetleri istemcisi, C# dilinde *dinamik* tür kullandığınızda olduğu gibi, geç bağlantılı nesneler için sorguları destekler. Ancak, performans nedenleriyle, veri hizmetine yönelik kesin olarak belirlenmiş sorguları her zaman oluşturmanız gerekir. <xref:System.Tuple>Tür ve dinamik nesneler istemci tarafından desteklenmez.

## <a name="linq-queries"></a>LINQ Sorguları

<xref:System.Data.Services.Client.DataServiceQuery%601>Sınıfı <xref:System.Linq.IQueryable%601> LINQ tarafından tanımlanan arabirimi uyguladığından WCF veri Hizmetleri istemci KITAPLıĞı, LINQ sorgularını varlık kümesi verilerine karşı veri hizmeti kaynağına göre değerlendirilen bir sorgu ifadesini temsil eden bir URI 'ye dönüştürebiliyor. Aşağıdaki örnek, <xref:System.Data.Services.Client.DataServiceQuery%601> `Orders` $30 'den daha fazla nakliye maliyeti olan ve sonuçları navlun maliyetine göre sipariş eden geri dönüşe denk olan bir LINQ sorgusudur.

[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqspecific)]
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqspecific)]

Bu LINQ sorgusu, Northwind tabanlı [hızlı başlangıç](quickstart-wcf-data-services.md) veri hizmeti 'ne karşı yürütülen AŞAĞıDAKI sorgu URI 'sine çevrilir:

```http
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30
```

> [!NOTE]
> LINQ sözdiziminde ifade edilen sorgu kümesi, veri Hizmetleri tarafından kullanılan temsili durum aktarımı (REST) tabanlı URI sözdiziminde etkinleştirilenlerden daha yavaştır. <xref:System.NotSupportedException>Sorgu, hedef veri hizmetindeki BIR URI ile eşleştirilemez olduğunda tetiklenir.

Daha fazla bilgi için bkz. [LINQ hususları](linq-considerations-wcf-data-services.md).

## <a name="adding-query-options"></a>Sorgu seçenekleri ekleme

Veri hizmeti sorguları, WCF veri Servicess 'in sağladığı tüm sorgu seçeneklerini destekler. <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A>Sorgu seçeneklerini bir örneğe eklemek için yöntemini çağırın <xref:System.Data.Services.Client.DataServiceQuery%601> . <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A><xref:System.Data.Services.Client.DataServiceQuery%601>özgün sorguya eşit olan, ancak yeni sorgu seçeneği ayarlanmış yeni bir örnek döndürür. Aşağıdaki sorgu yürütüldüğünde, `Orders` değere göre filtrelenen `Freight` ve `OrderID` azalan düzende sıralanan döndürür:

[!code-csharp[Astoria Northwind Client#AddQueryOptionsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionsspecific)]
[!code-vb[Astoria Northwind Client#AddQueryOptionsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionsspecific)]

`$orderby`Sorgu seçeneğini, döndürülen `Orders` nesneleri, özelliğin değerine göre filtreleyen ve sipariş eden aşağıdaki örnekte olduğu gibi tek bir özelliğe göre sıralamak ve filtrelemek için kullanabilirsiniz `Freight` :

[!code-csharp[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#orderwithfilter)]
[!code-vb[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#orderwithfilter)]

<xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A>Karmaşık sorgu ifadeleri oluşturmak için yöntemi arka arkaya çağırabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: veri hizmeti sorgusuna sorgu seçenekleri ekleme](how-to-add-query-options-to-a-data-service-query-wcf-data-services.md).

Sorgu seçenekleri bir LINQ sorgusunun sözdizimsel bileşenlerini ifade etmek için size başka bir yol sağlar. Daha fazla bilgi için bkz. [LINQ hususları](linq-considerations-wcf-data-services.md).

> [!NOTE]
> `$select`Sorgu seçeneği, yöntemi kullanılarak sorgu URI 'sine eklenemez <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> . <xref:System.Linq.Enumerable.Select%2A>İstemcinin `$select` istek URI 'sinde sorgu seçeneğini OLUŞTURMASı için LINQ metodunu kullanmanızı öneririz.

<a name="executingQueries"></a>

## <a name="client-versus-server-execution"></a>İstemci sunucu yürütmeye karşı

İstemci iki bölümden bir sorgu yürütür. Mümkün olduğunda, bir sorgudaki ifadeler öncelikle istemcide değerlendirilir ve ardından, bir URI tabanlı sorgu oluşturulup hizmette verilere göre değerlendirme için veri hizmetine gönderilir. Aşağıdaki LINQ sorgusunu göz önünde bulundurun:

[!code-csharp[Astoria Northwind Client#LinqQueryClientEvalSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqqueryclientevalspecific)]
[!code-vb[Astoria Northwind Client#LinqQueryClientEvalSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqqueryclientevalspecific)]

Bu örnekte, ifadesi `(basePrice – (basePrice * discount))` istemcisinde değerlendirilir. Bu nedenle, veri hizmetine gönderilen gerçek sorgu URI 'SI, `http://localhost:12345/northwind.svc/Products()?$filter=(UnitPrice gt 90.00M) and substringof('bike',ProductName)` filtre yan tümcesinde zaten hesaplanmış olan ondalık değerini içerir `90` . Filtre ifadesinin alt dize ifadesi de dahil diğer bölümleri veri hizmeti tarafından değerlendirilir. İstemci üzerinde değerlendirilen ifadeler ortak dil çalışma zamanı (CLR) semantiğini izler, veri hizmetine gönderilen ifadeler OData protokolünün veri hizmeti uygulamasını kullanır. Ayrıca, her iki istemci ve hizmet farklı saat dilimlerinde zamana dayalı değerlendirmeler gerçekleştirmede olduğu gibi, bu ayrı değerlendirmenin beklenmedik sonuçlara neden olabileceği senaryolara dikkat etmeniz gerekir.

## <a name="query-responses"></a>Sorgu yanıtları

Yürütüldüğünde, <xref:System.Data.Services.Client.DataServiceQuery%601> <xref:System.Collections.Generic.IEnumerable%601> İstenen varlık türünün bir örneğini döndürür. Bu sorgu sonucu <xref:System.Data.Services.Client.QueryOperationResponse%601> , aşağıdaki örnekte olduğu gibi bir nesneye alınabilir:

[!code-csharp[Astoria Northwind Client#GetResponseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getresponsespecific)]
[!code-vb[Astoria Northwind Client#GetResponseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getresponsespecific)]

Veri hizmetindeki varlıkları temsil eden varlık türü örnekleri, istemci üzerinde nesne materialization adlı bir işlem tarafından oluşturulur. Daha fazla bilgi için bkz. [nesne materialization](object-materialization-wcf-data-services.md). <xref:System.Data.Services.Client.QueryOperationResponse%601>Nesnesi, <xref:System.Collections.Generic.IEnumerable%601> sorgunun sonuçlarına erişim sağlamak için uygular.

<xref:System.Data.Services.Client.QueryOperationResponse%601>Ayrıca, bir sorgu sonucuyla ilgili ek bilgilere erişmenizi sağlayan aşağıdaki üyelere sahiptir:

- <xref:System.Data.Services.Client.OperationResponse.Error%2A>-varsa, işlem tarafından oluşturulan bir hata alır.

- <xref:System.Data.Services.Client.OperationResponse.Headers%2A>-sorgu yanıtıyla ilişkili HTTP yanıt üst bilgileri koleksiyonunu içerir.

- <xref:System.Data.Services.Client.QueryOperationResponse.Query%2A>-tarafından oluşturulan orijinali alır <xref:System.Data.Services.Client.DataServiceQuery%601> <xref:System.Data.Services.Client.QueryOperationResponse%601> .

- <xref:System.Data.Services.Client.OperationResponse.StatusCode%2A>-sorgu yanıtının HTTP yanıt kodunu alır.

- <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A>-Yöntem üzerinde çağrıldığında varlık kümesindeki toplam varlık sayısını alır <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> <xref:System.Data.Services.Client.DataServiceQuery%601> .

- <xref:System.Data.Services.Client.QueryOperationResponse.GetContinuation%2A>-bir <xref:System.Data.Services.Client.DataServiceQueryContinuation> sonraki sonuç SAYFASıNıN URI 'sini içeren bir nesne döndürür.

Varsayılan olarak, WCF Veri Hizmetleri yalnızca sorgu URI 'SI tarafından açıkça seçilen verileri döndürür. Bu, gerektiğinde veri hizmetinden ek verileri açıkça yükleme seçeneği sunar. Veri hizmetinden verileri her açık şekilde yüklediğinizde veri hizmetine bir istek gönderilir. Açık şekilde yüklenebilen veriler ilgili varlıkları, disk belleğine alınan yanıt verilerini ve ikili veri akışlarını içerir.

> [!NOTE]
> Bir veri hizmeti disk belleğine alınmış bir yanıt döndürebileceğinden, uygulamanızın disk belleğine alınmış bir veri hizmeti yanıtını işlemek için programlama modelini kullanmasını öneririz. Daha fazla bilgi için bkz. [ertelenmiş Içerik yükleme](loading-deferred-content-wcf-data-services.md).

Bir sorgu tarafından döndürülen veri miktarı, bir varlığın yalnızca belirli özelliklerinin yanıt olarak döndürüleceğini belirtilerek de azaltılabilir. Daha fazla bilgi için bkz. [sorgu tahminleri](query-projections-wcf-data-services.md).

## <a name="getting-a-count-of-the-total-number-of-entities-in-the-set"></a>Küme içindeki toplam varlık sayısının sayısını alma

Bazı senaryolarda, yalnızca sorgu tarafından döndürülen sayıyı değil, bir varlık kümesindeki toplam varlık sayısını bilmek yararlıdır. <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> <xref:System.Data.Services.Client.DataServiceQuery%601> Kümesindeki bu toplam varlık sayısının sorgu sonucuna dahil edilmesini istemek için öğesinde yöntemini çağırın. Bu durumda, <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> döndürülen öğesinin özelliği, <xref:System.Data.Services.Client.QueryOperationResponse%601> küme içindeki toplam varlık sayısını döndürür.

Ayrıca <xref:System.Int32> <xref:System.Int64> , <xref:System.Linq.Enumerable.Count%2A> sırasıyla veya yöntemlerini çağırarak, küme içindeki varlıkların toplam sayısını ya da değeri olarak da alabilirsiniz <xref:System.Linq.Enumerable.LongCount%2A> . Bu Yöntemler çağrıldığında, bir <xref:System.Data.Services.Client.QueryOperationResponse%601> döndürülmez; yalnızca Count değeri döndürülür. Daha fazla bilgi için bkz. [nasıl yapılır: bir sorgu tarafından döndürülen varlıkların sayısını belirleme](number-of-entities-returned-by-a-query-wcf.md).

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
