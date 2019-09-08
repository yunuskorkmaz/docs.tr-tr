---
title: Hizmet Işlemlerini çağırma (WCF Veri Hizmetleri)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1767f3a7-29d2-4834-a763-7d169693fa8b
ms.openlocfilehash: 21ae73054935373607909902e0b3e82ba5146f43
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791151"
---
# <a name="calling-service-operations-wcf-data-services"></a>Hizmet Işlemlerini çağırma (WCF Veri Hizmetleri)
, [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Bir veri hizmeti için hizmet işlemlerini tanımlar. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]Bu tür işlemleri veri hizmetindeki yöntemler olarak tanımlamanızı sağlar. Diğer veri hizmeti kaynakları gibi bu hizmet işlemleri de URI 'Ler kullanılarak karşılanır. Bir hizmet işlemi varlık türleri, tek varlık türü örnekleri ve tamsayı ve dize gibi basit türler için Koleksiyonlar döndürebilir. Ayrıca, bir hizmet işlemi de `null` döndürebilir`Nothing` (Visual Basic). İstemci [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] kitaplığı, http get isteklerini destekleyen hizmet işlemlerine erişmek için kullanılabilir. Bu tür hizmet işlemleri, <xref:System.ServiceModel.Web.WebGetAttribute> uygulanmış olan yöntemler olarak tanımlanır. Daha fazla bilgi için bkz. [hizmet işlemleri](service-operations-wcf-data-services.md).  
  
 Hizmet işlemleri, [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]uygulayan bir veri hizmeti tarafından döndürülen meta verilerde gösterilir. Meta verilerde, hizmet işlemleri öğeler olarak `FunctionImport` temsil edilir. Türü kesin belirlenmiş <xref:System.Data.Services.Client.DataServiceContext>olarak oluşturulurken hizmet başvurusu Ekle ve DataSvcUtil. exe araçları bu öğeyi yoksayar. Bu nedenle, bir hizmet işlemini doğrudan çağırmak için kullanılabilen bağlamda bir yöntem bulamacaksınız. Ancak, şu iki şekilde hizmet işlemlerini [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] çağırmak için istemcisini kullanmaya devam edebilirsiniz:  
  
- <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> Üzerinde yöntemini çağırarak, hizmet işleminin URI 'sini, tüm parametrelerle birlikte sağlayarak. <xref:System.Data.Services.Client.DataServiceContext> Bu yöntem, tüm hizmet Al işlemlerini çağırmak için kullanılır.  
  
- Bir <xref:System.Data.Services.Client.DataServiceContext> <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> nesnesioluşturmakiçin<xref:System.Data.Services.Client.DataServiceQuery%601> üzerinde yöntemini kullanarak. Çağrılırken <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>, hizmet işleminin adı `entitySetName` parametreye sağlanır. Bu yöntem, <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> ya <xref:System.Data.Services.Client.DataServiceQuery%601> da yöntemi çağrıldığında hizmet işlemini çağıran bir nesne döndürür. Bu yöntem, bir koleksiyon döndüren GET hizmeti işlemlerini çağırmak için kullanılır. <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> Yöntemi kullanılarak tek bir parametre sağlanabilir. Bu <xref:System.Data.Services.Client.DataServiceQuery%601> yöntemin döndürdüğü nesne, herhangi bir sorgu nesnesi gibi daha fazla bulunabilir. Daha fazla bilgi için bkz. [veri hizmetini sorgulama](querying-the-data-service-wcf-data-services.md).  
  
## <a name="considerations-for-calling-service-operations"></a>Hizmet Işlemlerini çağırma konuları  
 İstemci, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] hizmet işlemlerini çağırmak için kullanılırken aşağıdaki önemli noktalar geçerlidir.  
  
- Veri <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> hizmetine zaman uyumsuz olarak erişirken, üzerinde eşdeğer zaman uyumsuz <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A> / yöntemleri <xref:System.Data.Services.Client.DataServiceContext> veya / üzerindeki <xref:System.Data.Services.Client.DataServiceQuery%601>yöntemleri kullanmanız gerekir.  
  
