---
title: schemeSettings için <add> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
ms.openlocfilehash: ed40098e8d4c2d1298771e67a618b8d04f59c912
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74087712"
---
# <a name="add-element-for-schemesettings-uri-settings"></a><span data-ttu-id="236c7-102">schemeSettings için \<add> Öğesi (Uri Ayarları)</span><span class="sxs-lookup"><span data-stu-id="236c7-102">\<add> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="236c7-103">Düzen adı için bir düzen ayarı ekler.</span><span class="sxs-lookup"><span data-stu-id="236c7-103">Adds a scheme setting for a scheme name.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="236c7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="236c7-104">Syntax</span></span>  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="236c7-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="236c7-105">Attributes and Elements</span></span>  
 <span data-ttu-id="236c7-106">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="236c7-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="236c7-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="236c7-107">Attributes</span></span>  
  
|<span data-ttu-id="236c7-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="236c7-108">Attribute</span></span>|<span data-ttu-id="236c7-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="236c7-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="236c7-110">name</span><span class="sxs-lookup"><span data-stu-id="236c7-110">name</span></span>|<span data-ttu-id="236c7-111">Bu ayarın geçerli olduğu Düzen adı.</span><span class="sxs-lookup"><span data-stu-id="236c7-111">The scheme name for which this setting applies.</span></span> <span data-ttu-id="236c7-112">Yalnızca Name = "http" ve Name = "https" değerleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="236c7-112">The only supported values are name="http" and name="https".</span></span>|  
  
## <a name="attribute-name-attribute"></a><span data-ttu-id="236c7-113">{Öznitelik adı} Özniteliğe</span><span class="sxs-lookup"><span data-stu-id="236c7-113">{Attribute name} Attribute</span></span>  
  
|<span data-ttu-id="236c7-114">Değer</span><span class="sxs-lookup"><span data-stu-id="236c7-114">Value</span></span>|<span data-ttu-id="236c7-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="236c7-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="236c7-116">genericUriParserOptions</span><span class="sxs-lookup"><span data-stu-id="236c7-116">genericUriParserOptions</span></span>|<span data-ttu-id="236c7-117">Bu şema için ayrıştırıcı seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="236c7-117">The parser options for this scheme.</span></span> <span data-ttu-id="236c7-118">Yalnızca genericUriParserOptions = "DontUnescapePathDotsAndSlashes" değeri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="236c7-118">The only supported value is genericUriParserOptions= "DontUnescapePathDotsAndSlashes".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="236c7-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="236c7-119">Child Elements</span></span>  
 <span data-ttu-id="236c7-120">Yok</span><span class="sxs-lookup"><span data-stu-id="236c7-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="236c7-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="236c7-121">Parent Elements</span></span>  
  
|<span data-ttu-id="236c7-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="236c7-122">Element</span></span>|<span data-ttu-id="236c7-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="236c7-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="236c7-124">\<schemeSettings>Öğesi (URI ayarları)</span><span class="sxs-lookup"><span data-stu-id="236c7-124">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="236c7-125"><xref:System.Uri>Belirli düzenler için nasıl ayrıştırılacaksınız belirtir.</span><span class="sxs-lookup"><span data-stu-id="236c7-125">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="236c7-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="236c7-126">Remarks</span></span>  
 <span data-ttu-id="236c7-127">Varsayılan olarak, <xref:System.Uri?displayProperty=nameWithType> sınıfı yol sıkıştırmayı yürütmeden önce, yüzde olarak kodlanmış yol sınırlayıcılarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="236c7-127">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="236c7-128">Bu, aşağıdaki gibi saldırılara karşı bir güvenlik mekanizması olarak uygulanmıştır:</span><span class="sxs-lookup"><span data-stu-id="236c7-128">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="236c7-129">Bu URI, yüzde kodlamalı karakterleri doğru şekilde işlemeyen modüllere geçiriliyorsa, aşağıdaki komut sunucu tarafından yürütülebilmesiyle sonuçlanabilir:</span><span class="sxs-lookup"><span data-stu-id="236c7-129">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="236c7-130">Bu nedenle, <xref:System.Uri?displayProperty=nameWithType> sınıf ilk olarak yol sınırlayıcılarını iptal eder ve yol sıkıştırması uygular.</span><span class="sxs-lookup"><span data-stu-id="236c7-130">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="236c7-131">Yukarıdaki kötü amaçlı URL 'YI sınıf oluşturucusuna geçirmenin sonucu <xref:System.Uri?displayProperty=nameWithType> AŞAĞıDAKI URI ile sonuçlanır:</span><span class="sxs-lookup"><span data-stu-id="236c7-131">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="236c7-132">Bu varsayılan davranış, belirli bir düzen için ıgmesettings yapılandırma seçeneği kullanılarak yüzde olmayan kodlanmış yol sınırlayıcılarını kaçırılmamış şekilde değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="236c7-132">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="236c7-133">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="236c7-133">Configuration Files</span></span>  
 <span data-ttu-id="236c7-134">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="236c7-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="236c7-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="236c7-135">Example</span></span>  
 <span data-ttu-id="236c7-136">Aşağıdaki örnek, <xref:System.Uri> http şeması için yüzde kodlamalı bir yol sınırlayıcılarını yok etmek üzere sınıfı tarafından kullanılan bir yapılandırmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="236c7-136">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="236c7-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="236c7-137">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="236c7-138">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="236c7-138">Network Settings Schema</span></span>](index.md)
