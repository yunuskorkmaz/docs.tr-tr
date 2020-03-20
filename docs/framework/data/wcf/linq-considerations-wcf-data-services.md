---
title: LINQ Hususlar (WCF Veri Hizmetleri)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ
- querying the data service [WCF Data Services]
- WCF Data Services, querying
ms.assetid: cc4ec9e9-348f-42a6-a78e-1cd40e370656
ms.openlocfilehash: 6c0cd7dcebb46b5408079848862ef4da1bb7f0a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174673"
---
# <a name="linq-considerations-wcf-data-services"></a>LINQ Hususlar (WCF Veri Hizmetleri)
Bu konu, WCF Veri Hizmetleri istemcisini kullanırken LINQ sorgularının oluşturulup yürütülme şekli ve Açık Veri Protokolü 'nü (OData) uygulayan bir veri hizmetini sorgulamak için LINQ kullanma sınırlamaları hakkında bilgi sağlar. OData tabanlı bir veri hizmetine karşı sorgu oluşturma ve yürütme hakkında daha fazla bilgi için [bkz.](querying-the-data-service-wcf-data-services.md)  
  
## <a name="composing-linq-queries"></a>LINQ Sorgularını Oluşturma  
 LINQ, uygulayan nesneler koleksiyonuna karşı sorgu lar oluşturmanıza <xref:System.Collections.Generic.IEnumerable%601>olanak tanır. Visual Studio'daki **Hizmet Başvurusu Ekle** iletişim kutusu ve DataSvcUtil.exe aracı, bir OData hizmetinin, akışlarında <xref:System.Data.Services.Client.DataServiceContext>döndürülen varlıkları temsil eden nesneleri devralan bir varlık kapsayıcı sınıfı olarak temsil etmek için kullanılır. Bu araçlar, hizmet tarafından akış olarak ortaya çıkarılan koleksiyonlar için varlık kapsayıcı sınıfında özellikler de oluşturur. Veri hizmetini kapsülleyen sınıfın bu özelliklerinin her biri <xref:System.Data.Services.Client.DataServiceQuery%601>bir . <xref:System.Data.Services.Client.DataServiceQuery%601> Sınıf LINQ tarafından <xref:System.Linq.IQueryable%601> tanımlanan arabirimi uyguladığından, istemci kitaplığı tarafından yürütme deki veri hizmetine gönderilen bir sorgu isteği URI'sine çevrilen veri hizmeti tarafından açığa çıkarılan akışlara karşı bir LINQ sorgusu oluşturabilirsiniz.  
  
> [!IMPORTANT]
> LINQ sözdiziminde ifade edilen sorgu kümesi, OData veri hizmetleri tarafından kullanılan URI sözdiziminde etkinleştirilenlerden daha geniştir. Sorgu <xref:System.NotSupportedException> hedef veri hizmetinde bir URI eşlenemediğinde a yükseltilir. Daha fazla bilgi için bu konuda [desteklenmeyen LINQ Yöntemleri'ne](linq-considerations-wcf-data-services.md#unsupportedMethods) bakın.  
  
 Aşağıdaki örnek, navlun maliyeti `Orders` 30 TL'den fazla olan ve en son sevkiyat tarihinden başlayarak sonuçları sevkiyat tarihine göre sıralayan bir LINQ sorgusudur:  
  
[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqspecific)]
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqspecific)]
  
 Bu LINQ sorgusu Northwind tabanlı [quickstart](quickstart-wcf-data-services.md) veri hizmetikarşı yürütülür aşağıdaki sorgu URI tercüme edilir:  
  
