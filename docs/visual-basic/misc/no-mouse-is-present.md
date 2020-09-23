---
title: Fare yok
ms.date: 07/20/2015
f1_keywords:
- vbrMouse_NoMouseIsPresent
ms.assetid: 4472fd57-4217-4463-9d3c-dc4a8fe88f1b
ms.openlocfilehash: ceb850d98d29c232da304fbdfaddf5611714ef1a
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91078859"
---
# <a name="no-mouse-is-present"></a><span data-ttu-id="b0308-102">Fare yok</span><span class="sxs-lookup"><span data-stu-id="b0308-102">No mouse is present</span></span>

<span data-ttu-id="b0308-103">Nesnenin özelliklerinden biri `My.Computer.Mouse` çağrıldı, ancak bilgisayarda fare veya fare bağlantı noktası yüklü değil.</span><span class="sxs-lookup"><span data-stu-id="b0308-103">One of the properties of the `My.Computer.Mouse` object was called, but the computer has no mouse or mouse port installed.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b0308-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="b0308-104">To correct this error</span></span>  
  
- <span data-ttu-id="b0308-105">`Try...Catch`Nesnenin özelliğine yapılan çağrının etrafına bir blok ekleyin `My.Computer.Mouse` .</span><span class="sxs-lookup"><span data-stu-id="b0308-105">Add a `Try...Catch` block around the call to the property of the `My.Computer.Mouse` object.</span></span>  
  
     <span data-ttu-id="b0308-106">veya</span><span class="sxs-lookup"><span data-stu-id="b0308-106">— or —</span></span>  
  
- <span data-ttu-id="b0308-107">Bilgisayara bir fare yükler.</span><span class="sxs-lookup"><span data-stu-id="b0308-107">Install a mouse on the computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0308-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0308-108">See also</span></span>

- [<span data-ttu-id="b0308-109">My. Computer. Mouse</span><span class="sxs-lookup"><span data-stu-id="b0308-109">My.Computer.Mouse</span></span>](xref:Microsoft.VisualBasic.Devices.Mouse)
- [<span data-ttu-id="b0308-110">.NET 'te özel durumları işleme ve atma</span><span class="sxs-lookup"><span data-stu-id="b0308-110">Handling and throwing exceptions in .NET</span></span>](../../standard/exceptions/index.md)
- [<span data-ttu-id="b0308-111">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="b0308-111">Try...Catch...Finally Statement</span></span>](../language-reference/statements/try-catch-finally-statement.md)
