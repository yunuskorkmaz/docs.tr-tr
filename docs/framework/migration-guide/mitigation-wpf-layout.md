---
title: Mayı WPF düzeni
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d266ad33110d2bda8f7911d89981c372624c3f36
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779073"
---
# <a name="mitigation-wpf-layout"></a><span data-ttu-id="2a22b-102">Mayı WPF düzeni</span><span class="sxs-lookup"><span data-stu-id="2a22b-102">Mitigation: WPF Layout</span></span>
<span data-ttu-id="2a22b-103">WPF denetimlerinin düzeni biraz değişebilir.</span><span class="sxs-lookup"><span data-stu-id="2a22b-103">The layout of WPF controls can change slightly.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="2a22b-104">Etki</span><span class="sxs-lookup"><span data-stu-id="2a22b-104">Impact</span></span>  
 <span data-ttu-id="2a22b-105">Bu değişikliğin sonucu olarak:</span><span class="sxs-lookup"><span data-stu-id="2a22b-105">As a result of this change:</span></span>  
  
- <span data-ttu-id="2a22b-106">Öğelerin genişliği veya yüksekliği, en fazla bir piksel ile büyüyebilir veya küçülebilir.</span><span class="sxs-lookup"><span data-stu-id="2a22b-106">The width or height of elements may grow or shrink by at most one pixel.</span></span>  
  
- <span data-ttu-id="2a22b-107">Bir nesnenin yerleştirilmesi en çok bir piksel kadar hareket edebilir.</span><span class="sxs-lookup"><span data-stu-id="2a22b-107">The placement of an object can move by at most one pixel.</span></span>  
  
- <span data-ttu-id="2a22b-108">Ortalanmış öğeler, en fazla bir piksel olarak orta veya yatay olarak devre dışı olabilir.</span><span class="sxs-lookup"><span data-stu-id="2a22b-108">Centered elements can be vertically or horizontally off center by at most one pixel.</span></span>  
  
 <span data-ttu-id="2a22b-109">Varsayılan olarak, bu yeni düzen yalnızca .NET Framework 4,6 ' i hedefleyen uygulamalar için etkindir.</span><span class="sxs-lookup"><span data-stu-id="2a22b-109">By default, this new layout is enabled only for apps that target the .NET Framework 4.6.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="2a22b-110">Azaltma</span><span class="sxs-lookup"><span data-stu-id="2a22b-110">Mitigation</span></span>  
 <span data-ttu-id="2a22b-111">Bu değişiklik, yüksek DPG 'de WPF denetimlerinin sağ veya alt kısmının kırpılmasını ortadan kaldıran eğilimi yaptığından, .NET Framework önceki sürümlerini hedefleyen ancak .NET Framework 4,6 üzerinde çalışan uygulamalar bu yeni davranışa aşağıdaki satırı ekleyerek `<runtime>` App. config dosyasının bölümü:</span><span class="sxs-lookup"><span data-stu-id="2a22b-111">Since this modification tends to eliminate clipping of the right or bottom of WPF controls at high DPIs, apps that target earlier versions of the .NET Framework but are running on the .NET Framework 4.6 can opt into this new behavior by adding the following line to the `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 <span data-ttu-id="2a22b-112">.NET Framework 4,6 ' i hedefleyen ancak WPF denetimlerinin önceki düzen algoritmasını kullanarak işlemesini tercih eden uygulamalar, App. config dosyasının `<runtime>` bölümüne aşağıdaki satırı ekleyerek bunu yapabilir:</span><span class="sxs-lookup"><span data-stu-id="2a22b-112">Apps that target the .NET Framework 4.6 but want WPF controls to render using the previous layout algorithm can do so by adding the following line to the  `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="2a22b-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a22b-113">See also</span></span>

- [<span data-ttu-id="2a22b-114">Yeniden Hedefleme Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="2a22b-114">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6.md)
