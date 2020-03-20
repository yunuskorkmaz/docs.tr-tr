---
title: Sağlayıcı Bildirimi Belirtimi
ms.date: 03/30/2017
ms.assetid: bb450b47-8951-4f99-9350-26f05a4d4e46
ms.openlocfilehash: 28bae8a6e249aa1fdab3c67759c8f8575cbdaa10
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149732"
---
# <a name="provider-manifest-specification"></a><span data-ttu-id="f422a-102">Sağlayıcı Bildirimi Belirtimi</span><span class="sxs-lookup"><span data-stu-id="f422a-102">Provider Manifest Specification</span></span>
<span data-ttu-id="f422a-103">Bu bölümde, bir veri deposu sağlayıcısının veri deposundaki türleri ve işlevleri nasıl destekleyebilir ilerler.</span><span class="sxs-lookup"><span data-stu-id="f422a-103">This section discusses how a data store provider can support the types and functions in the data store.</span></span>  
  
 <span data-ttu-id="f422a-104">Varlık Hizmetleri, belirli bir veri deposu sağlayıcısından bağımsız olarak çalışır, ancak yine de bir veri sağlayıcısının modellerin, eşlemelerin ve sorguların temel bir veri deposuyla nasıl etkileşimde olduğunu açıkça tanımlamasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="f422a-104">Entity Services operates independently of a specific data store provider yet still allows a data provider to explicitly define how models, mappings, and queries interact with an underlying data store.</span></span> <span data-ttu-id="f422a-105">Bir soyutlama katmanı olmadan, Varlık Hizmetleri yalnızca belirli bir veri deposuveya veri sağlayıcısını hedefleyebilir.</span><span class="sxs-lookup"><span data-stu-id="f422a-105">Without a layer of abstraction, Entity Services could only be targeted at a specific data store or data provider.</span></span>  
  
 <span data-ttu-id="f422a-106">Sağlayıcının desteklediği türler, temel veritabanı tarafından doğrudan veya dolaylı olarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f422a-106">Types that the provider supports are directly or indirectly supported by the underlying database.</span></span> <span data-ttu-id="f422a-107">Bu türler tam depo türleri değil, sağlayıcının Varlık Çerçevesini desteklemek için kullandığı türlerdir.</span><span class="sxs-lookup"><span data-stu-id="f422a-107">These types are not necessarily the exact store types, but the types the provider uses to support the Entity Framework.</span></span> <span data-ttu-id="f422a-108">Sağlayıcı/depo türleri Varlık Veri Modeli (EDM) terimlerinde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f422a-108">Provider/store types are described in the Entity Data Model (EDM) terms.</span></span>  
  
 <span data-ttu-id="f422a-109">Veri deposu tarafından desteklenen işlevler için parametre ve iade türleri EDM terimleriyle belirtilir.</span><span class="sxs-lookup"><span data-stu-id="f422a-109">Parameter and return types for the functions supported by the data store are specified in EDM terms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f422a-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f422a-110">Requirements</span></span>  
 <span data-ttu-id="f422a-111">Varlık Çerçevesi ve veri deposunun, herhangi bir veri kaybı veya kesilme olmaksızın bilinen türlerde verileri ileri geri aktarabilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f422a-111">The Entity Framework and the data store need to be able to pass data back and forth in known types without any data loss or truncation.</span></span>  
  
 <span data-ttu-id="f422a-112">Sağlayıcı bildirimi, veri deposuna bağlantı açmak zorunda kalmadan tasarım zamanında araçlar tarafından yüklenebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f422a-112">The provider manifest must be loadable by tools at design time without having to open a connection to the data store.</span></span>  
  
 <span data-ttu-id="f422a-113">Varlık Çerçevesi büyük/küçük harf duyarlıdır, ancak temel veri deposu olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="f422a-113">The Entity Framework is case sensitive, but the underlying data store may not be.</span></span> <span data-ttu-id="f422a-114">EDM yapıları (tanımlayıcılar ve tür adları, örneğin) tanımlandığında ve bildirimde kullanıldığında, Varlık Çerçevesi durum hassasiyetini kullanmaları gerekir.</span><span class="sxs-lookup"><span data-stu-id="f422a-114">When EDM artifacts (identifiers and type names, for example) are defined and used in the manifest, they must use the Entity Framework case sensitivity.</span></span> <span data-ttu-id="f422a-115">Örnek olay açısından duyarlı olabilecek veri depolama öğeleri sağlayıcı bildiriminde görünürse, kasanın sağlayıcı bildiriminde tutulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f422a-115">If data store elements that may be case sensitive appear in the provider manifest, that casing needs to be maintained in the provider manifest.</span></span>  
  
 <span data-ttu-id="f422a-116">Varlık Çerçevesi, tüm veri sağlayıcıları için bir sağlayıcı bildirimi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f422a-116">The Entity Framework requires a provider manifest for all data providers.</span></span> <span data-ttu-id="f422a-117">Varlık Çerçevesi ile sağlayıcı bildirimi olmayan bir sağlayıcı kullanmaya çalışırsanız, bir hata alırsınız.</span><span class="sxs-lookup"><span data-stu-id="f422a-117">If you try to use a provider that does not have a provider manifest with the Entity Framework, you will get an error.</span></span>  
  
 <span data-ttu-id="f422a-118">Aşağıdaki tabloda, sağlayıcı etkileşimi yoluyla özel durumlar ortaya çıktığında Varlık Çerçevesi'nin atacağı özel durum türleri açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="f422a-118">The following table describes the kinds of exceptions the Entity Framework would throw when exceptions arise through provider interaction:</span></span>  
  
