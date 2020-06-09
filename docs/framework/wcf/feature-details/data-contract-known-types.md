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
ms.openlocfilehash: b7d78def4d656dea59af5400c7ed7deeef28cd0c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597455"
---
# <a name="data-contract-known-types"></a><span data-ttu-id="f49b4-102">Veri Sözleşmesi Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="f49b4-102">Data Contract Known Types</span></span>
<span data-ttu-id="f49b4-103"><xref:System.Runtime.Serialization.KnownTypeAttribute>Sınıfı, serisini kaldırma sırasında dikkate alınması gereken türleri önceden belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="f49b4-103">The <xref:System.Runtime.Serialization.KnownTypeAttribute> class allows you to specify, in advance, the types that should be included for consideration during deserialization.</span></span> <span data-ttu-id="f49b4-104">Çalışan bir örnek için, [bilinen türler](../samples/known-types.md) örneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="f49b4-104">For a working example, see the [Known Types](../samples/known-types.md) example.</span></span>  
  
 <span data-ttu-id="f49b4-105">Normalde, parametreleri geçirirken ve bir istemci ile bir hizmet arasında değer döndürmelerinde, her iki uç nokta de iletilmek üzere verilerin tüm veri sözleşmelerini paylaşır.</span><span class="sxs-lookup"><span data-stu-id="f49b4-105">Normally, when passing parameters and return values between a client and a service, both endpoints share all of the data contracts of the data to be transmitted.</span></span> <span data-ttu-id="f49b4-106">Ancak, aşağıdaki durumlarda bu durum böyle değildir:</span><span class="sxs-lookup"><span data-stu-id="f49b4-106">However, this is not the case in the following circumstances:</span></span>  
  
- <span data-ttu-id="f49b4-107">Gönderilen veri sözleşmesi, beklenen veri sözleşmesinden türetilir.</span><span class="sxs-lookup"><span data-stu-id="f49b4-107">The sent data contract is derived from the expected data contract.</span></span> <span data-ttu-id="f49b4-108">Daha fazla bilgi için, [veri sözleşmesindeki](data-contract-equivalence.md)devralma hakkında bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="f49b4-108">For more information, see the section about inheritance in [Data Contract Equivalence](data-contract-equivalence.md)).</span></span> <span data-ttu-id="f49b4-109">Bu durumda, iletilen veriler, alıcı uç noktası tarafından beklenen veri sözleşmesine sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="f49b4-109">In that case, the transmitted data does not have the same data contract as expected by the receiving endpoint.</span></span>  
  
- <span data-ttu-id="f49b4-110">İletilecek bilgiler için, bir sınıf, yapı veya numaralandırmanın aksine, bir arabirim olduğu bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f49b4-110">The declared type for the information to be transmitted is an interface, as opposed to a class, structure, or enumeration.</span></span> <span data-ttu-id="f49b4-111">Bu nedenle, arabirimi uygulayan türün gerçekten gönderildiği ve bu nedenle alıcı uç noktasının iletilen veriler için veri sözleşmesinin ön planda belirleyemediği bilinmez.</span><span class="sxs-lookup"><span data-stu-id="f49b4-111">Therefore, it cannot be known in advance which type that implements the interface is actually sent and therefore, the receiving endpoint cannot determine in advance the data contract for the transmitted data.</span></span>  
  
- <span data-ttu-id="f49b4-112">İletilecek bilgiler için belirtilen tür <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="f49b4-112">The declared type for the information to be transmitted is <xref:System.Object>.</span></span> <span data-ttu-id="f49b4-113">Her tür öğesinden devralındığından <xref:System.Object> ve bu türün gerçekten gönderildiği bilinmediği için, alıcı uç noktası aktarılan verilerin veri sözleşmesinin ön planda saptanamıyor.</span><span class="sxs-lookup"><span data-stu-id="f49b4-113">Because every type inherits from <xref:System.Object>, and it cannot be known in advance which type is actually sent, the receiving endpoint cannot determine in advance the data contract for the transmitted data.</span></span> <span data-ttu-id="f49b4-114">Bu, ilk öğenin özel bir durumdur: her veri sözleşmesi, için oluşturulan boş bir veri sözleşmesinin varsayılan değerinden türetilir <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="f49b4-114">This is a special case of the first item: Every data contract derives from the default, a blank data contract that is generated for <xref:System.Object>.</span></span>  
  
