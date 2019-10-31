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
ms.openlocfilehash: c835e1bcef7bbfdc990c8db177eafed4ec6bb30c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115209"
---
# <a name="timespan_legacyformatmode-element"></a><span data-ttu-id="f23cc-102">\<TimeSpan_LegacyFormatMode > öğesi</span><span class="sxs-lookup"><span data-stu-id="f23cc-102">\<TimeSpan_LegacyFormatMode> Element</span></span>

<span data-ttu-id="f23cc-103">Çalışma zamanının, <xref:System.TimeSpan?displayProperty=nameWithType> değerleriyle biçimlendirme işlemlerinde eski davranışı koruyamayacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="f23cc-103">Determines whether the runtime preserves legacy behavior in formatting operations with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>

<span data-ttu-id="f23cc-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="f23cc-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f23cc-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="f23cc-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="f23cc-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<TimeSpan_LegacyFormatMode >**</span><span class="sxs-lookup"><span data-stu-id="f23cc-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<TimeSpan_LegacyFormatMode>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="f23cc-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f23cc-107">Syntax</span></span>

```xml
<TimeSpan_LegacyFormatMode
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f23cc-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f23cc-108">Attributes and Elements</span></span>

<span data-ttu-id="f23cc-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f23cc-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="f23cc-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f23cc-110">Attributes</span></span>

|<span data-ttu-id="f23cc-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f23cc-111">Attribute</span></span>|<span data-ttu-id="f23cc-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f23cc-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="f23cc-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="f23cc-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="f23cc-114">Çalışma zamanının <xref:System.TimeSpan?displayProperty=nameWithType> değerlerle eski biçimlendirme davranışı kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f23cc-114">Specifies whether the runtime uses legacy formatting behavior with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="f23cc-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f23cc-115">enabled Attribute</span></span>

|<span data-ttu-id="f23cc-116">Değer</span><span class="sxs-lookup"><span data-stu-id="f23cc-116">Value</span></span>|<span data-ttu-id="f23cc-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f23cc-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="f23cc-118">Çalışma zamanı eski biçimlendirme davranışını geri yüklemez.</span><span class="sxs-lookup"><span data-stu-id="f23cc-118">The runtime does not restore legacy formatting behavior.</span></span>|
|`true`|<span data-ttu-id="f23cc-119">Çalışma zamanı eski biçimlendirme davranışını geri yükler.</span><span class="sxs-lookup"><span data-stu-id="f23cc-119">The runtime restores legacy formatting behavior.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="f23cc-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f23cc-120">Child Elements</span></span>

<span data-ttu-id="f23cc-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="f23cc-121">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f23cc-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f23cc-122">Parent Elements</span></span>

|<span data-ttu-id="f23cc-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="f23cc-123">Element</span></span>|<span data-ttu-id="f23cc-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f23cc-124">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="f23cc-125">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="f23cc-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="f23cc-126">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="f23cc-126">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f23cc-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f23cc-127">Remarks</span></span>

<span data-ttu-id="f23cc-128">.NET Framework 4 ' te başlayarak, <xref:System.TimeSpan?displayProperty=nameWithType> yapısı <xref:System.IFormattable> arabirimini uygular ve standart ve özel biçim dizeleriyle biçimlendirme işlemlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="f23cc-128">Starting with the .NET Framework 4, the <xref:System.TimeSpan?displayProperty=nameWithType> structure implements the <xref:System.IFormattable> interface and supports formatting operations with standard and custom format strings.</span></span> <span data-ttu-id="f23cc-129">Bir ayrıştırma yöntemi desteklenmeyen bir biçim belirticisi veya biçim dizesiyle karşılaşırsa, bir <xref:System.FormatException>oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f23cc-129">If a parsing method encounters an unsupported format specifier or format string, it throws a <xref:System.FormatException>.</span></span>

<span data-ttu-id="f23cc-130">.NET Framework önceki sürümlerinde, <xref:System.TimeSpan> yapısı <xref:System.IFormattable> gerçekleştirmedi ve biçim dizelerini desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="f23cc-130">In previous versions of the .NET Framework, the <xref:System.TimeSpan> structure did not implement <xref:System.IFormattable> and did not support format strings.</span></span> <span data-ttu-id="f23cc-131">Ancak pek çok geliştirici, <xref:System.TimeSpan> bir dizi biçim dizesini destekledikleri ve bunları <xref:System.String.Format%2A?displayProperty=nameWithType>gibi yöntemlerle [Bileşik biçimlendirme işlemlerinde](../../../../standard/base-types/composite-formatting.md) kullanmışın yanlışlıkla kabul ediyor.</span><span class="sxs-lookup"><span data-stu-id="f23cc-131">However, many developers mistakenly assumed that <xref:System.TimeSpan> did support a set of format strings and used them in [composite formatting operations](../../../../standard/base-types/composite-formatting.md) with methods such as <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f23cc-132">Genellikle, bir tür <xref:System.IFormattable> uygular ve biçim dizelerini destekliyorsa, desteklenmeyen biçim dizelerine sahip biçimlendirme yöntemlerine yapılan çağrılar genellikle bir <xref:System.FormatException>oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f23cc-132">Ordinarily, if a type implements <xref:System.IFormattable> and supports format strings, calls to formatting methods with unsupported format strings usually throw a <xref:System.FormatException>.</span></span> <span data-ttu-id="f23cc-133">Ancak <xref:System.TimeSpan> <xref:System.IFormattable>uygulamadığından, çalışma zamanı biçim dizesini yoksaydı ve bunun yerine <xref:System.TimeSpan.ToString?displayProperty=nameWithType> yöntemi çağırılır.</span><span class="sxs-lookup"><span data-stu-id="f23cc-133">However, because <xref:System.TimeSpan> did not implement <xref:System.IFormattable>, the runtime ignored the format string and instead called the <xref:System.TimeSpan.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="f23cc-134">Bu, biçim dizelerinin biçimlendirme işlemi üzerinde hiçbir etkisi olmamasına karşın, varlığı <xref:System.FormatException>neden olmadı.</span><span class="sxs-lookup"><span data-stu-id="f23cc-134">This means that, although the format strings had no effect on the formatting operation, their presence did not result in a <xref:System.FormatException>.</span></span>

<span data-ttu-id="f23cc-135">Eski kodun bir bileşik biçimlendirme yöntemini ve geçersiz biçim dizesini geçirdiğini ve kodun yeniden derlenmesi durumunda, eski <xref:System.TimeSpan> davranışını geri yüklemek için `<TimeSpan_LegacyFormatMode>` öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f23cc-135">For cases in which legacy code passes a composite formatting method and an invalid format string, and that code cannot be recompiled, you can use the `<TimeSpan_LegacyFormatMode>` element to restore the legacy <xref:System.TimeSpan> behavior.</span></span> <span data-ttu-id="f23cc-136">Bu öğenin `enabled` özniteliğini `true`olarak ayarladığınızda, bileşik biçimlendirme yöntemi <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>yerine <xref:System.TimeSpan.ToString?displayProperty=nameWithType> çağrısıyla sonuçlanır ve bir <xref:System.FormatException> oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="f23cc-136">When you set the `enabled` attribute of this element to `true`, the composite formatting method results in a call to <xref:System.TimeSpan.ToString?displayProperty=nameWithType> rather than <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, and a <xref:System.FormatException> is not thrown.</span></span>

## <a name="example"></a><span data-ttu-id="f23cc-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="f23cc-137">Example</span></span>

<span data-ttu-id="f23cc-138">Aşağıdaki örnek bir <xref:System.TimeSpan> nesnesini örnekleyerek, desteklenmeyen bir standart biçim dizesi kullanarak onu <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> yöntemiyle biçimlendirmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="f23cc-138">The following example instantiates a <xref:System.TimeSpan> object and attempts to format it with the <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> method by using an unsupported standard format string.</span></span>

[!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
[!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]

<span data-ttu-id="f23cc-139">Örneği .NET Framework 3,5 veya önceki bir sürümde çalıştırdığınızda aşağıdaki çıktıyı görüntüler:</span><span class="sxs-lookup"><span data-stu-id="f23cc-139">When you run the example on the .NET Framework 3.5 or on an earlier version, it displays the following output:</span></span>

```
12:30:45
```

<span data-ttu-id="f23cc-140">Bu, örneği .NET Framework 4 veya sonraki bir sürümde çalıştırırsanız, çıktının dışında da farklılık gösterir:</span><span class="sxs-lookup"><span data-stu-id="f23cc-140">This differs markedly from the output if you run the example on the .NET Framework 4 or later version:</span></span>

```
Invalid Format
```

<span data-ttu-id="f23cc-141">Ancak, aşağıdaki yapılandırma dosyasını örnek dizinine ekler ve sonra örneği .NET Framework 4 veya sonraki bir sürümde çalıştırırsanız, çıkış, .NET Framework 3,5 üzerinde çalıştırıldığında örnek tarafından oluşturulan ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="f23cc-141">However, if you add the following configuration file to the example's directory and then run the example on the .NET Framework 4 or later version, the output is identical to that produced by the example when it is run on .NET Framework 3.5.</span></span>

```xml
<?xml version ="1.0"?>
<configuration>
   <runtime>
      <TimeSpan_LegacyFormatMode enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="f23cc-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f23cc-142">See also</span></span>

- [<span data-ttu-id="f23cc-143">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="f23cc-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f23cc-144">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="f23cc-144">Configuration File Schema</span></span>](../index.md)