|<span data-ttu-id="f422a-119">Sorun</span><span class="sxs-lookup"><span data-stu-id="f422a-119">Issue</span></span>|<span data-ttu-id="f422a-120">Özel durum</span><span class="sxs-lookup"><span data-stu-id="f422a-120">Exception</span></span>|  
|-----------|---------------|  
|<span data-ttu-id="f422a-121">Sağlayıcı, DbProviderServices'te GetProviderManifest'i desteklemez.</span><span class="sxs-lookup"><span data-stu-id="f422a-121">The Provider does not support GetProviderManifest in DbProviderServices.</span></span>|<span data-ttu-id="f422a-122">Providerıncompatibleexception</span><span class="sxs-lookup"><span data-stu-id="f422a-122">ProviderIncompatibleException</span></span>|  
|<span data-ttu-id="f422a-123">Eksik sağlayıcı bildirimi: `null` sağlayıcı bildirimini almaya çalışırken sağlayıcı geri döner.</span><span class="sxs-lookup"><span data-stu-id="f422a-123">Missing provider manifest: the provider returns `null` when attempting to retrieve the provider manifest.</span></span>|<span data-ttu-id="f422a-124">Providerıncompatibleexception</span><span class="sxs-lookup"><span data-stu-id="f422a-124">ProviderIncompatibleException</span></span>|  
|<span data-ttu-id="f422a-125">Geçersiz sağlayıcı bildirimi: sağlayıcı bildirimini almaya çalışırken sağlayıcı geçersiz XML'i döndürür.</span><span class="sxs-lookup"><span data-stu-id="f422a-125">Invalid provider manifest: the provider returns invalid XML when attempting to retrieve the provider manifest.</span></span>|<span data-ttu-id="f422a-126">Providerıncompatibleexception</span><span class="sxs-lookup"><span data-stu-id="f422a-126">ProviderIncompatibleException</span></span>|  
  
## <a name="scenarios"></a><span data-ttu-id="f422a-127">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="f422a-127">Scenarios</span></span>  
 <span data-ttu-id="f422a-128">Sağlayıcı aşağıdaki senaryoları desteklemelidir:</span><span class="sxs-lookup"><span data-stu-id="f422a-128">A provider should support the following scenarios:</span></span>  
  
### <a name="writing-a-provider-with-symmetric-type-mapping"></a><span data-ttu-id="f422a-129">Simetrik Tip Eşlemeli Sağlayıcı Yazma</span><span class="sxs-lookup"><span data-stu-id="f422a-129">Writing a Provider with Symmetric Type Mapping</span></span>  
 <span data-ttu-id="f422a-130">Eşleme yönü ne olursa olsun, her mağaza türü tek bir EDM türüne eşlem ler yaptığı Entity Framework için bir sağlayıcı yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f422a-130">You can write a provider for the Entity Framework where each store type maps to a single EDM type, regardless of the mapping direction.</span></span> <span data-ttu-id="f422a-131">EDM türüne karşılık gelen çok basit eşleme türüne sahip bir sağlayıcı türü için, tür sistemi basit olduğundan veya EDM türleri ile eşleştiğinden simetrik bir çözüm kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f422a-131">For a provider type that has very simple mapping that corresponds with an EDM type, you can use a symmetric solution because the type system is simple or matches EDM types.</span></span>  
  
 <span data-ttu-id="f422a-132">Etki alanlarının basitliğini kullanabilir ve statik bir bildirim sağlayıcı bildirimi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f422a-132">You can use the simplicity of their domain and produce a static declarative provider manifest.</span></span>  
  
 <span data-ttu-id="f422a-133">İki bölümden bir XML dosyası yazarsınız:</span><span class="sxs-lookup"><span data-stu-id="f422a-133">You write an XML file that has two sections:</span></span>  
  
