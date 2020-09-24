---
title: <legacyCorruptedStateExceptionsPolicy> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
ms.openlocfilehash: f36e27a1b85cff2ba8c7e838bace37890a5aa760
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151213"
---
# <a name="legacycorruptedstateexceptionspolicy-element"></a><span data-ttu-id="6498f-102">\<legacyCorruptedStateExceptionsPolicy> Öğesi</span><span class="sxs-lookup"><span data-stu-id="6498f-102">\<legacyCorruptedStateExceptionsPolicy> Element</span></span>

<span data-ttu-id="6498f-103">Ortak dil çalışma zamanının yönetilen kodun erişim ihlallerini ve diğer bozuk durum özel durumlarını yakalayıp belirlemesine izin verip içermediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6498f-103">Specifies whether the common language runtime allows managed code to catch access violations and other corrupted state exceptions.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<legacyCorruptedStateExceptionsPolicy>**  
  
## <a name="syntax"></a><span data-ttu-id="6498f-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="6498f-104">Syntax</span></span>  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6498f-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6498f-105">Attributes and Elements</span></span>  

 <span data-ttu-id="6498f-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6498f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6498f-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6498f-107">Attributes</span></span>  
  
|<span data-ttu-id="6498f-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6498f-108">Attribute</span></span>|<span data-ttu-id="6498f-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6498f-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="6498f-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6498f-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="6498f-111">Uygulamanın erişim ihlalleri gibi bozulmaları durum özel durum başarısızlıklarını yakalayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="6498f-111">Specifies that the application will catch corrupting state exception failures such as access violations.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="6498f-112">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6498f-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="6498f-113">Değer</span><span class="sxs-lookup"><span data-stu-id="6498f-113">Value</span></span>|<span data-ttu-id="6498f-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6498f-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="6498f-115">Uygulama, erişim ihlalleri gibi bozulmayan durum özel durum başarısızlıklarını yakalayamaz.</span><span class="sxs-lookup"><span data-stu-id="6498f-115">The application will not catch corrupting state exception failures such as access violations.</span></span> <span data-ttu-id="6498f-116">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="6498f-116">This is the default.</span></span>|  
|`true`|<span data-ttu-id="6498f-117">Uygulama, erişim ihlalleri gibi bozulmaları durum özel durum başarısızlıklarını yakalar.</span><span class="sxs-lookup"><span data-stu-id="6498f-117">The application will catch corrupting state exception failures such as access violations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6498f-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6498f-118">Child Elements</span></span>  

 <span data-ttu-id="6498f-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="6498f-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6498f-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6498f-120">Parent Elements</span></span>  
  
|<span data-ttu-id="6498f-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="6498f-121">Element</span></span>|<span data-ttu-id="6498f-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6498f-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6498f-123">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="6498f-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="6498f-124">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="6498f-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6498f-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6498f-125">Remarks</span></span>  

 <span data-ttu-id="6498f-126">.NET Framework sürüm 3,5 ve önceki sürümlerde, ortak dil çalışma zamanının bozuk işlem durumları tarafından oluşturulan özel durumları yakalayabileceği yönetilen koda izin verilir.</span><span class="sxs-lookup"><span data-stu-id="6498f-126">In the .NET Framework version 3.5 and earlier, the common language runtime allowed managed code to catch exceptions that were raised by corrupted process states.</span></span> <span data-ttu-id="6498f-127">Erişim ihlali, bu tür bir özel durum örneğidir.</span><span class="sxs-lookup"><span data-stu-id="6498f-127">An access violation is an example of this type of exception.</span></span>  
  
 <span data-ttu-id="6498f-128">.NET Framework 4 ' te başlayarak, yönetilen kod artık bloklardaki bu tür özel durumları yakalamayacaktır `catch` .</span><span class="sxs-lookup"><span data-stu-id="6498f-128">Starting with the .NET Framework 4, managed code no longer catches these types of exceptions in `catch` blocks.</span></span> <span data-ttu-id="6498f-129">Ancak, bu değişikliği geçersiz kılabilir ve bozulmuş durum istisnalarını iki şekilde işleme devam edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6498f-129">However, you can override this change and maintain the handling of corrupted state exceptions in two ways:</span></span>  
  
- <span data-ttu-id="6498f-130">`<legacyCorruptedStateExceptionsPolicy>`Öğenin `enabled` özniteliğini olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="6498f-130">Set the `<legacyCorruptedStateExceptionsPolicy>` element's `enabled` attribute to `true`.</span></span> <span data-ttu-id="6498f-131">Bu yapılandırma ayarı, processwide uygulanır ve tüm yöntemleri etkiler.</span><span class="sxs-lookup"><span data-stu-id="6498f-131">This configuration setting is applied processwide and affects all methods.</span></span>  
  
 <span data-ttu-id="6498f-132">-veya-</span><span class="sxs-lookup"><span data-stu-id="6498f-132">-or-</span></span>  
  
- <span data-ttu-id="6498f-133"><xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType>Özel durum bloğunu içeren yönteme özniteliğini uygulayın `catch` .</span><span class="sxs-lookup"><span data-stu-id="6498f-133">Apply the <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> attribute to the method that contains the exceptions `catch` block.</span></span>  
  
 <span data-ttu-id="6498f-134">Bu yapılandırma öğesi yalnızca .NET Framework 4 ve üzeri sürümlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6498f-134">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6498f-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="6498f-135">Example</span></span>  

 <span data-ttu-id="6498f-136">Aşağıdaki örnek, uygulamanın .NET Framework 4 ' den önceki davranışa ne şekilde dönmesi gerektiğini belirtir ve tüm bozulmalı durum özel durum başarısızlıklarını yakalar.</span><span class="sxs-lookup"><span data-stu-id="6498f-136">The following example shows how to specify that the application should revert to the behavior before the .NET Framework 4, and catch all corrupting state exception failures.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6498f-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6498f-137">See also</span></span>

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>
- [<span data-ttu-id="6498f-138">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="6498f-138">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6498f-139">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="6498f-139">Configuration File Schema</span></span>](../index.md)