```http
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30  
```  
  
 LINQ hakkında daha fazla bilgi için bkz: [Dil-Tümleşik Sorgu (LINQ) - C#](../../../csharp/programming-guide/concepts/linq/index.md) veya [Dil-Tümleşik Sorgu (LINQ) - Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md).  
  
 LINQ, önceki örnekte gösterilen dile özgü bildirimsorgusu sözdizimini ve standart sorgu işleçleri olarak bilinen bir dizi sorgu yöntemini kullanarak sorgu oluşturmanıza olanak tanır. Önceki örneğe eşdeğer bir sorgu, aşağıdaki örnekte gösterildiği gibi yalnızca yöntem tabanlı sözdizimi kullanılarak oluşturulabilir:  
  
[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqExpressionSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqexpressionspecific)]
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqExpressionSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqexpressionspecific)]
  
 WCF Veri Hizmetleri istemcisi, her iki türde oluşan sorguyu bir sorgu URI'sine çevirebilir ve sorgu yöntemlerini sorgu ifadesine ekleyerek linq sorgusunu genişletebilirsiniz. Linq sorgularını bir sorgu ifadesine veya bir <xref:System.Data.Services.Client.DataServiceQuery%601>, bir sorgu ifadesine yöntem sözdizimi ekleyerek oluşturduğunuzda, işlemler yöntemin çağrıldığı sırada URI sorgusuna eklenir. Bu, her sorgu <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> seçeneğini URI sorgusuna eklemek için arama yöntemine eşdeğerdir.  
  
