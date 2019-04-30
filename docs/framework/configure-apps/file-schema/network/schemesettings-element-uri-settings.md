---
title: <schemeSettings> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
ms.openlocfilehash: 8dc505d8a9de4e8939372af61b23652551c36530
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705018"
---
# <a name="schemesettings-element-uri-settings"></a><span data-ttu-id="96300-102">\<schemeSettings > öğesi (Uri ayarları)</span><span class="sxs-lookup"><span data-stu-id="96300-102">\<schemeSettings> Element (Uri Settings)</span></span>
<span data-ttu-id="96300-103">Belirtir nasıl bir <xref:System.Uri> belirli düzenleri için ayrıştırılacak.</span><span class="sxs-lookup"><span data-stu-id="96300-103">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>  
  
 <span data-ttu-id="96300-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="96300-104">\<configuration></span></span>  
<span data-ttu-id="96300-105">\<URI ></span><span class="sxs-lookup"><span data-stu-id="96300-105">\<uri></span></span>  
<span data-ttu-id="96300-106">\<schemeSettings ></span><span class="sxs-lookup"><span data-stu-id="96300-106">\<schemeSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96300-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="96300-107">Syntax</span></span>  
  
```xml  
<schemeSettings>   
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="96300-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="96300-108">Attributes and Elements</span></span>  
 <span data-ttu-id="96300-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="96300-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="96300-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="96300-110">Attributes</span></span>  
 <span data-ttu-id="96300-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="96300-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="96300-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="96300-112">Child Elements</span></span>  
  
|<span data-ttu-id="96300-113">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="96300-113">**Element**</span></span>|<span data-ttu-id="96300-114">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="96300-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="96300-115">add</span><span class="sxs-lookup"><span data-stu-id="96300-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="96300-116">Düzen adı için bir düzen ayarı ekler.</span><span class="sxs-lookup"><span data-stu-id="96300-116">Adds a scheme setting for a scheme name.</span></span>|  
|[<span data-ttu-id="96300-117">Temizle</span><span class="sxs-lookup"><span data-stu-id="96300-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="96300-118">Tüm mevcut düzeni ayarlarını temizler.</span><span class="sxs-lookup"><span data-stu-id="96300-118">Clears all existing scheme settings.</span></span>|  
|[<span data-ttu-id="96300-119">remove</span><span class="sxs-lookup"><span data-stu-id="96300-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="96300-120">Düzen adı için bir düzen ayarı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="96300-120">Removes a scheme setting for a scheme name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="96300-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="96300-121">Parent Elements</span></span>  
  
|<span data-ttu-id="96300-122">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="96300-122">**Element**</span></span>|<span data-ttu-id="96300-123">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="96300-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="96300-124">URI</span><span class="sxs-lookup"><span data-stu-id="96300-124">uri</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|<span data-ttu-id="96300-125">.NET Framework web adresleri Tekdüzen Kaynak Tanımlayıcıları (URI'lar) kullanılarak ifade nasıl işlediğini belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="96300-125">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96300-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="96300-126">Remarks</span></span>  
 <span data-ttu-id="96300-127">Varsayılan olarak, <xref:System.Uri?displayProperty=nameWithType> sınıfı Geri Al çıkışları yüzde yolu sınırlayıcı yolu sıkıştırma yürütmeden önce kodlanmış.</span><span class="sxs-lookup"><span data-stu-id="96300-127">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="96300-128">Bu, aşağıdaki gibi saldırılarına karşı bir güvenlik mekanizması olarak uygulanmıştır:</span><span class="sxs-lookup"><span data-stu-id="96300-128">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="96300-129">Bu URI iletilir aşağı modülleri yüzde işlenmemesinin karakterlerin doğru kodlanmış, sunucu tarafından çalıştırılan aşağıdaki komutu neden:</span><span class="sxs-lookup"><span data-stu-id="96300-129">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="96300-130">Bu nedenle, <xref:System.Uri?displayProperty=nameWithType> sınıf ilk geri al çıkışları yol ayırıcıları ve yol sıkıştırma uygular.</span><span class="sxs-lookup"><span data-stu-id="96300-130">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="96300-131">Yukarıda kötü amaçlı URL'sini geçirme sonucunu <xref:System.Uri?displayProperty=nameWithType> sınıf oluşturucu sonuçları aşağıdaki URI:</span><span class="sxs-lookup"><span data-stu-id="96300-131">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="96300-132">Bu varsayılan davranışı değil, için belirli bir düzeni schemeSettings yapılandırma seçeneğini kullanarak kaldırın kaçış yüzde kodlanmış yolu sınırlayıcılar için değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="96300-132">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="96300-133">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="96300-133">Configuration Files</span></span>  
 <span data-ttu-id="96300-134">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="96300-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="96300-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="96300-135">Example</span></span>  
 <span data-ttu-id="96300-136">Aşağıdaki örnek tarafından kullanılan bir yapılandırma gösterir <xref:System.Uri> http düzeni için yol yüzde olarak kodlanmış sınırlayıcılar kaçış değil desteklemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="96300-136">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="96300-137">Öğe Bilgisi</span><span class="sxs-lookup"><span data-stu-id="96300-137">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="96300-138">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="96300-138">Namespace</span></span>|<span data-ttu-id="96300-139">Sistem</span><span class="sxs-lookup"><span data-stu-id="96300-139">System</span></span>|  
|<span data-ttu-id="96300-140">Şema adı</span><span class="sxs-lookup"><span data-stu-id="96300-140">Schema Name</span></span>||  
|<span data-ttu-id="96300-141">Doğrulama dosyası</span><span class="sxs-lookup"><span data-stu-id="96300-141">Validation File</span></span>||  
|<span data-ttu-id="96300-142">Boş olabilir.</span><span class="sxs-lookup"><span data-stu-id="96300-142">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="96300-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96300-143">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="96300-144">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="96300-144">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
