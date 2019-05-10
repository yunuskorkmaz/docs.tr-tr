---
title: Sağlayıcı Bildirimi Belirtimi
ms.date: 03/30/2017
ms.assetid: bb450b47-8951-4f99-9350-26f05a4d4e46
ms.openlocfilehash: 0f3eaa73a26c3f8519e1c168ab2e2968ed4ab28d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64641161"
---
# <a name="provider-manifest-specification"></a><span data-ttu-id="f5d02-102">Sağlayıcı Bildirimi Belirtimi</span><span class="sxs-lookup"><span data-stu-id="f5d02-102">Provider Manifest Specification</span></span>
<span data-ttu-id="f5d02-103">Bu bölümde, nasıl bir veri deposu sağlayıcısı türleri ve işlevleri veri deposunda destekleyebileceğini açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f5d02-103">This section discusses how a data store provider can support the types and functions in the data store.</span></span>  
  
 <span data-ttu-id="f5d02-104">Varlık Hizmetleri belirli veri depolama sağlayıcısının bağımsız olarak çalışır ancak hala modelleri, eşlemeler ve sorguları bir temel alınan veri deposuyla nasıl etkileşim açıkça tanımlamak bir veri sağlayıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5d02-104">Entity Services operates independently of a specific data store provider yet still allows a data provider to explicitly define how models, mappings, and queries interact with an underlying data store.</span></span> <span data-ttu-id="f5d02-105">Bir Soyutlama Katmanı varlık Hizmetleri yalnızca belirli bir veri deposu ya da veri sağlayıcısı hedeflenecek.</span><span class="sxs-lookup"><span data-stu-id="f5d02-105">Without a layer of abstraction, Entity Services could only be targeted at a specific data store or data provider.</span></span>  
  
 <span data-ttu-id="f5d02-106">Sağlayıcının desteklediği türleri, doğrudan veya dolaylı olarak temel alınan veritabanı tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f5d02-106">Types that the provider supports are directly or indirectly supported by the underlying database.</span></span> <span data-ttu-id="f5d02-107">Bu tür mutlaka tam deposu türlerini ancak sağlayıcısı kullanan desteklemek için türleri olmayan [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f5d02-107">These types are not necessarily the exact store types, but the types the provider uses to support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="f5d02-108">Varlık veri modeli (EDM) koşullarını sağlayıcısı depolama türleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f5d02-108">Provider/store types are described in the Entity Data Model (EDM) terms.</span></span>  
  
 <span data-ttu-id="f5d02-109">Veri deposu tarafından desteklenen işlevler için parametre ve dönüş türleri'EDM koşullarını belirtilir.</span><span class="sxs-lookup"><span data-stu-id="f5d02-109">Parameter and return types for the functions supported by the data store are specified in EDM terms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5d02-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f5d02-110">Requirements</span></span>  
 <span data-ttu-id="f5d02-111">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Ve bilinen türler kesilmesi veya veri kaybı olmadan sürekli içinde veri geçirebilmek için gereken veri deposu.</span><span class="sxs-lookup"><span data-stu-id="f5d02-111">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] and the data store need to be able to pass data back and forth in known types without any data loss or truncation.</span></span>  
  
 <span data-ttu-id="f5d02-112">Sağlayıcı bildirimi tasarım zamanında veri deposuna bağlantı açmak zorunda kalmadan araçlar tarafından yüklenebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f5d02-112">The provider manifest must be loadable by tools at design time without having to open a connection to the data store.</span></span>  
  
 <span data-ttu-id="f5d02-113">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Çalışması büyük/küçük harfe duyarlıdır, ancak temel alınan veri deposu çalışmıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="f5d02-113">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] is case sensitive, but the underlying data store may not be.</span></span> <span data-ttu-id="f5d02-114">Zaman EDM yapıtları (tanımlayıcıları ve örneğin tür adları) tanımlandığını ve kullanıldığını bildiriminde kullandıkları gerekir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] büyük küçük harf duyarlılığı.</span><span class="sxs-lookup"><span data-stu-id="f5d02-114">When EDM artifacts (identifiers and type names, for example) are defined and used in the manifest, they must use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] case sensitivity.</span></span> <span data-ttu-id="f5d02-115">Büyük küçük harfe duyarlı veri deposu öğeleri sağlayıcı bildiriminde görünüyorsa, bu büyük/küçük harf sağlayıcı bildiriminde tutulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f5d02-115">If data store elements that may be case sensitive appear in the provider manifest, that casing needs to be maintained in the provider manifest.</span></span>  
  
 <span data-ttu-id="f5d02-116">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Tüm veri sağlayıcıları için bir sağlayıcı bildirimi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f5d02-116">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] requires a provider manifest for all data providers.</span></span> <span data-ttu-id="f5d02-117">Bir sağlayıcı yok. bir sağlayıcı kullanmayı denerseniz ile bildirim [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], bir hata alırsınız.</span><span class="sxs-lookup"><span data-stu-id="f5d02-117">If you try to use a provider that does not have a provider manifest with the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], you will get an error.</span></span>  
  
 <span data-ttu-id="f5d02-118">Aşağıdaki tabloda tür özel durumlar açıklanmaktadır [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] sağlayıcı etkileşimi özel durumlar ortaya çıktığında throw:</span><span class="sxs-lookup"><span data-stu-id="f5d02-118">The following table describes the kinds of exceptions the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] would throw when exceptions arise through provider interaction:</span></span>  
  
