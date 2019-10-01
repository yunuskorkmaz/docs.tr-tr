---
title: schemeSettings için <remove> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: 4095ba51-de20-4f87-b562-018abe422c91
ms.openlocfilehash: 0dc8c6111157ba1f23d4a0449bee8f6626027e23
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697857"
---
# <a name="remove-element-for-schemesettings-uri-settings"></a><span data-ttu-id="6f5ab-102">\<mesettings için > öğesini kaldırın (URI ayarları)</span><span class="sxs-lookup"><span data-stu-id="6f5ab-102">\<remove> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="6f5ab-103">Düzen adı için bir düzen ayarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="6f5ab-103">Removes a scheme setting for a scheme name.</span></span>  
  
[<span data-ttu-id="6f5ab-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="6f5ab-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="6f5ab-105">&nbsp; @ no__t-1[ **\<urı >** ](uri-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="6f5ab-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span></span>  
<span data-ttu-id="6f5ab-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<bir mesettings >** ](schemesettings-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="6f5ab-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)</span></span>  
<span data-ttu-id="6f5ab-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<remove >**</span><span class="sxs-lookup"><span data-stu-id="6f5ab-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f5ab-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6f5ab-108">Syntax</span></span>  
  
```xml  
<remove
  name="http|https"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f5ab-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6f5ab-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6f5ab-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6f5ab-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f5ab-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6f5ab-111">Attributes</span></span>  
  
|<span data-ttu-id="6f5ab-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6f5ab-112">Attribute</span></span>|<span data-ttu-id="6f5ab-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f5ab-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6f5ab-114">name</span><span class="sxs-lookup"><span data-stu-id="6f5ab-114">name</span></span>|<span data-ttu-id="6f5ab-115">Bu ayarın geçerli olduğu Düzen adı.</span><span class="sxs-lookup"><span data-stu-id="6f5ab-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="6f5ab-116">Yalnızca Name = "http" ve Name = "https" değerleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="6f5ab-116">The only supported values are name="http" and name="https".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6f5ab-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6f5ab-117">Child Elements</span></span>  
 <span data-ttu-id="6f5ab-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="6f5ab-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6f5ab-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6f5ab-119">Parent Elements</span></span>  
  
|<span data-ttu-id="6f5ab-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="6f5ab-120">Element</span></span>|<span data-ttu-id="6f5ab-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f5ab-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6f5ab-122">\<Ramesettings > öğesi (Uri Ayarları)</span><span class="sxs-lookup"><span data-stu-id="6f5ab-122">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="6f5ab-123">Belirli düzenler için <xref:System.Uri> ' ın nasıl ayrıştıralınacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f5ab-123">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f5ab-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6f5ab-124">Remarks</span></span>  
 <span data-ttu-id="6f5ab-125">Varsayılan olarak, <xref:System.Uri?displayProperty=nameWithType> sınıfı, yol sıkıştırmayı yürütmeden önce yüzde kodlamalı yol sınırlayıcılarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="6f5ab-125">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="6f5ab-126">Bu, aşağıdaki gibi saldırılara karşı bir güvenlik mekanizması olarak uygulanmıştır:</span><span class="sxs-lookup"><span data-stu-id="6f5ab-126">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="6f5ab-127">Bu URI, yüzde kodlamalı karakterleri doğru şekilde işlemeyen modüllere geçiriliyorsa, aşağıdaki komut sunucu tarafından yürütülebilmesiyle sonuçlanabilir:</span><span class="sxs-lookup"><span data-stu-id="6f5ab-127">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="6f5ab-128">Bu nedenle, <xref:System.Uri?displayProperty=nameWithType> sınıfı ilk olarak yol sınırlayıcılarını yok eder ve ardından yol sıkıştırması uygular.</span><span class="sxs-lookup"><span data-stu-id="6f5ab-128">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="6f5ab-129">Yukarıdaki kötü amaçlı URL 'YI <xref:System.Uri?displayProperty=nameWithType> sınıf oluşturucusuna geçirmenin sonucu aşağıdaki URI ile sonuçlanır:</span><span class="sxs-lookup"><span data-stu-id="6f5ab-129">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="6f5ab-130">Bu varsayılan davranış, belirli bir düzen için ıgmesettings yapılandırma seçeneği kullanılarak yüzde olmayan kodlanmış yol sınırlayıcılarını kaçırılmamış şekilde değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="6f5ab-130">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="6f5ab-131">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="6f5ab-131">Configuration Files</span></span>  
 <span data-ttu-id="6f5ab-132">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6f5ab-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f5ab-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="6f5ab-133">Example</span></span>  
 <span data-ttu-id="6f5ab-134">Aşağıdaki örnek, http şeması için tüm düzen ayarlarını kaldıran <xref:System.Uri> sınıfı tarafından kullanılan bir yapılandırmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f5ab-134">The following example shows a configuration used by the <xref:System.Uri> class that removes any scheme settings for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <remove name="http"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6f5ab-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f5ab-135">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="6f5ab-136">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="6f5ab-136">Network Settings Schema</span></span>](index.md)
