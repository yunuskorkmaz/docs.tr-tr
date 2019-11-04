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
ms.openlocfilehash: ff82b0bfc1983240431e582dbd78778dc4469241
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459936"
---
# <a name="xnull-markup-extension"></a><span data-ttu-id="fd429-102">x:Null Biçimlendirme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="fd429-102">x:Null Markup Extension</span></span>
<span data-ttu-id="fd429-103">XAML üyesi için değer olarak `null` belirtir.</span><span class="sxs-lookup"><span data-stu-id="fd429-103">Specifies `null` as a value for a XAML member.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="fd429-104">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="fd429-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a><span data-ttu-id="fd429-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fd429-105">Remarks</span></span>  
 <span data-ttu-id="fd429-106">Ve C# C++ içindeki null başvurusunun anahtar sözcüğü null.</span><span class="sxs-lookup"><span data-stu-id="fd429-106">The keyword for a null reference in C# and C++ is null.</span></span> <span data-ttu-id="fd429-107">Bir null başvurusunun Microsoft Visual Basic anahtar sözcüğü `Nothing`, ancak XAML ile ilişkilendirdiğiniz arka plan kod diline bakılmaksızın `{x:Null}` her zaman XAML kullanımı olarak kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="fd429-107">The Microsoft Visual Basic keyword for a null reference is `Nothing`, but you always use `{x:Null}` as the XAML usage regardless which code-behind language you associate with the XAML.</span></span>  
  
 <span data-ttu-id="fd429-108">`x:Null` biçimlendirme uzantısının ayarlanabilir bir özelliği yok.</span><span class="sxs-lookup"><span data-stu-id="fd429-108">The `x:Null` markup extension has no settable properties.</span></span>  
  
 <span data-ttu-id="fd429-109">Null kullanımı genellikle CLR <xref:System.Nullable%601> değerinin XAML üye pozlaması ile ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="fd429-109">A null usage is often associated with the XAML member exposure of a CLR <xref:System.Nullable%601> value.</span></span>  
  
 <span data-ttu-id="fd429-110">Tüm XAML biçimlendirme uzantıları gibi `x:Null` biçimlendirme uzantısı, öznitelik değerlerinin işlenmesini, değişmez değer veya olay işleyici başvuruları dışında bırakmak için parantez (`{,}`) kullanır.</span><span class="sxs-lookup"><span data-stu-id="fd429-110">The `x:Null` markup extension, like all XAML markup extensions, uses the braces (`{,}`) for escaping the handling of attribute values to be other than literals or event-handler references.</span></span> <span data-ttu-id="fd429-111">Öznitelik sözdizimi, bu biçimlendirme uzantısıyla en sık kullanılan sözdizimidir.</span><span class="sxs-lookup"><span data-stu-id="fd429-111">Attribute syntax is the syntax most frequently used with this markup extension.</span></span> <span data-ttu-id="fd429-112">Bir nesne öğesi sözdizimi `<x:Null />` teknik açıdan olasıdır, ancak `x:Null` işaretleme uzantısının Konumsal parametre veya oluşturma bağımsız değişkenleri olmadığından nadiren kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fd429-112">An object element syntax `<x:Null />` is technically possible, but is rarely used because the `x:Null` markup extension has no positional parameters or construction arguments.</span></span>  
  
 <span data-ttu-id="fd429-113">Biçimlendirme uzantıları hakkında daha fazla bilgi için bkz. [Biçimlendirme uzantıları ve WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="fd429-113">For information about markup extensions, see [Markup Extensions and WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
 <span data-ttu-id="fd429-114">.NET Framework XAML hizmetlerinde, bu biçimlendirme uzantısının işlenmesi <xref:System.Windows.Markup.NullExtension> sınıfı tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="fd429-114">In .NET Framework XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.NullExtension> class.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="fd429-115">WPF kullanım notları</span><span class="sxs-lookup"><span data-stu-id="fd429-115">WPF Usage Notes</span></span>  
 <span data-ttu-id="fd429-116">`null`, başvuru türü bağımlılık özelliği için ilk önceden ayarlama değeri gerekmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="fd429-116">Note that `null` is not necessarily the initial unset value for a reference-type dependency property.</span></span> <span data-ttu-id="fd429-117">İlk varsayılan değer her bağımlılık özelliği için farklılık gösterebilir ve özelliğe özgü meta verileri temel alabilir.</span><span class="sxs-lookup"><span data-stu-id="fd429-117">The initial default value can vary for each dependency property and can be based on property-specific metadata.</span></span> <span data-ttu-id="fd429-118">Birçok bağımlılık özelliği, doğrulama geri çağırma uygulamalarından dolayı biçimlendirme veya kod aracılığıyla `null` değer olarak kabul etmez.</span><span class="sxs-lookup"><span data-stu-id="fd429-118">Many dependency properties do not accept `null` as a value, either through markup or code because of their validation callback implementations.</span></span> <span data-ttu-id="fd429-119">Bağımlılık özellikleri hakkında daha fazla bilgi için bkz. [bağımlılık özelliklerine genel bakış](../wpf/advanced/dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="fd429-119">For more information about dependency properties, see [Dependency Properties Overview](../wpf/advanced/dependency-properties-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd429-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd429-120">See also</span></span>

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [<span data-ttu-id="fd429-121">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="fd429-121">XAML Overview (WPF)</span></span>](../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="fd429-122">İşaretleme Uzantıları ve WPF XAML</span><span class="sxs-lookup"><span data-stu-id="fd429-122">Markup Extensions and WPF XAML</span></span>](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
