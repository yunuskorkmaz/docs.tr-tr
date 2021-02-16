---
description: 'Daha fazla bilgi edinin: fare tekerleği yok'
title: Fare tekerleği yok
ms.date: 07/20/2015
f1_keywords:
- vbrMouse_NoWheelIsPresent
ms.assetid: e924ffba-4af1-4247-9a6f-d19a03738f62
ms.openlocfilehash: c712903f41aa9f7c37c0cf1e3ffdc76edfd85b7f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100479107"
---
# <a name="no-mouse-wheel-is-present"></a><span data-ttu-id="3ffea-103">Fare tekerleği yok</span><span class="sxs-lookup"><span data-stu-id="3ffea-103">No mouse wheel is present</span></span>

<span data-ttu-id="3ffea-104">`My.Computer.Mouse.WheelScrollLines`Özelliği çağrıldı, ancak fare kaydırma tekerleği yok.</span><span class="sxs-lookup"><span data-stu-id="3ffea-104">The `My.Computer.Mouse.WheelScrollLines` property was called, but the mouse has no scroll wheel.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3ffea-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="3ffea-105">To correct this error</span></span>  
  
- <span data-ttu-id="3ffea-106">`My.Computer.Mouse.WheelExists`Özelliği çağırmadan önce farenin bir kaydırma tekerleği olup olmadığını görmek için özelliği denetleyin `My.Computer.Mouse.WheelScrollLines` .</span><span class="sxs-lookup"><span data-stu-id="3ffea-106">Check the `My.Computer.Mouse.WheelExists` property to see if the mouse has a scroll wheel before calling the `My.Computer.Mouse.WheelScrollLines` property.</span></span>  
  
     <span data-ttu-id="3ffea-107">-veya-</span><span class="sxs-lookup"><span data-stu-id="3ffea-107">-or-</span></span>  
  
- <span data-ttu-id="3ffea-108">Bilgisayara bir kaydırma tekerleği ile bir fare yükler.</span><span class="sxs-lookup"><span data-stu-id="3ffea-108">Install a mouse with a scroll wheel on the computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ffea-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3ffea-109">See also</span></span>

- [<span data-ttu-id="3ffea-110">My. Computer. Mouse. WheelScrollLines</span><span class="sxs-lookup"><span data-stu-id="3ffea-110">My.Computer.Mouse.WheelScrollLines</span></span>](xref:Microsoft.VisualBasic.Devices.Mouse.WheelScrollLines)
- [<span data-ttu-id="3ffea-111">My. Computer. Mouse. WheelExists</span><span class="sxs-lookup"><span data-stu-id="3ffea-111">My.Computer.Mouse.WheelExists</span></span>](xref:Microsoft.VisualBasic.Devices.Mouse.WheelExists)
- [<span data-ttu-id="3ffea-112">.NET 'te özel durumları işleme ve atma</span><span class="sxs-lookup"><span data-stu-id="3ffea-112">Handling and throwing exceptions in .NET</span></span>](../../standard/exceptions/index.md)
