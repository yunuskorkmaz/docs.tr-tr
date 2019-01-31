---
title: schemeSettings için <remove> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: 4095ba51-de20-4f87-b562-018abe422c91
ms.openlocfilehash: fd137c86d7373947f57364c13eb3875cba46b269
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55262651"
---
# <a name="remove-element-for-schemesettings-uri-settings"></a><span data-ttu-id="8e09d-102">\<kaldırma > öğesi (Uri ayarları) schemeSettings için</span><span class="sxs-lookup"><span data-stu-id="8e09d-102">\<remove> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="8e09d-103">Düzen adı için bir düzen ayarı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="8e09d-103">Removes a scheme setting for a scheme name.</span></span>  
  
 <span data-ttu-id="8e09d-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="8e09d-104">\<configuration></span></span>  
<span data-ttu-id="8e09d-105">\<URI ></span><span class="sxs-lookup"><span data-stu-id="8e09d-105">\<uri></span></span>  
<span data-ttu-id="8e09d-106">\<schemeSettings ></span><span class="sxs-lookup"><span data-stu-id="8e09d-106">\<schemeSettings></span></span>  
<span data-ttu-id="8e09d-107">\<kaldırma ></span><span class="sxs-lookup"><span data-stu-id="8e09d-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e09d-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8e09d-108">Syntax</span></span>  
  
```xml  
<remove
  name="http|https"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8e09d-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8e09d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8e09d-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8e09d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8e09d-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8e09d-111">Attributes</span></span>  
  
|<span data-ttu-id="8e09d-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8e09d-112">Attribute</span></span>|<span data-ttu-id="8e09d-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8e09d-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8e09d-114">name</span><span class="sxs-lookup"><span data-stu-id="8e09d-114">name</span></span>|<span data-ttu-id="8e09d-115">Bu ayarın geçerli olduğu için Düzen adı.</span><span class="sxs-lookup"><span data-stu-id="8e09d-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="8e09d-116">Desteklenen değerler şunlardır: adı yalnızca "http" ve name = "https".</span><span class="sxs-lookup"><span data-stu-id="8e09d-116">The only supported values are name="http" and name="https".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8e09d-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8e09d-117">Child Elements</span></span>  
 <span data-ttu-id="8e09d-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="8e09d-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8e09d-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8e09d-119">Parent Elements</span></span>  
  
|<span data-ttu-id="8e09d-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="8e09d-120">Element</span></span>|<span data-ttu-id="8e09d-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8e09d-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8e09d-122">\<schemeSettings > öğesi (Uri ayarları)</span><span class="sxs-lookup"><span data-stu-id="8e09d-122">\<schemeSettings> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="8e09d-123">Belirtir nasıl bir <xref:System.Uri> belirli düzenleri için ayrıştırılacak.</span><span class="sxs-lookup"><span data-stu-id="8e09d-123">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e09d-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8e09d-124">Remarks</span></span>  
 <span data-ttu-id="8e09d-125">Varsayılan olarak, <xref:System.Uri?displayProperty=nameWithType> sınıfı Geri Al çıkışları yüzde yolu sınırlayıcı yolu sıkıştırma yürütmeden önce kodlanmış.</span><span class="sxs-lookup"><span data-stu-id="8e09d-125">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="8e09d-126">Bu, aşağıdaki gibi saldırılarına karşı bir güvenlik mekanizması olarak uygulanmıştır:</span><span class="sxs-lookup"><span data-stu-id="8e09d-126">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="8e09d-127">Bu URI iletilir aşağı modülleri yüzde işlenmemesinin karakterlerin doğru kodlanmış, sunucu tarafından çalıştırılan aşağıdaki komutu neden:</span><span class="sxs-lookup"><span data-stu-id="8e09d-127">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="8e09d-128">Bu nedenle, <xref:System.Uri?displayProperty=nameWithType> sınıf ilk geri al çıkışları yol ayırıcıları ve yol sıkıştırma uygular.</span><span class="sxs-lookup"><span data-stu-id="8e09d-128">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="8e09d-129">Yukarıda kötü amaçlı URL'sini geçirme sonucunu <xref:System.Uri?displayProperty=nameWithType> sınıf oluşturucu sonuçları aşağıdaki URI:</span><span class="sxs-lookup"><span data-stu-id="8e09d-129">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="8e09d-130">Bu varsayılan davranışı değil, için belirli bir düzeni schemeSettings yapılandırma seçeneğini kullanarak kaldırın kaçış yüzde kodlanmış yolu sınırlayıcılar için değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8e09d-130">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="8e09d-131">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="8e09d-131">Configuration Files</span></span>  
 <span data-ttu-id="8e09d-132">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8e09d-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e09d-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e09d-133">Example</span></span>  
 <span data-ttu-id="8e09d-134">Aşağıdaki örnek tarafından kullanılan bir yapılandırma gösterir <xref:System.Uri> http düzeni düzeni ayarlarını silen sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8e09d-134">The following example shows a configuration used by the <xref:System.Uri> class that removes any scheme settings for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <remove name="http"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8e09d-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e09d-135">See also</span></span>
- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="8e09d-136">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="8e09d-136">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
