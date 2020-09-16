---
title: Hizmet Işlemlerini çağırma (WCF Veri Hizmetleri)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1767f3a7-29d2-4834-a763-7d169693fa8b
ms.openlocfilehash: 63c6e903fa811d5c61550d086b4f1ce84973f2bc
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553629"
---
# <a name="calling-service-operations-wcf-data-services"></a>Hizmet Işlemlerini çağırma (WCF Veri Hizmetleri)
Açık Veri Protokolü (OData), bir veri hizmeti için hizmet işlemlerini tanımlar. WCF Veri Hizmetleri, bu işlemleri veri hizmetindeki yöntemler olarak tanımlamanızı sağlar. Diğer veri hizmeti kaynakları gibi bu hizmet işlemleri de URI 'Ler kullanılarak karşılanır. Bir hizmet işlemi varlık türleri, tek varlık türü örnekleri ve tamsayı ve dize gibi basit türler için Koleksiyonlar döndürebilir. Ayrıca, bir hizmet işlemi de döndürebilir `null` ( `Nothing` Visual Basic). WCF Veri Hizmetleri istemci kitaplığı, HTTP GET isteklerini destekleyen hizmet işlemlerine erişmek için kullanılabilir. Bu tür hizmet işlemleri, uygulanmış olan yöntemler olarak tanımlanır <xref:System.ServiceModel.Web.WebGetAttribute> . Daha fazla bilgi için bkz. [hizmet işlemleri](service-operations-wcf-data-services.md).  
  
 Hizmet işlemleri, OData 'i uygulayan bir veri hizmeti tarafından döndürülen meta verilerde gösterilir. Meta verilerde, hizmet işlemleri öğeler olarak temsil edilir `FunctionImport` . Türü kesin belirlenmiş bir oluşturma sırasında <xref:System.Data.Services.Client.DataServiceContext> , hizmet başvurusu Ekle ve DataSvcUtil.exe araçları bu öğeyi yoksayar. Bu nedenle, bir hizmet işlemini doğrudan çağırmak için kullanılabilen bağlamda bir yöntem bulamacaksınız. Ancak, bu iki şekilde hizmet işlemlerini çağırmak için WCF Veri Hizmetleri istemcisini kullanmaya devam edebilirsiniz:  
  
- <xref:System.Data.Services.Client.DataServiceContext.Execute%2A>Üzerinde yöntemini çağırarak, <xref:System.Data.Services.Client.DataServiceContext> HIZMET işleminin URI 'sini, tüm parametrelerle birlikte sağlayarak. Bu yöntem, tüm hizmet Al işlemlerini çağırmak için kullanılır.  
  
- <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> <xref:System.Data.Services.Client.DataServiceContext> Bir nesnesi oluşturmak için üzerinde yöntemini kullanarak <xref:System.Data.Services.Client.DataServiceQuery%601> . Çağrılırken <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> , hizmet işleminin adı `entitySetName` parametreye sağlanır. Bu yöntem <xref:System.Data.Services.Client.DataServiceQuery%601> , ya da yöntemi çağrıldığında hizmet işlemini çağıran bir nesne döndürür <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> . Bu yöntem, bir koleksiyon döndüren GET hizmeti işlemlerini çağırmak için kullanılır. Yöntemi kullanılarak tek bir parametre sağlanabilir <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> . <xref:System.Data.Services.Client.DataServiceQuery%601>Bu yöntemin döndürdüğü nesne, herhangi bir sorgu nesnesi gibi daha fazla bulunabilir. Daha fazla bilgi için bkz. [veri hizmetini sorgulama](querying-the-data-service-wcf-data-services.md).  
  
## <a name="considerations-for-calling-service-operations"></a>Hizmet Işlemlerini çağırma konuları  
 Aşağıdaki noktalar, hizmet işlemlerini çağırmak için WCF Veri Hizmetleri istemcisi kullanılırken geçerlidir.  
  
- Veri hizmetine zaman uyumsuz olarak erişirken, üzerinde eşdeğer zaman uyumsuz <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> / <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A> yöntemleri <xref:System.Data.Services.Client.DataServiceContext> veya <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> / <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> üzerindeki yöntemleri <xref:System.Data.Services.Client.DataServiceQuery%601> kullanmanız gerekir.  
  
