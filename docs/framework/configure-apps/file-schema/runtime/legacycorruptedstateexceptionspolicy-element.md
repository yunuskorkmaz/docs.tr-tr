---
title: '&lt;legacyCorruptedStateExceptionsPolicy&gt; öğesi'
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bdf2e69b307d55f778a5cb54f8cc77bc3c69a185
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613498"
---
# <a name="ltlegacycorruptedstateexceptionspolicygt-element"></a><span data-ttu-id="f9fea-102">&lt;legacyCorruptedStateExceptionsPolicy&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="f9fea-102">&lt;legacyCorruptedStateExceptionsPolicy&gt; Element</span></span>
<span data-ttu-id="f9fea-103">Ortak dil çalışma zamanı erişim ihlalleri ve diğer bozuk durum özel durumları yakalamak yönetilen kod izin verip vermediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f9fea-103">Specifies whether the common language runtime allows managed code to catch access violations and other corrupted state exceptions.</span></span>  
  
 <span data-ttu-id="f9fea-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="f9fea-104">\<configuration></span></span>  
<span data-ttu-id="f9fea-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="f9fea-105">\<runtime></span></span>  
<span data-ttu-id="f9fea-106">\<legacyCorruptedStateExceptionsPolicy ></span><span class="sxs-lookup"><span data-stu-id="f9fea-106">\<legacyCorruptedStateExceptionsPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9fea-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f9fea-107">Syntax</span></span>  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f9fea-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f9fea-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f9fea-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f9fea-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f9fea-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f9fea-110">Attributes</span></span>  
  
|<span data-ttu-id="f9fea-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f9fea-111">Attribute</span></span>|<span data-ttu-id="f9fea-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9fea-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="f9fea-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="f9fea-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="f9fea-114">Uygulama yakalar belirtir erişim ihlalleri gibi özel durum hataları durumu bozan.</span><span class="sxs-lookup"><span data-stu-id="f9fea-114">Specifies that the application will catch corrupting state exception failures such as access violations.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="f9fea-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f9fea-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="f9fea-116">Değer</span><span class="sxs-lookup"><span data-stu-id="f9fea-116">Value</span></span>|<span data-ttu-id="f9fea-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9fea-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="f9fea-118">Uygulama değil yakalar erişim ihlalleri gibi özel durum hataları durumu bozan.</span><span class="sxs-lookup"><span data-stu-id="f9fea-118">The application will not catch corrupting state exception failures such as access violations.</span></span> <span data-ttu-id="f9fea-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="f9fea-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="f9fea-120">Uygulama yakalar erişim ihlalleri gibi özel durum hataları durumu bozan.</span><span class="sxs-lookup"><span data-stu-id="f9fea-120">The application will catch corrupting state exception failures such as access violations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f9fea-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f9fea-121">Child Elements</span></span>  
 <span data-ttu-id="f9fea-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="f9fea-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f9fea-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f9fea-123">Parent Elements</span></span>  
  
|<span data-ttu-id="f9fea-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="f9fea-124">Element</span></span>|<span data-ttu-id="f9fea-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9fea-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f9fea-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="f9fea-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="f9fea-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="f9fea-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9fea-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f9fea-128">Remarks</span></span>  
 <span data-ttu-id="f9fea-129">.NET Framework sürüm 3.5 ve önceki sürümlerinde, ortak dil çalışma zamanı tarafından bozuk işlem durumları ortaya çıktı özel durumları yakalamak yönetilen kod izin.</span><span class="sxs-lookup"><span data-stu-id="f9fea-129">In the .NET Framework version 3.5 and earlier, the common language runtime allowed managed code to catch exceptions that were raised by corrupted process states.</span></span> <span data-ttu-id="f9fea-130">Erişim ihlali, bu özel durumun türünü örneğidir.</span><span class="sxs-lookup"><span data-stu-id="f9fea-130">An access violation is an example of this type of exception.</span></span>  
  
 <span data-ttu-id="f9fea-131">İle başlayarak [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], yönetilen kod artık bu tür özel durumları yakalayan `catch` engeller.</span><span class="sxs-lookup"><span data-stu-id="f9fea-131">Starting with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], managed code no longer catches these types of exceptions in `catch` blocks.</span></span> <span data-ttu-id="f9fea-132">Ancak, bu değişikliği geçersiz kılar ve iki yolla bozuk durum özel durumların işlenmesiyle Koru:</span><span class="sxs-lookup"><span data-stu-id="f9fea-132">However, you can override this change and maintain the handling of corrupted state exceptions in two ways:</span></span>  
  
-   <span data-ttu-id="f9fea-133">Ayarlama `<legacyCorruptedStateExceptionsPolicy>` öğenin `enabled` özniteliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="f9fea-133">Set the `<legacyCorruptedStateExceptionsPolicy>` element's `enabled` attribute to `true`.</span></span> <span data-ttu-id="f9fea-134">Bu yapılandırma ayarının uygulanan processwide olduğu ve tüm yöntemleri etkiler.</span><span class="sxs-lookup"><span data-stu-id="f9fea-134">This configuration setting is applied processwide and affects all methods.</span></span>  
  
 <span data-ttu-id="f9fea-135">-veya-</span><span class="sxs-lookup"><span data-stu-id="f9fea-135">-or-</span></span>  
  
-   <span data-ttu-id="f9fea-136">Uygulama <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> özniteliğini özel durumları içeren yöntemine `catch` blok.</span><span class="sxs-lookup"><span data-stu-id="f9fea-136">Apply the <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> attribute to the method that contains the exceptions `catch` block.</span></span>  
  
 <span data-ttu-id="f9fea-137">Bu yapılandırma öğesi yalnızca [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] ve daha sonra.</span><span class="sxs-lookup"><span data-stu-id="f9fea-137">This configuration element is available only in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9fea-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="f9fea-138">Example</span></span>  
 <span data-ttu-id="f9fea-139">Aşağıdaki örnek, uygulama davranışını önce geri belirtmek gösterilmektedir [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]ve tüm bozulan durumu özel durum hatalarını yakalar.</span><span class="sxs-lookup"><span data-stu-id="f9fea-139">The following example shows how to specify that the application should revert to the behavior before the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], and catch all corrupting state exception failures.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f9fea-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f9fea-140">See Also</span></span>  
- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>  
- [<span data-ttu-id="f9fea-141">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="f9fea-141">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [<span data-ttu-id="f9fea-142">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="f9fea-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
