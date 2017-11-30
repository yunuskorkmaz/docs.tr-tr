---
title: "Nasıl yapılır: SystemParameters Kullanma"
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
helpviewer_keywords: classes [WPF], SystemParameters
ms.assetid: 02e7a5de-94eb-4953-b91c-52e6c872ad5b
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f4b2ee3956017e10da8adda52fa9a0ec31cb19ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-systemparameters"></a><span data-ttu-id="49364-102">Nasıl yapılır: SystemParameters Kullanma</span><span class="sxs-lookup"><span data-stu-id="49364-102">How to: Use SystemParameters</span></span>
<span data-ttu-id="49364-103">Bu örnek erişmek ve özelliklerini kullanmak üzere nasıl gösterir <xref:System.Windows.SystemParameters> stil veya bir düğmeyi özelleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="49364-103">This example shows how to access and use the properties of <xref:System.Windows.SystemParameters> in order to style or customize a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49364-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="49364-104">Example</span></span>  
 <span data-ttu-id="49364-105">Kaynaklarınızı görselleri oluşturmanıza yardımcı olması için sistem ayarları ile tutarlı olarak sistem kaynaklarını birkaç sistem tabanlı ayarları kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="49364-105">System resources expose several system based settings as resources in order to help you create visuals that are consistent with system settings.</span></span> <span data-ttu-id="49364-106"><xref:System.Windows.SystemParameters>hem sistem parametre değeri özelliklerini hem de değerlere bağlanan kaynak anahtarları içeren bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="49364-106"><xref:System.Windows.SystemParameters> is a class that contains both system parameter value properties, and resource keys that bind to the values.</span></span> <span data-ttu-id="49364-107">Örneğin, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> olan bir <xref:System.Windows.SystemParameters> özellik değeri ve <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A> karşılık gelen kaynak anahtarı.</span><span class="sxs-lookup"><span data-stu-id="49364-107">For example, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> is a <xref:System.Windows.SystemParameters> property value and <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A> is the corresponding resource key.</span></span>  
  
 <span data-ttu-id="49364-108">İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], üyeleri kullanabilir <xref:System.Windows.SystemParameters> olarak bir statik özellik kullanımı veya dinamik kaynak başvurular (statik özellik değeri ile anahtar olarak).</span><span class="sxs-lookup"><span data-stu-id="49364-108">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can use the members of <xref:System.Windows.SystemParameters> as either a static property usage, or a dynamic resource references (with the static property value as the key).</span></span> <span data-ttu-id="49364-109">Uygulama çalışırken otomatik olarak güncelleştirmek için temel sistem değeri isterseniz, dinamik kaynak başvurusu kullanmak çalışır; Aksi halde, statik başvuru kullanın.</span><span class="sxs-lookup"><span data-stu-id="49364-109">Use a dynamic resource reference if you want the system based value to update automatically while the application runs; otherwise, use a static reference.</span></span> <span data-ttu-id="49364-110">Kaynak anahtarlara sahip soneki `Key` özellik adı eklenir.</span><span class="sxs-lookup"><span data-stu-id="49364-110">Resource keys have the suffix `Key` appended to the property name.</span></span>  
  
 <span data-ttu-id="49364-111">Aşağıdaki örnek statik değerlerini erişmek ve nasıl kullanılacağını gösterir <xref:System.Windows.SystemParameters> stil veya bir düğmeyi özelleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="49364-111">The following example shows how to access and use the static values of <xref:System.Windows.SystemParameters> to style or customize a button.</span></span> <span data-ttu-id="49364-112">Bu biçimlendirme örneği uygulayarak bir düğme boyutları <xref:System.Windows.SystemParameters> değerleri bir düğme.</span><span class="sxs-lookup"><span data-stu-id="49364-112">This markup example sizes a button by applying <xref:System.Windows.SystemParameters> values to a button.</span></span>  
  
 [!code-xaml[SystemRes_snip#ParameterStaticResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#parameterstaticresources)]  
  
 <span data-ttu-id="49364-113">Değerleri kullanmak için <xref:System.Windows.SystemParameters> kodda, statik referans veya dinamik kaynak başvuruları kullanmak gerekmez.</span><span class="sxs-lookup"><span data-stu-id="49364-113">To use the values of <xref:System.Windows.SystemParameters> in code, you do not have to use either static references or dynamic resource references.</span></span> <span data-ttu-id="49364-114">Bunun yerine, değerlerini kullanın <xref:System.Windows.SystemParameters> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="49364-114">Instead, use the values of the <xref:System.Windows.SystemParameters> class.</span></span> <span data-ttu-id="49364-115">Anahtar olmayan özellikler görünüşe göre statik özellikler olarak, çalışma zamanı davranışını tanımlanmasına rağmen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sistem tarafından barındırılan olarak gerçek zamanlı özelliklerinde yeniden ve hesap sistem değerlerine kullanıcı tarafından yapılan değişiklikleri için düzgün biçimde değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="49364-115">Although the non-key properties are apparently defined as static properties, the runtime behavior of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] as hosted by the system will reevaluate the properties in realtime, and will properly account for user-driven changes to system values.</span></span> <span data-ttu-id="49364-116">Aşağıdaki örnekte, genişlik ve yükseklik düğmesinin kullanarak ayarlamak gösterilmiştir <xref:System.Windows.SystemParameters> değerleri.</span><span class="sxs-lookup"><span data-stu-id="49364-116">The following example shows how to set the width and height of a button by using <xref:System.Windows.SystemParameters> values.</span></span>  
  
 [!code-csharp[SystemRes_snip#ParameterResourcesCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#parameterresourcescode)]
 [!code-vb[SystemRes_snip#ParameterResourcesCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#parameterresourcescode)]  
  
## <a name="see-also"></a><span data-ttu-id="49364-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="49364-117">See Also</span></span>  
 <xref:System.Windows.SystemParameters>  
 [<span data-ttu-id="49364-118">Sistem fırçası ile bir alanı boyama</span><span class="sxs-lookup"><span data-stu-id="49364-118">Paint an Area with a System Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [<span data-ttu-id="49364-119">SystemFonts kullanma</span><span class="sxs-lookup"><span data-stu-id="49364-119">Use SystemFonts</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)  
 [<span data-ttu-id="49364-120">Sistem parametreleri tuşlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="49364-120">Use System Parameters Keys</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-system-parameters-keys.md)  
 [<span data-ttu-id="49364-121">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="49364-121">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)
