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
ms.openlocfilehash: f4971d61d11ec14eaeac2d2f202353e4921b9325
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90549450"
---
# <a name="xnull-markup-extension"></a><span data-ttu-id="796a7-102">x:Null Biçimlendirme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="796a7-102">x:Null Markup Extension</span></span>

<span data-ttu-id="796a7-103">`null`Xaml üyesi için değer olarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="796a7-103">Specifies `null` as a value for a XAML member.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="796a7-104">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="796a7-104">XAML Attribute Usage</span></span>

```xaml
<object property="{x:Null}" .../>
```

## <a name="remarks"></a><span data-ttu-id="796a7-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="796a7-105">Remarks</span></span>

<span data-ttu-id="796a7-106">C# ve C++ içindeki null başvurusunun anahtar sözcüğü null.</span><span class="sxs-lookup"><span data-stu-id="796a7-106">The keyword for a null reference in C# and C++ is null.</span></span> <span data-ttu-id="796a7-107">Bir null başvurusunun Microsoft Visual Basic anahtar sözcüğü vardır `Nothing` , ancak `{x:Null}` XAML ile ilişkilendirdiğiniz kod arkasındaki dilin ne olursa olsun, her zaman XAML kullanımı olarak kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="796a7-107">The Microsoft Visual Basic keyword for a null reference is `Nothing`, but you always use `{x:Null}` as the XAML usage regardless which code-behind language you associate with the XAML.</span></span>

<span data-ttu-id="796a7-108">`x:Null`Biçimlendirme uzantısının ayarlanabilir bir özelliği yok.</span><span class="sxs-lookup"><span data-stu-id="796a7-108">The `x:Null` markup extension has no settable properties.</span></span>

<span data-ttu-id="796a7-109">Null kullanımı genellikle bir CLR değerinin XAML üye pozlaması ile ilişkilendirilir <xref:System.Nullable%601> .</span><span class="sxs-lookup"><span data-stu-id="796a7-109">A null usage is often associated with the XAML member exposure of a CLR <xref:System.Nullable%601> value.</span></span>

<span data-ttu-id="796a7-110">`x:Null`Biçimlendirme uzantısı, tüm XAML biçimlendirme uzantıları gibi, `{,}` öznitelik değerlerinin işlenmesini, değişmez değer veya olay işleyici başvuruları dışında bırakmak için parantez () kullanır.</span><span class="sxs-lookup"><span data-stu-id="796a7-110">The `x:Null` markup extension, like all XAML markup extensions, uses the braces (`{,}`) for escaping the handling of attribute values to be other than literals or event-handler references.</span></span> <span data-ttu-id="796a7-111">Öznitelik sözdizimi, bu biçimlendirme uzantısıyla en sık kullanılan sözdizimidir.</span><span class="sxs-lookup"><span data-stu-id="796a7-111">Attribute syntax is the syntax most frequently used with this markup extension.</span></span> <span data-ttu-id="796a7-112">Bir nesne öğesi sözdizimi `<x:Null />` Teknik açıdan olasıdır, ancak `x:Null` biçimlendirme uzantısının Konumsal parametre veya oluşturma bağımsız değişkenleri olmadığından nadiren kullanılır.</span><span class="sxs-lookup"><span data-stu-id="796a7-112">An object element syntax `<x:Null />` is technically possible, but is rarely used because the `x:Null` markup extension has no positional parameters or construction arguments.</span></span>

<span data-ttu-id="796a7-113">Biçimlendirme uzantıları hakkında daha fazla bilgi için bkz. [Biçimlendirme uzantıları ve WPF XAML](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml).</span><span class="sxs-lookup"><span data-stu-id="796a7-113">For information about markup extensions, see [Markup Extensions and WPF XAML](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml).</span></span>

<span data-ttu-id="796a7-114">.NET XAML hizmetlerinde, bu biçimlendirme uzantısının işlenmesi sınıfı tarafından tanımlanır <xref:System.Windows.Markup.NullExtension> .</span><span class="sxs-lookup"><span data-stu-id="796a7-114">In .NET XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.NullExtension> class.</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="796a7-115">WPF kullanım notları</span><span class="sxs-lookup"><span data-stu-id="796a7-115">WPF Usage Notes</span></span>

<span data-ttu-id="796a7-116">`null`Bir başvuru türü bağımlılık özelliği için ilk önceden ayarlama değeri olması gerekmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="796a7-116">Note that `null` is not necessarily the initial unset value for a reference-type dependency property.</span></span> <span data-ttu-id="796a7-117">İlk varsayılan değer her bağımlılık özelliği için farklılık gösterebilir ve özelliğe özgü meta verileri temel alabilir.</span><span class="sxs-lookup"><span data-stu-id="796a7-117">The initial default value can vary for each dependency property and can be based on property-specific metadata.</span></span> <span data-ttu-id="796a7-118">Birçok bağımlılık özelliği `null` , doğrulama geri çağırma uygulamalarından dolayı biçimlendirme veya kod aracılığıyla bir değer olarak kabul etmez.</span><span class="sxs-lookup"><span data-stu-id="796a7-118">Many dependency properties do not accept `null` as a value, either through markup or code because of their validation callback implementations.</span></span> <span data-ttu-id="796a7-119">Bağımlılık özellikleri hakkında daha fazla bilgi için bkz. [bağımlılık özelliklerine genel bakış](/dotnet/desktop/wpf/advanced/dependency-properties-overview).</span><span class="sxs-lookup"><span data-stu-id="796a7-119">For more information about dependency properties, see [Dependency Properties Overview](/dotnet/desktop/wpf/advanced/dependency-properties-overview).</span></span>

## <a name="see-also"></a><span data-ttu-id="796a7-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="796a7-120">See also</span></span>

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [<span data-ttu-id="796a7-121">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="796a7-121">XAML Overview (WPF)</span></span>](../fundamentals/xaml.md)
- [<span data-ttu-id="796a7-122">Biçimlendirme Uzantıları ve WPF XAML</span><span class="sxs-lookup"><span data-stu-id="796a7-122">Markup Extensions and WPF XAML</span></span>](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml)
