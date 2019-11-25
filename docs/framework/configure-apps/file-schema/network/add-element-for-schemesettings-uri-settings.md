---
title: schemeSettings için <add> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
ms.openlocfilehash: ed40098e8d4c2d1298771e67a618b8d04f59c912
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087712"
---
# <a name="add-element-for-schemesettings-uri-settings"></a><span data-ttu-id="de637-102">\<için > öğesi ekleme (Uri Ayarları)</span><span class="sxs-lookup"><span data-stu-id="de637-102">\<add> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="de637-103">Düzen adı için bir düzen ayarı ekler.</span><span class="sxs-lookup"><span data-stu-id="de637-103">Adds a scheme setting for a scheme name.</span></span>  

<span data-ttu-id="de637-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="de637-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="de637-105">&nbsp;&nbsp;[ **\<urı >** ](uri-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="de637-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span></span>\
<span data-ttu-id="de637-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ayarları**](schemesettings-element-uri-settings.md) ></span><span class="sxs-lookup"><span data-stu-id="de637-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)</span></span>\
<span data-ttu-id="de637-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<add >**</span><span class="sxs-lookup"><span data-stu-id="de637-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="de637-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="de637-108">Syntax</span></span>  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de637-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="de637-109">Attributes and Elements</span></span>  
 <span data-ttu-id="de637-110">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="de637-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de637-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="de637-111">Attributes</span></span>  
  
|<span data-ttu-id="de637-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="de637-112">Attribute</span></span>|<span data-ttu-id="de637-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de637-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="de637-114">name</span><span class="sxs-lookup"><span data-stu-id="de637-114">name</span></span>|<span data-ttu-id="de637-115">Bu ayarın geçerli olduğu Düzen adı.</span><span class="sxs-lookup"><span data-stu-id="de637-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="de637-116">Yalnızca Name = "http" ve Name = "https" değerleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="de637-116">The only supported values are name="http" and name="https".</span></span>|  
  
## <a name="attribute-name-attribute"></a><span data-ttu-id="de637-117">{Öznitelik adı} Özniteliğe</span><span class="sxs-lookup"><span data-stu-id="de637-117">{Attribute name} Attribute</span></span>  
  
|<span data-ttu-id="de637-118">Değer</span><span class="sxs-lookup"><span data-stu-id="de637-118">Value</span></span>|<span data-ttu-id="de637-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de637-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="de637-120">genericUriParserOptions</span><span class="sxs-lookup"><span data-stu-id="de637-120">genericUriParserOptions</span></span>|<span data-ttu-id="de637-121">Bu şema için ayrıştırıcı seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="de637-121">The parser options for this scheme.</span></span> <span data-ttu-id="de637-122">Yalnızca genericUriParserOptions = "DontUnescapePathDotsAndSlashes" değeri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="de637-122">The only supported value is genericUriParserOptions= "DontUnescapePathDotsAndSlashes".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="de637-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="de637-123">Child Elements</span></span>  
 <span data-ttu-id="de637-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="de637-124">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="de637-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="de637-125">Parent Elements</span></span>  
  
|<span data-ttu-id="de637-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="de637-126">Element</span></span>|<span data-ttu-id="de637-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de637-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="de637-128">\<düzeni > öğesi (URI ayarları)</span><span class="sxs-lookup"><span data-stu-id="de637-128">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="de637-129">Belirli düzenler için <xref:System.Uri> nasıl ayrıştırılagösterir.</span><span class="sxs-lookup"><span data-stu-id="de637-129">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de637-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="de637-130">Remarks</span></span>  
 <span data-ttu-id="de637-131">Varsayılan olarak, <xref:System.Uri?displayProperty=nameWithType> sınıfı, yol sıkıştırmayı yürütmeden önce yüzde kodlamalı yol sınırlayıcılarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="de637-131">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="de637-132">Bu, aşağıdaki gibi saldırılara karşı bir güvenlik mekanizması olarak uygulanmıştır:</span><span class="sxs-lookup"><span data-stu-id="de637-132">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="de637-133">Bu URI, yüzde kodlamalı karakterleri doğru şekilde işlemeyen modüllere geçiriliyorsa, aşağıdaki komut sunucu tarafından yürütülebilmesiyle sonuçlanabilir:</span><span class="sxs-lookup"><span data-stu-id="de637-133">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="de637-134">Bu nedenle, <xref:System.Uri?displayProperty=nameWithType> sınıfı ilk olarak yol sınırlayıcılarını kaldırın ve ardından yol sıkıştırması uygular.</span><span class="sxs-lookup"><span data-stu-id="de637-134">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="de637-135">Yukarıdaki kötü amaçlı URL 'YI <xref:System.Uri?displayProperty=nameWithType> sınıf oluşturucusuna geçirmenin sonucu aşağıdaki URI ile sonuçlanır:</span><span class="sxs-lookup"><span data-stu-id="de637-135">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="de637-136">Bu varsayılan davranış, belirli bir düzen için ıgmesettings yapılandırma seçeneği kullanılarak yüzde olmayan kodlanmış yol sınırlayıcılarını kaçırılmamış şekilde değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="de637-136">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="de637-137">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="de637-137">Configuration Files</span></span>  
 <span data-ttu-id="de637-138">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="de637-138">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="de637-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="de637-139">Example</span></span>  
 <span data-ttu-id="de637-140">Aşağıdaki örnek, http şemasına yönelik yüzde kodlamalı yol sınırlayıcılarını yok etmek için <xref:System.Uri> sınıfı tarafından kullanılan bir yapılandırmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="de637-140">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="de637-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de637-141">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="de637-142">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="de637-142">Network Settings Schema</span></span>](index.md)
