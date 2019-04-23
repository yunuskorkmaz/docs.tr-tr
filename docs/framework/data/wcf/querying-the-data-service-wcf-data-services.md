---
title: Veri hizmetini (WCF Veri Hizmetleri) sorgulama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: 823e9444-27aa-4f1f-be8e-0486d67f54c0
ms.openlocfilehash: abae49e709fa2e77d641d991dd6e09cf82216732
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59517297"
---
# <a name="querying-the-data-service-wcf-data-services"></a>Veri hizmetini (WCF Veri Hizmetleri) sorgulama
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] İstemci kitaplığı sağlar, tanıdık karşı kullanarak bir veri hizmeti sorguları yürütmek [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] programlama desenleri, dil ile tümleşik sorgu (LINQ) kullanımı dahil olmak üzere. İstemci Kitaplığı istemcide bir örneği olarak tanımlanan bir sorgu çevirir <xref:System.Data.Services.Client.DataServiceQuery%601> sınıfına bir HTTP GET isteği iletisi. Kitaplığı yanıt iletisini alır ve istemci veri hizmeti sınıfları örneğine çevirir. Bu sınıflar tarafından izlenen <xref:System.Data.Services.Client.DataServiceContext> hangi <xref:System.Data.Services.Client.DataServiceQuery%601> ait.  
  
## <a name="data-service-queries"></a>Veri Hizmeti sorguları  
 <xref:System.Data.Services.Client.DataServiceQuery%601> Genel bir sınıf, sıfır veya daha fazla varlık türü örneklerinin bir koleksiyonunu döndüren bir sorgu temsil eder. Veri Hizmeti sorgusuna her zaman var olan bir veri hizmeti bağlamına ait. Bu bağlam oluşturma ve sorgu yürütmek için gerekli olan hizmet URI'si ve meta veri bilgilerini korur.  
  
 Kullanırken **hizmet Başvurusu Ekle** bir veri hizmetine eklemek için iletişim bir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]-tabanlı bir istemci uygulaması, bir varlık kapsayıcı sınıfı devralınan oluşturulur <xref:System.Data.Services.Client.DataServiceContext> sınıfı. Bu sınıf döndüren türü belirlenmiş özellikler içeren <xref:System.Data.Services.Client.DataServiceQuery%601> örnekleri. Verileri kullanıma sunan hizmet her varlık kümesi için bir özellik yoktur. Bu özellikler bir türü belirtilmiş bir örneğini oluşturmak kolaylaştırır <xref:System.Data.Services.Client.DataServiceQuery%601>.  
  
 Bir sorgu, aşağıdaki senaryolarda çalıştırılır:  
  
-   Sonuçları örtülü olarak numaralandırılır olduğunda gibi:  
  
    -   Bir özellikte olduğunda <xref:System.Data.Services.Client.DataServiceContext> temsil eden ve varlık kümesi numaralandırılan, gibi sırasında bir `foreach` (C#) veya `For Each` döngüsü (Visual Basic).  
  
    -   Ne zaman sorgu atandığı bir `List` koleksiyonu.  
  
-   Zaman <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> veya <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> yöntemi açıkça çağrılmaz.  
  
-   Ne zaman bir LINQ Sorgu yürütme işleci gibi <xref:System.Linq.Enumerable.First%2A> veya <xref:System.Linq.Enumerable.Single%2A> çağrılır.  
  
 Aşağıdaki sorgu yürütüldüğünde, tüm döndürür `Customers` Northwind verileri hizmeti varlıklarda:  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getallcustomersspecific)]  
 [!code-vb[Astoria Northwind Client#GetAllCustomersSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getallcustomersspecific)]  
  
 Daha fazla bilgi için [nasıl yapılır: Veri Hizmeti sorguları yürütme](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md).  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] İstemci kullandığınızda gibi geç bağlanan nesneler için sorguları destekleyen *dinamik* yazın C#. Ancak, performansla ilgili nedenlerden dolayı her zaman kesin türü belirtilmiş veri hizmeti sorguları oluşturmak. <xref:System.Tuple> Türü ve dinamik nesneler, istemci tarafından desteklenmez.  
  
## <a name="linq-queries"></a>LINQ Sorguları  
 Çünkü <xref:System.Data.Services.Client.DataServiceQuery%601> sınıfının Implements <xref:System.Linq.IQueryable%601> LINQ tarafından tanımlanan arabirimi [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] karşı bir veri hizmeti değerlendirilen bir sorgu ifadesini gösteren bir URI LINQ sorguları varlık kümesi verileri dönüştürmek için İstemci Kitaplığı Kaynak. Aşağıdaki örnek, önceki denk bir LINQ sorgusu <xref:System.Data.Services.Client.DataServiceQuery%601> döndüren `Orders` maliyet freight tarafından birden fazla 30 ABD Doları ve siparişler sonuçları freight maliyetini sahip:  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqspecific)]  
 [!code-vb[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqspecific)]  
  
 Aşağıdaki sorgu Northwind tabanlı karşı yürütülen URI bu LINQ sorgusu çevrilir [hızlı](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) veri hizmeti:  
  
