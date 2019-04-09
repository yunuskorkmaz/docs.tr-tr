---
title: Hizmet işlemleri çağırma (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1767f3a7-29d2-4834-a763-7d169693fa8b
ms.openlocfilehash: 5ef00861624531e68ad5b8a3b080810040ae3ff6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109479"
---
# <a name="calling-service-operations-wcf-data-services"></a>Hizmet işlemleri çağırma (WCF Data Services)
[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Veri hizmeti için hizmet işlemleri tanımlar. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Bu işlemler veri hizmetinde yöntemler olarak tanımlamanızı sağlar. Diğer veri hizmeti kaynaklarına gibi bu hizmet işlemleri URI'ler kullanarak ele alınır. Bir hizmet işlemi, ilkel türler, tamsayı ve dize gibi varlık türleri ve tek bir varlık türü örnekleri koleksiyonunu döndürebilir. Bir hizmet işlemi ayrıca döndürebilir `null` (`Nothing` Visual Basic'te). [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] İstemci kitaplığı, HTTP GET isteklerini destekleyen hizmet işlemlerine erişimi için kullanılabilir. Bu tür hizmet işlemleri sahip yöntemler olarak adlandırılır <xref:System.ServiceModel.Web.WebGetAttribute> uygulanır. Daha fazla bilgi için [hizmet işlemleri](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md).  
  
 Hizmet işlemleri uygulayan bir veri hizmeti tarafından döndürülen meta veriler sunulur [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. Meta verilerde, hizmet işlemleri olarak temsil edilmektedir `FunctionImport` öğeleri. Türü kesin belirlenmiş oluştururken <xref:System.Data.Services.Client.DataServiceContext>, bu öğe hizmet Başvurusu Ekle ve DataSvcUtil.exe araçlarını yoksay. Bu nedenle, bir yöntem bir hizmet işlemi doğrudan çağırmak için kullanılan bağlama bulmaz. Ancak, kullanmaya devam edebilirsiniz [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] şu iki yoldan biriyle hizmet işlemlerini aramak üzere istemci:  
  
-   Çağırarak <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> metodunda <xref:System.Data.Services.Client.DataServiceContext>, herhangi bir parametre ile birlikte hizmet işlemi URI'si sağlama. Bu yöntem, herhangi bir GET hizmet işlemi çağırmak için kullanılır.  
  
-   Kullanarak <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> metodunda <xref:System.Data.Services.Client.DataServiceContext> oluşturmak için bir <xref:System.Data.Services.Client.DataServiceQuery%601> nesne. Çağrılırken <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>, hizmet işlemi adını sağlanan `entitySetName` parametresi. Bu yöntem döndürür bir <xref:System.Data.Services.Client.DataServiceQuery%601> numaralandırılan ne zaman veya zaman hizmet işlemini çağırır nesne <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> yöntemi çağrılır. Bu yöntem bir koleksiyon döndüren GET hizmet işlemlerini aramak üzere kullanılır. Tek bir parametre kullanarak sağlanabilir <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> yöntemi. <xref:System.Data.Services.Client.DataServiceQuery%601> Bu yöntem tarafından döndürülen nesne daha oluşan karşı gibi herhangi bir sorgu nesnesi. Daha fazla bilgi için [veri hizmetini sorgulama](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
## <a name="considerations-for-calling-service-operations"></a>Hizmet işlemleri çağırma dikkat edilmesi gereken noktalar  
 Kullanırken aşağıdaki maddeler geçerlidir [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] hizmet işlemlerini aramak üzere istemci.  
  
-   Veri hizmetini zaman uyumsuz olarak erişirken, zaman uyumsuz eşdeğer kullanmalısınız <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> / <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A> yöntemlerde <xref:System.Data.Services.Client.DataServiceContext> veya <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> / <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> yöntemlerde <xref:System.Data.Services.Client.DataServiceQuery%601>.  
  
-   [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] İstemci kitaplığı, ilkel türler koleksiyonunu döndüren bir hizmet işlemi sonuçlardan depolanabildiği olamaz.  
  
-   [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] İstemci kitaplığı, çağıran sonrası hizmet işlemleri desteklemez. Bir HTTP POST tarafından çağrılan hizmet işlemleri kullanarak tanımlanmış <xref:System.ServiceModel.Web.WebInvokeAttribute> ile `Method="POST"` parametresi. Bir HTTP POST isteği'ni kullanarak bir hizmet işlemi çağırmak için kullanmanız gereken bir <xref:System.Net.HttpWebRequest>.  
  
-   Kullanamazsınız <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> varlık veya ilkel tür, tek bir sonuç döndürür veya birden fazla giriş parametresi gerektiren bir GET hizmet işlemi çağırmak için. Bunun yerine çağırmalıdır <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> yöntemi.  
  
-   Kesin tür belirtilmiş üzerinde bir genişletme yöntemi oluşturmayı göz önünde bulundurun <xref:System.Data.Services.Client.DataServiceContext> kullanan ya da araçları tarafından oluşturulan kısmi sınıf, <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> veya <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> bir hizmet işlemi çağrılacak yöntem. Bu, doğrudan bağlamdan hizmet işlemlerini aramak üzere sağlar. Daha fazla bilgi için bkz. blog gönderisine [hizmet işlemleri ve WCF Veri Hizmetleri istemci](https://go.microsoft.com/fwlink/?LinkId=215668).  
  
-   Kullanırken <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> bir hizmet işlemi çağırmak için istemci kitaplığını otomatik olarak sağlanan karakterleri kaçırır <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> "ve işareti" gibi ayrılmış karakterleri için yüzde kodlama yaparak (&) ve tek tırnak içinde kaçış dizeleri. Ancak, çağırdığınızda birini *yürütme* bir hizmet işlemi çağırmak için yöntem herhangi bir kullanıcı tarafından sağlanan dize değeri kaçış gerçekleştirmek unutmamanız gerekir. Tek tırnak içinde bir URI'leri tek tırnak işareti çiftleri olarak atlanır.  
  
## <a name="examples-of-calling-service-operations"></a>Hizmet işlemleri çağırma örnekleri  
 Bu bölüm aşağıdaki örnekleri kullanarak hizmet işlemlerini aramak üzere nasıl içerir [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemci kitaplığı:  
  
-   [Arama yürütme&lt;T&gt; varlıklar koleksiyonu döndürmek için](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecuteIQueryable)  
  
-   [CreateQuery kullanarak&lt;T&gt; varlıklar koleksiyonu döndürmek için](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#CreateQueryIQueryable)  
  
-   [Arama yürütme&lt;T&gt; tek bir varlık döndürmek için](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecuteSingleEntity)  
  
-   [Arama yürütme&lt;T&gt; basit değerlerin koleksiyonunu döndürmek için](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecutePrimitiveCollection)  
  
-   [Arama yürütme&lt;T&gt; temel tek bir değer döndürmek için](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecutePrimitiveValue)  
  
-   [Bir hizmet işlemi çağırmak veri döndürmez](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecuteVoid)  
  
-   [Bir hizmet işlemi zaman uyumsuz olarak çağırma](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecuteAsync)  
  
<a name="ExecuteIQueryable"></a>   
### <a name="calling-executet-to-return-a-collection-of-entities"></a>Arama yürütme\<T > varlıklar koleksiyonu döndürmek için  
 Aşağıdaki örnek bir dize parametresi alan GetOrdersByCity adlı bir hizmet işlemi çağırır `city` ve döndüren bir <xref:System.Linq.IQueryable%601>:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationiqueryable)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationiqueryable)]  
  
 Bu örnekte, bir koleksiyonu hizmet işlemi dönüşünden `Order` nesneleriyle ilgili `Order_Detail` nesneleri.  
  
<a name="CreateQueryIQueryable"></a>   
### <a name="using-createqueryt-to-return-a-collection-of-entities"></a>CreateQuery kullanarak\<T > varlıklar koleksiyonu döndürmek için  
 Aşağıdaki örnekte <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> döndürülecek bir <xref:System.Data.Services.Client.DataServiceQuery%601> aynı GetOrdersByCity hizmet işlemini çağırmak için kullanılır:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationcreatequery)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationcreatequery)]  
  
 Bu örnekte, <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> yöntemi parametre sorguya eklemek için kullanılır ve <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> yöntemi sonuçlarında ilgili Order_Details nesneler için kullanılır.  
  
