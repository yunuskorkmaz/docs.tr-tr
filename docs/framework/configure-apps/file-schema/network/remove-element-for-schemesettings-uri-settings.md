---
title: schemeSettings için <remove> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: 4095ba51-de20-4f87-b562-018abe422c91
ms.openlocfilehash: 018a08693a39bb297bdaa468ba59d4bf097f6922
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151395"
---
# <a name="remove-element-for-schemesettings-uri-settings"></a><span data-ttu-id="f4e15-102">schemeSettings için \<remove> Öğesi (Uri Ayarları)</span><span class="sxs-lookup"><span data-stu-id="f4e15-102">\<remove> Element for schemeSettings (Uri Settings)</span></span>

<span data-ttu-id="f4e15-103">Düzen adı için bir düzen ayarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f4e15-103">Removes a scheme setting for a scheme name.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="f4e15-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="f4e15-104">Syntax</span></span>  
  
```xml  
<remove
  name="http|https"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f4e15-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f4e15-105">Attributes and Elements</span></span>  

 <span data-ttu-id="f4e15-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f4e15-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f4e15-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f4e15-107">Attributes</span></span>  
  
|<span data-ttu-id="f4e15-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f4e15-108">Attribute</span></span>|<span data-ttu-id="f4e15-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f4e15-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f4e15-110">name</span><span class="sxs-lookup"><span data-stu-id="f4e15-110">name</span></span>|<span data-ttu-id="f4e15-111">Bu ayarın geçerli olduğu Düzen adı.</span><span class="sxs-lookup"><span data-stu-id="f4e15-111">The scheme name for which this setting applies.</span></span> <span data-ttu-id="f4e15-112">Yalnızca Name = "http" ve Name = "https" değerleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f4e15-112">The only supported values are name="http" and name="https".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f4e15-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f4e15-113">Child Elements</span></span>  

 <span data-ttu-id="f4e15-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="f4e15-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f4e15-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f4e15-115">Parent Elements</span></span>  
  
|<span data-ttu-id="f4e15-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="f4e15-116">Element</span></span>|<span data-ttu-id="f4e15-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f4e15-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f4e15-118">\<schemeSettings> Öğesi (URI ayarları)</span><span class="sxs-lookup"><span data-stu-id="f4e15-118">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="f4e15-119"><xref:System.Uri>Belirli düzenler için nasıl ayrıştırılacaksınız belirtir.</span><span class="sxs-lookup"><span data-stu-id="f4e15-119">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4e15-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f4e15-120">Remarks</span></span>  

 <span data-ttu-id="f4e15-121">Varsayılan olarak, <xref:System.Uri?displayProperty=nameWithType> sınıfı yol sıkıştırmayı yürütmeden önce, yüzde olarak kodlanmış yol sınırlayıcılarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f4e15-121">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="f4e15-122">Bu, aşağıdaki gibi saldırılara karşı bir güvenlik mekanizması olarak uygulanmıştır:</span><span class="sxs-lookup"><span data-stu-id="f4e15-122">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="f4e15-123">Bu URI, yüzde kodlamalı karakterleri doğru şekilde işlemeyen modüllere geçiriliyorsa, aşağıdaki komut sunucu tarafından yürütülebilmesiyle sonuçlanabilir:</span><span class="sxs-lookup"><span data-stu-id="f4e15-123">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="f4e15-124">Bu nedenle, <xref:System.Uri?displayProperty=nameWithType> sınıf ilk olarak yol sınırlayıcılarını iptal eder ve yol sıkıştırması uygular.</span><span class="sxs-lookup"><span data-stu-id="f4e15-124">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="f4e15-125">Yukarıdaki kötü amaçlı URL 'YI sınıf oluşturucusuna geçirmenin sonucu <xref:System.Uri?displayProperty=nameWithType> AŞAĞıDAKI URI ile sonuçlanır:</span><span class="sxs-lookup"><span data-stu-id="f4e15-125">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="f4e15-126">Bu varsayılan davranış, belirli bir düzen için ıgmesettings yapılandırma seçeneği kullanılarak yüzde olmayan kodlanmış yol sınırlayıcılarını kaçırılmamış şekilde değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="f4e15-126">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="f4e15-127">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="f4e15-127">Configuration Files</span></span>  

 <span data-ttu-id="f4e15-128">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f4e15-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4e15-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="f4e15-129">Example</span></span>  

 <span data-ttu-id="f4e15-130">Aşağıdaki örnek, <xref:System.Uri> http şeması için tüm düzen ayarlarını kaldıran sınıf tarafından kullanılan bir yapılandırmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4e15-130">The following example shows a configuration used by the <xref:System.Uri> class that removes any scheme settings for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <remove name="http"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f4e15-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4e15-131">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="f4e15-132">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="f4e15-132">Network Settings Schema</span></span>](index.md)
