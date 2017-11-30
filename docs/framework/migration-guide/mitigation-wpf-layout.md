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
ms.openlocfilehash: d3ba5ac792169cc076f9621025f35444281cec6e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="mitigation-wpf-layout"></a><span data-ttu-id="36b0a-102">Azaltma: WPF Düzeni</span><span class="sxs-lookup"><span data-stu-id="36b0a-102">Mitigation: WPF Layout</span></span>
<span data-ttu-id="36b0a-103">WPF denetimleri düzenini biraz değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36b0a-103">The layout of WPF controls can change slightly.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="36b0a-104">Etki</span><span class="sxs-lookup"><span data-stu-id="36b0a-104">Impact</span></span>  
 <span data-ttu-id="36b0a-105">Bu değişikliğin sonucu olarak:</span><span class="sxs-lookup"><span data-stu-id="36b0a-105">As a result of this change:</span></span>  
  
-   <span data-ttu-id="36b0a-106">Genişlik veya yüksekliğinden öğelerinin büyütür veya en çok bir piksel küçültür.</span><span class="sxs-lookup"><span data-stu-id="36b0a-106">The width or height of elements may grow or shrink by at most one pixel.</span></span>  
  
-   <span data-ttu-id="36b0a-107">Bir nesne yerleşimini en çok bir piksel taşıyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36b0a-107">The placement of an object can move by at most one pixel.</span></span>  
  
-   <span data-ttu-id="36b0a-108">Ortalanmış öğeleri dikey veya yatay olarak merkezi en çok bir piksel tarafından devre dışı olabilir.</span><span class="sxs-lookup"><span data-stu-id="36b0a-108">Centered elements can be vertically or horizontally off center by at most one pixel.</span></span>  
  
 <span data-ttu-id="36b0a-109">Varsayılan olarak, bu yeni düzen .NET Framework 4.6 hedefleyen uygulamalar için etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="36b0a-109">By default, this new layout is enabled only for apps that target the .NET Framework 4.6.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="36b0a-110">Azaltma</span><span class="sxs-lookup"><span data-stu-id="36b0a-110">Mitigation</span></span>  
 <span data-ttu-id="36b0a-111">Kırpma sağa ya da yüksek DPIs WPF denetimleri alt ortadan kaldırmak için bu değişiklik eğilimlidir olduğundan, .NET Framework'ün önceki sürümlerini hedefleyen ama .NET Framework 4.6 üzerinde çalışan uygulamalar bu yeni davranış aşağıdaki satırı ekleyerek seçebilirsiniz `<runtime>` app.config dosyasının:</span><span class="sxs-lookup"><span data-stu-id="36b0a-111">Since this modification tends to eliminate clipping of the right or bottom of WPF controls at high DPIs, apps that target earlier versions of the .NET Framework but are running on the .NET Framework 4.6 can opt into this new behavior by adding the following line to the `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 <span data-ttu-id="36b0a-112">.NET Framework 4.6 hedef ancak WPF denetimleri önceki düzeni algoritmasını kullanarak oluşturmak istediğiniz uygulamalar yapabilirsiniz aşağıdaki satırı ekleyerek `<runtime>` app.config dosyasının:</span><span class="sxs-lookup"><span data-stu-id="36b0a-112">Apps that target the .NET Framework 4.6 but want WPF controls to render using the previous layout algorithm can do so by adding the following line to the  `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="36b0a-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="36b0a-113">See Also</span></span>  
 [<span data-ttu-id="36b0a-114">Yeniden hedefleme değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="36b0a-114">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
