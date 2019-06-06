---
title: <TimeSpan_LegacyFormatMode> Öğesi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <TimeSpan_LegacyFormatMode> element
- TimeSpan_LegacyFormatMode element
ms.assetid: 865e7207-d050-4442-b574-57ea29d5e2d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4e265fd1de6047cd53b0f8d1c20c8a9e87b3e813
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66689673"
---
# <a name="timespanlegacyformatmode-element"></a><span data-ttu-id="8f25e-102">\<TimeSpan_LegacyFormatMode > öğesi</span><span class="sxs-lookup"><span data-stu-id="8f25e-102">\<TimeSpan_LegacyFormatMode> Element</span></span>

<span data-ttu-id="8f25e-103">Çalışma zamanı işlemleriyle biçimlendirmede eski davranışı korur olup olmadığını belirler <xref:System.TimeSpan?displayProperty=nameWithType> değerleri.</span><span class="sxs-lookup"><span data-stu-id="8f25e-103">Determines whether the runtime preserves legacy behavior in formatting operations with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>

<span data-ttu-id="8f25e-104">\<Yapılandırma > </span><span class="sxs-lookup"><span data-stu-id="8f25e-104">\<configuration></span></span>\
<span data-ttu-id="8f25e-105">\<çalışma zamanı > </span><span class="sxs-lookup"><span data-stu-id="8f25e-105">\<runtime></span></span>\
<span data-ttu-id="8f25e-106">\<TimeSpan_LegacyFormatMode></span><span class="sxs-lookup"><span data-stu-id="8f25e-106">\<TimeSpan_LegacyFormatMode></span></span>

## <a name="syntax"></a><span data-ttu-id="8f25e-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8f25e-107">Syntax</span></span>

