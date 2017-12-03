---
title: "Veri Sözleşmesi Bilinen Türler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], known types
- KnownTypeAttribute [WCF]
- KnownTypes [WCF]
ms.assetid: 1a0baea1-27b7-470d-9136-5bbad86c4337
caps.latest.revision: "42"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cdb9e539d16b874ffd37b8e381757594561386e7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="data-contract-known-types"></a><span data-ttu-id="a87bc-102">Veri Sözleşmesi Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="a87bc-102">Data Contract Known Types</span></span>
<span data-ttu-id="a87bc-103"><xref:System.Runtime.Serialization.KnownTypeAttribute> Sınıfı, öncelikli göz önünde bulundurarak seri durumdan çıkarma sırasında için dahil edilecek türleri belirtmenize olanak verir.</span><span class="sxs-lookup"><span data-stu-id="a87bc-103">The <xref:System.Runtime.Serialization.KnownTypeAttribute> class allows you to specify, in advance, the types that should be included for consideration during deserialization.</span></span> <span data-ttu-id="a87bc-104">Çalışan bir örnek için bkz: [bilinen türleri](../../../../docs/framework/wcf/samples/known-types.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="a87bc-104">For a working example, see the [Known Types](../../../../docs/framework/wcf/samples/known-types.md) example.</span></span>  
  
 <span data-ttu-id="a87bc-105">Normalde, parametreler ve dönüş değerleri bir istemci ve hizmet arasında geçirirken, her iki uç noktalar tüm aktarılacak olan verilerin veri sözleşmeleri paylaşır.</span><span class="sxs-lookup"><span data-stu-id="a87bc-105">Normally, when passing parameters and return values between a client and a service, both endpoints share all of the data contracts of the data to be transmitted.</span></span> <span data-ttu-id="a87bc-106">Ancak, aşağıdaki koşullarda durumda değil:</span><span class="sxs-lookup"><span data-stu-id="a87bc-106">However, this is not the case in the following circumstances:</span></span>  
  
-   <span data-ttu-id="a87bc-107">Gönderilen veri sözleşmesi beklenen veri sözleşmeden türetilir.</span><span class="sxs-lookup"><span data-stu-id="a87bc-107">The sent data contract is derived from the expected data contract.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="a87bc-108">Devralma hakkındaki bölüme [veri sözleşmesi eşitliği](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)).</span><span class="sxs-lookup"><span data-stu-id="a87bc-108"> the section about inheritance in [Data Contract Equivalence](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)).</span></span> <span data-ttu-id="a87bc-109">Bu durumda, aktarılan verilerin alıcı bitiş noktası tarafından beklendiği gibi sözleşme aynı veri yok.</span><span class="sxs-lookup"><span data-stu-id="a87bc-109">In that case, the transmitted data does not have the same data contract as expected by the receiving endpoint.</span></span>  
  
-   <span data-ttu-id="a87bc-110">Aktarılacak türü bilgileri için bir sınıf, yapı veya numaralandırma aksine bir arabirimdir.</span><span class="sxs-lookup"><span data-stu-id="a87bc-110">The declared type for the information to be transmitted is an interface, as opposed to a class, structure, or enumeration.</span></span> <span data-ttu-id="a87bc-111">Bu nedenle, bu önceden uygulayan arabirimi gerçekte gönderilir ve bu nedenle, alıcı endpoint iletilen veriler veri sözleşmesi önceden belirleyemiyor tür bilinmesi olamaz.</span><span class="sxs-lookup"><span data-stu-id="a87bc-111">Therefore, it cannot be known in advance which type that implements the interface is actually sent and therefore, the receiving endpoint cannot determine in advance the data contract for the transmitted data.</span></span>  
  
