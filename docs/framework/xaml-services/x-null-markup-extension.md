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
ms.openlocfilehash: 94cfaee9a0a9a9f3892b9df50ac59103709a3b14
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562355"
---
# <a name="xnull-markup-extension"></a><span data-ttu-id="8863d-102">x:Null İşaretleme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="8863d-102">x:Null Markup Extension</span></span>
<span data-ttu-id="8863d-103">Belirtir `null` XAML üyesi için bir değer olarak.</span><span class="sxs-lookup"><span data-stu-id="8863d-103">Specifies `null` as a value for a XAML member.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="8863d-104">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="8863d-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a><span data-ttu-id="8863d-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8863d-105">Remarks</span></span>  
 <span data-ttu-id="8863d-106">Bir null başvuru C# anahtar sözcüğü ve [!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)] null.</span><span class="sxs-lookup"><span data-stu-id="8863d-106">The keyword for a null reference in C# and [!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)] is null.</span></span> <span data-ttu-id="8863d-107">Microsoft Visual Basic anahtar sözcüğü bir null başvuru için `Nothing`, ancak her zaman kullanmanız `{x:Null}` arka plan kod dili XAML ile ilişkilendirmek XAML kullanımı bağımsız olarak.</span><span class="sxs-lookup"><span data-stu-id="8863d-107">The Microsoft Visual Basic keyword for a null reference is `Nothing`, but you always use `{x:Null}` as the XAML usage regardless which code-behind language you associate with the XAML.</span></span>  
  
 <span data-ttu-id="8863d-108">`x:Null` Biçimlendirme uzantısı olan ayarlanabilir özellik yok.</span><span class="sxs-lookup"><span data-stu-id="8863d-108">The `x:Null` markup extension has no settable properties.</span></span>  
  
 <span data-ttu-id="8863d-109">Bir null kullanımı genellikle bir CLR XAML üye riskini ile ilişkilendirilen <xref:System.Nullable%601> değeri.</span><span class="sxs-lookup"><span data-stu-id="8863d-109">A null usage is often associated with the XAML member exposure of a CLR <xref:System.Nullable%601> value.</span></span>  
  
 <span data-ttu-id="8863d-110">`x:Null` Tüm XAML biçimlendirme uzantıları gibi biçimlendirme uzantısı kullanır küme ayraçları (`{,}`) öznitelik değerlerini değişmez değerleri veya olay işleyicisi başvuruları dışında olacak şekilde işlenmesini kaçış için.</span><span class="sxs-lookup"><span data-stu-id="8863d-110">The `x:Null` markup extension, like all XAML markup extensions, uses the braces (`{,}`) for escaping the handling of attribute values to be other than literals or event-handler references.</span></span> <span data-ttu-id="8863d-111">Öznitelik sözdizimi bu biçimlendirme uzantısı ile en sık kullanılan sözdizimi şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="8863d-111">Attribute syntax is the syntax most frequently used with this markup extension.</span></span> <span data-ttu-id="8863d-112">Bir nesne öğesi sözdizimi `<x:Null />` teknik olarak mümkün olmakla birlikte, çünkü nadiren kullanılır `x:Null` biçimlendirme uzantısı hiçbir konumsal parametreler ya da yapım bağımsız değişken içeriyor.</span><span class="sxs-lookup"><span data-stu-id="8863d-112">An object element syntax `<x:Null />` is technically possible, but is rarely used because the `x:Null` markup extension has no positional parameters or construction arguments.</span></span>  
  
 <span data-ttu-id="8863d-113">Biçimlendirme uzantıları hakkında daha fazla bilgi için bkz: [biçimlendirme uzantıları ve WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="8863d-113">For information about markup extensions, see [Markup Extensions and WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
 <span data-ttu-id="8863d-114">.NET Framework XAML hizmetlerinde bu biçimlendirme uzantısı işlenmesi tarafından tanımlanan <xref:System.Windows.Markup.NullExtension> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8863d-114">In .NET Framework XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.NullExtension> class.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="8863d-115">WPF kullanım notları</span><span class="sxs-lookup"><span data-stu-id="8863d-115">WPF Usage Notes</span></span>  
 <span data-ttu-id="8863d-116">Unutmayın `null` mutlaka bir başvuru türü bağımlılık özelliği için ilk unset değer değil.</span><span class="sxs-lookup"><span data-stu-id="8863d-116">Note that `null` is not necessarily the initial unset value for a reference-type dependency property.</span></span> <span data-ttu-id="8863d-117">İlk varsayılan değer her bağımlılık özelliği için farklı olabilir ve özelliklere özgü meta verileri temel alarak.</span><span class="sxs-lookup"><span data-stu-id="8863d-117">The initial default value can vary for each dependency property and can be based on property-specific metadata.</span></span> <span data-ttu-id="8863d-118">Pek çok bağımlılık özellikleri kabul `null` olarak işaretleme veya kod kendi doğrulama geri çağırma uygulamalarını nedeniyle yoluyla bir değer.</span><span class="sxs-lookup"><span data-stu-id="8863d-118">Many dependency properties do not accept `null` as a value, either through markup or code because of their validation callback implementations.</span></span> <span data-ttu-id="8863d-119">Bağımlılık özellikleri hakkında daha fazla bilgi için bkz: [bağımlılık özelliklerine genel bakış](../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8863d-119">For more information about dependency properties, see [Dependency Properties Overview](../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8863d-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8863d-120">See Also</span></span>  
 <xref:System.Windows.DependencyProperty.UnsetValue>  
 [<span data-ttu-id="8863d-121">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="8863d-121">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="8863d-122">İşaretleme Uzantıları ve WPF XAML</span><span class="sxs-lookup"><span data-stu-id="8863d-122">Markup Extensions and WPF XAML</span></span>](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
