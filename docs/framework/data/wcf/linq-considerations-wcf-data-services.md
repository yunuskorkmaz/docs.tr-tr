---
title: LINQ konuları (WCF Veri Hizmetleri)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ
- querying the data service [WCF Data Services]
- WCF Data Services, querying
ms.assetid: cc4ec9e9-348f-42a6-a78e-1cd40e370656
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c20817e791ae95efecd00a41a44c14eedec017d4
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="linq-considerations-wcf-data-services"></a>LINQ konuları (WCF Veri Hizmetleri)
Bu konuda hangi LINQ sorgularını oluşur ve kullanırken yürütülen yolu hakkında bilgi verilmektedir [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemci ve uygulayan bir veri hizmeti sorgulamak için LINQ kullanma sınırlamaları [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] oluşturma ve sorguları yürütme bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-veri hizmeti temel bkz [veri hizmeti sorgulanırken](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
## <a name="composing-linq-queries"></a>Çıktısından LINQ sorguları  
 LINQ sorguları uygulayan nesneler koleksiyonunu oluşturan olanak tanır <xref:System.Collections.Generic.IEnumerable%601>. Her iki **hizmet Başvurusu Ekle** Visual Studio iletişim kutusunda ve DataSvcUtil.exe aracı bir gösterimini üretmek için kullanılan bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] öğesinden devralınan bir varlık kapsayıcı sınıfı olarak hizmet <xref:System.Data.Services.Client.DataServiceContext>, yanı akışlarında döndürülen varlıklar temsil eden nesneler. Bu araçları ayrıca akışları hizmet tarafından sunulan koleksiyonlar için varlık kapsayıcı sınıfındaki özellikleri oluşturur. Dönüş veri hizmeti yalıtan sınıfının bu özelliklerin her biri bir <xref:System.Data.Services.Client.DataServiceQuery%601>. Çünkü <xref:System.Data.Services.Client.DataServiceQuery%601> uygulayan sınıf <xref:System.Linq.IQueryable%601> LINQ tarafından tanımlanan arabirimi istemci kitaplığı tarafından bir sorgu isteği veri hizmetine gönderilen URI içine çevrilen veri hizmeti tarafından sunulan akışları bir LINQ Sorgu oluşturma yürütme.  
  
> [!IMPORTANT]
>  LINQ sözdiziminde ifade sorguları kümesi tarafından kullanılan URI sözdizimi etkin olandan daha geniş [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Veri Hizmetleri. A <xref:System.NotSupportedException> hedef veri hizmetindeki bir URI sorgu eşlenemiyor tetiklenir. Daha fazla bilgi için bkz: [desteklenmeyen LINQ yöntemleri](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md#unsupportedMethods) bu konuda.  
  
 Aşağıdaki örnek döndüren bir LINQ Sorgu olduğu `Orders` birden fazla $30 bir nakliye maliyeti ve en son sevk tarihten başlayarak sonuçları sevkiyat tarihine göre sıralar:  
  
[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionslinqspecific)]      
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionslinqspecific)]    
  
 Aşağıdaki sorgu Northwind tabanlı karşı yürütülen URI içine bu LINQ sorgusu çevrilen [Hızlı Başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) veri hizmeti:  
  
```  
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30  
```  
  
 LINQ hakkında daha fazla genel bilgi için bkz: [LINQ (dil ile tümleşik sorgu)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).  
  
 LINQ sorgularını önceki örnekte, aynı zamanda sorgu yöntemleri bir dizi standart sorgu işleçleri bilinen iki dile özgü bildirim temelli sorgu sözdizimini, kullanarak oluşturmak etkinleştirir. Önceki örnekte eşdeğer bir sorguya yalnızca yöntem temelli söz dizimi kullanarak birleştirilebilen aşağıdaki örnekte gösterildiği gibi:  
  
