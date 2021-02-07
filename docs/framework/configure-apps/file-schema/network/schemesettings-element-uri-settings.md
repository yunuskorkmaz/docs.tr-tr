---
description: 'Daha fazla bilgi edinin: <schemeSettings> öğesi (URI ayarları)'
title: <schemeSettings> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
ms.openlocfilehash: 218676c10a8acaa79c2eb2146214e77beee9a972
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698446"
---
# <a name="schemesettings-element-uri-settings"></a><span data-ttu-id="788a1-103">\<schemeSettings> Öğesi (Uri Ayarları)</span><span class="sxs-lookup"><span data-stu-id="788a1-103">\<schemeSettings> Element (Uri Settings)</span></span>

<span data-ttu-id="788a1-104"><xref:System.Uri>Belirli düzenler için nasıl ayrıştırılacaksınız belirtir.</span><span class="sxs-lookup"><span data-stu-id="788a1-104">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<schemeSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="788a1-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="788a1-105">Syntax</span></span>  
  
```xml  
<schemeSettings>
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="788a1-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="788a1-106">Attributes and Elements</span></span>  

 <span data-ttu-id="788a1-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="788a1-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="788a1-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="788a1-108">Attributes</span></span>  

 <span data-ttu-id="788a1-109">Yok</span><span class="sxs-lookup"><span data-stu-id="788a1-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="788a1-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="788a1-110">Child Elements</span></span>  
  
|<span data-ttu-id="788a1-111">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="788a1-111">**Element**</span></span>|<span data-ttu-id="788a1-112">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="788a1-112">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="788a1-113">add</span><span class="sxs-lookup"><span data-stu-id="788a1-113">add</span></span>](add-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="788a1-114">Düzen adı için bir düzen ayarı ekler.</span><span class="sxs-lookup"><span data-stu-id="788a1-114">Adds a scheme setting for a scheme name.</span></span>|  
|[<span data-ttu-id="788a1-115">lediğiniz</span><span class="sxs-lookup"><span data-stu-id="788a1-115">clear</span></span>](clear-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="788a1-116">Varolan tüm düzen ayarlarını temizler.</span><span class="sxs-lookup"><span data-stu-id="788a1-116">Clears all existing scheme settings.</span></span>|  
|[<span data-ttu-id="788a1-117">temizlenmesine</span><span class="sxs-lookup"><span data-stu-id="788a1-117">remove</span></span>](remove-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="788a1-118">Düzen adı için bir düzen ayarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="788a1-118">Removes a scheme setting for a scheme name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="788a1-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="788a1-119">Parent Elements</span></span>  
  
|<span data-ttu-id="788a1-120">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="788a1-120">**Element**</span></span>|<span data-ttu-id="788a1-121">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="788a1-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="788a1-122">kullanılmamışsa</span><span class="sxs-lookup"><span data-stu-id="788a1-122">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="788a1-123">.NET Framework Tekdüzen Kaynak tanımlayıcıları (URI 'Ler) kullanarak ifade edilen Web adreslerini nasıl işleyeceğini belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="788a1-123">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="788a1-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="788a1-124">Remarks</span></span>  

 <span data-ttu-id="788a1-125">Varsayılan olarak, <xref:System.Uri?displayProperty=nameWithType> sınıfı yol sıkıştırmayı yürütmeden önce, yüzde olarak kodlanmış yol sınırlayıcılarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="788a1-125">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="788a1-126">Bu, aşağıdaki gibi saldırılara karşı bir güvenlik mekanizması olarak uygulanmıştır:</span><span class="sxs-lookup"><span data-stu-id="788a1-126">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="788a1-127">Bu URI, yüzde kodlamalı karakterleri doğru şekilde işlemeyen modüllere geçiriliyorsa, aşağıdaki komut sunucu tarafından yürütülebilmesiyle sonuçlanabilir:</span><span class="sxs-lookup"><span data-stu-id="788a1-127">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="788a1-128">Bu nedenle, <xref:System.Uri?displayProperty=nameWithType> sınıf ilk olarak yol sınırlayıcılarını iptal eder ve yol sıkıştırması uygular.</span><span class="sxs-lookup"><span data-stu-id="788a1-128">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="788a1-129">Yukarıdaki kötü amaçlı URL 'YI sınıf oluşturucusuna geçirmenin sonucu <xref:System.Uri?displayProperty=nameWithType> AŞAĞıDAKI URI ile sonuçlanır:</span><span class="sxs-lookup"><span data-stu-id="788a1-129">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="788a1-130">Bu varsayılan davranış, belirli bir düzen için ıgmesettings yapılandırma seçeneği kullanılarak yüzde olmayan kodlanmış yol sınırlayıcılarını kaçırılmamış şekilde değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="788a1-130">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="788a1-131">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="788a1-131">Configuration Files</span></span>  

 <span data-ttu-id="788a1-132">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="788a1-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="788a1-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="788a1-133">Example</span></span>  

 <span data-ttu-id="788a1-134">Aşağıdaki örnek, <xref:System.Uri> http şeması için yüzde kodlamalı bir yol sınırlayıcılarını yok etmek üzere sınıfı tarafından kullanılan bir yapılandırmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="788a1-134">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="788a1-135">Öğe Bilgisi</span><span class="sxs-lookup"><span data-stu-id="788a1-135">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="788a1-136">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="788a1-136">Namespace</span></span>|<span data-ttu-id="788a1-137">Sistem</span><span class="sxs-lookup"><span data-stu-id="788a1-137">System</span></span>|  
|<span data-ttu-id="788a1-138">Şema adı</span><span class="sxs-lookup"><span data-stu-id="788a1-138">Schema Name</span></span>||  
|<span data-ttu-id="788a1-139">Doğrulama dosyası</span><span class="sxs-lookup"><span data-stu-id="788a1-139">Validation File</span></span>||  
|<span data-ttu-id="788a1-140">Boş olabilir</span><span class="sxs-lookup"><span data-stu-id="788a1-140">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="788a1-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="788a1-141">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="788a1-142">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="788a1-142">Network Settings Schema</span></span>](index.md)
