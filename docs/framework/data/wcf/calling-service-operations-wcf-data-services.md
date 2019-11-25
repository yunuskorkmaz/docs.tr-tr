---
title: Hizmet Işlemlerini çağırma (WCF Veri Hizmetleri)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1767f3a7-29d2-4834-a763-7d169693fa8b
ms.openlocfilehash: a64a09195101cd4b1ec3c6f990dd09d54466aea0
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975409"
---
# <a name="calling-service-operations-wcf-data-services"></a>Hizmet Işlemlerini çağırma (WCF Veri Hizmetleri)
Açık Veri Protokolü (OData), bir veri hizmeti için hizmet işlemlerini tanımlar. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], bu işlemleri veri hizmetindeki yöntemler olarak tanımlamanızı sağlar. Diğer veri hizmeti kaynakları gibi bu hizmet işlemleri de URI 'Ler kullanılarak karşılanır. Bir hizmet işlemi varlık türleri, tek varlık türü örnekleri ve tamsayı ve dize gibi basit türler için Koleksiyonlar döndürebilir. Ayrıca, bir hizmet işlemi `null` (`Nothing` Visual Basic) döndürebilir. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemci kitaplığı, HTTP GET isteklerini destekleyen hizmet işlemlerine erişmek için kullanılabilir. Bu tür hizmet işlemleri, <xref:System.ServiceModel.Web.WebGetAttribute> uygulanmış yöntemler olarak tanımlanır. Daha fazla bilgi için bkz. [hizmet işlemleri](service-operations-wcf-data-services.md).  
  
 Hizmet işlemleri, OData 'i uygulayan bir veri hizmeti tarafından döndürülen meta verilerde gösterilir. Meta verilerde, hizmet işlemleri `FunctionImport` öğesi olarak temsil edilir. Türü kesin belirlenmiş <xref:System.Data.Services.Client.DataServiceContext>oluştururken, Hizmet Başvurusu Ekle ve DataSvcUtil. exe araçları bu öğeyi yoksayar. Bu nedenle, bir hizmet işlemini doğrudan çağırmak için kullanılabilen bağlamda bir yöntem bulamacaksınız. Ancak, bu iki şekilde hizmet işlemlerini çağırmak için [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemcisini kullanmaya devam edebilirsiniz:  
  
- <xref:System.Data.Services.Client.DataServiceContext><xref:System.Data.Services.Client.DataServiceContext.Execute%2A> yöntemini çağırarak, hizmet işleminin URI 'sini, tüm parametrelerle birlikte sağlayarak. Bu yöntem, tüm hizmet Al işlemlerini çağırmak için kullanılır.  
  
- <xref:System.Data.Services.Client.DataServiceContext> <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> yöntemi kullanarak bir <xref:System.Data.Services.Client.DataServiceQuery%601> nesnesi oluşturun. <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>çağrılırken, hizmet işleminin adı `entitySetName` parametresine sağlanır. Bu yöntem, <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> yöntemi çağrıldığında veya oluşturulduğunda hizmet işlemini çağıran bir <xref:System.Data.Services.Client.DataServiceQuery%601> nesnesi döndürür. Bu yöntem, bir koleksiyon döndüren GET hizmeti işlemlerini çağırmak için kullanılır. Tek bir parametre <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> yöntemi kullanılarak sağlanabilir. Bu yöntem tarafından döndürülen <xref:System.Data.Services.Client.DataServiceQuery%601> nesnesi, herhangi bir sorgu nesnesi gibi daha fazla bulunabilir. Daha fazla bilgi için bkz. [veri hizmetini sorgulama](querying-the-data-service-wcf-data-services.md).  
  
