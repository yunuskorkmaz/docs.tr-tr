---
title: <uri> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
ms.openlocfilehash: a492baf9951466383ca0277a2927b8554e5bb332
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "71697434"
---
# <a name="uri-element-uri-settings"></a><span data-ttu-id="edb7a-102">\<uri> Öğesi (Uri Ayarları)</span><span class="sxs-lookup"><span data-stu-id="edb7a-102">\<uri> Element (Uri Settings)</span></span>
<span data-ttu-id="edb7a-103">.NET Framework Tekdüzen Kaynak tanımlayıcıları (URI 'Ler) kullanarak ifade edilen Web adreslerini nasıl işleyeceğini belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="edb7a-103">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<uri>**  
  
## <a name="syntax"></a><span data-ttu-id="edb7a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="edb7a-104">Syntax</span></span>  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="edb7a-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="edb7a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="edb7a-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="edb7a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="edb7a-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="edb7a-107">Attributes</span></span>  
 <span data-ttu-id="edb7a-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="edb7a-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="edb7a-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="edb7a-109">Child Elements</span></span>  
  
|<span data-ttu-id="edb7a-110">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="edb7a-110">**Element**</span></span>|<span data-ttu-id="edb7a-111">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="edb7a-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="edb7a-112">IDN</span><span class="sxs-lookup"><span data-stu-id="edb7a-112">idn</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="edb7a-113">Uluslararası etki alanı adı (ıDN) ayrıştırma 'nın etki alanı adlarına uygulandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="edb7a-113">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="edb7a-114">iriParsing</span><span class="sxs-lookup"><span data-stu-id="edb7a-114">iriParsing</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="edb7a-115">Uluslararası kaynak tanımlayıcı (IRI) ayrıştırmanın uygulanıp uygulanmadığını <xref:System.Uri> ve IRI ayrıştırma kurallarının uygulanıp uygulanamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="edb7a-115">Specifies if International Resource Identifier (IRI) parsing is applied to <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="edb7a-116">schemeSettings</span><span class="sxs-lookup"><span data-stu-id="edb7a-116">schemeSettings</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="edb7a-117"><xref:System.Uri>Belirli düzenler için nasıl ayrıştırılacaksınız belirtir.</span><span class="sxs-lookup"><span data-stu-id="edb7a-117">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="edb7a-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="edb7a-118">Parent Elements</span></span>  
  
|<span data-ttu-id="edb7a-119">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="edb7a-119">**Element**</span></span>|<span data-ttu-id="edb7a-120">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="edb7a-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="edb7a-121">yapılandırmada</span><span class="sxs-lookup"><span data-stu-id="edb7a-121">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="edb7a-122">Tüm ad alanları için ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="edb7a-122">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="edb7a-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="edb7a-123">Remarks</span></span>  
 <span data-ttu-id="edb7a-124">`uri`Öğesi, <xref:System.Uri> ad alanındaki sınıflar tarafından kullanılan sınıf üyeleri için ayarları içerir <xref:System.Net> .</span><span class="sxs-lookup"><span data-stu-id="edb7a-124">The `uri` element contains settings for members of the <xref:System.Uri> class used by classes in the <xref:System.Net> namespace.</span></span> <span data-ttu-id="edb7a-125">Ayarlar IRI ve ıDN desteğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="edb7a-125">The settings configure support for IRI and IDN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="edb7a-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="edb7a-126">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="edb7a-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="edb7a-127">Description</span></span>  
 <span data-ttu-id="edb7a-128">Aşağıdaki örnek, <xref:System.Uri> IRI ayrıştırma ve IDN adlarını desteklemek için sınıfı tarafından kullanılan bir yapılandırmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="edb7a-128">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span> <span data-ttu-id="edb7a-129">Örnek, tüm düzen ayarlarını da temizler ve ardından http şeması için tam olmayan yüzde kodlamalı yol sınırlayıcıları için destek ekler.</span><span class="sxs-lookup"><span data-stu-id="edb7a-129">The example also clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
### <a name="code"></a><span data-ttu-id="edb7a-130">Kod</span><span class="sxs-lookup"><span data-stu-id="edb7a-130">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="edb7a-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="edb7a-131">See also</span></span>

- [<span data-ttu-id="edb7a-132">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="edb7a-132">Network Settings Schema</span></span>](index.md)
