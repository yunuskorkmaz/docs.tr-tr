---
description: 'Daha fazla bilgi edinin: fare yok'
title: Fare yok
ms.date: 07/20/2015
f1_keywords:
- vbrMouse_NoMouseIsPresent
ms.assetid: 4472fd57-4217-4463-9d3c-dc4a8fe88f1b
ms.openlocfilehash: 1964f1def655a1e38ce2b8919a69ab2e6ac929a7
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100479133"
---
# <a name="no-mouse-is-present"></a><span data-ttu-id="447f4-103">Fare yok</span><span class="sxs-lookup"><span data-stu-id="447f4-103">No mouse is present</span></span>

<span data-ttu-id="447f4-104">Nesnenin özelliklerinden biri `My.Computer.Mouse` çağrıldı, ancak bilgisayarda fare veya fare bağlantı noktası yüklü değil.</span><span class="sxs-lookup"><span data-stu-id="447f4-104">One of the properties of the `My.Computer.Mouse` object was called, but the computer has no mouse or mouse port installed.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="447f4-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="447f4-105">To correct this error</span></span>  
  
- <span data-ttu-id="447f4-106">`Try...Catch`Nesnenin özelliğine yapılan çağrının etrafına bir blok ekleyin `My.Computer.Mouse` .</span><span class="sxs-lookup"><span data-stu-id="447f4-106">Add a `Try...Catch` block around the call to the property of the `My.Computer.Mouse` object.</span></span>  
  
     <span data-ttu-id="447f4-107">veya</span><span class="sxs-lookup"><span data-stu-id="447f4-107">— or —</span></span>  
  
- <span data-ttu-id="447f4-108">Bilgisayara bir fare yükler.</span><span class="sxs-lookup"><span data-stu-id="447f4-108">Install a mouse on the computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="447f4-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="447f4-109">See also</span></span>

- [<span data-ttu-id="447f4-110">My. Computer. Mouse</span><span class="sxs-lookup"><span data-stu-id="447f4-110">My.Computer.Mouse</span></span>](xref:Microsoft.VisualBasic.Devices.Mouse)
- [<span data-ttu-id="447f4-111">.NET 'te özel durumları işleme ve atma</span><span class="sxs-lookup"><span data-stu-id="447f4-111">Handling and throwing exceptions in .NET</span></span>](../../standard/exceptions/index.md)
- [<span data-ttu-id="447f4-112">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="447f4-112">Try...Catch...Finally Statement</span></span>](../language-reference/statements/try-catch-finally-statement.md)