-   <span data-ttu-id="a87bc-112">Aktarılacak bildirilen türü bilgi <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="a87bc-112">The declared type for the information to be transmitted is <xref:System.Object>.</span></span> <span data-ttu-id="a87bc-113">Her tür devraldığı çünkü <xref:System.Object>ve bunu önceden hangi tür gerçekte gönderilen bilinmesi olamaz, alıcı uç noktası önceden iletilen veriler veri sözleşmesi belirleyemiyor.</span><span class="sxs-lookup"><span data-stu-id="a87bc-113">Because every type inherits from <xref:System.Object>, and it cannot be known in advance which type is actually sent, the receiving endpoint cannot determine in advance the data contract for the transmitted data.</span></span> <span data-ttu-id="a87bc-114">Bu bir ilk öğe özel durumdur: her veri sözleşmesi için oluşturulan bir boş veri sözleşmesi varsayılan türetilen <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="a87bc-114">This is a special case of the first item: Every data contract derives from the default, a blank data contract that is generated for <xref:System.Object>.</span></span>  
  
-   <span data-ttu-id="a87bc-115">Dahil bazı türleri [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türleri, önceki üç kategoriden birinde üyelerin sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a87bc-115">Some types, which include [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] types, have members that are in one of the preceding three categories.</span></span> <span data-ttu-id="a87bc-116">Örneğin, <xref:System.Collections.Hashtable> kullanan <xref:System.Object> karma tablosunda gerçek nesneleri depolamak için.</span><span class="sxs-lookup"><span data-stu-id="a87bc-116">For example, <xref:System.Collections.Hashtable> uses <xref:System.Object> to store the actual objects in the hash table.</span></span> <span data-ttu-id="a87bc-117">Bu tür serileştirme, alma tarafı önceden bu üyeler için veri sözleşmesi belirleyemiyor.</span><span class="sxs-lookup"><span data-stu-id="a87bc-117">When serializing these types, the receiving side cannot determine in advance the data contract for these members.</span></span>  
  
## <a name="the-knowntypeattribute-class"></a><span data-ttu-id="a87bc-118">KnownTypeAttribute sınıfı</span><span class="sxs-lookup"><span data-stu-id="a87bc-118">The KnownTypeAttribute Class</span></span>  
 <span data-ttu-id="a87bc-119">Veri alma bir bitiş noktasına ulaştığında [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çalışma zamanı verileri bir ortak dil çalışma zamanı (CLR) türünün bir örneği seri durumdan dener.</span><span class="sxs-lookup"><span data-stu-id="a87bc-119">When data arrives at a receiving endpoint, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime attempts to deserialize the data into an instance of a common language runtime (CLR) type.</span></span> <span data-ttu-id="a87bc-120">İlk veri belirlemek için gelen ileti sözleşme iletinin içeriğini uygun olması inceleyerek çıkarma için örneği türü seçilir.</span><span class="sxs-lookup"><span data-stu-id="a87bc-120">The type that is instantiated for deserialization is chosen by first inspecting the incoming message to determine the data contract to which the contents of the message conform.</span></span> <span data-ttu-id="a87bc-121">Seri durumdan çıkarma altyapısı sonra ileti içeriği ile uyumlu bir veri sözleşmesi uygulayan bir CLR türü bulmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="a87bc-121">The deserialization engine then attempts to find a CLR type that implements a data contract compatible with the message contents.</span></span> <span data-ttu-id="a87bc-122">Bu işlem sırasında seri durumdan çıkarma altyapısı izin veren adayı türleri kümesi "bilinen türler." seri kaldırıcı'nın kümesi verilir</span><span class="sxs-lookup"><span data-stu-id="a87bc-122">The set of candidate types that the deserialization engine allows for during this process is referred to as the deserializer's set of "known types."</span></span>  
  
 <span data-ttu-id="a87bc-123">Türü hakkında bilmeniz seri durumdan çıkarma altyapısı izin vermek için bir yoldur kullanarak <xref:System.Runtime.Serialization.KnownTypeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a87bc-123">One way to let the deserialization engine know about a type is by using the <xref:System.Runtime.Serialization.KnownTypeAttribute>.</span></span> <span data-ttu-id="a87bc-124">Öznitelik, yalnızca tüm veri sözleşme türleri için ayrı veri üyelerine uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="a87bc-124">The attribute cannot be applied to individual data members, only to whole data contract types.</span></span> <span data-ttu-id="a87bc-125">Öznitelik uygulanan bir *dış türü* bir sınıf veya bir yapı olabilir.</span><span class="sxs-lookup"><span data-stu-id="a87bc-125">The attribute is applied to an *outer type* that can be a class or a structure.</span></span> <span data-ttu-id="a87bc-126">En temel kullanımını öznitelik uygulama türü "bilinen bir tür olarak." belirtir</span><span class="sxs-lookup"><span data-stu-id="a87bc-126">In its most basic usage, applying the attribute specifies a type as a "known type."</span></span> <span data-ttu-id="a87bc-127">Bu bilinen türleri dış türünde bir nesne her bir parçası olarak bilinen türü neden olur veya üyeleri başvurulan herhangi bir nesne seri durumdan çıkarılmakta olan.</span><span class="sxs-lookup"><span data-stu-id="a87bc-127">This causes the known type to be a part of the set of known types whenever an object of the outer type or any object referred to through its members is being deserialized.</span></span> <span data-ttu-id="a87bc-128">Birden fazla <xref:System.Runtime.Serialization.KnownTypeAttribute> özniteliği aynı türüne uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="a87bc-128">More than one <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute can be applied to the same type.</span></span>  
  
## <a name="known-types-and-primitives"></a><span data-ttu-id="a87bc-129">Bilinen türleri ve temelleri</span><span class="sxs-lookup"><span data-stu-id="a87bc-129">Known Types and Primitives</span></span>  
 <span data-ttu-id="a87bc-130">İlkel türler olarak belirli türleri temel olarak kabul edilir (örneğin, <xref:System.DateTime> ve <xref:System.Xml.XmlElement>) her zaman "bilinen" ve hiçbir zaman bu mekanizma eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a87bc-130">Primitive types, as well as certain types treated as primitives (for example, <xref:System.DateTime> and <xref:System.Xml.XmlElement>) are always "known" and never have to be added through this mechanism.</span></span> <span data-ttu-id="a87bc-131">Ancak, ilkel türlerin dizileri açıkça eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a87bc-131">However, arrays of primitive types have to be added explicitly.</span></span> <span data-ttu-id="a87bc-132">Çoğu koleksiyonları diziler için eşdeğer olarak değerlendiriliyor.</span><span class="sxs-lookup"><span data-stu-id="a87bc-132">Most collections are considered equivalent to arrays.</span></span> <span data-ttu-id="a87bc-133">(Olmayan genel koleksiyonlar için dizileri eşdeğer değerlendirilir <xref:System.Object>).</span><span class="sxs-lookup"><span data-stu-id="a87bc-133">(Non-generic collections are considered equivalent to arrays of <xref:System.Object>).</span></span> <span data-ttu-id="a87bc-134">Kullanarak bir örnek temelleri, basit diziler ve ilkel koleksiyonlar, örnek 4 bakın.</span><span class="sxs-lookup"><span data-stu-id="a87bc-134">For an example of the using primitives, primitive arrays, and primitive collections, see Example 4.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a87bc-135">Başka ilkel türler aksine <xref:System.DateTimeOffset> yapısı değil varsayılan olarak, bilinen bir türe şekilde el ile bilinen türleri listesine eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="a87bc-135">Unlike other primitive types, the <xref:System.DateTimeOffset> structure is not a known type by default, so it must be manually added to the list of known types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="a87bc-136">Örnekler</span><span class="sxs-lookup"><span data-stu-id="a87bc-136">Examples</span></span>  
 <span data-ttu-id="a87bc-137">Aşağıdaki örneklerde gösterildiği <xref:System.Runtime.Serialization.KnownTypeAttribute> sınıfı kullanımda.</span><span class="sxs-lookup"><span data-stu-id="a87bc-137">The following examples show the <xref:System.Runtime.Serialization.KnownTypeAttribute> class in use.</span></span>  
  
#### <a name="example-1"></a><span data-ttu-id="a87bc-138">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="a87bc-138">Example 1</span></span>  
 <span data-ttu-id="a87bc-139">Üç sınıflarıyla bir devralma ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="a87bc-139">There are three classes with an inheritance relationship.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#1)]
 [!code-vb[C_KnownTypeAttribute#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#1)]  
  
 <span data-ttu-id="a87bc-140">Aşağıdaki `CompanyLogo` sınıfı hale getirilebilir, varsa kaldırılamaz ancak `ShapeOfLogo` üye olarak ayarlanmış çok ya da bir `CircleType` veya `TriangleType` nesne seri durumdan çıkarma altyapısı herhangi bir veri sözleşmesi adları türleriyle tanımadığından " Daire"veya"Üçgen."</span><span class="sxs-lookup"><span data-stu-id="a87bc-140">The following `CompanyLogo` class can be serialized, but cannot be deserialized if the `ShapeOfLogo` member is set to either a `CircleType` or a `TriangleType` object, because the deserialization engine does not recognize any types with data contract names "Circle" or "Triangle."</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#2)]
 [!code-vb[C_KnownTypeAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#2)]  
  
 <span data-ttu-id="a87bc-141">Yazmak için doğru bir şekilde `CompanyLogo` türü aşağıdaki kodda gösterilir.</span><span class="sxs-lookup"><span data-stu-id="a87bc-141">The correct way to write the `CompanyLogo` type is shown in the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#3)]
 [!code-vb[C_KnownTypeAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#3)]  
  
 <span data-ttu-id="a87bc-142">Her dış türü `CompanyLogo2` olan bildiği seri durumdan çıkarma altyapısı seri durumdan çıkarılmakta `CircleType` ve `TriangleType` ve bu nedenle, eşleşen türleri için "Daire" ve "Üçgen" veri sözleşmeleri bulamıyor.</span><span class="sxs-lookup"><span data-stu-id="a87bc-142">Whenever the outer type `CompanyLogo2` is being deserialized, the deserialization engine knows about `CircleType` and `TriangleType` and, therefore, is able to find matching types for the "Circle" and "Triangle" data contracts.</span></span>  
  
#### <a name="example-2"></a><span data-ttu-id="a87bc-143">Örnek 2</span><span class="sxs-lookup"><span data-stu-id="a87bc-143">Example 2</span></span>  
 <span data-ttu-id="a87bc-144">Aşağıdaki örnekte, olsa da her ikisini de `CustomerTypeA` ve `CustomerTypeB` sahip `Customer` veri sözleşmesi, örneği `CustomerTypeB` ne zaman oluşturulur bir `PurchaseOrder` , çünkü seri durumdan olan yalnızca `CustomerTypeB` bilinen seri durumdan çıkarma altyapısı.</span><span class="sxs-lookup"><span data-stu-id="a87bc-144">In the following example, even though both `CustomerTypeA` and `CustomerTypeB` have the `Customer` data contract, an instance of `CustomerTypeB` is created whenever a `PurchaseOrder` is deserialized, because only `CustomerTypeB` is known to the deserialization engine.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#4)]
 [!code-vb[C_KnownTypeAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#4)]  
  
#### <a name="example-3"></a><span data-ttu-id="a87bc-145">Örnek 3</span><span class="sxs-lookup"><span data-stu-id="a87bc-145">Example 3</span></span>  
 <span data-ttu-id="a87bc-146">Aşağıdaki örnekte, bir <xref:System.Collections.Hashtable> içeriğinin depolar dahili olarak <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="a87bc-146">In the following example, a <xref:System.Collections.Hashtable> stores its contents internally as <xref:System.Object>.</span></span> <span data-ttu-id="a87bc-147">Başarıyla bir karma tablosu seri durumdan çıkarılacak seri durumdan çıkarma altyapısı var. oluşabilecek olası türleri kümesini bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a87bc-147">To successfully deserialize a hash table, the deserialization engine must know the set of possible types that can occur there.</span></span> <span data-ttu-id="a87bc-148">Bu durumda, önceden yalnızca biliyoruz `Book` ve `Magazine` nesneleri depolanır `Catalog`, bu kullanılarak eklenen <xref:System.Runtime.Serialization.KnownTypeAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a87bc-148">In this case, we know in advance that only `Book` and `Magazine` objects are stored in the `Catalog`, so those are added using the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#5)]
 [!code-vb[C_KnownTypeAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#5)]  
  
#### <a name="example-4"></a><span data-ttu-id="a87bc-149">Örnek 4</span><span class="sxs-lookup"><span data-stu-id="a87bc-149">Example 4</span></span>  
 <span data-ttu-id="a87bc-150">Aşağıdaki örnekte, bir sayı ve bir işlem sayısına gerçekleştirmek için bir veri sözleşmesi depolar.</span><span class="sxs-lookup"><span data-stu-id="a87bc-150">In the following example, a data contract stores a number and an operation to perform on the number.</span></span> <span data-ttu-id="a87bc-151">`Numbers` Veri üyesi dizisi, bir tamsayı olabilir veya bir <xref:System.Collections.Generic.List%601> tamsayılar içerir.</span><span class="sxs-lookup"><span data-stu-id="a87bc-151">The `Numbers` data member can be an integer, an array of integers, or a <xref:System.Collections.Generic.List%601> that contains integers.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="a87bc-152">Bu yalnızca istemci tarafında çalışmayacak SVCUTIL. EXE WCF proxy oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a87bc-152">This will only work on the client side if SVCUTIL.EXE is used to generate a WCF proxy.</span></span> <span data-ttu-id="a87bc-153">SVCUTIL. EXE herhangi bilinen türleri dahil olmak üzere hizmetinden meta verilerini alır.</span><span class="sxs-lookup"><span data-stu-id="a87bc-153">SVCUTIL.EXE retrieves metadata from the service including any known types.</span></span> <span data-ttu-id="a87bc-154">Bu bilgiler olmadan bir istemci türleri seri durumdan mümkün olmaz.</span><span class="sxs-lookup"><span data-stu-id="a87bc-154">Without this information a client will not be able to deserialize the types.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#6)]
 [!code-vb[C_KnownTypeAttribute#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#6)]  
  
 <span data-ttu-id="a87bc-155">Uygulama kodu budur.</span><span class="sxs-lookup"><span data-stu-id="a87bc-155">This is the application code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#7)]
 [!code-vb[C_KnownTypeAttribute#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#7)]  
  
## <a name="known-types-inheritance-and-interfaces"></a><span data-ttu-id="a87bc-156">Bilinen türler, devralma ve arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a87bc-156">Known Types, Inheritance, and Interfaces</span></span>  
 <span data-ttu-id="a87bc-157">Bilinen bir türe olduğunda belirli türünü kullanarak ilişkili `KnownTypeAttribute` özniteliği, bilinen türü de türetilmiş türler bu türdeki tüm ile ilişkili.</span><span class="sxs-lookup"><span data-stu-id="a87bc-157">When a known type is associated with a particular type using the `KnownTypeAttribute` attribute, the known type is also associated with all of the derived types of that type.</span></span> <span data-ttu-id="a87bc-158">Örneğin, aşağıdaki kodu bakın.</span><span class="sxs-lookup"><span data-stu-id="a87bc-158">For example, see the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#8)]
 [!code-vb[C_KnownTypeAttribute#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#8)]  
  
 <span data-ttu-id="a87bc-159">`DoubleDrawing` Sınıfı gerektirmez `KnownTypeAttribute` kullanmak için öznitelik `Square` ve `Circle` içinde `AdditionalShape` , çünkü alan temel sınıfı (`Drawing`) zaten uygulanan bu özniteliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a87bc-159">The `DoubleDrawing` class does not require the `KnownTypeAttribute` attribute to use `Square` and `Circle` in the `AdditionalShape` field, because the base class (`Drawing`) already has these attributes applied.</span></span>  
  
 <span data-ttu-id="a87bc-160">Bilinen türler yalnızca sınıfları ve yapıları, arabirimler değil ile ilişkili olabilir.</span><span class="sxs-lookup"><span data-stu-id="a87bc-160">Known types can be associated only with classes and structures, not interfaces.</span></span>  
  
## <a name="known-types-using-open-generic-methods"></a><span data-ttu-id="a87bc-161">Açık genel yöntemler kullanarak bilinen türler</span><span class="sxs-lookup"><span data-stu-id="a87bc-161">Known Types Using Open Generic Methods</span></span>  
 <span data-ttu-id="a87bc-162">Genel bir tür bilinen bir türe eklemek gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="a87bc-162">It may be necessary to add a generic type as a known type.</span></span> <span data-ttu-id="a87bc-163">Ancak, açık genel tür parametre olarak gönderilemez. `KnownTypeAttribute` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a87bc-163">However, an open generic type cannot be passed as a parameter to the `KnownTypeAttribute` attribute.</span></span>  
  
 <span data-ttu-id="a87bc-164">Alternatif bir mekanizma kullanarak bu sorun çözülebilir: bilinen türleri koleksiyona eklemek için türlerinin bir listesini döndüren bir yöntem yazma.</span><span class="sxs-lookup"><span data-stu-id="a87bc-164">This problem can be solved by using an alternative mechanism: Write a method that returns a list of types to add to the known types collection.</span></span> <span data-ttu-id="a87bc-165">Yöntemin adını sonra bir dize bağımsız değişkeni olarak belirtilen `KnownTypeAttribute` bazı kısıtlamalar nedeniyle özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a87bc-165">The name of the method is then specified as a string argument to the `KnownTypeAttribute` attribute due to some restrictions.</span></span>  
  
 <span data-ttu-id="a87bc-166">Yöntemi hangi türünde bulunmalıdır `KnownTypeAttribute` özniteliği uygulanır, statik olmalıdır, herhangi bir parametre kabul etmeniz gerekir ve atanabilir bir nesne döndürmelidir <xref:System.Collections.IEnumerable> , <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="a87bc-166">The method must exist on the type to which the `KnownTypeAttribute` attribute is applied, must be static, must accept no parameters, and must return an object that can be assigned to <xref:System.Collections.IEnumerable> of <xref:System.Type>.</span></span>  
  
 <span data-ttu-id="a87bc-167">Birleştiremez `KnownTypeAttribute` bir yöntem adı özniteliğiyle ve `KnownTypeAttribute` gerçek türlerinde aynı türde olan öznitelikler.</span><span class="sxs-lookup"><span data-stu-id="a87bc-167">You cannot combine the `KnownTypeAttribute` attribute with a method name and `KnownTypeAttribute` attributes with actual types on the same type.</span></span> <span data-ttu-id="a87bc-168">Ayrıca, birden fazla uygulanamıyor `KnownTypeAttribute` bir yöntem adı aynı türe sahip.</span><span class="sxs-lookup"><span data-stu-id="a87bc-168">Furthermore, you cannot apply more than one `KnownTypeAttribute` with a method name to the same type.</span></span>  
  
 <span data-ttu-id="a87bc-169">Aşağıdaki sınıf bakın.</span><span class="sxs-lookup"><span data-stu-id="a87bc-169">See the following class.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#9)]
 [!code-vb[C_KnownTypeAttribute#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#9)]  
  
 <span data-ttu-id="a87bc-170">`theDrawing` Alan genel bir sınıf örneklerini içerir `ColorDrawing` ve genel bir sınıf `BlackAndWhiteDrawing`, her ikisi de bir genel sınıfından `Drawing`.</span><span class="sxs-lookup"><span data-stu-id="a87bc-170">The `theDrawing` field contains instances of a generic class `ColorDrawing` and a generic class `BlackAndWhiteDrawing`, both of which inherit from a generic class `Drawing`.</span></span> <span data-ttu-id="a87bc-171">Normalde, hem bilinen türleri eklenmesi gerekir, ancak şu öznitelikler için geçerli sözdizimi değil.</span><span class="sxs-lookup"><span data-stu-id="a87bc-171">Normally, both must be added to known types, but the following is not valid syntax for attributes.</span></span>  
  
```csharp  
// Invalid syntax for attributes:  
// [KnownType(typeof(ColorDrawing<T>))]  
// [KnownType(typeof(BlackAndWhiteDrawing<T>))]  
```  
  
```vb  
' Invalid syntax for attributes:  
' <KnownType(GetType(ColorDrawing(Of T))), _  
' KnownType(GetType(BlackAndWhiteDrawing(Of T)))>  
```  
  
 <span data-ttu-id="a87bc-172">Bu nedenle, bu tür döndürmek için bir yöntem oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a87bc-172">Thus, a method must be created to return these types.</span></span> <span data-ttu-id="a87bc-173">Bu tür yazmak için doğru bir şekilde daha sonra aşağıdaki kodda gösterilir.</span><span class="sxs-lookup"><span data-stu-id="a87bc-173">The correct way to write this type, then, is shown in the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#10)]
 [!code-vb[C_KnownTypeAttribute#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#10)]  
  
## <a name="additional-ways-to-add-known-types"></a><span data-ttu-id="a87bc-174">Bilinen türler eklemek için başka bir yolu</span><span class="sxs-lookup"><span data-stu-id="a87bc-174">Additional Ways to Add Known Types</span></span>  
 <span data-ttu-id="a87bc-175">Ayrıca, bilinen türleri bir yapılandırma dosyası eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="a87bc-175">Additionally, known types can be added through a configuration file.</span></span> <span data-ttu-id="a87bc-176">Uygun seri durumdan çıkarma üçüncü taraf kullanarak yazdığınızda kitaplıklarıyla gibi bilinen türleri gerektiren türü kontrol etmez gerektiğinde bu faydalıdır [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a87bc-176">This is useful when you do not control the type that requires known types for proper deserialization, such as when using third-party type libraries with [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span>  
  
 <span data-ttu-id="a87bc-177">Aşağıdaki yapılandırma dosyası, bilinen bir türe bir yapılandırma dosyası belirtmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a87bc-177">The following configuration file shows how to specify a known type in a configuration file.</span></span>  
  
 `<configuration>`  
  
 `<system.runtime.serialization>`  
  
 `<dataContractSerializer>`  
  
 `<declaredTypes>`  
  
 `<add type="MyCompany.Library.Shape,`  
  
 `MyAssembly, Version=2.0.0.0, Culture=neutral,`  
  
 `PublicKeyToken=XXXXXX, processorArchitecture=MSIL">`  
  
 `<knownType type="MyCompany.Library.Circle,`  
  
 `MyAssembly, Version=2.0.0.0, Culture=neutral,`  
  
 `PublicKeyToken=XXXXXX, processorArchitecture=MSIL"/>`  
  
 `</add>`  
  
 `</declaredTypes>`  
  
 `</dataContractSerializer>`  
  
 `</system.runtime.serialization>`  
  
 `</configuration>`  
  
 <span data-ttu-id="a87bc-178">Adlı bir veri sözleşmesi türü yukarıdaki yapılandırmada dosya `MyCompany.Library.Shape` sağlamak için bildirilen `MyCompany.Library.Circle` bilinen türü.</span><span class="sxs-lookup"><span data-stu-id="a87bc-178">In the preceding configuration file a data contract type called `MyCompany.Library.Shape` is declared to have `MyCompany.Library.Circle` as a known type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a87bc-179">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a87bc-179">See Also</span></span>  
 <xref:System.Runtime.Serialization.KnownTypeAttribute>  
 <xref:System.Collections.Hashtable>  
 <xref:System.Object>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A>  
 [<span data-ttu-id="a87bc-180">Bilinen türler</span><span class="sxs-lookup"><span data-stu-id="a87bc-180">Known Types</span></span>](../../../../docs/framework/wcf/samples/known-types.md)  
 [<span data-ttu-id="a87bc-181">Veri sözleşmesi eşitliği</span><span class="sxs-lookup"><span data-stu-id="a87bc-181">Data Contract Equivalence</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [<span data-ttu-id="a87bc-182">Hizmet sözleşmeleri tasarlama</span><span class="sxs-lookup"><span data-stu-id="a87bc-182">Designing Service Contracts</span></span>](../../../../docs/framework/wcf/designing-service-contracts.md)
