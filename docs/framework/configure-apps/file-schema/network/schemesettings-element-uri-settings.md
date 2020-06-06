---
title: <schemeSettings> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
ms.openlocfilehash: c745c90bb61b9ee393687d7f6db4fd11565c7dc7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154653"
---
# <a name="schemesettings-element-uri-settings"></a><span data-ttu-id="87536-102">\<schemeSettings> Öğesi (Uri Ayarları)</span><span class="sxs-lookup"><span data-stu-id="87536-102">\<schemeSettings> Element (Uri Settings)</span></span>
<span data-ttu-id="87536-103"><xref:System.Uri>Belirli düzenler için nasıl ayrıştırılacaksınız belirtir.</span><span class="sxs-lookup"><span data-stu-id="87536-103">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<schemeSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="87536-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="87536-104">Syntax</span></span>  
  
```xml  
<schemeSettings>
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87536-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="87536-105">Attributes and Elements</span></span>  
 <span data-ttu-id="87536-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="87536-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87536-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="87536-107">Attributes</span></span>  
 <span data-ttu-id="87536-108">Yok</span><span class="sxs-lookup"><span data-stu-id="87536-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="87536-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="87536-109">Child Elements</span></span>  
  
|<span data-ttu-id="87536-110">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="87536-110">**Element**</span></span>|<span data-ttu-id="87536-111">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="87536-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="87536-112">add</span><span class="sxs-lookup"><span data-stu-id="87536-112">add</span></span>](add-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="87536-113">Düzen adı için bir düzen ayarı ekler.</span><span class="sxs-lookup"><span data-stu-id="87536-113">Adds a scheme setting for a scheme name.</span></span>|  
|[<span data-ttu-id="87536-114">lediğiniz</span><span class="sxs-lookup"><span data-stu-id="87536-114">clear</span></span>](clear-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="87536-115">Varolan tüm düzen ayarlarını temizler.</span><span class="sxs-lookup"><span data-stu-id="87536-115">Clears all existing scheme settings.</span></span>|  
|[<span data-ttu-id="87536-116">temizlenmesine</span><span class="sxs-lookup"><span data-stu-id="87536-116">remove</span></span>](remove-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="87536-117">Düzen adı için bir düzen ayarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="87536-117">Removes a scheme setting for a scheme name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="87536-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="87536-118">Parent Elements</span></span>  
  
|<span data-ttu-id="87536-119">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="87536-119">**Element**</span></span>|<span data-ttu-id="87536-120">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="87536-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="87536-121">kullanılmamışsa</span><span class="sxs-lookup"><span data-stu-id="87536-121">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="87536-122">.NET Framework Tekdüzen Kaynak tanımlayıcıları (URI 'Ler) kullanarak ifade edilen Web adreslerini nasıl işleyeceğini belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="87536-122">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87536-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="87536-123">Remarks</span></span>  
 <span data-ttu-id="87536-124">Varsayılan olarak, <xref:System.Uri?displayProperty=nameWithType> sınıfı yol sıkıştırmayı yürütmeden önce, yüzde olarak kodlanmış yol sınırlayıcılarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="87536-124">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="87536-125">Bu, aşağıdaki gibi saldırılara karşı bir güvenlik mekanizması olarak uygulanmıştır:</span><span class="sxs-lookup"><span data-stu-id="87536-125">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="87536-126">Bu URI, yüzde kodlamalı karakterleri doğru şekilde işlemeyen modüllere geçiriliyorsa, aşağıdaki komut sunucu tarafından yürütülebilmesiyle sonuçlanabilir:</span><span class="sxs-lookup"><span data-stu-id="87536-126">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="87536-127">Bu nedenle, <xref:System.Uri?displayProperty=nameWithType> sınıf ilk olarak yol sınırlayıcılarını iptal eder ve yol sıkıştırması uygular.</span><span class="sxs-lookup"><span data-stu-id="87536-127">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="87536-128">Yukarıdaki kötü amaçlı URL 'YI sınıf oluşturucusuna geçirmenin sonucu <xref:System.Uri?displayProperty=nameWithType> AŞAĞıDAKI URI ile sonuçlanır:</span><span class="sxs-lookup"><span data-stu-id="87536-128">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="87536-129">Bu varsayılan davranış, belirli bir düzen için ıgmesettings yapılandırma seçeneği kullanılarak yüzde olmayan kodlanmış yol sınırlayıcılarını kaçırılmamış şekilde değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="87536-129">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="87536-130">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="87536-130">Configuration Files</span></span>  
 <span data-ttu-id="87536-131">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="87536-131">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="87536-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="87536-132">Example</span></span>  
 <span data-ttu-id="87536-133">Aşağıdaki örnek, <xref:System.Uri> http şeması için yüzde kodlamalı bir yol sınırlayıcılarını yok etmek üzere sınıfı tarafından kullanılan bir yapılandırmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="87536-133">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="87536-134">Öğe Bilgisi</span><span class="sxs-lookup"><span data-stu-id="87536-134">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="87536-135">Ad alanı</span><span class="sxs-lookup"><span data-stu-id="87536-135">Namespace</span></span>|<span data-ttu-id="87536-136">Sistem</span><span class="sxs-lookup"><span data-stu-id="87536-136">System</span></span>|  
|<span data-ttu-id="87536-137">Şema adı</span><span class="sxs-lookup"><span data-stu-id="87536-137">Schema Name</span></span>||  
|<span data-ttu-id="87536-138">Doğrulama dosyası</span><span class="sxs-lookup"><span data-stu-id="87536-138">Validation File</span></span>||  
|<span data-ttu-id="87536-139">Boş olabilir</span><span class="sxs-lookup"><span data-stu-id="87536-139">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="87536-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87536-140">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="87536-141">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="87536-141">Network Settings Schema</span></span>](index.md)
