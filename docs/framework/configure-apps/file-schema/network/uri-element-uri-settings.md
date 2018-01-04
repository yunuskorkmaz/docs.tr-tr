---
title: "&lt;URI&gt; öğesi (URI ayarları)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 735a6596b22e6d6fdcff776dd79224230db5b7b3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="lturigt-element-uri-settings"></a><span data-ttu-id="b51ef-102">&lt;URI&gt; öğesi (URI ayarları)</span><span class="sxs-lookup"><span data-stu-id="b51ef-102">&lt;Uri&gt; Element (Uri Settings)</span></span>
<span data-ttu-id="b51ef-103">.NET Framework Tekdüzen Kaynak Tanımlayıcıları (URI'ler) kullanılarak ifade web adresleri işleme biçimini belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="b51ef-103">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="b51ef-104">Şema hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="b51ef-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="b51ef-105">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="b51ef-105">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="b51ef-106">\<URI ></span><span class="sxs-lookup"><span data-stu-id="b51ef-106">\<uri></span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="b51ef-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b51ef-107">Syntax</span></span>  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b51ef-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b51ef-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b51ef-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b51ef-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b51ef-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b51ef-110">Attributes</span></span>  
 <span data-ttu-id="b51ef-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="b51ef-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b51ef-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b51ef-112">Child Elements</span></span>  
  
|<span data-ttu-id="b51ef-113">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="b51ef-113">**Element**</span></span>|<span data-ttu-id="b51ef-114">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="b51ef-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b51ef-115">IDN</span><span class="sxs-lookup"><span data-stu-id="b51ef-115">idn</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)|<span data-ttu-id="b51ef-116">Etki alanı adlarının Uluslararası yapılan etki alanı adı (IDN) ayrıştırma uygulanmış olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b51ef-116">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="b51ef-117">iriParsing</span><span class="sxs-lookup"><span data-stu-id="b51ef-117">iriParsing</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)|<span data-ttu-id="b51ef-118">Uluslararası kaynak tanımlayıcısı (IRI) ayrıştırma için uygulanıp uygulanmadığını belirtir <xref:System.Uri> ve kuralları ayrıştırma IRI uygulanıp.</span><span class="sxs-lookup"><span data-stu-id="b51ef-118">Specifies if International Resource Identifier (IRI) parsing is applied to <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="b51ef-119">schemeSettings</span><span class="sxs-lookup"><span data-stu-id="b51ef-119">schemeSettings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="b51ef-120">Belirtir nasıl bir <xref:System.Uri> için belirli düzenleri ayrıştırılır.</span><span class="sxs-lookup"><span data-stu-id="b51ef-120">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b51ef-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b51ef-121">Parent Elements</span></span>  
  
|<span data-ttu-id="b51ef-122">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="b51ef-122">**Element**</span></span>|<span data-ttu-id="b51ef-123">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="b51ef-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b51ef-124">yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b51ef-124">configuration</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="b51ef-125">Tüm ad alanlarını ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="b51ef-125">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b51ef-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b51ef-126">Remarks</span></span>  
 <span data-ttu-id="b51ef-127">`uri` Ögesinin üyeleri için ayarları <xref:System.Uri> sınıfları tarafından kullanılan sınıf <xref:System.Net> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="b51ef-127">The `uri` element contains settings for members of the <xref:System.Uri> class used by classes in the <xref:System.Net> namespace.</span></span> <span data-ttu-id="b51ef-128">Ayarları IRI ve IDN desteğini yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="b51ef-128">The settings configure support for IRI and IDN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b51ef-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="b51ef-129">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="b51ef-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b51ef-130">Description</span></span>  
 <span data-ttu-id="b51ef-131">Aşağıdaki örnek tarafından kullanılan bir yapılandırma gösterir <xref:System.Uri> IRI ayrıştırma ve IDN adları desteklemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="b51ef-131">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span> <span data-ttu-id="b51ef-132">Örnek aynı zamanda tüm düzeni ayarlarını temizler ve yüzde olarak kodlanmış yol ayırıcısı http şeması için kaçış değil için destek ekler.</span><span class="sxs-lookup"><span data-stu-id="b51ef-132">The example also clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b51ef-133">Kod</span><span class="sxs-lookup"><span data-stu-id="b51ef-133">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
    <schemeSettings>  
      <clear/>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b51ef-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b51ef-134">See Also</span></span>  
 [<span data-ttu-id="b51ef-135">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="b51ef-135">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
