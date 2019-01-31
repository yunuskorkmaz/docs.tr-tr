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
ms.openlocfilehash: e823d6065ea23f3a47dad6853a1b9e1237a616c9
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257830"
---
# <a name="webproxyscript-element-network-settings"></a><span data-ttu-id="89985-102">\<webProxyScript > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="89985-102">\<webProxyScript> Element (Network Settings)</span></span>
<span data-ttu-id="89985-103">Web proxy'leri bulmak için kullanılan komut dosyası özelliklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="89985-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  
  
 <span data-ttu-id="89985-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="89985-104">\<configuration></span></span>  
<span data-ttu-id="89985-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="89985-105">\<system.net></span></span>  
<span data-ttu-id="89985-106">\<Ayarlar ></span><span class="sxs-lookup"><span data-stu-id="89985-106">\<settings></span></span>  
<span data-ttu-id="89985-107">\<webProxyScript ></span><span class="sxs-lookup"><span data-stu-id="89985-107">\<webProxyScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89985-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="89985-108">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89985-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="89985-109">Attributes and Elements</span></span>  
 <span data-ttu-id="89985-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="89985-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89985-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="89985-111">Attributes</span></span>  
  
|<span data-ttu-id="89985-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="89985-112">Attribute</span></span>|<span data-ttu-id="89985-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89985-113">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="89985-114">Saat, dakika ve saniye betiği indirmek için en uzun süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="89985-114">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="89985-115">Bir dakika varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="89985-115">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="89985-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="89985-116">Child Elements</span></span>  
 <span data-ttu-id="89985-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="89985-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="89985-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="89985-118">Parent Elements</span></span>  
  
|<span data-ttu-id="89985-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="89985-119">Element</span></span>|<span data-ttu-id="89985-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89985-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="89985-121">Ayarlar</span><span class="sxs-lookup"><span data-stu-id="89985-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="89985-122">Temel ağ seçeneklerini yapılandırır <xref:System.Net> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="89985-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89985-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="89985-123">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="89985-124">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="89985-124">Configuration Files</span></span>  
 <span data-ttu-id="89985-125">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="89985-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89985-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89985-126">See also</span></span>
- [<span data-ttu-id="89985-127">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="89985-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
