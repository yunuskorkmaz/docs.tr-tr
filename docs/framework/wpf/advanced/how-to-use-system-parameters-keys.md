---
title: "Nasıl yapılır: Sistem Parametreleri Tuşlarını Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resource keys [WPF], SystemParameters class
- classes [WPF], SystemParameters
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2b5f45f386c58b0577a2716c6fe1396f4c44f4ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-system-parameters-keys"></a><span data-ttu-id="a5833-102">Nasıl yapılır: Sistem Parametreleri Tuşlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="a5833-102">How to: Use System Parameters Keys</span></span>
<span data-ttu-id="a5833-103">Sistem kaynakları, geliştiriciler Sistem ayarları ile tutarlı görselleri oluşturmanıza yardımcı olacak kaynaklar olarak sistem ölçümleri sayısını kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="a5833-103">System resources expose a number of system metrics as resources to help developers create visuals that are consistent with system settings.</span></span> <span data-ttu-id="a5833-104"><xref:System.Windows.SystemParameters>sistem parametre değerlerini ve değerlere bağlanan kaynak anahtarları içeren bir sınıf — Örneğin, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> ve <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="a5833-104"><xref:System.Windows.SystemParameters> is a class that contains both system parameter values and resource keys that bind to the values—for example, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> and <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>.</span></span> <span data-ttu-id="a5833-105">Sistem parametre ölçüleri statik veya dinamik kaynaklar olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a5833-105">System parameter metrics can be used as either static or dynamic resources.</span></span> <span data-ttu-id="a5833-106">Uygulama çalışırken otomatik olarak güncelleştirmek için parametre ölçüsünün istiyorsanız, dinamik kaynak kullanın çalışır; Aksi halde statik kaynak kullanın.</span><span class="sxs-lookup"><span data-stu-id="a5833-106">Use a dynamic resource if you want the parameter metric to update automatically while the application runs; otherwise use a static resource.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5833-107">Dinamik kaynaklarınız anahtar sözcüğü *anahtar* özellik adı eklenir.</span><span class="sxs-lookup"><span data-stu-id="a5833-107">Dynamic resources have the keyword *Key* appended to the property name.</span></span>  
  
 <span data-ttu-id="a5833-108">Aşağıdaki örnek, erişim ve stil veya bir düğmeyi özelleştirmek için sistem parametre dinamik kaynaklarının nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a5833-108">The following example shows how to access and use system parameter dynamic resources to style or customize a button.</span></span> <span data-ttu-id="a5833-109">Bu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] örnek atayarak düğmeyi boyutlandırır <xref:System.Windows.SystemParameters> düğmenin genişlik ve yükseklik değerleri.</span><span class="sxs-lookup"><span data-stu-id="a5833-109">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example sizes a button by assigning <xref:System.Windows.SystemParameters> values to the button's width and height.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5833-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="a5833-110">Example</span></span>  
 [!code-xaml[SystemRes_snip#ParameterDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## <a name="see-also"></a><span data-ttu-id="a5833-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a5833-111">See Also</span></span>  
 [<span data-ttu-id="a5833-112">Sistem fırçası ile bir alanı boyama</span><span class="sxs-lookup"><span data-stu-id="a5833-112">Paint an Area with a System Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [<span data-ttu-id="a5833-113">SystemFonts kullanma</span><span class="sxs-lookup"><span data-stu-id="a5833-113">Use SystemFonts</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)  
 [<span data-ttu-id="a5833-114">SystemParameters kullanımı</span><span class="sxs-lookup"><span data-stu-id="a5833-114">Use SystemParameters</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)
