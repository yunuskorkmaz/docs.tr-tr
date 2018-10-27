---
title: '&lt;Temizle&gt; schemeSettings (Uri ayarları) için'
ms.date: 03/30/2017
ms.assetid: 65098332-ce61-4542-ab8d-e7dc0257d31f
ms.openlocfilehash: b7dba6335f12b546fa4309ba9eb26d6007ec1bac
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50043302"
---
# <a name="ltcleargt-element-for-schemesettings-uri-settings"></a><span data-ttu-id="4f533-102">&lt;Temizle&gt; schemeSettings (Uri ayarları) için</span><span class="sxs-lookup"><span data-stu-id="4f533-102">&lt;clear&gt; Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="4f533-103">Tüm mevcut düzeni ayarlarını temizler.</span><span class="sxs-lookup"><span data-stu-id="4f533-103">Clears all existing scheme settings.</span></span>  
  
 <span data-ttu-id="4f533-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="4f533-104">\<configuration></span></span>  
<span data-ttu-id="4f533-105">\<URI ></span><span class="sxs-lookup"><span data-stu-id="4f533-105">\<uri></span></span>  
<span data-ttu-id="4f533-106">\<schemeSettings ></span><span class="sxs-lookup"><span data-stu-id="4f533-106">\<schemeSettings></span></span>  
<span data-ttu-id="4f533-107">\<Temizleme ></span><span class="sxs-lookup"><span data-stu-id="4f533-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f533-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4f533-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4f533-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4f533-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4f533-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4f533-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4f533-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4f533-111">Attributes</span></span>  
 <span data-ttu-id="4f533-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="4f533-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4f533-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4f533-113">Child Elements</span></span>  
 <span data-ttu-id="4f533-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="4f533-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4f533-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4f533-115">Parent Elements</span></span>  
  
|<span data-ttu-id="4f533-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="4f533-116">Element</span></span>|<span data-ttu-id="4f533-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4f533-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4f533-118">\<schemeSettings > öğesi (Uri ayarları)</span><span class="sxs-lookup"><span data-stu-id="4f533-118">\<schemeSettings> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="4f533-119">Belirtir nasıl bir <xref:System.Uri> belirli düzenleri için ayrıştırılacak.</span><span class="sxs-lookup"><span data-stu-id="4f533-119">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f533-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4f533-120">Remarks</span></span>  
 <span data-ttu-id="4f533-121">Varsayılan olarak, <xref:System.Uri?displayProperty=nameWithType> sınıfı Geri Al çıkışları yüzde yolu sınırlayıcı yolu sıkıştırma yürütmeden önce kodlanmış.</span><span class="sxs-lookup"><span data-stu-id="4f533-121">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="4f533-122">Bu, aşağıdaki gibi saldırılarına karşı bir güvenlik mekanizması olarak uygulanmıştır:</span><span class="sxs-lookup"><span data-stu-id="4f533-122">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="4f533-123">Bu URI iletilir aşağı modülleri yüzde işlenmemesinin karakterlerin doğru kodlanmış, sunucu tarafından çalıştırılan aşağıdaki komutu neden:</span><span class="sxs-lookup"><span data-stu-id="4f533-123">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="4f533-124">Bu nedenle, <xref:System.Uri?displayProperty=nameWithType> sınıf ilk geri al çıkışları yol ayırıcıları ve yol sıkıştırma uygular.</span><span class="sxs-lookup"><span data-stu-id="4f533-124">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="4f533-125">Yukarıda kötü amaçlı URL'sini geçirme sonucunu <xref:System.Uri?displayProperty=nameWithType> sınıf oluşturucu sonuçları aşağıdaki URI:</span><span class="sxs-lookup"><span data-stu-id="4f533-125">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="4f533-126">Bu varsayılan davranışı değil, için belirli bir düzeni schemeSettings yapılandırma seçeneğini kullanarak kaldırın kaçış yüzde kodlanmış yolu sınırlayıcılar için değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="4f533-126">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="4f533-127">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="4f533-127">Configuration Files</span></span>  
 <span data-ttu-id="4f533-128">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4f533-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f533-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="4f533-129">Example</span></span>  
 <span data-ttu-id="4f533-130">Aşağıdaki örnek tarafından kullanılan bir yapılandırma gösterir <xref:System.Uri> sınıfı, tüm düzeni ayarlarını temizler ve ardından http düzeni için yol yüzde olarak kodlanmış sınırlayıcılar kaçış değil desteği ekler.</span><span class="sxs-lookup"><span data-stu-id="4f533-130">The following example shows a configuration used by the <xref:System.Uri> class that clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4f533-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4f533-131">See Also</span></span>  
 <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>  
 <xref:System.GenericUriParserOptions?displayProperty=nameWithType>  
 <xref:System.Uri?displayProperty=nameWithType>  
 [<span data-ttu-id="4f533-132">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="4f533-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
