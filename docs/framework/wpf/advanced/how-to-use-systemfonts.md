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
ms.openlocfilehash: 5976bc0cb8b34e68d5e89dd70a608d7e52ded332
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59216788"
---
# <a name="how-to-use-systemfonts"></a><span data-ttu-id="69574-102">Nasıl yapılır: SystemFonts Kullanma</span><span class="sxs-lookup"><span data-stu-id="69574-102">How to: Use SystemFonts</span></span>
<span data-ttu-id="69574-103">Bu örnek, statik kaynakları kullanmayı gösterir. <xref:System.Windows.SystemFonts> stil veya bir düğmeyi özelleştirmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="69574-103">This example shows how to use the static resources of the <xref:System.Windows.SystemFonts> class in order to style or customize a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69574-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="69574-104">Example</span></span>  
 <span data-ttu-id="69574-105">Sistem kaynakları sistem ayarları ile tutarlı, görsel oluşturmanıza yardımcı olmak için birkaç sistem tarafından belirlenen değeri hem kaynak hem de özellikleri olarak kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="69574-105">System resources expose several system-determined values as both resources and properties in order to help you create visuals that are consistent with system settings.</span></span> <xref:System.Windows.SystemFonts> <span data-ttu-id="69574-106">statik özellikler ve bu değerleri çalışma zamanında dinamik olarak erişmek için kullanılan kaynak anahtarlarını başvuran özellikleri olarak her iki sistem yazı tipi değerlerini içeren bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="69574-106">is a class that contains both system font values as static properties, and properties that reference resource keys that can be used to access those values dynamically at run time.</span></span> <span data-ttu-id="69574-107">Örneğin, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> olduğu bir <xref:System.Windows.SystemFonts> değeri ve <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> karşılık gelen bir kaynak anahtarı.</span><span class="sxs-lookup"><span data-stu-id="69574-107">For example, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> is a <xref:System.Windows.SystemFonts> value, and <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> is a corresponding resource key.</span></span>  
  
 <span data-ttu-id="69574-108">İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], üyelerinin kullanabileceği <xref:System.Windows.SystemFonts> statik özellikler veya dinamik kaynak başvuruları (statik özellik değeriyle anahtar olarak).</span><span class="sxs-lookup"><span data-stu-id="69574-108">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can use the members of <xref:System.Windows.SystemFonts> as either static properties or dynamic resource references (with the static property value as the key).</span></span> <span data-ttu-id="69574-109">Yazı tipi ölçüsünün uygulama çalışırken otomatik olarak güncelleştirmek istiyorsanız, bir dinamik kaynak başvurusu kullanmak çalışır; Aksi takdirde, statik bir referans kullanın.</span><span class="sxs-lookup"><span data-stu-id="69574-109">Use a dynamic resource reference if you want the font metric to automatically update while the application runs; otherwise, use a static value reference.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69574-110">Kaynak anahtarları için özellik adı "Anahtarını" eklenen son ekine sahip.</span><span class="sxs-lookup"><span data-stu-id="69574-110">The resource keys have the suffix "Key" appended to the property name.</span></span>  
  
 <span data-ttu-id="69574-111">Aşağıdaki örnek, erişme ve özelliklerini kullanma işlemi gösterilmektedir <xref:System.Windows.SystemFonts> stil veya bir düğmeyi özelleştirmek için statik bir değer olarak.</span><span class="sxs-lookup"><span data-stu-id="69574-111">The following example shows how to access and use the properties of <xref:System.Windows.SystemFonts> as static values in order to style or customize a button.</span></span> <span data-ttu-id="69574-112">Bu işaretleme örnek atar <xref:System.Windows.SystemFonts> değerleri.</span><span class="sxs-lookup"><span data-stu-id="69574-112">This markup example assigns <xref:System.Windows.SystemFonts> values to a button.</span></span>  
  
 [!code-xaml[SystemRes_snip#FontStaticResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#fontstaticresources)]  
  
 <span data-ttu-id="69574-113">Değerlerini kullanılacak <xref:System.Windows.SystemFonts> kod içinde statik bir değer veya bir dinamik kaynak başvurusu kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="69574-113">To use the values of <xref:System.Windows.SystemFonts> in code, you do not have to use either a static value or a dynamic resource reference.</span></span> <span data-ttu-id="69574-114">Bunun yerine, anahtar olmayan özelliklerini kullanma <xref:System.Windows.SystemFonts> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="69574-114">Instead, use the non-key properties of the <xref:System.Windows.SystemFonts> class.</span></span> <span data-ttu-id="69574-115">Anahtar olmayan özellikler statik özellik olarak, çalışma zamanı davranışını görünüşe göre tanımlanmasına rağmen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sistem tarafından barındırılan olarak gerçek zamanlı özelliklerinde yeniden değerlendirir ve düzgün şekilde sistem değerleri kullanıcı tarafından yapılan değişiklikleri hesaba katmayacak.</span><span class="sxs-lookup"><span data-stu-id="69574-115">Although the non-key properties are apparently defined as static properties, the run-time behavior of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] as hosted by the system will reevaluate the properties in real time and will properly account for user-driven changes to system values.</span></span> <span data-ttu-id="69574-116">Aşağıdaki örnek, bir düğme yazı tipi ayarlarını belirtmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="69574-116">The following example shows how to specify the font settings of a button.</span></span>  
  
 [!code-csharp[SystemRes_snip#FontResourcesCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#fontresourcescode)]
 [!code-vb[SystemRes_snip#FontResourcesCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#fontresourcescode)]  
  
## <a name="see-also"></a><span data-ttu-id="69574-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69574-117">See also</span></span>

- <xref:System.Windows.SystemFonts>
- [<span data-ttu-id="69574-118">Sistem Fırçası ile bir Alanı Boyama</span><span class="sxs-lookup"><span data-stu-id="69574-118">Paint an Area with a System Brush</span></span>](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="69574-119">SystemParameters Kullanma</span><span class="sxs-lookup"><span data-stu-id="69574-119">Use SystemParameters</span></span>](how-to-use-systemparameters.md)
- [<span data-ttu-id="69574-120">Sistem Yazı Tipleri Tuşlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="69574-120">Use System Fonts Keys</span></span>](how-to-use-system-fonts-keys.md)
- [<span data-ttu-id="69574-121">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="69574-121">How-to Topics</span></span>](resources-how-to-topics.md)
- [<span data-ttu-id="69574-122">x:Static İşaretleme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="69574-122">x:Static Markup Extension</span></span>](../../xaml-services/x-static-markup-extension.md)
- [<span data-ttu-id="69574-123">XAML Kaynakları</span><span class="sxs-lookup"><span data-stu-id="69574-123">XAML Resources</span></span>](xaml-resources.md)
- [<span data-ttu-id="69574-124">DynamicResource Biçimlendirme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="69574-124">DynamicResource Markup Extension</span></span>](dynamicresource-markup-extension.md)