- <span data-ttu-id="f422a-134">Bir mağaza türü veya işlevinin "EDM muadili" açısından ifade edilen sağlayıcı türlerinin listesi.</span><span class="sxs-lookup"><span data-stu-id="f422a-134">A list of provider types expressed in terms of the "EDM counterpart" of a store type or function.</span></span> <span data-ttu-id="f422a-135">Mağaza türlerinin benzer EDM türleri vardır.</span><span class="sxs-lookup"><span data-stu-id="f422a-135">Store types have counterpart EDM types.</span></span> <span data-ttu-id="f422a-136">Mağaza işlevleri karşılık gelen EDM işlevlerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f422a-136">Store functions have corresponding EDM functions.</span></span> <span data-ttu-id="f422a-137">Örneğin, varchar bir SQL Server türüdür, ancak karşılık gelen EDM türü dizedir.</span><span class="sxs-lookup"><span data-stu-id="f422a-137">For example, varchar is a SQL Server type but the corresponding EDM type is string.</span></span>  
  
- <span data-ttu-id="f422a-138">Parametre ve dönüş türlerinin EDM terimleriyle ifade edildiği sağlayıcı tarafından desteklenen işlevlerin listesi.</span><span class="sxs-lookup"><span data-stu-id="f422a-138">A list of functions supported by the provider where parameter and return types are expressed in EDM terms.</span></span>  
  
### <a name="writing-a-provider-with-asymmetric-type-mapping"></a><span data-ttu-id="f422a-139">Asimetrik Tip Eşlemeli Sağlayıcı Yazma</span><span class="sxs-lookup"><span data-stu-id="f422a-139">Writing a Provider with Asymmetric Type Mapping</span></span>  
 <span data-ttu-id="f422a-140">Varlık Çerçevesi için bir veri deposu sağlayıcısı yazarken, bazı türler için EDM'den sağlayıcıya tür eşleme sağlayıcısından EDM türüeşlemeden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="f422a-140">When writing a data store provider for the Entity Framework, the EDM-to-provider type mapping for some types may be different from provider-to-EDM type mapping.</span></span> <span data-ttu-id="f422a-141">Örneğin, sınırsız EDM PrimitiveTypeKind.String sağlayıcıda nvarchar(4000) ile eşlenebilirken, nvarchar(4000) EDM PrimitiveTypeKind.String(MaxLength=4000) ile eşlenir.</span><span class="sxs-lookup"><span data-stu-id="f422a-141">For instance, unbounded EDM PrimitiveTypeKind.String may map to nvarchar(4000) on the provider, while nvarchar(4000) maps to the EDM PrimitiveTypeKind.String(MaxLength=4000).</span></span>  
  
 <span data-ttu-id="f422a-142">İki bölümden bir XML dosyası yazarsınız:</span><span class="sxs-lookup"><span data-stu-id="f422a-142">You write an XML file that has two sections:</span></span>  
  
- <span data-ttu-id="f422a-143">EDM terimleriyle ifade edilen sağlayıcı türlerinin listesi ve her iki yön için eşleme tanımlayın: EDM-to-sağlayıcı ve sağlayıcı-EDM.</span><span class="sxs-lookup"><span data-stu-id="f422a-143">A list of provider types expressed in EDM terms and define mapping for both direction: EDM-to-provider and provider-to-EDM.</span></span>  
  
- <span data-ttu-id="f422a-144">Parametre ve dönüş türlerinin EDM terimleriyle ifade edildiği sağlayıcı tarafından desteklenen işlevlerin listesi.</span><span class="sxs-lookup"><span data-stu-id="f422a-144">A list of functions supported by the provider where parameter and return types are expressed in EDM terms.</span></span>  
  
