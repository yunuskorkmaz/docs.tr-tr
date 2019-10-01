---
title: <webProxyScript> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webProxyScript
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/webProxyScript
helpviewer_keywords:
- <webProxyScript> element
- webProxyScript element
ms.assetid: a13c26db-6218-4af3-9696-38f24b23bfac
ms.openlocfilehash: 2abab3de2965c31c11d9acaf7b78f3a668563506
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697449"
---
# <a name="webproxyscript-element-network-settings"></a><span data-ttu-id="7c5fe-102">\<webProxyScript > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="7c5fe-102">\<webProxyScript> Element (Network Settings)</span></span>
<span data-ttu-id="7c5fe-103">Web proxy 'lerini keşfetme için kullanılan betiğin özelliklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="7c5fe-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  
  
[<span data-ttu-id="7c5fe-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="7c5fe-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="7c5fe-105">&nbsp; @ no__t-1[ **@no__t -4system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="7c5fe-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="7c5fe-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<settings >** ](settings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="7c5fe-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)</span></span>  
<span data-ttu-id="7c5fe-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<webProxyScript >**</span><span class="sxs-lookup"><span data-stu-id="7c5fe-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webProxyScript>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c5fe-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7c5fe-108">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7c5fe-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7c5fe-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7c5fe-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7c5fe-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7c5fe-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7c5fe-111">Attributes</span></span>  
  
|<span data-ttu-id="7c5fe-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7c5fe-112">Attribute</span></span>|<span data-ttu-id="7c5fe-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7c5fe-113">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="7c5fe-114">Betiği saat, dakika ve saniye cinsinden indirmek için en uzun süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="7c5fe-114">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="7c5fe-115">Varsayılan değer bir dakikadır.</span><span class="sxs-lookup"><span data-stu-id="7c5fe-115">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7c5fe-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7c5fe-116">Child Elements</span></span>  
 <span data-ttu-id="7c5fe-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="7c5fe-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7c5fe-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7c5fe-118">Parent Elements</span></span>  
  
|<span data-ttu-id="7c5fe-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="7c5fe-119">Element</span></span>|<span data-ttu-id="7c5fe-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7c5fe-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c5fe-121">Ayarlar</span><span class="sxs-lookup"><span data-stu-id="7c5fe-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="7c5fe-122">@No__t-0 ad alanı için temel ağ seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="7c5fe-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c5fe-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7c5fe-123">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="7c5fe-124">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="7c5fe-124">Configuration Files</span></span>  
 <span data-ttu-id="7c5fe-125">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7c5fe-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c5fe-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c5fe-126">See also</span></span>

- [<span data-ttu-id="7c5fe-127">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="7c5fe-127">Network Settings Schema</span></span>](index.md)
