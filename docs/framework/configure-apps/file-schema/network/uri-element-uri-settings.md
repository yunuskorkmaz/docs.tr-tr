---
title: <uri> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
ms.openlocfilehash: a492baf9951466383ca0277a2927b8554e5bb332
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697434"
---
# <a name="uri-element-uri-settings"></a><span data-ttu-id="b2f6d-102">\<uri > öğesi (URI ayarları)</span><span class="sxs-lookup"><span data-stu-id="b2f6d-102">\<uri> Element (Uri Settings)</span></span>
<span data-ttu-id="b2f6d-103">.NET Framework Tekdüzen Kaynak tanımlayıcıları (URI 'Ler) kullanarak ifade edilen Web adreslerini nasıl işleyeceğini belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="b2f6d-103">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>  
  
[<span data-ttu-id="b2f6d-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="b2f6d-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="b2f6d-105">&nbsp; @ no__t-1 **\<uri >**</span><span class="sxs-lookup"><span data-stu-id="b2f6d-105">&nbsp;&nbsp;**\<uri>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2f6d-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b2f6d-106">Syntax</span></span>  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b2f6d-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b2f6d-107">Attributes and Elements</span></span>  
 <span data-ttu-id="b2f6d-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b2f6d-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b2f6d-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b2f6d-109">Attributes</span></span>  
 <span data-ttu-id="b2f6d-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="b2f6d-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b2f6d-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b2f6d-111">Child Elements</span></span>  
  
|<span data-ttu-id="b2f6d-112">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="b2f6d-112">**Element**</span></span>|<span data-ttu-id="b2f6d-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="b2f6d-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b2f6d-114">IDN</span><span class="sxs-lookup"><span data-stu-id="b2f6d-114">idn</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="b2f6d-115">Uluslararası etki alanı adı (ıDN) ayrıştırma 'nın etki alanı adlarına uygulandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2f6d-115">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="b2f6d-116">iriParsing</span><span class="sxs-lookup"><span data-stu-id="b2f6d-116">iriParsing</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="b2f6d-117">Uluslararası kaynak tanımlayıcı (IRI) ayrıştırma <xref:System.Uri> ' a uygulanıp uygulanmadığını ve IRI ayrıştırma kurallarının uygulanıp uygulanamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2f6d-117">Specifies if International Resource Identifier (IRI) parsing is applied to <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="b2f6d-118">schemeSettings</span><span class="sxs-lookup"><span data-stu-id="b2f6d-118">schemeSettings</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="b2f6d-119">Belirli düzenler için <xref:System.Uri> ' ın nasıl ayrıştıralınacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2f6d-119">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b2f6d-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b2f6d-120">Parent Elements</span></span>  
  
|<span data-ttu-id="b2f6d-121">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="b2f6d-121">**Element**</span></span>|<span data-ttu-id="b2f6d-122">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="b2f6d-122">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b2f6d-123">yapılandırmada</span><span class="sxs-lookup"><span data-stu-id="b2f6d-123">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="b2f6d-124">Tüm ad alanları için ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="b2f6d-124">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2f6d-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b2f6d-125">Remarks</span></span>  
 <span data-ttu-id="b2f6d-126">@No__t-0 öğesi, <xref:System.Net> ad alanındaki sınıflar tarafından kullanılan <xref:System.Uri> sınıfının üyelerine yönelik ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="b2f6d-126">The `uri` element contains settings for members of the <xref:System.Uri> class used by classes in the <xref:System.Net> namespace.</span></span> <span data-ttu-id="b2f6d-127">Ayarlar IRI ve ıDN desteğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="b2f6d-127">The settings configure support for IRI and IDN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2f6d-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="b2f6d-128">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="b2f6d-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b2f6d-129">Description</span></span>  
 <span data-ttu-id="b2f6d-130">Aşağıdaki örnekte, IRI ayrıştırma ve ıDN adlarını desteklemek için <xref:System.Uri> sınıfı tarafından kullanılan bir yapılandırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b2f6d-130">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span> <span data-ttu-id="b2f6d-131">Örnek, tüm düzen ayarlarını da temizler ve ardından http şeması için tam olmayan yüzde kodlamalı yol sınırlayıcıları için destek ekler.</span><span class="sxs-lookup"><span data-stu-id="b2f6d-131">The example also clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b2f6d-132">Kod</span><span class="sxs-lookup"><span data-stu-id="b2f6d-132">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b2f6d-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2f6d-133">See also</span></span>

- [<span data-ttu-id="b2f6d-134">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="b2f6d-134">Network Settings Schema</span></span>](index.md)
