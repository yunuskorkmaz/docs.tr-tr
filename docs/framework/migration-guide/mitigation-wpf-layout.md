---
title: 'Azaltma: WPF Düzeni'
description: WPF denetimleri düzeninde, bir pikselin hareket eden bir nesnenin yerleşimi gibi bir değişikliğin sonucu olan sorunları nasıl azaltacağınızı öğrenin.
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
ms.openlocfilehash: caed758f6e86a1e2bee255c2f29ca3160b327e17
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244086"
---
# <a name="mitigation-wpf-layout"></a><span data-ttu-id="c431f-103">Azaltma: WPF Düzeni</span><span class="sxs-lookup"><span data-stu-id="c431f-103">Mitigation: WPF Layout</span></span>

<span data-ttu-id="c431f-104">WPF denetimlerinin düzeni biraz değişebilir.</span><span class="sxs-lookup"><span data-stu-id="c431f-104">The layout of WPF controls can change slightly.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="c431f-105">Etki</span><span class="sxs-lookup"><span data-stu-id="c431f-105">Impact</span></span>  

 <span data-ttu-id="c431f-106">Bu değişikliğin sonucu olarak:</span><span class="sxs-lookup"><span data-stu-id="c431f-106">As a result of this change:</span></span>  
  
- <span data-ttu-id="c431f-107">Öğelerin genişliği veya yüksekliği, en fazla bir piksel ile büyüyebilir veya küçülebilir.</span><span class="sxs-lookup"><span data-stu-id="c431f-107">The width or height of elements may grow or shrink by at most one pixel.</span></span>  
  
- <span data-ttu-id="c431f-108">Bir nesnenin yerleştirilmesi en çok bir piksel kadar hareket edebilir.</span><span class="sxs-lookup"><span data-stu-id="c431f-108">The placement of an object can move by at most one pixel.</span></span>  
  
- <span data-ttu-id="c431f-109">Ortalanmış öğeler, en fazla bir piksel olarak orta veya yatay olarak devre dışı olabilir.</span><span class="sxs-lookup"><span data-stu-id="c431f-109">Centered elements can be vertically or horizontally off center by at most one pixel.</span></span>  
  
 <span data-ttu-id="c431f-110">Varsayılan olarak, bu yeni düzen yalnızca .NET Framework 4,6 ' i hedefleyen uygulamalar için etkindir.</span><span class="sxs-lookup"><span data-stu-id="c431f-110">By default, this new layout is enabled only for apps that target the .NET Framework 4.6.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="c431f-111">Risk azaltma</span><span class="sxs-lookup"><span data-stu-id="c431f-111">Mitigation</span></span>  

 <span data-ttu-id="c431f-112">Bu değişiklik, yüksek DPA 'daki WPF denetimlerinin sağ veya alt bölümünün kırpılmasını ortadan kaldırmaya eğiliminden, .NET Framework önceki sürümlerini hedefleyen ancak .NET Framework 4,6 üzerinde çalışan uygulamalar, app.config dosyasının bölümüne aşağıdaki satırı ekleyerek bu yeni davranışı kabul edebilir `<runtime>` :</span><span class="sxs-lookup"><span data-stu-id="c431f-112">Since this modification tends to eliminate clipping of the right or bottom of WPF controls at high DPIs, apps that target earlier versions of the .NET Framework but are running on the .NET Framework 4.6 can opt into this new behavior by adding the following line to the `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 <span data-ttu-id="c431f-113">.NET Framework 4,6 ' i hedefleyen ancak WPF denetimlerinin önceki düzen algoritmasını kullanarak işlemesini tercih eden uygulamalar, app.config dosyasının bölümüne aşağıdaki satırı ekleyerek yapabilir  `<runtime>` :</span><span class="sxs-lookup"><span data-stu-id="c431f-113">Apps that target the .NET Framework 4.6 but want WPF controls to render using the previous layout algorithm can do so by adding the following line to the  `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="c431f-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c431f-114">See also</span></span>

- [<span data-ttu-id="c431f-115">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="c431f-115">Application compatibility</span></span>](application-compatibility.md)
