---
title: Fare tekerleği yok
ms.date: 07/20/2015
f1_keywords:
- vbrMouse_NoWheelIsPresent
ms.assetid: e924ffba-4af1-4247-9a6f-d19a03738f62
ms.openlocfilehash: a9b468d876945a177f3e326a7dc37e6c8a80285d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91078846"
---
# <a name="no-mouse-wheel-is-present"></a><span data-ttu-id="0b833-102">Fare tekerleği yok</span><span class="sxs-lookup"><span data-stu-id="0b833-102">No mouse wheel is present</span></span>

<span data-ttu-id="0b833-103">`My.Computer.Mouse.WheelScrollLines`Özelliği çağrıldı, ancak fare kaydırma tekerleği yok.</span><span class="sxs-lookup"><span data-stu-id="0b833-103">The `My.Computer.Mouse.WheelScrollLines` property was called, but the mouse has no scroll wheel.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0b833-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="0b833-104">To correct this error</span></span>  
  
- <span data-ttu-id="0b833-105">`My.Computer.Mouse.WheelExists`Özelliği çağırmadan önce farenin bir kaydırma tekerleği olup olmadığını görmek için özelliği denetleyin `My.Computer.Mouse.WheelScrollLines` .</span><span class="sxs-lookup"><span data-stu-id="0b833-105">Check the `My.Computer.Mouse.WheelExists` property to see if the mouse has a scroll wheel before calling the `My.Computer.Mouse.WheelScrollLines` property.</span></span>  
  
     <span data-ttu-id="0b833-106">-veya-</span><span class="sxs-lookup"><span data-stu-id="0b833-106">-or-</span></span>  
  
- <span data-ttu-id="0b833-107">Bilgisayara bir kaydırma tekerleği ile bir fare yükler.</span><span class="sxs-lookup"><span data-stu-id="0b833-107">Install a mouse with a scroll wheel on the computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b833-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b833-108">See also</span></span>

- [<span data-ttu-id="0b833-109">My. Computer. Mouse. WheelScrollLines</span><span class="sxs-lookup"><span data-stu-id="0b833-109">My.Computer.Mouse.WheelScrollLines</span></span>](xref:Microsoft.VisualBasic.Devices.Mouse.WheelScrollLines)
- [<span data-ttu-id="0b833-110">My. Computer. Mouse. WheelExists</span><span class="sxs-lookup"><span data-stu-id="0b833-110">My.Computer.Mouse.WheelExists</span></span>](xref:Microsoft.VisualBasic.Devices.Mouse.WheelExists)
- [<span data-ttu-id="0b833-111">.NET 'te özel durumları işleme ve atma</span><span class="sxs-lookup"><span data-stu-id="0b833-111">Handling and throwing exceptions in .NET</span></span>](../../standard/exceptions/index.md)
