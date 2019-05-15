---
title: Veri Sözleşmesi Bilinen Türler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], known types
- KnownTypeAttribute [WCF]
- KnownTypes [WCF]
ms.assetid: 1a0baea1-27b7-470d-9136-5bbad86c4337
ms.openlocfilehash: dc297bd35d7bfdb25fc50135b8e684e1b9452cb2
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592577"
---
# <a name="data-contract-known-types"></a><span data-ttu-id="c3a40-102">Veri Sözleşmesi Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="c3a40-102">Data Contract Known Types</span></span>
<span data-ttu-id="c3a40-103"><xref:System.Runtime.Serialization.KnownTypeAttribute> Sınıfı, öncelikli seri durumundan çıkarma sırasında göz önünde bulundurmanız için dahil edilmesi gereken türleri belirtmenize olanak verir.</span><span class="sxs-lookup"><span data-stu-id="c3a40-103">The <xref:System.Runtime.Serialization.KnownTypeAttribute> class allows you to specify, in advance, the types that should be included for consideration during deserialization.</span></span> <span data-ttu-id="c3a40-104">Çalışan bir örnek için bkz. [bilinen türleri](../../../../docs/framework/wcf/samples/known-types.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="c3a40-104">For a working example, see the [Known Types](../../../../docs/framework/wcf/samples/known-types.md) example.</span></span>  
  
 <span data-ttu-id="c3a40-105">Normalde, parametreler ve dönüş değerleri bir istemci ve hizmet arasında geçirirken, her iki bitiş tüm aktarılacak olan verilerin veri sözleşmeleri paylaşır.</span><span class="sxs-lookup"><span data-stu-id="c3a40-105">Normally, when passing parameters and return values between a client and a service, both endpoints share all of the data contracts of the data to be transmitted.</span></span> <span data-ttu-id="c3a40-106">Ancak, bu durum aşağıdaki durumlarda geçerli değildir:</span><span class="sxs-lookup"><span data-stu-id="c3a40-106">However, this is not the case in the following circumstances:</span></span>  
  
- <span data-ttu-id="c3a40-107">Gönderilen veri anlaşması beklenen veri sözleşme üzerinden türetilir.</span><span class="sxs-lookup"><span data-stu-id="c3a40-107">The sent data contract is derived from the expected data contract.</span></span> <span data-ttu-id="c3a40-108">Bölüm içinde devralma hakkında daha fazla bilgi için bkz. [veri anlaşması eşitliği](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)).</span><span class="sxs-lookup"><span data-stu-id="c3a40-108">For more information, see the section about inheritance in [Data Contract Equivalence](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)).</span></span> <span data-ttu-id="c3a40-109">Bu durumda, aktarılan veri alan uç noktası tarafından beklenen şekilde sözleşme aynı veri yok.</span><span class="sxs-lookup"><span data-stu-id="c3a40-109">In that case, the transmitted data does not have the same data contract as expected by the receiving endpoint.</span></span>  
  
- <span data-ttu-id="c3a40-110">İletilecek bilgiler için bildirilen tür bir sınıf, yapı ya da numaralandırma aksine bir arabirimdir.</span><span class="sxs-lookup"><span data-stu-id="c3a40-110">The declared type for the information to be transmitted is an interface, as opposed to a class, structure, or enumeration.</span></span> <span data-ttu-id="c3a40-111">Bu nedenle, bunu önceden uyguladığı arabirim gerçekten gönderilir ve bu nedenle, alıcı uç nokta aktarılan veriler için veri anlaşması önceden belirleyemiyor tür bilinmesi olamaz.</span><span class="sxs-lookup"><span data-stu-id="c3a40-111">Therefore, it cannot be known in advance which type that implements the interface is actually sent and therefore, the receiving endpoint cannot determine in advance the data contract for the transmitted data.</span></span>  
  
