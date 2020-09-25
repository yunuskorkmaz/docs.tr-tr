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
ms.openlocfilehash: e36b470b1ec348085b13a58630b0ac6833e43946
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178313"
---
# <a name="webproxyscript-element-network-settings"></a><span data-ttu-id="7759c-102">\<webProxyScript> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="7759c-102">\<webProxyScript> Element (Network Settings)</span></span>

<span data-ttu-id="7759c-103">Web proxy 'lerini keşfetme için kullanılan betiğin özelliklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="7759c-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webProxyScript>**

## <a name="syntax"></a><span data-ttu-id="7759c-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="7759c-104">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7759c-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7759c-105">Attributes and Elements</span></span>  

 <span data-ttu-id="7759c-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7759c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7759c-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7759c-107">Attributes</span></span>  
  
|<span data-ttu-id="7759c-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7759c-108">Attribute</span></span>|<span data-ttu-id="7759c-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7759c-109">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="7759c-110">Betiği saat, dakika ve saniye cinsinden indirmek için en uzun süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="7759c-110">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="7759c-111">Varsayılan değer bir dakikadır.</span><span class="sxs-lookup"><span data-stu-id="7759c-111">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7759c-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7759c-112">Child Elements</span></span>  

 <span data-ttu-id="7759c-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="7759c-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7759c-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7759c-114">Parent Elements</span></span>  
  
|<span data-ttu-id="7759c-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="7759c-115">Element</span></span>|<span data-ttu-id="7759c-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7759c-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7759c-117">ayarlar</span><span class="sxs-lookup"><span data-stu-id="7759c-117">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="7759c-118">Ad alanı için temel ağ seçeneklerini yapılandırır <xref:System.Net> .</span><span class="sxs-lookup"><span data-stu-id="7759c-118">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7759c-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7759c-119">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="7759c-120">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="7759c-120">Configuration Files</span></span>  

 <span data-ttu-id="7759c-121">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7759c-121">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7759c-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7759c-122">See also</span></span>

- [<span data-ttu-id="7759c-123">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="7759c-123">Network Settings Schema</span></span>](index.md)
