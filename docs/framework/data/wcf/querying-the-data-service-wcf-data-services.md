---
title: Veri Hizmeti (WCF Veri Hizmetleri) sorgulama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: 823e9444-27aa-4f1f-be8e-0486d67f54c0
ms.openlocfilehash: bcdeb4f9755f526827045a9cc63bc8bdad4b28d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="querying-the-data-service-wcf-data-services"></a>Veri Hizmeti (WCF Veri Hizmetleri) sorgulama
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] İstemci kitaplığını kullanarak bir veri hizmeti tanıdık sorgu yürütebilir olanak tanır [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dil ile tümleşik sorgu (LINQ) kullanımı dahil olmak üzere düzenleri programlama. İstemcide bir örneği olarak tanımlanan bir sorgu istemci kitaplığı çevirir <xref:System.Data.Services.Client.DataServiceQuery%601> sınıfına bir HTTP GET isteği iletisi. Kitaplık yanıt iletisini alır ve istemci veri hizmeti sınıfları örneğine çevirir. Bu sınıf tarafından izlenen <xref:System.Data.Services.Client.DataServiceContext> hangi <xref:System.Data.Services.Client.DataServiceQuery%601> ait.  
  
## <a name="data-service-queries"></a>Veri hizmeti sorgular  
 <xref:System.Data.Services.Client.DataServiceQuery%601> Genel sınıfı, sıfır veya daha fazla varlık türü örneklerinin bir koleksiyonunu döndüren bir sorgu temsil eder. Veri Hizmeti sorgusu her zaman varolan bir veri hizmeti bağlamına ait. Bu bağlamda oluşturabilir ve sorguyu yürütmek için gerekli olan hizmet URI ve meta veri bilgilerini korur.  
  
 Kullandığınızda **hizmet Başvurusu Ekle** bir veri hizmetine eklemek için iletişim bir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]-tabanlı istemci uygulaması, bir varlık kapsayıcı sınıfı öğesinden devralınan oluşturulur <xref:System.Data.Services.Client.DataServiceContext> sınıfı. Bu sınıf yazılan döndüren özellikleri içeren <xref:System.Data.Services.Client.DataServiceQuery%601> örnekleri. Veri çıkarır hizmeti her bir varlık kümesi için bir özellik yok. Bu özellikleri yazılmış bir örneği oluşturmak daha kolay <xref:System.Data.Services.Client.DataServiceQuery%601>.  
  
 Bir sorgu aşağıdaki senaryolarda çalıştırılır:  
  
