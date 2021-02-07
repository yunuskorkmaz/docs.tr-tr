---
description: 'Daha fazla bilgi edinin: <uri> öğesi (URI ayarları)'
title: <uri> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
ms.openlocfilehash: dc30778fdf5babfb87da0e32829ed9a3ae412c2e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740125"
---
# <a name="uri-element-uri-settings"></a><span data-ttu-id="fadd4-103">\<uri> Öğesi (Uri Ayarları)</span><span class="sxs-lookup"><span data-stu-id="fadd4-103">\<uri> Element (Uri Settings)</span></span>

<span data-ttu-id="fadd4-104">.NET Framework Tekdüzen Kaynak tanımlayıcıları (URI 'Ler) kullanarak ifade edilen Web adreslerini nasıl işleyeceğini belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="fadd4-104">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<uri>**  
  
## <a name="syntax"></a><span data-ttu-id="fadd4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="fadd4-105">Syntax</span></span>  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fadd4-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fadd4-106">Attributes and Elements</span></span>  

 <span data-ttu-id="fadd4-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fadd4-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fadd4-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fadd4-108">Attributes</span></span>  

 <span data-ttu-id="fadd4-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="fadd4-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fadd4-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fadd4-110">Child Elements</span></span>  
  
|<span data-ttu-id="fadd4-111">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="fadd4-111">**Element**</span></span>|<span data-ttu-id="fadd4-112">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="fadd4-112">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="fadd4-113">IDN</span><span class="sxs-lookup"><span data-stu-id="fadd4-113">idn</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="fadd4-114">Uluslararası etki alanı adı (ıDN) ayrıştırma 'nın etki alanı adlarına uygulandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fadd4-114">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="fadd4-115">iriParsing</span><span class="sxs-lookup"><span data-stu-id="fadd4-115">iriParsing</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="fadd4-116">Uluslararası kaynak tanımlayıcı (IRI) ayrıştırmanın uygulanıp uygulanmadığını <xref:System.Uri> ve IRI ayrıştırma kurallarının uygulanıp uygulanamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fadd4-116">Specifies if International Resource Identifier (IRI) parsing is applied to <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="fadd4-117">schemeSettings</span><span class="sxs-lookup"><span data-stu-id="fadd4-117">schemeSettings</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="fadd4-118"><xref:System.Uri>Belirli düzenler için nasıl ayrıştırılacaksınız belirtir.</span><span class="sxs-lookup"><span data-stu-id="fadd4-118">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fadd4-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fadd4-119">Parent Elements</span></span>  
  
|<span data-ttu-id="fadd4-120">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="fadd4-120">**Element**</span></span>|<span data-ttu-id="fadd4-121">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="fadd4-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="fadd4-122">yapılandırmada</span><span class="sxs-lookup"><span data-stu-id="fadd4-122">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="fadd4-123">Tüm ad alanları için ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="fadd4-123">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fadd4-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fadd4-124">Remarks</span></span>  

 <span data-ttu-id="fadd4-125">`uri`Öğesi, <xref:System.Uri> ad alanındaki sınıflar tarafından kullanılan sınıf üyeleri için ayarları içerir <xref:System.Net> .</span><span class="sxs-lookup"><span data-stu-id="fadd4-125">The `uri` element contains settings for members of the <xref:System.Uri> class used by classes in the <xref:System.Net> namespace.</span></span> <span data-ttu-id="fadd4-126">Ayarlar IRI ve ıDN desteğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="fadd4-126">The settings configure support for IRI and IDN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fadd4-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="fadd4-127">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="fadd4-128">Description</span><span class="sxs-lookup"><span data-stu-id="fadd4-128">Description</span></span>  

 <span data-ttu-id="fadd4-129">Aşağıdaki örnek, <xref:System.Uri> IRI ayrıştırma ve IDN adlarını desteklemek için sınıfı tarafından kullanılan bir yapılandırmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="fadd4-129">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span> <span data-ttu-id="fadd4-130">Örnek, tüm düzen ayarlarını da temizler ve ardından http şeması için tam olmayan yüzde kodlamalı yol sınırlayıcıları için destek ekler.</span><span class="sxs-lookup"><span data-stu-id="fadd4-130">The example also clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
### <a name="code"></a><span data-ttu-id="fadd4-131">Kod</span><span class="sxs-lookup"><span data-stu-id="fadd4-131">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fadd4-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fadd4-132">See also</span></span>

- [<span data-ttu-id="fadd4-133">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="fadd4-133">Network Settings Schema</span></span>](index.md)
