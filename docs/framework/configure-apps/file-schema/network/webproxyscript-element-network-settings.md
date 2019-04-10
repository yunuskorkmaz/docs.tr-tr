---
title: <webProxyScript> Öğesi (ağ ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webProxyScript
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/webProxyScript
helpviewer_keywords:
- <webProxyScript> element
- webProxyScript element
ms.assetid: a13c26db-6218-4af3-9696-38f24b23bfac
ms.openlocfilehash: e73ba86cc17fa51cbf4030f2304ab9141fcc0f26
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218673"
---
# <a name="webproxyscript-element-network-settings"></a><span data-ttu-id="3bf6c-102">\<webProxyScript > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="3bf6c-102">\<webProxyScript> Element (Network Settings)</span></span>
<span data-ttu-id="3bf6c-103">Web proxy'leri bulmak için kullanılan komut dosyası özelliklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="3bf6c-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  
  
 <span data-ttu-id="3bf6c-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="3bf6c-104">\<configuration></span></span>  
<span data-ttu-id="3bf6c-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="3bf6c-105">\<system.net></span></span>  
<span data-ttu-id="3bf6c-106">\<Ayarlar ></span><span class="sxs-lookup"><span data-stu-id="3bf6c-106">\<settings></span></span>  
<span data-ttu-id="3bf6c-107">\<webProxyScript ></span><span class="sxs-lookup"><span data-stu-id="3bf6c-107">\<webProxyScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bf6c-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3bf6c-108">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3bf6c-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3bf6c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3bf6c-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3bf6c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3bf6c-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3bf6c-111">Attributes</span></span>  
  
|<span data-ttu-id="3bf6c-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3bf6c-112">Attribute</span></span>|<span data-ttu-id="3bf6c-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3bf6c-113">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="3bf6c-114">Saat, dakika ve saniye betiği indirmek için en uzun süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="3bf6c-114">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="3bf6c-115">Bir dakika varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="3bf6c-115">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3bf6c-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3bf6c-116">Child Elements</span></span>  
 <span data-ttu-id="3bf6c-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="3bf6c-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3bf6c-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3bf6c-118">Parent Elements</span></span>  
  
|<span data-ttu-id="3bf6c-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="3bf6c-119">Element</span></span>|<span data-ttu-id="3bf6c-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3bf6c-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3bf6c-121">ayarlar</span><span class="sxs-lookup"><span data-stu-id="3bf6c-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="3bf6c-122">Temel ağ seçeneklerini yapılandırır <xref:System.Net> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="3bf6c-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3bf6c-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3bf6c-123">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="3bf6c-124">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="3bf6c-124">Configuration Files</span></span>  
 <span data-ttu-id="3bf6c-125">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3bf6c-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bf6c-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3bf6c-126">See also</span></span>

- [<span data-ttu-id="3bf6c-127">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="3bf6c-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
