---
title: Sağlayıcı Bildirimi Belirtimi
ms.date: 03/30/2017
ms.assetid: bb450b47-8951-4f99-9350-26f05a4d4e46
ms.openlocfilehash: cc58bbc82f3930f087b5da0c64afb4f9f03e905b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854495"
---
# <a name="provider-manifest-specification"></a><span data-ttu-id="7ed28-102">Sağlayıcı Bildirimi Belirtimi</span><span class="sxs-lookup"><span data-stu-id="7ed28-102">Provider Manifest Specification</span></span>
<span data-ttu-id="7ed28-103">Bu bölümde, bir veri deposu sağlayıcısının veri deposundaki türleri ve işlevleri nasıl destekleyebileceği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7ed28-103">This section discusses how a data store provider can support the types and functions in the data store.</span></span>  
  
 <span data-ttu-id="7ed28-104">Varlık hizmetleri belirli bir veri deposu sağlayıcısından bağımsız olarak çalışır, ancak bir veri sağlayıcısının model, eşlemeler ve sorguların temel alınan bir veri deposuyla nasıl etkileşim kuracağını açıkça tanımlamasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="7ed28-104">Entity Services operates independently of a specific data store provider yet still allows a data provider to explicitly define how models, mappings, and queries interact with an underlying data store.</span></span> <span data-ttu-id="7ed28-105">Bir soyutlama katmanı olmadan, varlık Hizmetleri yalnızca belirli bir veri deposuna veya veri sağlayıcısına hedeflenebilir.</span><span class="sxs-lookup"><span data-stu-id="7ed28-105">Without a layer of abstraction, Entity Services could only be targeted at a specific data store or data provider.</span></span>  
  
 <span data-ttu-id="7ed28-106">Sağlayıcının desteklediği türler, temel alınan veritabanı tarafından doğrudan veya dolaylı olarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="7ed28-106">Types that the provider supports are directly or indirectly supported by the underlying database.</span></span> <span data-ttu-id="7ed28-107">Bu türlerin tam depo türleri olması gerekmez, ancak sağlayıcının Entity Framework desteklemek için kullandığı türler.</span><span class="sxs-lookup"><span data-stu-id="7ed28-107">These types are not necessarily the exact store types, but the types the provider uses to support the Entity Framework.</span></span> <span data-ttu-id="7ed28-108">Sağlayıcı/depolama türleri Varlık Veri Modeli (EDM) koşullarında açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="7ed28-108">Provider/store types are described in the Entity Data Model (EDM) terms.</span></span>  
  
 <span data-ttu-id="7ed28-109">Veri deposunun desteklediği işlevlerin parametresi ve dönüş türleri EDM koşullarında belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7ed28-109">Parameter and return types for the functions supported by the data store are specified in EDM terms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ed28-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7ed28-110">Requirements</span></span>  
 <span data-ttu-id="7ed28-111">Entity Framework ve veri deposunun verileri, herhangi bir veri kaybı veya kesilme olmadan bilinen türlerde geri ve ileri geçirebilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="7ed28-111">The Entity Framework and the data store need to be able to pass data back and forth in known types without any data loss or truncation.</span></span>  
  
 <span data-ttu-id="7ed28-112">Sağlayıcı bildirimi, veri deposuna bir bağlantı açmak zorunda kalmadan tasarım zamanında araçlar tarafından yüklenebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7ed28-112">The provider manifest must be loadable by tools at design time without having to open a connection to the data store.</span></span>  
  
 <span data-ttu-id="7ed28-113">Entity Framework büyük/küçük harfe duyarlıdır, ancak temel alınan veri deposu olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="7ed28-113">The Entity Framework is case sensitive, but the underlying data store may not be.</span></span> <span data-ttu-id="7ed28-114">EDM yapıtlar (örneğin, tanımlayıcılar ve tür adları) tanımlandıklarında ve bildiriminde kullanıldığında, Entity Framework büyük/küçük harf duyarlılığı kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7ed28-114">When EDM artifacts (identifiers and type names, for example) are defined and used in the manifest, they must use the Entity Framework case sensitivity.</span></span> <span data-ttu-id="7ed28-115">Büyük/küçük harfe duyarlı olabilecek veri deposu öğeleri sağlayıcı bildiriminde görünürse, bu büyük/küçük harf sağlayıcısı bildiriminde saklanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7ed28-115">If data store elements that may be case sensitive appear in the provider manifest, that casing needs to be maintained in the provider manifest.</span></span>  
  
 <span data-ttu-id="7ed28-116">Entity Framework tüm veri sağlayıcıları için bir sağlayıcı bildirimi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7ed28-116">The Entity Framework requires a provider manifest for all data providers.</span></span> <span data-ttu-id="7ed28-117">Entity Framework bir sağlayıcı bildirimine sahip olmayan bir sağlayıcıyı kullanmayı denerseniz, bir hata alırsınız.</span><span class="sxs-lookup"><span data-stu-id="7ed28-117">If you try to use a provider that does not have a provider manifest with the Entity Framework, you will get an error.</span></span>  
  
 <span data-ttu-id="7ed28-118">Aşağıdaki tabloda, sağlayıcı etkileşimi üzerinden özel durumlar ortaya çıktığında Entity Framework özel durumların türleri açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="7ed28-118">The following table describes the kinds of exceptions the Entity Framework would throw when exceptions arise through provider interaction:</span></span>  
  
