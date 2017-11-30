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
ms.openlocfilehash: d1258301af903ef5c36df854c7c6dd504d6eef15
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltwebproxyscriptgt-element-network-settings"></a><span data-ttu-id="230db-102">&lt;webProxyScript&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="230db-102">&lt;webProxyScript&gt; Element (Network Settings)</span></span>
<span data-ttu-id="230db-103">Web proxy bulmak için kullanılan komut dosyası özelliklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="230db-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  
  
 <span data-ttu-id="230db-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="230db-104">\<configuration></span></span>  
<span data-ttu-id="230db-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="230db-105">\<system.net></span></span>  
<span data-ttu-id="230db-106">\<Ayarlar ></span><span class="sxs-lookup"><span data-stu-id="230db-106">\<settings></span></span>  
<span data-ttu-id="230db-107">\<webProxyScript ></span><span class="sxs-lookup"><span data-stu-id="230db-107">\<webProxyScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="230db-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="230db-108">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="230db-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="230db-109">Attributes and Elements</span></span>  
 <span data-ttu-id="230db-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="230db-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="230db-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="230db-111">Attributes</span></span>  
  
|<span data-ttu-id="230db-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="230db-112">Attribute</span></span>|<span data-ttu-id="230db-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="230db-113">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="230db-114">Saat, dakika ve saniye olarak komut dosyasını karşıdan yüklemek için en uzun süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="230db-114">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="230db-115">Varsayılan değer bir dakikadır.</span><span class="sxs-lookup"><span data-stu-id="230db-115">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="230db-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="230db-116">Child Elements</span></span>  
 <span data-ttu-id="230db-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="230db-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="230db-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="230db-118">Parent Elements</span></span>  
  
|<span data-ttu-id="230db-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="230db-119">Element</span></span>|<span data-ttu-id="230db-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="230db-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="230db-121">Ayarlar</span><span class="sxs-lookup"><span data-stu-id="230db-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="230db-122">Temel ağ seçeneklerini yapılandırır <xref:System.Net> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="230db-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="230db-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="230db-123">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="230db-124">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="230db-124">Configuration Files</span></span>  
 <span data-ttu-id="230db-125">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="230db-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="230db-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="230db-126">See Also</span></span>  
 [<span data-ttu-id="230db-127">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="230db-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
