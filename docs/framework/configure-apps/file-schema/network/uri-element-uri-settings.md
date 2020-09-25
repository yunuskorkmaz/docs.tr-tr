---
title: <uri> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
ms.openlocfilehash: 2f22d70407d10dbb38f0cb8d3a8ac74ff3fe8763
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190208"
---
# <a name="uri-element-uri-settings"></a><span data-ttu-id="54fae-102">\<uri> Öğesi (Uri Ayarları)</span><span class="sxs-lookup"><span data-stu-id="54fae-102">\<uri> Element (Uri Settings)</span></span>

<span data-ttu-id="54fae-103">.NET Framework Tekdüzen Kaynak tanımlayıcıları (URI 'Ler) kullanarak ifade edilen Web adreslerini nasıl işleyeceğini belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="54fae-103">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<uri>**  
  
## <a name="syntax"></a><span data-ttu-id="54fae-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="54fae-104">Syntax</span></span>  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="54fae-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="54fae-105">Attributes and Elements</span></span>  

 <span data-ttu-id="54fae-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="54fae-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="54fae-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="54fae-107">Attributes</span></span>  

 <span data-ttu-id="54fae-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="54fae-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="54fae-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="54fae-109">Child Elements</span></span>  
  
|<span data-ttu-id="54fae-110">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="54fae-110">**Element**</span></span>|<span data-ttu-id="54fae-111">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="54fae-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="54fae-112">IDN</span><span class="sxs-lookup"><span data-stu-id="54fae-112">idn</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="54fae-113">Uluslararası etki alanı adı (ıDN) ayrıştırma 'nın etki alanı adlarına uygulandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="54fae-113">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="54fae-114">iriParsing</span><span class="sxs-lookup"><span data-stu-id="54fae-114">iriParsing</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="54fae-115">Uluslararası kaynak tanımlayıcı (IRI) ayrıştırmanın uygulanıp uygulanmadığını <xref:System.Uri> ve IRI ayrıştırma kurallarının uygulanıp uygulanamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="54fae-115">Specifies if International Resource Identifier (IRI) parsing is applied to <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="54fae-116">schemeSettings</span><span class="sxs-lookup"><span data-stu-id="54fae-116">schemeSettings</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="54fae-117"><xref:System.Uri>Belirli düzenler için nasıl ayrıştırılacaksınız belirtir.</span><span class="sxs-lookup"><span data-stu-id="54fae-117">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="54fae-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="54fae-118">Parent Elements</span></span>  
  
|<span data-ttu-id="54fae-119">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="54fae-119">**Element**</span></span>|<span data-ttu-id="54fae-120">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="54fae-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="54fae-121">yapılandırmada</span><span class="sxs-lookup"><span data-stu-id="54fae-121">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="54fae-122">Tüm ad alanları için ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="54fae-122">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54fae-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="54fae-123">Remarks</span></span>  

 <span data-ttu-id="54fae-124">`uri`Öğesi, <xref:System.Uri> ad alanındaki sınıflar tarafından kullanılan sınıf üyeleri için ayarları içerir <xref:System.Net> .</span><span class="sxs-lookup"><span data-stu-id="54fae-124">The `uri` element contains settings for members of the <xref:System.Uri> class used by classes in the <xref:System.Net> namespace.</span></span> <span data-ttu-id="54fae-125">Ayarlar IRI ve ıDN desteğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="54fae-125">The settings configure support for IRI and IDN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54fae-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="54fae-126">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="54fae-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="54fae-127">Description</span></span>  

 <span data-ttu-id="54fae-128">Aşağıdaki örnek, <xref:System.Uri> IRI ayrıştırma ve IDN adlarını desteklemek için sınıfı tarafından kullanılan bir yapılandırmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="54fae-128">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span> <span data-ttu-id="54fae-129">Örnek, tüm düzen ayarlarını da temizler ve ardından http şeması için tam olmayan yüzde kodlamalı yol sınırlayıcıları için destek ekler.</span><span class="sxs-lookup"><span data-stu-id="54fae-129">The example also clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
### <a name="code"></a><span data-ttu-id="54fae-130">Kod</span><span class="sxs-lookup"><span data-stu-id="54fae-130">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="54fae-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54fae-131">See also</span></span>

- [<span data-ttu-id="54fae-132">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="54fae-132">Network Settings Schema</span></span>](index.md)
