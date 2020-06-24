---
title: Veri Sözleşmesi Bilinen Türler
description: Veri anlaşması modelinin, WCF 'de seri durumundan çıkarma sırasında dahil edilecek türleri belirtmek için KnownTypeAttribute sınıfını nasıl kullandığını öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], known types
- KnownTypeAttribute [WCF]
- KnownTypes [WCF]
ms.assetid: 1a0baea1-27b7-470d-9136-5bbad86c4337
ms.openlocfilehash: 52b0caaaac976893dcf5ef5c228ccc4f53bdbe9e
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247487"
---
# <a name="data-contract-known-types"></a><span data-ttu-id="abd98-103">Veri Sözleşmesi Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="abd98-103">Data Contract Known Types</span></span>
<span data-ttu-id="abd98-104"><xref:System.Runtime.Serialization.KnownTypeAttribute>Sınıfı, serisini kaldırma sırasında dikkate alınması gereken türleri önceden belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="abd98-104">The <xref:System.Runtime.Serialization.KnownTypeAttribute> class allows you to specify, in advance, the types that should be included for consideration during deserialization.</span></span> <span data-ttu-id="abd98-105">Çalışan bir örnek için, [bilinen türler](../samples/known-types.md) örneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="abd98-105">For a working example, see the [Known Types](../samples/known-types.md) example.</span></span>  
  
 <span data-ttu-id="abd98-106">Normalde, parametreleri geçirirken ve bir istemci ile bir hizmet arasında değer döndürmelerinde, her iki uç nokta de iletilmek üzere verilerin tüm veri sözleşmelerini paylaşır.</span><span class="sxs-lookup"><span data-stu-id="abd98-106">Normally, when passing parameters and return values between a client and a service, both endpoints share all of the data contracts of the data to be transmitted.</span></span> <span data-ttu-id="abd98-107">Ancak, aşağıdaki durumlarda bu durum böyle değildir:</span><span class="sxs-lookup"><span data-stu-id="abd98-107">However, this is not the case in the following circumstances:</span></span>  
  
- <span data-ttu-id="abd98-108">Gönderilen veri sözleşmesi, beklenen veri sözleşmesinden türetilir.</span><span class="sxs-lookup"><span data-stu-id="abd98-108">The sent data contract is derived from the expected data contract.</span></span> <span data-ttu-id="abd98-109">Daha fazla bilgi için, [veri sözleşmesindeki](data-contract-equivalence.md)devralma hakkında bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="abd98-109">For more information, see the section about inheritance in [Data Contract Equivalence](data-contract-equivalence.md)).</span></span> <span data-ttu-id="abd98-110">Bu durumda, iletilen veriler, alıcı uç noktası tarafından beklenen veri sözleşmesine sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="abd98-110">In that case, the transmitted data does not have the same data contract as expected by the receiving endpoint.</span></span>  
  
- <span data-ttu-id="abd98-111">İletilecek bilgiler için, bir sınıf, yapı veya numaralandırmanın aksine, bir arabirim olduğu bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="abd98-111">The declared type for the information to be transmitted is an interface, as opposed to a class, structure, or enumeration.</span></span> <span data-ttu-id="abd98-112">Bu nedenle, arabirimi uygulayan türün gerçekten gönderildiği ve bu nedenle alıcı uç noktasının iletilen veriler için veri sözleşmesinin ön planda belirleyemediği bilinmez.</span><span class="sxs-lookup"><span data-stu-id="abd98-112">Therefore, it cannot be known in advance which type that implements the interface is actually sent and therefore, the receiving endpoint cannot determine in advance the data contract for the transmitted data.</span></span>  
  
- <span data-ttu-id="abd98-113">İletilecek bilgiler için belirtilen tür <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="abd98-113">The declared type for the information to be transmitted is <xref:System.Object>.</span></span> <span data-ttu-id="abd98-114">Her tür öğesinden devralındığından <xref:System.Object> ve bu türün gerçekten gönderildiği bilinmediği için, alıcı uç noktası aktarılan verilerin veri sözleşmesinin ön planda saptanamıyor.</span><span class="sxs-lookup"><span data-stu-id="abd98-114">Because every type inherits from <xref:System.Object>, and it cannot be known in advance which type is actually sent, the receiving endpoint cannot determine in advance the data contract for the transmitted data.</span></span> <span data-ttu-id="abd98-115">Bu, ilk öğenin özel bir durumdur: her veri sözleşmesi, için oluşturulan boş bir veri sözleşmesinin varsayılan değerinden türetilir <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="abd98-115">This is a special case of the first item: Every data contract derives from the default, a blank data contract that is generated for <xref:System.Object>.</span></span>  
  
