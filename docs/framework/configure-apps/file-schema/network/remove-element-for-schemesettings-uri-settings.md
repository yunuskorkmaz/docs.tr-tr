---
title: schemeSettings için <remove> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: 4095ba51-de20-4f87-b562-018abe422c91
ms.openlocfilehash: faf254174527ea74638442a139841eb2365d1e5d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74089155"
---
# <a name="remove-element-for-schemesettings-uri-settings"></a><span data-ttu-id="352d8-102">schemeSettings için \<remove> Öğesi (Uri Ayarları)</span><span class="sxs-lookup"><span data-stu-id="352d8-102">\<remove> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="352d8-103">Düzen adı için bir düzen ayarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="352d8-103">Removes a scheme setting for a scheme name.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="352d8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="352d8-104">Syntax</span></span>  
  
```xml  
<remove
  name="http|https"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="352d8-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="352d8-105">Attributes and Elements</span></span>  
 <span data-ttu-id="352d8-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="352d8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="352d8-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="352d8-107">Attributes</span></span>  
  
|<span data-ttu-id="352d8-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="352d8-108">Attribute</span></span>|<span data-ttu-id="352d8-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="352d8-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="352d8-110">name</span><span class="sxs-lookup"><span data-stu-id="352d8-110">name</span></span>|<span data-ttu-id="352d8-111">Bu ayarın geçerli olduğu Düzen adı.</span><span class="sxs-lookup"><span data-stu-id="352d8-111">The scheme name for which this setting applies.</span></span> <span data-ttu-id="352d8-112">Yalnızca Name = "http" ve Name = "https" değerleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="352d8-112">The only supported values are name="http" and name="https".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="352d8-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="352d8-113">Child Elements</span></span>  
 <span data-ttu-id="352d8-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="352d8-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="352d8-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="352d8-115">Parent Elements</span></span>  
  
|<span data-ttu-id="352d8-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="352d8-116">Element</span></span>|<span data-ttu-id="352d8-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="352d8-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="352d8-118">\<schemeSettings>Öğesi (URI ayarları)</span><span class="sxs-lookup"><span data-stu-id="352d8-118">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="352d8-119"><xref:System.Uri>Belirli düzenler için nasıl ayrıştırılacaksınız belirtir.</span><span class="sxs-lookup"><span data-stu-id="352d8-119">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="352d8-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="352d8-120">Remarks</span></span>  
 <span data-ttu-id="352d8-121">Varsayılan olarak, <xref:System.Uri?displayProperty=nameWithType> sınıfı yol sıkıştırmayı yürütmeden önce, yüzde olarak kodlanmış yol sınırlayıcılarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="352d8-121">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="352d8-122">Bu, aşağıdaki gibi saldırılara karşı bir güvenlik mekanizması olarak uygulanmıştır:</span><span class="sxs-lookup"><span data-stu-id="352d8-122">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="352d8-123">Bu URI, yüzde kodlamalı karakterleri doğru şekilde işlemeyen modüllere geçiriliyorsa, aşağıdaki komut sunucu tarafından yürütülebilmesiyle sonuçlanabilir:</span><span class="sxs-lookup"><span data-stu-id="352d8-123">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="352d8-124">Bu nedenle, <xref:System.Uri?displayProperty=nameWithType> sınıf ilk olarak yol sınırlayıcılarını iptal eder ve yol sıkıştırması uygular.</span><span class="sxs-lookup"><span data-stu-id="352d8-124">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="352d8-125">Yukarıdaki kötü amaçlı URL 'YI sınıf oluşturucusuna geçirmenin sonucu <xref:System.Uri?displayProperty=nameWithType> AŞAĞıDAKI URI ile sonuçlanır:</span><span class="sxs-lookup"><span data-stu-id="352d8-125">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="352d8-126">Bu varsayılan davranış, belirli bir düzen için ıgmesettings yapılandırma seçeneği kullanılarak yüzde olmayan kodlanmış yol sınırlayıcılarını kaçırılmamış şekilde değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="352d8-126">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="352d8-127">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="352d8-127">Configuration Files</span></span>  
 <span data-ttu-id="352d8-128">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="352d8-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="352d8-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="352d8-129">Example</span></span>  
 <span data-ttu-id="352d8-130">Aşağıdaki örnek, <xref:System.Uri> http şeması için tüm düzen ayarlarını kaldıran sınıf tarafından kullanılan bir yapılandırmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="352d8-130">The following example shows a configuration used by the <xref:System.Uri> class that removes any scheme settings for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <remove name="http"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="352d8-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="352d8-131">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="352d8-132">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="352d8-132">Network Settings Schema</span></span>](index.md)
