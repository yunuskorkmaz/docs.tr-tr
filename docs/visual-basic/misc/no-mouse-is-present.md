---
title: Fare yok
ms.date: 07/20/2015
f1_keywords:
- vbrMouse_NoMouseIsPresent
ms.assetid: 4472fd57-4217-4463-9d3c-dc4a8fe88f1b
ms.openlocfilehash: 748661cae35292968aae989789a96d1df855b6ce
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84376130"
---
# <a name="no-mouse-is-present"></a><span data-ttu-id="bf507-102">Fare yok</span><span class="sxs-lookup"><span data-stu-id="bf507-102">No mouse is present</span></span>
<span data-ttu-id="bf507-103">Nesnenin özelliklerinden biri `My.Computer.Mouse` çağrıldı, ancak bilgisayarda fare veya fare bağlantı noktası yüklü değil.</span><span class="sxs-lookup"><span data-stu-id="bf507-103">One of the properties of the `My.Computer.Mouse` object was called, but the computer has no mouse or mouse port installed.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bf507-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="bf507-104">To correct this error</span></span>  
  
- <span data-ttu-id="bf507-105">`Try...Catch`Nesnenin özelliğine yapılan çağrının etrafına bir blok ekleyin `My.Computer.Mouse` .</span><span class="sxs-lookup"><span data-stu-id="bf507-105">Add a `Try...Catch` block around the call to the property of the `My.Computer.Mouse` object.</span></span>  
  
     <span data-ttu-id="bf507-106">veya</span><span class="sxs-lookup"><span data-stu-id="bf507-106">— or —</span></span>  
  
- <span data-ttu-id="bf507-107">Bilgisayara bir fare yükler.</span><span class="sxs-lookup"><span data-stu-id="bf507-107">Install a mouse on the computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf507-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf507-108">See also</span></span>

- [<span data-ttu-id="bf507-109">My. Computer. Mouse</span><span class="sxs-lookup"><span data-stu-id="bf507-109">My.Computer.Mouse</span></span>](xref:Microsoft.VisualBasic.Devices.Mouse)
- [<span data-ttu-id="bf507-110">.NET 'te özel durumları işleme ve atma</span><span class="sxs-lookup"><span data-stu-id="bf507-110">Handling and throwing exceptions in .NET</span></span>](../../standard/exceptions/index.md)
- [<span data-ttu-id="bf507-111">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="bf507-111">Try...Catch...Finally Statement</span></span>](../language-reference/statements/try-catch-finally-statement.md)
