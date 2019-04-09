---
title: <legacyCorruptedStateExceptionsPolicy> Öğe
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 777d496614435106b84b47b9aa3d35d964bc3e07
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115108"
---
# <a name="legacycorruptedstateexceptionspolicy-element"></a><span data-ttu-id="27c24-102">\<legacyCorruptedStateExceptionsPolicy > öğesi</span><span class="sxs-lookup"><span data-stu-id="27c24-102">\<legacyCorruptedStateExceptionsPolicy> Element</span></span>
<span data-ttu-id="27c24-103">Ortak dil çalışma zamanı erişim ihlalleri ve diğer bozuk durum özel durumları yakalamak yönetilen kod izin verip vermediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="27c24-103">Specifies whether the common language runtime allows managed code to catch access violations and other corrupted state exceptions.</span></span>  
  
 <span data-ttu-id="27c24-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="27c24-104">\<configuration></span></span>  
<span data-ttu-id="27c24-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="27c24-105">\<runtime></span></span>  
<span data-ttu-id="27c24-106">\<legacyCorruptedStateExceptionsPolicy ></span><span class="sxs-lookup"><span data-stu-id="27c24-106">\<legacyCorruptedStateExceptionsPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27c24-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="27c24-107">Syntax</span></span>  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="27c24-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="27c24-108">Attributes and Elements</span></span>  
 <span data-ttu-id="27c24-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="27c24-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="27c24-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="27c24-110">Attributes</span></span>  
  
|<span data-ttu-id="27c24-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="27c24-111">Attribute</span></span>|<span data-ttu-id="27c24-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27c24-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="27c24-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="27c24-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="27c24-114">Uygulama yakalar belirtir erişim ihlalleri gibi özel durum hataları durumu bozan.</span><span class="sxs-lookup"><span data-stu-id="27c24-114">Specifies that the application will catch corrupting state exception failures such as access violations.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="27c24-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="27c24-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="27c24-116">Değer</span><span class="sxs-lookup"><span data-stu-id="27c24-116">Value</span></span>|<span data-ttu-id="27c24-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27c24-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="27c24-118">Uygulama değil yakalar erişim ihlalleri gibi özel durum hataları durumu bozan.</span><span class="sxs-lookup"><span data-stu-id="27c24-118">The application will not catch corrupting state exception failures such as access violations.</span></span> <span data-ttu-id="27c24-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="27c24-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="27c24-120">Uygulama yakalar erişim ihlalleri gibi özel durum hataları durumu bozan.</span><span class="sxs-lookup"><span data-stu-id="27c24-120">The application will catch corrupting state exception failures such as access violations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="27c24-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="27c24-121">Child Elements</span></span>  
 <span data-ttu-id="27c24-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="27c24-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="27c24-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="27c24-123">Parent Elements</span></span>  
  
|<span data-ttu-id="27c24-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="27c24-124">Element</span></span>|<span data-ttu-id="27c24-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27c24-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="27c24-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="27c24-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="27c24-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="27c24-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27c24-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="27c24-128">Remarks</span></span>  
 <span data-ttu-id="27c24-129">.NET Framework sürüm 3.5 ve önceki sürümlerinde, ortak dil çalışma zamanı tarafından bozuk işlem durumları ortaya çıktı özel durumları yakalamak yönetilen kod izin.</span><span class="sxs-lookup"><span data-stu-id="27c24-129">In the .NET Framework version 3.5 and earlier, the common language runtime allowed managed code to catch exceptions that were raised by corrupted process states.</span></span> <span data-ttu-id="27c24-130">Erişim ihlali, bu özel durumun türünü örneğidir.</span><span class="sxs-lookup"><span data-stu-id="27c24-130">An access violation is an example of this type of exception.</span></span>  
  
 <span data-ttu-id="27c24-131">İle başlayarak [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], yönetilen kod artık bu tür özel durumları yakalayan `catch` engeller.</span><span class="sxs-lookup"><span data-stu-id="27c24-131">Starting with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], managed code no longer catches these types of exceptions in `catch` blocks.</span></span> <span data-ttu-id="27c24-132">Ancak, bu değişikliği geçersiz kılar ve iki yolla bozuk durum özel durumların işlenmesiyle Koru:</span><span class="sxs-lookup"><span data-stu-id="27c24-132">However, you can override this change and maintain the handling of corrupted state exceptions in two ways:</span></span>  
  
-   <span data-ttu-id="27c24-133">Ayarlama `<legacyCorruptedStateExceptionsPolicy>` öğenin `enabled` özniteliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="27c24-133">Set the `<legacyCorruptedStateExceptionsPolicy>` element's `enabled` attribute to `true`.</span></span> <span data-ttu-id="27c24-134">Bu yapılandırma ayarının uygulanan processwide olduğu ve tüm yöntemleri etkiler.</span><span class="sxs-lookup"><span data-stu-id="27c24-134">This configuration setting is applied processwide and affects all methods.</span></span>  
  
 <span data-ttu-id="27c24-135">-veya-</span><span class="sxs-lookup"><span data-stu-id="27c24-135">-or-</span></span>  
  
-   <span data-ttu-id="27c24-136">Uygulama <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> özniteliğini özel durumları içeren yöntemine `catch` blok.</span><span class="sxs-lookup"><span data-stu-id="27c24-136">Apply the <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> attribute to the method that contains the exceptions `catch` block.</span></span>  
  
 <span data-ttu-id="27c24-137">Bu yapılandırma öğesi yalnızca [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] ve daha sonra.</span><span class="sxs-lookup"><span data-stu-id="27c24-137">This configuration element is available only in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27c24-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="27c24-138">Example</span></span>  
 <span data-ttu-id="27c24-139">Aşağıdaki örnek, uygulama davranışını önce geri belirtmek gösterilmektedir [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]ve tüm bozulan durumu özel durum hatalarını yakalar.</span><span class="sxs-lookup"><span data-stu-id="27c24-139">The following example shows how to specify that the application should revert to the behavior before the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], and catch all corrupting state exception failures.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="27c24-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27c24-140">See also</span></span>

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>
- [<span data-ttu-id="27c24-141">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="27c24-141">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="27c24-142">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="27c24-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