## <a name="considerations-for-calling-service-operations"></a>Hizmet Işlemlerini çağırma konuları  
 Aşağıdaki noktalar, hizmet işlemlerini çağırmak için [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemcisi kullanılırken geçerlidir.  
  
- Veri hizmetine zaman uyumsuz olarak erişirken, <xref:System.Data.Services.Client.DataServiceContext> üzerinde <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A> yöntemleri veya <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A>/<xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> yöntemleri /<xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A>eş zamanlı zaman uyumsuz kullanmanız gerekir.  
  
- [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemci kitaplığı, temel türlerin bir koleksiyonunu döndüren bir hizmet işleminden sonuçları yürütülemiyor.  
  
- [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemci kitaplığı, hizmet gönderme işlemlerinin çağrılmasını desteklemez. Bir HTTP POST tarafından çağrılan hizmet işlemleri `Method="POST"` parametresiyle <xref:System.ServiceModel.Web.WebInvokeAttribute> kullanılarak tanımlanır. Bir HTTP POST isteği kullanarak bir hizmet işlemini çağırmak için, bunun yerine bir <xref:System.Net.HttpWebRequest>kullanmanız gerekir.  
  
- Tek bir sonuç döndüren veya birden fazla giriş parametresi gerektiren bir GET hizmeti işlemini çağırmak için <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> kullanamazsınız. Bunun yerine <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> yöntemini çağırmanız gerekir.  
  
- Araçlar tarafından oluşturulan, bir hizmet işlemini çağırmak için <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> veya <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> yöntemini kullanan kesin olarak belirlenmiş <xref:System.Data.Services.Client.DataServiceContext> kısmi sınıfında bir genişletme yöntemi oluşturmayı düşünün. Bu, hizmet işlemlerini doğrudan bağlamdan çağırmanızı sağlar. Daha fazla bilgi için bkz. Blog Post [hizmeti işlemleri ve WCF veri Hizmetleri istemcisi](https://go.microsoft.com/fwlink/?LinkId=215668).  
  
- Bir hizmet işlemini çağırmak için <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> kullandığınızda, istemci kitaplığı, ampersan (&) ve dizelerde tek tırnak işareti gibi ayrılmış karakterlerin yüzde kodlaması gerçekleştirerek <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> sağlanan karakterleri otomatik olarak çıkar. Ancak, bir hizmet işlemini çağırmak için *Execute* yöntemlerinden birini çağırdığınızda, Kullanıcı tarafından sağlanan herhangi bir dize değerinin bu kaçışı gerçekleştirmeyi unutmamanız gerekir. URI 'Lerinde tek tırnak işareti, tek tırnak çifti olarak atlardır.  
  
## <a name="examples-of-calling-service-operations"></a>Hizmet Işlemlerini çağırma örnekleri  
 Bu bölüm, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemci kitaplığını kullanarak hizmet işlemlerini çağırma hakkında aşağıdaki örnekleri içerir:  
  
- [Bir varlık koleksiyonu döndürmek için Execute&lt;T&gt; çağrılıyor](calling-service-operations-wcf-data-services.md#ExecuteIQueryable)  
  
- [Bir varlık koleksiyonu döndürmek için CreateQuery&lt;T&gt; kullanma](calling-service-operations-wcf-data-services.md#CreateQueryIQueryable)  
  
- [Tek bir varlık döndürmek için Execute&lt;T&gt; çağrılıyor](calling-service-operations-wcf-data-services.md#ExecuteSingleEntity)  
  
- [Temel değerlerin bir koleksiyonunu döndürmek için Execute&lt;T&gt; çağrılıyor](calling-service-operations-wcf-data-services.md#ExecutePrimitiveCollection)  
  
- [Tek bir temel değer döndürmek için Execute&lt;T&gt; çağrılıyor](calling-service-operations-wcf-data-services.md#ExecutePrimitiveValue)  
  
- [Veri döndüren bir hizmet Işlemi çağırma](calling-service-operations-wcf-data-services.md#ExecuteVoid)  
  
- [Hizmet Işlemi zaman uyumsuz olarak çağrılıyor](calling-service-operations-wcf-data-services.md#ExecuteAsync)  
  
<a name="ExecuteIQueryable"></a>   
### <a name="calling-executet-to-return-a-collection-of-entities"></a>Bir varlık koleksiyonu döndürmek için Execute\<T > çağrılıyor  
 Aşağıdaki örnek, bir `city` dize parametresi alan ve bir <xref:System.Linq.IQueryable%601>döndüren GetOrdersByCity adlı bir hizmet işlemini çağırır:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationiqueryable)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationiqueryable)]  
  
 Bu örnekte, hizmet işlemi ilgili `Order_Detail` nesneleri olan `Order` nesnelerinin bir koleksiyonunu döndürür.  
  
<a name="CreateQueryIQueryable"></a>   
### <a name="using-createqueryt-to-return-a-collection-of-entities"></a>Bir varlık koleksiyonu döndürmek için CreateQuery\<T > kullanma  
 Aşağıdaki örnek, aynı GetOrdersByCity hizmeti işlemini çağırmak için kullanılan bir <xref:System.Data.Services.Client.DataServiceQuery%601> döndürmek için <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> kullanır:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationcreatequery)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationcreatequery)]  
  
 Bu örnekte <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> yöntemi, sorguya parametreyi eklemek için kullanılır ve <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> yöntemi, sonuçlarda ilgili Order_Details nesneleri dahil etmek için kullanılır.  
  
<a name="ExecuteSingleEntity"></a>   
### <a name="calling-executet-to-return-a-single-entity"></a>Tek bir varlık döndürmek için Execute\<T > çağrılıyor  
 Aşağıdaki örnek, yalnızca tek bir sipariş varlığı döndüren GetNewestOrder adlı bir hizmet işlemini çağırır:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationsingleentity)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationsingleentity)]  
  
 Bu örnekte, yürütme sırasında yalnızca tek bir sipariş varlığı istemek için <xref:System.Linq.Enumerable.FirstOrDefault%2A> yöntemi kullanılır.  
  
<a name="ExecutePrimitiveCollection"></a>   
### <a name="calling-executet-to-return-a-collection-of-primitive-values"></a>Temel değerlerin bir koleksiyonunu döndürmek için Execute\<T > çağrılıyor  
 Aşağıdaki örnek, bir dize değerleri koleksiyonu döndüren bir hizmet işlemini çağırır:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationEnumString](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationenumstring)]  
  