## <a name="provider-manifest-discoverability"></a><span data-ttu-id="f422a-145">Sağlayıcı Manifesto Keşfedilebilirlik</span><span class="sxs-lookup"><span data-stu-id="f422a-145">Provider Manifest Discoverability</span></span>  
 <span data-ttu-id="f422a-146">Bildirim, Varlık Hizmetleri'ndeki (Araçlar veya Sorgu gibi) dolaylı olarak birkaç bileşen türü tarafından kullanılır, ancak veri deposu meta veri yükleyicisinin kullanımı yoluyla meta veriler tarafından daha doğrudan yararlanılır.</span><span class="sxs-lookup"><span data-stu-id="f422a-146">The manifest is used indirectly by several component types in Entity Services (for example Tools or Query) but more directly leveraged by metadata through the use of the data store metadata loader.</span></span>  
  
 <span data-ttu-id="f422a-147">![dfb3d02b&#45;7a8c&#45;4d51&#45;ac5a&#45;a73d8aa145e6](./media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6")</span><span class="sxs-lookup"><span data-stu-id="f422a-147">![dfb3d02b&#45;7a8c&#45;4d51&#45;ac5a&#45;a73d8aa145e6](./media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6")</span></span>  
  
 <span data-ttu-id="f422a-148">Ancak, belirli bir sağlayıcı farklı mağazaları veya aynı mağazanın farklı sürümlerini destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="f422a-148">However, a given provider may support different stores or different versions of the same store.</span></span> <span data-ttu-id="f422a-149">Bu nedenle, bir sağlayıcı desteklenen her veri deposu için farklı bir bildirim rapor etmelidir.</span><span class="sxs-lookup"><span data-stu-id="f422a-149">Therefore, a provider must report a different manifest for each supported data store.</span></span>  
  
### <a name="provider-manifest-token"></a><span data-ttu-id="f422a-150">Sağlayıcı Bildirimi Belirteci</span><span class="sxs-lookup"><span data-stu-id="f422a-150">Provider Manifest Token</span></span>  
 <span data-ttu-id="f422a-151">Bir veri deposu bağlantısı açıldığında, sağlayıcı doğru bildirimi döndürmek için bilgi sorgulayabilir.</span><span class="sxs-lookup"><span data-stu-id="f422a-151">When a data store connection is opened, the provider can query for information to return the right manifest.</span></span> <span data-ttu-id="f422a-152">Bu, bağlantı bilgilerinin kullanılamadığı çevrimdışı senaryolarda veya mağazaya bağlanmanın mümkün olmadığı durumlarda mümkün olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="f422a-152">This may not be possible in offline scenarios where connection information is not available or when it is not possible to connect to the store.</span></span> <span data-ttu-id="f422a-153">.ssdl `ProviderManifestToken` dosyasındaki öğenin `Schema` özniteliğini kullanarak bildirimi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="f422a-153">Identify the manifest by using the `ProviderManifestToken` attribute of the `Schema` element in the .ssdl file.</span></span> <span data-ttu-id="f422a-154">Bu öznitelik için gerekli bir biçim yoktur; sağlayıcı, mağazaya bağlantı açmadan bir bildirimi tanımlamak için gereken minimum bilgileri seçer.</span><span class="sxs-lookup"><span data-stu-id="f422a-154">There is no required format for this attribute; the provider chooses the minimum information needed to identify a manifest without opening a connection to the store.</span></span>  
  
 <span data-ttu-id="f422a-155">Örnek:</span><span class="sxs-lookup"><span data-stu-id="f422a-155">For example:</span></span>  
  
```xml  
<Schema Namespace="Northwind" Provider="System.Data.SqlClient" ProviderManifestToken="2005" xmlns:edm="http://schemas.microsoft.com/ado/2006/04/edm/ssdl" xmlns="http://schemas.microsoft.com/ado/2006/04/edm/ssdl">  
```  
  
## <a name="provider-manifest-programming-model"></a><span data-ttu-id="f422a-156">Sağlayıcı Manifesto Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="f422a-156">Provider Manifest Programming Model</span></span>  
 <span data-ttu-id="f422a-157"><xref:System.Data.Common.DbXmlEnabledProviderManifest>Sağlayıcılar, bildirimlerini bildirimsel olarak belirtmelerini sağlayan,</span><span class="sxs-lookup"><span data-stu-id="f422a-157">Providers derive from <xref:System.Data.Common.DbXmlEnabledProviderManifest>, which allows them to specify their manifests declaratively.</span></span> <span data-ttu-id="f422a-158">Aşağıdaki resimde bir sağlayıcının sınıf hiyerarşisi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="f422a-158">The following illustration shows the class hierarchy of a provider:</span></span>  
  
 <span data-ttu-id="f422a-159">![Yok](./media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")</span><span class="sxs-lookup"><span data-stu-id="f422a-159">![None](./media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")</span></span>  
  
### <a name="discoverability-api"></a><span data-ttu-id="f422a-160">Keşfedilebilirlik API'si</span><span class="sxs-lookup"><span data-stu-id="f422a-160">Discoverability API</span></span>  
 <span data-ttu-id="f422a-161">Sağlayıcı bildirimi, bir veri deposu bağlantısı veya sağlayıcı bildirimi kullanılarak Store Meta data yükleyici (StoreItemCollection) tarafından yüklenir.</span><span class="sxs-lookup"><span data-stu-id="f422a-161">The provider manifest is loaded by the Store Metadata loader (StoreItemCollection), either by using a data store connection or a provider manifest token.</span></span>  
  
#### <a name="using-a-data-store-connection"></a><span data-ttu-id="f422a-162">Veri Deposu Bağlantısı Kullanma</span><span class="sxs-lookup"><span data-stu-id="f422a-162">Using a Data Store Connection</span></span>  
 <span data-ttu-id="f422a-163">Veri deposu bağlantısı kullanılabilir olduğunda, <xref:System.Data.Common.DbProviderServices.GetProviderManifestToken%2A?displayProperty=nameWithType> <xref:System.Data.Common.DbProviderServices.GetProviderManifest%2A> döndüren <xref:System.Data.Common.DbProviderManifest>yönteme geçirilen belirteci döndürmek için arayın.</span><span class="sxs-lookup"><span data-stu-id="f422a-163">When the data store connection is available, call <xref:System.Data.Common.DbProviderServices.GetProviderManifestToken%2A?displayProperty=nameWithType> to return the token that is passed to the <xref:System.Data.Common.DbProviderServices.GetProviderManifest%2A> method, which returns <xref:System.Data.Common.DbProviderManifest>.</span></span> <span data-ttu-id="f422a-164">Bu yöntem sağlayıcının uygulanmasına yetki `GetDbProviderManifestToken`verir.</span><span class="sxs-lookup"><span data-stu-id="f422a-164">This method delegates to the provider's implementation of `GetDbProviderManifestToken`.</span></span>  
  
```csharp
public string GetProviderManifestToken(DbConnection connection);  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
#### <a name="using-a-provider-manifest-token"></a><span data-ttu-id="f422a-165">Sağlayıcı Bildirimi Belirteci Kullanma</span><span class="sxs-lookup"><span data-stu-id="f422a-165">Using a Provider Manifest Token</span></span>  
 <span data-ttu-id="f422a-166">Çevrimdışı senaryo için belirteç SSDL gösteriminden seçilir.</span><span class="sxs-lookup"><span data-stu-id="f422a-166">For the offline scenario, the token is picked from SSDL representation.</span></span> <span data-ttu-id="f422a-167">SSDL, daha fazla bilgi için bir ProviderManifestToken belirtmenize olanak tanır (daha fazla bilgi için [Bkz. Şema Elemanı (SSDL).](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl)</span><span class="sxs-lookup"><span data-stu-id="f422a-167">The SSDL allows you to specify a ProviderManifestToken (see [Schema Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl) for more information).</span></span> <span data-ttu-id="f422a-168">Örneğin, bir bağlantı açılamıyorsa, SSDL'de bildirimle ilgili bilgileri belirten bir sağlayıcı bildirimi belirteç vardır.</span><span class="sxs-lookup"><span data-stu-id="f422a-168">For example, if a connection cannot be opened, the SSDL has a provider manifest token that specifies information about the manifest.</span></span>  
  
```csharp
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
### <a name="provider-manifest-schema"></a><span data-ttu-id="f422a-169">Sağlayıcı Manifesto Şeması</span><span class="sxs-lookup"><span data-stu-id="f422a-169">Provider Manifest Schema</span></span>  
 <span data-ttu-id="f422a-170">Her sağlayıcı için tanımlanan bilgi şeması, meta veriler tarafından tüketilecek statik bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="f422a-170">The schema of information defined for each provider contains the static information to be consumed by metadata:</span></span>  
  
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
  
#### <a name="types-node"></a><span data-ttu-id="f422a-171">Tür Düğümü</span><span class="sxs-lookup"><span data-stu-id="f422a-171">Types Node</span></span>  
 <span data-ttu-id="f422a-172">Sağlayıcı bildirimindeki Tür düğümü, veri deposu veya sağlayıcı aracılığıyla yerel olarak desteklenen Türler hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="f422a-172">The Types node in the provider manifest contains information about the Types that are supported natively by the data store or through the provider.</span></span>  
  
##### <a name="type-node"></a><span data-ttu-id="f422a-173">Tip Düğümü</span><span class="sxs-lookup"><span data-stu-id="f422a-173">Type Node</span></span>  
 <span data-ttu-id="f422a-174">Her Tür düğümü EDM açısından bir sağlayıcı türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f422a-174">Each Type node defines a provider type in terms of EDM.</span></span> <span data-ttu-id="f422a-175">Tür düğümü sağlayıcı türünün adını ve eşlenere eşlenebilen model türüyle ilgili bilgileri açıklar ve bu tür eşlemi açıklamak için yönlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f422a-175">The Type node describes the name of the provider type, and information related to the model type it maps to and facets to describe that type mapping.</span></span>  
  
 <span data-ttu-id="f422a-176">Sağlayıcı bildiriminde bu tür bilgileri ifade etmek için, her TypeInformation bildiriminin her Tür için birkaç farklı açıklama tanımlaması gerekir:</span><span class="sxs-lookup"><span data-stu-id="f422a-176">In order to express this type information in the provider manifest, each TypeInformation declaration must define several facet descriptions for each Type:</span></span>  
  
|<span data-ttu-id="f422a-177">Öznitelik Adı</span><span class="sxs-lookup"><span data-stu-id="f422a-177">Attribute Name</span></span>|<span data-ttu-id="f422a-178">Veri Türü</span><span class="sxs-lookup"><span data-stu-id="f422a-178">Data Type</span></span>|<span data-ttu-id="f422a-179">Gerekli</span><span class="sxs-lookup"><span data-stu-id="f422a-179">Required</span></span>|<span data-ttu-id="f422a-180">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="f422a-180">Default Value</span></span>|<span data-ttu-id="f422a-181">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f422a-181">Description</span></span>|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|<span data-ttu-id="f422a-182">Adı</span><span class="sxs-lookup"><span data-stu-id="f422a-182">Name</span></span>|<span data-ttu-id="f422a-183">Dize</span><span class="sxs-lookup"><span data-stu-id="f422a-183">String</span></span>|<span data-ttu-id="f422a-184">Evet</span><span class="sxs-lookup"><span data-stu-id="f422a-184">Yes</span></span>|<span data-ttu-id="f422a-185">yok</span><span class="sxs-lookup"><span data-stu-id="f422a-185">n/a</span></span>|<span data-ttu-id="f422a-186">Sağlayıcıya özel veri türü adı</span><span class="sxs-lookup"><span data-stu-id="f422a-186">Provider-specific data type name</span></span>|  
|<span data-ttu-id="f422a-187">Primitivetypekind</span><span class="sxs-lookup"><span data-stu-id="f422a-187">PrimitiveTypeKind</span></span>|<span data-ttu-id="f422a-188">Primitivetypekind</span><span class="sxs-lookup"><span data-stu-id="f422a-188">PrimitiveTypeKind</span></span>|<span data-ttu-id="f422a-189">Evet</span><span class="sxs-lookup"><span data-stu-id="f422a-189">Yes</span></span>|<span data-ttu-id="f422a-190">yok</span><span class="sxs-lookup"><span data-stu-id="f422a-190">n/a</span></span>|<span data-ttu-id="f422a-191">EDM türü adı</span><span class="sxs-lookup"><span data-stu-id="f422a-191">EDM type name</span></span>|  
  
###### <a name="function-node"></a><span data-ttu-id="f422a-192">Fonksiyon Düğümü</span><span class="sxs-lookup"><span data-stu-id="f422a-192">Function Node</span></span>  
 <span data-ttu-id="f422a-193">Her İşlev sağlayıcı aracılığıyla kullanılabilen tek bir işlevi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f422a-193">Each Function defines a single function available through the provider.</span></span>  
  
|<span data-ttu-id="f422a-194">Öznitelik Adı</span><span class="sxs-lookup"><span data-stu-id="f422a-194">Attribute Name</span></span>|<span data-ttu-id="f422a-195">Veri Türü</span><span class="sxs-lookup"><span data-stu-id="f422a-195">Data Type</span></span>|<span data-ttu-id="f422a-196">Gerekli</span><span class="sxs-lookup"><span data-stu-id="f422a-196">Required</span></span>|<span data-ttu-id="f422a-197">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="f422a-197">Default Value</span></span>|<span data-ttu-id="f422a-198">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f422a-198">Description</span></span>|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|<span data-ttu-id="f422a-199">Adı</span><span class="sxs-lookup"><span data-stu-id="f422a-199">Name</span></span>|<span data-ttu-id="f422a-200">Dize</span><span class="sxs-lookup"><span data-stu-id="f422a-200">String</span></span>|<span data-ttu-id="f422a-201">Evet</span><span class="sxs-lookup"><span data-stu-id="f422a-201">Yes</span></span>|<span data-ttu-id="f422a-202">yok</span><span class="sxs-lookup"><span data-stu-id="f422a-202">n/a</span></span>|<span data-ttu-id="f422a-203">İşlevin tanımlayıcısı/adı</span><span class="sxs-lookup"><span data-stu-id="f422a-203">Identifier/name of the function</span></span>|  
|<span data-ttu-id="f422a-204">Returntype</span><span class="sxs-lookup"><span data-stu-id="f422a-204">ReturnType</span></span>|<span data-ttu-id="f422a-205">Dize</span><span class="sxs-lookup"><span data-stu-id="f422a-205">String</span></span>|<span data-ttu-id="f422a-206">Hayır</span><span class="sxs-lookup"><span data-stu-id="f422a-206">No</span></span>|<span data-ttu-id="f422a-207">Void</span><span class="sxs-lookup"><span data-stu-id="f422a-207">Void</span></span>|<span data-ttu-id="f422a-208">Fonksiyonun EDM dönüş türü</span><span class="sxs-lookup"><span data-stu-id="f422a-208">The EDM return type of the function</span></span>|  
|<span data-ttu-id="f422a-209">Toplama</span><span class="sxs-lookup"><span data-stu-id="f422a-209">Aggregate</span></span>|<span data-ttu-id="f422a-210">Boole</span><span class="sxs-lookup"><span data-stu-id="f422a-210">Boolean</span></span>|<span data-ttu-id="f422a-211">Hayır</span><span class="sxs-lookup"><span data-stu-id="f422a-211">No</span></span>|<span data-ttu-id="f422a-212">False</span><span class="sxs-lookup"><span data-stu-id="f422a-212">False</span></span>|<span data-ttu-id="f422a-213">İşlev bir toplu işlevse doğru</span><span class="sxs-lookup"><span data-stu-id="f422a-213">True if the function is an aggregate function</span></span>|  
|<span data-ttu-id="f422a-214">Yerleşik</span><span class="sxs-lookup"><span data-stu-id="f422a-214">BuiltIn</span></span>|<span data-ttu-id="f422a-215">Boole</span><span class="sxs-lookup"><span data-stu-id="f422a-215">Boolean</span></span>|<span data-ttu-id="f422a-216">Hayır</span><span class="sxs-lookup"><span data-stu-id="f422a-216">No</span></span>|<span data-ttu-id="f422a-217">True</span><span class="sxs-lookup"><span data-stu-id="f422a-217">True</span></span>|<span data-ttu-id="f422a-218">İşlev veri deposunda yerleşikse doğru</span><span class="sxs-lookup"><span data-stu-id="f422a-218">True if the function is built into the data store</span></span>|  
|<span data-ttu-id="f422a-219">StoreFunctionName</span><span class="sxs-lookup"><span data-stu-id="f422a-219">StoreFunctionName</span></span>|<span data-ttu-id="f422a-220">Dize</span><span class="sxs-lookup"><span data-stu-id="f422a-220">String</span></span>|<span data-ttu-id="f422a-221">Hayır</span><span class="sxs-lookup"><span data-stu-id="f422a-221">No</span></span>|<span data-ttu-id="f422a-222">\<İsim></span><span class="sxs-lookup"><span data-stu-id="f422a-222">\<Name></span></span>|<span data-ttu-id="f422a-223">Veri deposundaki Işlev Adı.</span><span class="sxs-lookup"><span data-stu-id="f422a-223">Function Name in the data store.</span></span>  <span data-ttu-id="f422a-224">İşlev adlarının yeniden yönlendirme düzeyini sağlar.</span><span class="sxs-lookup"><span data-stu-id="f422a-224">Allows for a level of redirection of function names.</span></span>|  
|<span data-ttu-id="f422a-225">NiladicFunction</span><span class="sxs-lookup"><span data-stu-id="f422a-225">NiladicFunction</span></span>|<span data-ttu-id="f422a-226">Boole</span><span class="sxs-lookup"><span data-stu-id="f422a-226">Boolean</span></span>|<span data-ttu-id="f422a-227">Hayır</span><span class="sxs-lookup"><span data-stu-id="f422a-227">No</span></span>|<span data-ttu-id="f422a-228">False</span><span class="sxs-lookup"><span data-stu-id="f422a-228">False</span></span>|<span data-ttu-id="f422a-229">İşlev parametreleri gerektirmiyorsa ve herhangi bir parametre olmadan çağrılırsa doğru</span><span class="sxs-lookup"><span data-stu-id="f422a-229">True if the function does not require parameters and is called without any parameters</span></span>|  
|<span data-ttu-id="f422a-230">ParametreTürü</span><span class="sxs-lookup"><span data-stu-id="f422a-230">ParameterType</span></span><br /><br /> <span data-ttu-id="f422a-231">Semantiği</span><span class="sxs-lookup"><span data-stu-id="f422a-231">Semantics</span></span>|<span data-ttu-id="f422a-232">ParametreSemantics</span><span class="sxs-lookup"><span data-stu-id="f422a-232">ParameterSemantics</span></span>|<span data-ttu-id="f422a-233">Hayır</span><span class="sxs-lookup"><span data-stu-id="f422a-233">No</span></span>|<span data-ttu-id="f422a-234">İzin Kolaylığı</span><span class="sxs-lookup"><span data-stu-id="f422a-234">AllowImplicit</span></span><br /><br /> <span data-ttu-id="f422a-235">Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="f422a-235">Conversion</span></span>|<span data-ttu-id="f422a-236">Sorgu ardışık lığı parametre türü ikame ile nasıl başa çıkmalıdır seçimi:</span><span class="sxs-lookup"><span data-stu-id="f422a-236">Choice of how the query pipeline should deal with parameter type substitution:</span></span><br /><br /> <span data-ttu-id="f422a-237">- ExactMatchOnly</span><span class="sxs-lookup"><span data-stu-id="f422a-237">-   ExactMatchOnly</span></span><br /><span data-ttu-id="f422a-238">- İzin Basitlik Promosyon</span><span class="sxs-lookup"><span data-stu-id="f422a-238">-   AllowImplicitPromotion</span></span><br /><span data-ttu-id="f422a-239">- İzin Basit dönüşüm</span><span class="sxs-lookup"><span data-stu-id="f422a-239">-   AllowImplicitConversion</span></span>|  
  
 <span data-ttu-id="f422a-240">**Parametreler Düğümü**</span><span class="sxs-lookup"><span data-stu-id="f422a-240">**Parameters Node**</span></span>  
  
 <span data-ttu-id="f422a-241">Her işlevin bir veya daha fazla Parametre düğümü nden oluşan bir koleksiyonu vardır.</span><span class="sxs-lookup"><span data-stu-id="f422a-241">Each function has a collection of one or more Parameter nodes.</span></span>  
  
|<span data-ttu-id="f422a-242">Öznitelik Adı</span><span class="sxs-lookup"><span data-stu-id="f422a-242">Attribute Name</span></span>|<span data-ttu-id="f422a-243">Veri Türü</span><span class="sxs-lookup"><span data-stu-id="f422a-243">Data Type</span></span>|<span data-ttu-id="f422a-244">Gerekli</span><span class="sxs-lookup"><span data-stu-id="f422a-244">Required</span></span>|<span data-ttu-id="f422a-245">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="f422a-245">Default Value</span></span>|<span data-ttu-id="f422a-246">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f422a-246">Description</span></span>|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|<span data-ttu-id="f422a-247">Adı</span><span class="sxs-lookup"><span data-stu-id="f422a-247">Name</span></span>|<span data-ttu-id="f422a-248">Dize</span><span class="sxs-lookup"><span data-stu-id="f422a-248">String</span></span>|<span data-ttu-id="f422a-249">Evet</span><span class="sxs-lookup"><span data-stu-id="f422a-249">Yes</span></span>|<span data-ttu-id="f422a-250">yok</span><span class="sxs-lookup"><span data-stu-id="f422a-250">n/a</span></span>|<span data-ttu-id="f422a-251">Parametrenin tanımlayıcısı/adı.</span><span class="sxs-lookup"><span data-stu-id="f422a-251">Identifier/name of the parameter.</span></span>|  
|<span data-ttu-id="f422a-252">Tür</span><span class="sxs-lookup"><span data-stu-id="f422a-252">Type</span></span>|<span data-ttu-id="f422a-253">Dize</span><span class="sxs-lookup"><span data-stu-id="f422a-253">String</span></span>|<span data-ttu-id="f422a-254">Evet</span><span class="sxs-lookup"><span data-stu-id="f422a-254">Yes</span></span>|<span data-ttu-id="f422a-255">yok</span><span class="sxs-lookup"><span data-stu-id="f422a-255">n/a</span></span>|<span data-ttu-id="f422a-256">Parametrenin EDM türü.</span><span class="sxs-lookup"><span data-stu-id="f422a-256">The EDM type of the parameter.</span></span>|  
|<span data-ttu-id="f422a-257">Mod</span><span class="sxs-lookup"><span data-stu-id="f422a-257">Mode</span></span>|<span data-ttu-id="f422a-258">Parametre</span><span class="sxs-lookup"><span data-stu-id="f422a-258">Parameter</span></span><br /><br /> <span data-ttu-id="f422a-259">Yön</span><span class="sxs-lookup"><span data-stu-id="f422a-259">Direction</span></span>|<span data-ttu-id="f422a-260">Evet</span><span class="sxs-lookup"><span data-stu-id="f422a-260">Yes</span></span>|<span data-ttu-id="f422a-261">yok</span><span class="sxs-lookup"><span data-stu-id="f422a-261">n/a</span></span>|<span data-ttu-id="f422a-262">Parametrenin yönü:</span><span class="sxs-lookup"><span data-stu-id="f422a-262">Direction of parameter:</span></span><br /><br /> <span data-ttu-id="f422a-263">- içinde</span><span class="sxs-lookup"><span data-stu-id="f422a-263">-   in</span></span><br /><span data-ttu-id="f422a-264">- çıkış</span><span class="sxs-lookup"><span data-stu-id="f422a-264">-   out</span></span><br /><span data-ttu-id="f422a-265">- inout</span><span class="sxs-lookup"><span data-stu-id="f422a-265">-   inout</span></span>|  
  
##### <a name="namespace-attribute"></a><span data-ttu-id="f422a-266">Namespace Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f422a-266">Namespace Attribute</span></span>  
 <span data-ttu-id="f422a-267">Her veri deposu sağlayıcısı, bildirimde tanımlanan bilgiler için bir ad alanı veya ad alanı grubu tanımlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="f422a-267">Each data store provider must define a namespace or group of namespaces for information defined in the manifest.</span></span> <span data-ttu-id="f422a-268">Bu ad alanı, işlevve tür adlarını çözmek için Entity SQL sorgularında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f422a-268">This namespace can be used in Entity SQL queries to resolve names of functions and types.</span></span> <span data-ttu-id="f422a-269">Örneğin: SqlServer.</span><span class="sxs-lookup"><span data-stu-id="f422a-269">For instance: SqlServer.</span></span> <span data-ttu-id="f422a-270">Bu ad alanı, Entity SQL sorguları tarafından desteklenen standart işlevler için Entity Services tarafından tanımlanan kanonik ad alanı EDM'den farklı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f422a-270">That namespace must be different from the canonical namespace, EDM, defined by Entity Services for standard functions to be supported by Entity SQL queries.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f422a-271">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f422a-271">See also</span></span>

- [<span data-ttu-id="f422a-272">Entity Framework Veri Sağlayıcısı Yazma</span><span class="sxs-lookup"><span data-stu-id="f422a-272">Writing an Entity Framework Data Provider</span></span>](writing-an-ef-data-provider.md)
