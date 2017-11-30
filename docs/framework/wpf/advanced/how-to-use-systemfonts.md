---
title: "Nasıl yapılır: SystemFonts Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- system fonts [WPF]
- fonts [WPF], system fonts
- classes [WPF], SystemFonts
ms.assetid: 3f46a4ec-2225-408a-8123-8838a8f7057a
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8ce82724a4e9a547b8441628f43621f29eab6307
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-systemfonts"></a><span data-ttu-id="24f6a-102">Nasıl yapılır: SystemFonts Kullanma</span><span class="sxs-lookup"><span data-stu-id="24f6a-102">How to: Use SystemFonts</span></span>
<span data-ttu-id="24f6a-103">Bu örnek, statik kaynaklarının nasıl kullanılacağını gösterir <xref:System.Windows.SystemFonts> stil ya da bir düğmeyi özelleştirmek amacıyla sınıfı.</span><span class="sxs-lookup"><span data-stu-id="24f6a-103">This example shows how to use the static resources of the <xref:System.Windows.SystemFonts> class in order to style or customize a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24f6a-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="24f6a-104">Example</span></span>  
 <span data-ttu-id="24f6a-105">Sistem kaynakları sistem ayarları ile tutarlı görselleri oluşturmanıza yardımcı olması için birkaç sistem tarafından belirlenen değerleri hem kaynak hem de özellikleri olarak kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="24f6a-105">System resources expose several system-determined values as both resources and properties in order to help you create visuals that are consistent with system settings.</span></span> <span data-ttu-id="24f6a-106"><xref:System.Windows.SystemFonts>statik özellikler ve bu değerleri çalışma zamanında dinamik olarak erişmek için kullanılan kaynak anahtarlara başvuran özellikleri olarak her iki sistem yazı tipi değerlerini içeren bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="24f6a-106"><xref:System.Windows.SystemFonts> is a class that contains both system font values as static properties, and properties that reference resource keys that can be used to access those values dynamically at run time.</span></span> <span data-ttu-id="24f6a-107">Örneğin, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> olan bir <xref:System.Windows.SystemFonts> değeri ve <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> karşılık gelen bir kaynak anahtardır.</span><span class="sxs-lookup"><span data-stu-id="24f6a-107">For example, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> is a <xref:System.Windows.SystemFonts> value, and <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> is a corresponding resource key.</span></span>  
  
 <span data-ttu-id="24f6a-108">İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], üyeleri kullanabilir <xref:System.Windows.SystemFonts> olarak statik özellik veya dinamik kaynak başvurular (statik özellik değeri ile anahtar olarak).</span><span class="sxs-lookup"><span data-stu-id="24f6a-108">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can use the members of <xref:System.Windows.SystemFonts> as either static properties or dynamic resource references (with the static property value as the key).</span></span> <span data-ttu-id="24f6a-109">Uygulama çalışırken otomatik olarak güncelleştirmek için yazı tipi ölçüsünün isterseniz, dinamik kaynak başvurusu kullanmak çalışır; Aksi takdirde statik referans kullanın.</span><span class="sxs-lookup"><span data-stu-id="24f6a-109">Use a dynamic resource reference if you want the font metric to automatically update while the application runs; otherwise, use a static value reference.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24f6a-110">Kaynak anahtarlarının eklenen özellik adı "Tuş" son ekine sahip.</span><span class="sxs-lookup"><span data-stu-id="24f6a-110">The resource keys have the suffix "Key" appended to the property name.</span></span>  
  
 <span data-ttu-id="24f6a-111">Aşağıdaki örnek erişmek ve özelliklerini kullanmak üzere nasıl gösterir <xref:System.Windows.SystemFonts> stil veya bir düğmeyi özelleştirmek için statik değerler olarak.</span><span class="sxs-lookup"><span data-stu-id="24f6a-111">The following example shows how to access and use the properties of <xref:System.Windows.SystemFonts> as static values in order to style or customize a button.</span></span> <span data-ttu-id="24f6a-112">Bu biçimlendirme örneği atar <xref:System.Windows.SystemFonts> değerleri bir düğme.</span><span class="sxs-lookup"><span data-stu-id="24f6a-112">This markup example assigns <xref:System.Windows.SystemFonts> values to a button.</span></span>  
  
 [!code-xaml[SystemRes_snip#FontStaticResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#fontstaticresources)]  
  
 <span data-ttu-id="24f6a-113">Değerleri kullanmak için <xref:System.Windows.SystemFonts> kod içinde statik bir değer veya dinamik kaynak başvurusu kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="24f6a-113">To use the values of <xref:System.Windows.SystemFonts> in code, you do not have to use either a static value or a dynamic resource reference.</span></span> <span data-ttu-id="24f6a-114">Bunun yerine, anahtar olmayan özelliklerini kullanın <xref:System.Windows.SystemFonts> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="24f6a-114">Instead, use the non-key properties of the <xref:System.Windows.SystemFonts> class.</span></span> <span data-ttu-id="24f6a-115">Anahtar olmayan özellikler görünüşe göre statik özellikler olarak, çalışma zamanı davranışını tanımlanmasına rağmen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tarafından barındırılan olarak sistem gerçek zamanlı özelliklerinde yeniden ve düzgün şekilde sistem değerlerine kullanıcı tarafından yapılan değişiklikleri hesaba katmayacak.</span><span class="sxs-lookup"><span data-stu-id="24f6a-115">Although the non-key properties are apparently defined as static properties, the run-time behavior of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] as hosted by the system will reevaluate the properties in real time and will properly account for user-driven changes to system values.</span></span> <span data-ttu-id="24f6a-116">Aşağıdaki örnek, bir düğme yazı tipi ayarlarını belirtmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="24f6a-116">The following example shows how to specify the font settings of a button.</span></span>  
  
 [!code-csharp[SystemRes_snip#FontResourcesCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#fontresourcescode)]
 [!code-vb[SystemRes_snip#FontResourcesCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#fontresourcescode)]  
  
## <a name="see-also"></a><span data-ttu-id="24f6a-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="24f6a-117">See Also</span></span>  
 <xref:System.Windows.SystemFonts>  
 [<span data-ttu-id="24f6a-118">Sistem fırçası ile bir alanı boyama</span><span class="sxs-lookup"><span data-stu-id="24f6a-118">Paint an Area with a System Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [<span data-ttu-id="24f6a-119">SystemParameters kullanımı</span><span class="sxs-lookup"><span data-stu-id="24f6a-119">Use SystemParameters</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)  
 [<span data-ttu-id="24f6a-120">Sistem yazı tiplerini tuşlarını kullanın</span><span class="sxs-lookup"><span data-stu-id="24f6a-120">Use System Fonts Keys</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-system-fonts-keys.md)  
 [<span data-ttu-id="24f6a-121">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="24f6a-121">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)  
 [<span data-ttu-id="24f6a-122">x: Static işaretleme uzantısı</span><span class="sxs-lookup"><span data-stu-id="24f6a-122">x:Static Markup Extension</span></span>](../../../../docs/framework/xaml-services/x-static-markup-extension.md)  
 [<span data-ttu-id="24f6a-123">XAML kaynakları</span><span class="sxs-lookup"><span data-stu-id="24f6a-123">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="24f6a-124">DynamicResource Biçimlendirme uzantısı</span><span class="sxs-lookup"><span data-stu-id="24f6a-124">DynamicResource Markup Extension</span></span>](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)