- İstemci [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] kitaplığı, temel türlerin bir koleksiyonunu döndüren bir hizmet işleminden sonuçları değerlendirilemiyor.  
  
- İstemci [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] kitaplığı, hizmet gönderme işlemlerinin çağrılmasını desteklemez. Bir http post tarafından çağrılan hizmet işlemleri <xref:System.ServiceModel.Web.WebInvokeAttribute> `Method="POST"` parametresiyle kullanılarak tanımlanır. Bir HTTP POST isteği kullanarak bir hizmet işlemini çağırmak için, bunun yerine bir <xref:System.Net.HttpWebRequest>kullanmalısınız.  
  
- Tek bir sonuç döndüren veya birden fazla giriş parametresi gerektiren bir get hizmeti işlemini çağırmak içinkullanamazsınız.<xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> Bunun yerine <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> yöntemini çağırmanız gerekir.  
  
- Araçlar tarafından oluşturulan ve bir hizmet işlemini çağırmak için <xref:System.Data.Services.Client.DataServiceContext> <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> yöntemini kullanan <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> kesin türü belirtilmiş kısmi sınıfta bir genişletme yöntemi oluşturmayı düşünün. Bu, hizmet işlemlerini doğrudan bağlamdan çağırmanızı sağlar. Daha fazla bilgi için bkz. Blog Post [hizmeti işlemleri ve WCF veri Hizmetleri istemcisi](https://go.microsoft.com/fwlink/?LinkId=215668).  
  
- Bir hizmet işlemini <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> çağırmak için kullandığınızda, istemci kitaplığı, ve ' de tek tırnak işareti (&) <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> gibi ayrılmış karakterlerin yüzde kodlaması gerçekleştirerek otomatik olarak öğesine verilen karakterleri çıkar. Strings. Ancak, bir hizmet işlemini çağırmak için *Execute* yöntemlerinden birini çağırdığınızda, Kullanıcı tarafından sağlanan herhangi bir dize değerinin bu kaçışı gerçekleştirmeyi unutmamanız gerekir. URI 'Lerinde tek tırnak işareti, tek tırnak çifti olarak atlardır.  
  
## <a name="examples-of-calling-service-operations"></a>Hizmet Işlemlerini çağırma örnekleri  
 Bu bölüm, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] istemci kitaplığını kullanarak hizmet işlemlerinin nasıl çağrılacağını gösteren aşağıdaki örnekleri içerir:  
  
