---
title: "&lt;schemeSettings&gt; öğesi (URI ayarları)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
caps.latest.revision: "6"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 19bcb64beb7b022d20bbde1210ae6d844690d891
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltschemesettingsgt-element-uri-settings"></a><span data-ttu-id="56157-102">&lt;schemeSettings&gt; öğesi (URI ayarları)</span><span class="sxs-lookup"><span data-stu-id="56157-102">&lt;schemeSettings&gt; Element (Uri Settings)</span></span>
<span data-ttu-id="56157-103">Belirtir nasıl bir <xref:System.Uri> için belirli düzenleri ayrıştırılır.</span><span class="sxs-lookup"><span data-stu-id="56157-103">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>  
  
 <span data-ttu-id="56157-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="56157-104">\<configuration></span></span>  
<span data-ttu-id="56157-105">\<URI ></span><span class="sxs-lookup"><span data-stu-id="56157-105">\<uri></span></span>  
<span data-ttu-id="56157-106">\<schemeSettings ></span><span class="sxs-lookup"><span data-stu-id="56157-106">\<schemeSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56157-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="56157-107">Syntax</span></span>  
  
```xml  
<schemeSettings>   
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="56157-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="56157-108">Attributes and Elements</span></span>  
 <span data-ttu-id="56157-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="56157-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="56157-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="56157-110">Attributes</span></span>  
 <span data-ttu-id="56157-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="56157-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="56157-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="56157-112">Child Elements</span></span>  
  
|<span data-ttu-id="56157-113">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="56157-113">**Element**</span></span>|<span data-ttu-id="56157-114">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="56157-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="56157-115">add</span><span class="sxs-lookup"><span data-stu-id="56157-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="56157-116">Düzen adı için bir düzeni ayarı ekler.</span><span class="sxs-lookup"><span data-stu-id="56157-116">Adds a scheme setting for a scheme name.</span></span>|  
|[<span data-ttu-id="56157-117">Temizle</span><span class="sxs-lookup"><span data-stu-id="56157-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="56157-118">Tüm mevcut düzeni ayarlarını temizler.</span><span class="sxs-lookup"><span data-stu-id="56157-118">Clears all existing scheme settings.</span></span>|  
|[<span data-ttu-id="56157-119">remove</span><span class="sxs-lookup"><span data-stu-id="56157-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="56157-120">Düzen adı için bir düzeni ayarı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="56157-120">Removes a scheme setting for a scheme name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="56157-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="56157-121">Parent Elements</span></span>  
  
|<span data-ttu-id="56157-122">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="56157-122">**Element**</span></span>|<span data-ttu-id="56157-123">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="56157-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="56157-124">URI</span><span class="sxs-lookup"><span data-stu-id="56157-124">uri</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|<span data-ttu-id="56157-125">.NET Framework Tekdüzen Kaynak Tanımlayıcıları (URI'ler) kullanılarak ifade web adresleri işleme biçimini belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="56157-125">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56157-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="56157-126">Remarks</span></span>  
 <span data-ttu-id="56157-127">Varsayılan olarak, <xref:System.Uri?displayProperty=nameWithType> sınıfı kaydını çıkışları yüzde yolu sıkıştırma yürütmeden önce yolu ayırıcısı kodlanmış.</span><span class="sxs-lookup"><span data-stu-id="56157-127">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="56157-128">Bu, aşağıdaki gibi saldırılarına karşı bir güvenlik mekanizması olarak kullanılmıştır:</span><span class="sxs-lookup"><span data-stu-id="56157-128">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="56157-129">Bu URI aktarılırsa modülleri aşağıya doğru yüzde işlenmemesinin karakterlerin doğru kodlanmış, sunucu tarafından yürütülen aşağıdaki komutta neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="56157-129">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="56157-130">Bu nedenle, <xref:System.Uri?displayProperty=nameWithType> sınıfı ilk kaydını çıkışları yol ayırıcısı ve yol sıkıştırma uygular.</span><span class="sxs-lookup"><span data-stu-id="56157-130">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="56157-131">Yukarıdaki kötü amaçlı URL'sine geçirme sonucunu <xref:System.Uri?displayProperty=nameWithType> sınıfı aşağıdaki URI Oluşturucusu sonuçlanır:</span><span class="sxs-lookup"><span data-stu-id="56157-131">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="56157-132">Bu varsayılan davranışı değil, özel şema için schemeSettings yapılandırma seçeneğini kullanarak kaldırın kaçış yüzde kodlanmış yolu sınırlayıcıları için değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="56157-132">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="56157-133">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="56157-133">Configuration Files</span></span>  
 <span data-ttu-id="56157-134">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="56157-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="56157-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="56157-135">Example</span></span>  
 <span data-ttu-id="56157-136">Aşağıdaki örnek tarafından kullanılan bir yapılandırma gösterir <xref:System.Uri> http şeması için yüzde olarak kodlanmış yol ayırıcısı kaçış değil desteklemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="56157-136">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="56157-137">Öğe Bilgisi</span><span class="sxs-lookup"><span data-stu-id="56157-137">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="56157-138">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="56157-138">Namespace</span></span>|<span data-ttu-id="56157-139">Sistem</span><span class="sxs-lookup"><span data-stu-id="56157-139">System</span></span>|  
|<span data-ttu-id="56157-140">Şema adı</span><span class="sxs-lookup"><span data-stu-id="56157-140">Schema Name</span></span>||  
|<span data-ttu-id="56157-141">Dosya doğrulama</span><span class="sxs-lookup"><span data-stu-id="56157-141">Validation File</span></span>||  
|<span data-ttu-id="56157-142">Boş olabilir.</span><span class="sxs-lookup"><span data-stu-id="56157-142">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="56157-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="56157-143">See Also</span></span>  
 <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>  
 <xref:System.GenericUriParserOptions?displayProperty=nameWithType>  
 <xref:System.Uri?displayProperty=nameWithType>  
 [<span data-ttu-id="56157-144">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="56157-144">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
