---
title: schemeSettings için <add> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
ms.openlocfilehash: 027c7aaffea7950739f532309255d77afa031ada
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659550"
---
# <a name="add-element-for-schemesettings-uri-settings"></a><span data-ttu-id="99f6e-102">\<ıviewmesettings için > öğesi ekleme (URI ayarları)</span><span class="sxs-lookup"><span data-stu-id="99f6e-102">\<add> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="99f6e-103">Düzen adı için bir düzen ayarı ekler.</span><span class="sxs-lookup"><span data-stu-id="99f6e-103">Adds a scheme setting for a scheme name.</span></span>  
  
 <span data-ttu-id="99f6e-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="99f6e-104">\<configuration></span></span>  
<span data-ttu-id="99f6e-105">\<Uri ></span><span class="sxs-lookup"><span data-stu-id="99f6e-105">\<uri></span></span>  
<span data-ttu-id="99f6e-106">\<> düzeni</span><span class="sxs-lookup"><span data-stu-id="99f6e-106">\<schemeSettings></span></span>  
<span data-ttu-id="99f6e-107">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="99f6e-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99f6e-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="99f6e-108">Syntax</span></span>  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99f6e-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="99f6e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="99f6e-110">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="99f6e-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99f6e-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="99f6e-111">Attributes</span></span>  
  
|<span data-ttu-id="99f6e-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="99f6e-112">Attribute</span></span>|<span data-ttu-id="99f6e-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99f6e-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="99f6e-114">name</span><span class="sxs-lookup"><span data-stu-id="99f6e-114">name</span></span>|<span data-ttu-id="99f6e-115">Bu ayarın geçerli olduğu Düzen adı.</span><span class="sxs-lookup"><span data-stu-id="99f6e-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="99f6e-116">Yalnızca Name = "http" ve Name = "https" değerleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="99f6e-116">The only supported values are name="http" and name="https".</span></span>|  
  
## <a name="attribute-name-attribute"></a><span data-ttu-id="99f6e-117">{Öznitelik adı} Özniteliğe</span><span class="sxs-lookup"><span data-stu-id="99f6e-117">{Attribute name} Attribute</span></span>  
  
|<span data-ttu-id="99f6e-118">Değer</span><span class="sxs-lookup"><span data-stu-id="99f6e-118">Value</span></span>|<span data-ttu-id="99f6e-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99f6e-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="99f6e-120">genericUriParserOptions</span><span class="sxs-lookup"><span data-stu-id="99f6e-120">genericUriParserOptions</span></span>|<span data-ttu-id="99f6e-121">Bu şema için ayrıştırıcı seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="99f6e-121">The parser options for this scheme.</span></span> <span data-ttu-id="99f6e-122">Yalnızca genericUriParserOptions = "DontUnescapePathDotsAndSlashes" değeri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="99f6e-122">The only supported value is genericUriParserOptions= "DontUnescapePathDotsAndSlashes".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="99f6e-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="99f6e-123">Child Elements</span></span>  
 <span data-ttu-id="99f6e-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="99f6e-124">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="99f6e-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="99f6e-125">Parent Elements</span></span>  
  
|<span data-ttu-id="99f6e-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="99f6e-126">Element</span></span>|<span data-ttu-id="99f6e-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99f6e-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="99f6e-128">\<> düzeni öğesi (URI ayarları)</span><span class="sxs-lookup"><span data-stu-id="99f6e-128">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="99f6e-129">Belirli düzenler için <xref:System.Uri> nasıl ayrıştırılacaksınız belirtir.</span><span class="sxs-lookup"><span data-stu-id="99f6e-129">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99f6e-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="99f6e-130">Remarks</span></span>  
 <span data-ttu-id="99f6e-131">Varsayılan olarak, <xref:System.Uri?displayProperty=nameWithType> sınıfı yol sıkıştırmayı yürütmeden önce, yüzde olarak kodlanmış yol sınırlayıcılarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="99f6e-131">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="99f6e-132">Bu, aşağıdaki gibi saldırılara karşı bir güvenlik mekanizması olarak uygulanmıştır:</span><span class="sxs-lookup"><span data-stu-id="99f6e-132">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="99f6e-133">Bu URI, yüzde kodlamalı karakterleri doğru şekilde işlemeyen modüllere geçiriliyorsa, aşağıdaki komut sunucu tarafından yürütülebilmesiyle sonuçlanabilir:</span><span class="sxs-lookup"><span data-stu-id="99f6e-133">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="99f6e-134">Bu nedenle, sınıf <xref:System.Uri?displayProperty=nameWithType> ilk olarak yol sınırlayıcılarını iptal eder ve yol sıkıştırması uygular.</span><span class="sxs-lookup"><span data-stu-id="99f6e-134">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="99f6e-135">Yukarıdaki kötü amaçlı URL 'yi sınıf oluşturucusuna geçirmenin sonucu <xref:System.Uri?displayProperty=nameWithType> aşağıdaki URI ile sonuçlanır:</span><span class="sxs-lookup"><span data-stu-id="99f6e-135">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="99f6e-136">Bu varsayılan davranış, belirli bir düzen için ıgmesettings yapılandırma seçeneği kullanılarak yüzde olmayan kodlanmış yol sınırlayıcılarını kaçırılmamış şekilde değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="99f6e-136">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="99f6e-137">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="99f6e-137">Configuration Files</span></span>  
 <span data-ttu-id="99f6e-138">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="99f6e-138">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="99f6e-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="99f6e-139">Example</span></span>  
 <span data-ttu-id="99f6e-140">Aşağıdaki örnek, http şeması için yüzde kodlamalı bir <xref:System.Uri> yol sınırlayıcılarını yok etmek üzere sınıfı tarafından kullanılan bir yapılandırmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="99f6e-140">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="99f6e-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99f6e-141">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="99f6e-142">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="99f6e-142">Network Settings Schema</span></span>](index.md)
