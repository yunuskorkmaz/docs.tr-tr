---
title: "Hizmet işlemleri (WCF Veri Hizmetleri)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: 583a690a-e60f-4990-8991-d6efce069d76
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 72af11330bc9190ea0c07e23f2e87e5f4840b677
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="service-operations-wcf-data-services"></a><span data-ttu-id="afc46-102">Hizmet işlemleri (WCF Veri Hizmetleri)</span><span class="sxs-lookup"><span data-stu-id="afc46-102">Service Operations (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="afc46-103">Sunucu üzerindeki yöntemleri kullanıma sunmak için veri hizmeti hizmet işlemleri tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="afc46-103"> enables you to define service operations on a data service to expose methods on the server.</span></span> <span data-ttu-id="afc46-104">Veri Hizmeti kaynaklar gibi hizmet işlemleri URI tarafından ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="afc46-104">Like other data service resources, service operations are addressed by URIs.</span></span> <span data-ttu-id="afc46-105">Hizmet işlemleri, bir veri hizmeti iş mantığı gibi rol tabanlı güvenlik, uygulamak için doğrulama mantığını uygulamak için kullanıma sunmak etkinleştirin veya özellikleri sorgulama kullanıma sunmak için özelleştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="afc46-105">Service operations enable you to expose business logic in a data service, such as to implement validation logic, to apply role-based security, or to expose specialized querying capabilities.</span></span> <span data-ttu-id="afc46-106">Hizmet işlemleri yöntemlerdir türetilen veri hizmet sınıfı eklenen <xref:System.Data.Services.DataService%601>.</span><span class="sxs-lookup"><span data-stu-id="afc46-106">Service operations are methods added to the data service class that derives from <xref:System.Data.Services.DataService%601>.</span></span> <span data-ttu-id="afc46-107">Tüm veri hizmeti kaynaklar gibi hizmet işlemi yöntemi için parametreler sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="afc46-107">Like all other data service resources, you can supply parameters to the service operation method.</span></span> <span data-ttu-id="afc46-108">Örneğin, aşağıdaki işlemi URI hizmet (temel [Hızlı Başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) veri hizmeti) değeri geçirir `London` için `city` parametre:</span><span class="sxs-lookup"><span data-stu-id="afc46-108">For example, the following service operation URI (based on the [quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) data service) passes the value `London` to the `city` parameter:</span></span>  
  
```  
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'  
```  
  
 <span data-ttu-id="afc46-109">Bu hizmet işlemi tanımı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="afc46-109">The definition for this service operation is as follows:</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationdef)]
 [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationdef)]  
  
 <span data-ttu-id="afc46-110">Kullanabileceğiniz <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> , <xref:System.Data.Services.DataService%601> doğrudan veri hizmeti kullanarak veri kaynağına erişmek için.</span><span class="sxs-lookup"><span data-stu-id="afc46-110">You can use the <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> of the <xref:System.Data.Services.DataService%601> to directly access the data source that the data service is using.</span></span> <span data-ttu-id="afc46-111">Daha fazla bilgi için bkz: [nasıl yapılır: bir hizmet işlemi tanımlamak](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="afc46-111">For more information, see [How to: Define a Service Operation](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="afc46-112">Bir .NET Framework istemci uygulamasından bir hizmet işlemi çağırma hakkında daha fazla bilgi için bkz: [hizmet işlemlerini çağırma](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="afc46-112">For information on how to call a service operation from a .NET Framework client application, see [Calling Service Operations](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md).</span></span>  
  
## <a name="service-operation-requirements"></a><span data-ttu-id="afc46-113">Hizmet işlem gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="afc46-113">Service Operation Requirements</span></span>  
 <span data-ttu-id="afc46-114">Veri Hizmeti hizmet işlemleri tanımlarken, aşağıdaki gereksinimleri geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="afc46-114">The following requirements apply when defining service operations on the data service.</span></span> <span data-ttu-id="afc46-115">Bir yöntem bu gereksinimlerini karşılamıyorsa, veri hizmeti için bir hizmet işlemi olarak sunulur değil.</span><span class="sxs-lookup"><span data-stu-id="afc46-115">If a method does not meet these requirements, it will not be exposed as a service operation for the data service.</span></span>  
  
-   <span data-ttu-id="afc46-116">İşlemi, veri hizmeti sınıf üyesi olan bir ortak örnek yöntemi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="afc46-116">The operation must be a public instance method that is a member of the data service class.</span></span>  
  
-   <span data-ttu-id="afc46-117">İşlem yöntemi yalnızca giriş parametreleri kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="afc46-117">The operation method may only accept input parameters.</span></span> <span data-ttu-id="afc46-118">İleti gövdesinde gönderilen veriler veri hizmeti tarafından erişilemiyor.</span><span class="sxs-lookup"><span data-stu-id="afc46-118">Data sent in the message body cannot be accessed by the data service.</span></span>  
  
-   <span data-ttu-id="afc46-119">Parametreleri tanımlanmışsa, her parametrenin türü basit tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="afc46-119">If parameters are defined, the type of each parameter must be a primitive type.</span></span> <span data-ttu-id="afc46-120">Bir basit olmayan türde herhangi bir veri seri hale getirilmiş ve bir dize parametresi geçirildi.</span><span class="sxs-lookup"><span data-stu-id="afc46-120">Any data of a non-primitive type must be serialized and passed into a string parameter.</span></span>  
  
-   <span data-ttu-id="afc46-121">Yöntem aşağıdakilerden birini döndürmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="afc46-121">The method must return one of the following:</span></span>  
  
    -   <span data-ttu-id="afc46-122">`void`(`Nothing` Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afc46-122">`void` (`Nothing` in Visual Basic)</span></span>  
  
    -   <xref:System.Collections.Generic.IEnumerable%601>  
  
    -   <xref:System.Linq.IQueryable%601>  
  
    -   <span data-ttu-id="afc46-123">Bir varlık türü veri modelinde verileri düzenlemenizi sağlayan hizmet.</span><span class="sxs-lookup"><span data-stu-id="afc46-123">An entity type in the data model that the data service exposes.</span></span>  
  
    -   <span data-ttu-id="afc46-124">Tamsayı veya dize gibi basit bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="afc46-124">A primitive class such as integer or string.</span></span>  
  
-   <span data-ttu-id="afc46-125">Sıralama, disk belleği ve filtreleme gibi sorgu seçeneklerini desteklemek için hizmet işlemi yöntemleri döndürmelidir <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="afc46-125">In order to support query options such as sorting, paging, and filtering, service operation methods should return <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="afc46-126">Sorgu seçenekleri hizmet işlemleri istekleri, yalnızca geri işlemleri için reddedilir <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="afc46-126">Requests to service operations that include query options are rejected for operations that only return <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
-   <span data-ttu-id="afc46-127">İlgili varlık Gezinti özellikleri kullanarak erişim desteklemek için hizmet işlemi döndürmelidir <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="afc46-127">In order to support accessing related entities by using navigation properties, the service operation must return <xref:System.Linq.IQueryable%601>.</span></span>  
  
-   <span data-ttu-id="afc46-128">Yöntem ile Açıklama eklenmelidir `[WebGet]` veya `[WebInvoke]` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="afc46-128">The method must be annotated with the `[WebGet]` or `[WebInvoke]` attribute.</span></span>  
  
    -   <span data-ttu-id="afc46-129">`[WebGet]`GET isteği kullanarak çağrılacak yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="afc46-129">`[WebGet]` enables the method to be invoked by using a GET request.</span></span>  
  
    -   <span data-ttu-id="afc46-130">`[WebInvoke(Method = "POST")]`Bir POST isteği kullanarak çağrılacak yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="afc46-130">`[WebInvoke(Method = "POST")]` enables the method to be invoked by using a POST request.</span></span> <span data-ttu-id="afc46-131">Diğer <xref:System.ServiceModel.Web.WebInvokeAttribute> yöntemleri desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="afc46-131">Other <xref:System.ServiceModel.Web.WebInvokeAttribute> methods are not supported.</span></span>  
  
-   <span data-ttu-id="afc46-132">Bir hizmet işlemi ile Açıklama <xref:System.Data.Services.SingleResultAttribute> yöntemden dönüş değeri bir varlıklar koleksiyonu yerine tek bir varlık olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="afc46-132">A service operation may be annotated with the <xref:System.Data.Services.SingleResultAttribute> that specifies that the return value from the method is a single entity rather than a collection of entities.</span></span> <span data-ttu-id="afc46-133">Bu ayrım yanıt ve ek gezinti özelliği çapraz geçişlerine URI'de temsil edilir şekilde elde edilen serileştirmek belirler.</span><span class="sxs-lookup"><span data-stu-id="afc46-133">This distinction dictates the resulting serialization of the response and the manner in which additional navigation property traversals are represented in the URI.</span></span> <span data-ttu-id="afc46-134">Örneğin, AtomPub serileştirme kullanırken, tek bir kaynak türü örneği olarak bir giriş öğesini ve bir örnek kümesini akış öğesi olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="afc46-134">For example, when using AtomPub serialization, a single resource type instance is represented as an entry element and a set of instances as a feed element.</span></span>  
  
## <a name="addressing-service-operations"></a><span data-ttu-id="afc46-135">Hizmet işlemleri adresleme</span><span class="sxs-lookup"><span data-stu-id="afc46-135">Addressing Service Operations</span></span>  
 <span data-ttu-id="afc46-136">Bir URI ilk yol kesimi yöntemin adını koyarak hizmet işlemleri karşılayabilir.</span><span class="sxs-lookup"><span data-stu-id="afc46-136">You can address service operations by placing the name of the method in the first path segment of a URI.</span></span> <span data-ttu-id="afc46-137">Örnek olarak, aşağıdaki URI erişen bir `GetOrdersByState` döndüren işlemi bir <xref:System.Linq.IQueryable%601> koleksiyonu `Orders` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="afc46-137">As an example, the following URI accesses a `GetOrdersByState` operation that returns an <xref:System.Linq.IQueryable%601> collection of `Orders` objects.</span></span>  
  
```  
http://localhost:12345/Northwind.svc/GetOrdersByState?state='CA'&includeItems=true  
```  
  
 <span data-ttu-id="afc46-138">Bir hizmet işlemi çağırırken parametre olarak sorgu seçenekleri sağlanır.</span><span class="sxs-lookup"><span data-stu-id="afc46-138">When calling a service operation, parameters are supplied as query options.</span></span> <span data-ttu-id="afc46-139">Önceki hizmet işlemi her iki dize parametresi kabul `state` ve bir Boolean parametresiyle `includeItems` belirten dahil etmek için ilgili olmadığını `Order_Detail` yanıt nesneleri.</span><span class="sxs-lookup"><span data-stu-id="afc46-139">The previous service operation accepts both a string parameter `state` and a Boolean parameter `includeItems` that indicates whether to include related `Order_Detail` objects in the response.</span></span>  
  
 <span data-ttu-id="afc46-140">Bir hizmet işlemi için geçerli dönüş türleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="afc46-140">The following are valid return types for a service operation:</span></span>  
  
|<span data-ttu-id="afc46-141">Geçerli dönüş türleri</span><span class="sxs-lookup"><span data-stu-id="afc46-141">Valid Return Types</span></span>|<span data-ttu-id="afc46-142">URI kuralları</span><span class="sxs-lookup"><span data-stu-id="afc46-142">URI Rules</span></span>|  
|------------------------|---------------|  
|<span data-ttu-id="afc46-143">`void`(`Nothing` Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afc46-143">`void` (`Nothing` in Visual Basic)</span></span><br /><br /> <span data-ttu-id="afc46-144">veya</span><span class="sxs-lookup"><span data-stu-id="afc46-144">-or-</span></span><br /><br /> <span data-ttu-id="afc46-145">Varlık türleri</span><span class="sxs-lookup"><span data-stu-id="afc46-145">Entity types</span></span><br /><br /> <span data-ttu-id="afc46-146">veya</span><span class="sxs-lookup"><span data-stu-id="afc46-146">-or-</span></span><br /><br /> <span data-ttu-id="afc46-147">İlkel türler</span><span class="sxs-lookup"><span data-stu-id="afc46-147">Primitive types</span></span>|<span data-ttu-id="afc46-148">Hizmet işlemini adı tek bir yol kesimi URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="afc46-148">The URI must be a single path segment that is the name of the service operation.</span></span> <span data-ttu-id="afc46-149">Sorgu seçeneklerine izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="afc46-149">Query options are not allowed.</span></span>|  
|<xref:System.Collections.Generic.IEnumerable%601>|<span data-ttu-id="afc46-150">Hizmet işlemini adı tek bir yol kesimi URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="afc46-150">The URI must be a single path segment that is the name of the service operation.</span></span> <span data-ttu-id="afc46-151">Sonuç türü olmadığından bir <xref:System.Linq.IQueryable%601> türü, sorgu seçeneklerine izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="afc46-151">Because the result type is not an <xref:System.Linq.IQueryable%601> type, query options are not allowed.</span></span>|  
|<xref:System.Linq.IQueryable%601>|<span data-ttu-id="afc46-152">Sorgu yol kesimleri hizmet işlemi adını yolu ek olarak izin verilir.</span><span class="sxs-lookup"><span data-stu-id="afc46-152">Query path segments in addition to the path that is the name of the service operation are allowed.</span></span> <span data-ttu-id="afc46-153">Sorgu seçenekleri de izin verilir.</span><span class="sxs-lookup"><span data-stu-id="afc46-153">Query options are also allowed.</span></span>|  
  
 <span data-ttu-id="afc46-154">Ek yol kesimleri veya sorgu seçeneklerini URI hizmet işlemi dönüş türüne bağlı olarak eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="afc46-154">Additional path segments or query options may be added to the URI depending on the return type of the service operation.</span></span> <span data-ttu-id="afc46-155">Örneğin, aşağıdaki URI erişen bir `GetOrdersByCity` döndüren işlemi bir <xref:System.Linq.IQueryable%601> koleksiyonu `Orders` göre sıralanmış nesneleri `RequiredDate` ilgili birlikte azalan `Order_Details` nesneler:</span><span class="sxs-lookup"><span data-stu-id="afc46-155">For example, the following URI accesses a `GetOrdersByCity` operation that returns an <xref:System.Linq.IQueryable%601> collection of `Orders` objects, ordered by `RequiredDate` in descending order, along with the related `Order_Details` objects:</span></span>  
  
```  
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc  
```  
  
## <a name="service-operations-access-control"></a><span data-ttu-id="afc46-156">Hizmet işlemleri erişim denetimi</span><span class="sxs-lookup"><span data-stu-id="afc46-156">Service Operations Access Control</span></span>  
 <span data-ttu-id="afc46-157">Hizmet geneli görünürlüğünü hizmet işlemleri tarafından denetlenir <xref:System.Data.Services.IDataServiceConfiguration.SetServiceOperationAccessRule%2A> yöntemi <xref:System.Data.Services.IDataServiceConfiguration> varlık görünürlüğü kümesi benzer şekilde sınıfında kullanılarak denetlenir <xref:System.Data.Services.IDataServiceConfiguration.SetEntitySetAccessRule%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="afc46-157">Service-wide visibility of service operations is controlled by the <xref:System.Data.Services.IDataServiceConfiguration.SetServiceOperationAccessRule%2A> method on the <xref:System.Data.Services.IDataServiceConfiguration> class in much the same way that entity set visibility is controlled by using the <xref:System.Data.Services.IDataServiceConfiguration.SetEntitySetAccessRule%2A> method.</span></span> <span data-ttu-id="afc46-158">Örneğin, veri hizmeti tanımı kod aşağıdaki satırı erişimini etkinleştirir `CustomersByCity` hizmet işlemi.</span><span class="sxs-lookup"><span data-stu-id="afc46-158">For example, the following line of code in the data service definition enables access to the `CustomersByCity` service operation.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationconfig)]
 [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationconfig)]  
  
> [!NOTE]
>  <span data-ttu-id="afc46-159">Bir hizmet işlemi temel varlık kümeleri erişimi kısıtlayarak gizli bir dönüş türü varsa, hizmet işlemini istemci uygulamaları için kullanılabilir olmaz.</span><span class="sxs-lookup"><span data-stu-id="afc46-159">If a service operation has a return type that has been hidden by restricting access on the underlying entity sets, then the service operation will not be available to client applications.</span></span>  
  
 <span data-ttu-id="afc46-160">Daha fazla bilgi için bkz: [nasıl yapılır: bir hizmet işlemi tanımlamak](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="afc46-160">For more information, see [How to: Define a Service Operation](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md).</span></span>  
  
## <a name="raising-exceptions"></a><span data-ttu-id="afc46-161">Özel durumlarını oluşturma</span><span class="sxs-lookup"><span data-stu-id="afc46-161">Raising Exceptions</span></span>  
 <span data-ttu-id="afc46-162">Kullanmanızı öneririz <xref:System.Data.Services.DataServiceException> bir özel durum veri hizmeti yürütmesinde Yükselt her sınıf.</span><span class="sxs-lookup"><span data-stu-id="afc46-162">We recommend that you use the <xref:System.Data.Services.DataServiceException> class whenever you raise an exception in the data service execution.</span></span> <span data-ttu-id="afc46-163">Veri Hizmeti çalışma zamanı bildiği için bu özel durum nesnesi özelliklerini doğru HTTP yanıt iletisi eşleme budur.</span><span class="sxs-lookup"><span data-stu-id="afc46-163">This is because the data service runtime knows how to map properties of this exception object correctly to the HTTP response message.</span></span> <span data-ttu-id="afc46-164">Yükselttiğinizde bir <xref:System.Data.Services.DataServiceException> döndürülen özel durum bir hizmet işlemi sarmalanmış bir <xref:System.Reflection.TargetInvocationException>.</span><span class="sxs-lookup"><span data-stu-id="afc46-164">When you raise a <xref:System.Data.Services.DataServiceException> in a service operation, the returned exception is wrapped in a <xref:System.Reflection.TargetInvocationException>.</span></span> <span data-ttu-id="afc46-165">Temel döndürülecek <xref:System.Data.Services.DataServiceException> kapsayan olmadan <xref:System.Reflection.TargetInvocationException>, geçersiz kılmanız gerekir <xref:System.Data.Services.DataService%601.HandleException%2A> yönteminde <xref:System.Data.Services.DataService%601>, ayıklamak <xref:System.Data.Services.DataServiceException> gelen <xref:System.Reflection.TargetInvocationException>ve aşağıdaki örnekteki gibi üst düzey hata olarak döndürün:</span><span class="sxs-lookup"><span data-stu-id="afc46-165">To return the base <xref:System.Data.Services.DataServiceException> without the enclosing <xref:System.Reflection.TargetInvocationException>, you must override the <xref:System.Data.Services.DataService%601.HandleException%2A> method in the <xref:System.Data.Services.DataService%601>, extract the <xref:System.Data.Services.DataServiceException> from the <xref:System.Reflection.TargetInvocationException>, and return it as the top-level error, as in the following example:</span></span>  
  
 [!code-csharp[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#handleexceptions)]
 [!code-vb[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#handleexceptions)]  
  
## <a name="see-also"></a><span data-ttu-id="afc46-166">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="afc46-166">See Also</span></span>  
 [<span data-ttu-id="afc46-167">Durdurucular</span><span class="sxs-lookup"><span data-stu-id="afc46-167">Interceptors</span></span>](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md)
