---
title: schemeSettings için <clear> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: 65098332-ce61-4542-ab8d-e7dc0257d31f
ms.openlocfilehash: e954fef455d0279a945c33f2014913fea9d63064
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699439"
---
# <a name="clear-element-for-schemesettings-uri-settings"></a><span data-ttu-id="0c4bd-102">@no__t, ıviewmesettings için > öğesi (URI ayarları)</span><span class="sxs-lookup"><span data-stu-id="0c4bd-102">\<clear> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="0c4bd-103">Varolan tüm düzen ayarlarını temizler.</span><span class="sxs-lookup"><span data-stu-id="0c4bd-103">Clears all existing scheme settings.</span></span>  
  
[<span data-ttu-id="0c4bd-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="0c4bd-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="0c4bd-105">&nbsp; @ no__t-1[ **\<urı >** ](uri-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="0c4bd-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span></span>  
<span data-ttu-id="0c4bd-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<bir mesettings >** ](schemesettings-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="0c4bd-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)</span></span>  
<span data-ttu-id="0c4bd-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<clear >**</span><span class="sxs-lookup"><span data-stu-id="0c4bd-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c4bd-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0c4bd-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c4bd-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0c4bd-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0c4bd-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0c4bd-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c4bd-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0c4bd-111">Attributes</span></span>  
 <span data-ttu-id="0c4bd-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="0c4bd-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0c4bd-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0c4bd-113">Child Elements</span></span>  
 <span data-ttu-id="0c4bd-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="0c4bd-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0c4bd-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0c4bd-115">Parent Elements</span></span>  
  
|<span data-ttu-id="0c4bd-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="0c4bd-116">Element</span></span>|<span data-ttu-id="0c4bd-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c4bd-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0c4bd-118">\<Ramesettings > öğesi (Uri Ayarları)</span><span class="sxs-lookup"><span data-stu-id="0c4bd-118">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="0c4bd-119">Belirli düzenler için <xref:System.Uri> ' ın nasıl ayrıştıralınacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0c4bd-119">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c4bd-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0c4bd-120">Remarks</span></span>  
 <span data-ttu-id="0c4bd-121">Varsayılan olarak, <xref:System.Uri?displayProperty=nameWithType> sınıfı, yol sıkıştırmayı yürütmeden önce yüzde kodlamalı yol sınırlayıcılarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0c4bd-121">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="0c4bd-122">Bu, aşağıdaki gibi saldırılara karşı bir güvenlik mekanizması olarak uygulanmıştır:</span><span class="sxs-lookup"><span data-stu-id="0c4bd-122">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="0c4bd-123">Bu URI, yüzde kodlamalı karakterleri doğru şekilde işlemeyen modüllere geçiriliyorsa, aşağıdaki komut sunucu tarafından yürütülebilmesiyle sonuçlanabilir:</span><span class="sxs-lookup"><span data-stu-id="0c4bd-123">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="0c4bd-124">Bu nedenle, <xref:System.Uri?displayProperty=nameWithType> sınıfı ilk olarak yol sınırlayıcılarını yok eder ve ardından yol sıkıştırması uygular.</span><span class="sxs-lookup"><span data-stu-id="0c4bd-124">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="0c4bd-125">Yukarıdaki kötü amaçlı URL 'YI <xref:System.Uri?displayProperty=nameWithType> sınıf oluşturucusuna geçirmenin sonucu aşağıdaki URI ile sonuçlanır:</span><span class="sxs-lookup"><span data-stu-id="0c4bd-125">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="0c4bd-126">Bu varsayılan davranış, belirli bir düzen için ıgmesettings yapılandırma seçeneği kullanılarak yüzde olmayan kodlanmış yol sınırlayıcılarını kaçırılmamış şekilde değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="0c4bd-126">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="0c4bd-127">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="0c4bd-127">Configuration Files</span></span>  
 <span data-ttu-id="0c4bd-128">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0c4bd-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c4bd-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="0c4bd-129">Example</span></span>  
 <span data-ttu-id="0c4bd-130">Aşağıdaki örnek, tüm düzen ayarlarını temizleyen <xref:System.Uri> sınıfı tarafından kullanılan bir yapılandırmayı gösterir ve ardından http şeması için tam olmayan yüzde kodlamalı yol sınırlayıcıları için destek ekler.</span><span class="sxs-lookup"><span data-stu-id="0c4bd-130">The following example shows a configuration used by the <xref:System.Uri> class that clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0c4bd-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c4bd-131">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="0c4bd-132">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="0c4bd-132">Network Settings Schema</span></span>](index.md)
