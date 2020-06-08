---
title: <httpWebRequest> Öğesi (Ağ Ayarları)
description: <httpWebRequest>Ağ ayarları öğesi .NET Framework Web isteği parametrelerini özelleştirir.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/httpWebRequest
- http://schemas.microsoft.com/.NetConfiguration/v2.0#httpWebRequest
helpviewer_keywords:
- <httpWebRequest> element
- httpWebRequest element
ms.assetid: 52acd9d2-5bdc-4dc4-9c2a-f0a476ccbb31
ms.openlocfilehash: 59ab425dcef8ac5283035910a9d78a89a16be8b1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504595"
---
# <a name="httpwebrequest-element-network-settings"></a><span data-ttu-id="d8c2f-103">\<httpWebRequest> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="d8c2f-103">\<httpWebRequest> Element (Network Settings)</span></span>
<span data-ttu-id="d8c2f-104">Web isteği parametrelerini özelleştirir.</span><span class="sxs-lookup"><span data-stu-id="d8c2f-104">Customizes Web request parameters.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpWebRequest>**

## <a name="syntax"></a><span data-ttu-id="d8c2f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8c2f-105">Syntax</span></span>  
  
```xml  
<httpWebRequest  
  maximumResponseHeadersLength="size"  
  maximumErrorResponseLength="size"  
  maximumUnauthorizedUploadLength="size"  
  useUnsafeHeaderParsing="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8c2f-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d8c2f-106">Attributes and Elements</span></span>  
 <span data-ttu-id="d8c2f-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d8c2f-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8c2f-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d8c2f-108">Attributes</span></span>  
  
|<span data-ttu-id="d8c2f-109">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="d8c2f-109">**Attribute**</span></span>|<span data-ttu-id="d8c2f-110">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="d8c2f-110">**Description**</span></span>|  
|-------------------|---------------------|  
|`maximumResponseHeadersLength`|<span data-ttu-id="d8c2f-111">Yanıt üst bilgisinin kilobayt cinsinden uzunluk üst sınırını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d8c2f-111">Specifies the maximum length of a response header, in kilobytes.</span></span> <span data-ttu-id="d8c2f-112">Varsayılan değer 64 ' dir.</span><span class="sxs-lookup"><span data-stu-id="d8c2f-112">The default is 64.</span></span> <span data-ttu-id="d8c2f-113">-1 değeri, yanıt üst bilgilerine hiçbir boyut sınırının kullanılmayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8c2f-113">A value of -1 indicates that no size limit will be imposed on the response headers.</span></span>|  
|`maximumErrorResponseLength`|<span data-ttu-id="d8c2f-114">Bir hata yanıtının kilobayt cinsinden uzunluk üst sınırını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d8c2f-114">Specifies the maximum length of an error response, in kilobytes.</span></span> <span data-ttu-id="d8c2f-115">Varsayılan değer 64 ' dir.</span><span class="sxs-lookup"><span data-stu-id="d8c2f-115">The default is 64.</span></span> <span data-ttu-id="d8c2f-116">-1 değeri, hata yanıtına hiçbir boyut sınırının kullanılamayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8c2f-116">A value of -1 indicates that no size limit will be imposed on the error response.</span></span>|  
|`maximumUnauthorizedUploadLength`|<span data-ttu-id="d8c2f-117">Yetkisiz bir hata koduna yanıt olarak, bir karşıya yükleme işleminin bayt cinsinden uzunluk üst sınırını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d8c2f-117">Specifies the maximum length of an upload in response to an unauthorized error code, in bytes.</span></span> <span data-ttu-id="d8c2f-118">Varsayılan değer-1 ' dir.</span><span class="sxs-lookup"><span data-stu-id="d8c2f-118">The default is -1.</span></span> <span data-ttu-id="d8c2f-119">-1 değeri, karşıya yükleme sırasında hiçbir boyut sınırının kullanılamayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8c2f-119">A value of -1 indicates that no size limit will be imposed on the upload.</span></span>|  
|`useUnsafeHeaderParsing`|<span data-ttu-id="d8c2f-120">Güvenli olmayan üstbilgi ayrıştırma özelliğinin etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d8c2f-120">Specifies whether unsafe header parsing is enabled.</span></span> <span data-ttu-id="d8c2f-121">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="d8c2f-121">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d8c2f-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d8c2f-122">Child Elements</span></span>  
 <span data-ttu-id="d8c2f-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="d8c2f-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d8c2f-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d8c2f-124">Parent Elements</span></span>  
  
|<span data-ttu-id="d8c2f-125">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="d8c2f-125">**Element**</span></span>|<span data-ttu-id="d8c2f-126">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="d8c2f-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d8c2f-127">ayarlar</span><span class="sxs-lookup"><span data-stu-id="d8c2f-127">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="d8c2f-128">Ad alanı için temel ağ seçeneklerini yapılandırır <xref:System.Net> .</span><span class="sxs-lookup"><span data-stu-id="d8c2f-128">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8c2f-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8c2f-129">Remarks</span></span>  
 <span data-ttu-id="d8c2f-130">.NET Framework, varsayılan olarak, URI ayrıştırma için RFC 2616 ' i kesinlikle uygular.</span><span class="sxs-lookup"><span data-stu-id="d8c2f-130">By default, the .NET Framework strictly enforces RFC 2616 for URI parsing.</span></span> <span data-ttu-id="d8c2f-131">Bazı sunucu yanıtları yasaklanmış alanlardaki denetim karakterlerini içerebilir ve bu, metodun bir oluşturmasına neden olur <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> <xref:System.Net.WebException> .</span><span class="sxs-lookup"><span data-stu-id="d8c2f-131">Some server responses may include control characters in prohibited fields, which will cause the <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> method to throw a <xref:System.Net.WebException>.</span></span> <span data-ttu-id="d8c2f-132">**Useunsafeheaderayrıştırma** **true**olarak ayarlanırsa, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> Bu durumda throw olmaz; ancak, uygulamanız bazı URI ayrıştırma saldırılarına karşı savunmasız olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d8c2f-132">If **useUnsafeHeaderParsing** is set to **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> will not throw in this case; however, your application will be vulnerable to several forms of URI parsing attacks.</span></span> <span data-ttu-id="d8c2f-133">En iyi çözüm, yanıtın denetim karakterleri içermediği şekilde sunucuyu değiştirmemelidir.</span><span class="sxs-lookup"><span data-stu-id="d8c2f-133">The best solution is to change the server so that the response does not include control characters.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d8c2f-134">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="d8c2f-134">Configuration Files</span></span>  
 <span data-ttu-id="d8c2f-135">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d8c2f-135">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8c2f-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="d8c2f-136">Example</span></span>  
 <span data-ttu-id="d8c2f-137">Aşağıdaki örnek, normal en büyük üstbilgi uzunluğundan daha büyük bir değer belirtmeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8c2f-137">The following example shows how to specify a larger than normal maximum header length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d8c2f-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8c2f-138">See also</span></span>

- <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>
- [<span data-ttu-id="d8c2f-139">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="d8c2f-139">Network Settings Schema</span></span>](index.md)