-   Sonuçları dolaylı olarak numaralandırılır zaman gibi:  
  
    -   Bir özellik zaman <xref:System.Data.Services.Client.DataServiceContext> temsil eden ve varlık kümesi numaralandırılan, gibi sırasında bir `foreach` (C#) veya `For Each` (Visual Basic) döngü.  
  
    -   Ne zaman sorgu atanması bir `List` koleksiyonu.  
  
-   Zaman <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> veya <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> yöntemi açıkça çağrılır.  
  
-   Ne zaman bir LINQ Sorgu yürütme işleci gibi <xref:System.Linq.Enumerable.First%2A> veya <xref:System.Linq.Enumerable.Single%2A> olarak adlandırılır.  
  
 Yürütüldüğünde, aşağıdaki sorgu tüm döndürür `Customers` Northwind veri hizmeti varlıklarda:  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getallcustomersspecific)]  
 [!code-vb[Astoria Northwind Client#GetAllCustomersSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getallcustomersspecific)]  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: veri hizmeti sorguları yürütmek](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md).  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] İstemcisi kullandığınızda gibi geç bağlama nesneler için sorguları destekler *dinamik* C# türü. Ancak, performansı artırmak için her zaman kesin türü belirtilmiş veri hizmeti sorguları oluşturma. <xref:System.Tuple> Türü ve dinamik nesneler istemci tarafından desteklenmez.  
  
## <a name="linq-queries"></a>LINQ Sorguları  
 Çünkü <xref:System.Data.Services.Client.DataServiceQuery%601> uygulayan sınıf <xref:System.Linq.IQueryable%601> LINQ tarafından tanımlanan arabirimi [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemci kitaplığı veri hizmeti karşı hesaplanan bir sorgu ifadesi gösteren bir URI varlık kümesi verilerinin LINQ sorguları dönüştürmek için Kaynak. Önceki denk bir LINQ Sorgu aşağıdaki örnekte olduğu <xref:System.Data.Services.Client.DataServiceQuery%601> döndüren `Orders` maliyet nakliye tarafından bir nakliye maliyetini birden fazla $30 ve siparişleri sonuçları vardır:  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionslinqspecific)]  
 [!code-vb[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionslinqspecific)]  
  
 Aşağıdaki sorgu Northwind tabanlı karşı yürütülen URI içine bu LINQ sorgusu çevrilen [Hızlı Başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) veri hizmeti:  
  
```  
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30  
```  
  
> [!NOTE]
>  Sorgu LINQ sözdiziminde ifade kümesini temsili durum aktarımı (REST) etkin olandan daha geniş-veri hizmetleri tarafından kullanılan URI sözdizimi tabanlı. A <xref:System.NotSupportedException> hedef veri hizmetindeki bir URI sorgu eşlenemiyor tetiklenir.  
  
 Daha fazla bilgi için bkz: [LINQ konuları](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md).  
  
## <a name="adding-query-options"></a>Sorgu seçeneklerini ekleme  
 Veri Hizmeti sorguları desteği tüm sorgu seçeneklerini [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]s sağlar. Çağırmanız <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> sorgu seçeneklerini eklenecek yöntemi bir <xref:System.Data.Services.Client.DataServiceQuery%601> örneği. <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> Yeni bir döndürür <xref:System.Data.Services.Client.DataServiceQuery%601> özgün sorguya eşdeğer olan örneği ancak yeni sorgu seçenek kümesi. Çalıştırıldığında, aşağıdaki sorguyu döndürür `Orders` göre filtrelenmiş `Freight` değer ve göre sıralanmış `OrderID`, azalan:  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionsspecific)]  
 [!code-vb[Astoria Northwind Client#AddQueryOptionsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionsspecific)]  
  
 Kullanabileceğiniz `$orderby` sorgu seçeneği hem de sipariş ve filtreler ve döndürülen siparişleri aşağıdaki örnekteki gibi tek bir özelliğe dayalı bir sorgu filtre `Orders` nesneleri değeri temel alarak `Freight` özelliği:  
  
 [!code-csharp[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#orderwithfilter)]
 [!code-vb[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#orderwithfilter)]  
  
 Çağırabilirsiniz <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> art arda karmaşık sorgu ifadeleri oluşturmak için yöntem. Daha fazla bilgi için bkz: [nasıl yapılır: bir veri hizmeti sorgusu sorgu seçeneklerini eklemek](../../../../docs/framework/data/wcf/how-to-add-query-options-to-a-data-service-query-wcf-data-services.md).  
  
 Sorgu seçeneklerini LINQ sorgusu sözdizimsel bileşenlerini ifade etmek için başka bir yol sağlar. Daha fazla bilgi için bkz: [LINQ konuları](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md).  
  
> [!NOTE]
>  `$select` Sorgu seçeneği eklenemez bir sorgu URI kullanılarak <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> yöntemi. LINQ kullanmanızı öneririz <xref:System.Linq.Enumerable.Select%2A> yöntemi oluşturmak istemcinin `$select` seçeneği URI isteğinde sorgu.  
  
<a name="executingQueries"></a>   
## <a name="client-versus-server-execution"></a>İstemci sunucusu yürütme karşılaştırması  
 İstemci bir sorgu iki parça halinde yürütür. Mümkün olduğunda, bir sorgu ifadelerinde, ilk olarak istemci üzerinde değerlendirilir ve ardından URI tabanlı bir sorgunun oluşturulur ve veri hizmeti için hizmet veri karşı değerlendirme için gönderilir. Aşağıdaki LINQ sorgusu göz önünde bulundurun:  
  
 [!code-csharp[Astoria Northwind Client#LinqQueryClientEvalSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqqueryclientevalspecific)]  
 [!code-vb[Astoria Northwind Client#LinqQueryClientEvalSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqqueryclientevalspecific)]  
  
 Bu örnekte, ifade `(basePrice – (basePrice * discount))` istemcide değerlendirilir. Bu nedenle, gerçek sorgu URI `http://localhost:12345/northwind.svc/Products()?$filter=(UnitPrice gt 90.00M) and substringof('bike',ProductName)` , gönderilen verileri hizmeti zaten hesaplanan ondalık değeri içeren `90` filtre yan tümcesi içinde. Filtre ifadesinin substring ifade dahil olmak üzere diğer bölümleri veri hizmeti tarafından değerlendirilir. İstemci üzerinde değerlendirilir ifadeleri izleyin ortak dil çalışma zamanı (CLR) semantiği, veri hizmeti uygulaması üzerinde veri hizmetine gönderilen ifadeler kullanan sırada [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokolü. Ayrıca bu ayrı değerlendirme hem istemci hem de hizmet zamana dayalı değerlendirmeleri farklı saat dilimlerinde yapılırken gibi beklenmeyen sonuçlara neden olduğu senaryolar haberdar olmanız gerekir.  
  
## <a name="query-responses"></a>Sorgu yanıtları  
 Çalıştırıldığında, <xref:System.Data.Services.Client.DataServiceQuery%601> döndüren bir <xref:System.Collections.Generic.IEnumerable%601> istenen varlık türü. Bu sorgu sonucu atanabilecek bir <xref:System.Data.Services.Client.QueryOperationResponse%601> nesnesi, aşağıdaki örnekteki gibi:  
  
 [!code-csharp[Astoria Northwind Client#GetResponseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getresponsespecific)]
 [!code-vb[Astoria Northwind Client#GetResponseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getresponsespecific)]  
  
 Veri Hizmeti varlıklarda temsil eden varlık türü örnekleri istemcide nesne materialization adlı bir işlem tarafından oluşturulur. Daha fazla bilgi için bkz: [nesne Materialization](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md). <xref:System.Data.Services.Client.QueryOperationResponse%601> Uygulayan nesne <xref:System.Collections.Generic.IEnumerable%601> sorgu sonuçlarını erişim sağlamak için.  
  
 <xref:System.Data.Services.Client.QueryOperationResponse%601> Sorgu sonucu hakkında ek bilgi erişmenize olanak sağlayan aşağıdaki üyeleri de vardır:  
  
-   <xref:System.Data.Services.Client.OperationResponse.Error%2A> -herhangi bir oluştu varsa işlemi tarafından oluşturulan bir hata alır.  
  
-   <xref:System.Data.Services.Client.OperationResponse.Headers%2A> -sorgu yanıtı ile ilişkili HTTP yanıt üstbilgilerinin koleksiyonunu içerir.  
  
-   <xref:System.Data.Services.Client.QueryOperationResponse.Query%2A> -özgün alır <xref:System.Data.Services.Client.DataServiceQuery%601> oluşturulan <xref:System.Data.Services.Client.QueryOperationResponse%601>.  
  
-   <xref:System.Data.Services.Client.OperationResponse.StatusCode%2A> -HTTP yanıt kodunu sorgu yanıtı alır.  
  
-   <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> -alır varlıklar varlıktaki toplam sayısına ayarlanan ne zaman <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> yöntemi çağrıldı <xref:System.Data.Services.Client.DataServiceQuery%601>.  
  
-   <xref:System.Data.Services.Client.QueryOperationResponse.GetContinuation%2A> -döndüren bir <xref:System.Data.Services.Client.DataServiceQueryContinuation> sonraki sonuç sayfasını URI'sini içeren nesne.  
  
 Varsayılan olarak, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] yalnızca açıkça URI sorgu tarafından seçilen verileri döndürür. Bu dosyayı gerektiğinde ek veriler veri hizmetinden açıkça yüklemek için seçeneği sunar. Bir istek veri hizmetinden veri açıkça yükleyen her zaman veri hizmetine gönderilir. Açıkça yüklenen veriler ilgili varlıklar, disk belleğine alınan yanıt verilerini ve ikili veri akışlarını içerir.  
  
> [!NOTE]
>  Veri Hizmeti disk belleğine alınan yanıt döndürebileceği için uygulamanızı bir disk belleğine alınan veri hizmeti yanıtı işlemek için programlama düzeni kullanmanızı öneririz. Daha fazla bilgi için bkz: [ertelenmiş içerik yüklenirken](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).  
  
 Bir sorgu tarafından döndürülen veri miktarını da yalnızca belirli özellikleri bir varlığın yanıtta döndürüldüğünü belirterek azaltılabilir. Daha fazla bilgi için bkz: [sorgu tahminleri](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md).  
  
## <a name="getting-a-count-of-the-total-number-of-entities-in-the-set"></a>Kümesindeki varlıkların sayısı toplam sayısını alma  
 Bazı senaryolarda, bir varlık kümesindeki varlıkların toplam sayısı ve kesmenin sorgu tarafından döndürülen sayı bilmek yararlıdır. Çağrı <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> yöntemi <xref:System.Data.Services.Client.DataServiceQuery%601> bu toplam sayı kümesindeki varlıkların sorgu sonucu ile gelen istemek için. Bu durumda, <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> özelliği döndürülen <xref:System.Data.Services.Client.QueryOperationResponse%601> kümesindeki varlıkların toplam sayısını döndürür.  
  
 Varlıklar yalnızca toplam hata sayısı kümesinde alabilir ya da farklı bir <xref:System.Int32> veya as bir <xref:System.Int64> çağırarak değeri <xref:System.Linq.Enumerable.Count%2A> veya <xref:System.Linq.Enumerable.LongCount%2A> yöntemleri sırasıyla. Bu yöntem çağrıldığında, bir <xref:System.Data.Services.Client.QueryOperationResponse%601> döndürülmez; yalnızca sayısı değeri döndürülür. Daha fazla bilgi için bkz: [nasıl yapılır: sayı, varlıklar tarafından döndürülen bir sorgu belirlemek](../../../../docs/framework/data/wcf/number-of-entities-returned-by-a-query-wcf.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Sorgu Projeksiyonları](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)  
  
 [Nesne Gerçekleştirme](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)  
  
 [LINQ Konuları](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)  
  
 [Nasıl yapılır: Veri Hizmeti Sorguları Yürütme](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)  
  
 [Nasıl yapılır: Veri Hizmeti Sorgusuna Sorgu Seçenekleri Ekleme](../../../../docs/framework/data/wcf/how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)  
  
 [Nasıl yapılır: Sorgu Tarafından Döndürülen Varlık Sayısını Belirleme](../../../../docs/framework/data/wcf/number-of-entities-returned-by-a-query-wcf.md)  
  
 [Nasıl yapılır: Veri Hizmeti İsteği için İstemci Kimlik Bilgileri Belirtme](../../../../docs/framework/data/wcf/specify-client-creds-for-a-data-service-request-wcf.md)  
  
 [Nasıl yapılır: İstemci İsteğinde Üst Bilgileri Ayarlama](../../../../docs/framework/data/wcf/how-to-set-headers-in-the-client-request-wcf-data-services.md)  
  
 [Nasıl Yapılır: Sorgu Sonuçlarını Yansıtma](../../../../docs/framework/data/wcf/how-to-project-query-results-wcf-data-services.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
