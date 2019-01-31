---
title: <Uri> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
ms.openlocfilehash: f432be7594b1659dfcae0c6eee706358230f2cbb
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269256"
---
# <a name="uri-element-uri-settings"></a><span data-ttu-id="60819-102">\<URI > öğesi (Uri ayarları)</span><span class="sxs-lookup"><span data-stu-id="60819-102">\<Uri> Element (Uri Settings)</span></span>
<span data-ttu-id="60819-103">.NET Framework web adresleri Tekdüzen Kaynak Tanımlayıcıları (URI'lar) kullanılarak ifade nasıl işlediğini belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="60819-103">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="60819-104">Şema hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="60819-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="60819-105">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="60819-105">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="60819-106">\<URI ></span><span class="sxs-lookup"><span data-stu-id="60819-106">\<uri></span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="60819-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="60819-107">Syntax</span></span>  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="60819-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="60819-108">Attributes and Elements</span></span>  
 <span data-ttu-id="60819-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="60819-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="60819-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="60819-110">Attributes</span></span>  
 <span data-ttu-id="60819-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="60819-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="60819-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="60819-112">Child Elements</span></span>  
  
|<span data-ttu-id="60819-113">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="60819-113">**Element**</span></span>|<span data-ttu-id="60819-114">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="60819-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="60819-115">IDN</span><span class="sxs-lookup"><span data-stu-id="60819-115">idn</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)|<span data-ttu-id="60819-116">Etki alanı adları için Uluslararası yapılan etki alanı adı (IDN) ayrıştırma uygulanıp uygulanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="60819-116">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="60819-117">iriParsing</span><span class="sxs-lookup"><span data-stu-id="60819-117">iriParsing</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)|<span data-ttu-id="60819-118">Uluslararası kaynak tanımlayıcı (IRI) ayrıştırma için uygulanıp uygulanmadığını belirtir <xref:System.Uri> ve IRI ayrıştırma kurallarını uygulanıp.</span><span class="sxs-lookup"><span data-stu-id="60819-118">Specifies if International Resource Identifier (IRI) parsing is applied to <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="60819-119">schemeSettings</span><span class="sxs-lookup"><span data-stu-id="60819-119">schemeSettings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="60819-120">Belirtir nasıl bir <xref:System.Uri> belirli düzenleri için ayrıştırılacak.</span><span class="sxs-lookup"><span data-stu-id="60819-120">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="60819-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="60819-121">Parent Elements</span></span>  
  
|<span data-ttu-id="60819-122">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="60819-122">**Element**</span></span>|<span data-ttu-id="60819-123">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="60819-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="60819-124">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="60819-124">configuration</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="60819-125">Tüm ad alanları için ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="60819-125">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60819-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="60819-126">Remarks</span></span>  
 <span data-ttu-id="60819-127">`uri` Ögesinin üyeleri için ayarları <xref:System.Uri> sınıfları tarafından kullanılan sınıf <xref:System.Net> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="60819-127">The `uri` element contains settings for members of the <xref:System.Uri> class used by classes in the <xref:System.Net> namespace.</span></span> <span data-ttu-id="60819-128">IRI ve IDN desteğini ayarlarını yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="60819-128">The settings configure support for IRI and IDN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60819-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="60819-129">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="60819-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="60819-130">Description</span></span>  
 <span data-ttu-id="60819-131">Aşağıdaki örnek tarafından kullanılan bir yapılandırma gösterir <xref:System.Uri> IRI ayrıştırma ve IDN adları desteklemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="60819-131">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span> <span data-ttu-id="60819-132">Örnek aynı zamanda tüm düzeni ayarlarını temizler ve ardından http düzeni için yol yüzde olarak kodlanmış sınırlayıcılar kaçış değil desteği ekler.</span><span class="sxs-lookup"><span data-stu-id="60819-132">The example also clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
### <a name="code"></a><span data-ttu-id="60819-133">Kod</span><span class="sxs-lookup"><span data-stu-id="60819-133">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="60819-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60819-134">See also</span></span>
- [<span data-ttu-id="60819-135">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="60819-135">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
