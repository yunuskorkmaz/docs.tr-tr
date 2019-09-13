---
title: LINQ hususları (WCF Veri Hizmetleri)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ
- querying the data service [WCF Data Services]
- WCF Data Services, querying
ms.assetid: cc4ec9e9-348f-42a6-a78e-1cd40e370656
ms.openlocfilehash: 659e3ba02367feee4539a984b679173ee4544d17
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894307"
---
# <a name="linq-considerations-wcf-data-services"></a>LINQ hususları (WCF Veri Hizmetleri)
Bu konu, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]LINQ sorgularının nasıl oluşturulduğu ve yürütüldüğü ve ' i uygulayan bir veri hizmetini sorgulamak için LINQ kullanma sınırlamaları hakkında bilgi sağlar. Tabanlı bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]veri hizmetine yönelik sorgu oluşturma ve yürütme hakkında daha fazla bilgi için bkz. [veri hizmetini sorgulama](querying-the-data-service-wcf-data-services.md).  
  
## <a name="composing-linq-queries"></a>LINQ sorguları oluşturuluyor  
 LINQ, uygulayan <xref:System.Collections.Generic.IEnumerable%601>bir nesne koleksiyonuna karşı sorgu oluşturma imkanı sağlar. Visual Studio 'daki **hizmet başvurusu Ekle** iletişim kutusu ve DataSvcUtil. exe aracı, bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] hizmetin bir gösterimini, öğesinden <xref:System.Data.Services.Client.DataServiceContext>devralan bir varlık kapsayıcı sınıfı olarak oluşturmak için kullanılır ve bunu temsil eden nesneler akışlara döndürülen varlıklar. Bu araçlar, hizmet tarafından akış olarak gösterilen koleksiyonlar için varlık kapsayıcı sınıfında özellikler de oluşturur. Veri hizmetini kapsülleyen sınıfın bu özelliklerinin her biri, döndürür <xref:System.Data.Services.Client.DataServiceQuery%601>. Sınıfı, LINQ tarafından tanımlanan <xref:System.Linq.IQueryable%601> arabirimi uyguladığından, istemci kitaplığı tarafından sunulan veri hizmetine gönderilen akışlara yönelik bir LINQ sorgusu oluşturabilir ve bu, istemci kitaplığı tarafından veri hizmetine gönderilen bir sorgu isteği URI 'sine çevrilir. <xref:System.Data.Services.Client.DataServiceQuery%601> yürütme.  
  
> [!IMPORTANT]
> LINQ sözdiziminde ifade edilen sorgu kümesi, veri Hizmetleri tarafından [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kullanılan URI sözdiziminde etkinleştirilenlerden daha yavaştır. <xref:System.NotSupportedException> Sorgu, hedef veri hizmetindeki bir URI ile eşleştirilemez olduğunda tetiklenir. Daha fazla bilgi için bu konudaki [Desteklenmeyen LINQ yöntemlerine](linq-considerations-wcf-data-services.md#unsupportedMethods) bakın.  
  
 Aşağıdaki örnek, $30 'den daha fazla nakliye maliyeti `Orders` olan bir LINQ sorgusudur ve en son teslim tarihinden itibaren sevkiyat tarihine göre sonuçları sıralar:  
  
[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqspecific)]      
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqspecific)]    
  
 Bu LINQ sorgusu, Northwind tabanlı [hızlı başlangıç](quickstart-wcf-data-services.md) veri hizmeti 'ne karşı yürütülen AŞAĞıDAKI sorgu URI 'sine çevrilir:  
  
