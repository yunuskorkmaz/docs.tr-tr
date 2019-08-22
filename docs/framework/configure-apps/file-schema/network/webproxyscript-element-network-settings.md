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
ms.openlocfilehash: 8a77c2567401fd80e355bb7fcee17b6684653ebe
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659039"
---
# <a name="webproxyscript-element-network-settings"></a><span data-ttu-id="31867-102">\<webProxyScript > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="31867-102">\<webProxyScript> Element (Network Settings)</span></span>
<span data-ttu-id="31867-103">Web proxy 'lerini keşfetme için kullanılan betiğin özelliklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="31867-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  
  
 <span data-ttu-id="31867-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="31867-104">\<configuration></span></span>  
<span data-ttu-id="31867-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="31867-105">\<system.net></span></span>  
<span data-ttu-id="31867-106">\<Ayarlar ></span><span class="sxs-lookup"><span data-stu-id="31867-106">\<settings></span></span>  
<span data-ttu-id="31867-107">\<webProxyScript ></span><span class="sxs-lookup"><span data-stu-id="31867-107">\<webProxyScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31867-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="31867-108">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="31867-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="31867-109">Attributes and Elements</span></span>  
 <span data-ttu-id="31867-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="31867-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="31867-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="31867-111">Attributes</span></span>  
  
|<span data-ttu-id="31867-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="31867-112">Attribute</span></span>|<span data-ttu-id="31867-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="31867-113">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="31867-114">Betiği saat, dakika ve saniye cinsinden indirmek için en uzun süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="31867-114">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="31867-115">Varsayılan değer bir dakikadır.</span><span class="sxs-lookup"><span data-stu-id="31867-115">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="31867-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="31867-116">Child Elements</span></span>  
 <span data-ttu-id="31867-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="31867-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="31867-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="31867-118">Parent Elements</span></span>  
  
|<span data-ttu-id="31867-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="31867-119">Element</span></span>|<span data-ttu-id="31867-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="31867-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="31867-121">Ayarlar</span><span class="sxs-lookup"><span data-stu-id="31867-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="31867-122"><xref:System.Net> Ad alanı için temel ağ seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="31867-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31867-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="31867-123">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="31867-124">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="31867-124">Configuration Files</span></span>  
 <span data-ttu-id="31867-125">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="31867-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31867-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31867-126">See also</span></span>

- [<span data-ttu-id="31867-127">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="31867-127">Network Settings Schema</span></span>](index.md)