|<span data-ttu-id="f5d02-119">Sorun</span><span class="sxs-lookup"><span data-stu-id="f5d02-119">Issue</span></span>|<span data-ttu-id="f5d02-120">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="f5d02-120">Exception</span></span>|  
|-----------|---------------|  
|<span data-ttu-id="f5d02-121">Sağlayıcı GetProviderManifest DbProviderServices içinde desteklemez.</span><span class="sxs-lookup"><span data-stu-id="f5d02-121">The Provider does not support GetProviderManifest in DbProviderServices.</span></span>|<span data-ttu-id="f5d02-122">ProviderIncompatibleException</span><span class="sxs-lookup"><span data-stu-id="f5d02-122">ProviderIncompatibleException</span></span>|  
|<span data-ttu-id="f5d02-123">Sağlayıcı bildirimi eksik: sağlayıcının döndürdüğü `null` sağlayıcı bildirimi alınmaya çalışılırken.</span><span class="sxs-lookup"><span data-stu-id="f5d02-123">Missing provider manifest: the provider returns `null` when attempting to retrieve the provider manifest.</span></span>|<span data-ttu-id="f5d02-124">ProviderIncompatibleException</span><span class="sxs-lookup"><span data-stu-id="f5d02-124">ProviderIncompatibleException</span></span>|  
|<span data-ttu-id="f5d02-125">Geçersiz sağlayıcı bildirimi: sağlayıcı geçersiz XML sağlayıcı bildirimi alınmaya çalışılırken döndürür.</span><span class="sxs-lookup"><span data-stu-id="f5d02-125">Invalid provider manifest: the provider returns invalid XML when attempting to retrieve the provider manifest.</span></span>|<span data-ttu-id="f5d02-126">ProviderIncompatibleException</span><span class="sxs-lookup"><span data-stu-id="f5d02-126">ProviderIncompatibleException</span></span>|  
  
## <a name="scenarios"></a><span data-ttu-id="f5d02-127">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="f5d02-127">Scenarios</span></span>  
 <span data-ttu-id="f5d02-128">Bir sağlayıcı, aşağıdaki senaryolarda desteklemesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="f5d02-128">A provider should support the following scenarios:</span></span>  
  
### <a name="writing-a-provider-with-symmetric-type-mapping"></a><span data-ttu-id="f5d02-129">Simetrik tür eşlemesine sahip bir sağlayıcı yazma</span><span class="sxs-lookup"><span data-stu-id="f5d02-129">Writing a Provider with Symmetric Type Mapping</span></span>  
 <span data-ttu-id="f5d02-130">Sağlayıcı için yazabileceğiniz [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] eşleme yönü bağımsız olarak tek bir EDM türü her depo türü burada eşleştirir.</span><span class="sxs-lookup"><span data-stu-id="f5d02-130">You can write a provider for the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] where each store type maps to a single EDM type, regardless of the mapping direction.</span></span> <span data-ttu-id="f5d02-131">Karşılık gelen çok basit eşlemesi bir EDM türü için bir sağlayıcı türü, tür sisteminde basit olduğu için veya EDM türleri eşleşen simetrik bir çözüm kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5d02-131">For a provider type that has very simple mapping that corresponds with an EDM type, you can use a symmetric solution because the type system is simple or matches EDM types.</span></span>  
  
 <span data-ttu-id="f5d02-132">Kendi etki alanı basitliği ve bir statik bildirim temelli sağlayıcı bildirimi üreten kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5d02-132">You can use the simplicity of their domain and produce a static declarative provider manifest.</span></span>  
  
 <span data-ttu-id="f5d02-133">İki bölüme sahip bir XML dosyası yazma:</span><span class="sxs-lookup"><span data-stu-id="f5d02-133">You write an XML file that has two sections:</span></span>  
  
