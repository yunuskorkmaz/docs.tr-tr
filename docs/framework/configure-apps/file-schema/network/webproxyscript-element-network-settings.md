---
title: "&lt;webProxyScript&gt; öğesi (ağ ayarları)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webProxyScript
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/webProxyScript
helpviewer_keywords:
- <webProxyScript> element
- webProxyScript element
ms.assetid: a13c26db-6218-4af3-9696-38f24b23bfac
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 4c7d6154d354e806a04ccc9da062db64c534039b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltwebproxyscriptgt-element-network-settings"></a><span data-ttu-id="f4005-102">&lt;webProxyScript&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="f4005-102">&lt;webProxyScript&gt; Element (Network Settings)</span></span>
<span data-ttu-id="f4005-103">Web proxy bulmak için kullanılan komut dosyası özelliklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="f4005-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  
  
 <span data-ttu-id="f4005-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="f4005-104">\<configuration></span></span>  
<span data-ttu-id="f4005-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="f4005-105">\<system.net></span></span>  
<span data-ttu-id="f4005-106">\<Ayarlar ></span><span class="sxs-lookup"><span data-stu-id="f4005-106">\<settings></span></span>  
<span data-ttu-id="f4005-107">\<webProxyScript ></span><span class="sxs-lookup"><span data-stu-id="f4005-107">\<webProxyScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4005-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f4005-108">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f4005-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f4005-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f4005-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f4005-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f4005-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f4005-111">Attributes</span></span>  
  
|<span data-ttu-id="f4005-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f4005-112">Attribute</span></span>|<span data-ttu-id="f4005-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f4005-113">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="f4005-114">Saat, dakika ve saniye olarak komut dosyasını karşıdan yüklemek için en uzun süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="f4005-114">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="f4005-115">Varsayılan değer bir dakikadır.</span><span class="sxs-lookup"><span data-stu-id="f4005-115">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f4005-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f4005-116">Child Elements</span></span>  
 <span data-ttu-id="f4005-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="f4005-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f4005-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f4005-118">Parent Elements</span></span>  
  
|<span data-ttu-id="f4005-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="f4005-119">Element</span></span>|<span data-ttu-id="f4005-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f4005-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f4005-121">Ayarlar</span><span class="sxs-lookup"><span data-stu-id="f4005-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="f4005-122">Temel ağ seçeneklerini yapılandırır <xref:System.Net> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="f4005-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4005-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f4005-123">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="f4005-124">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="f4005-124">Configuration Files</span></span>  
 <span data-ttu-id="f4005-125">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f4005-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4005-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f4005-126">See Also</span></span>  
 [<span data-ttu-id="f4005-127">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="f4005-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