- <span data-ttu-id="c3a40-112">İletilecek bilgiler için bildirilen türü <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="c3a40-112">The declared type for the information to be transmitted is <xref:System.Object>.</span></span> <span data-ttu-id="c3a40-113">Her tür öğesinden devralındığından <xref:System.Object>ve bunu önceden hangi tür gerçekten gönderilen bilinmesi olamaz, alan uç noktası önceden aktarılan veriler için veri anlaşması belirlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="c3a40-113">Because every type inherits from <xref:System.Object>, and it cannot be known in advance which type is actually sent, the receiving endpoint cannot determine in advance the data contract for the transmitted data.</span></span> <span data-ttu-id="c3a40-114">Bu, ilk öğenin bir özel durumdur: Varsayılan olarak oluşturulan bir boş veri anlaşması her veri anlaşması türetildiği <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="c3a40-114">This is a special case of the first item: Every data contract derives from the default, a blank data contract that is generated for <xref:System.Object>.</span></span>  
  
- <span data-ttu-id="c3a40-115">.NET Framework türleri dahil, bazı türleri önceki üç kategoriden birinde olan üyeleri var.</span><span class="sxs-lookup"><span data-stu-id="c3a40-115">Some types, which include .NET Framework types, have members that are in one of the preceding three categories.</span></span> <span data-ttu-id="c3a40-116">Örneğin, <xref:System.Collections.Hashtable> kullanan <xref:System.Object> karma tablosundan gerçek nesneleri depolamak için.</span><span class="sxs-lookup"><span data-stu-id="c3a40-116">For example, <xref:System.Collections.Hashtable> uses <xref:System.Object> to store the actual objects in the hash table.</span></span> <span data-ttu-id="c3a40-117">Bu türler seri hale getirme, alma tarafı önceden bu üyeler için veri anlaşması belirlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="c3a40-117">When serializing these types, the receiving side cannot determine in advance the data contract for these members.</span></span>  
  
## <a name="the-knowntypeattribute-class"></a><span data-ttu-id="c3a40-118">KnownTypeAttribute sınıfı</span><span class="sxs-lookup"><span data-stu-id="c3a40-118">The KnownTypeAttribute Class</span></span>  
 <span data-ttu-id="c3a40-119">Veri alma bir bitiş noktasına ulaştığında, bir ortak dil çalışma zamanı (CLR) türünün bir örneğine verileri seri durumdan WCF çalıştırma zamanı çalışır.</span><span class="sxs-lookup"><span data-stu-id="c3a40-119">When data arrives at a receiving endpoint, the WCF runtime attempts to deserialize the data into an instance of a common language runtime (CLR) type.</span></span> <span data-ttu-id="c3a40-120">İlk verileri belirlemek için gelen ileti anlaşması iletinin içeriğini uygun olması inceleyerek seri durumundan çıkarma için örneği türü seçilir.</span><span class="sxs-lookup"><span data-stu-id="c3a40-120">The type that is instantiated for deserialization is chosen by first inspecting the incoming message to determine the data contract to which the contents of the message conform.</span></span> <span data-ttu-id="c3a40-121">Seri durumundan çıkarma altyapısı ardından ileti içeriği ile uyumlu bir veri anlaşması uygulayan bir CLR türü bulmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="c3a40-121">The deserialization engine then attempts to find a CLR type that implements a data contract compatible with the message contents.</span></span> <span data-ttu-id="c3a40-122">Bu işlem sırasında seri durumundan çıkarma altyapısı sağlayan aday türleri "bilinen türleri." seri kaldırıcı'nın kümesi olarak adlandırılır</span><span class="sxs-lookup"><span data-stu-id="c3a40-122">The set of candidate types that the deserialization engine allows for during this process is referred to as the deserializer's set of "known types."</span></span>  
  
 <span data-ttu-id="c3a40-123">Bir tür hakkında bilmeniz seri durumundan çıkarma altyapısının yollarından biri açıklanmıştır kullanarak <xref:System.Runtime.Serialization.KnownTypeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="c3a40-123">One way to let the deserialization engine know about a type is by using the <xref:System.Runtime.Serialization.KnownTypeAttribute>.</span></span> <span data-ttu-id="c3a40-124">Öznitelik, yalnızca tüm veri anlaşması türleri için tek tek veri üyeleri için uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="c3a40-124">The attribute cannot be applied to individual data members, only to whole data contract types.</span></span> <span data-ttu-id="c3a40-125">Öznitelik uygulandığı bir *dış türün* bir sınıf veya yapı olabilir.</span><span class="sxs-lookup"><span data-stu-id="c3a40-125">The attribute is applied to an *outer type* that can be a class or a structure.</span></span> <span data-ttu-id="c3a40-126">En temel kullanımını özniteliği uygulama türü "bilinen bir tür olarak." belirtir</span><span class="sxs-lookup"><span data-stu-id="c3a40-126">In its most basic usage, applying the attribute specifies a type as a "known type."</span></span> <span data-ttu-id="c3a40-127">Bu neden olan bilinen türleri dış türün bir nesnenin her bir parçası olarak bilinen türü veya üyelerini başvurulan herhangi bir nesne seri durumdan çıkarılmakta olan.</span><span class="sxs-lookup"><span data-stu-id="c3a40-127">This causes the known type to be a part of the set of known types whenever an object of the outer type or any object referred to through its members is being deserialized.</span></span> <span data-ttu-id="c3a40-128">Birden fazla <xref:System.Runtime.Serialization.KnownTypeAttribute> özniteliği aynı türe uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="c3a40-128">More than one <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute can be applied to the same type.</span></span>  
  