- <span data-ttu-id="f49b4-115">.NET Framework türlerini içeren bazı türlerin önceki üç kategoriden birinde olan üyeleri vardır.</span><span class="sxs-lookup"><span data-stu-id="f49b4-115">Some types, which include .NET Framework types, have members that are in one of the preceding three categories.</span></span> <span data-ttu-id="f49b4-116">Örneğin, <xref:System.Collections.Hashtable> <xref:System.Object> karma tablodaki gerçek nesneleri depolamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="f49b4-116">For example, <xref:System.Collections.Hashtable> uses <xref:System.Object> to store the actual objects in the hash table.</span></span> <span data-ttu-id="f49b4-117">Bu türler serileştirilirken, alıcı taraf bu üyeler için veri sözleşmesinin ön kısmına göre saptanamaz.</span><span class="sxs-lookup"><span data-stu-id="f49b4-117">When serializing these types, the receiving side cannot determine in advance the data contract for these members.</span></span>  
  
## <a name="the-knowntypeattribute-class"></a><span data-ttu-id="f49b4-118">KnownTypeAttribute sınıfı</span><span class="sxs-lookup"><span data-stu-id="f49b4-118">The KnownTypeAttribute Class</span></span>  
 <span data-ttu-id="f49b4-119">Veriler alma uç noktasına ulaştığında, WCF çalışma zamanı verileri ortak dil çalışma zamanı (CLR) türünün bir örneğine serisini kaldırma girişiminde bulunur.</span><span class="sxs-lookup"><span data-stu-id="f49b4-119">When data arrives at a receiving endpoint, the WCF runtime attempts to deserialize the data into an instance of a common language runtime (CLR) type.</span></span> <span data-ttu-id="f49b4-120">Seri durumdan çıkarma için örneği oluşturulan tür, önce iletinin içeriğinin uyumlu olduğu veri sözleşmesinin belirlenmesi için gelen iletiyi inceleyerek seçilir.</span><span class="sxs-lookup"><span data-stu-id="f49b4-120">The type that is instantiated for deserialization is chosen by first inspecting the incoming message to determine the data contract to which the contents of the message conform.</span></span> <span data-ttu-id="f49b4-121">Seri kaldırma altyapısı daha sonra ileti içeriğiyle uyumlu bir veri sözleşmesi uygulayan bir CLR türü bulmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="f49b4-121">The deserialization engine then attempts to find a CLR type that implements a data contract compatible with the message contents.</span></span> <span data-ttu-id="f49b4-122">Seri durumdan çıkarma altyapısının bu işlem sırasında izin verdiği aday türleri kümesi, seri hale getirici 'nin "bilinen türler" kümesi olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="f49b4-122">The set of candidate types that the deserialization engine allows for during this process is referred to as the deserializer's set of "known types."</span></span>  
  
 <span data-ttu-id="f49b4-123">Seri durumdan çıkarma altyapısının bir tür hakkında bilgi almasına imkan sağlamanın bir yolu, ' nı kullanmaktır <xref:System.Runtime.Serialization.KnownTypeAttribute> .</span><span class="sxs-lookup"><span data-stu-id="f49b4-123">One way to let the deserialization engine know about a type is by using the <xref:System.Runtime.Serialization.KnownTypeAttribute>.</span></span> <span data-ttu-id="f49b4-124">Öznitelik, tek tek veri üyelerine yalnızca tüm veri anlaşması türlerine uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="f49b4-124">The attribute cannot be applied to individual data members, only to whole data contract types.</span></span> <span data-ttu-id="f49b4-125">Özniteliği, bir sınıf veya yapı olabilecek bir *dış türe* uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f49b4-125">The attribute is applied to an *outer type* that can be a class or a structure.</span></span> <span data-ttu-id="f49b4-126">En temel kullanımındaki özniteliği uygulamak, bir türü "bilinen tür" olarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="f49b4-126">In its most basic usage, applying the attribute specifies a type as a "known type."</span></span> <span data-ttu-id="f49b4-127">Bu, dış türdeki bir nesne veya üyeleri aracılığıyla başvurulan herhangi bir nesne seri durumdan çıkarıldığı zaman bilinen türün bilinen türler kümesinin bir parçası olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="f49b4-127">This causes the known type to be a part of the set of known types whenever an object of the outer type or any object referred to through its members is being deserialized.</span></span> <span data-ttu-id="f49b4-128"><xref:System.Runtime.Serialization.KnownTypeAttribute>Aynı türde birden fazla öznitelik uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="f49b4-128">More than one <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute can be applied to the same type.</span></span>  
  
