---
description: 'Daha fazla bilgi edinin: <legacyCorruptedStateExceptionsPolicy> öğesi'
title: <legacyCorruptedStateExceptionsPolicy> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
ms.openlocfilehash: 34082c0779b09400a875894359cf7cf501173508
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786960"
---
# <a name="legacycorruptedstateexceptionspolicy-element"></a><span data-ttu-id="e6f81-103">\<legacyCorruptedStateExceptionsPolicy> Öğesi</span><span class="sxs-lookup"><span data-stu-id="e6f81-103">\<legacyCorruptedStateExceptionsPolicy> Element</span></span>

<span data-ttu-id="e6f81-104">Ortak dil çalışma zamanının yönetilen kodun erişim ihlallerini ve diğer bozuk durum özel durumlarını yakalayıp belirlemesine izin verip içermediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6f81-104">Specifies whether the common language runtime allows managed code to catch access violations and other corrupted state exceptions.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<legacyCorruptedStateExceptionsPolicy>**  
  
## <a name="syntax"></a><span data-ttu-id="e6f81-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e6f81-105">Syntax</span></span>  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6f81-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e6f81-106">Attributes and Elements</span></span>  

 <span data-ttu-id="e6f81-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e6f81-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6f81-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e6f81-108">Attributes</span></span>  
  
|<span data-ttu-id="e6f81-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e6f81-109">Attribute</span></span>|<span data-ttu-id="e6f81-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6f81-110">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="e6f81-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e6f81-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="e6f81-112">Uygulamanın erişim ihlalleri gibi bozulmaları durum özel durum başarısızlıklarını yakalayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="e6f81-112">Specifies that the application will catch corrupting state exception failures such as access violations.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="e6f81-113">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e6f81-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="e6f81-114">Değer</span><span class="sxs-lookup"><span data-stu-id="e6f81-114">Value</span></span>|<span data-ttu-id="e6f81-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6f81-115">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="e6f81-116">Uygulama, erişim ihlalleri gibi bozulmayan durum özel durum başarısızlıklarını yakalayamaz.</span><span class="sxs-lookup"><span data-stu-id="e6f81-116">The application will not catch corrupting state exception failures such as access violations.</span></span> <span data-ttu-id="e6f81-117">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="e6f81-117">This is the default.</span></span>|  
|`true`|<span data-ttu-id="e6f81-118">Uygulama, erişim ihlalleri gibi bozulmaları durum özel durum başarısızlıklarını yakalar.</span><span class="sxs-lookup"><span data-stu-id="e6f81-118">The application will catch corrupting state exception failures such as access violations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6f81-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e6f81-119">Child Elements</span></span>  

 <span data-ttu-id="e6f81-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="e6f81-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e6f81-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e6f81-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e6f81-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="e6f81-122">Element</span></span>|<span data-ttu-id="e6f81-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6f81-123">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e6f81-124">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="e6f81-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e6f81-125">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="e6f81-125">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6f81-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e6f81-126">Remarks</span></span>  

 <span data-ttu-id="e6f81-127">.NET Framework sürüm 3,5 ve önceki sürümlerde, ortak dil çalışma zamanının bozuk işlem durumları tarafından oluşturulan özel durumları yakalayabileceği yönetilen koda izin verilir.</span><span class="sxs-lookup"><span data-stu-id="e6f81-127">In the .NET Framework version 3.5 and earlier, the common language runtime allowed managed code to catch exceptions that were raised by corrupted process states.</span></span> <span data-ttu-id="e6f81-128">Erişim ihlali, bu tür bir özel durum örneğidir.</span><span class="sxs-lookup"><span data-stu-id="e6f81-128">An access violation is an example of this type of exception.</span></span>  
  
 <span data-ttu-id="e6f81-129">.NET Framework 4 ' te başlayarak, yönetilen kod artık bloklardaki bu tür özel durumları yakalamayacaktır `catch` .</span><span class="sxs-lookup"><span data-stu-id="e6f81-129">Starting with the .NET Framework 4, managed code no longer catches these types of exceptions in `catch` blocks.</span></span> <span data-ttu-id="e6f81-130">Ancak, bu değişikliği geçersiz kılabilir ve bozulmuş durum istisnalarını iki şekilde işleme devam edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e6f81-130">However, you can override this change and maintain the handling of corrupted state exceptions in two ways:</span></span>  
  
- <span data-ttu-id="e6f81-131">`<legacyCorruptedStateExceptionsPolicy>`Öğenin `enabled` özniteliğini olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="e6f81-131">Set the `<legacyCorruptedStateExceptionsPolicy>` element's `enabled` attribute to `true`.</span></span> <span data-ttu-id="e6f81-132">Bu yapılandırma ayarı, processwide uygulanır ve tüm yöntemleri etkiler.</span><span class="sxs-lookup"><span data-stu-id="e6f81-132">This configuration setting is applied processwide and affects all methods.</span></span>  
  
 <span data-ttu-id="e6f81-133">-veya-</span><span class="sxs-lookup"><span data-stu-id="e6f81-133">-or-</span></span>  
  
- <span data-ttu-id="e6f81-134"><xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType>Özel durum bloğunu içeren yönteme özniteliğini uygulayın `catch` .</span><span class="sxs-lookup"><span data-stu-id="e6f81-134">Apply the <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> attribute to the method that contains the exceptions `catch` block.</span></span>  
  
 <span data-ttu-id="e6f81-135">Bu yapılandırma öğesi yalnızca .NET Framework 4 ve üzeri sürümlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e6f81-135">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6f81-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="e6f81-136">Example</span></span>  

 <span data-ttu-id="e6f81-137">Aşağıdaki örnek, uygulamanın .NET Framework 4 ' den önceki davranışa ne şekilde dönmesi gerektiğini belirtir ve tüm bozulmalı durum özel durum başarısızlıklarını yakalar.</span><span class="sxs-lookup"><span data-stu-id="e6f81-137">The following example shows how to specify that the application should revert to the behavior before the .NET Framework 4, and catch all corrupting state exception failures.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e6f81-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6f81-138">See also</span></span>

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>
- [<span data-ttu-id="e6f81-139">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="e6f81-139">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e6f81-140">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="e6f81-140">Configuration File Schema</span></span>](../index.md)