|<span data-ttu-id="7ed28-119">Sorun</span><span class="sxs-lookup"><span data-stu-id="7ed28-119">Issue</span></span>|<span data-ttu-id="7ed28-120">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="7ed28-120">Exception</span></span>|  
|-----------|---------------|  
|<span data-ttu-id="7ed28-121">Sağlayıcı, DbProviderServices 'de GetProviderManifest 'i desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="7ed28-121">The Provider does not support GetProviderManifest in DbProviderServices.</span></span>|<span data-ttu-id="7ed28-122">ProviderIncompatibleException</span><span class="sxs-lookup"><span data-stu-id="7ed28-122">ProviderIncompatibleException</span></span>|  
|<span data-ttu-id="7ed28-123">Eksik sağlayıcı bildirimi: sağlayıcı, sağlayıcı `null` bildirimini almaya çalışırken döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="7ed28-123">Missing provider manifest: the provider returns `null` when attempting to retrieve the provider manifest.</span></span>|<span data-ttu-id="7ed28-124">ProviderIncompatibleException</span><span class="sxs-lookup"><span data-stu-id="7ed28-124">ProviderIncompatibleException</span></span>|  
|<span data-ttu-id="7ed28-125">Geçersiz sağlayıcı bildirimi: sağlayıcı, sağlayıcı bildirimini almaya çalışırken geçersiz XML döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="7ed28-125">Invalid provider manifest: the provider returns invalid XML when attempting to retrieve the provider manifest.</span></span>|<span data-ttu-id="7ed28-126">ProviderIncompatibleException</span><span class="sxs-lookup"><span data-stu-id="7ed28-126">ProviderIncompatibleException</span></span>|  
  
## <a name="scenarios"></a><span data-ttu-id="7ed28-127">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="7ed28-127">Scenarios</span></span>  
 <span data-ttu-id="7ed28-128">Sağlayıcı aşağıdaki senaryoları desteklemelidir:</span><span class="sxs-lookup"><span data-stu-id="7ed28-128">A provider should support the following scenarios:</span></span>  
  
### <a name="writing-a-provider-with-symmetric-type-mapping"></a><span data-ttu-id="7ed28-129">Simetrik tür eşleme ile sağlayıcı yazma</span><span class="sxs-lookup"><span data-stu-id="7ed28-129">Writing a Provider with Symmetric Type Mapping</span></span>  
 <span data-ttu-id="7ed28-130">Eşleme yönüne bakılmaksızın her bir mağaza türünün tek bir EDM türüne eşlendiği Entity Framework için bir sağlayıcı yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ed28-130">You can write a provider for the Entity Framework where each store type maps to a single EDM type, regardless of the mapping direction.</span></span> <span data-ttu-id="7ed28-131">Bir EDM türüne karşılık gelen çok basit eşlemeye sahip bir sağlayıcı türü için, tür sistemi basit veya EDM türleriyle eşleştiğinden, simetrik bir çözüm kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ed28-131">For a provider type that has very simple mapping that corresponds with an EDM type, you can use a symmetric solution because the type system is simple or matches EDM types.</span></span>  
  
 <span data-ttu-id="7ed28-132">Etki alanını basitlik olarak kullanabilir ve statik bir bildirime dayalı sağlayıcı bildirimi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ed28-132">You can use the simplicity of their domain and produce a static declarative provider manifest.</span></span>  
  
 <span data-ttu-id="7ed28-133">İki bölümden oluşan bir XML dosyası yazarsınız:</span><span class="sxs-lookup"><span data-stu-id="7ed28-133">You write an XML file that has two sections:</span></span>  
  
- <span data-ttu-id="7ed28-134">Bir depo türü veya işlevinin "EDM karşılığı" olarak ifade edilen sağlayıcı türlerinin listesi.</span><span class="sxs-lookup"><span data-stu-id="7ed28-134">A list of provider types expressed in terms of the "EDM counterpart" of a store type or function.</span></span> <span data-ttu-id="7ed28-135">Depo türlerinde karşılık gelen EDM türleri var.</span><span class="sxs-lookup"><span data-stu-id="7ed28-135">Store types have counterpart EDM types.</span></span> <span data-ttu-id="7ed28-136">Depo işlevlerinde karşılık gelen EDM işlevleri vardır.</span><span class="sxs-lookup"><span data-stu-id="7ed28-136">Store functions have corresponding EDM functions.</span></span> <span data-ttu-id="7ed28-137">Örneğin, varchar bir SQL Server türüdür, ancak karşılık gelen EDM türü dizedir.</span><span class="sxs-lookup"><span data-stu-id="7ed28-137">For example, varchar is a SQL Server type but the corresponding EDM type is string.</span></span>  
  
- <span data-ttu-id="7ed28-138">Sağlayıcı tarafından desteklenen ve parametre ve dönüş türlerinin EDM koşullarında ifade edildiği işlevlerin listesi.</span><span class="sxs-lookup"><span data-stu-id="7ed28-138">A list of functions supported by the provider where parameter and return types are expressed in EDM terms.</span></span>  
  
### <a name="writing-a-provider-with-asymmetric-type-mapping"></a><span data-ttu-id="7ed28-139">Asimetrik tür eşleme ile sağlayıcı yazma</span><span class="sxs-lookup"><span data-stu-id="7ed28-139">Writing a Provider with Asymmetric Type Mapping</span></span>  
 <span data-ttu-id="7ed28-140">Entity Framework için bir veri deposu sağlayıcısı yazarken, bazı türler için EDM-sağlayıcıya tür eşlemesi sağlayıcıdan EDM tür eşleştirmesinden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="7ed28-140">When writing a data store provider for the Entity Framework, the EDM-to-provider type mapping for some types may be different from provider-to-EDM type mapping.</span></span> <span data-ttu-id="7ed28-141">Örneğin, sınırlandırılmamış EDM PrimitiveTypeKind. String, sağlayıcıdaki nvarchar (4000) ile eşleşirken, nvarchar (4000), EDM PrimitiveTypeKind. String (MaxLength = 4000) ile eşlenir.</span><span class="sxs-lookup"><span data-stu-id="7ed28-141">For instance, unbounded EDM PrimitiveTypeKind.String may map to nvarchar(4000) on the provider, while nvarchar(4000) maps to the EDM PrimitiveTypeKind.String(MaxLength=4000).</span></span>  
  
 <span data-ttu-id="7ed28-142">İki bölümden oluşan bir XML dosyası yazarsınız:</span><span class="sxs-lookup"><span data-stu-id="7ed28-142">You write an XML file that has two sections:</span></span>  
  
