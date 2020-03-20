---
title: Arama Hizmeti İşlemleri (WCF Veri Hizmetleri)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1767f3a7-29d2-4834-a763-7d169693fa8b
ms.openlocfilehash: 41aac38cec97ae1afdd3c3c051d04ff242e7729d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174361"
---
# <a name="calling-service-operations-wcf-data-services"></a>Arama Hizmeti İşlemleri (WCF Veri Hizmetleri)
Açık Veri Protokolü (OData), bir veri hizmetiiçin hizmet işlemlerini tanımlar. WCF Veri Hizmetleri, bu tür işlemleri veri hizmetindeki yöntemler gibi tanımlamanıza olanak tanır. Diğer veri hizmeti kaynakları gibi, bu hizmet işlemleri de URI kullanılarak ele alınır. Bir hizmet işlemi varlık türleri, tek varlık türü örnekleri ve tamsayı ve dize gibi ilkel türlerin koleksiyonlarını döndürebilir. Bir hizmet işlemi `null` de`Nothing` (Visual Basic'te) geri dönebilir. WCF Veri Hizmetleri istemci kitaplığı, HTTP GET isteklerini destekleyen hizmet işlemlerine erişmek için kullanılabilir. Bu tür hizmet işlemleri <xref:System.ServiceModel.Web.WebGetAttribute> uygulanan yöntemler olarak tanımlanır. Daha fazla bilgi için [Hizmet İşlemleri'ne](service-operations-wcf-data-services.md)bakın.  
  
 Hizmet işlemleri, OData'yı uygulayan bir veri hizmeti tarafından döndürülen meta verilerde ortaya çıkarır. Meta verilerde, hizmet işlemleri öğeler `FunctionImport` olarak temsil edilir. Güçlü bir şekilde yazılan <xref:System.Data.Services.Client.DataServiceContext>, Hizmet Başvurusu Ekle ve DataSvcUtil.exe araçlarını oluştururken bu öğeyi yoksun. Bu nedenle, bağlam üzerinde bir hizmet işlemini doğrudan çağırmak için kullanılabilecek bir yöntem bulamazsınız. Ancak, hizmet işlemlerini şu iki şekilde aramak için WCF Veri Hizmetleri istemcisini kullanmaya devam edebilirsiniz:  
  
- Herhangi bir <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> parametre <xref:System.Data.Services.Client.DataServiceContext>ile birlikte, hizmet işleminin URI temini üzerinde yöntem arayarak. Bu yöntem, herhangi bir GET servis işlemini çağırmak için kullanılır.  
  
- Bir <xref:System.Data.Services.Client.DataServiceQuery%601> nesne <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> oluşturmak <xref:System.Data.Services.Client.DataServiceContext> için yöntemi kullanarak. Arama <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>yaparken, hizmet işleminin adı `entitySetName` parametreye verilir. Bu yöntem, <xref:System.Data.Services.Client.DataServiceQuery%601> numaralandırıldığında veya <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> yöntem çağrıldığında hizmet işlemini çağıran bir nesneyi döndürür. Bu yöntem, bir koleksiyon döndüren GET hizmet işlemlerini çağırmak için kullanılır. Yöntem kullanılarak <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> tek bir parametre sağlanabilir. Bu <xref:System.Data.Services.Client.DataServiceQuery%601> yöntemle döndürülen nesne, herhangi bir sorgu nesnesi gibi daha da oluşturulabilir. Daha fazla bilgi için [Bkz. Veri Hizmetini Sorgulama.](querying-the-data-service-wcf-data-services.md)  
  
## <a name="considerations-for-calling-service-operations"></a>Arama Hizmeti İşlemlerinde Dikkat Edilecek Hususlar  
 Hizmet işlemlerini aramak için WCF Veri Hizmetleri istemcisini kullanırken aşağıdaki hususlar geçerlidir.  
  
- Veri hizmetine eşit olarak erişirken, eşdeğer eşzamanlı <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> / <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A> yöntemleri <xref:System.Data.Services.Client.DataServiceContext> veya <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> / <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> 'deki <xref:System.Data.Services.Client.DataServiceQuery%601>yöntemleri kullanmanız gerekir.  
  
