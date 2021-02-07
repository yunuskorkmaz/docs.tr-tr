---
description: 'Hakkında daha fazla bilgi edinin: <remove> ıviewmesettings için öğesi (Uri Ayarları)'
title: schemeSettings için <remove> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: 4095ba51-de20-4f87-b562-018abe422c91
ms.openlocfilehash: 125a347cfcbb1393ea70032b7e1b198a1a5a4ed0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713032"
---
# <a name="remove-element-for-schemesettings-uri-settings"></a><span data-ttu-id="19a0b-103">schemeSettings için \<remove> Öğesi (Uri Ayarları)</span><span class="sxs-lookup"><span data-stu-id="19a0b-103">\<remove> Element for schemeSettings (Uri Settings)</span></span>

<span data-ttu-id="19a0b-104">Düzen adı için bir düzen ayarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="19a0b-104">Removes a scheme setting for a scheme name.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="19a0b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="19a0b-105">Syntax</span></span>  
  
```xml  
<remove
  name="http|https"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="19a0b-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="19a0b-106">Attributes and Elements</span></span>  

 <span data-ttu-id="19a0b-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="19a0b-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="19a0b-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="19a0b-108">Attributes</span></span>  
  
|<span data-ttu-id="19a0b-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="19a0b-109">Attribute</span></span>|<span data-ttu-id="19a0b-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="19a0b-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="19a0b-111">name</span><span class="sxs-lookup"><span data-stu-id="19a0b-111">name</span></span>|<span data-ttu-id="19a0b-112">Bu ayarın geçerli olduğu Düzen adı.</span><span class="sxs-lookup"><span data-stu-id="19a0b-112">The scheme name for which this setting applies.</span></span> <span data-ttu-id="19a0b-113">Yalnızca Name = "http" ve Name = "https" değerleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="19a0b-113">The only supported values are name="http" and name="https".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="19a0b-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="19a0b-114">Child Elements</span></span>  

 <span data-ttu-id="19a0b-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="19a0b-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="19a0b-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="19a0b-116">Parent Elements</span></span>  
  
|<span data-ttu-id="19a0b-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="19a0b-117">Element</span></span>|<span data-ttu-id="19a0b-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="19a0b-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="19a0b-119">\<schemeSettings> Öğesi (URI ayarları)</span><span class="sxs-lookup"><span data-stu-id="19a0b-119">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="19a0b-120"><xref:System.Uri>Belirli düzenler için nasıl ayrıştırılacaksınız belirtir.</span><span class="sxs-lookup"><span data-stu-id="19a0b-120">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19a0b-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="19a0b-121">Remarks</span></span>  

 <span data-ttu-id="19a0b-122">Varsayılan olarak, <xref:System.Uri?displayProperty=nameWithType> sınıfı yol sıkıştırmayı yürütmeden önce, yüzde olarak kodlanmış yol sınırlayıcılarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="19a0b-122">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="19a0b-123">Bu, aşağıdaki gibi saldırılara karşı bir güvenlik mekanizması olarak uygulanmıştır:</span><span class="sxs-lookup"><span data-stu-id="19a0b-123">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="19a0b-124">Bu URI, yüzde kodlamalı karakterleri doğru şekilde işlemeyen modüllere geçiriliyorsa, aşağıdaki komut sunucu tarafından yürütülebilmesiyle sonuçlanabilir:</span><span class="sxs-lookup"><span data-stu-id="19a0b-124">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="19a0b-125">Bu nedenle, <xref:System.Uri?displayProperty=nameWithType> sınıf ilk olarak yol sınırlayıcılarını iptal eder ve yol sıkıştırması uygular.</span><span class="sxs-lookup"><span data-stu-id="19a0b-125">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="19a0b-126">Yukarıdaki kötü amaçlı URL 'YI sınıf oluşturucusuna geçirmenin sonucu <xref:System.Uri?displayProperty=nameWithType> AŞAĞıDAKI URI ile sonuçlanır:</span><span class="sxs-lookup"><span data-stu-id="19a0b-126">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="19a0b-127">Bu varsayılan davranış, belirli bir düzen için ıgmesettings yapılandırma seçeneği kullanılarak yüzde olmayan kodlanmış yol sınırlayıcılarını kaçırılmamış şekilde değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="19a0b-127">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="19a0b-128">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="19a0b-128">Configuration Files</span></span>  

 <span data-ttu-id="19a0b-129">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="19a0b-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="19a0b-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="19a0b-130">Example</span></span>  

 <span data-ttu-id="19a0b-131">Aşağıdaki örnek, <xref:System.Uri> http şeması için tüm düzen ayarlarını kaldıran sınıf tarafından kullanılan bir yapılandırmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="19a0b-131">The following example shows a configuration used by the <xref:System.Uri> class that removes any scheme settings for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <remove name="http"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="19a0b-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19a0b-132">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="19a0b-133">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="19a0b-133">Network Settings Schema</span></span>](index.md)