- <span data-ttu-id="7ed28-143">EDM koşullarında ifade edilen ve her iki yön için eşlemeyi tanımlayan sağlayıcı türlerinin listesi: EDM-sağlayıcı ve sağlayıcıdan EDM.</span><span class="sxs-lookup"><span data-stu-id="7ed28-143">A list of provider types expressed in EDM terms and define mapping for both direction: EDM-to-provider and provider-to-EDM.</span></span>  
  
- <span data-ttu-id="7ed28-144">Sağlayıcı tarafından desteklenen ve parametre ve dönüş türlerinin EDM koşullarında ifade edildiği işlevlerin listesi.</span><span class="sxs-lookup"><span data-stu-id="7ed28-144">A list of functions supported by the provider where parameter and return types are expressed in EDM terms.</span></span>  
  
## <a name="provider-manifest-discoverability"></a><span data-ttu-id="7ed28-145">Sağlayıcı bildirimi bulunabilirliği</span><span class="sxs-lookup"><span data-stu-id="7ed28-145">Provider Manifest Discoverability</span></span>  
 <span data-ttu-id="7ed28-146">Bildirim, varlık hizmetlerindeki (örneğin, araçlar veya sorgu) çeşitli bileşen türleri tarafından dolaylı olarak kullanılır, ancak veri deposu meta veri yükleyicisinin kullanımı aracılığıyla meta veriler tarafından daha doğrudan yararlanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7ed28-146">The manifest is used indirectly by several component types in Entity Services (for example Tools or Query) but more directly leveraged by metadata through the use of the data store metadata loader.</span></span>  
  
 <span data-ttu-id="7ed28-147">![dfb3d02b&#45;7a8c&#45;4d51&#45;AC5A&#45;a73d8aa145e6](./media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-AC5A-a73d8aa145e6")</span><span class="sxs-lookup"><span data-stu-id="7ed28-147">![dfb3d02b&#45;7a8c&#45;4d51&#45;ac5a&#45;a73d8aa145e6](./media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6")</span></span>  
  
 <span data-ttu-id="7ed28-148">Ancak, belirli bir sağlayıcı aynı deponun farklı mağazalarını veya farklı sürümlerini destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="7ed28-148">However, a given provider may support different stores or different versions of the same store.</span></span> <span data-ttu-id="7ed28-149">Bu nedenle, bir sağlayıcı desteklenen her veri deposu için farklı bir bildirim rapormalıdır.</span><span class="sxs-lookup"><span data-stu-id="7ed28-149">Therefore, a provider must report a different manifest for each supported data store.</span></span>  
  
### <a name="provider-manifest-token"></a><span data-ttu-id="7ed28-150">Sağlayıcı bildirim belirteci</span><span class="sxs-lookup"><span data-stu-id="7ed28-150">Provider Manifest Token</span></span>  
 <span data-ttu-id="7ed28-151">Bir veri deposu bağlantısı açıldığında sağlayıcı, doğru bildirimi döndürecek bilgileri sorgulayabilir.</span><span class="sxs-lookup"><span data-stu-id="7ed28-151">When a data store connection is opened, the provider can query for information to return the right manifest.</span></span> <span data-ttu-id="7ed28-152">Bu, bağlantı bilgilerinin kullanılamadığı veya depoya bağlanamamasının mümkün olmadığı çevrimdışı senaryolarda mümkün olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="7ed28-152">This may not be possible in offline scenarios where connection information is not available or when it is not possible to connect to the store.</span></span> <span data-ttu-id="7ed28-153">. Ssdl dosyasındaki `ProviderManifestToken` `Schema` öğesinin özniteliğini kullanarak bildirimi belirler.</span><span class="sxs-lookup"><span data-stu-id="7ed28-153">Identify the manifest by using the `ProviderManifestToken` attribute of the `Schema` element in the .ssdl file.</span></span> <span data-ttu-id="7ed28-154">Bu öznitelik için gerekli biçim yok; sağlayıcı, depoya bir bağlantı açmadan bir bildirimi tanımlamak için gereken en düşük bilgileri seçer.</span><span class="sxs-lookup"><span data-stu-id="7ed28-154">There is no required format for this attribute; the provider chooses the minimum information needed to identify a manifest without opening a connection to the store.</span></span>  
  
 <span data-ttu-id="7ed28-155">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="7ed28-155">For example:</span></span>  
  
```xml  
<Schema Namespace="Northwind" Provider="System.Data.SqlClient" ProviderManifestToken="2005" xmlns:edm="http://schemas.microsoft.com/ado/2006/04/edm/ssdl" xmlns="http://schemas.microsoft.com/ado/2006/04/edm/ssdl">  
```  
  
## <a name="provider-manifest-programming-model"></a><span data-ttu-id="7ed28-156">Sağlayıcı bildirimi programlama modeli</span><span class="sxs-lookup"><span data-stu-id="7ed28-156">Provider Manifest Programming Model</span></span>  
 <span data-ttu-id="7ed28-157">Sağlayıcılar öğesinden <xref:System.Data.Common.DbXmlEnabledProviderManifest>türetilir, bu da kendilerine bildirimleri bildirimli olarak belirtmelerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="7ed28-157">Providers derive from <xref:System.Data.Common.DbXmlEnabledProviderManifest>, which allows them to specify their manifests declaratively.</span></span> <span data-ttu-id="7ed28-158">Aşağıdaki çizimde bir sağlayıcının sınıf hiyerarşisi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7ed28-158">The following illustration shows the class hierarchy of a provider:</span></span>  
  
 <span data-ttu-id="7ed28-159">![Hiçbiri](./media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")</span><span class="sxs-lookup"><span data-stu-id="7ed28-159">![None](./media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")</span></span>  
  
### <a name="discoverability-api"></a><span data-ttu-id="7ed28-160">Keşfedilebilirlik API 'SI</span><span class="sxs-lookup"><span data-stu-id="7ed28-160">Discoverability API</span></span>  
 <span data-ttu-id="7ed28-161">Sağlayıcı bildirimi, bir veri deposu bağlantısı veya sağlayıcı bildirim belirteci kullanılarak mağaza meta veri yükleyicisi (StoreItemCollection) tarafından yüklenir.</span><span class="sxs-lookup"><span data-stu-id="7ed28-161">The provider manifest is loaded by the Store Metadata loader (StoreItemCollection), either by using a data store connection or a provider manifest token.</span></span>  
  
#### <a name="using-a-data-store-connection"></a><span data-ttu-id="7ed28-162">Veri deposu bağlantısı kullanma</span><span class="sxs-lookup"><span data-stu-id="7ed28-162">Using a Data Store Connection</span></span>  
 <span data-ttu-id="7ed28-163">Veri deposu bağlantısı kullanılabilir olduğunda, ' i döndüren <xref:System.Data.Common.DbProviderServices.GetProviderManifestToken%2A?displayProperty=nameWithType> <xref:System.Data.Common.DbProviderServices.GetProviderManifest%2A> <xref:System.Data.Common.DbProviderManifest>yöntemine geçirilen belirteci döndürmek için çağırın.</span><span class="sxs-lookup"><span data-stu-id="7ed28-163">When the data store connection is available, call <xref:System.Data.Common.DbProviderServices.GetProviderManifestToken%2A?displayProperty=nameWithType> to return the token that is passed to the <xref:System.Data.Common.DbProviderServices.GetProviderManifest%2A> method, which returns <xref:System.Data.Common.DbProviderManifest>.</span></span> <span data-ttu-id="7ed28-164">Bu yöntem, sağlayıcının uygulamasını `GetDbProviderManifestToken`devreder.</span><span class="sxs-lookup"><span data-stu-id="7ed28-164">This method delegates to the provider's implementation of `GetDbProviderManifestToken`.</span></span>  
  
```csharp
public string GetProviderManifestToken(DbConnection connection);  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
#### <a name="using-a-provider-manifest-token"></a><span data-ttu-id="7ed28-165">Sağlayıcı bildirim belirteci kullanma</span><span class="sxs-lookup"><span data-stu-id="7ed28-165">Using a Provider Manifest Token</span></span>  
 <span data-ttu-id="7ed28-166">Çevrimdışı senaryo için, belirteç SSDL gösteriminden çekilir.</span><span class="sxs-lookup"><span data-stu-id="7ed28-166">For the offline scenario, the token is picked from SSDL representation.</span></span> <span data-ttu-id="7ed28-167">SSDL, bir ProviderManifestToken belirtmenize olanak tanır (daha fazla bilgi için bkz. [şema öğesi (ssdl)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl) ).</span><span class="sxs-lookup"><span data-stu-id="7ed28-167">The SSDL allows you to specify a ProviderManifestToken (see [Schema Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl) for more information).</span></span> <span data-ttu-id="7ed28-168">Örneğin, bir bağlantı açılamadığı için SSDL, bildirimle ilgili bilgileri belirten bir sağlayıcı bildirim belirtecine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="7ed28-168">For example, if a connection cannot be opened, the SSDL has a provider manifest token that specifies information about the manifest.</span></span>  
  
```  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
### <a name="provider-manifest-schema"></a><span data-ttu-id="7ed28-169">Sağlayıcı bildirim şeması</span><span class="sxs-lookup"><span data-stu-id="7ed28-169">Provider Manifest Schema</span></span>  
 <span data-ttu-id="7ed28-170">Her sağlayıcı için tanımlanan bilgilerin şeması, meta veriler tarafından tüketilen statik bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="7ed28-170">The schema of information defined for each provider contains the static information to be consumed by metadata:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema elementFormDefault="qualified"  
   xmlns:xs="http://www.w3.org/2001/XMLSchema"  
   targetNamespace="http://schemas.microsoft.com/ado/2006/04/edm/providermanifest"  
   xmlns:pm="http://schemas.microsoft.com/ado/2006/04/edm/providermanifest">  
  
  <xs:element name="ProviderManifest">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="Types" type="pm:TTypes" minOccurs="1" maxOccurs="1" />  
        <xs:element name="Functions" type="pm:TFunctions" minOccurs="0" maxOccurs="1"/>  
      </xs:sequence>  
      <xs:attribute name="Namespace" type="xs:string" use="required"/>  
    </xs:complexType>  
  </xs:element>  
  <xs:complexType name="TVersion">  
    <xs:attribute name="Major" type="xs:int" use="required" />  
    <xs:attribute name="Minor" type="xs:int" use="required" />  
    <xs:attribute name="Build" type="xs:int" use="required" />  
    <xs:attribute name="Revision" type="xs:int" use="required" />  
  </xs:complexType>  
  
  <xs:complexType name="TIntegerFacetDescription">  
    <xs:attribute name="Minimum" type="xs:int" use="optional" />  
    <xs:attribute name="Maximum" type="xs:int" use="optional" />  
    <xs:attribute name="DefaultValue" type="xs:int" use="optional" />  
    <xs:attribute name="Constant" type="xs:boolean" default="false" />  
  </xs:complexType>  
  
  <xs:complexType name="TBooleanFacetDescription">  
    <xs:attribute name="DefaultValue" type="xs:boolean" use="optional" />  
    <xs:attribute name="Constant" type="xs:boolean" default="true" />  
  </xs:complexType>  
  
  <xs:complexType name="TDateTimeFacetDescription">  
    <xs:attribute name="Constant" type="xs:boolean" default="false" />  
  </xs:complexType>  
  
  <xs:complexType name="TFacetDescriptions">  
    <xs:choice maxOccurs="unbounded">  
      <xs:element name="Precision" minOccurs="0" maxOccurs="1" type="pm:TIntegerFacetDescription"/>  
      <xs:element name="Scale" minOccurs="0" maxOccurs="1" type="pm:TIntegerFacetDescription"/>  
      <xs:element name="MaxLength" minOccurs="0" maxOccurs="1" type="pm:TIntegerFacetDescription"/>  
      <xs:element name="Unicode" minOccurs="0" maxOccurs="1" type="pm:TBooleanFacetDescription"/>  
      <xs:element name="FixedLength" minOccurs="0" maxOccurs="1" type="pm:TBooleanFacetDescription"/>  
    </xs:choice>  
  </xs:complexType>  
  
  <xs:complexType name="TType">  
    <xs:sequence>  
      <xs:element name="FacetDescriptions" type="pm:TFacetDescriptions" minOccurs="0" maxOccurs="1"/>  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="required"/>  
    <xs:attribute name="PrimitiveTypeKind" type="pm:TPrimitiveTypeKind" use="required" />  
  </xs:complexType>  
  
  <xs:complexType name="TTypes">  
    <xs:sequence>  
      <xs:element name="Type" type="pm:TType" minOccurs="0" maxOccurs="unbounded"/>  
    </xs:sequence>  
  </xs:complexType>  
  
  <xs:attributeGroup name="TFacetAttribute">  
    <xs:attribute name="Precision" type="xs:int" use="optional"/>  
    <xs:attribute name="Scale" type="xs:int" use="optional"/>  
    <xs:attribute name="MaxLength" type="xs:int" use="optional"/>  
    <xs:attribute name="Unicode" type="xs:boolean" use="optional"/>  
    <xs:attribute name="FixedLength" type="xs:boolean" use="optional"/>  
  </xs:attributeGroup>  
  
  <xs:complexType name="TFunctionParameter">  
    <xs:attribute name="Name" type="xs:string" use="required" />  
    <xs:attribute name="Type" type="xs:string" use="required" />  
    <xs:attributeGroup ref="pm:TFacetAttribute" />  
    <xs:attribute name="Mode" type="pm:TParameterDirection" use="required" />  
  </xs:complexType>  
  
  <xs:complexType name="TReturnType">  
    <xs:attribute name="Type" type="xs:string" use="required" />  
    <xs:attributeGroup ref="pm:TFacetAttribute" />  
  </xs:complexType>  
  
  <xs:complexType name="TFunction">  
    <xs:choice minOccurs="0" maxOccurs ="unbounded">  
      <xs:element name ="ReturnType" type="pm:TReturnType" minOccurs="0" maxOccurs="1" />  
      <xs:element name="Parameter" type="pm:TFunctionParameter" minOccurs="0" maxOccurs="unbounded"/>  
    </xs:choice>  
    <xs:attribute name="Name" type="xs:string" use="required" />  
    <xs:attribute name="Aggregate" type="xs:boolean" use="optional" />  
    <xs:attribute name="BuiltIn" type="xs:boolean" use="optional" />  
    <xs:attribute name="StoreFunctionName" type="xs:string" use="optional" />  
    <xs:attribute name="NiladicFunction" type="xs:boolean" use="optional" />  
    <xs:attribute name="ParameterTypeSemantics" type="pm:TParameterTypeSemantics" use="optional" default="AllowImplicitConversion" />  
  </xs:complexType>  
  
  <xs:complexType name="TFunctions">  
    <xs:sequence>  
      <xs:element name="Function" type="pm:TFunction" minOccurs="0" maxOccurs="unbounded"/>  
    </xs:sequence>  
  </xs:complexType>  
  
  <xs:simpleType name="TPrimitiveTypeKind">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Binary"/>  
      <xs:enumeration value="Boolean"/>  
      <xs:enumeration value="Byte"/>  
      <xs:enumeration value="Decimal"/>  
      <xs:enumeration value="DateTime"/>  
      <xs:enumeration value="Time"/>  
      <xs:enumeration value="DateTimeOffset"/>          
      <xs:enumeration value="Double"/>  
      <xs:enumeration value="Guid"/>  
      <xs:enumeration value="Single"/>  
      <xs:enumeration value="SByte"/>  
      <xs:enumeration value="Int16"/>  
      <xs:enumeration value="Int32"/>  
      <xs:enumeration value="Int64"/>  
      <xs:enumeration value="String"/>  
    </xs:restriction>  
  </xs:simpleType>  
  
  <xs:simpleType name="TParameterDirection">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="In"/>  
      <xs:enumeration value="Out"/>  
      <xs:enumeration value="InOut"/>  
    </xs:restriction>  
  </xs:simpleType>  
  
  <xs:simpleType name="TParameterTypeSemantics">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="ExactMatchOnly" />  
      <xs:enumeration value="AllowImplicitPromotion" />  
      <xs:enumeration value="AllowImplicitConversion" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
```  
  
#### <a name="types-node"></a><span data-ttu-id="7ed28-171">Türler düğümü</span><span class="sxs-lookup"><span data-stu-id="7ed28-171">Types Node</span></span>  
 <span data-ttu-id="7ed28-172">Sağlayıcı bildirimindeki türler düğümü, veri deposu tarafından veya sağlayıcı aracılığıyla yerel olarak desteklenen türler hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="7ed28-172">The Types node in the provider manifest contains information about the Types that are supported natively by the data store or through the provider.</span></span>  
  
##### <a name="type-node"></a><span data-ttu-id="7ed28-173">Tür düğümü</span><span class="sxs-lookup"><span data-stu-id="7ed28-173">Type Node</span></span>  
 <span data-ttu-id="7ed28-174">Her tür düğüm, EDM açısından bir sağlayıcı türü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7ed28-174">Each Type node defines a provider type in terms of EDM.</span></span> <span data-ttu-id="7ed28-175">Tür düğümü, sağlayıcı türünün adını ve eşlendiği model türüyle ilgili bilgileri ve bu tür eşlemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="7ed28-175">The Type node describes the name of the provider type, and information related to the model type it maps to and facets to describe that type mapping.</span></span>  
  
 <span data-ttu-id="7ed28-176">Bu tür bilgilerini sağlayıcı bildiriminde ifade etmek için her TypeInformation bildiriminin her bir tür için birkaç model açıklaması tanımlaması gerekir:</span><span class="sxs-lookup"><span data-stu-id="7ed28-176">In order to express this type information in the provider manifest, each TypeInformation declaration must define several facet descriptions for each Type:</span></span>  
  
|<span data-ttu-id="7ed28-177">Öznitelik adı</span><span class="sxs-lookup"><span data-stu-id="7ed28-177">Attribute Name</span></span>|<span data-ttu-id="7ed28-178">Veri Türü</span><span class="sxs-lookup"><span data-stu-id="7ed28-178">Data Type</span></span>|<span data-ttu-id="7ed28-179">Gerekli</span><span class="sxs-lookup"><span data-stu-id="7ed28-179">Required</span></span>|<span data-ttu-id="7ed28-180">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="7ed28-180">Default Value</span></span>|<span data-ttu-id="7ed28-181">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7ed28-181">Description</span></span>|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|<span data-ttu-id="7ed28-182">Ad</span><span class="sxs-lookup"><span data-stu-id="7ed28-182">Name</span></span>|<span data-ttu-id="7ed28-183">Dize</span><span class="sxs-lookup"><span data-stu-id="7ed28-183">String</span></span>|<span data-ttu-id="7ed28-184">Evet</span><span class="sxs-lookup"><span data-stu-id="7ed28-184">Yes</span></span>|<span data-ttu-id="7ed28-185">yok</span><span class="sxs-lookup"><span data-stu-id="7ed28-185">n/a</span></span>|<span data-ttu-id="7ed28-186">Sağlayıcıya özgü veri türü adı</span><span class="sxs-lookup"><span data-stu-id="7ed28-186">Provider-specific data type name</span></span>|  
|<span data-ttu-id="7ed28-187">PrimitiveTypeKind</span><span class="sxs-lookup"><span data-stu-id="7ed28-187">PrimitiveTypeKind</span></span>|<span data-ttu-id="7ed28-188">PrimitiveTypeKind</span><span class="sxs-lookup"><span data-stu-id="7ed28-188">PrimitiveTypeKind</span></span>|<span data-ttu-id="7ed28-189">Evet</span><span class="sxs-lookup"><span data-stu-id="7ed28-189">Yes</span></span>|<span data-ttu-id="7ed28-190">yok</span><span class="sxs-lookup"><span data-stu-id="7ed28-190">n/a</span></span>|<span data-ttu-id="7ed28-191">EDM türü adı</span><span class="sxs-lookup"><span data-stu-id="7ed28-191">EDM type name</span></span>|  
  
###### <a name="function-node"></a><span data-ttu-id="7ed28-192">İşlev düğümü</span><span class="sxs-lookup"><span data-stu-id="7ed28-192">Function Node</span></span>  
 <span data-ttu-id="7ed28-193">Her Işlev, sağlayıcı aracılığıyla kullanılabilen tek bir işlevi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7ed28-193">Each Function defines a single function available through the provider.</span></span>  
  
|<span data-ttu-id="7ed28-194">Öznitelik adı</span><span class="sxs-lookup"><span data-stu-id="7ed28-194">Attribute Name</span></span>|<span data-ttu-id="7ed28-195">Veri Türü</span><span class="sxs-lookup"><span data-stu-id="7ed28-195">Data Type</span></span>|<span data-ttu-id="7ed28-196">Gerekli</span><span class="sxs-lookup"><span data-stu-id="7ed28-196">Required</span></span>|<span data-ttu-id="7ed28-197">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="7ed28-197">Default Value</span></span>|<span data-ttu-id="7ed28-198">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7ed28-198">Description</span></span>|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|<span data-ttu-id="7ed28-199">Ad</span><span class="sxs-lookup"><span data-stu-id="7ed28-199">Name</span></span>|<span data-ttu-id="7ed28-200">Dize</span><span class="sxs-lookup"><span data-stu-id="7ed28-200">String</span></span>|<span data-ttu-id="7ed28-201">Evet</span><span class="sxs-lookup"><span data-stu-id="7ed28-201">Yes</span></span>|<span data-ttu-id="7ed28-202">yok</span><span class="sxs-lookup"><span data-stu-id="7ed28-202">n/a</span></span>|<span data-ttu-id="7ed28-203">İşlevin tanımlayıcısı/adı</span><span class="sxs-lookup"><span data-stu-id="7ed28-203">Identifier/name of the function</span></span>|  
|<span data-ttu-id="7ed28-204">'Indaki</span><span class="sxs-lookup"><span data-stu-id="7ed28-204">ReturnType</span></span>|<span data-ttu-id="7ed28-205">Dize</span><span class="sxs-lookup"><span data-stu-id="7ed28-205">String</span></span>|<span data-ttu-id="7ed28-206">Hayır</span><span class="sxs-lookup"><span data-stu-id="7ed28-206">No</span></span>|<span data-ttu-id="7ed28-207">Kağıt</span><span class="sxs-lookup"><span data-stu-id="7ed28-207">Void</span></span>|<span data-ttu-id="7ed28-208">İşlevin EDM dönüş türü</span><span class="sxs-lookup"><span data-stu-id="7ed28-208">The EDM return type of the function</span></span>|  
|<span data-ttu-id="7ed28-209">Toplama</span><span class="sxs-lookup"><span data-stu-id="7ed28-209">Aggregate</span></span>|<span data-ttu-id="7ed28-210">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="7ed28-210">Boolean</span></span>|<span data-ttu-id="7ed28-211">Hayır</span><span class="sxs-lookup"><span data-stu-id="7ed28-211">No</span></span>|<span data-ttu-id="7ed28-212">False</span><span class="sxs-lookup"><span data-stu-id="7ed28-212">False</span></span>|<span data-ttu-id="7ed28-213">İşlev bir toplama işlevse doğru</span><span class="sxs-lookup"><span data-stu-id="7ed28-213">True if the function is an aggregate function</span></span>|  
|<span data-ttu-id="7ed28-214">Yerleik</span><span class="sxs-lookup"><span data-stu-id="7ed28-214">BuiltIn</span></span>|<span data-ttu-id="7ed28-215">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="7ed28-215">Boolean</span></span>|<span data-ttu-id="7ed28-216">Hayır</span><span class="sxs-lookup"><span data-stu-id="7ed28-216">No</span></span>|<span data-ttu-id="7ed28-217">Doğru</span><span class="sxs-lookup"><span data-stu-id="7ed28-217">True</span></span>|<span data-ttu-id="7ed28-218">İşlev veri deposunda yerleşik ise doğru</span><span class="sxs-lookup"><span data-stu-id="7ed28-218">True if the function is built into the data store</span></span>|  
|<span data-ttu-id="7ed28-219">StoreFunctionName</span><span class="sxs-lookup"><span data-stu-id="7ed28-219">StoreFunctionName</span></span>|<span data-ttu-id="7ed28-220">Dize</span><span class="sxs-lookup"><span data-stu-id="7ed28-220">String</span></span>|<span data-ttu-id="7ed28-221">Hayır</span><span class="sxs-lookup"><span data-stu-id="7ed28-221">No</span></span>|<span data-ttu-id="7ed28-222">\<Ad ></span><span class="sxs-lookup"><span data-stu-id="7ed28-222">\<Name></span></span>|<span data-ttu-id="7ed28-223">Veri deposundaki işlev adı.</span><span class="sxs-lookup"><span data-stu-id="7ed28-223">Function Name in the data store.</span></span>  <span data-ttu-id="7ed28-224">İşlev adlarının yeniden yönlendirme düzeyine izin verir.</span><span class="sxs-lookup"><span data-stu-id="7ed28-224">Allows for a level of redirection of function names.</span></span>|  
|<span data-ttu-id="7ed28-225">NiladicFunction</span><span class="sxs-lookup"><span data-stu-id="7ed28-225">NiladicFunction</span></span>|<span data-ttu-id="7ed28-226">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="7ed28-226">Boolean</span></span>|<span data-ttu-id="7ed28-227">Hayır</span><span class="sxs-lookup"><span data-stu-id="7ed28-227">No</span></span>|<span data-ttu-id="7ed28-228">False</span><span class="sxs-lookup"><span data-stu-id="7ed28-228">False</span></span>|<span data-ttu-id="7ed28-229">İşlev parametre gerektirmiyorsa ve parametre olmadan çağrılırsa doğru</span><span class="sxs-lookup"><span data-stu-id="7ed28-229">True if the function does not require parameters and is called without any parameters</span></span>|  
|<span data-ttu-id="7ed28-230">ParameterType</span><span class="sxs-lookup"><span data-stu-id="7ed28-230">ParameterType</span></span><br /><br /> <span data-ttu-id="7ed28-231">İçeriyor</span><span class="sxs-lookup"><span data-stu-id="7ed28-231">Semantics</span></span>|<span data-ttu-id="7ed28-232">Parametersemantik</span><span class="sxs-lookup"><span data-stu-id="7ed28-232">ParameterSemantics</span></span>|<span data-ttu-id="7ed28-233">Hayır</span><span class="sxs-lookup"><span data-stu-id="7ed28-233">No</span></span>|<span data-ttu-id="7ed28-234">Allowwimplicit</span><span class="sxs-lookup"><span data-stu-id="7ed28-234">AllowImplicit</span></span><br /><br /> <span data-ttu-id="7ed28-235">Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="7ed28-235">Conversion</span></span>|<span data-ttu-id="7ed28-236">Sorgu işlem hattının parametre türü değiştirme ile nasıl ele alınacağını seçme:</span><span class="sxs-lookup"><span data-stu-id="7ed28-236">Choice of how the query pipeline should deal with parameter type substitution:</span></span><br /><br /> <span data-ttu-id="7ed28-237">- ExactMatchOnly</span><span class="sxs-lookup"><span data-stu-id="7ed28-237">-   ExactMatchOnly</span></span><br /><span data-ttu-id="7ed28-238">-Allowimplicitpromosyonu</span><span class="sxs-lookup"><span data-stu-id="7ed28-238">-   AllowImplicitPromotion</span></span><br /><span data-ttu-id="7ed28-239">-AllowImplicitConversion</span><span class="sxs-lookup"><span data-stu-id="7ed28-239">-   AllowImplicitConversion</span></span>|  
  
 <span data-ttu-id="7ed28-240">**Parameters düğümü**</span><span class="sxs-lookup"><span data-stu-id="7ed28-240">**Parameters Node**</span></span>  
  
 <span data-ttu-id="7ed28-241">Her işlevde bir veya daha fazla parametre düğümü koleksiyonu vardır.</span><span class="sxs-lookup"><span data-stu-id="7ed28-241">Each function has a collection of one or more Parameter nodes.</span></span>  
  
|<span data-ttu-id="7ed28-242">Öznitelik adı</span><span class="sxs-lookup"><span data-stu-id="7ed28-242">Attribute Name</span></span>|<span data-ttu-id="7ed28-243">Veri Türü</span><span class="sxs-lookup"><span data-stu-id="7ed28-243">Data Type</span></span>|<span data-ttu-id="7ed28-244">Gerekli</span><span class="sxs-lookup"><span data-stu-id="7ed28-244">Required</span></span>|<span data-ttu-id="7ed28-245">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="7ed28-245">Default Value</span></span>|<span data-ttu-id="7ed28-246">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7ed28-246">Description</span></span>|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|<span data-ttu-id="7ed28-247">Ad</span><span class="sxs-lookup"><span data-stu-id="7ed28-247">Name</span></span>|<span data-ttu-id="7ed28-248">Dize</span><span class="sxs-lookup"><span data-stu-id="7ed28-248">String</span></span>|<span data-ttu-id="7ed28-249">Evet</span><span class="sxs-lookup"><span data-stu-id="7ed28-249">Yes</span></span>|<span data-ttu-id="7ed28-250">yok</span><span class="sxs-lookup"><span data-stu-id="7ed28-250">n/a</span></span>|<span data-ttu-id="7ed28-251">Parametrenin tanımlayıcı/adı.</span><span class="sxs-lookup"><span data-stu-id="7ed28-251">Identifier/name of the parameter.</span></span>|  
|<span data-ttu-id="7ed28-252">Tür</span><span class="sxs-lookup"><span data-stu-id="7ed28-252">Type</span></span>|<span data-ttu-id="7ed28-253">Dize</span><span class="sxs-lookup"><span data-stu-id="7ed28-253">String</span></span>|<span data-ttu-id="7ed28-254">Evet</span><span class="sxs-lookup"><span data-stu-id="7ed28-254">Yes</span></span>|<span data-ttu-id="7ed28-255">yok</span><span class="sxs-lookup"><span data-stu-id="7ed28-255">n/a</span></span>|<span data-ttu-id="7ed28-256">Parametrenin EDM türü.</span><span class="sxs-lookup"><span data-stu-id="7ed28-256">The EDM type of the parameter.</span></span>|  
|<span data-ttu-id="7ed28-257">Mod</span><span class="sxs-lookup"><span data-stu-id="7ed28-257">Mode</span></span>|<span data-ttu-id="7ed28-258">Parametre</span><span class="sxs-lookup"><span data-stu-id="7ed28-258">Parameter</span></span><br /><br /> <span data-ttu-id="7ed28-259">Yön</span><span class="sxs-lookup"><span data-stu-id="7ed28-259">Direction</span></span>|<span data-ttu-id="7ed28-260">Evet</span><span class="sxs-lookup"><span data-stu-id="7ed28-260">Yes</span></span>|<span data-ttu-id="7ed28-261">yok</span><span class="sxs-lookup"><span data-stu-id="7ed28-261">n/a</span></span>|<span data-ttu-id="7ed28-262">Parametrenin yönü:</span><span class="sxs-lookup"><span data-stu-id="7ed28-262">Direction of parameter:</span></span><br /><br /> <span data-ttu-id="7ed28-263">-ın</span><span class="sxs-lookup"><span data-stu-id="7ed28-263">-   in</span></span><br /><span data-ttu-id="7ed28-264">-Out</span><span class="sxs-lookup"><span data-stu-id="7ed28-264">-   out</span></span><br /><span data-ttu-id="7ed28-265">-InOut</span><span class="sxs-lookup"><span data-stu-id="7ed28-265">-   inout</span></span>|  
  
##### <a name="namespace-attribute"></a><span data-ttu-id="7ed28-266">Namespace özniteliği</span><span class="sxs-lookup"><span data-stu-id="7ed28-266">Namespace Attribute</span></span>  
 <span data-ttu-id="7ed28-267">Her veri deposu sağlayıcısı, bildirimde tanımlanan bilgiler için bir ad alanı veya ad alanı grubu tanımlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="7ed28-267">Each data store provider must define a namespace or group of namespaces for information defined in the manifest.</span></span> <span data-ttu-id="7ed28-268">Bu ad alanı, işlev ve tür adlarını çözümlemek için Entity SQL sorgularında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7ed28-268">This namespace can be used in Entity SQL queries to resolve names of functions and types.</span></span> <span data-ttu-id="7ed28-269">Örneğin: SqlServer.</span><span class="sxs-lookup"><span data-stu-id="7ed28-269">For instance: SqlServer.</span></span> <span data-ttu-id="7ed28-270">Bu ad alanı, Entity SQL sorguları tarafından desteklenecek standart işlevler için varlık Hizmetleri tarafından tanımlanan EDM ad alanından farklı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7ed28-270">That namespace must be different from the canonical namespace, EDM, defined by Entity Services for standard functions to be supported by Entity SQL queries.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ed28-271">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ed28-271">See also</span></span>

- [<span data-ttu-id="7ed28-272">Entity Framework Veri Sağlayıcısı Yazma</span><span class="sxs-lookup"><span data-stu-id="7ed28-272">Writing an Entity Framework Data Provider</span></span>](writing-an-ef-data-provider.md)
