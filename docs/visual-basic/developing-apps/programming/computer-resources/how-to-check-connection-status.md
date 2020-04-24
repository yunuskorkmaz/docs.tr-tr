---
title: 'Nasıl yapılır: Bağlantı Durumunu Denetleme'
ms.date: 07/20/2015
helpviewer_keywords:
- Web connections [Visual Basic]
- IsAvailable property [Visual Basic], about IsAvailable
- connections [Visual Basic], checking status
- connection status [Visual Basic]
ms.assetid: 4d9ee8ab-9a6f-4279-ace4-b75afc976a74
ms.openlocfilehash: 89ef431759dac25bd213fd954db0712ad95434b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345888"
---
# <a name="how-to-check-connection-status-in-visual-basic"></a><span data-ttu-id="e4e7f-102">Nasıl Yapılır: Visual Basic'te Bağlantı Durumunu Denetleme</span><span class="sxs-lookup"><span data-stu-id="e4e7f-102">How to: Check Connection Status in Visual Basic</span></span>

<span data-ttu-id="e4e7f-103"><xref:Microsoft.VisualBasic.Devices.Network.IsAvailable> Özelliği, bilgisayarın çalışan bir ağa veya Internet bağlantısına sahip olup olmadığını anlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e4e7f-103">The <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable> property can be used to determine whether the computer has a working network or Internet connection.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-check-whether-a-computer-has-a-working-connection"></a><span data-ttu-id="e4e7f-104">Bilgisayarda çalışan bir bağlantı olup olmadığını denetlemek için</span><span class="sxs-lookup"><span data-stu-id="e4e7f-104">To check whether a computer has a working connection</span></span>  
  
- <span data-ttu-id="e4e7f-105">`IsAvailable` Özelliğin `True` veya `False`olup olmadığını belirleme.</span><span class="sxs-lookup"><span data-stu-id="e4e7f-105">Determine whether the `IsAvailable` property is `True` or `False`.</span></span> <span data-ttu-id="e4e7f-106">Aşağıdaki kod özelliğin durumunu denetler ve raporlar:</span><span class="sxs-lookup"><span data-stu-id="e4e7f-106">The following code checks the property's status and reports it:</span></span>  
  
     [!code-vb[VbResourceTasks#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#3)]  
  
     <span data-ttu-id="e4e7f-107">Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e4e7f-107">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="e4e7f-108">Kod parçacığı seçicide, **bağlantı ve ağ**bölümünde bulunur.</span><span class="sxs-lookup"><span data-stu-id="e4e7f-108">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="e4e7f-109">Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="e4e7f-109">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4e7f-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4e7f-110">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable>