```http
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30  
```  
  
 LINQ hakkında daha fazla genel bilgi için bkz. [dil ile tümleşik sorgu (LINQ) C# -](../../../csharp/programming-guide/concepts/linq/index.md) veya [dil ile tümleşik sorgu (LINQ)-Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md).  
  
 LINQ, önceki örnekte gösterilen dile özgü bildirim temelli sorgu söz dizimini ve standart sorgu işleçleri olarak bilinen bir sorgu yöntemleri kümesini kullanarak sorgu oluşturma imkanı sağlar. Önceki örneğe eşdeğer bir sorgu, aşağıdaki örnekte gösterildiği gibi yalnızca Yöntem tabanlı sözdizimi kullanılarak oluşturulabilir:  
  
[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqExpressionSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqexpressionspecific)]      
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqExpressionSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqexpressionspecific)]    
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] İstemci her iki tür oluşturulmuş sorguyu bir sorgu URI 'sine çevirebilir ve sorgu yöntemlerini sorgu ifadesine ekleyerek bir LINQ sorgusunu genişletebilirsiniz. Bir sorgu ifadesine ya <xref:System.Data.Services.Client.DataServiceQuery%601>da öğesine Yöntem sözdizimini ekleyerek LINQ sorguları oluşturduğunuzda, işlemler sorgu URI 'sine yöntemlerin çağrıldığı sırada eklenir. Bu, her sorgu seçeneğini sorgu <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> URI 'sine eklemek için yöntemini çağırmaya eşdeğerdir.  
  
## <a name="executing-linq-queries"></a>LINQ sorguları yürütülüyor  
 Sorgunun eklendiği gibi <xref:System.Linq.Enumerable.First%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> <xref:System.Linq.Enumerable.Single%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>bazı LINQ sorgu yöntemleri, sorgunun yürütülmesine neden olur. Bir sorgu, `foreach` döngü sırasında veya sorgu bir `List` koleksiyona atandığında olduğu gibi, sonuçlar örtük olarak numaralandırıldıktan sonra da yürütülür. Daha fazla bilgi için bkz. [veri hizmetini sorgulama](querying-the-data-service-wcf-data-services.md).  
  
 İstemci iki bölümde bir LINQ sorgusu yürütür. Mümkün olduğunda, bir sorgudaki LINQ ifadeleri ilk olarak istemcide değerlendirilir ve ardından bir URI tabanlı sorgu oluşturulup hizmette verilere göre değerlendirme için veri hizmetine gönderilir. Daha fazla bilgi için, [veri hizmetini sorgularken](querying-the-data-service-wcf-data-services.md) [Istemci ile sunucu yürütme karşılaştırması](querying-the-data-service-wcf-data-services.md#executingQueries) bölümüne bakın.  
  
 Bir LINQ sorgusu, uyumlu bir sorgu URI 'sine [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]çevrilemez, yürütme denendiğinde bir özel durum oluşturulur. Daha fazla bilgi için bkz. [veri hizmetini sorgulama](querying-the-data-service-wcf-data-services.md).  
  
## <a name="linq-query-examples"></a>LINQ sorgu örnekleri  
 Aşağıdaki bölümlerde yer alan örneklerde, bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] hizmette yürütülen LINQ sorgularının türleri gösterilmektedir.  
  
<a name="filtering"></a>   
### <a name="filtering"></a>Filtreleme  
 Bu bölümdeki LINQ sorgu örnekleri, hizmet tarafından döndürülen akıştaki verileri filtreleyin.  
  
 Aşağıdaki örnekler, döndürülen `Orders` varlıkların yalnızca $30 'den büyük bir nakliye maliyeti olan siparişlerin döndürüldüğünden filtre uygulayan eşdeğer sorgulardır:  
  
- LINQ sorgu söz dizimini kullanma:  
  
