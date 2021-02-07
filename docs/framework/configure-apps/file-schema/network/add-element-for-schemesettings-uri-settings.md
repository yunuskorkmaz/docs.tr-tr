---
description: 'Hakkında daha fazla bilgi edinin: <add> ıviewmesettings için öğesi (Uri Ayarları)'
title: schemeSettings için <add> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
ms.openlocfilehash: c372577af1c7fbfe669455b50c8b55c82da4fc52
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698627"
---
# <a name="add-element-for-schemesettings-uri-settings"></a><span data-ttu-id="31c8f-103">schemeSettings için \<add> Öğesi (Uri Ayarları)</span><span class="sxs-lookup"><span data-stu-id="31c8f-103">\<add> Element for schemeSettings (Uri Settings)</span></span>

<span data-ttu-id="31c8f-104">Düzen adı için bir düzen ayarı ekler.</span><span class="sxs-lookup"><span data-stu-id="31c8f-104">Adds a scheme setting for a scheme name.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="31c8f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="31c8f-105">Syntax</span></span>  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="31c8f-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="31c8f-106">Attributes and Elements</span></span>  

 <span data-ttu-id="31c8f-107">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="31c8f-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="31c8f-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="31c8f-108">Attributes</span></span>  
  
|<span data-ttu-id="31c8f-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="31c8f-109">Attribute</span></span>|<span data-ttu-id="31c8f-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="31c8f-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="31c8f-111">name</span><span class="sxs-lookup"><span data-stu-id="31c8f-111">name</span></span>|<span data-ttu-id="31c8f-112">Bu ayarın geçerli olduğu Düzen adı.</span><span class="sxs-lookup"><span data-stu-id="31c8f-112">The scheme name for which this setting applies.</span></span> <span data-ttu-id="31c8f-113">Yalnızca Name = "http" ve Name = "https" değerleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="31c8f-113">The only supported values are name="http" and name="https".</span></span>|  
  
## <a name="attribute-name-attribute"></a><span data-ttu-id="31c8f-114">{Öznitelik adı} Özniteliğe</span><span class="sxs-lookup"><span data-stu-id="31c8f-114">{Attribute name} Attribute</span></span>  
  
|<span data-ttu-id="31c8f-115">Değer</span><span class="sxs-lookup"><span data-stu-id="31c8f-115">Value</span></span>|<span data-ttu-id="31c8f-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="31c8f-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="31c8f-117">genericUriParserOptions</span><span class="sxs-lookup"><span data-stu-id="31c8f-117">genericUriParserOptions</span></span>|<span data-ttu-id="31c8f-118">Bu şema için ayrıştırıcı seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="31c8f-118">The parser options for this scheme.</span></span> <span data-ttu-id="31c8f-119">Yalnızca genericUriParserOptions = "DontUnescapePathDotsAndSlashes" değeri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="31c8f-119">The only supported value is genericUriParserOptions= "DontUnescapePathDotsAndSlashes".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="31c8f-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="31c8f-120">Child Elements</span></span>  

 <span data-ttu-id="31c8f-121">Yok</span><span class="sxs-lookup"><span data-stu-id="31c8f-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="31c8f-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="31c8f-122">Parent Elements</span></span>  
  
|<span data-ttu-id="31c8f-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="31c8f-123">Element</span></span>|<span data-ttu-id="31c8f-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="31c8f-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="31c8f-125">\<schemeSettings> Öğesi (URI ayarları)</span><span class="sxs-lookup"><span data-stu-id="31c8f-125">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="31c8f-126"><xref:System.Uri>Belirli düzenler için nasıl ayrıştırılacaksınız belirtir.</span><span class="sxs-lookup"><span data-stu-id="31c8f-126">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31c8f-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="31c8f-127">Remarks</span></span>  

 <span data-ttu-id="31c8f-128">Varsayılan olarak, <xref:System.Uri?displayProperty=nameWithType> sınıfı yol sıkıştırmayı yürütmeden önce, yüzde olarak kodlanmış yol sınırlayıcılarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="31c8f-128">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="31c8f-129">Bu, aşağıdaki gibi saldırılara karşı bir güvenlik mekanizması olarak uygulanmıştır:</span><span class="sxs-lookup"><span data-stu-id="31c8f-129">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="31c8f-130">Bu URI, yüzde kodlamalı karakterleri doğru şekilde işlemeyen modüllere geçiriliyorsa, aşağıdaki komut sunucu tarafından yürütülebilmesiyle sonuçlanabilir:</span><span class="sxs-lookup"><span data-stu-id="31c8f-130">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="31c8f-131">Bu nedenle, <xref:System.Uri?displayProperty=nameWithType> sınıf ilk olarak yol sınırlayıcılarını iptal eder ve yol sıkıştırması uygular.</span><span class="sxs-lookup"><span data-stu-id="31c8f-131">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="31c8f-132">Yukarıdaki kötü amaçlı URL 'YI sınıf oluşturucusuna geçirmenin sonucu <xref:System.Uri?displayProperty=nameWithType> AŞAĞıDAKI URI ile sonuçlanır:</span><span class="sxs-lookup"><span data-stu-id="31c8f-132">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="31c8f-133">Bu varsayılan davranış, belirli bir düzen için ıgmesettings yapılandırma seçeneği kullanılarak yüzde olmayan kodlanmış yol sınırlayıcılarını kaçırılmamış şekilde değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="31c8f-133">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="31c8f-134">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="31c8f-134">Configuration Files</span></span>  

 <span data-ttu-id="31c8f-135">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="31c8f-135">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="31c8f-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="31c8f-136">Example</span></span>  

 <span data-ttu-id="31c8f-137">Aşağıdaki örnek, <xref:System.Uri> http şeması için yüzde kodlamalı bir yol sınırlayıcılarını yok etmek üzere sınıfı tarafından kullanılan bir yapılandırmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="31c8f-137">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="31c8f-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31c8f-138">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="31c8f-139">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="31c8f-139">Network Settings Schema</span></span>](index.md)
