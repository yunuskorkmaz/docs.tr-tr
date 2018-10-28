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
ms.openlocfilehash: 683c4c5e3f3f62d947ce244c66cc590eabe64f17
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50195794"
---
# <a name="ltwebproxyscriptgt-element-network-settings"></a><span data-ttu-id="59e3d-102">&lt;webProxyScript&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="59e3d-102">&lt;webProxyScript&gt; Element (Network Settings)</span></span>
<span data-ttu-id="59e3d-103">Web proxy'leri bulmak için kullanılan komut dosyası özelliklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="59e3d-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  
  
 <span data-ttu-id="59e3d-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="59e3d-104">\<configuration></span></span>  
<span data-ttu-id="59e3d-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="59e3d-105">\<system.net></span></span>  
<span data-ttu-id="59e3d-106">\<Ayarlar ></span><span class="sxs-lookup"><span data-stu-id="59e3d-106">\<settings></span></span>  
<span data-ttu-id="59e3d-107">\<webProxyScript ></span><span class="sxs-lookup"><span data-stu-id="59e3d-107">\<webProxyScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59e3d-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="59e3d-108">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59e3d-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="59e3d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="59e3d-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="59e3d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59e3d-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="59e3d-111">Attributes</span></span>  
  
|<span data-ttu-id="59e3d-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="59e3d-112">Attribute</span></span>|<span data-ttu-id="59e3d-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="59e3d-113">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="59e3d-114">Saat, dakika ve saniye betiği indirmek için en uzun süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="59e3d-114">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="59e3d-115">Bir dakika varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="59e3d-115">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="59e3d-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="59e3d-116">Child Elements</span></span>  
 <span data-ttu-id="59e3d-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="59e3d-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="59e3d-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="59e3d-118">Parent Elements</span></span>  
  
|<span data-ttu-id="59e3d-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="59e3d-119">Element</span></span>|<span data-ttu-id="59e3d-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="59e3d-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59e3d-121">Ayarlar</span><span class="sxs-lookup"><span data-stu-id="59e3d-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="59e3d-122">Temel ağ seçeneklerini yapılandırır <xref:System.Net> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="59e3d-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59e3d-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="59e3d-123">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="59e3d-124">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="59e3d-124">Configuration Files</span></span>  
 <span data-ttu-id="59e3d-125">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="59e3d-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59e3d-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="59e3d-126">See Also</span></span>  
- [<span data-ttu-id="59e3d-127">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="59e3d-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