- WCF Veri Hizmetleri istemci kitaplığı, temel türlerin bir koleksiyonunu döndüren bir hizmet işleminden sonuçları yürütülemiyor.  
  
- WCF Veri Hizmetleri istemci kitaplığı, hizmet gönderme işlemlerinin çağrılmasını desteklemez. Bir HTTP POST tarafından çağrılan hizmet işlemleri parametresiyle kullanılarak tanımlanır <xref:System.ServiceModel.Web.WebInvokeAttribute> `Method="POST"` . Bir HTTP POST isteği kullanarak bir hizmet işlemini çağırmak için, bunun yerine bir kullanmalısınız <xref:System.Net.HttpWebRequest> .  
  
- <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>Tek bir sonuç döndüren veya birden fazla giriş parametresi gerektiren BIR Get hizmeti işlemini çağırmak için kullanamazsınız. Bunun yerine yöntemini çağırmanız gerekir <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> .  
  
- Araç tarafından oluşturulan kesin türü belirtilmiş kısmi sınıfta bir genişletme yöntemi oluşturmayı düşünün <xref:System.Data.Services.Client.DataServiceContext> . Bu, <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> bir hizmet işlemini çağırmak için ya da yöntemini kullanır. Bu, hizmet işlemlerini doğrudan bağlamdan çağırmanızı sağlar. Daha fazla bilgi için bkz. Blog Post [hizmeti işlemleri ve WCF veri Hizmetleri istemcisi](/archive/blogs/astoriateam/service-operations-and-the-wcf-data-services-client).  
  
- <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>Bir hizmet işlemini çağırmak için kullandığınızda, istemci kitaplığı, <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> ampersan (&) ve dizelerde tek tırnak işareti gibi ayrılmış karakterlerin yüzde kodlaması gerçekleştirerek otomatik olarak öğesine verilen karakterleri çıkar. Ancak, bir hizmet işlemini çağırmak için *Execute* yöntemlerinden birini çağırdığınızda, Kullanıcı tarafından sağlanan herhangi bir dize değerinin bu kaçışı gerçekleştirmeyi unutmamanız gerekir. URI 'Lerinde tek tırnak işareti, tek tırnak çifti olarak atlardır.  
  
## <a name="examples-of-calling-service-operations"></a>Hizmet Işlemlerini çağırma örnekleri  
 Bu bölüm, WCF Veri Hizmetleri istemci kitaplığını kullanarak hizmet işlemlerini çağırma hakkında aşağıdaki örnekleri içerir:  
  
