---
title: "&lt;TimeSpan_LegacyFormatMode&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <TimeSpan_LegacyFormatMode> element
- TimeSpan_LegacyFormatMode element
ms.assetid: 865e7207-d050-4442-b574-57ea29d5e2d6
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2724b3811e9cc28888a9beac0c1ed77092302c3b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="lttimespanlegacyformatmodegt-element"></a><span data-ttu-id="fe720-102">&lt;TimeSpan_LegacyFormatMode&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="fe720-102">&lt;TimeSpan_LegacyFormatMode&gt; Element</span></span>
<span data-ttu-id="fe720-103">Çalışma zamanı işlemleriyle biçimlendirmesindeki eski davranışı korur olup olmadığını belirler <xref:System.TimeSpan?displayProperty=nameWithType> değerleri.</span><span class="sxs-lookup"><span data-stu-id="fe720-103">Determines whether the runtime preserves legacy behavior in formatting operations with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>  
  
 <span data-ttu-id="fe720-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="fe720-104">\<configuration></span></span>  
<span data-ttu-id="fe720-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="fe720-105">\<runtime></span></span>  
<span data-ttu-id="fe720-106">< TimeSpan_LegacyFormatMode ></span><span class="sxs-lookup"><span data-stu-id="fe720-106"><TimeSpan_LegacyFormatMode></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe720-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fe720-107">Syntax</span></span>  
  