- WCF Veri Hizmetleri istemci kitaplığı, ilkel türler koleksiyonunu döndüren bir hizmet işleminin sonuçlarını somutlaştıramaz.  
  
- WCF Veri Hizmetleri istemci kitaplığı POST servis işlemlerini aramayı desteklemez. HTTP POST tarafından çağrılan servis işlemleri <xref:System.ServiceModel.Web.WebInvokeAttribute> `Method="POST"` parametre ile kullanılarak tanımlanır. Bir HTTP POST isteği kullanarak bir hizmet işlemini <xref:System.Net.HttpWebRequest>çağırmak için, bunun yerine bir .  
  
- Varlık veya <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> ilkel türde tek bir sonucu döndüren veya birden fazla giriş parametresi gerektiren get hizmet işlemini çağırmak için kullanamazsınız. Bunun yerine <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> yöntemi aramalısınız.  
  
- Bir hizmet işlemini çağırmak için ya <xref:System.Data.Services.Client.DataServiceContext> <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> da <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> yöntemi kullanan araçlar tarafından oluşturulan güçlü bir şekilde yazılan kısmi sınıfta bir uzantı yöntemi oluşturmayı düşünün. Bu, hizmet işlemlerini doğrudan bağlamdan aramanızı sağlar. Daha fazla bilgi için blog gönderisi [Hizmet İşlemleri ve WCF Veri Hizmetleri İstemci'si'ne](https://docs.microsoft.com/archive/blogs/astoriateam/service-operations-and-the-wcf-data-services-client)bakın.  
  
- Bir hizmet <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> işlemini çağırmak için kullandığınızda, istemci kitaplığı, ampersand (&) gibi ayrılmış karakterlerin yüzde kodlamasını <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> gerçekleştirerek ve dizelerdeki tek tırnak tan kaçarak otomatik olarak verilen karakterlerden kaçar. Ancak, bir hizmet işlemini çağırmak için *Yürüt metotlardan* birini çağırdığınızda, kullanıcı tarafından sağlanan dize değerlerinin bu kaçışını gerçekleştirmeyi unutmamanız gerekir. URI'lerde tek tırnak işaretleri tek tırnak çifti olarak kaçtır.  
  
## <a name="examples-of-calling-service-operations"></a>Arama Hizmeti İşlemleri Örnekleri  
 Bu bölümde, WCF Veri Hizmetleri istemci kitaplığını kullanarak hizmet işlemlerinin nasıl çağrılması ile ilgili aşağıdaki örnekler yer almaktadır:  
  
- [Varlıklar&lt;Koleksiyonunu&gt; Döndürmek Için Execute T'yi Arama](calling-service-operations-wcf-data-services.md#ExecuteIQueryable)  
  
- [Varlıklar Koleksiyonunu&lt;&gt; Döndürmek için CreateQuery T'yi kullanma](calling-service-operations-wcf-data-services.md#CreateQueryIQueryable)  
  
- [Tek&lt;Bir&gt; Varlığı Döndürmek Için Yürütme T'yi Arama](calling-service-operations-wcf-data-services.md#ExecuteSingleEntity)  
  
- [İlkel&lt;&gt; Değerler Koleksiyonunu Döndürmek Için Execute T'yi Çağırma](calling-service-operations-wcf-data-services.md#ExecutePrimitiveCollection)  
  
- [Tek&lt;Bir&gt; İlkel Değeri Döndürmek Için Yürütme T'yi Arama](calling-service-operations-wcf-data-services.md#ExecutePrimitiveValue)  
  
- [Veri İade Sayılmama Hizmeti İşlemini Çağırma](calling-service-operations-wcf-data-services.md#ExecuteVoid)  
  
- [Bir Hizmet İşlemini Eşzamanlı Olarak Çağırma](calling-service-operations-wcf-data-services.md#ExecuteAsync)  
  
<a name="ExecuteIQueryable"></a>
### <a name="calling-executet-to-return-a-collection-of-entities"></a>Varlıkların\<Bir Koleksiyon İade si için Execute T> Arama  
 Aşağıdaki örnek, getOrdersByCity adlı bir hizmet işlemini `city` çağırır ve <xref:System.Linq.IQueryable%601>bir dize parametresi alır ve bir:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationiqueryable)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationiqueryable)]  
  
 Bu örnekte, hizmet işlemi ilgili `Order` `Order_Detail` nesnelerle nesnelerin bir koleksiyon döndürür.  
  
<a name="CreateQueryIQueryable"></a>
### <a name="using-createqueryt-to-return-a-collection-of-entities"></a>Varlıkların Bir\<Koleksiyon Döndürme> CreateQuery T kullanma  
 Aşağıdaki örnek, <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> aynı GetOrdersByCity hizmet işlemini çağırmak için kullanılan bir iade <xref:System.Data.Services.Client.DataServiceQuery%601> yi kullanır:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationcreatequery)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationcreatequery)]  
  
 Bu örnekte, <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> yöntem sorguya parametre eklemek için kullanılır <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> ve yöntem sonuçlara ilgili Order_Details nesneleri eklemek için kullanılır.  
  
<a name="ExecuteSingleEntity"></a>
### <a name="calling-executet-to-return-a-single-entity"></a>Tek\<Bir Varlığı Döndürmek için Execute T>'ı arama  
 Aşağıdaki örnek, yalnızca tek bir Sipariş varlığını döndüren GetNewestOrder adlı bir hizmet işlemini çağırır:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationsingleentity)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationsingleentity)]  
  
 Bu örnekte, <xref:System.Linq.Enumerable.FirstOrDefault%2A> yöntem yürütme yalnızca tek bir Sipariş varlık istemek için kullanılır.  
  
