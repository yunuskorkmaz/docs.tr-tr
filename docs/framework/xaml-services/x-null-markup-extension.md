---
title: x:Null İşaretleme Uzantısı
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
ms.openlocfilehash: 5f0856f50e73a090d0ef624e2fb894d68b73c07e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54553327"
---
# <a name="xnull-markup-extension"></a><span data-ttu-id="a36d6-102">x:Null İşaretleme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="a36d6-102">x:Null Markup Extension</span></span>
<span data-ttu-id="a36d6-103">Belirtir `null` XAML üyesi için bir değer olarak.</span><span class="sxs-lookup"><span data-stu-id="a36d6-103">Specifies `null` as a value for a XAML member.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="a36d6-104">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="a36d6-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a><span data-ttu-id="a36d6-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a36d6-105">Remarks</span></span>  
 <span data-ttu-id="a36d6-106">Null başvuru anahtar sözcüğü C# ve [!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)] null.</span><span class="sxs-lookup"><span data-stu-id="a36d6-106">The keyword for a null reference in C# and [!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)] is null.</span></span> <span data-ttu-id="a36d6-107">Bir null başvuru için Microsoft Visual Basic anahtar `Nothing`, ancak her zaman `{x:Null}` arka plan kod dili ile XAML ilişkilendirmek XAML kullanım bakılmaksızın olarak.</span><span class="sxs-lookup"><span data-stu-id="a36d6-107">The Microsoft Visual Basic keyword for a null reference is `Nothing`, but you always use `{x:Null}` as the XAML usage regardless which code-behind language you associate with the XAML.</span></span>  
  
 <span data-ttu-id="a36d6-108">`x:Null` İşaretleme uzantısı ayarlanabilir özelliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a36d6-108">The `x:Null` markup extension has no settable properties.</span></span>  
  
 <span data-ttu-id="a36d6-109">Bir null kullanımı genellikle bir CLR XAML üye açığa ile ilişkilendirilir <xref:System.Nullable%601> değeri.</span><span class="sxs-lookup"><span data-stu-id="a36d6-109">A null usage is often associated with the XAML member exposure of a CLR <xref:System.Nullable%601> value.</span></span>  
  
 <span data-ttu-id="a36d6-110">`x:Null` Tüm XAML biçimlendirme uzantıları gibi işaretleme uzantısı ayraçlar kullanır (`{,}`) değişmez değerler veya olay işleyicisi başvuruları dışındaki öznitelik değerlerinin işlenmesi kaçış.</span><span class="sxs-lookup"><span data-stu-id="a36d6-110">The `x:Null` markup extension, like all XAML markup extensions, uses the braces (`{,}`) for escaping the handling of attribute values to be other than literals or event-handler references.</span></span> <span data-ttu-id="a36d6-111">Öznitelik sözdizimi, bu işaretleme uzantısı ile en sık kullanılan sözdizimidir.</span><span class="sxs-lookup"><span data-stu-id="a36d6-111">Attribute syntax is the syntax most frequently used with this markup extension.</span></span> <span data-ttu-id="a36d6-112">Bir nesne öğesi sözdizimi `<x:Null />` teknik olarak mümkündür, ancak nadiren kullanılır çünkü `x:Null` biçimlendirme uzantısına sahip hiçbir konumsal parametreler ya da yapı bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="a36d6-112">An object element syntax `<x:Null />` is technically possible, but is rarely used because the `x:Null` markup extension has no positional parameters or construction arguments.</span></span>  
  
 <span data-ttu-id="a36d6-113">Biçimlendirme uzantıları hakkında daha fazla bilgi için bkz. [biçimlendirme uzantıları ve WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="a36d6-113">For information about markup extensions, see [Markup Extensions and WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
 <span data-ttu-id="a36d6-114">.NET Framework XAML hizmetlerinde bu işaretleme uzantısının işlenmesi tarafından tanımlanan <xref:System.Windows.Markup.NullExtension> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a36d6-114">In .NET Framework XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.NullExtension> class.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="a36d6-115">WPF kullanım notları</span><span class="sxs-lookup"><span data-stu-id="a36d6-115">WPF Usage Notes</span></span>  
 <span data-ttu-id="a36d6-116">Unutmayın `null` mutlaka bir başvuru türü bağımlılık özelliği için başlangıç unset değeri değil.</span><span class="sxs-lookup"><span data-stu-id="a36d6-116">Note that `null` is not necessarily the initial unset value for a reference-type dependency property.</span></span> <span data-ttu-id="a36d6-117">İlk varsayılan değer, her bir bağımlılık özelliği için değişebilir ve özelliklere özgü meta veriler hakkında temel alabilir.</span><span class="sxs-lookup"><span data-stu-id="a36d6-117">The initial default value can vary for each dependency property and can be based on property-specific metadata.</span></span> <span data-ttu-id="a36d6-118">Birçok bağımlılık özellikleri kabul `null` bir değer olarak işaretleme ya da kendi doğrulama geri çağırma uygulamaları nedeniyle kod aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="a36d6-118">Many dependency properties do not accept `null` as a value, either through markup or code because of their validation callback implementations.</span></span> <span data-ttu-id="a36d6-119">Bağımlılık özellikleri hakkında daha fazla bilgi için bkz: [bağımlılık özelliklerine genel bakış](../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a36d6-119">For more information about dependency properties, see [Dependency Properties Overview](../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a36d6-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a36d6-120">See also</span></span>
- <xref:System.Windows.DependencyProperty.UnsetValue>
- [<span data-ttu-id="a36d6-121">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="a36d6-121">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="a36d6-122">İşaretleme Uzantıları ve WPF XAML</span><span class="sxs-lookup"><span data-stu-id="a36d6-122">Markup Extensions and WPF XAML</span></span>](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