- <span data-ttu-id="abd98-116">.NET Framework türlerini içeren bazı türlerin önceki üç kategoriden birinde olan üyeleri vardır.</span><span class="sxs-lookup"><span data-stu-id="abd98-116">Some types, which include .NET Framework types, have members that are in one of the preceding three categories.</span></span> <span data-ttu-id="abd98-117">Örneğin, <xref:System.Collections.Hashtable> <xref:System.Object> karma tablodaki gerçek nesneleri depolamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="abd98-117">For example, <xref:System.Collections.Hashtable> uses <xref:System.Object> to store the actual objects in the hash table.</span></span> <span data-ttu-id="abd98-118">Bu türler serileştirilirken, alıcı taraf bu üyeler için veri sözleşmesinin ön kısmına göre saptanamaz.</span><span class="sxs-lookup"><span data-stu-id="abd98-118">When serializing these types, the receiving side cannot determine in advance the data contract for these members.</span></span>  
  
## <a name="the-knowntypeattribute-class"></a><span data-ttu-id="abd98-119">KnownTypeAttribute sınıfı</span><span class="sxs-lookup"><span data-stu-id="abd98-119">The KnownTypeAttribute Class</span></span>  
 <span data-ttu-id="abd98-120">Veriler alma uç noktasına ulaştığında, WCF çalışma zamanı verileri ortak dil çalışma zamanı (CLR) türünün bir örneğine serisini kaldırma girişiminde bulunur.</span><span class="sxs-lookup"><span data-stu-id="abd98-120">When data arrives at a receiving endpoint, the WCF runtime attempts to deserialize the data into an instance of a common language runtime (CLR) type.</span></span> <span data-ttu-id="abd98-121">Seri durumdan çıkarma için örneği oluşturulan tür, önce iletinin içeriğinin uyumlu olduğu veri sözleşmesinin belirlenmesi için gelen iletiyi inceleyerek seçilir.</span><span class="sxs-lookup"><span data-stu-id="abd98-121">The type that is instantiated for deserialization is chosen by first inspecting the incoming message to determine the data contract to which the contents of the message conform.</span></span> <span data-ttu-id="abd98-122">Seri kaldırma altyapısı daha sonra ileti içeriğiyle uyumlu bir veri sözleşmesi uygulayan bir CLR türü bulmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="abd98-122">The deserialization engine then attempts to find a CLR type that implements a data contract compatible with the message contents.</span></span> <span data-ttu-id="abd98-123">Seri durumdan çıkarma altyapısının bu işlem sırasında izin verdiği aday türleri kümesi, seri hale getirici 'nin "bilinen türler" kümesi olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="abd98-123">The set of candidate types that the deserialization engine allows for during this process is referred to as the deserializer's set of "known types."</span></span>  
  
 <span data-ttu-id="abd98-124">Seri durumdan çıkarma altyapısının bir tür hakkında bilgi almasına imkan sağlamanın bir yolu, ' nı kullanmaktır <xref:System.Runtime.Serialization.KnownTypeAttribute> .</span><span class="sxs-lookup"><span data-stu-id="abd98-124">One way to let the deserialization engine know about a type is by using the <xref:System.Runtime.Serialization.KnownTypeAttribute>.</span></span> <span data-ttu-id="abd98-125">Öznitelik, tek tek veri üyelerine yalnızca tüm veri anlaşması türlerine uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="abd98-125">The attribute cannot be applied to individual data members, only to whole data contract types.</span></span> <span data-ttu-id="abd98-126">Özniteliği, bir sınıf veya yapı olabilecek bir *dış türe* uygulanır.</span><span class="sxs-lookup"><span data-stu-id="abd98-126">The attribute is applied to an *outer type* that can be a class or a structure.</span></span> <span data-ttu-id="abd98-127">En temel kullanımındaki özniteliği uygulamak, bir türü "bilinen tür" olarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="abd98-127">In its most basic usage, applying the attribute specifies a type as a "known type."</span></span> <span data-ttu-id="abd98-128">Bu, dış türdeki bir nesne veya üyeleri aracılığıyla başvurulan herhangi bir nesne seri durumdan çıkarıldığı zaman bilinen türün bilinen türler kümesinin bir parçası olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="abd98-128">This causes the known type to be a part of the set of known types whenever an object of the outer type or any object referred to through its members is being deserialized.</span></span> <span data-ttu-id="abd98-129"><xref:System.Runtime.Serialization.KnownTypeAttribute>Aynı türde birden fazla öznitelik uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="abd98-129">More than one <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute can be applied to the same type.</span></span>  
  