```xml  
<TimeSpan_LegacyFormatMode    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fe720-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fe720-108">Attributes and Elements</span></span>  
 <span data-ttu-id="fe720-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fe720-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fe720-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fe720-110">Attributes</span></span>  
  
|<span data-ttu-id="fe720-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fe720-111">Attribute</span></span>|<span data-ttu-id="fe720-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe720-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="fe720-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="fe720-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="fe720-114">Çalışma zamanı ile eski biçimlendirme davranışı kullanıp kullanmadığını belirtir <xref:System.TimeSpan?displayProperty=nameWithType> değerleri.</span><span class="sxs-lookup"><span data-stu-id="fe720-114">Specifies whether the runtime uses legacy formatting behavior with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="fe720-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fe720-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="fe720-116">Değer</span><span class="sxs-lookup"><span data-stu-id="fe720-116">Value</span></span>|<span data-ttu-id="fe720-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe720-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="fe720-118">Çalışma zamanı eski biçimlendirme davranışı geri yüklemeyin.</span><span class="sxs-lookup"><span data-stu-id="fe720-118">The runtime does not restore legacy formatting behavior.</span></span>|  
|`true`|<span data-ttu-id="fe720-119">Çalışma zamanı eski biçimlendirme davranışını geri yükler.</span><span class="sxs-lookup"><span data-stu-id="fe720-119">The runtime restores legacy formatting behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fe720-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fe720-120">Child Elements</span></span>  
 <span data-ttu-id="fe720-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="fe720-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fe720-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fe720-122">Parent Elements</span></span>  
  
|<span data-ttu-id="fe720-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="fe720-123">Element</span></span>|<span data-ttu-id="fe720-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe720-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="fe720-125">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="fe720-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="fe720-126">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="fe720-126">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe720-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fe720-127">Remarks</span></span>  
 <span data-ttu-id="fe720-128">İle başlayarak [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], <xref:System.TimeSpan?displayProperty=nameWithType> Implements yapısı <xref:System.IFormattable> arabirimi ve standart ve özel biçim dizeleri işlemleriyle biçimlendirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="fe720-128">Starting with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], the <xref:System.TimeSpan?displayProperty=nameWithType> structure implements the <xref:System.IFormattable> interface and supports formatting operations with standard and custom format strings.</span></span> <span data-ttu-id="fe720-129">Desteklenmeyen Biçim belirticisi veya biçim dizesini ayrıştırma yönteminin karşılaştığında oluşturur bir <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="fe720-129">If a parsing method encounters an unsupported format specifier or format string, it throws a <xref:System.FormatException>.</span></span>  
  
 <span data-ttu-id="fe720-130">.NET Framework'ün önceki sürümlerinde <xref:System.TimeSpan> uygulamaz yapısı <xref:System.IFormattable> ve biçim dizeleri desteklememektedir.</span><span class="sxs-lookup"><span data-stu-id="fe720-130">In previous versions of the .NET Framework, the <xref:System.TimeSpan> structure did not implement <xref:System.IFormattable> and did not support format strings.</span></span> <span data-ttu-id="fe720-131">Bununla birlikte, çoğu geliştiricinin yanlışlıkla kabul, <xref:System.TimeSpan> biçim dizeleri kümesi desteklemediği ve bunların içinde kullanılan [bileşik işlemleri biçimlendirme](../../../../../docs/standard/base-types/composite-formatting.md) gibi yöntemleriyle <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fe720-131">However, many developers mistakenly assumed that <xref:System.TimeSpan> did support a set of format strings and used them in [composite formatting operations](../../../../../docs/standard/base-types/composite-formatting.md) with methods such as <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fe720-132">Normalde, bir tür uyguluyorsa <xref:System.IFormattable> ve destekler biçim dizeleri, dizeler genellikle throw yöntemleri desteklenmeyen biçim çağrıları bir <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="fe720-132">Ordinarily, if a type implements <xref:System.IFormattable> and supports format strings, calls to formatting methods with unsupported format strings usually throw a <xref:System.FormatException>.</span></span> <span data-ttu-id="fe720-133">Ancak, çünkü <xref:System.TimeSpan> uygulamaz <xref:System.IFormattable>, çalışma zamanı biçim dizesi yoksayıldı ve bunun yerine adlı <xref:System.TimeSpan.ToString?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fe720-133">However, because <xref:System.TimeSpan> did not implement <xref:System.IFormattable>, the runtime ignored the format string and instead called the <xref:System.TimeSpan.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="fe720-134">Biçim dizeleri biçimlendirme işlemi üzerinde hiçbir etkisi olan karşın, bunların varlığı içinde sonucu oluşmadıysa, yani bir <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="fe720-134">This means that, although the format strings had no effect on the formatting operation, their presence did not result in a <xref:System.FormatException>.</span></span>  
  
 <span data-ttu-id="fe720-135">Eski kod iletir bir bileşik yöntemi ve geçersiz biçim dizesi biçimlendirme ve kodun yeniden derlenmesi durumlarda, kullandığınız `<TimeSpan_LegacyFormatMode>` eski geri yüklemek için öğesi <xref:System.TimeSpan> davranışı.</span><span class="sxs-lookup"><span data-stu-id="fe720-135">For cases in which legacy code passes a composite formatting method and an invalid format string, and that code cannot be recompiled, you can use the `<TimeSpan_LegacyFormatMode>` element to restore the legacy <xref:System.TimeSpan> behavior.</span></span> <span data-ttu-id="fe720-136">Ayarladığınızda `enabled` özniteliği bu öğenin `true`, bileşik bir çağrı yöntemi sonuçlarında biçimlendirme <xref:System.TimeSpan.ToString?displayProperty=nameWithType> yerine <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>ve bir <xref:System.FormatException> değil atılır.</span><span class="sxs-lookup"><span data-stu-id="fe720-136">When you set the `enabled` attribute of this element to `true`, the composite formatting method results in a call to <xref:System.TimeSpan.ToString?displayProperty=nameWithType> rather than <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, and a <xref:System.FormatException> is not thrown.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe720-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="fe720-137">Example</span></span>  
 <span data-ttu-id="fe720-138">Aşağıdaki örnek başlatır bir <xref:System.TimeSpan> nesne ve ile biçimlendirmeniz girişimleri <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> desteklenmeyen standart biçim dizesini kullanarak yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fe720-138">The following example instantiates a <xref:System.TimeSpan> object and attempts to format it with the <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> method by using an unsupported standard format string.</span></span>  
  
 [!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
 [!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]  
  
 <span data-ttu-id="fe720-139">Örnek çalıştırdığınızda [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] veya önceki bir sürümünde aşağıdaki çıkış gösterir:</span><span class="sxs-lookup"><span data-stu-id="fe720-139">When you run the example on the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] or on an earlier version, it displays the following output:</span></span>  
  
```  
12:30:45  
```  
  
 <span data-ttu-id="fe720-140">Örnek çalıştırırsanız, bu belirtmeyecektir çıktısını farklıdır [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] veya sonraki sürümü:</span><span class="sxs-lookup"><span data-stu-id="fe720-140">This differs markedly from the output if you run the example on the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] or later version:</span></span>  
  
```  
Invalid Format  
```  
  
 <span data-ttu-id="fe720-141">Ancak, örneği aşağıdaki yapılandırma dosyası eklerseniz, dizin adı ve örnek sonra çalıştıracağınız [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] veya sonraki bir sürümü çıktı çalışırken örnek tarafından üretilen özdeş [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fe720-141">However, if you add the following configuration file to the example's directory and then run the example on the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] or later version, the output is identical to that produced by the example when it is run on [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <TimeSpan_LegacyFormatMode enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fe720-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fe720-142">See Also</span></span>  
 [<span data-ttu-id="fe720-143">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="fe720-143">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="fe720-144">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="fe720-144">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
