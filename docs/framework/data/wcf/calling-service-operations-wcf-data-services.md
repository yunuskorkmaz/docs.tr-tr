---
title: Arama hizmet işlemleri (WCF Veri Hizmetleri)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1767f3a7-29d2-4834-a763-7d169693fa8b
ms.openlocfilehash: 82bba149f06fc68f2f01e0e7641d98ebb861dbe6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="calling-service-operations-wcf-data-services"></a>Arama hizmet işlemleri (WCF Veri Hizmetleri)
[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Veri hizmeti için hizmet işlemleri tanımlar. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] veri hizmeti yöntemi olarak gibi işlemleri tanımlamanızı sağlar. Veri Hizmeti kaynaklar gibi hizmet işlemlerini URI kullanılarak ele alınır. Bir hizmet işlemi, varlık türleri, tek bir varlık türü örnekleri ve tamsayı ve dize gibi basit türler koleksiyonlarının geri dönebilirsiniz. Bir hizmet işlemi de döndürebilir `null` (`Nothing` Visual Basic'te). [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] İstemci kitaplığı, HTTP GET isteklerini destekleyen hizmet işlemleri erişmek için kullanılabilir. Bu tür hizmet işlemleri sahip yöntemleri olarak tanımlanan <xref:System.ServiceModel.Web.WebGetAttribute> uygulanır. Daha fazla bilgi için bkz: [hizmet işlemleri](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md).  
  
 Hizmet işlemleri uygulayan bir veri hizmeti tarafından döndürülen meta verilerde açığa [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. Meta verilerde hizmet işlemleri olarak temsil edilir `FunctionImport` öğeleri. Kesin türü belirtilmiş oluştururken <xref:System.Data.Services.Client.DataServiceContext>, bu öğe hizmet Başvurusu Ekle ve DataSvcUtil.exe araçları yoksay. Bu nedenle, bir yöntem bir hizmet işlemi doğrudan çağırmak için kullanılabilecek bağlamda bulamaz. Ancak, kullanmaya devam edebilirsiniz [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] bu iki yoldan biriyle hizmet işlemlerini çağırma istemci:  
  
-   Çağırarak <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> yöntemi <xref:System.Data.Services.Client.DataServiceContext>, herhangi bir parametre birlikte hizmet işlemi URI'sini belirtin. Bu yöntem, herhangi bir GET hizmeti işlem çağırmak için kullanılır.  
  
-   Kullanarak <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> yöntemi <xref:System.Data.Services.Client.DataServiceContext> oluşturmak için bir <xref:System.Data.Services.Client.DataServiceQuery%601> nesnesi. Çağrılırken <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>, hizmet işlemi ad için sağlanan `entitySetName` parametresi. Bu yöntem bir <xref:System.Data.Services.Client.DataServiceQuery%601> veya numaralandırılmış zaman hizmet işlemini çağırır nesne <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> yöntemi çağrılır. Bu yöntem, bir koleksiyonu GET hizmet işlemleri çağırmak için kullanılır. Tek bir parametre kullanarak sağlanabilir <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> yöntemi. <xref:System.Data.Services.Client.DataServiceQuery%601> Bu yöntem tarafından döndürülen nesne daha fazla birleştirilebilen karşı gibi herhangi bir sorgu nesnesi. Daha fazla bilgi için bkz: [veri hizmeti sorgulanırken](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
## <a name="considerations-for-calling-service-operations"></a>Hizmet işlemlerini çağırma dikkat edilmesi gereken noktalar  
 Kullanırken aşağıdaki maddeler geçerlidir [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemci hizmet işlemlerini çağırma.  
  
-   Veri hizmeti zaman uyumsuz olarak erişirken zaman uyumsuz eşdeğer kullanmalısınız <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> / <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A> yöntemlere <xref:System.Data.Services.Client.DataServiceContext> veya <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> / <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> yöntemlere <xref:System.Data.Services.Client.DataServiceQuery%601>.  
  
-   [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] İstemci kitaplığı ilkel türler koleksiyonu döndüren bir hizmet işlemi sonuçlarından gerçekleştirmeye olamaz.  
  
-   [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] İstemci Kitaplığı arama POST hizmet işlemleri desteklemez. Bir HTTP POST tarafından çağrılan hizmet işlemleri kullanarak tanımlanmış <xref:System.ServiceModel.Web.WebInvokeAttribute> ile `Method="POST"` parametresi. Bir HTTP POST isteği kullanarak bir hizmet işlemi çağırmak için bunun yerine kullanmanız gerekir bir <xref:System.Net.HttpWebRequest>.  
  
-   Kullanamazsınız <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> varlık veya ilkel tür, tek bir sonuç döndürür veya birden fazla giriş parametresinin gerektiren bir GET hizmet işlemi çağırmak için. Bunun yerine çağırmalısınız <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> yöntemi.  
  
-   Kesin türü belirtilmiş üzerinde bir genişletme yöntemi oluşturmayı düşünün <xref:System.Data.Services.Client.DataServiceContext> ya da kullanan araçları tarafından oluşturulan, kısmi sınıfı, <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> veya <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> bir hizmet işlemi çağrılacak yöntem. Bu, hizmet işlemleri bağlamından doğrudan çağırmak sağlar. Daha fazla bilgi için blog gönderisine bakın [hizmet işlemleri ve WCF Veri Hizmetleri istemcisi](http://go.microsoft.com/fwlink/?LinkId=215668).  
  
-   Kullandığınızda <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> bir hizmet işlemi çağırmak için istemci kitaplığı otomatik olarak için sağlanan karakter çıkışları <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> ve işareti gibi ayrılmış karakterleri yüzde kodlama gerçekleştirerek (&) ve tek tırnak içinde kaçış dizeleri. Ancak, çağırdığınızda birini *yürütme* bir hizmet işlemi çağrılacak yöntemlerin herhangi bir kullanıcı tarafından sağlanan dize değeri kaçış gerçekleştirmek unutmamanız gerekir. Tek tırnak içinde URI'ler tek tırnak işareti çiftleri olarak atlanır.  
  
## <a name="examples-of-calling-service-operations"></a>Hizmet işlemlerini çağırma örnekleri  
 Bu bölüm, hizmet işlemleri kullanarak aramak aşağıdaki örnekleri içerir [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemci kitaplığı:  
  
-   [Arama yürütme&lt;T&gt; bir varlıklar koleksiyonu döndürmek için](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecuteIQueryable)  
  
-   [CreateQuery kullanarak&lt;T&gt; bir varlıklar koleksiyonu döndürmek için](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#CreateQueryIQueryable)  
  
-   [Arama yürütme&lt;T&gt; tek bir varlık döndürmek için](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecuteSingleEntity)  
  
-   [Arama yürütme&lt;T&gt; ilkel değerler koleksiyonu döndürmek için](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecutePrimitiveCollection)  
  
-   [Arama yürütme&lt;T&gt; tek bir İlkel değer döndürmek için](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecutePrimitiveValue)  
  
-   [Bir hizmet işlemi çağıran hiçbir veri döndürür](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecuteVoid)  
  
-   [Bir hizmet işlemi zaman uyumsuz olarak çağırma](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecuteAsync)  
  
<a name="ExecuteIQueryable"></a>   
### <a name="calling-executet-to-return-a-collection-of-entities"></a>Arama yürütme\<T > varlıklar koleksiyonu döndürmek için  
 Aşağıdaki örnek, bir dize parametresi alan GetOrdersByCity adlı bir hizmet işlemi çağırır `city` ve döndüren bir <xref:System.Linq.IQueryable%601>:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationiqueryable)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationiqueryable)]  
  
 Bu örnekte, hizmet işlemi koleksiyonunu döndürür `Order` nesneleriyle ilgili `Order_Detail` nesneleri.  
  
<a name="CreateQueryIQueryable"></a>   
### <a name="using-createqueryt-to-return-a-collection-of-entities"></a>CreateQuery kullanarak\<T > varlıklar koleksiyonu döndürmek için  
 Aşağıdaki örnek kullanır <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> döndürmek için bir <xref:System.Data.Services.Client.DataServiceQuery%601> aynı GetOrdersByCity hizmet işlemini çağırmak için kullanılır:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationcreatequery)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationcreatequery)]  
  
 Bu örnekte, <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> yöntemi parametreyi sorguya eklemek için kullanılır ve <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> yöntemi ilgili Order_Details nesneleri sonuçlara dahil etmek için kullanılır.  
  
<a name="ExecuteSingleEntity"></a>   
### <a name="calling-executet-to-return-a-single-entity"></a>Arama yürütme\<T > tek bir varlık döndürmek için  
 Aşağıdaki örnek, tek bir sipariş varlık döndüren GetNewestOrder adlı bir hizmet işlemi çağırır:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationsingleentity)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationsingleentity)]  
  
 Bu örnekte, <xref:System.Linq.Enumerable.FirstOrDefault%2A> yöntemi yalnızca tek bir sipariş varlıkta yürütme istemek için kullanılır.  
  
