---
title: <httpWebRequest> Öğesi (ağ ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/httpWebRequest
- http://schemas.microsoft.com/.NetConfiguration/v2.0#httpWebRequest
helpviewer_keywords:
- <httpWebRequest> element
- httpWebRequest element
ms.assetid: 52acd9d2-5bdc-4dc4-9c2a-f0a476ccbb31
ms.openlocfilehash: 722b2f726c9085f6dee6bad82044da3011b98702
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169305"
---
# <a name="httpwebrequest-element-network-settings"></a><span data-ttu-id="dfe8d-102">\<httpWebRequest > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="dfe8d-102">\<httpWebRequest> Element (Network Settings)</span></span>
<span data-ttu-id="dfe8d-103">Web isteği parametreleri özelleştirir.</span><span class="sxs-lookup"><span data-stu-id="dfe8d-103">Customizes Web request parameters.</span></span>  
  
 <span data-ttu-id="dfe8d-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="dfe8d-104">\<configuration></span></span>  
<span data-ttu-id="dfe8d-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="dfe8d-105">\<system.net></span></span>  
<span data-ttu-id="dfe8d-106">\<Ayarlar ></span><span class="sxs-lookup"><span data-stu-id="dfe8d-106">\<settings></span></span>  
<span data-ttu-id="dfe8d-107">\<httpWebRequest ></span><span class="sxs-lookup"><span data-stu-id="dfe8d-107">\<httpWebRequest></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfe8d-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dfe8d-108">Syntax</span></span>  
  
```xml  
<httpWebRequest  
  maximumResponseHeadersLength="size"  
  maximumErrorResponseLength="size"  
  maximumUnauthorizedUploadLength="size"  
  useUnsafeHeaderParsing="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dfe8d-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="dfe8d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="dfe8d-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dfe8d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dfe8d-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="dfe8d-111">Attributes</span></span>  
  
|**<span data-ttu-id="dfe8d-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="dfe8d-112">Attribute</span></span>**|**<span data-ttu-id="dfe8d-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dfe8d-113">Description</span></span>**|  
|-------------------|---------------------|  
|`maximumResponseHeadersLength`|<span data-ttu-id="dfe8d-114">Bir yanıt üstbilgisinin maksimum uzunluğunu kilobayt cinsinden belirtir.</span><span class="sxs-lookup"><span data-stu-id="dfe8d-114">Specifies the maximum length of a response header, in kilobytes.</span></span> <span data-ttu-id="dfe8d-115">64 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="dfe8d-115">The default is 64.</span></span> <span data-ttu-id="dfe8d-116">Boyut sınırı üzerinde yanıt üstbilgilerini uygulanan -1 değeri gösterir.</span><span class="sxs-lookup"><span data-stu-id="dfe8d-116">A value of -1 indicates that no size limit will be imposed on the response headers.</span></span>|  
|`maximumErrorResponseLength`|<span data-ttu-id="dfe8d-117">Bir hata yanıtı uzunluğu en fazla kilobayt cinsinden belirtir.</span><span class="sxs-lookup"><span data-stu-id="dfe8d-117">Specifies the maximum length of an error response, in kilobytes.</span></span> <span data-ttu-id="dfe8d-118">64 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="dfe8d-118">The default is 64.</span></span> <span data-ttu-id="dfe8d-119">Boyut sınırı üzerinde hata yanıtı uygulanan -1 değeri gösterir.</span><span class="sxs-lookup"><span data-stu-id="dfe8d-119">A value of -1 indicates that no size limit will be imposed on the error response.</span></span>|  
|`maximumUnauthorizedUploadLength`|<span data-ttu-id="dfe8d-120">Karşıya yükleme uzunluğu en fazla bayt cinsinden bir yetkisiz hata koduna karşılık belirtir.</span><span class="sxs-lookup"><span data-stu-id="dfe8d-120">Specifies the maximum length of an upload in response to an unauthorized error code, in bytes.</span></span> <span data-ttu-id="dfe8d-121">Varsayılan değer -1'dir.</span><span class="sxs-lookup"><span data-stu-id="dfe8d-121">The default is -1.</span></span> <span data-ttu-id="dfe8d-122">Boyut sınırı karşıya yükleme sırasında uygulanan -1 değeri gösterir.</span><span class="sxs-lookup"><span data-stu-id="dfe8d-122">A value of -1 indicates that no size limit will be imposed on the upload.</span></span>|  
|`useUnsafeHeaderParsing`|<span data-ttu-id="dfe8d-123">Güvenli olmayan bir üst bilgi ayrıştırma etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="dfe8d-123">Specifies whether unsafe header parsing is enabled.</span></span> <span data-ttu-id="dfe8d-124">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="dfe8d-124">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dfe8d-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="dfe8d-125">Child Elements</span></span>  
 <span data-ttu-id="dfe8d-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="dfe8d-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dfe8d-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="dfe8d-127">Parent Elements</span></span>  
  
|**<span data-ttu-id="dfe8d-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="dfe8d-128">Element</span></span>**|**<span data-ttu-id="dfe8d-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dfe8d-129">Description</span></span>**|  
|-----------------|---------------------|  
|[<span data-ttu-id="dfe8d-130">ayarlar</span><span class="sxs-lookup"><span data-stu-id="dfe8d-130">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="dfe8d-131">Temel ağ seçeneklerini yapılandırır <xref:System.Net> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="dfe8d-131">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dfe8d-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dfe8d-132">Remarks</span></span>  
 <span data-ttu-id="dfe8d-133">Varsayılan olarak, .NET Framework kesinlikle RFC 2616'urı ayrıştırmak için zorlar.</span><span class="sxs-lookup"><span data-stu-id="dfe8d-133">By default, the .NET Framework strictly enforces RFC 2616 for URI parsing.</span></span> <span data-ttu-id="dfe8d-134">Bazı sunucu yanıtları neden olur, izin verilmeyen alanlarına bir denetim karakteri içerebilir <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> yönteminin bir <xref:System.Net.WebException>.</span><span class="sxs-lookup"><span data-stu-id="dfe8d-134">Some server responses may include control characters in prohibited fields, which will cause the <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> method to throw a <xref:System.Net.WebException>.</span></span> <span data-ttu-id="dfe8d-135">Varsa **useUnsafeHeaderParsing** ayarlanır **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> oluşturmayacaksa bu durumda; ancak, uygulamanız URI saldırıları ayrıştırma birkaç biçimlerinin savunmasız olacaktır.</span><span class="sxs-lookup"><span data-stu-id="dfe8d-135">If **useUnsafeHeaderParsing** is set to **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> will not throw in this case; however, your application will be vulnerable to several forms of URI parsing attacks.</span></span> <span data-ttu-id="dfe8d-136">En uygun çözümü sunucu yanıt denetim karakterleri içermeyen şekilde değiştirmektir.</span><span class="sxs-lookup"><span data-stu-id="dfe8d-136">The best solution is to change the server so that the response does not include control characters.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="dfe8d-137">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="dfe8d-137">Configuration Files</span></span>  
 <span data-ttu-id="dfe8d-138">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dfe8d-138">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dfe8d-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="dfe8d-139">Example</span></span>  
 <span data-ttu-id="dfe8d-140">Aşağıdaki örnek, bir büyük belirtmek gösterilmektedir normal maksimum üstbilgi uzunluğundan.</span><span class="sxs-lookup"><span data-stu-id="dfe8d-140">The following example shows how to specify a larger than normal maximum header length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dfe8d-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dfe8d-141">See also</span></span>

- <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>
- [<span data-ttu-id="dfe8d-142">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="dfe8d-142">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
