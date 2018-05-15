---
title: '&lt;kaldırma&gt; öğesi schemeSettings (URI ayarları) için'
ms.date: 03/30/2017
ms.assetid: 4095ba51-de20-4f87-b562-018abe422c91
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 8e01f82a476286e27129e4b1a47fefc1ac77c2b5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltremovegt-element-for-schemesettings-uri-settings"></a><span data-ttu-id="6862f-102">&lt;kaldırma&gt; öğesi schemeSettings (URI ayarları) için</span><span class="sxs-lookup"><span data-stu-id="6862f-102">&lt;remove&gt; Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="6862f-103">Düzen adı için bir düzeni ayarı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="6862f-103">Removes a scheme setting for a scheme name.</span></span>  
  
 <span data-ttu-id="6862f-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="6862f-104">\<configuration></span></span>  
<span data-ttu-id="6862f-105">\<URI ></span><span class="sxs-lookup"><span data-stu-id="6862f-105">\<uri></span></span>  
<span data-ttu-id="6862f-106">\<schemeSettings ></span><span class="sxs-lookup"><span data-stu-id="6862f-106">\<schemeSettings></span></span>  
<span data-ttu-id="6862f-107">\<kaldırma ></span><span class="sxs-lookup"><span data-stu-id="6862f-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6862f-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6862f-108">Syntax</span></span>  
  
```xml  
<remove
  name="http|https"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6862f-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6862f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6862f-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6862f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6862f-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6862f-111">Attributes</span></span>  
  
|<span data-ttu-id="6862f-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6862f-112">Attribute</span></span>|<span data-ttu-id="6862f-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6862f-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6862f-114">name</span><span class="sxs-lookup"><span data-stu-id="6862f-114">name</span></span>|<span data-ttu-id="6862f-115">Bu ayar geçerli olduğu için Düzen adı.</span><span class="sxs-lookup"><span data-stu-id="6862f-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="6862f-116">Yalnızca desteklenen değerler name = "http" ve ad = "https".</span><span class="sxs-lookup"><span data-stu-id="6862f-116">The only supported values are name="http" and name="https".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6862f-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6862f-117">Child Elements</span></span>  
 <span data-ttu-id="6862f-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="6862f-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6862f-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6862f-119">Parent Elements</span></span>  
  
|<span data-ttu-id="6862f-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="6862f-120">Element</span></span>|<span data-ttu-id="6862f-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6862f-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6862f-122">\<schemeSettings > öğesi (URI ayarları)</span><span class="sxs-lookup"><span data-stu-id="6862f-122">\<schemeSettings> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="6862f-123">Belirtir nasıl bir <xref:System.Uri> için belirli düzenleri ayrıştırılır.</span><span class="sxs-lookup"><span data-stu-id="6862f-123">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6862f-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6862f-124">Remarks</span></span>  
 <span data-ttu-id="6862f-125">Varsayılan olarak, <xref:System.Uri?displayProperty=nameWithType> sınıfı kaydını çıkışları yüzde yolu sıkıştırma yürütmeden önce yolu ayırıcısı kodlanmış.</span><span class="sxs-lookup"><span data-stu-id="6862f-125">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="6862f-126">Bu, aşağıdaki gibi saldırılarına karşı bir güvenlik mekanizması olarak kullanılmıştır:</span><span class="sxs-lookup"><span data-stu-id="6862f-126">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="6862f-127">Bu URI aktarılırsa modülleri aşağıya doğru yüzde işlenmemesinin karakterlerin doğru kodlanmış, sunucu tarafından yürütülen aşağıdaki komutta neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="6862f-127">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="6862f-128">Bu nedenle, <xref:System.Uri?displayProperty=nameWithType> sınıfı ilk kaydını çıkışları yol ayırıcısı ve yol sıkıştırma uygular.</span><span class="sxs-lookup"><span data-stu-id="6862f-128">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="6862f-129">Yukarıdaki kötü amaçlı URL'sine geçirme sonucunu <xref:System.Uri?displayProperty=nameWithType> sınıfı aşağıdaki URI Oluşturucusu sonuçlanır:</span><span class="sxs-lookup"><span data-stu-id="6862f-129">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="6862f-130">Bu varsayılan davranışı değil, özel şema için schemeSettings yapılandırma seçeneğini kullanarak kaldırın kaçış yüzde kodlanmış yolu sınırlayıcıları için değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="6862f-130">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="6862f-131">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="6862f-131">Configuration Files</span></span>  
 <span data-ttu-id="6862f-132">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6862f-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6862f-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="6862f-133">Example</span></span>  
 <span data-ttu-id="6862f-134">Aşağıdaki örnek tarafından kullanılan bir yapılandırma gösterir <xref:System.Uri> http düzenini düzeni ayarlarını kaldırır sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6862f-134">The following example shows a configuration used by the <xref:System.Uri> class that removes any scheme settings for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <remove name="http"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6862f-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6862f-135">See Also</span></span>  
 <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>  
 <xref:System.GenericUriParserOptions?displayProperty=nameWithType>  
 <xref:System.Uri?displayProperty=nameWithType>  
 [<span data-ttu-id="6862f-136">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="6862f-136">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
