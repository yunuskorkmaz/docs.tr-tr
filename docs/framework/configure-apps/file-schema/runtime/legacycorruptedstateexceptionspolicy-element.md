---
title: <legacyCorruptedStateExceptionsPolicy> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6191ee2169a85725f0367763874e60c0ceb1d7a4
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489436"
---
# <a name="legacycorruptedstateexceptionspolicy-element"></a><span data-ttu-id="b1b29-102">\<legacyCorruptedStateExceptionsPolicy > öğesi</span><span class="sxs-lookup"><span data-stu-id="b1b29-102">\<legacyCorruptedStateExceptionsPolicy> Element</span></span>
<span data-ttu-id="b1b29-103">Ortak dil çalışma zamanı erişim ihlalleri ve diğer bozuk durum özel durumları yakalamak yönetilen kod izin verip vermediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b1b29-103">Specifies whether the common language runtime allows managed code to catch access violations and other corrupted state exceptions.</span></span>  
  
 <span data-ttu-id="b1b29-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="b1b29-104">\<configuration></span></span>  
<span data-ttu-id="b1b29-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="b1b29-105">\<runtime></span></span>  
<span data-ttu-id="b1b29-106">\<legacyCorruptedStateExceptionsPolicy ></span><span class="sxs-lookup"><span data-stu-id="b1b29-106">\<legacyCorruptedStateExceptionsPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1b29-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b1b29-107">Syntax</span></span>  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1b29-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b1b29-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b1b29-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b1b29-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1b29-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b1b29-110">Attributes</span></span>  
  
|<span data-ttu-id="b1b29-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b1b29-111">Attribute</span></span>|<span data-ttu-id="b1b29-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1b29-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="b1b29-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b1b29-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="b1b29-114">Uygulama yakalar belirtir erişim ihlalleri gibi özel durum hataları durumu bozan.</span><span class="sxs-lookup"><span data-stu-id="b1b29-114">Specifies that the application will catch corrupting state exception failures such as access violations.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="b1b29-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b1b29-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="b1b29-116">Değer</span><span class="sxs-lookup"><span data-stu-id="b1b29-116">Value</span></span>|<span data-ttu-id="b1b29-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1b29-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="b1b29-118">Uygulama değil yakalar erişim ihlalleri gibi özel durum hataları durumu bozan.</span><span class="sxs-lookup"><span data-stu-id="b1b29-118">The application will not catch corrupting state exception failures such as access violations.</span></span> <span data-ttu-id="b1b29-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="b1b29-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="b1b29-120">Uygulama yakalar erişim ihlalleri gibi özel durum hataları durumu bozan.</span><span class="sxs-lookup"><span data-stu-id="b1b29-120">The application will catch corrupting state exception failures such as access violations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b1b29-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b1b29-121">Child Elements</span></span>  
 <span data-ttu-id="b1b29-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="b1b29-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b1b29-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b1b29-123">Parent Elements</span></span>  
  
|<span data-ttu-id="b1b29-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="b1b29-124">Element</span></span>|<span data-ttu-id="b1b29-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1b29-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b1b29-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="b1b29-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="b1b29-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="b1b29-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1b29-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b1b29-128">Remarks</span></span>  
 <span data-ttu-id="b1b29-129">.NET Framework sürüm 3.5 ve önceki sürümlerinde, ortak dil çalışma zamanı tarafından bozuk işlem durumları ortaya çıktı özel durumları yakalamak yönetilen kod izin.</span><span class="sxs-lookup"><span data-stu-id="b1b29-129">In the .NET Framework version 3.5 and earlier, the common language runtime allowed managed code to catch exceptions that were raised by corrupted process states.</span></span> <span data-ttu-id="b1b29-130">Erişim ihlali, bu özel durumun türünü örneğidir.</span><span class="sxs-lookup"><span data-stu-id="b1b29-130">An access violation is an example of this type of exception.</span></span>  
  
 <span data-ttu-id="b1b29-131">.NET Framework 4 ile başlayarak, yönetilen kod artık bu tür özel durumları yakalayan `catch` engeller.</span><span class="sxs-lookup"><span data-stu-id="b1b29-131">Starting with the .NET Framework 4, managed code no longer catches these types of exceptions in `catch` blocks.</span></span> <span data-ttu-id="b1b29-132">Ancak, bu değişikliği geçersiz kılar ve iki yolla bozuk durum özel durumların işlenmesiyle Koru:</span><span class="sxs-lookup"><span data-stu-id="b1b29-132">However, you can override this change and maintain the handling of corrupted state exceptions in two ways:</span></span>  
  
- <span data-ttu-id="b1b29-133">Ayarlama `<legacyCorruptedStateExceptionsPolicy>` öğenin `enabled` özniteliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="b1b29-133">Set the `<legacyCorruptedStateExceptionsPolicy>` element's `enabled` attribute to `true`.</span></span> <span data-ttu-id="b1b29-134">Bu yapılandırma ayarının uygulanan processwide olduğu ve tüm yöntemleri etkiler.</span><span class="sxs-lookup"><span data-stu-id="b1b29-134">This configuration setting is applied processwide and affects all methods.</span></span>  
  
 <span data-ttu-id="b1b29-135">-veya-</span><span class="sxs-lookup"><span data-stu-id="b1b29-135">-or-</span></span>  
  
- <span data-ttu-id="b1b29-136">Uygulama <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> özniteliğini özel durumları içeren yöntemine `catch` blok.</span><span class="sxs-lookup"><span data-stu-id="b1b29-136">Apply the <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> attribute to the method that contains the exceptions `catch` block.</span></span>  
  
 <span data-ttu-id="b1b29-137">Bu yapılandırma öğesi, yalnızca .NET Framework 4'teki kullanılabilir ve üzerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="b1b29-137">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1b29-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="b1b29-138">Example</span></span>  
 <span data-ttu-id="b1b29-139">Aşağıdaki örnek, uygulama .NET Framework 4 önceki davranış geri dönmek ve tüm bozulan durumu özel durum hatalarını yakalar, belirtmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b1b29-139">The following example shows how to specify that the application should revert to the behavior before the .NET Framework 4, and catch all corrupting state exception failures.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b1b29-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1b29-140">See also</span></span>

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>
- [<span data-ttu-id="b1b29-141">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="b1b29-141">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="b1b29-142">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="b1b29-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
