---
title: 'Azaltma: WPF Düzeni'
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
ms.openlocfilehash: 3e08a2d11e815248d0fe73f804e9ef7edb7c04da
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126106"
---
# <a name="mitigation-wpf-layout"></a><span data-ttu-id="e0b20-102">Azaltma: WPF Düzeni</span><span class="sxs-lookup"><span data-stu-id="e0b20-102">Mitigation: WPF Layout</span></span>
<span data-ttu-id="e0b20-103">WPF denetimlerinin düzeni biraz değişebilir.</span><span class="sxs-lookup"><span data-stu-id="e0b20-103">The layout of WPF controls can change slightly.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="e0b20-104">Etki</span><span class="sxs-lookup"><span data-stu-id="e0b20-104">Impact</span></span>  
 <span data-ttu-id="e0b20-105">Bu değişikliğin sonucu olarak:</span><span class="sxs-lookup"><span data-stu-id="e0b20-105">As a result of this change:</span></span>  
  
- <span data-ttu-id="e0b20-106">Öğelerin genişliği veya yüksekliği, en fazla bir piksel ile büyüyebilir veya küçülebilir.</span><span class="sxs-lookup"><span data-stu-id="e0b20-106">The width or height of elements may grow or shrink by at most one pixel.</span></span>  
  
- <span data-ttu-id="e0b20-107">Bir nesnenin yerleştirilmesi en çok bir piksel kadar hareket edebilir.</span><span class="sxs-lookup"><span data-stu-id="e0b20-107">The placement of an object can move by at most one pixel.</span></span>  
  
- <span data-ttu-id="e0b20-108">Ortalanmış öğeler, en fazla bir piksel olarak orta veya yatay olarak devre dışı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e0b20-108">Centered elements can be vertically or horizontally off center by at most one pixel.</span></span>  
  
 <span data-ttu-id="e0b20-109">Varsayılan olarak, bu yeni düzen yalnızca .NET Framework 4,6 ' i hedefleyen uygulamalar için etkindir.</span><span class="sxs-lookup"><span data-stu-id="e0b20-109">By default, this new layout is enabled only for apps that target the .NET Framework 4.6.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="e0b20-110">Azaltma</span><span class="sxs-lookup"><span data-stu-id="e0b20-110">Mitigation</span></span>  
 <span data-ttu-id="e0b20-111">Bu değişiklik, yüksek DPG 'de WPF denetimlerinin sağ veya alt kısmının kırpılmasını ortadan kaldıran eğilimi yaptığından, .NET Framework önceki sürümlerini hedefleyen ancak .NET Framework 4,6 üzerinde çalışan uygulamalar, @no aşağıdaki satırı ekleyerek bu yeni davranışı kabul edebilir App. config dosyasının __t_0_ bölümü:</span><span class="sxs-lookup"><span data-stu-id="e0b20-111">Since this modification tends to eliminate clipping of the right or bottom of WPF controls at high DPIs, apps that target earlier versions of the .NET Framework but are running on the .NET Framework 4.6 can opt into this new behavior by adding the following line to the `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 <span data-ttu-id="e0b20-112">.NET Framework 4,6 ' i hedefleyen ancak WPF denetimlerinin önceki düzen algoritmasını kullanarak işlemesini tercih eden uygulamalar, App. config dosyasının `<runtime>` bölümüne aşağıdaki satırı ekleyerek bunu yapabilir:</span><span class="sxs-lookup"><span data-stu-id="e0b20-112">Apps that target the .NET Framework 4.6 but want WPF controls to render using the previous layout algorithm can do so by adding the following line to the  `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="e0b20-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0b20-113">See also</span></span>

- [<span data-ttu-id="e0b20-114">Yeniden Hedefleme Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="e0b20-114">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6.md)
