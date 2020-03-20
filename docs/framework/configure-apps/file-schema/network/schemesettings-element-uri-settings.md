---
title: <schemeSettings> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
ms.openlocfilehash: c745c90bb61b9ee393687d7f6db4fd11565c7dc7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154653"
---
# <a name="schemesettings-element-uri-settings"></a><span data-ttu-id="2cd0f-102">\<şemaAyarları> Öğesi (Uri Ayarları)</span><span class="sxs-lookup"><span data-stu-id="2cd0f-102">\<schemeSettings> Element (Uri Settings)</span></span>
<span data-ttu-id="2cd0f-103">Belirli düzenler için <xref:System.Uri> a'nın nasıl ayrıştırılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2cd0f-103">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>  
  
[<span data-ttu-id="2cd0f-104">**\<yapılandırma>**</span><span class="sxs-lookup"><span data-stu-id="2cd0f-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="2cd0f-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="2cd0f-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span></span>  
<span data-ttu-id="2cd0f-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<şemaAyarlar>**</span><span class="sxs-lookup"><span data-stu-id="2cd0f-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<schemeSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cd0f-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2cd0f-107">Syntax</span></span>  
  
```xml  
<schemeSettings>
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2cd0f-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2cd0f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2cd0f-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2cd0f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2cd0f-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2cd0f-110">Attributes</span></span>  
 <span data-ttu-id="2cd0f-111">None</span><span class="sxs-lookup"><span data-stu-id="2cd0f-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2cd0f-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2cd0f-112">Child Elements</span></span>  
  
|<span data-ttu-id="2cd0f-113">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="2cd0f-113">**Element**</span></span>|<span data-ttu-id="2cd0f-114">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="2cd0f-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2cd0f-115">Ekle</span><span class="sxs-lookup"><span data-stu-id="2cd0f-115">add</span></span>](add-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="2cd0f-116">Şema adı için düzen ayarı ekler.</span><span class="sxs-lookup"><span data-stu-id="2cd0f-116">Adds a scheme setting for a scheme name.</span></span>|  
|[<span data-ttu-id="2cd0f-117">Temizleyin</span><span class="sxs-lookup"><span data-stu-id="2cd0f-117">clear</span></span>](clear-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="2cd0f-118">Varolan tüm düzen ayarlarını temizler.</span><span class="sxs-lookup"><span data-stu-id="2cd0f-118">Clears all existing scheme settings.</span></span>|  
|[<span data-ttu-id="2cd0f-119">Kaldırmak</span><span class="sxs-lookup"><span data-stu-id="2cd0f-119">remove</span></span>](remove-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="2cd0f-120">Düzen adı için düzen ayarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="2cd0f-120">Removes a scheme setting for a scheme name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2cd0f-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2cd0f-121">Parent Elements</span></span>  
  
|<span data-ttu-id="2cd0f-122">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="2cd0f-122">**Element**</span></span>|<span data-ttu-id="2cd0f-123">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="2cd0f-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2cd0f-124">Urı</span><span class="sxs-lookup"><span data-stu-id="2cd0f-124">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="2cd0f-125">.NET Framework'ün tek düzen kaynak tanımlayıcıları (URI) kullanılarak ifade edilen web adreslerini nasıl işleyeceğini belirten ayarlar içerir.</span><span class="sxs-lookup"><span data-stu-id="2cd0f-125">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2cd0f-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2cd0f-126">Remarks</span></span>  
 <span data-ttu-id="2cd0f-127">Varsayılan olarak, <xref:System.Uri?displayProperty=nameWithType> sınıf yol sıkıştırma yürütmeden önce yüzde kodlanmış yol sınırlayıcıları kaçar.</span><span class="sxs-lookup"><span data-stu-id="2cd0f-127">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="2cd0f-128">Bu, aşağıdaki gibi saldırılara karşı bir güvenlik mekanizması olarak uygulanmıştır:</span><span class="sxs-lookup"><span data-stu-id="2cd0f-128">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="2cd0f-129">Bu URI, yüzde kodlanmış karakterleri doğru işlemeyan modüllere aktarılırsa, sunucu tarafından aşağıdaki komutun yürütülmesine neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="2cd0f-129">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="2cd0f-130">Bu nedenle, <xref:System.Uri?displayProperty=nameWithType> sınıf ilk un-escapes yol sınırlayıcılar ve daha sonra yol sıkıştırma uygular.</span><span class="sxs-lookup"><span data-stu-id="2cd0f-130">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="2cd0f-131">Yukarıdaki kötü amaçlı URL'yi <xref:System.Uri?displayProperty=nameWithType> sınıf oluşturucuya geçirmenin sonucu aşağıdaki URI ile sonuçlanır:</span><span class="sxs-lookup"><span data-stu-id="2cd0f-131">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="2cd0f-132">Bu varsayılan davranış, belirli bir düzen için düzenAyarlar yapılandırma seçeneğini kullanarak kodlanmış yol sınırçözücülerini kaldırmamak için değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="2cd0f-132">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="2cd0f-133">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="2cd0f-133">Configuration Files</span></span>  
 <span data-ttu-id="2cd0f-134">Bu öğe uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2cd0f-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2cd0f-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="2cd0f-135">Example</span></span>  
 <span data-ttu-id="2cd0f-136">Aşağıdaki örnek, <xref:System.Uri> sınıf tarafından http düzeni için yüzde kodlanmış yol sınır çözücülerden kaçmayan desteği için kullanılan bir yapılandırmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="2cd0f-136">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="2cd0f-137">Öğe Bilgisi</span><span class="sxs-lookup"><span data-stu-id="2cd0f-137">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="2cd0f-138">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="2cd0f-138">Namespace</span></span>|<span data-ttu-id="2cd0f-139">Sistem</span><span class="sxs-lookup"><span data-stu-id="2cd0f-139">System</span></span>|  
|<span data-ttu-id="2cd0f-140">Şema Adı</span><span class="sxs-lookup"><span data-stu-id="2cd0f-140">Schema Name</span></span>||  
|<span data-ttu-id="2cd0f-141">Doğrulama Dosyası</span><span class="sxs-lookup"><span data-stu-id="2cd0f-141">Validation File</span></span>||  
|<span data-ttu-id="2cd0f-142">Boş Olabilir</span><span class="sxs-lookup"><span data-stu-id="2cd0f-142">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="2cd0f-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2cd0f-143">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="2cd0f-144">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="2cd0f-144">Network Settings Schema</span></span>](index.md)
