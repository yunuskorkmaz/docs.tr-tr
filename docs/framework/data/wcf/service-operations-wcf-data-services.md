---
description: 'Hakkında daha fazla bilgi edinin: hizmet Işlemleri (WCF Veri Hizmetleri)'
title: Hizmet Işlemleri (WCF Veri Hizmetleri)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: 583a690a-e60f-4990-8991-d6efce069d76
ms.openlocfilehash: 3c811da86b1654f33675b46575d45884a6ba9b1f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773101"
---
# <a name="service-operations-wcf-data-services"></a><span data-ttu-id="a34e0-103">Hizmet Işlemleri (WCF Veri Hizmetleri)</span><span class="sxs-lookup"><span data-stu-id="a34e0-103">Service Operations (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="a34e0-104">WCF Veri Hizmetleri, sunucuda Yöntemler sergilemek için bir veri hizmetinde hizmet işlemleri tanımlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a34e0-104">WCF Data Services enables you to define service operations on a data service to expose methods on the server.</span></span> <span data-ttu-id="a34e0-105">Diğer veri hizmeti kaynakları gibi hizmet işlemleri de URI 'Ler tarafından karşılanır.</span><span class="sxs-lookup"><span data-stu-id="a34e0-105">Like other data service resources, service operations are addressed by URIs.</span></span> <span data-ttu-id="a34e0-106">Hizmet işlemleri, doğrulama mantığını uygulamak, rol tabanlı güvenlik uygulamak veya özelleştirilmiş sorgulama yeteneklerini göstermek gibi bir veri hizmetinde iş mantığını kullanıma sunmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a34e0-106">Service operations enable you to expose business logic in a data service, such as to implement validation logic, to apply role-based security, or to expose specialized querying capabilities.</span></span> <span data-ttu-id="a34e0-107">Hizmet işlemleri, ' den türetilen veri hizmeti sınıfına eklenen yöntemlerdir <xref:System.Data.Services.DataService%601> .</span><span class="sxs-lookup"><span data-stu-id="a34e0-107">Service operations are methods added to the data service class that derives from <xref:System.Data.Services.DataService%601>.</span></span> <span data-ttu-id="a34e0-108">Diğer tüm veri hizmeti kaynakları gibi, hizmet işlemi metoduna parametreler sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a34e0-108">Like all other data service resources, you can supply parameters to the service operation method.</span></span> <span data-ttu-id="a34e0-109">Örneğin, aşağıdaki hizmet işlemi URI 'SI ( [hızlı başlangıç](quickstart-wcf-data-services.md) veri hizmetine göre) değeri `London` parametreye geçirir `city` :</span><span class="sxs-lookup"><span data-stu-id="a34e0-109">For example, the following service operation URI (based on the [quickstart](quickstart-wcf-data-services.md) data service) passes the value `London` to the `city` parameter:</span></span>

```http
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'
```

<span data-ttu-id="a34e0-110">Bu hizmet işleminin tanımı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="a34e0-110">The definition for this service operation is as follows:</span></span>

[!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationdef)]
[!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationdef)]

<span data-ttu-id="a34e0-111"><xref:System.Data.Services.DataService%601.CurrentDataSource%2A> <xref:System.Data.Services.DataService%601> Veri hizmetinin kullandığı veri kaynağına doğrudan erişmek için öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a34e0-111">You can use the <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> of the <xref:System.Data.Services.DataService%601> to directly access the data source that the data service is using.</span></span> <span data-ttu-id="a34e0-112">Daha fazla bilgi için bkz. [nasıl yapılır: hizmet Işlemi tanımlama](how-to-define-a-service-operation-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="a34e0-112">For more information, see [How to: Define a Service Operation](how-to-define-a-service-operation-wcf-data-services.md).</span></span>