## <a name="known-types-and-primitives"></a><span data-ttu-id="abd98-130">Bilinen türler ve temel elemanlar</span><span class="sxs-lookup"><span data-stu-id="abd98-130">Known Types and Primitives</span></span>  
 <span data-ttu-id="abd98-131">İlkel türler ve temel öğeler (örneğin, ve) olarak değerlendirilen belirli türler <xref:System.DateTime> <xref:System.Xml.XmlElement> her zaman "biliniyor" ve bu mekanizmaya hiç eklenmemek zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="abd98-131">Primitive types, as well as certain types treated as primitives (for example, <xref:System.DateTime> and <xref:System.Xml.XmlElement>) are always "known" and never have to be added through this mechanism.</span></span> <span data-ttu-id="abd98-132">Ancak, temel türlerin dizileri açıkça eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="abd98-132">However, arrays of primitive types have to be added explicitly.</span></span> <span data-ttu-id="abd98-133">Çoğu koleksiyon dizilere eşit kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="abd98-133">Most collections are considered equivalent to arrays.</span></span> <span data-ttu-id="abd98-134">(Genel olmayan koleksiyonlar diziler için eşdeğer olarak kabul edilir <xref:System.Object> ).</span><span class="sxs-lookup"><span data-stu-id="abd98-134">(Non-generic collections are considered equivalent to arrays of <xref:System.Object>).</span></span> <span data-ttu-id="abd98-135">Temel elemanlar, ilkel diziler ve basit koleksiyonlar kullanmanın bir örneği için bkz. örnek 4.</span><span class="sxs-lookup"><span data-stu-id="abd98-135">For an example of the using primitives, primitive arrays, and primitive collections, see Example 4.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="abd98-136">Diğer temel türlerin aksine, <xref:System.DateTimeOffset> Yapı varsayılan olarak bilinen bir tür değildir, bu nedenle bilinen türler listesine el ile eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="abd98-136">Unlike other primitive types, the <xref:System.DateTimeOffset> structure is not a known type by default, so it must be manually added to the list of known types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="abd98-137">Örnekler</span><span class="sxs-lookup"><span data-stu-id="abd98-137">Examples</span></span>  
 <span data-ttu-id="abd98-138">Aşağıdaki örneklerde <xref:System.Runtime.Serialization.KnownTypeAttribute> kullanılan sınıf gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="abd98-138">The following examples show the <xref:System.Runtime.Serialization.KnownTypeAttribute> class in use.</span></span>  
  
