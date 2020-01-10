---
title: 'Nasıl yapılır: SystemFonts Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- system fonts [WPF]
- fonts [WPF], system fonts
- classes [WPF], SystemFonts
ms.assetid: 3f46a4ec-2225-408a-8123-8838a8f7057a
ms.openlocfilehash: 157565ceb9057049aef8b2bf274847d58c6b8dc8
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559969"
---
# <a name="how-to-use-systemfonts"></a><span data-ttu-id="eff1f-102">Nasıl yapılır: SystemFonts Kullanma</span><span class="sxs-lookup"><span data-stu-id="eff1f-102">How to: Use SystemFonts</span></span>
<span data-ttu-id="eff1f-103">Bu örnek, bir düğmeye stil eklemek veya özelleştirmek için <xref:System.Windows.SystemFonts> sınıfının statik kaynaklarının nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="eff1f-103">This example shows how to use the static resources of the <xref:System.Windows.SystemFonts> class in order to style or customize a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eff1f-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="eff1f-104">Example</span></span>  
 <span data-ttu-id="eff1f-105">Sistem kaynakları, sistem ayarlarıyla tutarlı görseller oluşturmanıza yardımcı olmak için, sistem tarafından belirlenen birkaç değeri hem kaynak hem de özellikler olarak kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="eff1f-105">System resources expose several system-determined values as both resources and properties in order to help you create visuals that are consistent with system settings.</span></span> <span data-ttu-id="eff1f-106"><xref:System.Windows.SystemFonts>, hem statik özellikler olarak sistem yazı tipi değerlerini hem de çalışma zamanında dinamik olarak bu değerlere erişmek için kullanılabilecek kaynak anahtarlarına başvuruda bulunan özellikleri içeren bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="eff1f-106"><xref:System.Windows.SystemFonts> is a class that contains both system font values as static properties, and properties that reference resource keys that can be used to access those values dynamically at run time.</span></span> <span data-ttu-id="eff1f-107">Örneğin, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> bir <xref:System.Windows.SystemFonts> değerdir ve <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> karşılık gelen bir kaynak anahtarıdır.</span><span class="sxs-lookup"><span data-stu-id="eff1f-107">For example, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> is a <xref:System.Windows.SystemFonts> value, and <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> is a corresponding resource key.</span></span>  
  
 <span data-ttu-id="eff1f-108">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], <xref:System.Windows.SystemFonts> üyelerini statik özellikler ya da dinamik kaynak başvuruları (anahtar olarak statik özellik değeri ile) olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eff1f-108">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can use the members of <xref:System.Windows.SystemFonts> as either static properties or dynamic resource references (with the static property value as the key).</span></span> <span data-ttu-id="eff1f-109">Yazı tipi ölçüsünün uygulama çalışırken otomatik olarak güncelleştirilmesini istiyorsanız dinamik bir kaynak başvurusu kullanın; Aksi takdirde, statik bir değer başvurusu kullanın.</span><span class="sxs-lookup"><span data-stu-id="eff1f-109">Use a dynamic resource reference if you want the font metric to automatically update while the application runs; otherwise, use a static value reference.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eff1f-110">Kaynak anahtarları, özellik adının sonuna "Key" önekini sahiptir.</span><span class="sxs-lookup"><span data-stu-id="eff1f-110">The resource keys have the suffix "Key" appended to the property name.</span></span>  
  
 <span data-ttu-id="eff1f-111">Aşağıdaki örnek, bir düğmeyi stil eklemek veya özelleştirmek için statik değerler olarak <xref:System.Windows.SystemFonts> özelliklerinin nasıl erişebileceğini ve kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="eff1f-111">The following example shows how to access and use the properties of <xref:System.Windows.SystemFonts> as static values in order to style or customize a button.</span></span> <span data-ttu-id="eff1f-112">Bu biçimlendirme örneği bir düğmeye <xref:System.Windows.SystemFonts> değerleri atar.</span><span class="sxs-lookup"><span data-stu-id="eff1f-112">This markup example assigns <xref:System.Windows.SystemFonts> values to a button.</span></span>  
  
 [!code-xaml[SystemRes_snip#FontStaticResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#fontstaticresources)]  
  
 <span data-ttu-id="eff1f-113">Kodda <xref:System.Windows.SystemFonts> değerlerini kullanmak için statik bir değer veya dinamik kaynak başvurusu kullanmak zorunda değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="eff1f-113">To use the values of <xref:System.Windows.SystemFonts> in code, you do not have to use either a static value or a dynamic resource reference.</span></span> <span data-ttu-id="eff1f-114">Bunun yerine, <xref:System.Windows.SystemFonts> sınıfının anahtar olmayan özelliklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="eff1f-114">Instead, use the non-key properties of the <xref:System.Windows.SystemFonts> class.</span></span> <span data-ttu-id="eff1f-115">Anahtar olmayan özellikler statik özellikler olarak tanımlanmasa da, sistem tarafından barındırılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çalışma zamanı davranışı özellikleri gerçek zamanlı olarak yeniden değerlendirerek, sistem değerlerinde Kullanıcı odaklı değişiklikler için düzgün şekilde hesaba sahip olur.</span><span class="sxs-lookup"><span data-stu-id="eff1f-115">Although the non-key properties are apparently defined as static properties, the run-time behavior of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] as hosted by the system will reevaluate the properties in real time and will properly account for user-driven changes to system values.</span></span> <span data-ttu-id="eff1f-116">Aşağıdaki örnek, bir düğmenin yazı tipi ayarlarının nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="eff1f-116">The following example shows how to specify the font settings of a button.</span></span>  
  
 [!code-csharp[SystemRes_snip#FontResourcesCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#fontresourcescode)]
 [!code-vb[SystemRes_snip#FontResourcesCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#fontresourcescode)]  
  
## <a name="see-also"></a><span data-ttu-id="eff1f-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eff1f-117">See also</span></span>

- <xref:System.Windows.SystemFonts>
- [<span data-ttu-id="eff1f-118">Sistem Fırçası ile bir Alanı Boyama</span><span class="sxs-lookup"><span data-stu-id="eff1f-118">Paint an Area with a System Brush</span></span>](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="eff1f-119">SystemParameters Kullanma</span><span class="sxs-lookup"><span data-stu-id="eff1f-119">Use SystemParameters</span></span>](how-to-use-systemparameters.md)
- [<span data-ttu-id="eff1f-120">Sistem Yazı Tipleri Tuşlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="eff1f-120">Use System Fonts Keys</span></span>](how-to-use-system-fonts-keys.md)
- [<span data-ttu-id="eff1f-121">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="eff1f-121">How-to Topics</span></span>](resources-how-to-topics.md)
- [<span data-ttu-id="eff1f-122">x:Static İşaretleme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="eff1f-122">x:Static Markup Extension</span></span>](../../../desktop-wpf/xaml-services/xstatic-markup-extension.md)
- [<span data-ttu-id="eff1f-123">XAML Kaynakları</span><span class="sxs-lookup"><span data-stu-id="eff1f-123">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="eff1f-124">DynamicResource İşaretleme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="eff1f-124">DynamicResource Markup Extension</span></span>](dynamicresource-markup-extension.md)
