---
title: 'Azaltma: WPF düzeni'
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f81af76ed305fb614202c240e449adc62b310933
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61871255"
---
# <a name="mitigation-wpf-layout"></a><span data-ttu-id="a67c2-102">Azaltma: WPF düzeni</span><span class="sxs-lookup"><span data-stu-id="a67c2-102">Mitigation: WPF Layout</span></span>
<span data-ttu-id="a67c2-103">WPF denetimleri düzenini biraz değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a67c2-103">The layout of WPF controls can change slightly.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="a67c2-104">Etki</span><span class="sxs-lookup"><span data-stu-id="a67c2-104">Impact</span></span>  
 <span data-ttu-id="a67c2-105">Bu değişikliğin ardından:</span><span class="sxs-lookup"><span data-stu-id="a67c2-105">As a result of this change:</span></span>  
  
- <span data-ttu-id="a67c2-106">Öğelerin yükseklik ve genişlik büyütür veya en fazla bir piksel küçültür.</span><span class="sxs-lookup"><span data-stu-id="a67c2-106">The width or height of elements may grow or shrink by at most one pixel.</span></span>  
  
- <span data-ttu-id="a67c2-107">Bir nesne yerleşimini en fazla bir piksel taşıyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a67c2-107">The placement of an object can move by at most one pixel.</span></span>  
  
- <span data-ttu-id="a67c2-108">Ortalanmış öğeleri yatay veya dikey olarak en fazla bir piksel merkezin olabilir.</span><span class="sxs-lookup"><span data-stu-id="a67c2-108">Centered elements can be vertically or horizontally off center by at most one pixel.</span></span>  
  
 <span data-ttu-id="a67c2-109">Bu yeni bir düzen, varsayılan olarak, yalnızca .NET Framework 4.6 hedefleyen uygulamalar için etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a67c2-109">By default, this new layout is enabled only for apps that target the .NET Framework 4.6.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="a67c2-110">Azaltma</span><span class="sxs-lookup"><span data-stu-id="a67c2-110">Mitigation</span></span>  
 <span data-ttu-id="a67c2-111">Bu yana sağında veya altında yüksek Dpı'larda WPF denetimleri, kırpma ortadan kaldırmak için bu değişikliği eğilimi gösterir, ancak .NET Framework 4.6 üzerinde çalışan .NET Framework'ün önceki sürümlerini hedefleyen uygulamalar bu yeni davranış aşağıdaki satırı ekleyerek seçebilirsiniz `<runtime>` app.config dosyasının:</span><span class="sxs-lookup"><span data-stu-id="a67c2-111">Since this modification tends to eliminate clipping of the right or bottom of WPF controls at high DPIs, apps that target earlier versions of the .NET Framework but are running on the .NET Framework 4.6 can opt into this new behavior by adding the following line to the `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 <span data-ttu-id="a67c2-112">.NET Framework 4.6 hedef ancak önceki yerleşimi algoritmasını kullanarak işlemek için WPF denetimleri isteyen uygulamalar bunu aşağıdaki satırı ekleyerek `<runtime>` app.config dosyasının:</span><span class="sxs-lookup"><span data-stu-id="a67c2-112">Apps that target the .NET Framework 4.6 but want WPF controls to render using the previous layout algorithm can do so by adding the following line to the  `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="a67c2-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a67c2-113">See also</span></span>

- [<span data-ttu-id="a67c2-114">Yeniden Hedefleme Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="a67c2-114">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
