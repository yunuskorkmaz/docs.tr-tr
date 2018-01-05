---
title: "Azaltma: WPF Düzeni"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1dcbe970281f3d9cf3b8ffe9adb543afc120ae6b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="mitigation-wpf-layout"></a><span data-ttu-id="e86e1-102">Azaltma: WPF Düzeni</span><span class="sxs-lookup"><span data-stu-id="e86e1-102">Mitigation: WPF Layout</span></span>
<span data-ttu-id="e86e1-103">WPF denetimleri düzenini biraz değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e86e1-103">The layout of WPF controls can change slightly.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="e86e1-104">Etki</span><span class="sxs-lookup"><span data-stu-id="e86e1-104">Impact</span></span>  
 <span data-ttu-id="e86e1-105">Bu değişikliğin sonucu olarak:</span><span class="sxs-lookup"><span data-stu-id="e86e1-105">As a result of this change:</span></span>  
  
-   <span data-ttu-id="e86e1-106">Genişlik veya yüksekliğinden öğelerinin büyütür veya en çok bir piksel küçültür.</span><span class="sxs-lookup"><span data-stu-id="e86e1-106">The width or height of elements may grow or shrink by at most one pixel.</span></span>  
  
-   <span data-ttu-id="e86e1-107">Bir nesne yerleşimini en çok bir piksel taşıyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e86e1-107">The placement of an object can move by at most one pixel.</span></span>  
  
-   <span data-ttu-id="e86e1-108">Ortalanmış öğeleri dikey veya yatay olarak merkezi en çok bir piksel tarafından devre dışı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e86e1-108">Centered elements can be vertically or horizontally off center by at most one pixel.</span></span>  
  
 <span data-ttu-id="e86e1-109">Varsayılan olarak, bu yeni düzen .NET Framework 4.6 hedefleyen uygulamalar için etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e86e1-109">By default, this new layout is enabled only for apps that target the .NET Framework 4.6.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="e86e1-110">Azaltma</span><span class="sxs-lookup"><span data-stu-id="e86e1-110">Mitigation</span></span>  
 <span data-ttu-id="e86e1-111">Kırpma sağa ya da yüksek DPIs WPF denetimleri alt ortadan kaldırmak için bu değişiklik eğilimlidir olduğundan, .NET Framework'ün önceki sürümlerini hedefleyen ama .NET Framework 4.6 üzerinde çalışan uygulamalar bu yeni davranış aşağıdaki satırı ekleyerek seçebilirsiniz `<runtime>` app.config dosyasının:</span><span class="sxs-lookup"><span data-stu-id="e86e1-111">Since this modification tends to eliminate clipping of the right or bottom of WPF controls at high DPIs, apps that target earlier versions of the .NET Framework but are running on the .NET Framework 4.6 can opt into this new behavior by adding the following line to the `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 <span data-ttu-id="e86e1-112">.NET Framework 4.6 hedef ancak WPF denetimleri önceki düzeni algoritmasını kullanarak oluşturmak istediğiniz uygulamalar yapabilirsiniz aşağıdaki satırı ekleyerek `<runtime>` app.config dosyasının:</span><span class="sxs-lookup"><span data-stu-id="e86e1-112">Apps that target the .NET Framework 4.6 but want WPF controls to render using the previous layout algorithm can do so by adding the following line to the  `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="e86e1-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e86e1-113">See Also</span></span>  
 [<span data-ttu-id="e86e1-114">Yeniden Hedefleme Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="e86e1-114">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
