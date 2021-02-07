---
description: 'Hakkında daha fazla bilgi edinin: <clear> ıviewmesettings için öğesi (Uri Ayarları)'
title: schemeSettings için <clear> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: 65098332-ce61-4542-ab8d-e7dc0257d31f
ms.openlocfilehash: 719296285c9a7da26eb6eaf16c630a63a10698b5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740463"
---
# <a name="clear-element-for-schemesettings-uri-settings"></a><span data-ttu-id="4c5b6-103">schemeSettings için \<clear> Öğesi (Uri Ayarları)</span><span class="sxs-lookup"><span data-stu-id="4c5b6-103">\<clear> Element for schemeSettings (Uri Settings)</span></span>

<span data-ttu-id="4c5b6-104">Varolan tüm düzen ayarlarını temizler.</span><span class="sxs-lookup"><span data-stu-id="4c5b6-104">Clears all existing scheme settings.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="4c5b6-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4c5b6-105">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4c5b6-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4c5b6-106">Attributes and Elements</span></span>  

 <span data-ttu-id="4c5b6-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4c5b6-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4c5b6-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4c5b6-108">Attributes</span></span>  

 <span data-ttu-id="4c5b6-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="4c5b6-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4c5b6-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4c5b6-110">Child Elements</span></span>  

 <span data-ttu-id="4c5b6-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="4c5b6-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4c5b6-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4c5b6-112">Parent Elements</span></span>  
  
|<span data-ttu-id="4c5b6-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="4c5b6-113">Element</span></span>|<span data-ttu-id="4c5b6-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c5b6-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4c5b6-115">\<schemeSettings> Öğesi (URI ayarları)</span><span class="sxs-lookup"><span data-stu-id="4c5b6-115">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="4c5b6-116"><xref:System.Uri>Belirli düzenler için nasıl ayrıştırılacaksınız belirtir.</span><span class="sxs-lookup"><span data-stu-id="4c5b6-116">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c5b6-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4c5b6-117">Remarks</span></span>  

 <span data-ttu-id="4c5b6-118">Varsayılan olarak, <xref:System.Uri?displayProperty=nameWithType> sınıfı yol sıkıştırmayı yürütmeden önce, yüzde olarak kodlanmış yol sınırlayıcılarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="4c5b6-118">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="4c5b6-119">Bu, aşağıdaki gibi saldırılara karşı bir güvenlik mekanizması olarak uygulanmıştır:</span><span class="sxs-lookup"><span data-stu-id="4c5b6-119">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="4c5b6-120">Bu URI, yüzde kodlamalı karakterleri doğru şekilde işlemeyen modüllere geçiriliyorsa, aşağıdaki komut sunucu tarafından yürütülebilmesiyle sonuçlanabilir:</span><span class="sxs-lookup"><span data-stu-id="4c5b6-120">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="4c5b6-121">Bu nedenle, <xref:System.Uri?displayProperty=nameWithType> sınıf ilk olarak yol sınırlayıcılarını iptal eder ve yol sıkıştırması uygular.</span><span class="sxs-lookup"><span data-stu-id="4c5b6-121">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="4c5b6-122">Yukarıdaki kötü amaçlı URL 'YI sınıf oluşturucusuna geçirmenin sonucu <xref:System.Uri?displayProperty=nameWithType> AŞAĞıDAKI URI ile sonuçlanır:</span><span class="sxs-lookup"><span data-stu-id="4c5b6-122">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="4c5b6-123">Bu varsayılan davranış, belirli bir düzen için ıgmesettings yapılandırma seçeneği kullanılarak yüzde olmayan kodlanmış yol sınırlayıcılarını kaçırılmamış şekilde değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="4c5b6-123">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="4c5b6-124">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="4c5b6-124">Configuration Files</span></span>  

 <span data-ttu-id="4c5b6-125">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4c5b6-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c5b6-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="4c5b6-126">Example</span></span>  

 <span data-ttu-id="4c5b6-127">Aşağıdaki örnek, <xref:System.Uri> tüm düzen ayarlarını temizleyen sınıf tarafından kullanılan bir yapılandırmayı gösterir ve ardından http şeması için tam olmayan yüzde kodlamalı yol sınırlayıcıları için destek ekler.</span><span class="sxs-lookup"><span data-stu-id="4c5b6-127">The following example shows a configuration used by the <xref:System.Uri> class that clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <clear/>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4c5b6-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c5b6-128">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="4c5b6-129">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="4c5b6-129">Network Settings Schema</span></span>](index.md)