<a name="ExecuteSingleEntity"></a>   
### <a name="calling-executet-to-return-a-single-entity"></a>Arama yürütme\<T > tek bir varlık döndürmek için  
 Aşağıdaki örnek, tek bir sipariş varlık döndüren GetNewestOrder adlı bir hizmet işlemi çağırır:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationsingleentity)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationsingleentity)]  
  
 Bu örnekte, <xref:System.Linq.Enumerable.FirstOrDefault%2A> yöntemi yalnızca tek bir sipariş varlığı temel yürütme istemek için kullanılır.  
  
<a name="ExecutePrimitiveCollection"></a>   
### <a name="calling-executet-to-return-a-collection-of-primitive-values"></a>Arama yürütme\<T > basit değerlerin koleksiyonunu döndürmek için  
 Aşağıdaki örnekte, dize değerlerinin koleksiyonunu döndüren bir hizmet işlemi çağırır:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationEnumString](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationenumstring)]  
  
<a name="ExecutePrimitiveValue"></a>   
### <a name="calling-executet-to-return-a-single-primitive-value"></a>Arama yürütme\<T > temel tek bir değer döndürmek için  
 Aşağıdaki örnek, tek bir dize değerini döndüren bir hizmet işlemi çağırır:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationsingleint)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationsingleint)]  
  
 Bu örnek içinde yeniden <xref:System.Linq.Enumerable.FirstOrDefault%2A> yöntemi yalnızca tek bir tamsayı değeri yürütme istemek için kullanılır.  
  
<a name="ExecuteVoid"></a>   
### <a name="calling-a-service-operation-that-returns-no-data"></a>Bir hizmet işlemi çağırmak veri döndürmez  
 Aşağıdaki örnek veri döndüren bir hizmet işlemi çağırır:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationvoid)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationvoid)]  
  
 Değil veri döndürdüğünden, yürütme değer atanmadı. İstek başarılı oldu tek belirti olan hiçbir <xref:System.Data.Services.Client.DataServiceQueryException> tetiklenir.  
  
<a name="ExecuteAsync"></a>   
### <a name="calling-a-service-operation-asynchronously"></a>Bir hizmet işlemi zaman uyumsuz olarak çağırma  
 Aşağıdaki örnek çağırarak bir hizmet işlemi zaman uyumsuz olarak çağırır. <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> ve <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#onasyncexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#onasyncexecutioncomplete)]  
  
 Hiçbir veri döndürdüğünden, yürütme tarafından döndürülen değer atanmadı. İstek başarılı oldu tek belirti olan hiçbir <xref:System.Data.Services.Client.DataServiceQueryException> tetiklenir.  
  
 Aşağıdaki örnek kullanarak aynı hizmet işlemi zaman uyumsuz olarak çağırır. <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationqueryasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationqueryasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#onasyncqueryexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#onasyncqueryexecutioncomplete)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
