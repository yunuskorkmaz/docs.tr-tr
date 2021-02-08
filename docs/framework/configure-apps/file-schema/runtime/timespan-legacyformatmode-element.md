---
description: 'Hakkında daha fazla bilgi edinin: <TimeSpan_LegacyFormatMode> öğesi'
title: <TimeSpan_LegacyFormatMode> Öğesi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <TimeSpan_LegacyFormatMode> element
- TimeSpan_LegacyFormatMode element
ms.assetid: 865e7207-d050-4442-b574-57ea29d5e2d6
ms.openlocfilehash: 1fa5c3a15941004ebab9e3622d4b3e7b27130e22
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802391"
---
# <a name="timespan_legacyformatmode-element"></a><span data-ttu-id="63dc0-103">\<TimeSpan_LegacyFormatMode> Öğesi</span><span class="sxs-lookup"><span data-stu-id="63dc0-103">\<TimeSpan_LegacyFormatMode> Element</span></span>

<span data-ttu-id="63dc0-104">Çalışma zamanının, değerleri olan biçimlendirme işlemlerinde eski davranışı koruyamayacağını belirler <xref:System.TimeSpan?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="63dc0-104">Determines whether the runtime preserves legacy behavior in formatting operations with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<TimeSpan_LegacyFormatMode>**  

## <a name="syntax"></a><span data-ttu-id="63dc0-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="63dc0-105">Syntax</span></span>