## <a name="known-types-and-primitives"></a><span data-ttu-id="f49b4-129">Bilinen türler ve temel elemanlar</span><span class="sxs-lookup"><span data-stu-id="f49b4-129">Known Types and Primitives</span></span>  
 <span data-ttu-id="f49b4-130">İlkel türler ve temel öğeler (örneğin, ve) olarak değerlendirilen belirli türler <xref:System.DateTime> <xref:System.Xml.XmlElement> her zaman "biliniyor" ve bu mekanizmaya hiç eklenmemek zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="f49b4-130">Primitive types, as well as certain types treated as primitives (for example, <xref:System.DateTime> and <xref:System.Xml.XmlElement>) are always "known" and never have to be added through this mechanism.</span></span> <span data-ttu-id="f49b4-131">Ancak, temel türlerin dizileri açıkça eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="f49b4-131">However, arrays of primitive types have to be added explicitly.</span></span> <span data-ttu-id="f49b4-132">Çoğu koleksiyon dizilere eşit kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="f49b4-132">Most collections are considered equivalent to arrays.</span></span> <span data-ttu-id="f49b4-133">(Genel olmayan koleksiyonlar diziler için eşdeğer olarak kabul edilir <xref:System.Object> ).</span><span class="sxs-lookup"><span data-stu-id="f49b4-133">(Non-generic collections are considered equivalent to arrays of <xref:System.Object>).</span></span> <span data-ttu-id="f49b4-134">Temel elemanlar, ilkel diziler ve basit koleksiyonlar kullanmanın bir örneği için bkz. örnek 4.</span><span class="sxs-lookup"><span data-stu-id="f49b4-134">For an example of the using primitives, primitive arrays, and primitive collections, see Example 4.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f49b4-135">Diğer temel türlerin aksine, <xref:System.DateTimeOffset> Yapı varsayılan olarak bilinen bir tür değildir, bu nedenle bilinen türler listesine el ile eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="f49b4-135">Unlike other primitive types, the <xref:System.DateTimeOffset> structure is not a known type by default, so it must be manually added to the list of known types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="f49b4-136">Örnekler</span><span class="sxs-lookup"><span data-stu-id="f49b4-136">Examples</span></span>  
 <span data-ttu-id="f49b4-137">Aşağıdaki örneklerde <xref:System.Runtime.Serialization.KnownTypeAttribute> kullanılan sınıf gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f49b4-137">The following examples show the <xref:System.Runtime.Serialization.KnownTypeAttribute> class in use.</span></span>  
  