- <span data-ttu-id="f5d02-134">"EDM karşılığı" deposu tür veya işlev açısından ifade sağlayıcısı türlerinin listesi.</span><span class="sxs-lookup"><span data-stu-id="f5d02-134">A list of provider types expressed in terms of the "EDM counterpart" of a store type or function.</span></span> <span data-ttu-id="f5d02-135">Store türlerin karşılığı EDM türleri vardır.</span><span class="sxs-lookup"><span data-stu-id="f5d02-135">Store types have counterpart EDM types.</span></span> <span data-ttu-id="f5d02-136">Store işlevlerin karşılık gelen EDM işlevleri vardır.</span><span class="sxs-lookup"><span data-stu-id="f5d02-136">Store functions have corresponding EDM functions.</span></span> <span data-ttu-id="f5d02-137">Örneğin, bir SQL Server türü varchar, ancak karşılık gelen EDM türü dize.</span><span class="sxs-lookup"><span data-stu-id="f5d02-137">For example, varchar is a SQL Server type but the corresponding EDM type is string.</span></span>  
  
- <span data-ttu-id="f5d02-138">Burada parametre ve dönüş türleri'EDM koşullarını ifade edilir sağlayıcısı tarafından desteklenen işlevlerin listesi.</span><span class="sxs-lookup"><span data-stu-id="f5d02-138">A list of functions supported by the provider where parameter and return types are expressed in EDM terms.</span></span>  
  
### <a name="writing-a-provider-with-asymmetric-type-mapping"></a><span data-ttu-id="f5d02-139">Asimetrik tür eşlemesine sahip bir sağlayıcı yazma</span><span class="sxs-lookup"><span data-stu-id="f5d02-139">Writing a Provider with Asymmetric Type Mapping</span></span>  
 <span data-ttu-id="f5d02-140">Ne zaman, bir veri deposu sağlayıcısı için yazma [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], bazı türleri sağlayıcısı EDM türü eşlemesinden farklı için eşleme sağlayıcısı için EDM türü.</span><span class="sxs-lookup"><span data-stu-id="f5d02-140">When writing a data store provider for the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], the EDM-to-provider type mapping for some types may be different from provider-to-EDM type mapping.</span></span> <span data-ttu-id="f5d02-141">Örneğin, nvarchar(4000) için EDM PrimitiveTypeKind.String(MaxLength=4000) eşleştirir. sırasında nvarchar(4000) sağlayıcısı için sınırsız EDM PrimitiveTypeKind.String eşlenebilir.</span><span class="sxs-lookup"><span data-stu-id="f5d02-141">For instance, unbounded EDM PrimitiveTypeKind.String may map to nvarchar(4000) on the provider, while nvarchar(4000) maps to the EDM PrimitiveTypeKind.String(MaxLength=4000).</span></span>  
  
 <span data-ttu-id="f5d02-142">İki bölüme sahip bir XML dosyası yazma:</span><span class="sxs-lookup"><span data-stu-id="f5d02-142">You write an XML file that has two sections:</span></span>  
  
- <span data-ttu-id="f5d02-143">Sağlayıcı türlerinin bir listesini EDM terimleriyle ifade edilen ve her iki yön için eşleme tanımlayın: EDM sağlayıcısı ve sağlayıcı EDM.</span><span class="sxs-lookup"><span data-stu-id="f5d02-143">A list of provider types expressed in EDM terms and define mapping for both direction: EDM-to-provider and provider-to-EDM.</span></span>  
  
- <span data-ttu-id="f5d02-144">Burada parametre ve dönüş türleri'EDM koşullarını ifade edilir sağlayıcısı tarafından desteklenen işlevlerin listesi.</span><span class="sxs-lookup"><span data-stu-id="f5d02-144">A list of functions supported by the provider where parameter and return types are expressed in EDM terms.</span></span>  
  