```  
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30  
```  
  
> [!NOTE]
>  Sorgu LINQ söz diziminde ifade kümesi temsili durum aktarımı (REST) etkin daha geniştir-Veri Hizmetleri tarafından kullanılan URI'si söz dizimi bağlı. A <xref:System.NotSupportedException> hedef data Service'teki bir URI sorgu eşlenemediğinde ortaya çıkar.  
  
 Daha fazla bilgi için [LINQ konuları](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md).  
  
## <a name="adding-query-options"></a>Sorgu seçenekleri ekleme  
 Veri Hizmeti sorguları desteği tüm sorgu seçeneklerini [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]s sağlar. Çağırmanızı <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> sorgu seçeneklerini eklenecek yöntemi bir <xref:System.Data.Services.Client.DataServiceQuery%601> örneği. <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> Yeni bir <xref:System.Data.Services.Client.DataServiceQuery%601> özgün sorguya eşdeğer olan örneği ancak yeni bir sorgu ile bir seçenek kümesi. Aşağıdaki sorgu çalıştırıldığında, döndürür `Orders` göre filtrelenmiş `Freight` değeri ve göre sıralanmış `OrderID`, azalan:  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionsspecific)]  
 [!code-vb[Astoria Northwind Client#AddQueryOptionsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionsspecific)]  
  
 Kullanabileceğiniz `$orderby` döndürülen sıralar ve filtreler aşağıdaki örnekte olduğu gibi tek bir özelliğe dayalı bir sorguya filtre uygulamak ve sorgu seçeneği için hem `Orders` nesneleri değerini temel alarak `Freight` özelliği:  
  
 [!code-csharp[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#orderwithfilter)]
 [!code-vb[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#orderwithfilter)]  
  
 Çağırabilirsiniz <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> art arda karmaşık sorgu ifadeleri oluşturmak için yöntemi. Daha fazla bilgi için [nasıl yapılır: Bir veri hizmeti sorgusuna sorgu seçenekleri ekleme](../../../../docs/framework/data/wcf/how-to-add-query-options-to-a-data-service-query-wcf-data-services.md).  
  
 Sorgu seçenekleri size bir LINQ Sorgu söz dizimi bileşenleri ifade etmek için başka bir yol sağlar. Daha fazla bilgi için [LINQ konuları](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md).  
  
> [!NOTE]
>  `$select` Sorgu seçeneği eklenemez bir URI sorgu kullanarak <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> yöntemi. LINQ kullanmanızı öneririz <xref:System.Linq.Enumerable.Select%2A> oluşturmak ve istemciye yöntemi `$select` seçeneği istek URI'SİNDE sorgu.  
  
<a name="executingQueries"></a>   
## <a name="client-versus-server-execution"></a>İstemci sunucunun yürütme karşılaştırması  
 İstemci, bir sorgu içindeki iki parça yürütür. Mümkün olduğunda, bir sorgu ifadelerinde istemcide önce değerlendirilir ve ardından URI tabanlı bir sorgu oluşturulur ve hizmetteki verilere karşı değerlendirme için veri hizmetine gönderilen. Aşağıdaki LINQ sorgusu göz önünde bulundurun:  
  
 [!code-csharp[Astoria Northwind Client#LinqQueryClientEvalSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqqueryclientevalspecific)]  
 [!code-vb[Astoria Northwind Client#LinqQueryClientEvalSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqqueryclientevalspecific)]  
  
 Bu örnekte, ifade `(basePrice – (basePrice * discount))` istemcide değerlendirilir. Bu nedenle, URI asıl sorguyu `http://localhost:12345/northwind.svc/Products()?$filter=(UnitPrice gt 90.00M) and substringof('bike',ProductName)` , gönderilir verileri, hizmet zaten hesaplanan ondalık değeri içeren `90` filtre yan tümcesi içinde. Filtre ifadesinin alt ifade de dahil olmak üzere diğer bölümleri, veri hizmeti tarafından değerlendirilir. Veri hizmeti uygulaması üzerinde veri hizmetine gönderilen ifadeler kullanan ancak istemcide değerlendirilen ifadeleri izleyin ortak dil çalışma zamanı (CLR) semantiğini [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokolü. Senaryoları burada bu ayrı değerlendirme hem istemci hem de hizmet değerlendirmeleri zamana dayalı farklı saat dilimlerinde gerçekleştirirken gibi beklenmeyen sonuçlara neden olabilir farkında olmalıdır.  
  
## <a name="query-responses"></a>Sorgu yanıtları  
 Yürütüldüğünde, <xref:System.Data.Services.Client.DataServiceQuery%601> döndürür bir <xref:System.Collections.Generic.IEnumerable%601> istenen varlık türü. Bu sorgu sonucu atanabilecek bir <xref:System.Data.Services.Client.QueryOperationResponse%601> aşağıdaki örnekteki gibi bir nesne:  
  
 [!code-csharp[Astoria Northwind Client#GetResponseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getresponsespecific)]
 [!code-vb[Astoria Northwind Client#GetResponseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getresponsespecific)]  
  
 Data Service'teki varlıkları temsil eden varlık türü örnekleri istemci üzerinde nesne gerçekleştirme olarak adlandırılan bir işlem tarafından oluşturulur. Daha fazla bilgi için [nesne gerçekleştirme](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md). <xref:System.Data.Services.Client.QueryOperationResponse%601> Uygulayan nesne <xref:System.Collections.Generic.IEnumerable%601> sorgunun sonuçlarını erişim sağlamak için.  
  
 <xref:System.Data.Services.Client.QueryOperationResponse%601> Da bir sorgu sonucu ile ilgili ek bilgiler erişmenize olanak sağlayan aşağıdaki üyeleri içerir:  
  
-   <xref:System.Data.Services.Client.OperationResponse.Error%2A> -Tüm oluştu varsa işlemi tarafından oluşturulan bir hata alır.  
  
-   <xref:System.Data.Services.Client.OperationResponse.Headers%2A> -Sorgu Yanıtla ilişkili HTTP yanıt üstbilgilerinin koleksiyonunu içerir.  
  
-   <xref:System.Data.Services.Client.QueryOperationResponse.Query%2A> -özgün alır <xref:System.Data.Services.Client.DataServiceQuery%601> oluşturulan <xref:System.Data.Services.Client.QueryOperationResponse%601>.  
  
-   <xref:System.Data.Services.Client.OperationResponse.StatusCode%2A> -sorgu yanıtı HTTP yanıt kodunu alır.  
  
-   <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> -alır varlıkları varlıktaki toplam sayısına ayarlanan zaman <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> yöntemi çağrıldı <xref:System.Data.Services.Client.DataServiceQuery%601>.  
  
-   <xref:System.Data.Services.Client.QueryOperationResponse.GetContinuation%2A> -döndürür bir <xref:System.Data.Services.Client.DataServiceQueryContinuation> sonraki sonuç sayfasını URI'sini içeren nesne.  
  
 Varsayılan olarak, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] yalnızca URI sorgu tarafından açıkça seçilen verileri döndürür. Bu, gerektiğinde ek veriler veri hizmetinden açıkça yüklemek için seçeneği sunar. Bir istek, veri hizmetinden veriyi açıkça yüklemek her zaman veri hizmetine gönderilir. İlgili varlıklar, disk belleğine alınan yanıt verileri ve ikili veri akışlarını açıkça yüklenen verileri içerir.  
  
> [!NOTE]
>  Bir veri hizmeti disk belleğine alınan yanıtı döndürebilir olduğundan, uygulamanızı bir disk belleğine alınan veri hizmeti yanıtı işlemek için programlama deseni kullanmanızı öneririz. Daha fazla bilgi için [ertelenmiş içerik yükleme](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).  
  
 Bir sorgu tarafından döndürülen veri miktarını da yalnızca belirli özellikleri bir varlığın içinde yanıt döndürüldüğünü belirterek azaltılabilir. Daha fazla bilgi için [sorgu projeksiyonları](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md).  
  
## <a name="getting-a-count-of-the-total-number-of-entities-in-the-set"></a>Kümesindeki varlıkların toplam sayısı sayısı alınıyor  
 Bazı senaryolarda, bir varlık kümesindeki varlıkların toplam sayısı ve değil yalnızca sorgu tarafından döndürülen sayı faydalıdır. Çağrı <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> metodunda <xref:System.Data.Services.Client.DataServiceQuery%601> bu varlık kümesindeki toplam sayı sorgu sonucu ile gelen istemek için. Bu durumda, <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> özelliği döndürülen <xref:System.Data.Services.Client.QueryOperationResponse%601> kümesindeki varlıkların toplam sayısını döndürür.  
  
 Yalnızca toplam sayısını, varlık kümesinde alabilirsiniz ya da farklı bir <xref:System.Int32> veya farklı bir <xref:System.Int64> çağırarak değeri <xref:System.Linq.Enumerable.Count%2A> veya <xref:System.Linq.Enumerable.LongCount%2A> yöntemleri sırasıyla. Bu yöntemler çağrıldığında bir <xref:System.Data.Services.Client.QueryOperationResponse%601> döndürülen değil; yalnızca sayı değeri döndürülür. Daha fazla bilgi için [nasıl yapılır: Bir sorgu tarafından döndürülen varlık sayısını belirleme](../../../../docs/framework/data/wcf/number-of-entities-returned-by-a-query-wcf.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Sorgu Projeksiyonları](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)  
  
 [Nesne Gerçekleştirme](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)  
  
 [LINQ Konuları](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)  
  
 [Nasıl yapılır: Veri Hizmeti sorguları yürütme](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)  
  
 [Nasıl yapılır: Bir veri hizmeti sorgusuna sorgu seçenekleri ekleme](../../../../docs/framework/data/wcf/how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)  
  
 [Nasıl yapılır: Bir sorgu tarafından döndürülen varlık sayısını belirleme](../../../../docs/framework/data/wcf/number-of-entities-returned-by-a-query-wcf.md)  
  
 [Nasıl yapılır: İstek veri hizmeti için istemci kimlik bilgilerini belirtin](../../../../docs/framework/data/wcf/specify-client-creds-for-a-data-service-request-wcf.md)  
  
 [Nasıl yapılır: İstemci isteğinde üst bilgileri Ayarla](../../../../docs/framework/data/wcf/how-to-set-headers-in-the-client-request-wcf-data-services.md)  
  
 [Nasıl yapılır: Proje sorgu sonuçları](../../../../docs/framework/data/wcf/how-to-project-query-results-wcf-data-services.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
