---
title: x:Null Biçimlendirme Uzantısı
ms.date: 03/30/2017
f1_keywords:
- NullExtension
- x:NullExtension
- x:Null
- "Null"
- xNull
helpviewer_keywords:
- Null markup extension in XAML [XAML Services]
- x:Null markup extension [XAML Services]
- XAML [XAML Services], x:Null markup extension
ms.assetid: 2e3ccc21-4996-481d-91b5-3910d8b3bfa3
ms.openlocfilehash: b83e893f951c15eca69fbb6b002369dd723ca469
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071432"
---
# <a name="xnull-markup-extension"></a><span data-ttu-id="50c10-102">x:Null Biçimlendirme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="50c10-102">x:Null Markup Extension</span></span>

<span data-ttu-id="50c10-103">Bir XAML üyesi için bir değer olarak belirtir. `null`</span><span class="sxs-lookup"><span data-stu-id="50c10-103">Specifies `null` as a value for a XAML member.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="50c10-104">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="50c10-104">XAML Attribute Usage</span></span>

```xaml
<object property="{x:Null}" .../>
```

## <a name="remarks"></a><span data-ttu-id="50c10-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="50c10-105">Remarks</span></span>

<span data-ttu-id="50c10-106">C# ve C++'da null başvurusu için kullanılan anahtar kelime null'dur.</span><span class="sxs-lookup"><span data-stu-id="50c10-106">The keyword for a null reference in C# and C++ is null.</span></span> <span data-ttu-id="50c10-107">Null reference için Microsoft Visual Basic `Nothing`anahtar sözcüğü, xaml ile ilişkilendirdiğiniz kod arkası dili ne olursa olsun her zaman XAML kullanımı olarak kullanılır. `{x:Null}`</span><span class="sxs-lookup"><span data-stu-id="50c10-107">The Microsoft Visual Basic keyword for a null reference is `Nothing`, but you always use `{x:Null}` as the XAML usage regardless which code-behind language you associate with the XAML.</span></span>

<span data-ttu-id="50c10-108">`x:Null` Biçimlendirme uzantısı ayarlanan özellikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="50c10-108">The `x:Null` markup extension has no settable properties.</span></span>

<span data-ttu-id="50c10-109">Null kullanımı genellikle bir CLR <xref:System.Nullable%601> değerinin XAML üye maruziyeti ile ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="50c10-109">A null usage is often associated with the XAML member exposure of a CLR <xref:System.Nullable%601> value.</span></span>

<span data-ttu-id="50c10-110">`x:Null` Tüm XAML biçimlendirme uzantıları gibi biçimlendirme uzantısı, öznitelik değerlerinin işlenmesinden gerçek veya olay işleyicisi başvurularından başka bir şekilde kaçmak için ayraçları ()`{,}`kullanır.</span><span class="sxs-lookup"><span data-stu-id="50c10-110">The `x:Null` markup extension, like all XAML markup extensions, uses the braces (`{,}`) for escaping the handling of attribute values to be other than literals or event-handler references.</span></span> <span data-ttu-id="50c10-111">Öznitelik sözdizimi, bu biçimlendirme uzantısı ile en sık kullanılan sözdizimidir.</span><span class="sxs-lookup"><span data-stu-id="50c10-111">Attribute syntax is the syntax most frequently used with this markup extension.</span></span> <span data-ttu-id="50c10-112">Bir nesne öğesi `<x:Null />` sözdizimi teknik olarak mümkündür, ancak `x:Null` biçimlendirme uzantısı konumsal parametreler veya yapı bağımsız değişkenleri olmadığından nadiren kullanılır.</span><span class="sxs-lookup"><span data-stu-id="50c10-112">An object element syntax `<x:Null />` is technically possible, but is rarely used because the `x:Null` markup extension has no positional parameters or construction arguments.</span></span>

<span data-ttu-id="50c10-113">Biçimlendirme uzantıları hakkında daha fazla bilgi için [bkz.](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)</span><span class="sxs-lookup"><span data-stu-id="50c10-113">For information about markup extensions, see [Markup Extensions and WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>

<span data-ttu-id="50c10-114">.NET XAML Hizmetleri'nde, bu biçimlendirme uzantısı <xref:System.Windows.Markup.NullExtension> için işleme sınıf tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="50c10-114">In .NET XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.NullExtension> class.</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="50c10-115">WPF Kullanım Notları</span><span class="sxs-lookup"><span data-stu-id="50c10-115">WPF Usage Notes</span></span>

<span data-ttu-id="50c10-116">Başvuru `null` türü bağımlılık özelliği için ilk ayarlanmamış değerin mutlaka olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="50c10-116">Note that `null` is not necessarily the initial unset value for a reference-type dependency property.</span></span> <span data-ttu-id="50c10-117">İlk varsayılan değer her bağımlılık özelliği için değişebilir ve özelliğe özgü meta verilere dayalı olabilir.</span><span class="sxs-lookup"><span data-stu-id="50c10-117">The initial default value can vary for each dependency property and can be based on property-specific metadata.</span></span> <span data-ttu-id="50c10-118">Birçok bağımlılık özelliği, `null` doğrulama geri arama uygulamaları nedeniyle biçimlendirme veya kod yoluyla bir değer olarak kabul etmez.</span><span class="sxs-lookup"><span data-stu-id="50c10-118">Many dependency properties do not accept `null` as a value, either through markup or code because of their validation callback implementations.</span></span> <span data-ttu-id="50c10-119">Bağımlılık özellikleri hakkında daha fazla bilgi için [bkz.](../../framework/wpf/advanced/dependency-properties-overview.md)</span><span class="sxs-lookup"><span data-stu-id="50c10-119">For more information about dependency properties, see [Dependency Properties Overview](../../framework/wpf/advanced/dependency-properties-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="50c10-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50c10-120">See also</span></span>

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [<span data-ttu-id="50c10-121">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="50c10-121">XAML Overview (WPF)</span></span>](../fundamentals/xaml.md)
- [<span data-ttu-id="50c10-122">Biçimlendirme Uzantıları ve WPF XAML</span><span class="sxs-lookup"><span data-stu-id="50c10-122">Markup Extensions and WPF XAML</span></span>](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
