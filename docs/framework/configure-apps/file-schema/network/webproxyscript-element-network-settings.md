---
title: '&lt;webProxyScript&gt; öğesi (ağ ayarları)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webProxyScript
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/webProxyScript
helpviewer_keywords:
- <webProxyScript> element
- webProxyScript element
ms.assetid: a13c26db-6218-4af3-9696-38f24b23bfac
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 1e1450d2df424b32aacc5c113b5936001f65915a
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47085659"
---
# <a name="ltwebproxyscriptgt-element-network-settings"></a><span data-ttu-id="a8fff-102">&lt;webProxyScript&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="a8fff-102">&lt;webProxyScript&gt; Element (Network Settings)</span></span>
<span data-ttu-id="a8fff-103">Web proxy'leri bulmak için kullanılan komut dosyası özelliklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="a8fff-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  
  
 <span data-ttu-id="a8fff-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="a8fff-104">\<configuration></span></span>  
<span data-ttu-id="a8fff-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="a8fff-105">\<system.net></span></span>  
<span data-ttu-id="a8fff-106">\<Ayarlar ></span><span class="sxs-lookup"><span data-stu-id="a8fff-106">\<settings></span></span>  
<span data-ttu-id="a8fff-107">\<webProxyScript ></span><span class="sxs-lookup"><span data-stu-id="a8fff-107">\<webProxyScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8fff-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a8fff-108">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a8fff-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a8fff-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a8fff-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a8fff-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a8fff-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a8fff-111">Attributes</span></span>  
  
|<span data-ttu-id="a8fff-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a8fff-112">Attribute</span></span>|<span data-ttu-id="a8fff-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a8fff-113">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="a8fff-114">Saat, dakika ve saniye betiği indirmek için en uzun süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="a8fff-114">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="a8fff-115">Bir dakika varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="a8fff-115">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a8fff-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a8fff-116">Child Elements</span></span>  
 <span data-ttu-id="a8fff-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="a8fff-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a8fff-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a8fff-118">Parent Elements</span></span>  
  
|<span data-ttu-id="a8fff-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="a8fff-119">Element</span></span>|<span data-ttu-id="a8fff-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a8fff-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a8fff-121">Ayarlar</span><span class="sxs-lookup"><span data-stu-id="a8fff-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="a8fff-122">Temel ağ seçeneklerini yapılandırır <xref:System.Net> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="a8fff-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8fff-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a8fff-123">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="a8fff-124">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="a8fff-124">Configuration Files</span></span>  
 <span data-ttu-id="a8fff-125">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a8fff-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8fff-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a8fff-126">See Also</span></span>  
 [<span data-ttu-id="a8fff-127">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="a8fff-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