- [Bir varlık&lt;koleksiyonu&gt; döndürmek için Execute T çağrılıyor](calling-service-operations-wcf-data-services.md#ExecuteIQueryable)  
  
- [Bir varlık koleksiyonu&lt;döndürmek&gt; için CreateQuery T kullanma](calling-service-operations-wcf-data-services.md#CreateQueryIQueryable)  
  
- [Tek bir&lt;varlık&gt; döndürmek için Execute T çağrılıyor](calling-service-operations-wcf-data-services.md#ExecuteSingleEntity)  
  
- [Temel değerlerin&lt;bir&gt; koleksiyonunu döndürmek için Execute T çağrılıyor](calling-service-operations-wcf-data-services.md#ExecutePrimitiveCollection)  
  
- [Tek bir&lt;temel&gt; değer döndürmek için Execute T çağrılıyor](calling-service-operations-wcf-data-services.md#ExecutePrimitiveValue)  
  
- [Veri döndüren bir hizmet Işlemi çağırma](calling-service-operations-wcf-data-services.md#ExecuteVoid)  
  
- [Hizmet Işlemi zaman uyumsuz olarak çağrılıyor](calling-service-operations-wcf-data-services.md#ExecuteAsync)  
  
<a name="ExecuteIQueryable"></a>   
### <a name="calling-executet-to-return-a-collection-of-entities"></a>Bir varlık\<koleksiyonu döndürmek için yürütme T > çağrılıyor  
 Aşağıdaki örnek, bir dize parametresi `city` alan ve bir <xref:System.Linq.IQueryable%601>döndüren GetOrdersByCity adlı bir hizmet işlemini çağırır:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationiqueryable)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationiqueryable)]  
  
 Bu örnekte, hizmet işlemi ilgili `Order` `Order_Detail` nesneler içeren bir nesne koleksiyonu döndürür.  
  
<a name="CreateQueryIQueryable"></a>   
### <a name="using-createqueryt-to-return-a-collection-of-entities"></a>Bir varlık koleksiyonu\<döndürmek için CreateQuery T > kullanma  
 Aşağıdaki örnek, <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> aynı GetOrdersByCity hizmeti işlemini çağırmak için kullanılan öğesini <xref:System.Data.Services.Client.DataServiceQuery%601> döndürmek için öğesini kullanır:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationcreatequery)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationcreatequery)]  
  
 Bu örnekte, <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> parametresini sorguya eklemek için yöntemi kullanılır <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> ve bu yöntem, sonuçlarda ilgili Order_Details nesneleri dahil etmek için kullanılır.  
  
<a name="ExecuteSingleEntity"></a>   
### <a name="calling-executet-to-return-a-single-entity"></a>Tek bir\<varlık döndürmek için Execute T > çağrılıyor  
 Aşağıdaki örnek, yalnızca tek bir sipariş varlığı döndüren GetNewestOrder adlı bir hizmet işlemini çağırır:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationsingleentity)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationsingleentity)]  
  
 Bu örnekte, <xref:System.Linq.Enumerable.FirstOrDefault%2A> yöntemi yürütme sırasında yalnızca tek bir sipariş varlığı istemek için kullanılır.  
  
<a name="ExecutePrimitiveCollection"></a>   
### <a name="calling-executet-to-return-a-collection-of-primitive-values"></a>Temel değerlerin\<bir koleksiyonunu döndürmek için Execute T > çağrılıyor  
 Aşağıdaki örnek, bir dize değerleri koleksiyonu döndüren bir hizmet işlemini çağırır:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationEnumString](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationenumstring)]  
  
<a name="ExecutePrimitiveValue"></a>   
### <a name="calling-executet-to-return-a-single-primitive-value"></a>Tek bir\<temel değer döndürmek için Execute T > çağrılıyor  
 Aşağıdaki örnek, tek bir dize değeri döndüren bir hizmet işlemini çağırır:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationsingleint)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationsingleint)]  
  
 Bu örnekte, <xref:System.Linq.Enumerable.FirstOrDefault%2A> yöntemi yürütme sırasında yalnızca tek bir tamsayı değeri istemek için kullanılır.  
  
<a name="ExecuteVoid"></a>   
### <a name="calling-a-service-operation-that-returns-no-data"></a>Veri döndüren bir hizmet Işlemi çağırma  
 Aşağıdaki örnek, veri döndüren bir hizmet işlemini çağırır:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationvoid)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationvoid)]  
  
 Veriler döndürülmediği için yürütmenin değeri atanmadı. İsteğin başarılı olduğu tek işaret, hiçbir <xref:System.Data.Services.Client.DataServiceQueryException> değer çıkarılmadığını belirtir.  
  
<a name="ExecuteAsync"></a>   
### <a name="calling-a-service-operation-asynchronously"></a>Hizmet Işlemi zaman uyumsuz olarak çağrılıyor  
 Aşağıdaki örnek, ve <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>çağırarak zaman uyumsuz olarak bir hizmet işlemi çağırır:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onasyncexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onasyncexecutioncomplete)]  
  
 Hiçbir veri döndürülmediği için, yürütme tarafından döndürülen değer atanmadı. İsteğin başarılı olduğu tek işaret, hiçbir <xref:System.Data.Services.Client.DataServiceQueryException> değer çıkarılmadığını belirtir.  
  
 Aşağıdaki örnek kullanarak <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>aynı hizmet işlemini zaman uyumsuz olarak çağırır:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationqueryasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationqueryasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onasyncqueryexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onasyncqueryexecutioncomplete)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
