---
title: '&lt;ekleme&gt; öğesi schemeSettings (URI ayarları) için'
ms.date: 03/30/2017
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: bd8033b07b29066633e5217645f3ee06937179da
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-element-for-schemesettings-uri-settings"></a><span data-ttu-id="f2dd6-102">&lt;ekleme&gt; öğesi schemeSettings (URI ayarları) için</span><span class="sxs-lookup"><span data-stu-id="f2dd6-102">&lt;add&gt; Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="f2dd6-103">Düzen adı için bir düzeni ayarı ekler.</span><span class="sxs-lookup"><span data-stu-id="f2dd6-103">Adds a scheme setting for a scheme name.</span></span>  
  
 <span data-ttu-id="f2dd6-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="f2dd6-104">\<configuration></span></span>  
<span data-ttu-id="f2dd6-105">\<URI ></span><span class="sxs-lookup"><span data-stu-id="f2dd6-105">\<uri></span></span>  
<span data-ttu-id="f2dd6-106">\<schemeSettings ></span><span class="sxs-lookup"><span data-stu-id="f2dd6-106">\<schemeSettings></span></span>  
<span data-ttu-id="f2dd6-107">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="f2dd6-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2dd6-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2dd6-108">Syntax</span></span>  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f2dd6-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2dd6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f2dd6-110">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="f2dd6-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f2dd6-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f2dd6-111">Attributes</span></span>  
  
|<span data-ttu-id="f2dd6-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f2dd6-112">Attribute</span></span>|<span data-ttu-id="f2dd6-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2dd6-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f2dd6-114">name</span><span class="sxs-lookup"><span data-stu-id="f2dd6-114">name</span></span>|<span data-ttu-id="f2dd6-115">Bu ayar geçerli olduğu için Düzen adı.</span><span class="sxs-lookup"><span data-stu-id="f2dd6-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="f2dd6-116">Yalnızca desteklenen değerler name = "http" ve ad = "https".</span><span class="sxs-lookup"><span data-stu-id="f2dd6-116">The only supported values are name="http" and name="https".</span></span>|  
  
## <a name="attribute-name-attribute"></a><span data-ttu-id="f2dd6-117">{Öznitelik adı} Özniteliği</span><span class="sxs-lookup"><span data-stu-id="f2dd6-117">{Attribute name} Attribute</span></span>  
  
|<span data-ttu-id="f2dd6-118">Değer</span><span class="sxs-lookup"><span data-stu-id="f2dd6-118">Value</span></span>|<span data-ttu-id="f2dd6-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2dd6-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f2dd6-120">genericUriParserOptions</span><span class="sxs-lookup"><span data-stu-id="f2dd6-120">genericUriParserOptions</span></span>|<span data-ttu-id="f2dd6-121">Bu düzen ayrıştırıcı seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="f2dd6-121">The parser options for this scheme.</span></span> <span data-ttu-id="f2dd6-122">Desteklenen genericUriParserOptions tek değer "DontUnescapePathDotsAndSlashes" =.</span><span class="sxs-lookup"><span data-stu-id="f2dd6-122">The only supported value is genericUriParserOptions= "DontUnescapePathDotsAndSlashes".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f2dd6-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2dd6-123">Child Elements</span></span>  
 <span data-ttu-id="f2dd6-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="f2dd6-124">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f2dd6-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2dd6-125">Parent Elements</span></span>  
  
|<span data-ttu-id="f2dd6-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="f2dd6-126">Element</span></span>|<span data-ttu-id="f2dd6-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2dd6-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f2dd6-128">\<schemeSettings > öğesi (URI ayarları)</span><span class="sxs-lookup"><span data-stu-id="f2dd6-128">\<schemeSettings> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="f2dd6-129">Belirtir nasıl bir <xref:System.Uri> için belirli düzenleri ayrıştırılır.</span><span class="sxs-lookup"><span data-stu-id="f2dd6-129">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2dd6-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f2dd6-130">Remarks</span></span>  
 <span data-ttu-id="f2dd6-131">Varsayılan olarak, <xref:System.Uri?displayProperty=nameWithType> sınıfı kaydını çıkışları yüzde yolu sıkıştırma yürütmeden önce yolu ayırıcısı kodlanmış.</span><span class="sxs-lookup"><span data-stu-id="f2dd6-131">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="f2dd6-132">Bu, aşağıdaki gibi saldırılarına karşı bir güvenlik mekanizması olarak kullanılmıştır:</span><span class="sxs-lookup"><span data-stu-id="f2dd6-132">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="f2dd6-133">Bu URI aktarılırsa modülleri aşağıya doğru yüzde işlenmemesinin karakterlerin doğru kodlanmış, sunucu tarafından yürütülen aşağıdaki komutta neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="f2dd6-133">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="f2dd6-134">Bu nedenle, <xref:System.Uri?displayProperty=nameWithType> sınıfı ilk kaydını çıkışları yol ayırıcısı ve yol sıkıştırma uygular.</span><span class="sxs-lookup"><span data-stu-id="f2dd6-134">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="f2dd6-135">Yukarıdaki kötü amaçlı URL'sine geçirme sonucunu <xref:System.Uri?displayProperty=nameWithType> sınıfı aşağıdaki URI Oluşturucusu sonuçlanır:</span><span class="sxs-lookup"><span data-stu-id="f2dd6-135">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="f2dd6-136">Bu varsayılan davranışı değil, özel şema için schemeSettings yapılandırma seçeneğini kullanarak kaldırın kaçış yüzde kodlanmış yolu sınırlayıcıları için değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="f2dd6-136">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="f2dd6-137">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="f2dd6-137">Configuration Files</span></span>  
 <span data-ttu-id="f2dd6-138">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f2dd6-138">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2dd6-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="f2dd6-139">Example</span></span>  
 <span data-ttu-id="f2dd6-140">Aşağıdaki örnek tarafından kullanılan bir yapılandırma gösterir <xref:System.Uri> http şeması için yüzde olarak kodlanmış yol ayırıcısı kaçış değil desteklemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="f2dd6-140">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f2dd6-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f2dd6-141">See Also</span></span>  
 <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>  
 <xref:System.GenericUriParserOptions?displayProperty=nameWithType>  
 <xref:System.Uri?displayProperty=nameWithType>  
 [<span data-ttu-id="f2dd6-142">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="f2dd6-142">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
