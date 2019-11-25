---
title: <httpWebRequest> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/httpWebRequest
- http://schemas.microsoft.com/.NetConfiguration/v2.0#httpWebRequest
helpviewer_keywords:
- <httpWebRequest> element
- httpWebRequest element
ms.assetid: 52acd9d2-5bdc-4dc4-9c2a-f0a476ccbb31
ms.openlocfilehash: d33dadc14510feb00e05ca557b507b0cf8fa0dd0
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087453"
---
# <a name="httpwebrequest-element-network-settings"></a><span data-ttu-id="4229d-102">\<httpWebRequest > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="4229d-102">\<httpWebRequest> Element (Network Settings)</span></span>
<span data-ttu-id="4229d-103">Web isteği parametrelerini özelleştirir.</span><span class="sxs-lookup"><span data-stu-id="4229d-103">Customizes Web request parameters.</span></span>  

<span data-ttu-id="4229d-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="4229d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4229d-105">[**System. net >\<** ](system-net-element-network-settings.md) &nbsp;&nbsp;</span><span class="sxs-lookup"><span data-stu-id="4229d-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="4229d-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ayarları >** ](settings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="4229d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)</span></span>\
<span data-ttu-id="4229d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<httpWebRequest >**</span><span class="sxs-lookup"><span data-stu-id="4229d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpWebRequest>**</span></span>

## <a name="syntax"></a><span data-ttu-id="4229d-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4229d-108">Syntax</span></span>  
  
```xml  
<httpWebRequest  
  maximumResponseHeadersLength="size"  
  maximumErrorResponseLength="size"  
  maximumUnauthorizedUploadLength="size"  
  useUnsafeHeaderParsing="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4229d-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4229d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4229d-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4229d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4229d-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4229d-111">Attributes</span></span>  
  
|<span data-ttu-id="4229d-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="4229d-112">**Attribute**</span></span>|<span data-ttu-id="4229d-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="4229d-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`maximumResponseHeadersLength`|<span data-ttu-id="4229d-114">Yanıt üst bilgisinin kilobayt cinsinden uzunluk üst sınırını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4229d-114">Specifies the maximum length of a response header, in kilobytes.</span></span> <span data-ttu-id="4229d-115">Varsayılan değer 64 ' dir.</span><span class="sxs-lookup"><span data-stu-id="4229d-115">The default is 64.</span></span> <span data-ttu-id="4229d-116">-1 değeri, yanıt üst bilgilerine hiçbir boyut sınırının kullanılmayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4229d-116">A value of -1 indicates that no size limit will be imposed on the response headers.</span></span>|  
|`maximumErrorResponseLength`|<span data-ttu-id="4229d-117">Bir hata yanıtının kilobayt cinsinden uzunluk üst sınırını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4229d-117">Specifies the maximum length of an error response, in kilobytes.</span></span> <span data-ttu-id="4229d-118">Varsayılan değer 64 ' dir.</span><span class="sxs-lookup"><span data-stu-id="4229d-118">The default is 64.</span></span> <span data-ttu-id="4229d-119">-1 değeri, hata yanıtına hiçbir boyut sınırının kullanılamayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4229d-119">A value of -1 indicates that no size limit will be imposed on the error response.</span></span>|  
|`maximumUnauthorizedUploadLength`|<span data-ttu-id="4229d-120">Yetkisiz bir hata koduna yanıt olarak, bir karşıya yükleme işleminin bayt cinsinden uzunluk üst sınırını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4229d-120">Specifies the maximum length of an upload in response to an unauthorized error code, in bytes.</span></span> <span data-ttu-id="4229d-121">Varsayılan değer-1 ' dir.</span><span class="sxs-lookup"><span data-stu-id="4229d-121">The default is -1.</span></span> <span data-ttu-id="4229d-122">-1 değeri, karşıya yükleme sırasında hiçbir boyut sınırının kullanılamayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4229d-122">A value of -1 indicates that no size limit will be imposed on the upload.</span></span>|  
|`useUnsafeHeaderParsing`|<span data-ttu-id="4229d-123">Güvenli olmayan üstbilgi ayrıştırma özelliğinin etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4229d-123">Specifies whether unsafe header parsing is enabled.</span></span> <span data-ttu-id="4229d-124">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4229d-124">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4229d-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4229d-125">Child Elements</span></span>  
 <span data-ttu-id="4229d-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="4229d-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4229d-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4229d-127">Parent Elements</span></span>  
  
|<span data-ttu-id="4229d-128">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="4229d-128">**Element**</span></span>|<span data-ttu-id="4229d-129">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="4229d-129">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="4229d-130">Ayarlar</span><span class="sxs-lookup"><span data-stu-id="4229d-130">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="4229d-131"><xref:System.Net> ad alanı için temel ağ seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="4229d-131">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4229d-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4229d-132">Remarks</span></span>  
 <span data-ttu-id="4229d-133">.NET Framework, varsayılan olarak, URI ayrıştırma için RFC 2616 ' i kesinlikle uygular.</span><span class="sxs-lookup"><span data-stu-id="4229d-133">By default, the .NET Framework strictly enforces RFC 2616 for URI parsing.</span></span> <span data-ttu-id="4229d-134">Bazı sunucu yanıtları yasaklanmış alanlardaki denetim karakterlerini içerebilir ve bu da <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> yönteminin bir <xref:System.Net.WebException>oluşturmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="4229d-134">Some server responses may include control characters in prohibited fields, which will cause the <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> method to throw a <xref:System.Net.WebException>.</span></span> <span data-ttu-id="4229d-135">**Useunsafeheaderayrýþtýrmaya** **true**olarak ayarlanırsa <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> bu durumda throw; Bununla birlikte, uygulamanız çeşitli URI ayrıştırma saldırılarına karşı savunmasız olacaktır.</span><span class="sxs-lookup"><span data-stu-id="4229d-135">If **useUnsafeHeaderParsing** is set to **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> will not throw in this case; however, your application will be vulnerable to several forms of URI parsing attacks.</span></span> <span data-ttu-id="4229d-136">En iyi çözüm, yanıtın denetim karakterleri içermediği şekilde sunucuyu değiştirmemelidir.</span><span class="sxs-lookup"><span data-stu-id="4229d-136">The best solution is to change the server so that the response does not include control characters.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="4229d-137">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="4229d-137">Configuration Files</span></span>  
 <span data-ttu-id="4229d-138">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4229d-138">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4229d-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="4229d-139">Example</span></span>  
 <span data-ttu-id="4229d-140">Aşağıdaki örnek, normal en büyük üstbilgi uzunluğundan daha büyük bir değer belirtmeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="4229d-140">The following example shows how to specify a larger than normal maximum header length.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <httpWebRequest  
        maximumResponseHeadersLength="128"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4229d-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4229d-141">See also</span></span>

- <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>
- [<span data-ttu-id="4229d-142">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="4229d-142">Network Settings Schema</span></span>](index.md)
