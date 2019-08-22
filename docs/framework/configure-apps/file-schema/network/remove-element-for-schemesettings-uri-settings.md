---
title: schemeSettings için <remove> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: 4095ba51-de20-4f87-b562-018abe422c91
ms.openlocfilehash: 4a891eb8a2fd2d66b6435e2ae774ecd4a157c0f9
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659227"
---
# <a name="remove-element-for-schemesettings-uri-settings"></a><span data-ttu-id="34d77-102">\<ıviewmesettings için > öğesini kaldır (URI ayarları)</span><span class="sxs-lookup"><span data-stu-id="34d77-102">\<remove> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="34d77-103">Düzen adı için bir düzen ayarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="34d77-103">Removes a scheme setting for a scheme name.</span></span>  
  
 <span data-ttu-id="34d77-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="34d77-104">\<configuration></span></span>  
<span data-ttu-id="34d77-105">\<Uri ></span><span class="sxs-lookup"><span data-stu-id="34d77-105">\<uri></span></span>  
<span data-ttu-id="34d77-106">\<> düzeni</span><span class="sxs-lookup"><span data-stu-id="34d77-106">\<schemeSettings></span></span>  
<span data-ttu-id="34d77-107">\<> Kaldır</span><span class="sxs-lookup"><span data-stu-id="34d77-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34d77-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="34d77-108">Syntax</span></span>  
  
```xml  
<remove
  name="http|https"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34d77-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="34d77-109">Attributes and Elements</span></span>  
 <span data-ttu-id="34d77-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="34d77-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34d77-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="34d77-111">Attributes</span></span>  
  
|<span data-ttu-id="34d77-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="34d77-112">Attribute</span></span>|<span data-ttu-id="34d77-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34d77-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="34d77-114">name</span><span class="sxs-lookup"><span data-stu-id="34d77-114">name</span></span>|<span data-ttu-id="34d77-115">Bu ayarın geçerli olduğu Düzen adı.</span><span class="sxs-lookup"><span data-stu-id="34d77-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="34d77-116">Yalnızca Name = "http" ve Name = "https" değerleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="34d77-116">The only supported values are name="http" and name="https".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="34d77-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="34d77-117">Child Elements</span></span>  
 <span data-ttu-id="34d77-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="34d77-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="34d77-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="34d77-119">Parent Elements</span></span>  
  
|<span data-ttu-id="34d77-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="34d77-120">Element</span></span>|<span data-ttu-id="34d77-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34d77-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="34d77-122">\<> düzeni öğesi (URI ayarları)</span><span class="sxs-lookup"><span data-stu-id="34d77-122">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="34d77-123">Belirli düzenler için <xref:System.Uri> nasıl ayrıştırılacaksınız belirtir.</span><span class="sxs-lookup"><span data-stu-id="34d77-123">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34d77-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="34d77-124">Remarks</span></span>  
 <span data-ttu-id="34d77-125">Varsayılan olarak, <xref:System.Uri?displayProperty=nameWithType> sınıfı yol sıkıştırmayı yürütmeden önce, yüzde olarak kodlanmış yol sınırlayıcılarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="34d77-125">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="34d77-126">Bu, aşağıdaki gibi saldırılara karşı bir güvenlik mekanizması olarak uygulanmıştır:</span><span class="sxs-lookup"><span data-stu-id="34d77-126">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="34d77-127">Bu URI, yüzde kodlamalı karakterleri doğru şekilde işlemeyen modüllere geçiriliyorsa, aşağıdaki komut sunucu tarafından yürütülebilmesiyle sonuçlanabilir:</span><span class="sxs-lookup"><span data-stu-id="34d77-127">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="34d77-128">Bu nedenle, sınıf <xref:System.Uri?displayProperty=nameWithType> ilk olarak yol sınırlayıcılarını iptal eder ve yol sıkıştırması uygular.</span><span class="sxs-lookup"><span data-stu-id="34d77-128">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="34d77-129">Yukarıdaki kötü amaçlı URL 'yi sınıf oluşturucusuna geçirmenin sonucu <xref:System.Uri?displayProperty=nameWithType> aşağıdaki URI ile sonuçlanır:</span><span class="sxs-lookup"><span data-stu-id="34d77-129">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="34d77-130">Bu varsayılan davranış, belirli bir düzen için ıgmesettings yapılandırma seçeneği kullanılarak yüzde olmayan kodlanmış yol sınırlayıcılarını kaçırılmamış şekilde değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="34d77-130">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="34d77-131">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="34d77-131">Configuration Files</span></span>  
 <span data-ttu-id="34d77-132">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="34d77-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="34d77-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="34d77-133">Example</span></span>  
 <span data-ttu-id="34d77-134">Aşağıdaki örnek, http şeması için tüm düzen ayarlarını <xref:System.Uri> kaldıran sınıf tarafından kullanılan bir yapılandırmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="34d77-134">The following example shows a configuration used by the <xref:System.Uri> class that removes any scheme settings for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <remove name="http"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="34d77-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34d77-135">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="34d77-136">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="34d77-136">Network Settings Schema</span></span>](index.md)
