---
title: "&lt;iriParsing&gt; öğesi (URI ayarları)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 6cd69df9ccba39520cca26bb7042dc2932565336
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltiriparsinggt-element-uri-settings"></a><span data-ttu-id="d421a-102">&lt;iriParsing&gt; öğesi (URI ayarları)</span><span class="sxs-lookup"><span data-stu-id="d421a-102">&lt;iriParsing&gt; Element (Uri Settings)</span></span>
<span data-ttu-id="d421a-103">Uluslararası kaynak tanımlayıcısı (IRI) ayrıştırma için uygulanmış olup olmadığını belirten bir <xref:System.Uri> ve kuralları ayrıştırma IRI uygulanıp.</span><span class="sxs-lookup"><span data-stu-id="d421a-103">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="d421a-104">Şema hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="d421a-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="d421a-105">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="d421a-105">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="d421a-106">\<URI > öğesi (URI ayarları)</span><span class="sxs-lookup"><span data-stu-id="d421a-106">\<Uri> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [<span data-ttu-id="d421a-107">\<iriParsing ></span><span class="sxs-lookup"><span data-stu-id="d421a-107">\<iriParsing></span></span>](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="d421a-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d421a-108">Syntax</span></span>  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d421a-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d421a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d421a-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d421a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d421a-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d421a-111">Attributes</span></span>  
  
|<span data-ttu-id="d421a-112">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="d421a-112">**Element**</span></span>|<span data-ttu-id="d421a-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="d421a-113">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="d421a-114">IRI ayrıştırma etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d421a-114">Specifies whether IRI parsing is enabled.</span></span> <span data-ttu-id="d421a-115">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="d421a-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d421a-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d421a-116">Child Elements</span></span>  
 <span data-ttu-id="d421a-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="d421a-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d421a-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d421a-118">Parent Elements</span></span>  
  
|<span data-ttu-id="d421a-119">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="d421a-119">**Element**</span></span>|<span data-ttu-id="d421a-120">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="d421a-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d421a-121">URI</span><span class="sxs-lookup"><span data-stu-id="d421a-121">uri</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|<span data-ttu-id="d421a-122">.NET Framework Tekdüzen Kaynak Tanımlayıcıları (URI'ler) kullanılarak ifade web adresleri işleme biçimini belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="d421a-122">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d421a-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d421a-123">Remarks</span></span>  
 <span data-ttu-id="d421a-124">Varolan <xref:System.Uri> sınıf .NET Framework 3. 5 ' genişletilmişse.</span><span class="sxs-lookup"><span data-stu-id="d421a-124">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="d421a-125">3.0 SP1 ve 2.0 SP1 uluslararası kaynak tanımlayıcıları (IRI) ve Uluslararası yapılan etki alanı adları (IDN) desteği sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="d421a-125">3.0 SP1, and 2.0 SP1 to provide support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="d421a-126">Geçerli kullanıcı özellikle IRI ve IDN etkinleştirmediğiniz sürece herhangi bir değişiklik .NET Framework 2.0 davranış görmezsiniz destekler.</span><span class="sxs-lookup"><span data-stu-id="d421a-126">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="d421a-127">Bu, .NET Framework'ün önceki sürümler ile uygulama uyumluluğunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="d421a-127">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="d421a-128">IRI desteğini etkinleştirmek için aşağıdaki iki değişiklik gereklidir:</span><span class="sxs-lookup"><span data-stu-id="d421a-128">To enable support for IRI, the following two changes are required:</span></span>  
  
1.  <span data-ttu-id="d421a-129">.NET Framework 2.0 dizini altındaki machine.config dosyasının aşağıdaki satırı ekleyin</span><span class="sxs-lookup"><span data-stu-id="d421a-129">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  <span data-ttu-id="d421a-130">Kuralları ayrıştırma IRI uygulanmış olup olmadığını belirtin.</span><span class="sxs-lookup"><span data-stu-id="d421a-130">Specify whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="d421a-131">Machine.config veya app.config dosyasında yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="d421a-131">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="d421a-132">IRI ayrıştırma etkinleştirme (etkin iriParsing = `true`) normalleştirme ne yapacağını ve en son IRI göre denetimi karakter 3987 RFC kuralları.</span><span class="sxs-lookup"><span data-stu-id="d421a-132">Enabling IRI parsing (iriParsing enabled = `true`) will do normalization and character checking according to the latest IRI rules in RFC 3987.</span></span> <span data-ttu-id="d421a-133">Varsayılan değer `false` ve normalleştirme yapın ve RFC 2396 göre denetleme ve RFC 3986 (IPv6 değişmez değerleri için) karakter.</span><span class="sxs-lookup"><span data-stu-id="d421a-133">The default value is `false` and will do normalization and character checking according to RFC 2396 and RFC 3986 (for IPv6 literals).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="d421a-134">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="d421a-134">Configuration Files</span></span>  
 <span data-ttu-id="d421a-135">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d421a-135">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d421a-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="d421a-136">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="d421a-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d421a-137">Description</span></span>  
 <span data-ttu-id="d421a-138">Aşağıdaki örnek tarafından kullanılan bir yapılandırma gösterir <xref:System.Uri> IRI ayrıştırma ve IDN adları desteklemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="d421a-138">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="d421a-139">Kod</span><span class="sxs-lookup"><span data-stu-id="d421a-139">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d421a-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d421a-140">See Also</span></span>  
 <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 [<span data-ttu-id="d421a-141">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="d421a-141">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
