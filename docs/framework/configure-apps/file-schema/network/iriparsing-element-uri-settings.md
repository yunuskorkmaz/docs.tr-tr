---
title: '&lt;iriParsing&gt; öğesi (Uri ayarları)'
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 446447f0d279755dbc06e0e3a25d50ad86ad555b
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47075232"
---
# <a name="ltiriparsinggt-element-uri-settings"></a><span data-ttu-id="5fe9e-102">&lt;iriParsing&gt; öğesi (Uri ayarları)</span><span class="sxs-lookup"><span data-stu-id="5fe9e-102">&lt;iriParsing&gt; Element (Uri Settings)</span></span>
<span data-ttu-id="5fe9e-103">Uluslararası kaynak tanımlayıcı (IRI) ayrıştırma için uygulanmış olup olmadığını belirten bir <xref:System.Uri> ve IRI ayrıştırma kurallarını uygulanıp.</span><span class="sxs-lookup"><span data-stu-id="5fe9e-103">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="5fe9e-104">Şema hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="5fe9e-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="5fe9e-105">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="5fe9e-105">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="5fe9e-106">\<URI > öğesi (Uri ayarları)</span><span class="sxs-lookup"><span data-stu-id="5fe9e-106">\<Uri> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [<span data-ttu-id="5fe9e-107">\<iriParsing ></span><span class="sxs-lookup"><span data-stu-id="5fe9e-107">\<iriParsing></span></span>](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="5fe9e-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5fe9e-108">Syntax</span></span>  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5fe9e-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5fe9e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5fe9e-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5fe9e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5fe9e-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5fe9e-111">Attributes</span></span>  
  
|<span data-ttu-id="5fe9e-112">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="5fe9e-112">**Element**</span></span>|<span data-ttu-id="5fe9e-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="5fe9e-113">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="5fe9e-114">IRI ayrıştırma etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5fe9e-114">Specifies whether IRI parsing is enabled.</span></span> <span data-ttu-id="5fe9e-115">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5fe9e-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5fe9e-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5fe9e-116">Child Elements</span></span>  
 <span data-ttu-id="5fe9e-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="5fe9e-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5fe9e-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5fe9e-118">Parent Elements</span></span>  
  
|<span data-ttu-id="5fe9e-119">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="5fe9e-119">**Element**</span></span>|<span data-ttu-id="5fe9e-120">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="5fe9e-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5fe9e-121">URI</span><span class="sxs-lookup"><span data-stu-id="5fe9e-121">uri</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|<span data-ttu-id="5fe9e-122">.NET Framework web adresleri Tekdüzen Kaynak Tanımlayıcıları (URI'lar) kullanılarak ifade nasıl işlediğini belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="5fe9e-122">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5fe9e-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5fe9e-123">Remarks</span></span>  
 <span data-ttu-id="5fe9e-124">Varolan <xref:System.Uri> sınıfı, .NET Framework 3.5 genişletilmişse.</span><span class="sxs-lookup"><span data-stu-id="5fe9e-124">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="5fe9e-125">3.0 SP1 ve 2.0 SP1 uluslararası kaynak tanımlayıcı (IRI) ve Uluslararası yapılan etki alanı adı (IDN) desteği sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="5fe9e-125">3.0 SP1, and 2.0 SP1 to provide support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="5fe9e-126">Özellikle IRI ve IDN etkinleştirmediğiniz sürece geçerli kullanıcıların .NET Framework 2.0 davranış herhangi bir değişikliği göremezsiniz destekler.</span><span class="sxs-lookup"><span data-stu-id="5fe9e-126">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="5fe9e-127">Bu, .NET Framework'ün önceki sürümleriyle uygulama uyumluluğu sağlar.</span><span class="sxs-lookup"><span data-stu-id="5fe9e-127">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="5fe9e-128">IRI desteğini etkinleştirmek için aşağıdaki iki değişiklik gerekmez:</span><span class="sxs-lookup"><span data-stu-id="5fe9e-128">To enable support for IRI, the following two changes are required:</span></span>  
  
1.  <span data-ttu-id="5fe9e-129">Machine.config dosyasının .NET Framework 2.0 dizininde aşağıdaki satırı ekleyin</span><span class="sxs-lookup"><span data-stu-id="5fe9e-129">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  <span data-ttu-id="5fe9e-130">IRI ayrıştırma kurallarını uygulanması gerektiğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="5fe9e-130">Specify whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="5fe9e-131">Bu, machine.config veya app.config dosyasında yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="5fe9e-131">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="5fe9e-132">IRI ayrıştırma etkinleştirme (etkin iriParsing = `true`) normalleştirme yapar ve karakter göre en son IRI denetleme kuralları RFC 3987.</span><span class="sxs-lookup"><span data-stu-id="5fe9e-132">Enabling IRI parsing (iriParsing enabled = `true`) will do normalization and character checking according to the latest IRI rules in RFC 3987.</span></span> <span data-ttu-id="5fe9e-133">Varsayılan değer `false` normalleştirme yapın ve RFC 2396 göre denetleme ve RFC 3986'ya (IPv6 değişmez değerleri için) karakter.</span><span class="sxs-lookup"><span data-stu-id="5fe9e-133">The default value is `false` and will do normalization and character checking according to RFC 2396 and RFC 3986 (for IPv6 literals).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="5fe9e-134">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="5fe9e-134">Configuration Files</span></span>  
 <span data-ttu-id="5fe9e-135">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5fe9e-135">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fe9e-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="5fe9e-136">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="5fe9e-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5fe9e-137">Description</span></span>  
 <span data-ttu-id="5fe9e-138">Aşağıdaki örnek tarafından kullanılan bir yapılandırma gösterir <xref:System.Uri> IRI ayrıştırma ve IDN adları desteklemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="5fe9e-138">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="5fe9e-139">Kod</span><span class="sxs-lookup"><span data-stu-id="5fe9e-139">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5fe9e-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5fe9e-140">See Also</span></span>  
 <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 [<span data-ttu-id="5fe9e-141">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="5fe9e-141">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
