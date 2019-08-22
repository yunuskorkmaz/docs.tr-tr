---
title: <legacyCorruptedStateExceptionsPolicy> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2715548a40579375cebbdd5fb9003738a42ff714
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663662"
---
# <a name="legacycorruptedstateexceptionspolicy-element"></a><span data-ttu-id="dfd14-102">\<Legacyboztedstateexceptionspolicy > öğesi</span><span class="sxs-lookup"><span data-stu-id="dfd14-102">\<legacyCorruptedStateExceptionsPolicy> Element</span></span>
<span data-ttu-id="dfd14-103">Ortak dil çalışma zamanının yönetilen kodun erişim ihlallerini ve diğer bozuk durum özel durumlarını yakalayıp belirlemesine izin verip içermediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="dfd14-103">Specifies whether the common language runtime allows managed code to catch access violations and other corrupted state exceptions.</span></span>  
  
 <span data-ttu-id="dfd14-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="dfd14-104">\<configuration></span></span>  
<span data-ttu-id="dfd14-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="dfd14-105">\<runtime></span></span>  
<span data-ttu-id="dfd14-106">\<Legacybozulmuş Tedstateexceptionspolicy ></span><span class="sxs-lookup"><span data-stu-id="dfd14-106">\<legacyCorruptedStateExceptionsPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfd14-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dfd14-107">Syntax</span></span>  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dfd14-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="dfd14-108">Attributes and Elements</span></span>  
 <span data-ttu-id="dfd14-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dfd14-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dfd14-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="dfd14-110">Attributes</span></span>  
  
|<span data-ttu-id="dfd14-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="dfd14-111">Attribute</span></span>|<span data-ttu-id="dfd14-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dfd14-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="dfd14-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="dfd14-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="dfd14-114">Uygulamanın erişim ihlalleri gibi bozulmaları durum özel durum başarısızlıklarını yakalayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="dfd14-114">Specifies that the application will catch corrupting state exception failures such as access violations.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="dfd14-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="dfd14-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="dfd14-116">Değer</span><span class="sxs-lookup"><span data-stu-id="dfd14-116">Value</span></span>|<span data-ttu-id="dfd14-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dfd14-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="dfd14-118">Uygulama, erişim ihlalleri gibi bozulmayan durum özel durum başarısızlıklarını yakalayamaz.</span><span class="sxs-lookup"><span data-stu-id="dfd14-118">The application will not catch corrupting state exception failures such as access violations.</span></span> <span data-ttu-id="dfd14-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="dfd14-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="dfd14-120">Uygulama, erişim ihlalleri gibi bozulmaları durum özel durum başarısızlıklarını yakalar.</span><span class="sxs-lookup"><span data-stu-id="dfd14-120">The application will catch corrupting state exception failures such as access violations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dfd14-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="dfd14-121">Child Elements</span></span>  
 <span data-ttu-id="dfd14-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="dfd14-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dfd14-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="dfd14-123">Parent Elements</span></span>  
  
|<span data-ttu-id="dfd14-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="dfd14-124">Element</span></span>|<span data-ttu-id="dfd14-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dfd14-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="dfd14-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="dfd14-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="dfd14-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="dfd14-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dfd14-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dfd14-128">Remarks</span></span>  
 <span data-ttu-id="dfd14-129">.NET Framework sürüm 3,5 ve önceki sürümlerde, ortak dil çalışma zamanının bozuk işlem durumları tarafından oluşturulan özel durumları yakalayabileceği yönetilen koda izin verilir.</span><span class="sxs-lookup"><span data-stu-id="dfd14-129">In the .NET Framework version 3.5 and earlier, the common language runtime allowed managed code to catch exceptions that were raised by corrupted process states.</span></span> <span data-ttu-id="dfd14-130">Erişim ihlali, bu tür bir özel durum örneğidir.</span><span class="sxs-lookup"><span data-stu-id="dfd14-130">An access violation is an example of this type of exception.</span></span>  
  
 <span data-ttu-id="dfd14-131">.NET Framework 4 ' te başlayarak, yönetilen kod artık bloklardaki `catch` bu tür özel durumları yakalamayacaktır.</span><span class="sxs-lookup"><span data-stu-id="dfd14-131">Starting with the .NET Framework 4, managed code no longer catches these types of exceptions in `catch` blocks.</span></span> <span data-ttu-id="dfd14-132">Ancak, bu değişikliği geçersiz kılabilir ve bozulmuş durum istisnalarını iki şekilde işleme devam edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="dfd14-132">However, you can override this change and maintain the handling of corrupted state exceptions in two ways:</span></span>  
  
- <span data-ttu-id="dfd14-133">Öğenin özniteliğini olarak`true`ayarlayın. `enabled` `<legacyCorruptedStateExceptionsPolicy>`</span><span class="sxs-lookup"><span data-stu-id="dfd14-133">Set the `<legacyCorruptedStateExceptionsPolicy>` element's `enabled` attribute to `true`.</span></span> <span data-ttu-id="dfd14-134">Bu yapılandırma ayarı, processwide uygulanır ve tüm yöntemleri etkiler.</span><span class="sxs-lookup"><span data-stu-id="dfd14-134">This configuration setting is applied processwide and affects all methods.</span></span>  
  
 <span data-ttu-id="dfd14-135">-veya-</span><span class="sxs-lookup"><span data-stu-id="dfd14-135">-or-</span></span>  
  
- <span data-ttu-id="dfd14-136">Özel durum`catch` bloğunu içeren yönteme özniteliğiniuygulayın.<xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="dfd14-136">Apply the <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> attribute to the method that contains the exceptions `catch` block.</span></span>  
  
 <span data-ttu-id="dfd14-137">Bu yapılandırma öğesi yalnızca .NET Framework 4 ve üzeri sürümlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dfd14-137">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dfd14-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="dfd14-138">Example</span></span>  
 <span data-ttu-id="dfd14-139">Aşağıdaki örnek, uygulamanın .NET Framework 4 ' den önceki davranışa ne şekilde dönmesi gerektiğini belirtir ve tüm bozulmalı durum özel durum başarısızlıklarını yakalar.</span><span class="sxs-lookup"><span data-stu-id="dfd14-139">The following example shows how to specify that the application should revert to the behavior before the .NET Framework 4, and catch all corrupting state exception failures.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dfd14-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dfd14-140">See also</span></span>

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>
- [<span data-ttu-id="dfd14-141">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="dfd14-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="dfd14-142">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="dfd14-142">Configuration File Schema</span></span>](../index.md)