[!code-csharp[Astoria Northwind Client#LinqWhereClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqwhereclausespecific)]      
[!code-vb[Astoria Northwind Client#LinqWhereClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqwhereclausespecific)]     
  
- LINQ sorgu yöntemlerini kullanma:  
  
[!code-csharp[Astoria Northwind Client#LinqWhereMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqwheremethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqWhereMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqwheremethodspecific)]       
  
- URI sorgu dizesi `$filter` seçeneği:  
  
[!code-csharp[Astoria Northwind Client#ExplicitQueryWhereMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#explicitquerywheremethodspecific)]      
[!code-vb[Astoria Northwind Client#ExplicitQueryWhereMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#explicitquerywheremethodspecific)]       
  
 Önceki örneklerin hepsi sorgu URI 'sine çevrilir: `http://localhost:12345/northwind.svc/Orders()?$filter=Freight gt 30M`.  
  
<a name="sorting"></a>   
### <a name="sorting"></a>Sıralama  
 Aşağıdaki örneklerde, döndürülen verileri hem şirket adına hem de posta koduna göre sıralayan, azalan olan eşdeğer sorgular gösterilmektedir:  
  
- LINQ sorgu söz dizimini kullanma:  
  
[!code-csharp[Astoria Northwind Client#LinqOrderByClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqorderbyclausespecific)]      
[!code-vb[Astoria Northwind Client#LinqOrderByClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqorderbyclausespecific)]        
  
- LINQ sorgu yöntemlerini kullanma:  
  
[!code-csharp[Astoria Northwind Client#LinqOrderByMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqorderbymethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqOrderByMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqorderbymethodspecific)]        
  
- URI sorgu dizesi `$orderby` seçeneği):  
  
[!code-csharp[Astoria Northwind Client#ExplicitQueryOrderByMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#explicitqueryorderbymethodspecific)]      
[!code-vb[Astoria Northwind Client#ExplicitQueryOrderByMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#explicitqueryorderbymethodspecific)]         
  
 Önceki örneklerin hepsi sorgu URI 'sine çevrilir: `http://localhost:12345/northwind.svc/Customers()?$orderby=CompanyName,PostalCode desc`.  
  
<a name="projection"></a>   
### <a name="projection"></a>Projeksiyon  
 Aşağıdaki örneklerde, projenin verileri daha dar `CustomerAddress` bir türe döndürdüğü eşdeğer sorgular gösterilmektedir:  
  
- LINQ sorgu söz dizimini kullanma:  
  
[!code-csharp[Astoria Northwind Client#LinqSelectClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqselectclausespecific)]      
[!code-vb[Astoria Northwind Client#LinqSelectClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqselectclausespecific)]         
  
- LINQ sorgu yöntemlerini kullanma:  
  
[!code-csharp[Astoria Northwind Client#LinqSelectMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqselectmethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqSelectMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqselectmethodspecific)]         

> [!NOTE]
> Sorgu seçeneği, <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> yöntemi kullanılarak sorgu URI 'sine eklenemez. `$select` İstemcinin istek URI 'sinde <xref:System.Linq.Enumerable.Select%2A> `$select` sorgu seçeneğini oluşturması için LINQ metodunu kullanmanızı öneririz.  
  
 Önceki örneklerin her ikisi de sorgu URI 'sine çevrilir: `"http://localhost:12345/northwind.svc/Customers()?$filter=Country eq 'GerGerm'&$select=CustomerID,Address,City,Region,PostalCode,Country"`.  
  
<a name="paging"></a>   
### <a name="client-paging"></a>İstemci disk belleği  
 Aşağıdaki örneklerde, 25 siparişi içeren sıralanmış sıra varlıklarının bir sayfasını isteyen ve ilk 50 siparişi atlayarak eşdeğer sorgular gösterilmektedir:  
  
- Sorgu yöntemleri bir LINQ sorgusuna uygulanıyor:  
  
[!code-csharp[Astoria Northwind Client#LinqSkipTakeMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqskiptakemethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqSkipTakeMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqskiptakemethodspecific)]     
  
- URI sorgu dizesi `$skip` ve `$top` seçenekleri):  
  
[!code-csharp[Astoria Northwind Client#ExplicitQuerySkipTakeMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#explicitqueryskiptakemethodspecific)]      
[!code-vb[Astoria Northwind Client#ExplicitQuerySkipTakeMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#explicitqueryskiptakemethodspecific)]     
  
 Önceki örneklerin her ikisi de sorgu URI 'sine çevrilir: `http://localhost:12345/northwind.svc/Orders()?$orderby=OrderDate desc&$skip=50&$top=25`.  
  
<a name="expand"></a>   
### <a name="expand"></a>Expand  
 Bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] veri hizmetini sorguladığınızda, sorgunun hedeflediği varlıkla ilgili varlıkların döndürülen akışı dahil edilmesini isteyebilirsiniz. Yöntemi, LINQ sorgusunun hedeflediği varlık <xref:System.Data.Services.Client.DataServiceQuery%601> kümesi için, `path` parametresi olarak sağlanan ilgili varlık kümesi adı ile çağrılır. <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> Daha fazla bilgi için bkz. [ertelenmiş Içerik yükleme](loading-deferred-content-wcf-data-services.md).  
  
 Aşağıdaki örneklerde, <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> yöntemi bir sorguda kullanmanın eşdeğer yolları gösterilmektedir:  
  
- LINQ sorgu sözdiziminde:  
  
[!code-csharp[Astoria Northwind Client#LinqQueryExpandSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqqueryexpandspecific)]      
[!code-vb[Astoria Northwind Client#LinqQueryExpandSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqqueryexpandspecific)]  
  
- LINQ sorgu yöntemleriyle:  

[!code-csharp[Astoria Northwind Client#LinqQueryExpandMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqqueryexpandmethodspecific)]       
[!code-vb[Astoria Northwind Client#LinqQueryExpandMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqqueryexpandmethodspecific)]       

 Önceki örneklerin her ikisi de sorgu URI 'sine çevrilir: `http://localhost:12345/northwind.svc/Orders()?$filter=CustomerID eq 'ALFKI'&$expand=Order_Details`.  
  
<a name="unsupportedMethods"></a>   
## <a name="unsupported-linq-methods"></a>Desteklenmeyen LINQ yöntemleri  
 Aşağıdaki tablo, LINQ yöntemlerinin sınıflarını içerir ve bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] hizmete karşı yürütülen bir sorguya eklenemez:  
  
|İşlem türü|Desteklenmeyen yöntemi|  
|--------------------|------------------------|  
|İşleç ayarla|Tüm küme işleçleri, aşağıdakileri içeren bir <xref:System.Data.Services.Client.DataServiceQuery%601>öğesine karşı desteklenmez:<br /><br /> -   <xref:System.Linq.Enumerable.All%2A><br />-   <xref:System.Linq.Enumerable.Any%2A><br />-   <xref:System.Linq.Enumerable.Concat%2A><br />-   <xref:System.Linq.Enumerable.DefaultIfEmpty%2A><br />-   <xref:System.Linq.Enumerable.Distinct%2A><br />-   <xref:System.Linq.Enumerable.Except%2A><br />-   <xref:System.Linq.Enumerable.Intersect%2A><br />-   <xref:System.Linq.Enumerable.Union%2A><br />-   <xref:System.Linq.Enumerable.Zip%2A>|  
|Sıralama işleçleri|Gerektiren <xref:System.Collections.Generic.IComparer%601> aşağıdaki sıralama işleçleri bir <xref:System.Data.Services.Client.DataServiceQuery%601>için desteklenmez:<br /><br /> -   <xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29>|  
|Projeksiyon ve filtreleme işleçleri|Konumsal bağımsız değişkeni kabul eden aşağıdaki projeksiyon ve filtreleme işleçleri bir <xref:System.Data.Services.Client.DataServiceQuery%601>için desteklenmez:<br /><br /> -   <xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%2CSystem.Collections.Generic.IEqualityComparer%7B%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2C%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Where%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Boolean%7D%29>|  
|Gruplandırma işleçleri|Aşağıdakiler de dahil olmak üzere tüm gruplandırma <xref:System.Data.Services.Client.DataServiceQuery%601>işleçleri bir için desteklenmez:<br /><br /> -   <xref:System.Linq.Enumerable.GroupBy%2A><br />-   <xref:System.Linq.Enumerable.GroupJoin%2A><br /><br /> Gruplandırma işlemlerinin istemcide gerçekleştirilmesi gerekir.|  
|Toplama işleçleri|Aşağıdakiler dahil olmak üzere tüm toplama işlemleri <xref:System.Data.Services.Client.DataServiceQuery%601>bir öğesine karşı desteklenmez:<br /><br /> -   <xref:System.Linq.Enumerable.Aggregate%2A><br />-   <xref:System.Linq.Enumerable.Average%2A><br />-   <xref:System.Linq.Enumerable.Count%2A><br />-   <xref:System.Linq.Enumerable.LongCount%2A><br />-   <xref:System.Linq.Enumerable.Max%2A><br />-   <xref:System.Linq.Enumerable.Min%2A><br />-   <xref:System.Linq.Enumerable.Sum%2A><br /><br /> Toplama işlemleri istemci üzerinde gerçekleştirilmelidir veya bir hizmet işlemi tarafından kapsüllenmelidir.|  
|Sayfalama işleçleri|Aşağıdaki sayfalama işleçleri bir <xref:System.Data.Services.Client.DataServiceQuery%601>için desteklenmez:<br /><br /> -   <xref:System.Linq.Enumerable.ElementAt%2A><br />-   <xref:System.Linq.Enumerable.Last%2A><br />-   <xref:System.Linq.Enumerable.LastOrDefault%2A><br />-   <xref:System.Linq.Enumerable.SkipWhile%2A><br />-   <xref:System.Linq.Enumerable.TakeWhile%2A>**Note:**  Boş bir dizide yürütülen sayfalama işleçleri null döndürür.|  
|Diğer işleçler|Aşağıdaki diğer işleçler bir <xref:System.Data.Services.Client.DataServiceQuery%601>için desteklenmez:<br /><br /> 1.  <xref:System.Linq.Enumerable.Empty%2A><br />2.  <xref:System.Linq.Enumerable.Range%2A><br />3.  <xref:System.Linq.Enumerable.Repeat%2A><br />4.  <xref:System.Linq.Enumerable.ToDictionary%2A><br />5.  <xref:System.Linq.Enumerable.ToLookup%2A>|  
  
<a name="supportedExpressions"></a>   
## <a name="supported-expression-functions"></a>Desteklenen Ifade Işlevleri  
 Aşağıdaki ortak dil çalışma zamanı (CLR) yöntemleri ve özellikleri, bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] hizmete istek URI 'sine eklenmek üzere bir sorgu ifadesinde çevrilebilmesi için desteklenir:  
  
|<xref:System.String>Üyesidir|Desteklenen [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] işlev|  
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
  
|<xref:System.DateTime>Üye<sup>1</sup>|Desteklenen [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] işlev|  
|-------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.DateTime.Day>|`int day(DateTime p0)`|  
|<xref:System.DateTime.Hour>|`int hour(DateTime p0)`|  
|<xref:System.DateTime.Minute>|`int minute(DateTime p0)`|  
|<xref:System.DateTime.Month>|`int month(DateTime p0)`|  
|<xref:System.DateTime.Second>|`int second(DateTime p0)`|  
|<xref:System.DateTime.Year>|`int year(DateTime p0)`|  
  
 <sup>1</sup> <xref:Microsoft.VisualBasic.DateAndTime?displayProperty=nameWithType>' Deki <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> yöntemin ve saat özelliklerinin yanı sıra Visual Basic de desteklenir.  
  
|<xref:System.Math>Üyesidir|Desteklenen [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] işlev|  
|---------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Math.Ceiling%28System.Decimal%29>|`decimal ceiling(decimal p0)`|  
|<xref:System.Math.Ceiling%28System.Double%29>|`double ceiling(double p0)`|  
|<xref:System.Math.Floor%28System.Decimal%29>|`decimal floor(decimal p0)`|  
|<xref:System.Math.Floor%28System.Double%29>|`double floor(double p0)`|  
|<xref:System.Math.Round%28System.Decimal%29>|`decimal round(decimal p0)`|  
|<xref:System.Math.Round%28System.Double%29>|`double round(double p0)`|  
  
|<xref:System.Linq.Expressions.Expression>Üyesidir|Desteklenen [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] işlev|  
|---------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Linq.Expressions.Expression.TypeIs%28System.Linq.Expressions.Expression%2CSystem.Type%29>|`bool isof(type p0)`|  
  
 İstemci Ayrıca istemcideki ek CLR işlevlerini değerlendirebiliyor olabilir. , <xref:System.NotSupportedException> İstemcide değerlendirilemeyen herhangi bir ifade için oluşturulur ve sunucuda değerlendirme için geçerli bir istek URI 'sine çevrilemez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmetini Sorgulama](querying-the-data-service-wcf-data-services.md)
- [Sorgu Projeksiyonları](query-projections-wcf-data-services.md)
- [Nesne Gerçekleştirme](object-materialization-wcf-data-services.md)
- [OData URI kuralları](https://go.microsoft.com/fwlink/?LinkID=185564)
