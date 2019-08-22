---
title: <Uri> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
ms.openlocfilehash: 80d71da5ca680872e4948fa8ff135fbbdf08cffe
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663974"
---
# <a name="uri-element-uri-settings"></a><span data-ttu-id="ec178-102">\<Uri > öğesi (Uri Ayarları)</span><span class="sxs-lookup"><span data-stu-id="ec178-102">\<Uri> Element (Uri Settings)</span></span>
<span data-ttu-id="ec178-103">.NET Framework Tekdüzen Kaynak tanımlayıcıları (URI 'Ler) kullanarak ifade edilen Web adreslerini nasıl işleyeceğini belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="ec178-103">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="ec178-104">Şema hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="ec178-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="ec178-105">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="ec178-105">\<configuration> Element</span></span>](../configuration-element.md)  
  
 [<span data-ttu-id="ec178-106">\<Uri ></span><span class="sxs-lookup"><span data-stu-id="ec178-106">\<uri></span></span>](uri-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="ec178-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ec178-107">Syntax</span></span>  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ec178-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ec178-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ec178-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ec178-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ec178-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ec178-110">Attributes</span></span>  
 <span data-ttu-id="ec178-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="ec178-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ec178-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ec178-112">Child Elements</span></span>  
  
|<span data-ttu-id="ec178-113">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="ec178-113">**Element**</span></span>|<span data-ttu-id="ec178-114">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="ec178-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="ec178-115">IDN</span><span class="sxs-lookup"><span data-stu-id="ec178-115">idn</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="ec178-116">Uluslararası etki alanı adı (ıDN) ayrıştırma 'nın etki alanı adlarına uygulandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ec178-116">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="ec178-117">iriParsing</span><span class="sxs-lookup"><span data-stu-id="ec178-117">iriParsing</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="ec178-118">Uluslararası kaynak tanımlayıcı (IRI) ayrıştırmanın uygulanıp uygulanmadığını <xref:System.Uri> ve IRI ayrıştırma kurallarının uygulanıp uygulanamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ec178-118">Specifies if International Resource Identifier (IRI) parsing is applied to <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="ec178-119">schemeSettings</span><span class="sxs-lookup"><span data-stu-id="ec178-119">schemeSettings</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="ec178-120">Belirli düzenler için <xref:System.Uri> nasıl ayrıştırılacaksınız belirtir.</span><span class="sxs-lookup"><span data-stu-id="ec178-120">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ec178-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ec178-121">Parent Elements</span></span>  
  
|<span data-ttu-id="ec178-122">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="ec178-122">**Element**</span></span>|<span data-ttu-id="ec178-123">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="ec178-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="ec178-124">yapılandırmada</span><span class="sxs-lookup"><span data-stu-id="ec178-124">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="ec178-125">Tüm ad alanları için ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="ec178-125">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec178-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ec178-126">Remarks</span></span>  
 <span data-ttu-id="ec178-127">Öğesi, <xref:System.Net> ad alanındaki sınıflar tarafından kullanılan <xref:System.Uri> sınıf üyeleri için ayarları içerir. `uri`</span><span class="sxs-lookup"><span data-stu-id="ec178-127">The `uri` element contains settings for members of the <xref:System.Uri> class used by classes in the <xref:System.Net> namespace.</span></span> <span data-ttu-id="ec178-128">Ayarlar IRI ve ıDN desteğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="ec178-128">The settings configure support for IRI and IDN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec178-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="ec178-129">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="ec178-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ec178-130">Description</span></span>  
 <span data-ttu-id="ec178-131">Aşağıdaki örnek, IRI ayrıştırma ve IDN adlarını desteklemek <xref:System.Uri> için sınıfı tarafından kullanılan bir yapılandırmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec178-131">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span> <span data-ttu-id="ec178-132">Örnek, tüm düzen ayarlarını da temizler ve ardından http şeması için tam olmayan yüzde kodlamalı yol sınırlayıcıları için destek ekler.</span><span class="sxs-lookup"><span data-stu-id="ec178-132">The example also clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ec178-133">Kod</span><span class="sxs-lookup"><span data-stu-id="ec178-133">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ec178-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec178-134">See also</span></span>

- [<span data-ttu-id="ec178-135">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="ec178-135">Network Settings Schema</span></span>](index.md)