## <a name="executing-linq-queries"></a>LINQ Sorgularını Yürütme  
 Sorguya eklendiğinde <xref:System.Linq.Enumerable.First%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> veya <xref:System.Linq.Enumerable.Single%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>, sorguya eklendiğinde, belirli LINQ sorgu yöntemleri, sorgunun yürütülmesine neden olur. Bir `foreach` döngü sırasında veya sorgu bir koleksiyona atandığında gibi sonuçlar örtülü olarak numaralandırıldığında da sorgu `List` yürütülür. Daha fazla bilgi için [Bkz. Veri Hizmetini Sorgulama.](querying-the-data-service-wcf-data-services.md)  
  
 İstemci iki bölümden bir LINQ sorgusu yürütür. Mümkün olduğunda, bir sorgudaki LINQ ifadeleri önce istemci üzerinde değerlendirilir ve ardından URI tabanlı bir sorgu oluşturulur ve hizmetteki verilere göre değerlendirilmek üzere veri hizmetine gönderilir. Daha fazla bilgi için, Veri Hizmetini Sorgulama bölümünde [Istemci ve Sunucu Yürütme](querying-the-data-service-wcf-data-services.md#executingQueries) [bölümüne](querying-the-data-service-wcf-data-services.md)bakın.  
  
 Bir LINQ sorgusu OData uyumlu bir sorgu URI'ye çevrilemiyorsa, yürütme denendiğinde bir özel durum yükseltilir. Daha fazla bilgi için [Bkz. Veri Hizmetini Sorgulama.](querying-the-data-service-wcf-data-services.md)  
  
## <a name="linq-query-examples"></a>LINQ Sorgu Örnekleri  
 Aşağıdaki bölümlerdeki örnekler, bir OData hizmetine karşı yürütülebilecek LINQ sorgu türlerini göstermektedir.  
  
<a name="filtering"></a>
### <a name="filtering"></a>Filtreleme  
 Bu bölümdeki LINQ sorgu örnekleri, hizmet tarafından döndürülen özet akışındaki verileri filtreler.  
  
 Aşağıdaki örnekler, yalnızca 30 TL'den büyük bir navlun maliyeti olan siparişlerin döndürülebilmeleri için döndürülen `Orders` varlıkları filtreleyen eşdeğer sorgulardır:  
  
- LINQ sorgu sözdizimini kullanma:  
  
[!code-csharp[Astoria Northwind Client#LinqWhereClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqwhereclausespecific)]
[!code-vb[Astoria Northwind Client#LinqWhereClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqwhereclausespecific)]
  
- LINQ sorgu yöntemlerini kullanma:  
  
[!code-csharp[Astoria Northwind Client#LinqWhereMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqwheremethodspecific)]
[!code-vb[Astoria Northwind Client#LinqWhereMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqwheremethodspecific)]
  
- URI sorgu `$filter` dize seçeneği:  
  
[!code-csharp[Astoria Northwind Client#ExplicitQueryWhereMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#explicitquerywheremethodspecific)]
[!code-vb[Astoria Northwind Client#ExplicitQueryWhereMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#explicitquerywheremethodspecific)]
  
 Önceki örneklerin tümü URI sorgusuna çevrilmiştir: `http://localhost:12345/northwind.svc/Orders()?$filter=Freight gt 30M`.  
  
<a name="sorting"></a>
### <a name="sorting"></a>Sıralama  
 Aşağıdaki örnekler, döndürülen verileri hem şirket adına hem de posta koduna göre sıralayan eşdeğer sorguları gösterir:  
  
- LINQ sorgu sözdizimini kullanma:  
  
[!code-csharp[Astoria Northwind Client#LinqOrderByClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqorderbyclausespecific)]
[!code-vb[Astoria Northwind Client#LinqOrderByClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqorderbyclausespecific)]
  
- LINQ sorgu yöntemlerini kullanma:  
  
[!code-csharp[Astoria Northwind Client#LinqOrderByMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqorderbymethodspecific)]
[!code-vb[Astoria Northwind Client#LinqOrderByMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqorderbymethodspecific)]
  
- URI sorgu `$orderby` dize seçeneği):  
  
[!code-csharp[Astoria Northwind Client#ExplicitQueryOrderByMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#explicitqueryorderbymethodspecific)]
[!code-vb[Astoria Northwind Client#ExplicitQueryOrderByMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#explicitqueryorderbymethodspecific)]
  
 Önceki örneklerin tümü URI sorgusuna çevrilmiştir: `http://localhost:12345/northwind.svc/Customers()?$orderby=CompanyName,PostalCode desc`.  
  
<a name="projection"></a>
### <a name="projection"></a>Yansıtma  
 Aşağıdaki örnekler, projenin verileri daha `CustomerAddress` dar türe döndürdene eşdeğer sorguları gösterir:  
  
- LINQ sorgu sözdizimini kullanma:  
  
[!code-csharp[Astoria Northwind Client#LinqSelectClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqselectclausespecific)]
[!code-vb[Astoria Northwind Client#LinqSelectClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqselectclausespecific)]
  
- LINQ sorgu yöntemlerini kullanma:  
  
[!code-csharp[Astoria Northwind Client#LinqSelectMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqselectmethodspecific)]
[!code-vb[Astoria Northwind Client#LinqSelectMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqselectmethodspecific)]

> [!NOTE]
> Sorgu `$select` seçeneği <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> yöntem kullanılarak bir sorgu URI eklenemez. İstemci URI'de <xref:System.Linq.Enumerable.Select%2A> `$select` sorgu seçeneğini oluşturmak için LINQ yöntemini kullanmanızı öneririz.  
  
 Önceki örneklerin her ikisi de uri `"http://localhost:12345/northwind.svc/Customers()?$filter=Country eq 'GerGerm'&$select=CustomerID,Address,City,Region,PostalCode,Country"`sorgusuna çevrilmiştir: .  
  
<a name="paging"></a>
### <a name="client-paging"></a>İstemci Sayfalama  
 Aşağıdaki örnekler, ilk 50 siparişi atlayarak 25 sipariş içeren sıralanmış sipariş varlıklarından oluşan bir sayfa isteyen eşdeğer sorguları gösterir:  
  
- Linq sorgusuna sorgu yöntemleri nin uygulanması:  
  
[!code-csharp[Astoria Northwind Client#LinqSkipTakeMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqskiptakemethodspecific)]
[!code-vb[Astoria Northwind Client#LinqSkipTakeMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqskiptakemethodspecific)]
  
- URI sorgu `$skip` `$top` dizesi ve seçenekleri):  
  
[!code-csharp[Astoria Northwind Client#ExplicitQuerySkipTakeMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#explicitqueryskiptakemethodspecific)]
[!code-vb[Astoria Northwind Client#ExplicitQuerySkipTakeMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#explicitqueryskiptakemethodspecific)]
  
 Önceki örneklerin her ikisi de uri `http://localhost:12345/northwind.svc/Orders()?$orderby=OrderDate desc&$skip=50&$top=25`sorgusuna çevrilmiştir: .  
  
<a name="expand"></a>
### <a name="expand"></a>Genişlet  
 Bir OData veri hizmetini sorgularken, sorgu tarafından hedeflenen varlıkla ilgili varlıkların iade edilen özet akışına eklenmesini isteyebilirsiniz. Yöntem, <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> linq <xref:System.Data.Services.Client.DataServiceQuery%601> sorgusu tarafından hedeflenen varlık kümesi için çağrılır ve ilgili varlık `path` kümesi adı parametre olarak verilir. Daha fazla bilgi için [bkz.](loading-deferred-content-wcf-data-services.md)  
  
 Aşağıdaki örnekler, bir sorguda <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> yöntemi kullanmanın eşdeğer yollarını gösterir:  
  
- LINQ sorgusunda sözdiziminde:  
  
[!code-csharp[Astoria Northwind Client#LinqQueryExpandSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqqueryexpandspecific)]
[!code-vb[Astoria Northwind Client#LinqQueryExpandSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqqueryexpandspecific)]  
  
- LINQ sorgu yöntemleri ile:  

[!code-csharp[Astoria Northwind Client#LinqQueryExpandMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqqueryexpandmethodspecific)]
[!code-vb[Astoria Northwind Client#LinqQueryExpandMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqqueryexpandmethodspecific)]

 Önceki örneklerin her ikisi de uri `http://localhost:12345/northwind.svc/Orders()?$filter=CustomerID eq 'ALFKI'&$expand=Order_Details`sorgusuna çevrilmiştir: .  
  
<a name="unsupportedMethods"></a>
## <a name="unsupported-linq-methods"></a>Desteklenmeyen LINQ Yöntemleri  
 Aşağıdaki tablo, LINQ yöntemlerinin desteklenmediğini ve bir OData hizmetine karşı yürütülen bir sorguya dahil edilemeyeceğini içerir:  
  
|İşlem Türü|Desteklenmeyen Yöntem|  
|--------------------|------------------------|  
|Operatörleri ayarla|Tüm set işleçleri, <xref:System.Data.Services.Client.DataServiceQuery%601>aşağıdakileri içeren bir , karşı desteklenmez:<br /><br /> -   <xref:System.Linq.Enumerable.All%2A><br />-   <xref:System.Linq.Enumerable.Any%2A><br />-   <xref:System.Linq.Enumerable.Concat%2A><br />-   <xref:System.Linq.Enumerable.DefaultIfEmpty%2A><br />-   <xref:System.Linq.Enumerable.Distinct%2A><br />-   <xref:System.Linq.Enumerable.Except%2A><br />-   <xref:System.Linq.Enumerable.Intersect%2A><br />-   <xref:System.Linq.Enumerable.Union%2A><br />-   <xref:System.Linq.Enumerable.Zip%2A>|  
|Sipariş operatörleri|Aşağıdaki sipariş işleçleri <xref:System.Collections.Generic.IComparer%601> aşağıdaki karşı <xref:System.Data.Services.Client.DataServiceQuery%601>desteklenmeyen:<br /><br /> -   <xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29>|  
|Projeksiyon ve filtreleme operatörleri|Konumsal bağımsız değişkeni kabul eden aşağıdaki projeksiyon ve filtreleme işleçleri <xref:System.Data.Services.Client.DataServiceQuery%601>aşağıdakiler karşı desteklenmez:<br /><br /> -   <xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%2CSystem.Collections.Generic.IEqualityComparer%7B%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2C%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Where%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Boolean%7D%29>|  
|Gruplandırma operatörleri|Tüm gruplandırma işleçleri, <xref:System.Data.Services.Client.DataServiceQuery%601>aşağıdakiler de dahil olmak üzere aşağıdakiler de dahil olmak üzere aşağıdakiler arasında desteklenmeyen bir<br /><br /> -   <xref:System.Linq.Enumerable.GroupBy%2A><br />-   <xref:System.Linq.Enumerable.GroupJoin%2A><br /><br /> Gruplandırma işlemleri istemci üzerinde gerçekleştirilmelidir.|  
|Toplam işleçler|Tüm toplu işlemler, aşağıdakiler <xref:System.Data.Services.Client.DataServiceQuery%601>de dahil olmak üzere bir karşı desteklenmez:<br /><br /> -   <xref:System.Linq.Enumerable.Aggregate%2A><br />-   <xref:System.Linq.Enumerable.Average%2A><br />-   <xref:System.Linq.Enumerable.Count%2A><br />-   <xref:System.Linq.Enumerable.LongCount%2A><br />-   <xref:System.Linq.Enumerable.Max%2A><br />-   <xref:System.Linq.Enumerable.Min%2A><br />-   <xref:System.Linq.Enumerable.Sum%2A><br /><br /> Toplam işlemler istemci üzerinde yapılmalı veya bir hizmet işlemi tarafından kapsüllenmelidir.|  
|Sayfalama operatörleri|Aşağıdaki çağrı operatörleri aşağıdaki <xref:System.Data.Services.Client.DataServiceQuery%601>ler arasında desteklenmez:<br /><br /> -   <xref:System.Linq.Enumerable.ElementAt%2A><br />-   <xref:System.Linq.Enumerable.Last%2A><br />-   <xref:System.Linq.Enumerable.LastOrDefault%2A><br />-   <xref:System.Linq.Enumerable.SkipWhile%2A><br />-   <xref:System.Linq.Enumerable.TakeWhile%2A><br/><br/>**Not:**  Boş bir sıra üzerinde çalıştırılan sayfalama işleçleri null döndürün.|  
|Diğer operatörler|Aşağıdaki işleçler de aşağıdaki <xref:System.Data.Services.Client.DataServiceQuery%601>karşı desteklenmez:<br /><br /> - <xref:System.Linq.Enumerable.Empty%2A><br />- <xref:System.Linq.Enumerable.Range%2A><br />- <xref:System.Linq.Enumerable.Repeat%2A><br />- <xref:System.Linq.Enumerable.ToDictionary%2A><br />- <xref:System.Linq.Enumerable.ToLookup%2A>|  
  
<a name="supportedExpressions"></a>
## <a name="supported-expression-functions"></a>Desteklenen İfade Fonksiyonları  
 Aşağıdaki ortak dil çalışma zamanı (CLR) yöntemleri ve özellikleri desteklenir, çünkü bunlar bir OData hizmetine uri isteğine dahil edilmesi için bir sorgu ifadesine çevrilebilir:  
  
|<xref:System.String>Üye|Desteklenen OData Fonksiyonu|  
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
  
|<xref:System.DateTime>Üye<sup>1</sup>|Desteklenen OData Fonksiyonu|  
|-------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.DateTime.Day>|`int day(DateTime p0)`|  
|<xref:System.DateTime.Hour>|`int hour(DateTime p0)`|  
|<xref:System.DateTime.Minute>|`int minute(DateTime p0)`|  
|<xref:System.DateTime.Month>|`int month(DateTime p0)`|  
|<xref:System.DateTime.Second>|`int second(DateTime p0)`|  
|<xref:System.DateTime.Year>|`int year(DateTime p0)`|  
  
 <sup>1.1.2</sup> Visual Basic'teki <xref:Microsoft.VisualBasic.DateAndTime?displayProperty=nameWithType> <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> eşdeğer tarih ve saat özellikleri ve yöntemi de desteklenir.  
  
|<xref:System.Math>Üye|Desteklenen OData Fonksiyonu|  
|---------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Math.Ceiling%28System.Decimal%29>|`decimal ceiling(decimal p0)`|  
|<xref:System.Math.Ceiling%28System.Double%29>|`double ceiling(double p0)`|  
|<xref:System.Math.Floor%28System.Decimal%29>|`decimal floor(decimal p0)`|  
|<xref:System.Math.Floor%28System.Double%29>|`double floor(double p0)`|  
|<xref:System.Math.Round%28System.Decimal%29>|`decimal round(decimal p0)`|  
|<xref:System.Math.Round%28System.Double%29>|`double round(double p0)`|  
  
|<xref:System.Linq.Expressions.Expression>Üye|Desteklenen OData Fonksiyonu|  
|---------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Linq.Expressions.Expression.TypeIs%28System.Linq.Expressions.Expression%2CSystem.Type%29>|`bool isof(type p0)`|  
  
 İstemci ayrıca istemci üzerinde ek CLR işlevlerini değerlendirmek mümkün olabilir. A <xref:System.NotSupportedException> istemci üzerinde değerlendirilemez ve sunucuda değerlendirme için geçerli bir istek URI çevrilemez herhangi bir ifade için yükseltilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmetini Sorgulama](querying-the-data-service-wcf-data-services.md)
- [Sorgu Projeksiyonları](query-projections-wcf-data-services.md)
- [Nesne Gerçekleştirme](object-materialization-wcf-data-services.md)
- [OData: URI Kuralları](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/)