<a name="ExecutePrimitiveCollection"></a>   
### <a name="calling-executet-to-return-a-collection-of-primitive-values"></a>Arama yürütme\<T > ilkel değerler koleksiyonu döndürmek için  
 Aşağıdaki örnekte, dize değerleri koleksiyonunu döndürür bir hizmet işlemi çağırır:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationEnumString](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationenumstring)]  
  
<a name="ExecutePrimitiveValue"></a>   
### <a name="calling-executet-to-return-a-single-primitive-value"></a>Arama yürütme\<T > tek bir İlkel değer döndürmek için  
 Aşağıdaki örnek, tek bir dize değerini döndüren bir hizmet işlemi çağırır:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationsingleint)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationsingleint)]  
  
 Bu örnekte, içinde yeniden <xref:System.Linq.Enumerable.FirstOrDefault%2A> yöntemi yalnızca tek bir tamsayı değeri yürütme üzerinde istemek için kullanılır.  
  
<a name="ExecuteVoid"></a>   
### <a name="calling-a-service-operation-that-returns-no-data"></a>Bir hizmet işlemi çağıran hiçbir veri döndürür  
 Aşağıdaki örnek veri döndüren bir hizmet işlemi çağırır:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationvoid)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationvoid)]  
  
 Verileri değil döndürdüğünden yürütme değeri atanmadı. İstek başarılı oldu tek belirti olan hiçbir <xref:System.Data.Services.Client.DataServiceQueryException> tetiklenir.  
  
<a name="ExecuteAsync"></a>   
### <a name="calling-a-service-operation-asynchronously"></a>Bir hizmet işlemi zaman uyumsuz olarak çağırma  
 Aşağıdaki örnek çağırarak bir hizmet işlemi zaman uyumsuz olarak çağırır. <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> ve <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#onasyncexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#onasyncexecutioncomplete)]  
  
 Hiçbir veri döndürdüğünden yürütme tarafından döndürülen değer atanmadı. İstek başarılı oldu tek belirti olan hiçbir <xref:System.Data.Services.Client.DataServiceQueryException> tetiklenir.  
  
 Aşağıdaki örnek kullanarak aynı hizmet işlemini zaman uyumsuz olarak çağırır. <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationqueryasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationqueryasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#onasyncqueryexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#onasyncqueryexecutioncomplete)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