```xml
<TimeSpan_LegacyFormatMode
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8f25e-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8f25e-108">Attributes and Elements</span></span>

<span data-ttu-id="8f25e-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8f25e-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="8f25e-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8f25e-110">Attributes</span></span>

|<span data-ttu-id="8f25e-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8f25e-111">Attribute</span></span>|<span data-ttu-id="8f25e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f25e-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="8f25e-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="8f25e-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="8f25e-114">Çalışma zamanı ile eski biçimlendirme davranışını kullanıp kullanmayacağını belirtir <xref:System.TimeSpan?displayProperty=nameWithType> değerleri.</span><span class="sxs-lookup"><span data-stu-id="8f25e-114">Specifies whether the runtime uses legacy formatting behavior with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="8f25e-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8f25e-115">enabled Attribute</span></span>

|<span data-ttu-id="8f25e-116">Değer</span><span class="sxs-lookup"><span data-stu-id="8f25e-116">Value</span></span>|<span data-ttu-id="8f25e-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f25e-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="8f25e-118">Çalışma zamanı biçimlendirme eski davranışı geri yüklemez.</span><span class="sxs-lookup"><span data-stu-id="8f25e-118">The runtime does not restore legacy formatting behavior.</span></span>|
|`true`|<span data-ttu-id="8f25e-119">Çalışma zamanı, eski biçimlendirme davranışını geri yükler.</span><span class="sxs-lookup"><span data-stu-id="8f25e-119">The runtime restores legacy formatting behavior.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="8f25e-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8f25e-120">Child Elements</span></span>

<span data-ttu-id="8f25e-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="8f25e-121">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8f25e-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8f25e-122">Parent Elements</span></span>

|<span data-ttu-id="8f25e-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="8f25e-123">Element</span></span>|<span data-ttu-id="8f25e-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f25e-124">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="8f25e-125">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="8f25e-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="8f25e-126">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="8f25e-126">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8f25e-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8f25e-127">Remarks</span></span>

<span data-ttu-id="8f25e-128">.NET Framework 4 ile başlayarak <xref:System.TimeSpan?displayProperty=nameWithType> Implements yapısı <xref:System.IFormattable> arabirimi ve biçimlendirme işlemleri ile standart ve özel biçim dizeleri destekler.</span><span class="sxs-lookup"><span data-stu-id="8f25e-128">Starting with the .NET Framework 4, the <xref:System.TimeSpan?displayProperty=nameWithType> structure implements the <xref:System.IFormattable> interface and supports formatting operations with standard and custom format strings.</span></span> <span data-ttu-id="8f25e-129">Bir ayrıştırma yönteminin bir desteklenmeyen biçim belirticisi veya biçim dizesi karşılaşırsa, oluşturur bir <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="8f25e-129">If a parsing method encounters an unsupported format specifier or format string, it throws a <xref:System.FormatException>.</span></span>

<span data-ttu-id="8f25e-130">.NET Framework'ün önceki sürümlerindeki <xref:System.TimeSpan> uygulamaz yapısı <xref:System.IFormattable> ve biçim dizeleri desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="8f25e-130">In previous versions of the .NET Framework, the <xref:System.TimeSpan> structure did not implement <xref:System.IFormattable> and did not support format strings.</span></span> <span data-ttu-id="8f25e-131">Ancak, birçok geliştiricinin yanlışlıkla kabul eden <xref:System.TimeSpan> bir dizi biçim dizesini desteklemediği ve kullanılan [bileşik biçimlendirme işlemleri](../../../../../docs/standard/base-types/composite-formatting.md) gibi yöntemlerle <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8f25e-131">However, many developers mistakenly assumed that <xref:System.TimeSpan> did support a set of format strings and used them in [composite formatting operations](../../../../../docs/standard/base-types/composite-formatting.md) with methods such as <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8f25e-132">Normalde, bir tür uyguluyorsa <xref:System.IFormattable> ve destekler biçim dizeleri, biçimlendirme yöntemlerine desteklenmeyen bir biçimde çağrı dizeler genellikle throw bir <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="8f25e-132">Ordinarily, if a type implements <xref:System.IFormattable> and supports format strings, calls to formatting methods with unsupported format strings usually throw a <xref:System.FormatException>.</span></span> <span data-ttu-id="8f25e-133">Ancak, çünkü <xref:System.TimeSpan> uygulamaz <xref:System.IFormattable>, çalışma zamanı biçim dizesi yoksayıldı ve bunun yerine adlı <xref:System.TimeSpan.ToString?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8f25e-133">However, because <xref:System.TimeSpan> did not implement <xref:System.IFormattable>, the runtime ignored the format string and instead called the <xref:System.TimeSpan.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="8f25e-134">Biçim dizeleri, biçimlendirme işlemi üzerinde hiçbir etkisi olmasına rağmen varlıklarını neden değil, yani bir <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="8f25e-134">This means that, although the format strings had no effect on the formatting operation, their presence did not result in a <xref:System.FormatException>.</span></span>

<span data-ttu-id="8f25e-135">Eski kod bir bileşik biçimlendirme yöntemi ve geçersiz bir biçim dizesi geçirir ve kod yeniden çalışmaları için kullanabileceğiniz `<TimeSpan_LegacyFormatMode>` eski geri yükleme öğesi <xref:System.TimeSpan> davranışı.</span><span class="sxs-lookup"><span data-stu-id="8f25e-135">For cases in which legacy code passes a composite formatting method and an invalid format string, and that code cannot be recompiled, you can use the `<TimeSpan_LegacyFormatMode>` element to restore the legacy <xref:System.TimeSpan> behavior.</span></span> <span data-ttu-id="8f25e-136">Ayarladığınızda `enabled` özniteliği bu öğenin `true`, bileşik biçimlendirme yöntemi çağrısı sonuçlarında <xref:System.TimeSpan.ToString?displayProperty=nameWithType> yerine <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>ve <xref:System.FormatException> değil oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8f25e-136">When you set the `enabled` attribute of this element to `true`, the composite formatting method results in a call to <xref:System.TimeSpan.ToString?displayProperty=nameWithType> rather than <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, and a <xref:System.FormatException> is not thrown.</span></span>

## <a name="example"></a><span data-ttu-id="8f25e-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="8f25e-137">Example</span></span>

<span data-ttu-id="8f25e-138">Aşağıdaki örnek bir <xref:System.TimeSpan> nesne ve ile biçimlendirmeniz girişimleri <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> desteklenmeyen standart biçim dizesi kullanarak yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8f25e-138">The following example instantiates a <xref:System.TimeSpan> object and attempts to format it with the <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> method by using an unsupported standard format string.</span></span>

[!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
[!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]

<span data-ttu-id="8f25e-139">.NET Framework 3.5 veya daha önceki bir sürümü örneği çalıştırdığınızda, aşağıdaki çıkışı görüntüler:</span><span class="sxs-lookup"><span data-stu-id="8f25e-139">When you run the example on the .NET Framework 3.5 or on an earlier version, it displays the following output:</span></span>

```
12:30:45
```

<span data-ttu-id="8f25e-140">.NET Framework 4 veya sonraki bir sürümü örneği çalıştırırsanız bu çıkışı ile farklıdır:</span><span class="sxs-lookup"><span data-stu-id="8f25e-140">This differs markedly from the output if you run the example on the .NET Framework 4 or later version:</span></span>

```
Invalid Format
```

<span data-ttu-id="8f25e-141">Örneğin dizinine şu yapılandırma dosyasını ekleyin ve ardından örnek .NET Framework 4 veya sonraki bir sürümünü çalıştırın, ancak çıktı, .NET Framework 3.5 üzerinde çalıştırıldığında örnek tarafından oluşturulanla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="8f25e-141">However, if you add the following configuration file to the example's directory and then run the example on the .NET Framework 4 or later version, the output is identical to that produced by the example when it is run on .NET Framework 3.5.</span></span>

```xml
<?xml version ="1.0"?>
<configuration>
   <runtime>
      <TimeSpan_LegacyFormatMode enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="8f25e-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f25e-142">See also</span></span>

- [<span data-ttu-id="8f25e-143">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="8f25e-143">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="8f25e-144">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="8f25e-144">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