[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqExpressionSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionslinqexpressionspecific)]      
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqExpressionSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionslinqexpressionspecific)]    
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] İstemci oluşan sorguları her iki tür bir sorgu URI'si Çevir mümkün olduğunda ve bir sorgu ifadesi sorgu yöntemleri ekleyerek bir LINQ Sorgu genişletebilirsiniz. Ne zaman, oluşturan LINQ sorgularını bir sorgu ifadesi yöntem sözdizimi ekleyerek veya <xref:System.Data.Services.Client.DataServiceQuery%601>, yöntemleri çağrılmadan sırayla URI sorgu işlemleri eklenir. Bu arama için eşdeğerdir <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> yöntemi her sorgu seçeneği URI sorguya ekleyin.  
  
## <a name="executing-linq-queries"></a>Yürütülen LINQ sorguları  
 Belirli LINQ Sorgu yöntemleri gibi <xref:System.Linq.Enumerable.First%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> veya <xref:System.Linq.Enumerable.Single%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>sorguya eklenmiş olduğunda, yürütülecek sorgu neden. Sorgu sonuçları olduğunda da yürütülür sırasında dolaylı olarak gibi numaralandırılmış bir `foreach` döngü veya sorgu atandığında bir `List` koleksiyonu. Daha fazla bilgi için bkz: [veri hizmeti sorgulanırken](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 İstemci bir LINQ Sorgu iki parça halinde yürütür. Mümkün olduğunda, bir sorguda LINQ ifadeleri, ilk olarak istemci üzerinde değerlendirilir ve ardından URI tabanlı bir sorgunun oluşturulur ve veri hizmeti için hizmet veri karşı değerlendirme için gönderilir. Daha fazla bilgi için bkz [Server yürütme karşı istemci](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md#executingQueries) içinde [veri hizmeti sorgulanırken](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 Ne zaman bir LINQ Sorgu çevrilemez içinde bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-yürütme denendiğinde uyumlu sorgu URI, bir özel durum oluşturulur. Daha fazla bilgi için bkz: [veri hizmeti sorgulanırken](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
## <a name="linq-query-examples"></a>LINQ Sorgu örnekleri  
 Aşağıdaki bölümlerde yer alan örnekler karşı yürütülen LINQ sorgularını türlerini gösteren bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] hizmet.  
  
<a name="filtering"></a>   
### <a name="filtering"></a>Filtreleme  
 Bu bölümdeki LINQ Sorgu örnekleri hizmet tarafından döndürülen akıştaki verileri filtreleyin.  
  
 Aşağıdaki örnekler döndürülen filtre eşdeğer sorguları `Orders` $30'dan büyük bir nakliye maliyeti ile yalnızca siparişleri şekilde varlıklar döndürüldü:  
  
-   LINQ sorgu sözdizimini kullanarak:  
  
[!code-csharp[Astoria Northwind Client#LinqWhereClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqwhereclausespecific)]      
[!code-vb[Astoria Northwind Client#LinqWhereClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqwhereclausespecific)]     
  
-   LINQ Sorgu yöntemleri kullanma:  
  
[!code-csharp[Astoria Northwind Client#LinqWhereMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqwheremethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqWhereMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqwheremethodspecific)]       
  
-   URI sorgu dizesi `$filter` seçeneği:  
  
[!code-csharp[Astoria Northwind Client#ExplicitQueryWhereMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#explicitquerywheremethodspecific)]      
[!code-vb[Astoria Northwind Client#ExplicitQueryWhereMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#explicitquerywheremethodspecific)]       
  
 Önceki örneklerde tümünün URI sorgu çevrilir: `http://localhost:12345/northwind.svc/Orders()?$filter=Freight gt 30M`.  
  
<a name="sorting"></a>   
### <a name="sorting"></a>Sıralama  
 Aşağıdaki örnekler, döndürülen veriler hem şirket adını ve posta kodu, azalan sıralama eşdeğer sorguları gösterir:  
  
-   LINQ sorgu sözdizimini kullanarak:  
  
[!code-csharp[Astoria Northwind Client#LinqOrderByClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqorderbyclausespecific)]      
[!code-vb[Astoria Northwind Client#LinqOrderByClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqorderbyclausespecific)]        
  
-   LINQ Sorgu yöntemleri kullanma:  
  
[!code-csharp[Astoria Northwind Client#LinqOrderByMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqorderbymethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqOrderByMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqorderbymethodspecific)]        
  
-   URI sorgu dizesi `$orderby` seçeneği):  
  
[!code-csharp[Astoria Northwind Client#ExplicitQueryOrderByMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#explicitqueryorderbymethodspecific)]      
[!code-vb[Astoria Northwind Client#ExplicitQueryOrderByMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#explicitqueryorderbymethodspecific)]         
  
 Önceki örneklerde tümünün URI sorgu çevrilir: `http://localhost:12345/northwind.svc/Customers()?$orderby=CompanyName,PostalCode desc`.  
  
<a name="projection"></a>   
### <a name="projection"></a>Projeksiyon  
 Aşağıdaki örnekler döndürülen veri dar proje eşdeğer sorguları `CustomerAddress` türü:  
  
-   LINQ sorgu sözdizimini kullanarak:  
  
[!code-csharp[Astoria Northwind Client#LinqSelectClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqselectclausespecific)]      
[!code-vb[Astoria Northwind Client#LinqSelectClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqselectclausespecific)]         
  
-   LINQ Sorgu yöntemleri kullanma:  
  
[!code-csharp[Astoria Northwind Client#LinqSelectMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqselectmethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqSelectMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqselectmethodspecific)]         
 
  
> [!NOTE]
>  `$select` Sorgu seçeneği eklenemez bir sorgu URI kullanılarak <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> yöntemi. LINQ kullanmanızı öneririz <xref:System.Linq.Enumerable.Select%2A> yöntemi oluşturmak istemcinin `$select` seçeneği URI isteğinde sorgu.  
  
 Önceki örneklerde her ikisi de URI sorgu çevrilir: `"http://localhost:12345/northwind.svc/Customers()?$filter=Country eq 'GerGerm'&$select=CustomerID,Address,City,Region,PostalCode,Country"`.  
  
<a name="paging"></a>   
### <a name="client-paging"></a>İstemci disk belleği  
 Aşağıdaki örnekler ilk 50 siparişleri atlanıyor 25 siparişleri içeren bir sayfa sıralanmış varlıkların isteği eşdeğer sorguları gösterir:  
  
-   Sorgu yöntemleri LINQ sorgusu için uygulanıyor:  
  
[!code-csharp[Astoria Northwind Client#LinqSkipTakeMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqskiptakemethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqSkipTakeMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqskiptakemethodspecific)]     
  
-   URI sorgu dizesi `$skip` ve `$top` seçenekleri):  
  
[!code-csharp[Astoria Northwind Client#ExplicitQuerySkipTakeMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#explicitqueryskiptakemethodspecific)]      
[!code-vb[Astoria Northwind Client#ExplicitQuerySkipTakeMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#explicitqueryskiptakemethodspecific)]     
  
 Önceki örneklerde her ikisi de URI sorgu çevrilir: `http://localhost:12345/northwind.svc/Orders()?$orderby=OrderDate desc&$skip=50&$top=25`.  
  
<a name="expand"></a>   
### <a name="expand"></a>Genişletme  
 Sorguladığınızda bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] veri hizmeti, sorgu tarafından hedeflenen varlıkla ilgili varlıklar dahil isteyebileceği döndürülen akış. <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> Yöntemi çağrıldığında <xref:System.Data.Services.Client.DataServiceQuery%601> LINQ Sorgu tarafından hedeflenen varlık kümesi için ile ilişkili varlık kümesinin adı olarak sağlanan `path` parametresi. Daha fazla bilgi için bkz: [ertelenmiş içerik yüklenirken](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).  
  
 Aşağıdaki örnekler kullanmak üzere eşdeğeri yolları <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> sorguda yöntemi:  
  
-   LINQ Sorgu söz dizimi:  
  
[!code-csharp[Astoria Northwind Client#LinqQueryExpandSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqqueryexpandspecific)]      
[!code-vb[Astoria Northwind Client#LinqQueryExpandSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqqueryexpandspecific)]  
  
-   LINQ Sorgu yöntemleriyle:  

[!code-csharp[Astoria Northwind Client#LinqQueryExpandMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqqueryexpandmethodspecific)]       
[!code-vb[Astoria Northwind Client#LinqQueryExpandMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqqueryexpandmethodspecific)]       
  
  
 Önceki örneklerde her ikisi de URI sorgu çevrilir: `http://localhost:12345/northwind.svc/Orders()?$filter=CustomerID eq 'ALFKI'&$expand=Order_Details`.  
  
<a name="unsupportedMethods"></a>   
## <a name="unsupported-linq-methods"></a>Desteklenmeyen LINQ yöntemleri  
 Aşağıdaki tabloda sınıfları içerir LINQ yöntemleri desteklenmez ve yürütülen sorguda eklenemez bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] hizmeti:  
  
|İşlem türü|Desteklenmeyen yöntemi|  
|--------------------|------------------------|  
|Küme işleci|Tüm küme işleci karşı desteklenmeyen bir <xref:System.Data.Services.Client.DataServiceQuery%601>, aşağıdakiler dahil:<br /><br /> -   <xref:System.Linq.Enumerable.All%2A><br />-   <xref:System.Linq.Enumerable.Any%2A><br />-   <xref:System.Linq.Enumerable.Concat%2A><br />-   <xref:System.Linq.Enumerable.DefaultIfEmpty%2A><br />-   <xref:System.Linq.Enumerable.Distinct%2A><br />-   <xref:System.Linq.Enumerable.Except%2A><br />-   <xref:System.Linq.Enumerable.Intersect%2A><br />-   <xref:System.Linq.Enumerable.Union%2A><br />-   <xref:System.Linq.Enumerable.Zip%2A>|  
|Sıralama işleçleri|Gerektiren aşağıdaki sıralama işleçleri <xref:System.Collections.Generic.IComparer%601> karşı desteklenmeyen bir <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> -   <xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29>|  
|Projeksiyon ve işleçler filtreleme|Konumsal bir bağımsız değişken kabul filtreleme işleçler ve aşağıdaki projeksiyon karşı desteklenmeyen bir <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> -   <xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%2CSystem.Collections.Generic.IEqualityComparer%7B%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2C%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Where%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Boolean%7D%29>|  
|Gruplandırma işleçleri|Tüm gruplandırma işleçleri karşı desteklenmeyen bir <xref:System.Data.Services.Client.DataServiceQuery%601>, aşağıdakiler dahil:<br /><br /> -   <xref:System.Linq.Enumerable.GroupBy%2A><br />-   <xref:System.Linq.Enumerable.GroupJoin%2A><br /><br /> Gruplandırma işlemleri istemcide gerçekleştirilmesi gerekir.|  
|Toplama işleçleri|Tüm toplama işlemleri karşı desteklenmeyen bir <xref:System.Data.Services.Client.DataServiceQuery%601>, aşağıdakiler dahil:<br /><br /> -   <xref:System.Linq.Enumerable.Aggregate%2A><br />-   <xref:System.Linq.Enumerable.Average%2A><br />-   <xref:System.Linq.Enumerable.Count%2A><br />-   <xref:System.Linq.Enumerable.LongCount%2A><br />-   <xref:System.Linq.Enumerable.Max%2A><br />-   <xref:System.Linq.Enumerable.Min%2A><br />-   <xref:System.Linq.Enumerable.Sum%2A><br /><br /> Toplama işlemleri istemcide ya da gerçekleştirilmesi gerekir veya bir hizmet işlemi tarafından kapsüllenir.|  
|Disk belleği işleçleri|Aşağıdaki disk belleği işleçleri karşı desteklenmiyor bir <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> -   <xref:System.Linq.Enumerable.ElementAt%2A><br />-   <xref:System.Linq.Enumerable.Last%2A><br />-   <xref:System.Linq.Enumerable.LastOrDefault%2A><br />-   <xref:System.Linq.Enumerable.SkipWhile%2A><br />-   <xref:System.Linq.Enumerable.TakeWhile%2A> **Not:** üzerinde boş bir dizi yürütülen disk belleği işleçleri null döndürür.|  
|Diğer işleçleri|Aşağıdaki diğer işleçler karşı desteklenmiyor bir <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> 1.  <xref:System.Linq.Enumerable.Empty%2A><br />2.  <xref:System.Linq.Enumerable.Range%2A><br />3.  <xref:System.Linq.Enumerable.Repeat%2A><br />4.  <xref:System.Linq.Enumerable.ToDictionary%2A><br />5.  <xref:System.Linq.Enumerable.ToLookup%2A>|  
  
<a name="supportedExpressions"></a>   
## <a name="supported-expression-functions"></a>Desteklenen ifade işlevleri  
 İstek URI'si eklenmek üzere bir sorgu ifadesinde çevrilebilir çünkü aşağıdaki ortak dil çalışma zamanı (CLR) yöntemleri ve özellikleri desteklenen için bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] hizmeti:  
  
|<xref:System.String> Üye|Desteklenen [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] işlevi|  
|-----------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.String.Concat%28System.String%2CSystem.String%29>|`string concat(string p0, string p1)`|  
|<xref:System.String.Contains%28System.String%29>|`bool substringof(string p0, string p1)`|  
|<xref:System.String.EndsWith%28System.String%29>|`bool endswith(string p0, string p1)`|  
|<xref:System.String.IndexOf%28System.String%2CSystem.Int32%29>|`int indexof(string p0, string p1)`|  
|<xref:System.String.Length>|`int length(string p0)`|  
|<xref:System.String.Replace%28System.String%2CSystem.String%29>|`string replace(string p0, string find, string replace)`|  
|<xref:System.String.Substring%28System.Int32%29>|`string substring(string p0, int pos)`|  
|<xref:System.String.Substring%28System.Int32%2CSystem.Int32%29>|`string substring(string p0, int pos, int length)`|  
|<xref:System.String.ToLower>|`string tolower(string p0)`|  
|<xref:System.String.ToUpper>|`string toupper(string p0)`|  
|<xref:System.String.Trim>|`string trim(string p0)`|  
  
|<xref:System.DateTime> Üye<sup>1</sup>|Desteklenen [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] işlevi|  
|-------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.DateTime.Day>|`int day(DateTime p0)`|  
|<xref:System.DateTime.Hour>|`int hour(DateTime p0)`|  
|<xref:System.DateTime.Minute>|`int minute(DateTime p0)`|  
|<xref:System.DateTime.Month>|`int month(DateTime p0)`|  
|<xref:System.DateTime.Second>|`int second(DateTime p0)`|  
|<xref:System.DateTime.Year>|`int year(DateTime p0)`|  
  
 <sup>1</sup>eşdeğer tarih ve saat özellikleri <xref:Microsoft.VisualBasic.DateAndTime?displayProperty=nameWithType>, yanı sıra <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> Visual Basic'te yöntemi de desteklenir.  
  
|<xref:System.Math> Üye|Desteklenen [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] işlevi|  
|---------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Math.Ceiling%28System.Decimal%29>|`decimal ceiling(decimal p0)`|  
|<xref:System.Math.Ceiling%28System.Double%29>|`double ceiling(double p0)`|  
|<xref:System.Math.Floor%28System.Decimal%29>|`decimal floor(decimal p0)`|  
|<xref:System.Math.Floor%28System.Double%29>|`double floor(double p0)`|  
|<xref:System.Math.Round%28System.Decimal%29>|`decimal round(decimal p0)`|  
|<xref:System.Math.Round%28System.Double%29>|`double round(double p0)`|  
  
|<xref:System.Linq.Expressions.Expression> Üye|Desteklenen [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] işlevi|  
|---------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Linq.Expressions.Expression.TypeIs%28System.Linq.Expressions.Expression%2CSystem.Type%29>|`bool isof(type p0)`|  
  
 İstemci ayrıca istemcide ek CLR işlevleri değerlendirmek mümkün olabilir. A <xref:System.NotSupportedException> istemcide değerlendirilemez ve değerlendirme sunucuda geçerli isteğin URI çevrilemez herhangi bir ifade için oluşturulur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Hizmetini Sorgulama](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
 [Sorgu Projeksiyonları](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)  
 [Nesne Gerçekleştirme](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)  
 [OData: URI kuralları](http://go.microsoft.com/fwlink/?LinkID=185564)
