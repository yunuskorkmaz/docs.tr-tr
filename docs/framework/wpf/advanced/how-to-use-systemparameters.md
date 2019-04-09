---
title: 'Nasıl yapılır: SystemParameters Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes [WPF], SystemParameters
ms.assetid: 02e7a5de-94eb-4953-b91c-52e6c872ad5b
ms.openlocfilehash: 344fb54b48bcbf188b36a29d8205c21deff713c4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59199862"
---
# <a name="how-to-use-systemparameters"></a><span data-ttu-id="aec3e-102">Nasıl yapılır: SystemParameters Kullanma</span><span class="sxs-lookup"><span data-stu-id="aec3e-102">How to: Use SystemParameters</span></span>
<span data-ttu-id="aec3e-103">Bu örnek, erişme ve özelliklerini kullanma işlemi gösterilmektedir <xref:System.Windows.SystemParameters> stil veya bir düğmeyi özelleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="aec3e-103">This example shows how to access and use the properties of <xref:System.Windows.SystemParameters> in order to style or customize a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aec3e-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="aec3e-104">Example</span></span>  
 <span data-ttu-id="aec3e-105">Kaynaklarınızı oluştumanıza Yardım için sistem ayarları ile tutarlı olarak sistem kaynaklarının birkaç temel sistem ayarları kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="aec3e-105">System resources expose several system based settings as resources in order to help you create visuals that are consistent with system settings.</span></span> <xref:System.Windows.SystemParameters> <span data-ttu-id="aec3e-106">hem sistem parametre değeri özelliklerini ve değerlere bağlanan kaynak anahtarlarını içeren bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="aec3e-106">is a class that contains both system parameter value properties, and resource keys that bind to the values.</span></span> <span data-ttu-id="aec3e-107">Örneğin, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> olduğu bir <xref:System.Windows.SystemParameters> özellik değeri ve <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A> karşılık gelen kaynak anahtarı.</span><span class="sxs-lookup"><span data-stu-id="aec3e-107">For example, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> is a <xref:System.Windows.SystemParameters> property value and <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A> is the corresponding resource key.</span></span>  
  
 <span data-ttu-id="aec3e-108">İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], üyelerinin kullanabileceği <xref:System.Windows.SystemParameters> statik özellik kullanımı veya bir dinamik kaynak başvuruları (statik özellik değeriyle anahtar olarak).</span><span class="sxs-lookup"><span data-stu-id="aec3e-108">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can use the members of <xref:System.Windows.SystemParameters> as either a static property usage, or a dynamic resource references (with the static property value as the key).</span></span> <span data-ttu-id="aec3e-109">Uygulama çalışırken otomatik olarak güncelleştirmek için temel sistem değeri istiyorsanız bir dinamik kaynak başvurusu kullanmak çalışır; Aksi takdirde, statik başvuru kullanın.</span><span class="sxs-lookup"><span data-stu-id="aec3e-109">Use a dynamic resource reference if you want the system based value to update automatically while the application runs; otherwise, use a static reference.</span></span> <span data-ttu-id="aec3e-110">Kaynak anahtarlara sahip soneki `Key` özellik adına eklenir.</span><span class="sxs-lookup"><span data-stu-id="aec3e-110">Resource keys have the suffix `Key` appended to the property name.</span></span>  
  
 <span data-ttu-id="aec3e-111">Aşağıdaki örnekte, erişme ve statik değerlerini kullanma işlemi gösterilmektedir <xref:System.Windows.SystemParameters> stil veya bir düğme özelleştirme.</span><span class="sxs-lookup"><span data-stu-id="aec3e-111">The following example shows how to access and use the static values of <xref:System.Windows.SystemParameters> to style or customize a button.</span></span> <span data-ttu-id="aec3e-112">Bu biçimlendirme örneği uygulayarak bir düğme boyutları <xref:System.Windows.SystemParameters> değerleri.</span><span class="sxs-lookup"><span data-stu-id="aec3e-112">This markup example sizes a button by applying <xref:System.Windows.SystemParameters> values to a button.</span></span>  
  
 [!code-xaml[SystemRes_snip#ParameterStaticResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#parameterstaticresources)]  
  
 <span data-ttu-id="aec3e-113">Değerlerini kullanılacak <xref:System.Windows.SystemParameters> kod içinde statik başvuruları veya dinamik kaynak başvurularını kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="aec3e-113">To use the values of <xref:System.Windows.SystemParameters> in code, you do not have to use either static references or dynamic resource references.</span></span> <span data-ttu-id="aec3e-114">Bunun yerine, değerlerini kullanmak <xref:System.Windows.SystemParameters> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="aec3e-114">Instead, use the values of the <xref:System.Windows.SystemParameters> class.</span></span> <span data-ttu-id="aec3e-115">Anahtar olmayan özellikler statik özellik olarak, çalışma zamanı davranışını görünüşe göre tanımlanmasına rağmen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sistem tarafından barındırılan olarak özellikleri yeniden değerlendir ve hesap için kullanıcı tarafından yapılan değişiklikleri sistem değerleri için düzgün biçimde değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="aec3e-115">Although the non-key properties are apparently defined as static properties, the runtime behavior of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] as hosted by the system will reevaluate the properties in realtime, and will properly account for user-driven changes to system values.</span></span> <span data-ttu-id="aec3e-116">Aşağıdaki örnekte, genişlik ve yükseklik bir düğmeyi kullanarak ayarlamak gösterilmektedir <xref:System.Windows.SystemParameters> değerleri.</span><span class="sxs-lookup"><span data-stu-id="aec3e-116">The following example shows how to set the width and height of a button by using <xref:System.Windows.SystemParameters> values.</span></span>  
  
 [!code-csharp[SystemRes_snip#ParameterResourcesCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#parameterresourcescode)]
 [!code-vb[SystemRes_snip#ParameterResourcesCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#parameterresourcescode)]  
  
## <a name="see-also"></a><span data-ttu-id="aec3e-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aec3e-117">See also</span></span>

- <xref:System.Windows.SystemParameters>
- [<span data-ttu-id="aec3e-118">Sistem Fırçası ile bir Alanı Boyama</span><span class="sxs-lookup"><span data-stu-id="aec3e-118">Paint an Area with a System Brush</span></span>](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="aec3e-119">SystemFonts Kullanma</span><span class="sxs-lookup"><span data-stu-id="aec3e-119">Use SystemFonts</span></span>](how-to-use-systemfonts.md)
- [<span data-ttu-id="aec3e-120">Sistem Parametreleri Tuşlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="aec3e-120">Use System Parameters Keys</span></span>](how-to-use-system-parameters-keys.md)
- [<span data-ttu-id="aec3e-121">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="aec3e-121">How-to Topics</span></span>](resources-how-to-topics.md)