- [&lt; &gt; Bir varlık koleksiyonu döndürmek için Execute T çağrılıyor](calling-service-operations-wcf-data-services.md#ExecuteIQueryable)  
  
- [&lt; &gt; Bir varlık koleksiyonu döndürmek Için CreateQuery T kullanma](calling-service-operations-wcf-data-services.md#CreateQueryIQueryable)  
  
- [&lt; &gt; Tek bir varlık döndürmek için Execute T çağrılıyor](calling-service-operations-wcf-data-services.md#ExecuteSingleEntity)  
  
- [&lt; &gt; Temel değerlerin bir koleksiyonunu döndürmek için Execute T çağrılıyor](calling-service-operations-wcf-data-services.md#ExecutePrimitiveCollection)  
  
- [&lt; &gt; Tek bir temel değer döndürmek için Execute T çağrılıyor](calling-service-operations-wcf-data-services.md#ExecutePrimitiveValue)  
  
- [Veri döndüren bir hizmet Işlemi çağırma](calling-service-operations-wcf-data-services.md#ExecuteVoid)  
  
- [Hizmet Işlemi zaman uyumsuz olarak çağrılıyor](calling-service-operations-wcf-data-services.md#ExecuteAsync)  
  
<a name="ExecuteIQueryable"></a>
### <a name="calling-executet-to-return-a-collection-of-entities"></a>\<T>Bir varlık koleksiyonu döndürmek Için Execute çağrılıyor  
 Aşağıdaki örnek, bir dize parametresi alan ve bir döndüren GetOrdersByCity adlı bir hizmet işlemini çağırır `city` <xref:System.Linq.IQueryable%601> :  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationiqueryable)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationiqueryable)]  
  
 Bu örnekte, hizmet işlemi `Order` ilgili nesneler içeren bir nesne koleksiyonu döndürür `Order_Detail` .  
  
<a name="CreateQueryIQueryable"></a>
### <a name="using-createqueryt-to-return-a-collection-of-entities"></a>\<T>Bir varlık koleksiyonu döndürmek Için CreateQuery kullanma  
 Aşağıdaki örnek, <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> <xref:System.Data.Services.Client.DataServiceQuery%601> aynı GetOrdersByCity hizmeti işlemini çağırmak için kullanılan öğesini döndürmek için öğesini kullanır:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationcreatequery)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationcreatequery)]  
  
 Bu örnekte, <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> parametresini sorguya eklemek için yöntemi kullanılır ve bu <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> Yöntem, sonuçlarda ilgili Order_Details nesneleri dahil etmek için kullanılır.  
  
<a name="ExecuteSingleEntity"></a>
### <a name="calling-executet-to-return-a-single-entity"></a>Execute, \<T> tek bir varlık döndürmek için çağrılıyor  
 Aşağıdaki örnek, yalnızca tek bir sipariş varlığı döndüren GetNewestOrder adlı bir hizmet işlemini çağırır:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationsingleentity)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationsingleentity)]  
  
 Bu örnekte, <xref:System.Linq.Enumerable.FirstOrDefault%2A> yöntemi yürütme sırasında yalnızca tek bir sipariş varlığı istemek için kullanılır.  
  
<a name="ExecutePrimitiveCollection"></a>
### <a name="calling-executet-to-return-a-collection-of-primitive-values"></a>\<T>Temel değerlerin bir koleksiyonunu döndürmek Için Execute çağrılıyor  
 Aşağıdaki örnek, bir dize değerleri koleksiyonu döndüren bir hizmet işlemini çağırır:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationEnumString](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationenumstring)]  
  
<a name="ExecutePrimitiveValue"></a>
### <a name="calling-executet-to-return-a-single-primitive-value"></a>Execute, \<T> tek bir temel değer döndürmek için çağrılıyor  
 Aşağıdaki örnek, tek bir dize değeri döndüren bir hizmet işlemini çağırır:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationsingleint)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationsingleint)]  
  
 Bu örnekte, <xref:System.Linq.Enumerable.FirstOrDefault%2A> yöntemi yürütme sırasında yalnızca tek bir tamsayı değeri istemek için kullanılır.  
  
<a name="ExecuteVoid"></a>
### <a name="calling-a-service-operation-that-returns-no-data"></a>Veri döndüren bir hizmet Işlemi çağırma  
 Aşağıdaki örnek, veri döndüren bir hizmet işlemini çağırır:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationvoid)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationvoid)]  
  
 Veriler döndürülmediği için yürütmenin değeri atanmadı. İsteğin başarılı olduğu tek işaret, hiçbir değer <xref:System.Data.Services.Client.DataServiceQueryException> çıkarılmadığını belirtir.  
  
<a name="ExecuteAsync"></a>
### <a name="calling-a-service-operation-asynchronously"></a>Hizmet Işlemi zaman uyumsuz olarak çağrılıyor  
 Aşağıdaki örnek, ve çağırarak zaman uyumsuz olarak bir hizmet işlemi çağırır <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A> :  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onasyncexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onasyncexecutioncomplete)]  
  
 Hiçbir veri döndürülmediği için, yürütme tarafından döndürülen değer atanmadı. İsteğin başarılı olduğu tek işaret, hiçbir değer <xref:System.Data.Services.Client.DataServiceQueryException> çıkarılmadığını belirtir.  
  
 Aşağıdaki örnek kullanarak aynı hizmet işlemini zaman uyumsuz olarak çağırır <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> :  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationqueryasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationqueryasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onasyncqueryexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onasyncqueryexecutioncomplete)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
