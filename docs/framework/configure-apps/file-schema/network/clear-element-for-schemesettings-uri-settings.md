---
title: schemeSettings için <clear> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: 65098332-ce61-4542-ab8d-e7dc0257d31f
ms.openlocfilehash: 17069a56a8647871e98d70826a97a8fe407a0887
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91205067"
---
# <a name="clear-element-for-schemesettings-uri-settings"></a><span data-ttu-id="17340-102">schemeSettings için \<clear> Öğesi (Uri Ayarları)</span><span class="sxs-lookup"><span data-stu-id="17340-102">\<clear> Element for schemeSettings (Uri Settings)</span></span>

<span data-ttu-id="17340-103">Varolan tüm düzen ayarlarını temizler.</span><span class="sxs-lookup"><span data-stu-id="17340-103">Clears all existing scheme settings.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="17340-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="17340-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="17340-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="17340-105">Attributes and Elements</span></span>  

 <span data-ttu-id="17340-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="17340-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="17340-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="17340-107">Attributes</span></span>  

 <span data-ttu-id="17340-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="17340-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="17340-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="17340-109">Child Elements</span></span>  

 <span data-ttu-id="17340-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="17340-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="17340-111">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="17340-111">Parent Elements</span></span>  
  
|<span data-ttu-id="17340-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="17340-112">Element</span></span>|<span data-ttu-id="17340-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="17340-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="17340-114">\<schemeSettings> Öğesi (URI ayarları)</span><span class="sxs-lookup"><span data-stu-id="17340-114">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="17340-115"><xref:System.Uri>Belirli düzenler için nasıl ayrıştırılacaksınız belirtir.</span><span class="sxs-lookup"><span data-stu-id="17340-115">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17340-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="17340-116">Remarks</span></span>  

 <span data-ttu-id="17340-117">Varsayılan olarak, <xref:System.Uri?displayProperty=nameWithType> sınıfı yol sıkıştırmayı yürütmeden önce, yüzde olarak kodlanmış yol sınırlayıcılarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="17340-117">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="17340-118">Bu, aşağıdaki gibi saldırılara karşı bir güvenlik mekanizması olarak uygulanmıştır:</span><span class="sxs-lookup"><span data-stu-id="17340-118">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="17340-119">Bu URI, yüzde kodlamalı karakterleri doğru şekilde işlemeyen modüllere geçiriliyorsa, aşağıdaki komut sunucu tarafından yürütülebilmesiyle sonuçlanabilir:</span><span class="sxs-lookup"><span data-stu-id="17340-119">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="17340-120">Bu nedenle, <xref:System.Uri?displayProperty=nameWithType> sınıf ilk olarak yol sınırlayıcılarını iptal eder ve yol sıkıştırması uygular.</span><span class="sxs-lookup"><span data-stu-id="17340-120">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="17340-121">Yukarıdaki kötü amaçlı URL 'YI sınıf oluşturucusuna geçirmenin sonucu <xref:System.Uri?displayProperty=nameWithType> AŞAĞıDAKI URI ile sonuçlanır:</span><span class="sxs-lookup"><span data-stu-id="17340-121">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="17340-122">Bu varsayılan davranış, belirli bir düzen için ıgmesettings yapılandırma seçeneği kullanılarak yüzde olmayan kodlanmış yol sınırlayıcılarını kaçırılmamış şekilde değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="17340-122">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="17340-123">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="17340-123">Configuration Files</span></span>  

 <span data-ttu-id="17340-124">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="17340-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="17340-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="17340-125">Example</span></span>  

 <span data-ttu-id="17340-126">Aşağıdaki örnek, <xref:System.Uri> tüm düzen ayarlarını temizleyen sınıf tarafından kullanılan bir yapılandırmayı gösterir ve ardından http şeması için tam olmayan yüzde kodlamalı yol sınırlayıcıları için destek ekler.</span><span class="sxs-lookup"><span data-stu-id="17340-126">The following example shows a configuration used by the <xref:System.Uri> class that clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="17340-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17340-127">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="17340-128">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="17340-128">Network Settings Schema</span></span>](index.md)