```xml
<TimeSpan_LegacyFormatMode
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="63dc0-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="63dc0-106">Attributes and Elements</span></span>

<span data-ttu-id="63dc0-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="63dc0-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="63dc0-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="63dc0-108">Attributes</span></span>

|<span data-ttu-id="63dc0-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="63dc0-109">Attribute</span></span>|<span data-ttu-id="63dc0-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="63dc0-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="63dc0-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="63dc0-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="63dc0-112">Çalışma zamanının değerlerle eski biçimlendirme davranışı kullanıp kullanmadığını belirtir <xref:System.TimeSpan?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="63dc0-112">Specifies whether the runtime uses legacy formatting behavior with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="63dc0-113">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="63dc0-113">enabled Attribute</span></span>

|<span data-ttu-id="63dc0-114">Değer</span><span class="sxs-lookup"><span data-stu-id="63dc0-114">Value</span></span>|<span data-ttu-id="63dc0-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="63dc0-115">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="63dc0-116">Çalışma zamanı eski biçimlendirme davranışını geri yüklemez.</span><span class="sxs-lookup"><span data-stu-id="63dc0-116">The runtime does not restore legacy formatting behavior.</span></span>|
|`true`|<span data-ttu-id="63dc0-117">Çalışma zamanı eski biçimlendirme davranışını geri yükler.</span><span class="sxs-lookup"><span data-stu-id="63dc0-117">The runtime restores legacy formatting behavior.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="63dc0-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="63dc0-118">Child Elements</span></span>

<span data-ttu-id="63dc0-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="63dc0-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="63dc0-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="63dc0-120">Parent Elements</span></span>

|<span data-ttu-id="63dc0-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="63dc0-121">Element</span></span>|<span data-ttu-id="63dc0-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="63dc0-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="63dc0-123">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="63dc0-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="63dc0-124">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="63dc0-124">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="63dc0-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="63dc0-125">Remarks</span></span>

<span data-ttu-id="63dc0-126">.NET Framework 4 ' te başlayarak, <xref:System.TimeSpan?displayProperty=nameWithType> Yapı <xref:System.IFormattable> arabirimini uygular ve standart ve özel biçim dizeleriyle biçimlendirme işlemlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="63dc0-126">Starting with the .NET Framework 4, the <xref:System.TimeSpan?displayProperty=nameWithType> structure implements the <xref:System.IFormattable> interface and supports formatting operations with standard and custom format strings.</span></span> <span data-ttu-id="63dc0-127">Bir ayrıştırma yöntemi desteklenmeyen bir biçim belirticisi veya biçim dizesiyle karşılaşırsa, bir oluşturur <xref:System.FormatException> .</span><span class="sxs-lookup"><span data-stu-id="63dc0-127">If a parsing method encounters an unsupported format specifier or format string, it throws a <xref:System.FormatException>.</span></span>

<span data-ttu-id="63dc0-128">.NET Framework önceki sürümlerinde, <xref:System.TimeSpan> Yapı uygulamadı <xref:System.IFormattable> ve biçim dizelerini desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="63dc0-128">In previous versions of the .NET Framework, the <xref:System.TimeSpan> structure did not implement <xref:System.IFormattable> and did not support format strings.</span></span> <span data-ttu-id="63dc0-129">Ancak birçok geliştirici yanlışlıkla <xref:System.TimeSpan> bir dizi biçim dizesini destekledikleri ve bunları gibi yöntemlerle [Bileşik biçimlendirme işlemlerinde](../../../../standard/base-types/composite-formatting.md) kullandık <xref:System.String.Format%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="63dc0-129">However, many developers mistakenly assumed that <xref:System.TimeSpan> did support a set of format strings and used them in [composite formatting operations](../../../../standard/base-types/composite-formatting.md) with methods such as <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="63dc0-130">Genellikle, bir tür, <xref:System.IFormattable> Biçim dizelerini uygular ve destekliyorsa, desteklenmeyen biçim dizelerine sahip biçimlendirme yöntemlerine yapılan çağrılar genellikle bir oluşturur <xref:System.FormatException> .</span><span class="sxs-lookup"><span data-stu-id="63dc0-130">Ordinarily, if a type implements <xref:System.IFormattable> and supports format strings, calls to formatting methods with unsupported format strings usually throw a <xref:System.FormatException>.</span></span> <span data-ttu-id="63dc0-131">Ancak, <xref:System.TimeSpan> uygulamadığından, <xref:System.IFormattable> çalışma zamanı biçim dizesini yoksaydı ve bunun yerine <xref:System.TimeSpan.ToString?displayProperty=nameWithType> yöntemi çağırılır.</span><span class="sxs-lookup"><span data-stu-id="63dc0-131">However, because <xref:System.TimeSpan> did not implement <xref:System.IFormattable>, the runtime ignored the format string and instead called the <xref:System.TimeSpan.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="63dc0-132">Bu, biçim dizelerinin biçimlendirme işlemi üzerinde hiçbir etkisi olmamasına karşın, varlığı bir ile sonuçlanmamasıdır <xref:System.FormatException> .</span><span class="sxs-lookup"><span data-stu-id="63dc0-132">This means that, although the format strings had no effect on the formatting operation, their presence did not result in a <xref:System.FormatException>.</span></span>

<span data-ttu-id="63dc0-133">Eski kodun bir bileşik biçimlendirme yöntemini ve geçersiz biçim dizesini geçirdiğini ve kodun yeniden derlenmesi durumunda, `<TimeSpan_LegacyFormatMode>` eski davranışı geri yüklemek için öğesini kullanabilirsiniz <xref:System.TimeSpan> .</span><span class="sxs-lookup"><span data-stu-id="63dc0-133">For cases in which legacy code passes a composite formatting method and an invalid format string, and that code cannot be recompiled, you can use the `<TimeSpan_LegacyFormatMode>` element to restore the legacy <xref:System.TimeSpan> behavior.</span></span> <span data-ttu-id="63dc0-134">`enabled`Bu öğenin özniteliğini olarak ayarladığınızda `true` , bileşik biçimlendirme yöntemi, yerine öğesine çağrı ile sonuçlanır <xref:System.TimeSpan.ToString?displayProperty=nameWithType> <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> ve bir oluşturulmaz <xref:System.FormatException> .</span><span class="sxs-lookup"><span data-stu-id="63dc0-134">When you set the `enabled` attribute of this element to `true`, the composite formatting method results in a call to <xref:System.TimeSpan.ToString?displayProperty=nameWithType> rather than <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, and a <xref:System.FormatException> is not thrown.</span></span>

## <a name="example"></a><span data-ttu-id="63dc0-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="63dc0-135">Example</span></span>

<span data-ttu-id="63dc0-136">Aşağıdaki örnek bir nesnesi oluşturur <xref:System.TimeSpan> ve <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> Desteklenmeyen bir standart biçim dizesi kullanarak yöntemi ile biçimlendirmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="63dc0-136">The following example instantiates a <xref:System.TimeSpan> object and attempts to format it with the <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> method by using an unsupported standard format string.</span></span>

[!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
[!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]

<span data-ttu-id="63dc0-137">Örneği .NET Framework 3,5 veya önceki bir sürümde çalıştırdığınızda aşağıdaki çıktıyı görüntüler:</span><span class="sxs-lookup"><span data-stu-id="63dc0-137">When you run the example on the .NET Framework 3.5 or on an earlier version, it displays the following output:</span></span>

```console
12:30:45
```

<span data-ttu-id="63dc0-138">Bu, örneği .NET Framework 4 veya sonraki bir sürümde çalıştırırsanız, çıktının dışında da farklılık gösterir:</span><span class="sxs-lookup"><span data-stu-id="63dc0-138">This differs markedly from the output if you run the example on the .NET Framework 4 or later version:</span></span>

```console
Invalid Format
```

<span data-ttu-id="63dc0-139">Ancak, aşağıdaki yapılandırma dosyasını örnek dizinine ekler ve sonra örneği .NET Framework 4 veya sonraki bir sürümde çalıştırırsanız, çıkış, .NET Framework 3,5 üzerinde çalıştırıldığında örnek tarafından oluşturulan ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="63dc0-139">However, if you add the following configuration file to the example's directory and then run the example on the .NET Framework 4 or later version, the output is identical to that produced by the example when it is run on .NET Framework 3.5.</span></span>

```xml
<?xml version ="1.0"?>
<configuration>
   <runtime>
      <TimeSpan_LegacyFormatMode enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="63dc0-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63dc0-140">See also</span></span>

- [<span data-ttu-id="63dc0-141">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="63dc0-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="63dc0-142">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="63dc0-142">Configuration File Schema</span></span>](../index.md)
