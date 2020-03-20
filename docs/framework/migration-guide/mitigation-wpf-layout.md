---
title: 'Azaltma: WPF Düzeni'
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
ms.openlocfilehash: 7a074698fd203d0c5f9b799bfee8a6a9cb40800e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457788"
---
# <a name="mitigation-wpf-layout"></a><span data-ttu-id="65dcd-102">Azaltma: WPF Düzeni</span><span class="sxs-lookup"><span data-stu-id="65dcd-102">Mitigation: WPF Layout</span></span>
<span data-ttu-id="65dcd-103">WPF denetimlerinin düzeni biraz değişebilir.</span><span class="sxs-lookup"><span data-stu-id="65dcd-103">The layout of WPF controls can change slightly.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="65dcd-104">Etki</span><span class="sxs-lookup"><span data-stu-id="65dcd-104">Impact</span></span>  
 <span data-ttu-id="65dcd-105">Bu değişikliğin bir sonucu olarak:</span><span class="sxs-lookup"><span data-stu-id="65dcd-105">As a result of this change:</span></span>  
  
- <span data-ttu-id="65dcd-106">Öğelerin genişliği veya yüksekliği en fazla bir piksel büyüyebilir veya küçülebilir.</span><span class="sxs-lookup"><span data-stu-id="65dcd-106">The width or height of elements may grow or shrink by at most one pixel.</span></span>  
  
- <span data-ttu-id="65dcd-107">Bir nesnenin yerleşimi en fazla bir piksel tarafından hareket edebilir.</span><span class="sxs-lookup"><span data-stu-id="65dcd-107">The placement of an object can move by at most one pixel.</span></span>  
  
- <span data-ttu-id="65dcd-108">Ortalanmış öğeler en fazla bir piksel ile dikey veya yatay kapalı merkezi olabilir.</span><span class="sxs-lookup"><span data-stu-id="65dcd-108">Centered elements can be vertically or horizontally off center by at most one pixel.</span></span>  
  
 <span data-ttu-id="65dcd-109">Varsayılan olarak, bu yeni düzen yalnızca .NET Framework 4.6'yı hedefleyen uygulamalar için etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="65dcd-109">By default, this new layout is enabled only for apps that target the .NET Framework 4.6.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="65dcd-110">Risk azaltma</span><span class="sxs-lookup"><span data-stu-id="65dcd-110">Mitigation</span></span>  
 <span data-ttu-id="65dcd-111">Bu değişiklik yüksek DPI'larda WPF denetimlerinin sağ veya alt kesiminin kırpma sını ortadan kaldırma eğiliminde olduğundan, .NET Framework'ün önceki sürümlerini hedefleyen ancak .NET `<runtime>` Framework 4.6 üzerinde çalışan uygulamalar, app.config dosyasının bölümüne aşağıdaki satırı ekleyerek bu yeni davranışı seçebilir:</span><span class="sxs-lookup"><span data-stu-id="65dcd-111">Since this modification tends to eliminate clipping of the right or bottom of WPF controls at high DPIs, apps that target earlier versions of the .NET Framework but are running on the .NET Framework 4.6 can opt into this new behavior by adding the following line to the `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 <span data-ttu-id="65dcd-112">.NET Framework 4.6'yı hedefleyen ancak WPF denetimlerinin önceki düzen algoritmasını kullanarak işlemesini `<runtime>` isteyen uygulamalar, app.config dosyasının bölümüne aşağıdaki satırı ekleyerek bunu yapabilir:</span><span class="sxs-lookup"><span data-stu-id="65dcd-112">Apps that target the .NET Framework 4.6 but want WPF controls to render using the previous layout algorithm can do so by adding the following line to the  `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="65dcd-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65dcd-113">See also</span></span>

- [<span data-ttu-id="65dcd-114">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="65dcd-114">Application compatibility</span></span>](application-compatibility.md)
