---
title: "&lt;Clear&gt; öğesi schemeSettings (URI ayarları) için"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65098332-ce61-4542-ab8d-e7dc0257d31f
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: ffbe875e99376a7c782f177438709bcbb0ccb528
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcleargt-element-for-schemesettings-uri-settings"></a><span data-ttu-id="01627-102">&lt;Clear&gt; öğesi schemeSettings (URI ayarları) için</span><span class="sxs-lookup"><span data-stu-id="01627-102">&lt;clear&gt; Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="01627-103">Tüm mevcut düzeni ayarlarını temizler.</span><span class="sxs-lookup"><span data-stu-id="01627-103">Clears all existing scheme settings.</span></span>  
  
 <span data-ttu-id="01627-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="01627-104">\<configuration></span></span>  
<span data-ttu-id="01627-105">\<URI ></span><span class="sxs-lookup"><span data-stu-id="01627-105">\<uri></span></span>  
<span data-ttu-id="01627-106">\<schemeSettings ></span><span class="sxs-lookup"><span data-stu-id="01627-106">\<schemeSettings></span></span>  
<span data-ttu-id="01627-107">\<Clear ></span><span class="sxs-lookup"><span data-stu-id="01627-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01627-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="01627-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="01627-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="01627-109">Attributes and Elements</span></span>  
 <span data-ttu-id="01627-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="01627-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="01627-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="01627-111">Attributes</span></span>  
 <span data-ttu-id="01627-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="01627-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="01627-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="01627-113">Child Elements</span></span>  
 <span data-ttu-id="01627-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="01627-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="01627-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="01627-115">Parent Elements</span></span>  
  
|<span data-ttu-id="01627-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="01627-116">Element</span></span>|<span data-ttu-id="01627-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="01627-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="01627-118">\<schemeSettings > öğesi (URI ayarları)</span><span class="sxs-lookup"><span data-stu-id="01627-118">\<schemeSettings> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="01627-119">Belirtir nasıl bir <xref:System.Uri> için belirli düzenleri ayrıştırılır.</span><span class="sxs-lookup"><span data-stu-id="01627-119">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01627-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="01627-120">Remarks</span></span>  
 <span data-ttu-id="01627-121">Varsayılan olarak, <xref:System.Uri?displayProperty=nameWithType> sınıfı kaydını çıkışları yüzde yolu sıkıştırma yürütmeden önce yolu ayırıcısı kodlanmış.</span><span class="sxs-lookup"><span data-stu-id="01627-121">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="01627-122">Bu, aşağıdaki gibi saldırılarına karşı bir güvenlik mekanizması olarak kullanılmıştır:</span><span class="sxs-lookup"><span data-stu-id="01627-122">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="01627-123">Bu URI aktarılırsa modülleri aşağıya doğru yüzde işlenmemesinin karakterlerin doğru kodlanmış, sunucu tarafından yürütülen aşağıdaki komutta neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="01627-123">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="01627-124">Bu nedenle, <xref:System.Uri?displayProperty=nameWithType> sınıfı ilk kaydını çıkışları yol ayırıcısı ve yol sıkıştırma uygular.</span><span class="sxs-lookup"><span data-stu-id="01627-124">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="01627-125">Yukarıdaki kötü amaçlı URL'sine geçirme sonucunu <xref:System.Uri?displayProperty=nameWithType> sınıfı aşağıdaki URI Oluşturucusu sonuçlanır:</span><span class="sxs-lookup"><span data-stu-id="01627-125">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="01627-126">Bu varsayılan davranışı değil, özel şema için schemeSettings yapılandırma seçeneğini kullanarak kaldırın kaçış yüzde kodlanmış yolu sınırlayıcıları için değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="01627-126">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="01627-127">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="01627-127">Configuration Files</span></span>  
 <span data-ttu-id="01627-128">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="01627-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="01627-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="01627-129">Example</span></span>  
 <span data-ttu-id="01627-130">Aşağıdaki örnek tarafından kullanılan bir yapılandırma gösterir <xref:System.Uri> tüm düzeni ayarlarını temizler ve yüzde olarak kodlanmış yol ayırıcısı http şeması için kaçış değil için destek ekleyen sınıfı.</span><span class="sxs-lookup"><span data-stu-id="01627-130">The following example shows a configuration used by the <xref:System.Uri> class that clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="01627-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="01627-131">See Also</span></span>  
 <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>  
 <xref:System.GenericUriParserOptions?displayProperty=nameWithType>  
 <xref:System.Uri?displayProperty=nameWithType>  
 [<span data-ttu-id="01627-132">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="01627-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