## <a name="known-types-and-primitives"></a><span data-ttu-id="c3a40-129">Bilinen türler ve temelleri</span><span class="sxs-lookup"><span data-stu-id="c3a40-129">Known Types and Primitives</span></span>  
 <span data-ttu-id="c3a40-130">İlkel türler olarak belirli türlerini temel olarak kabul edilir (örneğin, <xref:System.DateTime> ve <xref:System.Xml.XmlElement>) her zaman "bilinen" ve hiçbir zaman bu mekanizma aracılığıyla eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="c3a40-130">Primitive types, as well as certain types treated as primitives (for example, <xref:System.DateTime> and <xref:System.Xml.XmlElement>) are always "known" and never have to be added through this mechanism.</span></span> <span data-ttu-id="c3a40-131">Ancak, ilkel türlerin dizileri açıkça eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="c3a40-131">However, arrays of primitive types have to be added explicitly.</span></span> <span data-ttu-id="c3a40-132">Çoğu koleksiyonları diziler için eşdeğer olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="c3a40-132">Most collections are considered equivalent to arrays.</span></span> <span data-ttu-id="c3a40-133">(Genel olmayan koleksiyon dizileri için eşdeğer olarak değerlendirilir <xref:System.Object>).</span><span class="sxs-lookup"><span data-stu-id="c3a40-133">(Non-generic collections are considered equivalent to arrays of <xref:System.Object>).</span></span> <span data-ttu-id="c3a40-134">Kullanma örneği için temelleri, basit diziler ve temel koleksiyonları örnek 4 bakın.</span><span class="sxs-lookup"><span data-stu-id="c3a40-134">For an example of the using primitives, primitive arrays, and primitive collections, see Example 4.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c3a40-135">Diğer ilkel türler, aksine <xref:System.DateTimeOffset> yapısı bir bilinen tür değil varsayılan olarak, böylece el ile bilinen türler listesine eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="c3a40-135">Unlike other primitive types, the <xref:System.DateTimeOffset> structure is not a known type by default, so it must be manually added to the list of known types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="c3a40-136">Örnekler</span><span class="sxs-lookup"><span data-stu-id="c3a40-136">Examples</span></span>  
 <span data-ttu-id="c3a40-137">Aşağıdaki örneklerde gösterildiği <xref:System.Runtime.Serialization.KnownTypeAttribute> sınıfı kullanın.</span><span class="sxs-lookup"><span data-stu-id="c3a40-137">The following examples show the <xref:System.Runtime.Serialization.KnownTypeAttribute> class in use.</span></span>  
  