<span data-ttu-id="a34e0-113">Bir .NET Framework istemci uygulamasından bir hizmet işlemi çağırma hakkında daha fazla bilgi için bkz. [çağrı hizmeti işlemleri](calling-service-operations-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="a34e0-113">For information on how to call a service operation from a .NET Framework client application, see [Calling Service Operations](calling-service-operations-wcf-data-services.md).</span></span>

## <a name="service-operation-requirements"></a><span data-ttu-id="a34e0-114">Hizmet Işlemi gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="a34e0-114">Service Operation Requirements</span></span>

<span data-ttu-id="a34e0-115">Veri hizmetindeki hizmet işlemlerini tanımlarken aşağıdaki gereksinimler geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a34e0-115">The following requirements apply when defining service operations on the data service.</span></span> <span data-ttu-id="a34e0-116">Bir yöntem bu gereksinimleri karşılamıyorsa, veri hizmeti için bir hizmet işlemi olarak kullanıma sunulmaz.</span><span class="sxs-lookup"><span data-stu-id="a34e0-116">If a method does not meet these requirements, it will not be exposed as a service operation for the data service.</span></span>

- <span data-ttu-id="a34e0-117">İşlem, veri hizmeti sınıfının bir üyesi olan bir ortak örnek yöntemi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a34e0-117">The operation must be a public instance method that is a member of the data service class.</span></span>

- <span data-ttu-id="a34e0-118">İşlem yöntemi yalnızca giriş parametrelerini kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="a34e0-118">The operation method may only accept input parameters.</span></span> <span data-ttu-id="a34e0-119">İleti gövdesinde gönderilen verilere veri hizmeti tarafından erişilemiyor.</span><span class="sxs-lookup"><span data-stu-id="a34e0-119">Data sent in the message body cannot be accessed by the data service.</span></span>

- <span data-ttu-id="a34e0-120">Parametreler tanımlanmışsa, her parametrenin türü bir ilkel tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a34e0-120">If parameters are defined, the type of each parameter must be a primitive type.</span></span> <span data-ttu-id="a34e0-121">İlkel olmayan bir türdeki verilerin serileştirilmesi ve bir dize parametresine geçirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a34e0-121">Any data of a non-primitive type must be serialized and passed into a string parameter.</span></span>

- <span data-ttu-id="a34e0-122">Yöntemin aşağıdakilerden birini döndürmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="a34e0-122">The method must return one of the following:</span></span>

  - <span data-ttu-id="a34e0-123">`void` ( `Nothing` Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a34e0-123">`void` (`Nothing` in Visual Basic)</span></span>

  - <xref:System.Collections.Generic.IEnumerable%601>

  - <xref:System.Linq.IQueryable%601>

  - <span data-ttu-id="a34e0-124">Veri modelindeki veri hizmetinin sunduğu bir varlık türü.</span><span class="sxs-lookup"><span data-stu-id="a34e0-124">An entity type in the data model that the data service exposes.</span></span>

  - <span data-ttu-id="a34e0-125">Tamsayı veya dize gibi bir temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="a34e0-125">A primitive class such as integer or string.</span></span>

- <span data-ttu-id="a34e0-126">Sıralama, sayfalama ve filtreleme gibi sorgu seçeneklerini desteklemek için, hizmet işlemi yöntemleri döndürmelidir <xref:System.Linq.IQueryable%601> .</span><span class="sxs-lookup"><span data-stu-id="a34e0-126">In order to support query options such as sorting, paging, and filtering, service operation methods should return <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="a34e0-127">Sorgu seçeneklerini içeren hizmet işlemlerine yönelik istekler, yalnızca döndüren işlemler için reddedilir <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="a34e0-127">Requests to service operations that include query options are rejected for operations that only return <xref:System.Collections.Generic.IEnumerable%601>.</span></span>

- <span data-ttu-id="a34e0-128">Gezinti özelliklerini kullanarak ilgili varlıklara erişmeyi desteklemek için, hizmet işleminin döndürmesi gerekir <xref:System.Linq.IQueryable%601> .</span><span class="sxs-lookup"><span data-stu-id="a34e0-128">In order to support accessing related entities by using navigation properties, the service operation must return <xref:System.Linq.IQueryable%601>.</span></span>

- <span data-ttu-id="a34e0-129">Yöntemine `[WebGet]` veya özniteliğiyle açıklama eklenmelidir `[WebInvoke]` .</span><span class="sxs-lookup"><span data-stu-id="a34e0-129">The method must be annotated with the `[WebGet]` or `[WebInvoke]` attribute.</span></span>

  - <span data-ttu-id="a34e0-130">`[WebGet]` yöntemi bir GET isteği kullanılarak çağrılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a34e0-130">`[WebGet]` enables the method to be invoked by using a GET request.</span></span>

  - <span data-ttu-id="a34e0-131">`[WebInvoke(Method = "POST")]` yöntemin bir POST isteği kullanılarak çağrılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a34e0-131">`[WebInvoke(Method = "POST")]` enables the method to be invoked by using a POST request.</span></span> <span data-ttu-id="a34e0-132">Diğer <xref:System.ServiceModel.Web.WebInvokeAttribute> Yöntemler desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="a34e0-132">Other <xref:System.ServiceModel.Web.WebInvokeAttribute> methods are not supported.</span></span>

- <span data-ttu-id="a34e0-133">Bir hizmet işlemi, <xref:System.Data.Services.SingleResultAttribute> yöntemin dönüş değerinin bir varlık koleksiyonu yerine tek bir varlık olduğunu belirten ile birlikte açıklanmayabilir.</span><span class="sxs-lookup"><span data-stu-id="a34e0-133">A service operation may be annotated with the <xref:System.Data.Services.SingleResultAttribute> that specifies that the return value from the method is a single entity rather than a collection of entities.</span></span> <span data-ttu-id="a34e0-134">Bu ayrım, yanıtın sonuç serileştirmesini ve ek gezinti özelliği traversals URI içinde temsil edilme şeklini belirler.</span><span class="sxs-lookup"><span data-stu-id="a34e0-134">This distinction dictates the resulting serialization of the response and the manner in which additional navigation property traversals are represented in the URI.</span></span> <span data-ttu-id="a34e0-135">Örneğin, AtomPub serileştirme kullanılırken, tek bir kaynak türü örneği bir giriş öğesi ve bir örnek kümesi olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="a34e0-135">For example, when using AtomPub serialization, a single resource type instance is represented as an entry element and a set of instances as a feed element.</span></span>

## <a name="addressing-service-operations"></a><span data-ttu-id="a34e0-136">Hizmet Işlemlerini adresleme</span><span class="sxs-lookup"><span data-stu-id="a34e0-136">Addressing Service Operations</span></span>

<span data-ttu-id="a34e0-137">Bir URI 'nin ilk yol segmentine yöntemin adını yerleştirerek hizmet işlemlerine adres ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a34e0-137">You can address service operations by placing the name of the method in the first path segment of a URI.</span></span> <span data-ttu-id="a34e0-138">Örnek olarak, aşağıdaki URI bir `GetOrdersByState` nesne koleksiyonu döndüren bir işleme erişir <xref:System.Linq.IQueryable%601> `Orders` .</span><span class="sxs-lookup"><span data-stu-id="a34e0-138">As an example, the following URI accesses a `GetOrdersByState` operation that returns an <xref:System.Linq.IQueryable%601> collection of `Orders` objects.</span></span>

```http
http://localhost:12345/Northwind.svc/GetOrdersByState?state='CA'&includeItems=true
```

<span data-ttu-id="a34e0-139">Bir hizmet işlemi çağrılırken parametreler sorgu seçenekleri olarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="a34e0-139">When calling a service operation, parameters are supplied as query options.</span></span> <span data-ttu-id="a34e0-140">Önceki hizmet işlemi, bir dize parametresini `state` ve `includeItems` yanıtta ilgili nesnelerin eklenip eklenmeyeceğini gösteren bir Boolean parametresini kabul eder `Order_Detail` .</span><span class="sxs-lookup"><span data-stu-id="a34e0-140">The previous service operation accepts both a string parameter `state` and a Boolean parameter `includeItems` that indicates whether to include related `Order_Detail` objects in the response.</span></span>

<span data-ttu-id="a34e0-141">Aşağıda, bir hizmet işlemi için geçerli dönüş türleri verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="a34e0-141">The following are valid return types for a service operation:</span></span>

|<span data-ttu-id="a34e0-142">Geçerli dönüş türleri</span><span class="sxs-lookup"><span data-stu-id="a34e0-142">Valid Return Types</span></span>|<span data-ttu-id="a34e0-143">URI kuralları</span><span class="sxs-lookup"><span data-stu-id="a34e0-143">URI Rules</span></span>|
|------------------------|---------------|
|<span data-ttu-id="a34e0-144">`void` ( `Nothing` Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a34e0-144">`void` (`Nothing` in Visual Basic)</span></span><br /><br /> <span data-ttu-id="a34e0-145">-veya-</span><span class="sxs-lookup"><span data-stu-id="a34e0-145">-or-</span></span><br /><br /> <span data-ttu-id="a34e0-146">Varlık türleri</span><span class="sxs-lookup"><span data-stu-id="a34e0-146">Entity types</span></span><br /><br /> <span data-ttu-id="a34e0-147">-veya-</span><span class="sxs-lookup"><span data-stu-id="a34e0-147">-or-</span></span><br /><br /> <span data-ttu-id="a34e0-148">İlkel türler</span><span class="sxs-lookup"><span data-stu-id="a34e0-148">Primitive types</span></span>|<span data-ttu-id="a34e0-149">URI, hizmet işleminin adı olan tek bir yol kesimi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a34e0-149">The URI must be a single path segment that is the name of the service operation.</span></span> <span data-ttu-id="a34e0-150">Sorgu seçeneklerine izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="a34e0-150">Query options are not allowed.</span></span>|
|<xref:System.Collections.Generic.IEnumerable%601>|<span data-ttu-id="a34e0-151">URI, hizmet işleminin adı olan tek bir yol kesimi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a34e0-151">The URI must be a single path segment that is the name of the service operation.</span></span> <span data-ttu-id="a34e0-152">Sonuç türü bir <xref:System.Linq.IQueryable%601> tür olmadığından, sorgu seçeneklerine izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="a34e0-152">Because the result type is not an <xref:System.Linq.IQueryable%601> type, query options are not allowed.</span></span>|
|<xref:System.Linq.IQueryable%601>|<span data-ttu-id="a34e0-153">Hizmet işleminin adı olan yola ek olarak sorgu yolu kesimleri izin verilir.</span><span class="sxs-lookup"><span data-stu-id="a34e0-153">Query path segments in addition to the path that is the name of the service operation are allowed.</span></span> <span data-ttu-id="a34e0-154">Sorgu seçeneklerine de izin verilir.</span><span class="sxs-lookup"><span data-stu-id="a34e0-154">Query options are also allowed.</span></span>|

<span data-ttu-id="a34e0-155">Ek yol kesimleri veya sorgu seçenekleri, hizmet işleminin dönüş türüne bağlı olarak URI 'ye eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="a34e0-155">Additional path segments or query options may be added to the URI depending on the return type of the service operation.</span></span> <span data-ttu-id="a34e0-156">Örneğin, aşağıdaki URI, `GetOrdersByCity` <xref:System.Linq.IQueryable%601> `Orders` `RequiredDate` ilişkili nesnelerle birlikte azalan düzende sıralanmış bir nesne koleksiyonu döndüren bir işleme erişir `Order_Details` :</span><span class="sxs-lookup"><span data-stu-id="a34e0-156">For example, the following URI accesses a `GetOrdersByCity` operation that returns an <xref:System.Linq.IQueryable%601> collection of `Orders` objects, ordered by `RequiredDate` in descending order, along with the related `Order_Details` objects:</span></span>

```http
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc
```

## <a name="service-operations-access-control"></a><span data-ttu-id="a34e0-157">Hizmet Işlemleri Access Control</span><span class="sxs-lookup"><span data-stu-id="a34e0-157">Service Operations Access Control</span></span>

<span data-ttu-id="a34e0-158">Hizmet genelinde hizmet işlemlerinin, <xref:System.Data.Services.IDataServiceConfiguration.SetServiceOperationAccessRule%2A> <xref:System.Data.Services.IDataServiceConfiguration> varlık kümesi görünürlüğün yöntemi kullanılarak denetlenen şekilde, sınıftaki yöntemi tarafından denetlenir <xref:System.Data.Services.IDataServiceConfiguration.SetEntitySetAccessRule%2A> .</span><span class="sxs-lookup"><span data-stu-id="a34e0-158">Service-wide visibility of service operations is controlled by the <xref:System.Data.Services.IDataServiceConfiguration.SetServiceOperationAccessRule%2A> method on the <xref:System.Data.Services.IDataServiceConfiguration> class in much the same way that entity set visibility is controlled by using the <xref:System.Data.Services.IDataServiceConfiguration.SetEntitySetAccessRule%2A> method.</span></span> <span data-ttu-id="a34e0-159">Örneğin, veri hizmeti tanımındaki aşağıdaki kod satırı `CustomersByCity` hizmet işlemine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="a34e0-159">For example, the following line of code in the data service definition enables access to the `CustomersByCity` service operation.</span></span>

[!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationconfig)]
[!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationconfig)]

> [!NOTE]
> <span data-ttu-id="a34e0-160">Bir hizmet işleminin, temel varlık kümelerindeki erişimi kısıtlayarak gizlenmiş bir dönüş türü varsa, hizmet işlemi istemci uygulamalar tarafından kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a34e0-160">If a service operation has a return type that has been hidden by restricting access on the underlying entity sets, then the service operation will not be available to client applications.</span></span>

<span data-ttu-id="a34e0-161">Daha fazla bilgi için bkz. [nasıl yapılır: hizmet Işlemi tanımlama](how-to-define-a-service-operation-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="a34e0-161">For more information, see [How to: Define a Service Operation](how-to-define-a-service-operation-wcf-data-services.md).</span></span>

## <a name="raising-exceptions"></a><span data-ttu-id="a34e0-162">Özel durumları yükseltme</span><span class="sxs-lookup"><span data-stu-id="a34e0-162">Raising Exceptions</span></span>

<span data-ttu-id="a34e0-163"><xref:System.Data.Services.DataServiceException>Veri hizmeti yürütmesinde bir özel durum her yükselttiğinizde, sınıfını kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="a34e0-163">We recommend that you use the <xref:System.Data.Services.DataServiceException> class whenever you raise an exception in the data service execution.</span></span> <span data-ttu-id="a34e0-164">Bunun nedeni, veri hizmeti çalışma zamanının bu özel durum nesnesinin özelliklerinin HTTP yanıt iletisine doğru bir şekilde nasıl eşleneceğini biliyor olması.</span><span class="sxs-lookup"><span data-stu-id="a34e0-164">This is because the data service runtime knows how to map properties of this exception object correctly to the HTTP response message.</span></span> <span data-ttu-id="a34e0-165">Bir <xref:System.Data.Services.DataServiceException> hizmet işleminde bir hizmeti yükselttiğinizde, döndürülen özel durum bir içinde sarmalanır <xref:System.Reflection.TargetInvocationException> .</span><span class="sxs-lookup"><span data-stu-id="a34e0-165">When you raise a <xref:System.Data.Services.DataServiceException> in a service operation, the returned exception is wrapped in a <xref:System.Reflection.TargetInvocationException>.</span></span> <span data-ttu-id="a34e0-166">Temeli kapsayan olmadan döndürmek için, <xref:System.Data.Services.DataServiceException> <xref:System.Reflection.TargetInvocationException> <xref:System.Data.Services.DataService%601.HandleException%2A> içindeki yöntemini geçersiz kılmanız <xref:System.Data.Services.DataService%601> , öğesinden ayıklamalısınız <xref:System.Data.Services.DataServiceException> <xref:System.Reflection.TargetInvocationException> ve en üst düzey hata olarak, aşağıdaki örnekte olduğu gibi döndürün:</span><span class="sxs-lookup"><span data-stu-id="a34e0-166">To return the base <xref:System.Data.Services.DataServiceException> without the enclosing <xref:System.Reflection.TargetInvocationException>, you must override the <xref:System.Data.Services.DataService%601.HandleException%2A> method in the <xref:System.Data.Services.DataService%601>, extract the <xref:System.Data.Services.DataServiceException> from the <xref:System.Reflection.TargetInvocationException>, and return it as the top-level error, as in the following example:</span></span>

[!code-csharp[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#handleexceptions)]
[!code-vb[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#handleexceptions)]

## <a name="see-also"></a><span data-ttu-id="a34e0-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a34e0-167">See also</span></span>

- [<span data-ttu-id="a34e0-168">Durdurucular</span><span class="sxs-lookup"><span data-stu-id="a34e0-168">Interceptors</span></span>](interceptors-wcf-data-services.md)