## <a name="provider-manifest-discoverability"></a><span data-ttu-id="f5d02-145">Sağlayıcı bildirimi bulunabilirlik</span><span class="sxs-lookup"><span data-stu-id="f5d02-145">Provider Manifest Discoverability</span></span>  
 <span data-ttu-id="f5d02-146">Bildirim dolaylı olarak varlık Hizmetleri (örneğin, araçları veya sorgu) birçok bileşen türleri tarafından kullanılır ancak daha fazla veri kullanımı meta verileri tarafından doğrudan kullanılabilir meta veri yükleyici depolayın.</span><span class="sxs-lookup"><span data-stu-id="f5d02-146">The manifest is used indirectly by several component types in Entity Services (for example Tools or Query) but more directly leveraged by metadata through the use of the data store metadata loader.</span></span>  
  
 <span data-ttu-id="f5d02-147">![dfb3d02b&#45;7a8c&#45;4d 51&#45;ac5a&#45;a73d8aa145e6](../../../../../docs/framework/data/adonet/ef/media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6")</span><span class="sxs-lookup"><span data-stu-id="f5d02-147">![dfb3d02b&#45;7a8c&#45;4d51&#45;ac5a&#45;a73d8aa145e6](../../../../../docs/framework/data/adonet/ef/media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6")</span></span>  
  
 <span data-ttu-id="f5d02-148">Ancak, belirli bir sağlayıcı farklı mağazalarda veya aynı deponun'ün farklı sürümlerini desteklemiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="f5d02-148">However, a given provider may support different stores or different versions of the same store.</span></span> <span data-ttu-id="f5d02-149">Bu nedenle, bir sağlayıcı her desteklenen veri deposu için farklı bir bildirim bildirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f5d02-149">Therefore, a provider must report a different manifest for each supported data store.</span></span>  
  
### <a name="provider-manifest-token"></a><span data-ttu-id="f5d02-150">Sağlayıcı bildirimi belirteci</span><span class="sxs-lookup"><span data-stu-id="f5d02-150">Provider Manifest Token</span></span>  
 <span data-ttu-id="f5d02-151">Bir veri deposu bağlantısı açıldığında, sağlayıcı doğru bildirimi döndürmek bilgi için sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5d02-151">When a data store connection is opened, the provider can query for information to return the right manifest.</span></span> <span data-ttu-id="f5d02-152">Bu bağlantı bilgileri kullanılabildiği değil veya ne zaman mağazaya bağlanmanıza mümkün değildir çevrimdışı senaryolarda mümkün olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="f5d02-152">This may not be possible in offline scenarios where connection information is not available or when it is not possible to connect to the store.</span></span> <span data-ttu-id="f5d02-153">Bildirim kullanarak tanımlamak `ProviderManifestToken` özniteliği `Schema` .ssdl dosyasındaki öğesi.</span><span class="sxs-lookup"><span data-stu-id="f5d02-153">Identify the manifest by using the `ProviderManifestToken` attribute of the `Schema` element in the .ssdl file.</span></span> <span data-ttu-id="f5d02-154">Bu öznitelik için gerekli bir biçim vardır; Sağlayıcı bir bildirim mağazaya bir bağlantı açmaya gerek kalmadan tanımlamak için gereken en düşük bilgi seçer.</span><span class="sxs-lookup"><span data-stu-id="f5d02-154">There is no required format for this attribute; the provider chooses the minimum information needed to identify a manifest without opening a connection to the store.</span></span>  
  
 <span data-ttu-id="f5d02-155">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="f5d02-155">For example:</span></span>  
  
```xml  
<Schema Namespace="Northwind" Provider="System.Data.SqlClient" ProviderManifestToken="2005" xmlns:edm="http://schemas.microsoft.com/ado/2006/04/edm/ssdl" xmlns="http://schemas.microsoft.com/ado/2006/04/edm/ssdl">  
```  
  
## <a name="provider-manifest-programming-model"></a><span data-ttu-id="f5d02-156">Sağlayıcı bildirimi programlama modeli</span><span class="sxs-lookup"><span data-stu-id="f5d02-156">Provider Manifest Programming Model</span></span>  
 <span data-ttu-id="f5d02-157">Sağlayıcıları türetilen <xref:System.Data.Common.DbXmlEnabledProviderManifest>, bunları kendi bildirimleri bildirimli olarak belirtmek sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5d02-157">Providers derive from <xref:System.Data.Common.DbXmlEnabledProviderManifest>, which allows them to specify their manifests declaratively.</span></span> <span data-ttu-id="f5d02-158">Aşağıdaki çizimde bir sağlayıcı sınıf hiyerarşisini gösterir:</span><span class="sxs-lookup"><span data-stu-id="f5d02-158">The following illustration shows the class hierarchy of a provider:</span></span>  
  
 <span data-ttu-id="f5d02-159">![Hiçbiri](../../../../../docs/framework/data/adonet/ef/media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")</span><span class="sxs-lookup"><span data-stu-id="f5d02-159">![None](../../../../../docs/framework/data/adonet/ef/media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")</span></span>  
  
### <a name="discoverability-api"></a><span data-ttu-id="f5d02-160">API keşfedilebilirliğini</span><span class="sxs-lookup"><span data-stu-id="f5d02-160">Discoverability API</span></span>  
 <span data-ttu-id="f5d02-161">Sağlayıcı bildirimi (storeıtemcollection'ın) meta verileri Store yükleyicisi tarafından yüklenen, veri kullanılarak bağlantı veya sağlayıcı bildirimi belirteci depolama.</span><span class="sxs-lookup"><span data-stu-id="f5d02-161">The provider manifest is loaded by the Store Metadata loader (StoreItemCollection), either by using a data store connection or a provider manifest token.</span></span>  
  
#### <a name="using-a-data-store-connection"></a><span data-ttu-id="f5d02-162">Data Store bağlantı kullanma</span><span class="sxs-lookup"><span data-stu-id="f5d02-162">Using a Data Store Connection</span></span>  
 <span data-ttu-id="f5d02-163">Verileri depolamak bağlantısı kullanılabilir, DbProvderServices.GetProviderManifestToken DbProviderManifest döndüren GetProviderManifest yöntemine geçirilen bir belirteç döndürecek şekilde çağırın.</span><span class="sxs-lookup"><span data-stu-id="f5d02-163">When the data store connection is available, call DbProvderServices.GetProviderManifestToken to return the token that is passed to the GetProviderManifest method, which returns DbProviderManifest.</span></span> <span data-ttu-id="f5d02-164">Bu yöntem, sağlayıcının uygulanmasına GetDbProviderManifestToken atar.</span><span class="sxs-lookup"><span data-stu-id="f5d02-164">This method delegates to the provider's implementation of GetDbProviderManifestToken.</span></span>  
  
```  
public string GetProviderManifestToken(DbConnection connection);  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
#### <a name="using-a-provider-manifest-token"></a><span data-ttu-id="f5d02-165">Sağlayıcı bildirimi belirteciyle</span><span class="sxs-lookup"><span data-stu-id="f5d02-165">Using a Provider Manifest Token</span></span>  
 <span data-ttu-id="f5d02-166">Çevrimdışı senaryosu, belirteç SSDL temsilinden çekilir.</span><span class="sxs-lookup"><span data-stu-id="f5d02-166">For the offline scenario, the token is picked from SSDL representation.</span></span> <span data-ttu-id="f5d02-167">SSDL bir ProviderManifestToken belirtmenizi sağlar (bkz [şema öğesi (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl) daha fazla bilgi için).</span><span class="sxs-lookup"><span data-stu-id="f5d02-167">The SSDL allows you to specify a ProviderManifestToken (see [Schema Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl) for more information).</span></span> <span data-ttu-id="f5d02-168">Örneğin, bir bağlantı açılamıyor, SSDL bildirimi hakkında bilgi belirten sağlayıcısı bildirimi belirtece sahip.</span><span class="sxs-lookup"><span data-stu-id="f5d02-168">For example, if a connection cannot be opened, the SSDL has a provider manifest token that specifies information about the manifest.</span></span>  
  
```  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
### <a name="provider-manifest-schema"></a><span data-ttu-id="f5d02-169">Sağlayıcı bildirim şeması</span><span class="sxs-lookup"><span data-stu-id="f5d02-169">Provider Manifest Schema</span></span>  
 <span data-ttu-id="f5d02-170">Her hizmet sağlayıcısı için tanımlanan bilgileri şemasını meta veriler tarafından tüketilen statik bilgilerini içerir:</span><span class="sxs-lookup"><span data-stu-id="f5d02-170">The schema of information defined for each provider contains the static information to be consumed by metadata:</span></span>  
  
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
  
#### <a name="types-node"></a><span data-ttu-id="f5d02-171">Düğüm türleri</span><span class="sxs-lookup"><span data-stu-id="f5d02-171">Types Node</span></span>  
 <span data-ttu-id="f5d02-172">Sağlayıcı bildirimi türleri düğümünde veri deposu tarafından veya sağlayıcısı aracılığıyla yerel olarak desteklenen türleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="f5d02-172">The Types node in the provider manifest contains information about the Types that are supported natively by the data store or through the provider.</span></span>  
  
##### <a name="type-node"></a><span data-ttu-id="f5d02-173">Düğüm türü</span><span class="sxs-lookup"><span data-stu-id="f5d02-173">Type Node</span></span>  
 <span data-ttu-id="f5d02-174">Her tür düğümünün EDM açısından sağlayıcı türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f5d02-174">Each Type node defines a provider type in terms of EDM.</span></span> <span data-ttu-id="f5d02-175">Türü düğüm adı sağlayıcı türü ve bu tür eşlemesi açıklamak için eşlendiği model türünü ve modelleri için ilgili bilgiler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f5d02-175">The Type node describes the name of the provider type, and information related to the model type it maps to and facets to describe that type mapping.</span></span>  
  
 <span data-ttu-id="f5d02-176">Bu tür bilgisi sağlayıcı bildirimi express için her TypeInformation bildirimi her türü için birden fazla model açıklamaları tanımlamanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="f5d02-176">In order to express this type information in the provider manifest, each TypeInformation declaration must define several facet descriptions for each Type:</span></span>  
  
|<span data-ttu-id="f5d02-177">Öznitelik adı</span><span class="sxs-lookup"><span data-stu-id="f5d02-177">Attribute Name</span></span>|<span data-ttu-id="f5d02-178">Veri Türü</span><span class="sxs-lookup"><span data-stu-id="f5d02-178">Data Type</span></span>|<span data-ttu-id="f5d02-179">Gerekli</span><span class="sxs-lookup"><span data-stu-id="f5d02-179">Required</span></span>|<span data-ttu-id="f5d02-180">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="f5d02-180">Default Value</span></span>|<span data-ttu-id="f5d02-181">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f5d02-181">Description</span></span>|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|<span data-ttu-id="f5d02-182">Ad</span><span class="sxs-lookup"><span data-stu-id="f5d02-182">Name</span></span>|<span data-ttu-id="f5d02-183">Dize</span><span class="sxs-lookup"><span data-stu-id="f5d02-183">String</span></span>|<span data-ttu-id="f5d02-184">Evet</span><span class="sxs-lookup"><span data-stu-id="f5d02-184">Yes</span></span>|<span data-ttu-id="f5d02-185">yok</span><span class="sxs-lookup"><span data-stu-id="f5d02-185">n/a</span></span>|<span data-ttu-id="f5d02-186">Sağlayıcıya özel veri türü adı</span><span class="sxs-lookup"><span data-stu-id="f5d02-186">Provider-specific data type name</span></span>|  
|<span data-ttu-id="f5d02-187">PrimitiveTypeKind</span><span class="sxs-lookup"><span data-stu-id="f5d02-187">PrimitiveTypeKind</span></span>|<span data-ttu-id="f5d02-188">PrimitiveTypeKind</span><span class="sxs-lookup"><span data-stu-id="f5d02-188">PrimitiveTypeKind</span></span>|<span data-ttu-id="f5d02-189">Evet</span><span class="sxs-lookup"><span data-stu-id="f5d02-189">Yes</span></span>|<span data-ttu-id="f5d02-190">yok</span><span class="sxs-lookup"><span data-stu-id="f5d02-190">n/a</span></span>|<span data-ttu-id="f5d02-191">EDM türü adı</span><span class="sxs-lookup"><span data-stu-id="f5d02-191">EDM type name</span></span>|  
  
###### <a name="function-node"></a><span data-ttu-id="f5d02-192">Düğüm işlevi</span><span class="sxs-lookup"><span data-stu-id="f5d02-192">Function Node</span></span>  
 <span data-ttu-id="f5d02-193">Her işlev sağlayıcısı tek bir işlevi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f5d02-193">Each Function defines a single function available through the provider.</span></span>  
  
|<span data-ttu-id="f5d02-194">Öznitelik adı</span><span class="sxs-lookup"><span data-stu-id="f5d02-194">Attribute Name</span></span>|<span data-ttu-id="f5d02-195">Veri Türü</span><span class="sxs-lookup"><span data-stu-id="f5d02-195">Data Type</span></span>|<span data-ttu-id="f5d02-196">Gerekli</span><span class="sxs-lookup"><span data-stu-id="f5d02-196">Required</span></span>|<span data-ttu-id="f5d02-197">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="f5d02-197">Default Value</span></span>|<span data-ttu-id="f5d02-198">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f5d02-198">Description</span></span>|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|<span data-ttu-id="f5d02-199">Ad</span><span class="sxs-lookup"><span data-stu-id="f5d02-199">Name</span></span>|<span data-ttu-id="f5d02-200">Dize</span><span class="sxs-lookup"><span data-stu-id="f5d02-200">String</span></span>|<span data-ttu-id="f5d02-201">Evet</span><span class="sxs-lookup"><span data-stu-id="f5d02-201">Yes</span></span>|<span data-ttu-id="f5d02-202">yok</span><span class="sxs-lookup"><span data-stu-id="f5d02-202">n/a</span></span>|<span data-ttu-id="f5d02-203">Tanımlayıcı/işlevin adı</span><span class="sxs-lookup"><span data-stu-id="f5d02-203">Identifier/name of the function</span></span>|  
|<span data-ttu-id="f5d02-204">ReturnType</span><span class="sxs-lookup"><span data-stu-id="f5d02-204">ReturnType</span></span>|<span data-ttu-id="f5d02-205">Dize</span><span class="sxs-lookup"><span data-stu-id="f5d02-205">String</span></span>|<span data-ttu-id="f5d02-206">Hayır</span><span class="sxs-lookup"><span data-stu-id="f5d02-206">No</span></span>|<span data-ttu-id="f5d02-207">Geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="f5d02-207">Void</span></span>|<span data-ttu-id="f5d02-208">EDM işlevin dönüş türü</span><span class="sxs-lookup"><span data-stu-id="f5d02-208">The EDM return type of the function</span></span>|  
|<span data-ttu-id="f5d02-209">Toplama</span><span class="sxs-lookup"><span data-stu-id="f5d02-209">Aggregate</span></span>|<span data-ttu-id="f5d02-210">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="f5d02-210">Boolean</span></span>|<span data-ttu-id="f5d02-211">Hayır</span><span class="sxs-lookup"><span data-stu-id="f5d02-211">No</span></span>|<span data-ttu-id="f5d02-212">False</span><span class="sxs-lookup"><span data-stu-id="f5d02-212">False</span></span>|<span data-ttu-id="f5d02-213">İşlev bir toplama işlevi ise true</span><span class="sxs-lookup"><span data-stu-id="f5d02-213">True if the function is an aggregate function</span></span>|  
|<span data-ttu-id="f5d02-214">BuiltIn</span><span class="sxs-lookup"><span data-stu-id="f5d02-214">BuiltIn</span></span>|<span data-ttu-id="f5d02-215">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="f5d02-215">Boolean</span></span>|<span data-ttu-id="f5d02-216">Hayır</span><span class="sxs-lookup"><span data-stu-id="f5d02-216">No</span></span>|<span data-ttu-id="f5d02-217">Doğru</span><span class="sxs-lookup"><span data-stu-id="f5d02-217">True</span></span>|<span data-ttu-id="f5d02-218">İşlevi veri deposuna oluşturulursa true</span><span class="sxs-lookup"><span data-stu-id="f5d02-218">True if the function is built into the data store</span></span>|  
|<span data-ttu-id="f5d02-219">StoreFunctionName</span><span class="sxs-lookup"><span data-stu-id="f5d02-219">StoreFunctionName</span></span>|<span data-ttu-id="f5d02-220">Dize</span><span class="sxs-lookup"><span data-stu-id="f5d02-220">String</span></span>|<span data-ttu-id="f5d02-221">Hayır</span><span class="sxs-lookup"><span data-stu-id="f5d02-221">No</span></span>|<span data-ttu-id="f5d02-222">\<Adı ></span><span class="sxs-lookup"><span data-stu-id="f5d02-222">\<Name></span></span>|<span data-ttu-id="f5d02-223">Veri deposundaki işlev adı.</span><span class="sxs-lookup"><span data-stu-id="f5d02-223">Function Name in the data store.</span></span>  <span data-ttu-id="f5d02-224">İşlev adları yeniden yönlendirilmesi için bir düzeyi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5d02-224">Allows for a level of redirection of function names.</span></span>|  
|<span data-ttu-id="f5d02-225">NiladicFunction</span><span class="sxs-lookup"><span data-stu-id="f5d02-225">NiladicFunction</span></span>|<span data-ttu-id="f5d02-226">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="f5d02-226">Boolean</span></span>|<span data-ttu-id="f5d02-227">Hayır</span><span class="sxs-lookup"><span data-stu-id="f5d02-227">No</span></span>|<span data-ttu-id="f5d02-228">False</span><span class="sxs-lookup"><span data-stu-id="f5d02-228">False</span></span>|<span data-ttu-id="f5d02-229">İşlev parametreleri gerektirmez ve hiçbir parametre olmadan çağrılırsa true</span><span class="sxs-lookup"><span data-stu-id="f5d02-229">True if the function does not require parameters and is called without any parameters</span></span>|  
|<span data-ttu-id="f5d02-230">ParameterType</span><span class="sxs-lookup"><span data-stu-id="f5d02-230">ParameterType</span></span><br /><br /> <span data-ttu-id="f5d02-231">Semantiği</span><span class="sxs-lookup"><span data-stu-id="f5d02-231">Semantics</span></span>|<span data-ttu-id="f5d02-232">ParameterSemantics</span><span class="sxs-lookup"><span data-stu-id="f5d02-232">ParameterSemantics</span></span>|<span data-ttu-id="f5d02-233">Hayır</span><span class="sxs-lookup"><span data-stu-id="f5d02-233">No</span></span>|<span data-ttu-id="f5d02-234">AllowImplicit</span><span class="sxs-lookup"><span data-stu-id="f5d02-234">AllowImplicit</span></span><br /><br /> <span data-ttu-id="f5d02-235">Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="f5d02-235">Conversion</span></span>|<span data-ttu-id="f5d02-236">Sorgu işlem hattı parametre türü değiştirme ile nasıl ele alması gerektiğini Seçimi:</span><span class="sxs-lookup"><span data-stu-id="f5d02-236">Choice of how the query pipeline should deal with parameter type substitution:</span></span><br /><br /> <span data-ttu-id="f5d02-237">-ExactMatchOnly</span><span class="sxs-lookup"><span data-stu-id="f5d02-237">-   ExactMatchOnly</span></span><br /><span data-ttu-id="f5d02-238">-Allowımplicitpromotion</span><span class="sxs-lookup"><span data-stu-id="f5d02-238">-   AllowImplicitPromotion</span></span><br /><span data-ttu-id="f5d02-239">-Allowımplicitconversion</span><span class="sxs-lookup"><span data-stu-id="f5d02-239">-   AllowImplicitConversion</span></span>|  
  
 <span data-ttu-id="f5d02-240">**Parametreleri düğümü**</span><span class="sxs-lookup"><span data-stu-id="f5d02-240">**Parameters Node**</span></span>  
  
 <span data-ttu-id="f5d02-241">Her işlev bir veya daha fazla parametre düğümleri koleksiyonu vardır.</span><span class="sxs-lookup"><span data-stu-id="f5d02-241">Each function has a collection of one or more Parameter nodes.</span></span>  
  
|<span data-ttu-id="f5d02-242">Öznitelik adı</span><span class="sxs-lookup"><span data-stu-id="f5d02-242">Attribute Name</span></span>|<span data-ttu-id="f5d02-243">Veri Türü</span><span class="sxs-lookup"><span data-stu-id="f5d02-243">Data Type</span></span>|<span data-ttu-id="f5d02-244">Gerekli</span><span class="sxs-lookup"><span data-stu-id="f5d02-244">Required</span></span>|<span data-ttu-id="f5d02-245">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="f5d02-245">Default Value</span></span>|<span data-ttu-id="f5d02-246">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f5d02-246">Description</span></span>|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|<span data-ttu-id="f5d02-247">Ad</span><span class="sxs-lookup"><span data-stu-id="f5d02-247">Name</span></span>|<span data-ttu-id="f5d02-248">Dize</span><span class="sxs-lookup"><span data-stu-id="f5d02-248">String</span></span>|<span data-ttu-id="f5d02-249">Evet</span><span class="sxs-lookup"><span data-stu-id="f5d02-249">Yes</span></span>|<span data-ttu-id="f5d02-250">yok</span><span class="sxs-lookup"><span data-stu-id="f5d02-250">n/a</span></span>|<span data-ttu-id="f5d02-251">Tanımlayıcı/parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="f5d02-251">Identifier/name of the parameter.</span></span>|  
|<span data-ttu-id="f5d02-252">Tür</span><span class="sxs-lookup"><span data-stu-id="f5d02-252">Type</span></span>|<span data-ttu-id="f5d02-253">Dize</span><span class="sxs-lookup"><span data-stu-id="f5d02-253">String</span></span>|<span data-ttu-id="f5d02-254">Evet</span><span class="sxs-lookup"><span data-stu-id="f5d02-254">Yes</span></span>|<span data-ttu-id="f5d02-255">yok</span><span class="sxs-lookup"><span data-stu-id="f5d02-255">n/a</span></span>|<span data-ttu-id="f5d02-256">Parametrenin EDM türü.</span><span class="sxs-lookup"><span data-stu-id="f5d02-256">The EDM type of the parameter.</span></span>|  
|<span data-ttu-id="f5d02-257">Mod</span><span class="sxs-lookup"><span data-stu-id="f5d02-257">Mode</span></span>|<span data-ttu-id="f5d02-258">Parametre</span><span class="sxs-lookup"><span data-stu-id="f5d02-258">Parameter</span></span><br /><br /> <span data-ttu-id="f5d02-259">Yön</span><span class="sxs-lookup"><span data-stu-id="f5d02-259">Direction</span></span>|<span data-ttu-id="f5d02-260">Evet</span><span class="sxs-lookup"><span data-stu-id="f5d02-260">Yes</span></span>|<span data-ttu-id="f5d02-261">yok</span><span class="sxs-lookup"><span data-stu-id="f5d02-261">n/a</span></span>|<span data-ttu-id="f5d02-262">Parametre yönü:</span><span class="sxs-lookup"><span data-stu-id="f5d02-262">Direction of parameter:</span></span><br /><br /> <span data-ttu-id="f5d02-263">-içinde</span><span class="sxs-lookup"><span data-stu-id="f5d02-263">-   in</span></span><br /><span data-ttu-id="f5d02-264">-out</span><span class="sxs-lookup"><span data-stu-id="f5d02-264">-   out</span></span><br /><span data-ttu-id="f5d02-265">-ınout</span><span class="sxs-lookup"><span data-stu-id="f5d02-265">-   inout</span></span>|  
  
##### <a name="namespace-attribute"></a><span data-ttu-id="f5d02-266">Namespace özniteliği</span><span class="sxs-lookup"><span data-stu-id="f5d02-266">Namespace Attribute</span></span>  
 <span data-ttu-id="f5d02-267">Her bir veri deposu sağlayıcısı ad alanı veya ad alanı bildiriminde tanımlanan bilgi grubu tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f5d02-267">Each data store provider must define a namespace or group of namespaces for information defined in the manifest.</span></span> <span data-ttu-id="f5d02-268">Bu ad alanı Entity SQL sorguları, işlevi ve türü adlarını çözümlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f5d02-268">This namespace can be used in Entity SQL queries to resolve names of functions and types.</span></span> <span data-ttu-id="f5d02-269">Örneğin: SqlServer.</span><span class="sxs-lookup"><span data-stu-id="f5d02-269">For instance: SqlServer.</span></span> <span data-ttu-id="f5d02-270">Bu ad alanı Entity SQL sorguları tarafından desteklenen standart işlev için varlık Hizmetleri tarafından tanımlanan kurallı ad alanı, EDM, farklı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f5d02-270">That namespace must be different from the canonical namespace, EDM, defined by Entity Services for standard functions to be supported by Entity SQL queries.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5d02-271">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5d02-271">See also</span></span>

- [<span data-ttu-id="f5d02-272">Entity Framework Veri Sağlayıcısı Yazma</span><span class="sxs-lookup"><span data-stu-id="f5d02-272">Writing an Entity Framework Data Provider</span></span>](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
