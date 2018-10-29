---
title: '&lt;ekleme&gt; schemeSettings (Uri ayarları) için'
ms.date: 03/30/2017
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
ms.openlocfilehash: 07bcaf470c68a4d400057b0fe19e96524b2859cb
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50205184"
---
# <a name="ltaddgt-element-for-schemesettings-uri-settings"></a><span data-ttu-id="19013-102">&lt;ekleme&gt; schemeSettings (Uri ayarları) için</span><span class="sxs-lookup"><span data-stu-id="19013-102">&lt;add&gt; Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="19013-103">Düzen adı için bir düzen ayarı ekler.</span><span class="sxs-lookup"><span data-stu-id="19013-103">Adds a scheme setting for a scheme name.</span></span>  
  
 <span data-ttu-id="19013-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="19013-104">\<configuration></span></span>  
<span data-ttu-id="19013-105">\<URI ></span><span class="sxs-lookup"><span data-stu-id="19013-105">\<uri></span></span>  
<span data-ttu-id="19013-106">\<schemeSettings ></span><span class="sxs-lookup"><span data-stu-id="19013-106">\<schemeSettings></span></span>  
<span data-ttu-id="19013-107">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="19013-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19013-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="19013-108">Syntax</span></span>  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="19013-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="19013-109">Attributes and Elements</span></span>  
 <span data-ttu-id="19013-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="19013-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="19013-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="19013-111">Attributes</span></span>  
  
|<span data-ttu-id="19013-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="19013-112">Attribute</span></span>|<span data-ttu-id="19013-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="19013-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="19013-114">name</span><span class="sxs-lookup"><span data-stu-id="19013-114">name</span></span>|<span data-ttu-id="19013-115">Bu ayarın geçerli olduğu için Düzen adı.</span><span class="sxs-lookup"><span data-stu-id="19013-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="19013-116">Desteklenen değerler şunlardır: adı yalnızca "http" ve name = "https".</span><span class="sxs-lookup"><span data-stu-id="19013-116">The only supported values are name="http" and name="https".</span></span>|  
  
## <a name="attribute-name-attribute"></a><span data-ttu-id="19013-117">{Öznitelik adı} Özniteliği</span><span class="sxs-lookup"><span data-stu-id="19013-117">{Attribute name} Attribute</span></span>  
  
|<span data-ttu-id="19013-118">Değer</span><span class="sxs-lookup"><span data-stu-id="19013-118">Value</span></span>|<span data-ttu-id="19013-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="19013-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="19013-120">genericUriParserOptions</span><span class="sxs-lookup"><span data-stu-id="19013-120">genericUriParserOptions</span></span>|<span data-ttu-id="19013-121">Bu düzen ayrıştırıcısı seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="19013-121">The parser options for this scheme.</span></span> <span data-ttu-id="19013-122">Yalnızca desteklenen değer genericUriParserOptions "DontUnescapePathDotsAndSlashes" =.</span><span class="sxs-lookup"><span data-stu-id="19013-122">The only supported value is genericUriParserOptions= "DontUnescapePathDotsAndSlashes".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="19013-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="19013-123">Child Elements</span></span>  
 <span data-ttu-id="19013-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="19013-124">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="19013-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="19013-125">Parent Elements</span></span>  
  
|<span data-ttu-id="19013-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="19013-126">Element</span></span>|<span data-ttu-id="19013-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="19013-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="19013-128">\<schemeSettings > öğesi (Uri ayarları)</span><span class="sxs-lookup"><span data-stu-id="19013-128">\<schemeSettings> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="19013-129">Belirtir nasıl bir <xref:System.Uri> belirli düzenleri için ayrıştırılacak.</span><span class="sxs-lookup"><span data-stu-id="19013-129">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19013-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="19013-130">Remarks</span></span>  
 <span data-ttu-id="19013-131">Varsayılan olarak, <xref:System.Uri?displayProperty=nameWithType> sınıfı Geri Al çıkışları yüzde yolu sınırlayıcı yolu sıkıştırma yürütmeden önce kodlanmış.</span><span class="sxs-lookup"><span data-stu-id="19013-131">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="19013-132">Bu, aşağıdaki gibi saldırılarına karşı bir güvenlik mekanizması olarak uygulanmıştır:</span><span class="sxs-lookup"><span data-stu-id="19013-132">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="19013-133">Bu URI iletilir aşağı modülleri yüzde işlenmemesinin karakterlerin doğru kodlanmış, sunucu tarafından çalıştırılan aşağıdaki komutu neden:</span><span class="sxs-lookup"><span data-stu-id="19013-133">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="19013-134">Bu nedenle, <xref:System.Uri?displayProperty=nameWithType> sınıf ilk geri al çıkışları yol ayırıcıları ve yol sıkıştırma uygular.</span><span class="sxs-lookup"><span data-stu-id="19013-134">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="19013-135">Yukarıda kötü amaçlı URL'sini geçirme sonucunu <xref:System.Uri?displayProperty=nameWithType> sınıf oluşturucu sonuçları aşağıdaki URI:</span><span class="sxs-lookup"><span data-stu-id="19013-135">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="19013-136">Bu varsayılan davranışı değil, için belirli bir düzeni schemeSettings yapılandırma seçeneğini kullanarak kaldırın kaçış yüzde kodlanmış yolu sınırlayıcılar için değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="19013-136">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="19013-137">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="19013-137">Configuration Files</span></span>  
 <span data-ttu-id="19013-138">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="19013-138">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="19013-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="19013-139">Example</span></span>  
 <span data-ttu-id="19013-140">Aşağıdaki örnek tarafından kullanılan bir yapılandırma gösterir <xref:System.Uri> http düzeni için yol yüzde olarak kodlanmış sınırlayıcılar kaçış değil desteklemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="19013-140">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="19013-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="19013-141">See Also</span></span>  
- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>  
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>  
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>  
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>  
- <xref:System.Uri?displayProperty=nameWithType>  
- [<span data-ttu-id="19013-142">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="19013-142">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
