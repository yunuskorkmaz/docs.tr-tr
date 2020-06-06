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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74087453"
---
# <a name="httpwebrequest-element-network-settings"></a><span data-ttu-id="6420c-102">\<httpWebRequest> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="6420c-102">\<httpWebRequest> Element (Network Settings)</span></span>
<span data-ttu-id="6420c-103">Web isteği parametrelerini özelleştirir.</span><span class="sxs-lookup"><span data-stu-id="6420c-103">Customizes Web request parameters.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpWebRequest>**

## <a name="syntax"></a><span data-ttu-id="6420c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6420c-104">Syntax</span></span>  
  
```xml  
<httpWebRequest  
  maximumResponseHeadersLength="size"  
  maximumErrorResponseLength="size"  
  maximumUnauthorizedUploadLength="size"  
  useUnsafeHeaderParsing="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6420c-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6420c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="6420c-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6420c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6420c-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6420c-107">Attributes</span></span>  
  
|<span data-ttu-id="6420c-108">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="6420c-108">**Attribute**</span></span>|<span data-ttu-id="6420c-109">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="6420c-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`maximumResponseHeadersLength`|<span data-ttu-id="6420c-110">Yanıt üst bilgisinin kilobayt cinsinden uzunluk üst sınırını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6420c-110">Specifies the maximum length of a response header, in kilobytes.</span></span> <span data-ttu-id="6420c-111">Varsayılan değer 64 ' dir.</span><span class="sxs-lookup"><span data-stu-id="6420c-111">The default is 64.</span></span> <span data-ttu-id="6420c-112">-1 değeri, yanıt üst bilgilerine hiçbir boyut sınırının kullanılmayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6420c-112">A value of -1 indicates that no size limit will be imposed on the response headers.</span></span>|  
|`maximumErrorResponseLength`|<span data-ttu-id="6420c-113">Bir hata yanıtının kilobayt cinsinden uzunluk üst sınırını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6420c-113">Specifies the maximum length of an error response, in kilobytes.</span></span> <span data-ttu-id="6420c-114">Varsayılan değer 64 ' dir.</span><span class="sxs-lookup"><span data-stu-id="6420c-114">The default is 64.</span></span> <span data-ttu-id="6420c-115">-1 değeri, hata yanıtına hiçbir boyut sınırının kullanılamayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6420c-115">A value of -1 indicates that no size limit will be imposed on the error response.</span></span>|  
|`maximumUnauthorizedUploadLength`|<span data-ttu-id="6420c-116">Yetkisiz bir hata koduna yanıt olarak, bir karşıya yükleme işleminin bayt cinsinden uzunluk üst sınırını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6420c-116">Specifies the maximum length of an upload in response to an unauthorized error code, in bytes.</span></span> <span data-ttu-id="6420c-117">Varsayılan değer-1 ' dir.</span><span class="sxs-lookup"><span data-stu-id="6420c-117">The default is -1.</span></span> <span data-ttu-id="6420c-118">-1 değeri, karşıya yükleme sırasında hiçbir boyut sınırının kullanılamayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6420c-118">A value of -1 indicates that no size limit will be imposed on the upload.</span></span>|  
|`useUnsafeHeaderParsing`|<span data-ttu-id="6420c-119">Güvenli olmayan üstbilgi ayrıştırma özelliğinin etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6420c-119">Specifies whether unsafe header parsing is enabled.</span></span> <span data-ttu-id="6420c-120">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="6420c-120">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6420c-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6420c-121">Child Elements</span></span>  
 <span data-ttu-id="6420c-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="6420c-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6420c-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6420c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="6420c-124">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="6420c-124">**Element**</span></span>|<span data-ttu-id="6420c-125">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="6420c-125">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6420c-126">ayarlar</span><span class="sxs-lookup"><span data-stu-id="6420c-126">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="6420c-127">Ad alanı için temel ağ seçeneklerini yapılandırır <xref:System.Net> .</span><span class="sxs-lookup"><span data-stu-id="6420c-127">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6420c-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6420c-128">Remarks</span></span>  
 <span data-ttu-id="6420c-129">.NET Framework, varsayılan olarak, URI ayrıştırma için RFC 2616 ' i kesinlikle uygular.</span><span class="sxs-lookup"><span data-stu-id="6420c-129">By default, the .NET Framework strictly enforces RFC 2616 for URI parsing.</span></span> <span data-ttu-id="6420c-130">Bazı sunucu yanıtları yasaklanmış alanlardaki denetim karakterlerini içerebilir ve bu, metodun bir oluşturmasına neden olur <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> <xref:System.Net.WebException> .</span><span class="sxs-lookup"><span data-stu-id="6420c-130">Some server responses may include control characters in prohibited fields, which will cause the <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> method to throw a <xref:System.Net.WebException>.</span></span> <span data-ttu-id="6420c-131">**Useunsafeheaderayrıştırma** **true**olarak ayarlanırsa, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> Bu durumda throw olmaz; ancak, uygulamanız bazı URI ayrıştırma saldırılarına karşı savunmasız olacaktır.</span><span class="sxs-lookup"><span data-stu-id="6420c-131">If **useUnsafeHeaderParsing** is set to **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> will not throw in this case; however, your application will be vulnerable to several forms of URI parsing attacks.</span></span> <span data-ttu-id="6420c-132">En iyi çözüm, yanıtın denetim karakterleri içermediği şekilde sunucuyu değiştirmemelidir.</span><span class="sxs-lookup"><span data-stu-id="6420c-132">The best solution is to change the server so that the response does not include control characters.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="6420c-133">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="6420c-133">Configuration Files</span></span>  
 <span data-ttu-id="6420c-134">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6420c-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6420c-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="6420c-135">Example</span></span>  
 <span data-ttu-id="6420c-136">Aşağıdaki örnek, normal en büyük üstbilgi uzunluğundan daha büyük bir değer belirtmeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="6420c-136">The following example shows how to specify a larger than normal maximum header length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6420c-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6420c-137">See also</span></span>

- <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>
- [<span data-ttu-id="6420c-138">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="6420c-138">Network Settings Schema</span></span>](index.md)
