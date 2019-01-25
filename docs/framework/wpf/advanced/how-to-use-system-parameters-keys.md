---
title: 'Nasıl yapılır: Sistem Parametreleri Tuşlarını Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemParameters class
- classes [WPF], SystemParameters
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
ms.openlocfilehash: 13658b0bb97d842eecc8679ee64db68ae780a917
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54728370"
---
# <a name="how-to-use-system-parameters-keys"></a><span data-ttu-id="8bd2e-102">Nasıl yapılır: Sistem Parametreleri Tuşlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="8bd2e-102">How to: Use System Parameters Keys</span></span>
<span data-ttu-id="8bd2e-103">Sistem ayarları ile tutarlı, görsel oluşturmak geliştiriciler yardımcı olacak kaynaklar olarak sistem kaynaklarının sistem ölçümlerini sayısını kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="8bd2e-103">System resources expose a number of system metrics as resources to help developers create visuals that are consistent with system settings.</span></span> <span data-ttu-id="8bd2e-104"><xref:System.Windows.SystemParameters> sistem parametre değerleri hem değerlere bağlanan kaynak anahtarlarını içeren bir sınıf — Örneğin, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> ve <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="8bd2e-104"><xref:System.Windows.SystemParameters> is a class that contains both system parameter values and resource keys that bind to the values—for example, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> and <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>.</span></span> <span data-ttu-id="8bd2e-105">Sistem parametresi ölçümlerini statik veya dinamik kaynakları olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8bd2e-105">System parameter metrics can be used as either static or dynamic resources.</span></span> <span data-ttu-id="8bd2e-106">Parametre ölçüsünün uygulama çalışırken otomatik olarak güncelleştirmek istiyorsanız, bir dinamik kaynak kullanmak çalışır; Aksi takdirde bir statik kaynak kullanın.</span><span class="sxs-lookup"><span data-stu-id="8bd2e-106">Use a dynamic resource if you want the parameter metric to update automatically while the application runs; otherwise use a static resource.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8bd2e-107">Dinamik kaynaklara sahip anahtar sözcüğü *anahtar* özellik adına eklenir.</span><span class="sxs-lookup"><span data-stu-id="8bd2e-107">Dynamic resources have the keyword *Key* appended to the property name.</span></span>  
  
 <span data-ttu-id="8bd2e-108">Aşağıdaki örnek, bir düğmeye stil veya sistem parametresi dinamik kaynaklarına erişmek ve gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8bd2e-108">The following example shows how to access and use system parameter dynamic resources to style or customize a button.</span></span> <span data-ttu-id="8bd2e-109">Bu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] örnek boyutları bir düğme atayarak <xref:System.Windows.SystemParameters> düğmenin genişlik ve yükseklik değerleri.</span><span class="sxs-lookup"><span data-stu-id="8bd2e-109">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example sizes a button by assigning <xref:System.Windows.SystemParameters> values to the button's width and height.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8bd2e-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="8bd2e-110">Example</span></span>  
 [!code-xaml[SystemRes_snip#ParameterDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## <a name="see-also"></a><span data-ttu-id="8bd2e-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8bd2e-111">See also</span></span>
- [<span data-ttu-id="8bd2e-112">Sistem Fırçası ile bir Alanı Boyama</span><span class="sxs-lookup"><span data-stu-id="8bd2e-112">Paint an Area with a System Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="8bd2e-113">SystemFonts Kullanma</span><span class="sxs-lookup"><span data-stu-id="8bd2e-113">Use SystemFonts</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)
- [<span data-ttu-id="8bd2e-114">SystemParameters Kullanma</span><span class="sxs-lookup"><span data-stu-id="8bd2e-114">Use SystemParameters</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)