#### <a name="example-1"></a><span data-ttu-id="c3a40-138">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="c3a40-138">Example 1</span></span>  
 <span data-ttu-id="c3a40-139">Devralma ilişkisi ile üç sınıfı vardır.</span><span class="sxs-lookup"><span data-stu-id="c3a40-139">There are three classes with an inheritance relationship.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#1)]
 [!code-vb[C_KnownTypeAttribute#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#1)]  
  
 <span data-ttu-id="c3a40-140">Aşağıdaki `CompanyLogo` sınıfı serileştirilmiş, ancak, seri durumdan çıkarılamıyor `ShapeOfLogo` üye ayarlanmış olarak bir `CircleType` veya `TriangleType` nesne seri durumundan çıkarma altyapısı herhangi bir veri sözleşmesi adları türleriyle tanımadığından " Daire"veya"Üçgen."</span><span class="sxs-lookup"><span data-stu-id="c3a40-140">The following `CompanyLogo` class can be serialized, but cannot be deserialized if the `ShapeOfLogo` member is set to either a `CircleType` or a `TriangleType` object, because the deserialization engine does not recognize any types with data contract names "Circle" or "Triangle."</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#2)]
 [!code-vb[C_KnownTypeAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#2)]  
  
 <span data-ttu-id="c3a40-141">Yazma için doğru şekilde `CompanyLogo` türü, aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c3a40-141">The correct way to write the `CompanyLogo` type is shown in the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#3)]
 [!code-vb[C_KnownTypeAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#3)]  
  
 <span data-ttu-id="c3a40-142">Her dış türün `CompanyLogo2` olan bildiği seri durumundan çıkarma altyapısı seri durumdan çıkarılmakta `CircleType` ve `TriangleType` ve bu nedenle, eşleşen türleri için "Daire" ve "Üçgen" veri sözleşmeleri bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c3a40-142">Whenever the outer type `CompanyLogo2` is being deserialized, the deserialization engine knows about `CircleType` and `TriangleType` and, therefore, is able to find matching types for the "Circle" and "Triangle" data contracts.</span></span>  
  
#### <a name="example-2"></a><span data-ttu-id="c3a40-143">Örnek 2</span><span class="sxs-lookup"><span data-stu-id="c3a40-143">Example 2</span></span>  
 <span data-ttu-id="c3a40-144">Aşağıdaki örnekte, olsa bile her ikisi de `CustomerTypeA` ve `CustomerTypeB` sahip `Customer` veri anlaşması, örneği `CustomerTypeB` herhangi bir zamanda oluşturulmuş bir `PurchaseOrder` , çünkü seri durumda yalnızca `CustomerTypeB` bilinen Seri durumundan çıkarma altyapısı.</span><span class="sxs-lookup"><span data-stu-id="c3a40-144">In the following example, even though both `CustomerTypeA` and `CustomerTypeB` have the `Customer` data contract, an instance of `CustomerTypeB` is created whenever a `PurchaseOrder` is deserialized, because only `CustomerTypeB` is known to the deserialization engine.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#4)]
 [!code-vb[C_KnownTypeAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#4)]  
  
#### <a name="example-3"></a><span data-ttu-id="c3a40-145">Örnek 3</span><span class="sxs-lookup"><span data-stu-id="c3a40-145">Example 3</span></span>  
 <span data-ttu-id="c3a40-146">Aşağıdaki örnekte, bir <xref:System.Collections.Hashtable> içeriğini depolar dahili olarak <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="c3a40-146">In the following example, a <xref:System.Collections.Hashtable> stores its contents internally as <xref:System.Object>.</span></span> <span data-ttu-id="c3a40-147">Bir karma tablo başarılı bir şekilde seri durumdan çıkarılacak seri durumundan çıkarma altyapısı var. oluşabilecek olası türleri bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c3a40-147">To successfully deserialize a hash table, the deserialization engine must know the set of possible types that can occur there.</span></span> <span data-ttu-id="c3a40-148">Bu durumda, yalnızca bilgimiz `Book` ve `Magazine` nesnelerinin depolandığı `Catalog`, bu kullanılarak eklenen <xref:System.Runtime.Serialization.KnownTypeAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c3a40-148">In this case, we know in advance that only `Book` and `Magazine` objects are stored in the `Catalog`, so those are added using the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#5)]
 [!code-vb[C_KnownTypeAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#5)]  
  
#### <a name="example-4"></a><span data-ttu-id="c3a40-149">Örnek 4</span><span class="sxs-lookup"><span data-stu-id="c3a40-149">Example 4</span></span>  
 <span data-ttu-id="c3a40-150">Aşağıdaki örnekte, bir sayı ve bir işlem sayısına gerçekleştirmek için bir veri anlaşması depolar.</span><span class="sxs-lookup"><span data-stu-id="c3a40-150">In the following example, a data contract stores a number and an operation to perform on the number.</span></span> <span data-ttu-id="c3a40-151">`Numbers` Veri üyesi, bir tamsayı dizisi, olabilir veya bir <xref:System.Collections.Generic.List%601> tamsayılar içeren.</span><span class="sxs-lookup"><span data-stu-id="c3a40-151">The `Numbers` data member can be an integer, an array of integers, or a <xref:System.Collections.Generic.List%601> that contains integers.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="c3a40-152">Bu yalnızca istemci tarafında ise çalışır SVCUTIL. EXE, WCF proxy oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c3a40-152">This will only work on the client side if SVCUTIL.EXE is used to generate a WCF proxy.</span></span> <span data-ttu-id="c3a40-153">SVCUTIL. EXE herhangi bir bilinen türleri dahil olmak üzere hizmet meta verilerini alır.</span><span class="sxs-lookup"><span data-stu-id="c3a40-153">SVCUTIL.EXE retrieves metadata from the service including any known types.</span></span> <span data-ttu-id="c3a40-154">Bu bilgiler olmadan, bir istemci türleri seri durumdan çıkarılacak mümkün olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="c3a40-154">Without this information a client will not be able to deserialize the types.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#6)]
 [!code-vb[C_KnownTypeAttribute#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#6)]  
  
 <span data-ttu-id="c3a40-155">Uygulama kodu budur.</span><span class="sxs-lookup"><span data-stu-id="c3a40-155">This is the application code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#7)]
 [!code-vb[C_KnownTypeAttribute#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#7)]  
  
## <a name="known-types-inheritance-and-interfaces"></a><span data-ttu-id="c3a40-156">Bilinen türler, devralma ve arabirimler</span><span class="sxs-lookup"><span data-stu-id="c3a40-156">Known Types, Inheritance, and Interfaces</span></span>  
 <span data-ttu-id="c3a40-157">Bilinen bir türde olduğunda kullanarak bir türdeki ilişkili `KnownTypeAttribute` özniteliği, bilinen türü de tüm türetilmiş türleri türü ile ilişkili.</span><span class="sxs-lookup"><span data-stu-id="c3a40-157">When a known type is associated with a particular type using the `KnownTypeAttribute` attribute, the known type is also associated with all of the derived types of that type.</span></span> <span data-ttu-id="c3a40-158">Örneğin, aşağıdaki koda bakın.</span><span class="sxs-lookup"><span data-stu-id="c3a40-158">For example, see the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#8)]
 [!code-vb[C_KnownTypeAttribute#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#8)]  
  
 <span data-ttu-id="c3a40-159">`DoubleDrawing` Sınıfı gerektirmez `KnownTypeAttribute` kullanılacak özniteliği `Square` ve `Circle` içinde `AdditionalShape` çünkü alan taban sınıf (`Drawing`) zaten uygulanan bu özniteliklere sahip.</span><span class="sxs-lookup"><span data-stu-id="c3a40-159">The `DoubleDrawing` class does not require the `KnownTypeAttribute` attribute to use `Square` and `Circle` in the `AdditionalShape` field, because the base class (`Drawing`) already has these attributes applied.</span></span>  
  
 <span data-ttu-id="c3a40-160">Bilinen türler yalnızca sınıflar ve yapılar, arabirimler değil ile ilişkili olabilir.</span><span class="sxs-lookup"><span data-stu-id="c3a40-160">Known types can be associated only with classes and structures, not interfaces.</span></span>  
  
## <a name="known-types-using-open-generic-methods"></a><span data-ttu-id="c3a40-161">Açık genel yöntemler kullanarak bilinen türler</span><span class="sxs-lookup"><span data-stu-id="c3a40-161">Known Types Using Open Generic Methods</span></span>  
 <span data-ttu-id="c3a40-162">Genel bir tür bilinen bir tür eklemek gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="c3a40-162">It may be necessary to add a generic type as a known type.</span></span> <span data-ttu-id="c3a40-163">Ancak, bir açık genel tür parametresi olarak geçirilemez `KnownTypeAttribute` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c3a40-163">However, an open generic type cannot be passed as a parameter to the `KnownTypeAttribute` attribute.</span></span>  
  
 <span data-ttu-id="c3a40-164">Bu sorun, alternatif bir mekanizma kullanarak çözülebilir: Bilinen türlerin koleksiyonuna eklemek için türlerinin bir listesini döndüren bir yöntem yazmaktır.</span><span class="sxs-lookup"><span data-stu-id="c3a40-164">This problem can be solved by using an alternative mechanism: Write a method that returns a list of types to add to the known types collection.</span></span> <span data-ttu-id="c3a40-165">Yöntemin adını ardından bir dize bağımsız değişkeni olarak belirtilen `KnownTypeAttribute` bazı kısıtlamalar nedeniyle özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c3a40-165">The name of the method is then specified as a string argument to the `KnownTypeAttribute` attribute due to some restrictions.</span></span>  
  
 <span data-ttu-id="c3a40-166">Yöntem türü üzerinde bulunmalıdır `KnownTypeAttribute` özniteliği uygulanır, statik olmalıdır, hiçbir parametre kabul etmeniz gerekir ve atanabilir bir nesne döndürmelidir <xref:System.Collections.IEnumerable> , <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="c3a40-166">The method must exist on the type to which the `KnownTypeAttribute` attribute is applied, must be static, must accept no parameters, and must return an object that can be assigned to <xref:System.Collections.IEnumerable> of <xref:System.Type>.</span></span>  
  
 <span data-ttu-id="c3a40-167">Birleştirmeniz mümkün olmayacaktır `KnownTypeAttribute` özniteliği bir metot adı ile ve `KnownTypeAttribute` özniteliklerle aynı türünde gerçek türler.</span><span class="sxs-lookup"><span data-stu-id="c3a40-167">You cannot combine the `KnownTypeAttribute` attribute with a method name and `KnownTypeAttribute` attributes with actual types on the same type.</span></span> <span data-ttu-id="c3a40-168">Ayrıca, birden fazla uygulanamıyor `KnownTypeAttribute` bir yöntem adı aynı türe sahip.</span><span class="sxs-lookup"><span data-stu-id="c3a40-168">Furthermore, you cannot apply more than one `KnownTypeAttribute` with a method name to the same type.</span></span>  
  
 <span data-ttu-id="c3a40-169">Aşağıdaki sınıf konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="c3a40-169">See the following class.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#9)]
 [!code-vb[C_KnownTypeAttribute#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#9)]  
  
 <span data-ttu-id="c3a40-170">`theDrawing` Alan içeren bir genel sınıfın örnekleri `ColorDrawing` ve genel bir sınıf `BlackAndWhiteDrawing`, ikisi için de genel bir sınıftan devralınan `Drawing`.</span><span class="sxs-lookup"><span data-stu-id="c3a40-170">The `theDrawing` field contains instances of a generic class `ColorDrawing` and a generic class `BlackAndWhiteDrawing`, both of which inherit from a generic class `Drawing`.</span></span> <span data-ttu-id="c3a40-171">Normalde, her ikisi de bilinen türlere eklenen gerekir, ancak aşağıdaki öznitelikleri sözdizimi geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="c3a40-171">Normally, both must be added to known types, but the following is not valid syntax for attributes.</span></span>  
  
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
  
 <span data-ttu-id="c3a40-172">Bu nedenle, bu tür döndürmek için bir yöntem oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c3a40-172">Thus, a method must be created to return these types.</span></span> <span data-ttu-id="c3a40-173">Bu tür, yazma için doğru şekilde, daha sonra aşağıdaki kodda gösterilir.</span><span class="sxs-lookup"><span data-stu-id="c3a40-173">The correct way to write this type, then, is shown in the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#10)]
 [!code-vb[C_KnownTypeAttribute#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#10)]  
  
## <a name="additional-ways-to-add-known-types"></a><span data-ttu-id="c3a40-174">Bilinen türler eklemek için ek yol</span><span class="sxs-lookup"><span data-stu-id="c3a40-174">Additional Ways to Add Known Types</span></span>  
 <span data-ttu-id="c3a40-175">Ayrıca, bilinen türleri bir yapılandırma dosyası eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="c3a40-175">Additionally, known types can be added through a configuration file.</span></span> <span data-ttu-id="c3a40-176">Bilinen türler için uygun seri durumundan çıkarma gibi üçüncü taraf kullanarak yazdığınızda kitaplıkları ile Windows Communication Foundation (WCF) gerektiren türü kontrol edebilirim istediğinizde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="c3a40-176">This is useful when you do not control the type that requires known types for proper deserialization, such as when using third-party type libraries with Windows Communication Foundation (WCF).</span></span>  
  
 <span data-ttu-id="c3a40-177">Aşağıdaki yapılandırma dosyası, bir yapılandırma dosyasında bir bilinen türü belirtmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c3a40-177">The following configuration file shows how to specify a known type in a configuration file.</span></span>  
  
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
  
 <span data-ttu-id="c3a40-178">Önceki yapılandırma dosyası adlı bir veri anlaşması türü `MyCompany.Library.Shape` için bildirilen `MyCompany.Library.Circle` bilinen türü.</span><span class="sxs-lookup"><span data-stu-id="c3a40-178">In the preceding configuration file a data contract type called `MyCompany.Library.Shape` is declared to have `MyCompany.Library.Circle` as a known type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3a40-179">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3a40-179">See also</span></span>

- <xref:System.Runtime.Serialization.KnownTypeAttribute>
- <xref:System.Collections.Hashtable>
- <xref:System.Object>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A>
- [<span data-ttu-id="c3a40-180">Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="c3a40-180">Known Types</span></span>](../../../../docs/framework/wcf/samples/known-types.md)
- [<span data-ttu-id="c3a40-181">Veri Anlaşması Eşitliği</span><span class="sxs-lookup"><span data-stu-id="c3a40-181">Data Contract Equivalence</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [<span data-ttu-id="c3a40-182">Hizmet Sözleşmeleri Tasarlama</span><span class="sxs-lookup"><span data-stu-id="c3a40-182">Designing Service Contracts</span></span>](../../../../docs/framework/wcf/designing-service-contracts.md)