<a name="ExecutePrimitiveValue"></a>   
### <a name="calling-executet-to-return-a-single-primitive-value"></a>Tek bir temel değer döndürmek için Execute\<T > çağrılıyor  
 Aşağıdaki örnek, tek bir dize değeri döndüren bir hizmet işlemini çağırır:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationsingleint)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationsingleint)]  
  
 Bu örnekte, <xref:System.Linq.Enumerable.FirstOrDefault%2A> yöntemi yürütme sırasında yalnızca tek bir tamsayı değeri istemek için kullanılır.  
  
<a name="ExecuteVoid"></a>   
### <a name="calling-a-service-operation-that-returns-no-data"></a>Veri döndüren bir hizmet Işlemi çağırma  
 Aşağıdaki örnek, veri döndüren bir hizmet işlemini çağırır:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationvoid)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationvoid)]  
  
 Veriler döndürülmediği için yürütmenin değeri atanmadı. İsteğin başarılı olduğu tek gösterge <xref:System.Data.Services.Client.DataServiceQueryException> oluşturulmaz.  
  
<a name="ExecuteAsync"></a>   
### <a name="calling-a-service-operation-asynchronously"></a>Hizmet Işlemi zaman uyumsuz olarak çağrılıyor  
 Aşağıdaki örnek, <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> ve <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>çağırarak bir hizmet işlemini zaman uyumsuz olarak çağırır:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onasyncexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onasyncexecutioncomplete)]  
  
 Hiçbir veri döndürülmediği için, yürütme tarafından döndürülen değer atanmadı. İsteğin başarılı olduğu tek gösterge <xref:System.Data.Services.Client.DataServiceQueryException> oluşturulmaz.  
  
 Aşağıdaki örnek, <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>kullanarak aynı hizmet işlemini zaman uyumsuz olarak çağırır:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationqueryasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationqueryasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onasyncqueryexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onasyncqueryexecutioncomplete)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