<a name="ExecutePrimitiveCollection"></a>
### <a name="calling-executet-to-return-a-collection-of-primitive-values"></a>İlkel\<Değerler Koleksiyonunu Döndürmek için Execute T>'ı arama  
 Aşağıdaki örnek, dize değerleri koleksiyonunu döndüren bir hizmet işlemi çağırır:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationEnumString](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationenumstring)]  
  
<a name="ExecutePrimitiveValue"></a>
### <a name="calling-executet-to-return-a-single-primitive-value"></a>Tek\<Bir İlkel Değeri Döndürmek için Execute T>'ı arama  
 Aşağıdaki örnek, tek bir dize değeri döndüren bir hizmet işlemi çağırır:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationsingleint)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationsingleint)]  
  
 Yine bu örnekte, <xref:System.Linq.Enumerable.FirstOrDefault%2A> yöntem yürütme yalnızca tek bir tamsayı değeri istemek için kullanılır.  
  
<a name="ExecuteVoid"></a>
### <a name="calling-a-service-operation-that-returns-no-data"></a>Veri İade Sayılmama Hizmeti İşlemini Çağırma  
 Aşağıdaki örnek, veri döndüren bir hizmet işlemi çağırır:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationvoid)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationvoid)]  
  
 Veri döndürülmediği için yürütmenin değeri atanmıyor. İsteğin başarılı olduğunun tek göstergesi hayır'ın <xref:System.Data.Services.Client.DataServiceQueryException> yükseltilmesidir.  
  
<a name="ExecuteAsync"></a>
### <a name="calling-a-service-operation-asynchronously"></a>Bir Hizmet İşlemini Eşzamanlı Olarak Çağırma  
 Aşağıdaki örnek, bir servis işlemini eş <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>senkronize olarak arayarak çağırır ve:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onasyncexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onasyncexecutioncomplete)]  
  
 Veri döndürülmedığından, yürütme tarafından döndürülen değer atanmıyor. İsteğin başarılı olduğunun tek göstergesi hayır'ın <xref:System.Data.Services.Client.DataServiceQueryException> yükseltilmesidir.  
  
 Aşağıdaki örnek, aynı hizmet işlemini aşağıdakileri <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>kullanarak eşit olarak çağırır:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationqueryasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationqueryasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onasyncqueryexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onasyncqueryexecutioncomplete)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
