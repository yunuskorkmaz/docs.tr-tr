---
title: 'Nasıl yapılır: Sistem Parametreleri Tuşlarını Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemParameters class
- classes [WPF], SystemParameters
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
ms.openlocfilehash: edacb4b98ab01f081f668dc3374f6588492210d9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918378"
---
# <a name="how-to-use-system-parameters-keys"></a><span data-ttu-id="7be42-102">Nasıl yapılır: Sistem Parametreleri Tuşlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="7be42-102">How to: Use System Parameters Keys</span></span>
<span data-ttu-id="7be42-103">Sistem kaynakları, geliştiricilerin sistem ayarlarıyla tutarlı görseller oluşturmalarına yardımcı olmak için çeşitli sistem ölçümlerini kaynak olarak kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="7be42-103">System resources expose a number of system metrics as resources to help developers create visuals that are consistent with system settings.</span></span> <span data-ttu-id="7be42-104"><xref:System.Windows.SystemParameters>, hem sistem parametre değerlerini hem de değerlere bağlanan kaynak anahtarlarını içeren bir sınıftır — Örneğin, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> ve. <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A></span><span class="sxs-lookup"><span data-stu-id="7be42-104"><xref:System.Windows.SystemParameters> is a class that contains both system parameter values and resource keys that bind to the values—for example, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> and <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>.</span></span> <span data-ttu-id="7be42-105">Sistem parametresi ölçümleri, statik veya dinamik kaynaklar olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7be42-105">System parameter metrics can be used as either static or dynamic resources.</span></span> <span data-ttu-id="7be42-106">Parametre ölçüsünün uygulama çalışırken otomatik olarak güncelleştirilmesini istiyorsanız dinamik bir kaynak kullanın; Aksi halde statik kaynak kullanın.</span><span class="sxs-lookup"><span data-stu-id="7be42-106">Use a dynamic resource if you want the parameter metric to update automatically while the application runs; otherwise use a static resource.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7be42-107">Dinamik kaynaklarda, özellik adının sonuna anahtar sözcük *anahtarı* eklenir.</span><span class="sxs-lookup"><span data-stu-id="7be42-107">Dynamic resources have the keyword *Key* appended to the property name.</span></span>  
  
 <span data-ttu-id="7be42-108">Aşağıdaki örnek, bir düğmeye stil eklemek veya özelleştirmek için, sistem parametresi dinamik kaynaklarının nasıl erişebileceğini ve kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7be42-108">The following example shows how to access and use system parameter dynamic resources to style or customize a button.</span></span> <span data-ttu-id="7be42-109">Bu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] örnek, düğmenin genişliğine ve yüksekliğine <xref:System.Windows.SystemParameters> değerler atayarak bir düğmeyi boyutlandırır.</span><span class="sxs-lookup"><span data-stu-id="7be42-109">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example sizes a button by assigning <xref:System.Windows.SystemParameters> values to the button's width and height.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7be42-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="7be42-110">Example</span></span>  
 [!code-xaml[SystemRes_snip#ParameterDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## <a name="see-also"></a><span data-ttu-id="7be42-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7be42-111">See also</span></span>

- [<span data-ttu-id="7be42-112">Sistem Fırçası ile bir Alanı Boyama</span><span class="sxs-lookup"><span data-stu-id="7be42-112">Paint an Area with a System Brush</span></span>](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="7be42-113">SystemFonts Kullanma</span><span class="sxs-lookup"><span data-stu-id="7be42-113">Use SystemFonts</span></span>](how-to-use-systemfonts.md)
- [<span data-ttu-id="7be42-114">SystemParameters Kullanma</span><span class="sxs-lookup"><span data-stu-id="7be42-114">Use SystemParameters</span></span>](how-to-use-systemparameters.md)
