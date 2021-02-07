---
description: 'Daha fazla bilgi edinin: <webProxyScript> öğesi (ağ ayarları)'
title: <webProxyScript> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webProxyScript
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/webProxyScript
helpviewer_keywords:
- <webProxyScript> element
- webProxyScript element
ms.assetid: a13c26db-6218-4af3-9696-38f24b23bfac
ms.openlocfilehash: 1627b6650582202f3f1a4c1fdebf2d183e4a894b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740112"
---
# <a name="webproxyscript-element-network-settings"></a><span data-ttu-id="50509-103">\<webProxyScript> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="50509-103">\<webProxyScript> Element (Network Settings)</span></span>

<span data-ttu-id="50509-104">Web proxy 'lerini keşfetme için kullanılan betiğin özelliklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="50509-104">Configures the characteristics of the script used to discover Web proxies.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webProxyScript>**

## <a name="syntax"></a><span data-ttu-id="50509-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="50509-105">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="50509-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="50509-106">Attributes and Elements</span></span>  

 <span data-ttu-id="50509-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="50509-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="50509-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="50509-108">Attributes</span></span>  
  
|<span data-ttu-id="50509-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="50509-109">Attribute</span></span>|<span data-ttu-id="50509-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50509-110">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="50509-111">Betiği saat, dakika ve saniye cinsinden indirmek için en uzun süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="50509-111">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="50509-112">Varsayılan değer bir dakikadır.</span><span class="sxs-lookup"><span data-stu-id="50509-112">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="50509-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="50509-113">Child Elements</span></span>  

 <span data-ttu-id="50509-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="50509-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="50509-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="50509-115">Parent Elements</span></span>  
  
|<span data-ttu-id="50509-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="50509-116">Element</span></span>|<span data-ttu-id="50509-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50509-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="50509-118">ayarlar</span><span class="sxs-lookup"><span data-stu-id="50509-118">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="50509-119">Ad alanı için temel ağ seçeneklerini yapılandırır <xref:System.Net> .</span><span class="sxs-lookup"><span data-stu-id="50509-119">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50509-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="50509-120">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="50509-121">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="50509-121">Configuration Files</span></span>  

 <span data-ttu-id="50509-122">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="50509-122">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50509-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50509-123">See also</span></span>

- [<span data-ttu-id="50509-124">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="50509-124">Network Settings Schema</span></span>](index.md)