#### <a name="example-1"></a><span data-ttu-id="f49b4-138">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="f49b4-138">Example 1</span></span>  
 <span data-ttu-id="f49b4-139">Devralma ilişkisine sahip üç sınıf vardır.</span><span class="sxs-lookup"><span data-stu-id="f49b4-139">There are three classes with an inheritance relationship.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#1)]
 [!code-vb[C_KnownTypeAttribute#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#1)]  
  
 <span data-ttu-id="f49b4-140">Aşağıdaki `CompanyLogo` sınıf seri hale getirilebilir, ancak `ShapeOfLogo` üye bir ya da bir nesne olarak ayarlandıysa seri durumdan çıkarılamaz, `CircleType` `TriangleType` çünkü serisini kaldırma altyapısı veri sözleşme adları "Circle" veya "Triangle" olan herhangi bir türü tanımaz.</span><span class="sxs-lookup"><span data-stu-id="f49b4-140">The following `CompanyLogo` class can be serialized, but cannot be deserialized if the `ShapeOfLogo` member is set to either a `CircleType` or a `TriangleType` object, because the deserialization engine does not recognize any types with data contract names "Circle" or "Triangle."</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#2)]
 [!code-vb[C_KnownTypeAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#2)]  
  
 <span data-ttu-id="f49b4-141">Türü yazmanın doğru yolu `CompanyLogo` aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f49b4-141">The correct way to write the `CompanyLogo` type is shown in the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#3)]
 [!code-vb[C_KnownTypeAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#3)]  
  
 <span data-ttu-id="f49b4-142">Dış tür `CompanyLogo2` seri durumdan çıkarılabildiğinde, seri durumdan çıkarma motoru `CircleType` ve ile ilgili olarak, `TriangleType` "daire" ve "üçgen" veri sözleşmeleri için eşleşen türleri bulabilir.</span><span class="sxs-lookup"><span data-stu-id="f49b4-142">Whenever the outer type `CompanyLogo2` is being deserialized, the deserialization engine knows about `CircleType` and `TriangleType` and, therefore, is able to find matching types for the "Circle" and "Triangle" data contracts.</span></span>  
  
#### <a name="example-2"></a><span data-ttu-id="f49b4-143">Örnek 2</span><span class="sxs-lookup"><span data-stu-id="f49b4-143">Example 2</span></span>  
 <span data-ttu-id="f49b4-144">Aşağıdaki örnekte, her ikisi de `CustomerTypeA` ve veri sözleşmesine sahip olsa bile, her `CustomerTypeB` `Customer` `CustomerTypeB` bir seri hale geldiğinde bir örneği oluşturulur `PurchaseOrder` , çünkü yalnızca seri durumdan `CustomerTypeB` çıkarma altyapısı tarafından bilinir.</span><span class="sxs-lookup"><span data-stu-id="f49b4-144">In the following example, even though both `CustomerTypeA` and `CustomerTypeB` have the `Customer` data contract, an instance of `CustomerTypeB` is created whenever a `PurchaseOrder` is deserialized, because only `CustomerTypeB` is known to the deserialization engine.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#4)]
 [!code-vb[C_KnownTypeAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#4)]  
  
#### <a name="example-3"></a><span data-ttu-id="f49b4-145">Örnek 3</span><span class="sxs-lookup"><span data-stu-id="f49b4-145">Example 3</span></span>  
 <span data-ttu-id="f49b4-146">Aşağıdaki örnekte, bir, <xref:System.Collections.Hashtable> içeriğini dahili olarak depolar <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="f49b4-146">In the following example, a <xref:System.Collections.Hashtable> stores its contents internally as <xref:System.Object>.</span></span> <span data-ttu-id="f49b4-147">Bir karma tablonun serisini başarıyla kaldırmak için, seri durumdan çıkarma altyapısının, burada oluşabilecek olası türler kümesini bilmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="f49b4-147">To successfully deserialize a hash table, the deserialization engine must know the set of possible types that can occur there.</span></span> <span data-ttu-id="f49b4-148">Bu durumda, yalnızca `Book` ve `Magazine` nesnelerinin üzerinde depolandıkları için, bu, `Catalog` öznitelik kullanılarak eklenmeleri durumunda olduğunu biliyoruz <xref:System.Runtime.Serialization.KnownTypeAttribute> .</span><span class="sxs-lookup"><span data-stu-id="f49b4-148">In this case, we know in advance that only `Book` and `Magazine` objects are stored in the `Catalog`, so those are added using the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#5)]
 [!code-vb[C_KnownTypeAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#5)]  
  
#### <a name="example-4"></a><span data-ttu-id="f49b4-149">Örnek 4</span><span class="sxs-lookup"><span data-stu-id="f49b4-149">Example 4</span></span>  
 <span data-ttu-id="f49b4-150">Aşağıdaki örnekte, bir veri sözleşmesi numarayı ve numara üzerinde gerçekleştirilecek bir işlemi depolar.</span><span class="sxs-lookup"><span data-stu-id="f49b4-150">In the following example, a data contract stores a number and an operation to perform on the number.</span></span> <span data-ttu-id="f49b4-151">`Numbers`Veri üyesi tamsayı, tamsayılar dizisi veya tamsayılar içeren bir dize olabilir <xref:System.Collections.Generic.List%601> .</span><span class="sxs-lookup"><span data-stu-id="f49b4-151">The `Numbers` data member can be an integer, an array of integers, or a <xref:System.Collections.Generic.List%601> that contains integers.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="f49b4-152">Bu, yalnızca SVCUTIL ise istemci tarafında çalışır. EXE, bir WCF proxy oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f49b4-152">This will only work on the client side if SVCUTIL.EXE is used to generate a WCF proxy.</span></span> <span data-ttu-id="f49b4-153">SVCUTIL. EXE, bilinen türler dahil olmak üzere hizmetten meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="f49b4-153">SVCUTIL.EXE retrieves metadata from the service including any known types.</span></span> <span data-ttu-id="f49b4-154">Bu bilgiler olmadan, istemci türlerin serisini kaldıramıyor.</span><span class="sxs-lookup"><span data-stu-id="f49b4-154">Without this information a client will not be able to deserialize the types.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#6)]
 [!code-vb[C_KnownTypeAttribute#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#6)]  
  
 <span data-ttu-id="f49b4-155">Bu uygulama kodudur.</span><span class="sxs-lookup"><span data-stu-id="f49b4-155">This is the application code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#7)]
 [!code-vb[C_KnownTypeAttribute#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#7)]  
  
## <a name="known-types-inheritance-and-interfaces"></a><span data-ttu-id="f49b4-156">Bilinen türler, devralma ve arabirimler</span><span class="sxs-lookup"><span data-stu-id="f49b4-156">Known Types, Inheritance, and Interfaces</span></span>  
 <span data-ttu-id="f49b4-157">Bilinen bir tür özniteliği kullanılarak belirli bir türle ilişkilendirildiğinde `KnownTypeAttribute` , bilinen tür aynı zamanda bu türün türetilmiş tüm türleri ile ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="f49b4-157">When a known type is associated with a particular type using the `KnownTypeAttribute` attribute, the known type is also associated with all of the derived types of that type.</span></span> <span data-ttu-id="f49b4-158">Örneğin, aşağıdaki koda bakın.</span><span class="sxs-lookup"><span data-stu-id="f49b4-158">For example, see the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#8)]
 [!code-vb[C_KnownTypeAttribute#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#8)]  
  
 <span data-ttu-id="f49b4-159">`DoubleDrawing` `KnownTypeAttribute` `Square` `Circle` `AdditionalShape` Temel sınıf ( `Drawing` ) zaten bu özniteliklerin uygulanmış olması nedeniyle, sınıfı, ' ın ve alan içinde özniteliğini gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="f49b4-159">The `DoubleDrawing` class does not require the `KnownTypeAttribute` attribute to use `Square` and `Circle` in the `AdditionalShape` field, because the base class (`Drawing`) already has these attributes applied.</span></span>  
  
 <span data-ttu-id="f49b4-160">Bilinen türler, arabirimler değil yalnızca sınıflar ve yapılar ile ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="f49b4-160">Known types can be associated only with classes and structures, not interfaces.</span></span>  
  
## <a name="known-types-using-open-generic-methods"></a><span data-ttu-id="f49b4-161">Açık genel yöntemler kullanan bilinen türler</span><span class="sxs-lookup"><span data-stu-id="f49b4-161">Known Types Using Open Generic Methods</span></span>  
 <span data-ttu-id="f49b4-162">Bilinen bir tür olarak genel bir tür eklemek gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="f49b4-162">It may be necessary to add a generic type as a known type.</span></span> <span data-ttu-id="f49b4-163">Ancak açık genel tür özniteliğe parametre olarak geçirilemez `KnownTypeAttribute` .</span><span class="sxs-lookup"><span data-stu-id="f49b4-163">However, an open generic type cannot be passed as a parameter to the `KnownTypeAttribute` attribute.</span></span>  
  
 <span data-ttu-id="f49b4-164">Bu sorun, alternatif bir mekanizma kullanılarak çözülebilir: bilinen türler koleksiyonuna eklemek üzere türlerin bir listesini döndüren bir yöntem yazın.</span><span class="sxs-lookup"><span data-stu-id="f49b4-164">This problem can be solved by using an alternative mechanism: Write a method that returns a list of types to add to the known types collection.</span></span> <span data-ttu-id="f49b4-165">Yöntemin adı, daha sonra `KnownTypeAttribute` bazı kısıtlamalar nedeniyle özniteliğe dize bağımsız değişkeni olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="f49b4-165">The name of the method is then specified as a string argument to the `KnownTypeAttribute` attribute due to some restrictions.</span></span>  
  
 <span data-ttu-id="f49b4-166">Yöntemin, özniteliğin uygulandığı türde olması gerekir `KnownTypeAttribute` , statik olması gerekir, parametre içermemelidir ve ' nin atanabileceği bir nesne döndürmesi gerekir <xref:System.Collections.IEnumerable> <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="f49b4-166">The method must exist on the type to which the `KnownTypeAttribute` attribute is applied, must be static, must accept no parameters, and must return an object that can be assigned to <xref:System.Collections.IEnumerable> of <xref:System.Type>.</span></span>  
  
 <span data-ttu-id="f49b4-167">`KnownTypeAttribute`Özniteliği, `KnownTypeAttribute` aynı türde gerçek türler içeren bir yöntem adı ve özniteliklerle birleştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="f49b4-167">You cannot combine the `KnownTypeAttribute` attribute with a method name and `KnownTypeAttribute` attributes with actual types on the same type.</span></span> <span data-ttu-id="f49b4-168">Ayrıca, `KnownTypeAttribute` aynı türde bir yöntem adına sahip birden fazla tane uygulayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="f49b4-168">Furthermore, you cannot apply more than one `KnownTypeAttribute` with a method name to the same type.</span></span>  
  
 <span data-ttu-id="f49b4-169">Aşağıdaki sınıfa bakın.</span><span class="sxs-lookup"><span data-stu-id="f49b4-169">See the following class.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#9)]
 [!code-vb[C_KnownTypeAttribute#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#9)]  
  
 <span data-ttu-id="f49b4-170">`theDrawing`Alan, her ikisi de genel bir sınıftan devraldığı bir genel sınıfın `ColorDrawing` ve genel sınıfın örneklerini içerir `BlackAndWhiteDrawing` `Drawing` .</span><span class="sxs-lookup"><span data-stu-id="f49b4-170">The `theDrawing` field contains instances of a generic class `ColorDrawing` and a generic class `BlackAndWhiteDrawing`, both of which inherit from a generic class `Drawing`.</span></span> <span data-ttu-id="f49b4-171">Normalde, her ikisi de bilinen türlere eklenmelidir, ancak öznitelikler için geçerli sözdizimi şu değildir.</span><span class="sxs-lookup"><span data-stu-id="f49b4-171">Normally, both must be added to known types, but the following is not valid syntax for attributes.</span></span>  
  
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
  
 <span data-ttu-id="f49b4-172">Bu nedenle, bu türleri döndürmek için bir yöntem oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f49b4-172">Thus, a method must be created to return these types.</span></span> <span data-ttu-id="f49b4-173">Bu türü yazmanın doğru yolu aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f49b4-173">The correct way to write this type, then, is shown in the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#10)]
 [!code-vb[C_KnownTypeAttribute#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#10)]  
  
## <a name="additional-ways-to-add-known-types"></a><span data-ttu-id="f49b4-174">Bilinen türleri eklemenin ek yolları</span><span class="sxs-lookup"><span data-stu-id="f49b4-174">Additional Ways to Add Known Types</span></span>  
 <span data-ttu-id="f49b4-175">Ayrıca, bilinen türler bir yapılandırma dosyası aracılığıyla eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="f49b4-175">Additionally, known types can be added through a configuration file.</span></span> <span data-ttu-id="f49b4-176">Bu, Windows Communication Foundation (WCF) ile üçüncü taraf tür kitaplıkları kullanırken olduğu gibi, doğru seri durumundan çıkarma için bilinen türler gerektiren türü denetlemediğinde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="f49b4-176">This is useful when you do not control the type that requires known types for proper deserialization, such as when using third-party type libraries with Windows Communication Foundation (WCF).</span></span>  
  
 <span data-ttu-id="f49b4-177">Aşağıdaki yapılandırma dosyasında, bir yapılandırma dosyasında bilinen bir türün nasıl belirtilmesi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f49b4-177">The following configuration file shows how to specify a known type in a configuration file.</span></span>  
  
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
  
 <span data-ttu-id="f49b4-178">Yukarıdaki yapılandırma dosyasında, çağrılan bir veri anlaşması türü `MyCompany.Library.Shape` bilinen bir tür olacak şekilde bildirilmiştir `MyCompany.Library.Circle` .</span><span class="sxs-lookup"><span data-stu-id="f49b4-178">In the preceding configuration file a data contract type called `MyCompany.Library.Shape` is declared to have `MyCompany.Library.Circle` as a known type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f49b4-179">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f49b4-179">See also</span></span>

- <xref:System.Runtime.Serialization.KnownTypeAttribute>
- <xref:System.Collections.Hashtable>
- <xref:System.Object>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A>
- [<span data-ttu-id="f49b4-180">Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="f49b4-180">Known Types</span></span>](../samples/known-types.md)
- [<span data-ttu-id="f49b4-181">Veri Sözleşmesi Eşitliği</span><span class="sxs-lookup"><span data-stu-id="f49b4-181">Data Contract Equivalence</span></span>](data-contract-equivalence.md)
- [<span data-ttu-id="f49b4-182">Hizmet Sözleşmeleri Tasarlama</span><span class="sxs-lookup"><span data-stu-id="f49b4-182">Designing Service Contracts</span></span>](../designing-service-contracts.md)