#### <a name="example-1"></a><span data-ttu-id="abd98-139">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="abd98-139">Example 1</span></span>  
 <span data-ttu-id="abd98-140">Devralma ilişkisine sahip üç sınıf vardır.</span><span class="sxs-lookup"><span data-stu-id="abd98-140">There are three classes with an inheritance relationship.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#1)]
 [!code-vb[C_KnownTypeAttribute#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#1)]  
  
 <span data-ttu-id="abd98-141">Aşağıdaki `CompanyLogo` sınıf seri hale getirilebilir, ancak `ShapeOfLogo` üye bir ya da bir nesne olarak ayarlandıysa seri durumdan çıkarılamaz, `CircleType` `TriangleType` çünkü serisini kaldırma altyapısı veri sözleşme adları "Circle" veya "Triangle" olan herhangi bir türü tanımaz.</span><span class="sxs-lookup"><span data-stu-id="abd98-141">The following `CompanyLogo` class can be serialized, but cannot be deserialized if the `ShapeOfLogo` member is set to either a `CircleType` or a `TriangleType` object, because the deserialization engine does not recognize any types with data contract names "Circle" or "Triangle."</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#2)]
 [!code-vb[C_KnownTypeAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#2)]  
  
 <span data-ttu-id="abd98-142">Türü yazmanın doğru yolu `CompanyLogo` aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="abd98-142">The correct way to write the `CompanyLogo` type is shown in the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#3)]
 [!code-vb[C_KnownTypeAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#3)]  
  
 <span data-ttu-id="abd98-143">Dış tür `CompanyLogo2` seri durumdan çıkarılabildiğinde, seri durumdan çıkarma motoru `CircleType` ve ile ilgili olarak, `TriangleType` "daire" ve "üçgen" veri sözleşmeleri için eşleşen türleri bulabilir.</span><span class="sxs-lookup"><span data-stu-id="abd98-143">Whenever the outer type `CompanyLogo2` is being deserialized, the deserialization engine knows about `CircleType` and `TriangleType` and, therefore, is able to find matching types for the "Circle" and "Triangle" data contracts.</span></span>  
  
#### <a name="example-2"></a><span data-ttu-id="abd98-144">Örnek 2</span><span class="sxs-lookup"><span data-stu-id="abd98-144">Example 2</span></span>  
 <span data-ttu-id="abd98-145">Aşağıdaki örnekte, her ikisi de `CustomerTypeA` ve veri sözleşmesine sahip olsa bile, her `CustomerTypeB` `Customer` `CustomerTypeB` bir seri hale geldiğinde bir örneği oluşturulur `PurchaseOrder` , çünkü yalnızca seri durumdan `CustomerTypeB` çıkarma altyapısı tarafından bilinir.</span><span class="sxs-lookup"><span data-stu-id="abd98-145">In the following example, even though both `CustomerTypeA` and `CustomerTypeB` have the `Customer` data contract, an instance of `CustomerTypeB` is created whenever a `PurchaseOrder` is deserialized, because only `CustomerTypeB` is known to the deserialization engine.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#4)]
 [!code-vb[C_KnownTypeAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#4)]  
  
#### <a name="example-3"></a><span data-ttu-id="abd98-146">Örnek 3</span><span class="sxs-lookup"><span data-stu-id="abd98-146">Example 3</span></span>  
 <span data-ttu-id="abd98-147">Aşağıdaki örnekte, bir, <xref:System.Collections.Hashtable> içeriğini dahili olarak depolar <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="abd98-147">In the following example, a <xref:System.Collections.Hashtable> stores its contents internally as <xref:System.Object>.</span></span> <span data-ttu-id="abd98-148">Bir karma tablonun serisini başarıyla kaldırmak için, seri durumdan çıkarma altyapısının, burada oluşabilecek olası türler kümesini bilmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="abd98-148">To successfully deserialize a hash table, the deserialization engine must know the set of possible types that can occur there.</span></span> <span data-ttu-id="abd98-149">Bu durumda, yalnızca `Book` ve `Magazine` nesnelerinin üzerinde depolandıkları için, bu, `Catalog` öznitelik kullanılarak eklenmeleri durumunda olduğunu biliyoruz <xref:System.Runtime.Serialization.KnownTypeAttribute> .</span><span class="sxs-lookup"><span data-stu-id="abd98-149">In this case, we know in advance that only `Book` and `Magazine` objects are stored in the `Catalog`, so those are added using the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#5)]
 [!code-vb[C_KnownTypeAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#5)]  
  
#### <a name="example-4"></a><span data-ttu-id="abd98-150">Örnek 4</span><span class="sxs-lookup"><span data-stu-id="abd98-150">Example 4</span></span>  
 <span data-ttu-id="abd98-151">Aşağıdaki örnekte, bir veri sözleşmesi numarayı ve numara üzerinde gerçekleştirilecek bir işlemi depolar.</span><span class="sxs-lookup"><span data-stu-id="abd98-151">In the following example, a data contract stores a number and an operation to perform on the number.</span></span> <span data-ttu-id="abd98-152">`Numbers`Veri üyesi tamsayı, tamsayılar dizisi veya tamsayılar içeren bir dize olabilir <xref:System.Collections.Generic.List%601> .</span><span class="sxs-lookup"><span data-stu-id="abd98-152">The `Numbers` data member can be an integer, an array of integers, or a <xref:System.Collections.Generic.List%601> that contains integers.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="abd98-153">Bu, yalnızca bir WCF proxy oluşturmak için SVCUTIL.EXE kullanılıyorsa istemci tarafında çalışır.</span><span class="sxs-lookup"><span data-stu-id="abd98-153">This will only work on the client side if SVCUTIL.EXE is used to generate a WCF proxy.</span></span> <span data-ttu-id="abd98-154">SVCUTIL.EXE bilinen türler dahil olmak üzere hizmetten meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="abd98-154">SVCUTIL.EXE retrieves metadata from the service including any known types.</span></span> <span data-ttu-id="abd98-155">Bu bilgiler olmadan, istemci türlerin serisini kaldıramıyor.</span><span class="sxs-lookup"><span data-stu-id="abd98-155">Without this information a client will not be able to deserialize the types.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#6)]
 [!code-vb[C_KnownTypeAttribute#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#6)]  
  
 <span data-ttu-id="abd98-156">Bu uygulama kodudur.</span><span class="sxs-lookup"><span data-stu-id="abd98-156">This is the application code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#7)]
 [!code-vb[C_KnownTypeAttribute#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#7)]  
  
## <a name="known-types-inheritance-and-interfaces"></a><span data-ttu-id="abd98-157">Bilinen türler, devralma ve arabirimler</span><span class="sxs-lookup"><span data-stu-id="abd98-157">Known Types, Inheritance, and Interfaces</span></span>  
 <span data-ttu-id="abd98-158">Bilinen bir tür özniteliği kullanılarak belirli bir türle ilişkilendirildiğinde `KnownTypeAttribute` , bilinen tür aynı zamanda bu türün türetilmiş tüm türleri ile ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="abd98-158">When a known type is associated with a particular type using the `KnownTypeAttribute` attribute, the known type is also associated with all of the derived types of that type.</span></span> <span data-ttu-id="abd98-159">Örneğin, aşağıdaki koda bakın.</span><span class="sxs-lookup"><span data-stu-id="abd98-159">For example, see the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#8)]
 [!code-vb[C_KnownTypeAttribute#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#8)]  
  
 <span data-ttu-id="abd98-160">`DoubleDrawing` `KnownTypeAttribute` `Square` `Circle` `AdditionalShape` Temel sınıf ( `Drawing` ) zaten bu özniteliklerin uygulanmış olması nedeniyle, sınıfı, ' ın ve alan içinde özniteliğini gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="abd98-160">The `DoubleDrawing` class does not require the `KnownTypeAttribute` attribute to use `Square` and `Circle` in the `AdditionalShape` field, because the base class (`Drawing`) already has these attributes applied.</span></span>  
  
 <span data-ttu-id="abd98-161">Bilinen türler, arabirimler değil yalnızca sınıflar ve yapılar ile ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="abd98-161">Known types can be associated only with classes and structures, not interfaces.</span></span>  
  
## <a name="known-types-using-open-generic-methods"></a><span data-ttu-id="abd98-162">Açık genel yöntemler kullanan bilinen türler</span><span class="sxs-lookup"><span data-stu-id="abd98-162">Known Types Using Open Generic Methods</span></span>  
 <span data-ttu-id="abd98-163">Bilinen bir tür olarak genel bir tür eklemek gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="abd98-163">It may be necessary to add a generic type as a known type.</span></span> <span data-ttu-id="abd98-164">Ancak açık genel tür özniteliğe parametre olarak geçirilemez `KnownTypeAttribute` .</span><span class="sxs-lookup"><span data-stu-id="abd98-164">However, an open generic type cannot be passed as a parameter to the `KnownTypeAttribute` attribute.</span></span>  
  
 <span data-ttu-id="abd98-165">Bu sorun, alternatif bir mekanizma kullanılarak çözülebilir: bilinen türler koleksiyonuna eklemek üzere türlerin bir listesini döndüren bir yöntem yazın.</span><span class="sxs-lookup"><span data-stu-id="abd98-165">This problem can be solved by using an alternative mechanism: Write a method that returns a list of types to add to the known types collection.</span></span> <span data-ttu-id="abd98-166">Yöntemin adı, daha sonra `KnownTypeAttribute` bazı kısıtlamalar nedeniyle özniteliğe dize bağımsız değişkeni olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="abd98-166">The name of the method is then specified as a string argument to the `KnownTypeAttribute` attribute due to some restrictions.</span></span>  
  
 <span data-ttu-id="abd98-167">Yöntemin, özniteliğin uygulandığı türde olması gerekir `KnownTypeAttribute` , statik olması gerekir, parametre içermemelidir ve ' nin atanabileceği bir nesne döndürmesi gerekir <xref:System.Collections.IEnumerable> <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="abd98-167">The method must exist on the type to which the `KnownTypeAttribute` attribute is applied, must be static, must accept no parameters, and must return an object that can be assigned to <xref:System.Collections.IEnumerable> of <xref:System.Type>.</span></span>  
  
 <span data-ttu-id="abd98-168">`KnownTypeAttribute`Özniteliği, `KnownTypeAttribute` aynı türde gerçek türler içeren bir yöntem adı ve özniteliklerle birleştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="abd98-168">You cannot combine the `KnownTypeAttribute` attribute with a method name and `KnownTypeAttribute` attributes with actual types on the same type.</span></span> <span data-ttu-id="abd98-169">Ayrıca, `KnownTypeAttribute` aynı türde bir yöntem adına sahip birden fazla tane uygulayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="abd98-169">Furthermore, you cannot apply more than one `KnownTypeAttribute` with a method name to the same type.</span></span>  
  
 <span data-ttu-id="abd98-170">Aşağıdaki sınıfa bakın.</span><span class="sxs-lookup"><span data-stu-id="abd98-170">See the following class.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#9)]
 [!code-vb[C_KnownTypeAttribute#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#9)]  
  
 <span data-ttu-id="abd98-171">`theDrawing`Alan, her ikisi de genel bir sınıftan devraldığı bir genel sınıfın `ColorDrawing` ve genel sınıfın örneklerini içerir `BlackAndWhiteDrawing` `Drawing` .</span><span class="sxs-lookup"><span data-stu-id="abd98-171">The `theDrawing` field contains instances of a generic class `ColorDrawing` and a generic class `BlackAndWhiteDrawing`, both of which inherit from a generic class `Drawing`.</span></span> <span data-ttu-id="abd98-172">Normalde, her ikisi de bilinen türlere eklenmelidir, ancak öznitelikler için geçerli sözdizimi şu değildir.</span><span class="sxs-lookup"><span data-stu-id="abd98-172">Normally, both must be added to known types, but the following is not valid syntax for attributes.</span></span>  
  
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
  
 <span data-ttu-id="abd98-173">Bu nedenle, bu türleri döndürmek için bir yöntem oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="abd98-173">Thus, a method must be created to return these types.</span></span> <span data-ttu-id="abd98-174">Bu türü yazmanın doğru yolu aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="abd98-174">The correct way to write this type, then, is shown in the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#10)]
 [!code-vb[C_KnownTypeAttribute#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#10)]  
  
## <a name="additional-ways-to-add-known-types"></a><span data-ttu-id="abd98-175">Bilinen türleri eklemenin ek yolları</span><span class="sxs-lookup"><span data-stu-id="abd98-175">Additional Ways to Add Known Types</span></span>  
 <span data-ttu-id="abd98-176">Ayrıca, bilinen türler bir yapılandırma dosyası aracılığıyla eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="abd98-176">Additionally, known types can be added through a configuration file.</span></span> <span data-ttu-id="abd98-177">Bu, Windows Communication Foundation (WCF) ile üçüncü taraf tür kitaplıkları kullanırken olduğu gibi, doğru seri durumundan çıkarma için bilinen türler gerektiren türü denetlemediğinde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="abd98-177">This is useful when you do not control the type that requires known types for proper deserialization, such as when using third-party type libraries with Windows Communication Foundation (WCF).</span></span>  
  
 <span data-ttu-id="abd98-178">Aşağıdaki yapılandırma dosyasında, bir yapılandırma dosyasında bilinen bir türün nasıl belirtilmesi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="abd98-178">The following configuration file shows how to specify a known type in a configuration file.</span></span>  
  
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
  
 <span data-ttu-id="abd98-179">Yukarıdaki yapılandırma dosyasında, çağrılan bir veri anlaşması türü `MyCompany.Library.Shape` bilinen bir tür olacak şekilde bildirilmiştir `MyCompany.Library.Circle` .</span><span class="sxs-lookup"><span data-stu-id="abd98-179">In the preceding configuration file a data contract type called `MyCompany.Library.Shape` is declared to have `MyCompany.Library.Circle` as a known type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abd98-180">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="abd98-180">See also</span></span>

- <xref:System.Runtime.Serialization.KnownTypeAttribute>
- <xref:System.Collections.Hashtable>
- <xref:System.Object>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A>
- [<span data-ttu-id="abd98-181">Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="abd98-181">Known Types</span></span>](../samples/known-types.md)
- [<span data-ttu-id="abd98-182">Veri Sözleşmesi Eşitliği</span><span class="sxs-lookup"><span data-stu-id="abd98-182">Data Contract Equivalence</span></span>](data-contract-equivalence.md)
- [<span data-ttu-id="abd98-183">Hizmet Sözleşmeleri Tasarlama</span><span class="sxs-lookup"><span data-stu-id="abd98-183">Designing Service Contracts</span></span>](../designing-service-contracts.md)
