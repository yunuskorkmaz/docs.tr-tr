---
title: 'Nasıl yapılır: Sistem Parametreleri Tuşlarını Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemParameters class
- classes [WPF], SystemParameters
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
ms.openlocfilehash: 147f65b4bb214c12317309081c345251d7426cd6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59147341"
---
# <a name="how-to-use-system-parameters-keys"></a><span data-ttu-id="b102a-102">Nasıl yapılır: Sistem Parametreleri Tuşlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="b102a-102">How to: Use System Parameters Keys</span></span>
<span data-ttu-id="b102a-103">Sistem ayarları ile tutarlı, görsel oluşturmak geliştiriciler yardımcı olacak kaynaklar olarak sistem kaynaklarının sistem ölçümlerini sayısını kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="b102a-103">System resources expose a number of system metrics as resources to help developers create visuals that are consistent with system settings.</span></span> <xref:System.Windows.SystemParameters> <span data-ttu-id="b102a-104">sistem parametre değerleri hem değerlere bağlanan kaynak anahtarlarını içeren bir sınıf — Örneğin, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> ve <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="b102a-104">is a class that contains both system parameter values and resource keys that bind to the values—for example, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> and <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>.</span></span> <span data-ttu-id="b102a-105">Sistem parametresi ölçümlerini statik veya dinamik kaynakları olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b102a-105">System parameter metrics can be used as either static or dynamic resources.</span></span> <span data-ttu-id="b102a-106">Parametre ölçüsünün uygulama çalışırken otomatik olarak güncelleştirmek istiyorsanız, bir dinamik kaynak kullanmak çalışır; Aksi takdirde bir statik kaynak kullanın.</span><span class="sxs-lookup"><span data-stu-id="b102a-106">Use a dynamic resource if you want the parameter metric to update automatically while the application runs; otherwise use a static resource.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b102a-107">Dinamik kaynaklara sahip anahtar sözcüğü *anahtar* özellik adına eklenir.</span><span class="sxs-lookup"><span data-stu-id="b102a-107">Dynamic resources have the keyword *Key* appended to the property name.</span></span>  
  
 <span data-ttu-id="b102a-108">Aşağıdaki örnek, bir düğmeye stil veya sistem parametresi dinamik kaynaklarına erişmek ve gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b102a-108">The following example shows how to access and use system parameter dynamic resources to style or customize a button.</span></span> <span data-ttu-id="b102a-109">Bu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] örnek boyutları bir düğme atayarak <xref:System.Windows.SystemParameters> düğmenin genişlik ve yükseklik değerleri.</span><span class="sxs-lookup"><span data-stu-id="b102a-109">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example sizes a button by assigning <xref:System.Windows.SystemParameters> values to the button's width and height.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b102a-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="b102a-110">Example</span></span>  
 [!code-xaml[SystemRes_snip#ParameterDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## <a name="see-also"></a><span data-ttu-id="b102a-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b102a-111">See also</span></span>

- [<span data-ttu-id="b102a-112">Sistem Fırçası ile bir Alanı Boyama</span><span class="sxs-lookup"><span data-stu-id="b102a-112">Paint an Area with a System Brush</span></span>](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="b102a-113">SystemFonts Kullanma</span><span class="sxs-lookup"><span data-stu-id="b102a-113">Use SystemFonts</span></span>](how-to-use-systemfonts.md)
- [<span data-ttu-id="b102a-114">SystemParameters Kullanma</span><span class="sxs-lookup"><span data-stu-id="b102a-114">Use SystemParameters</span></span>](how-to-use-systemparameters.md)
