---
description: 'Şu konuda daha fazla bilgi edinin: nasıl yapılır: Visual Basic bağlantı durumunu denetleme'
title: 'Nasıl yapılır: Bağlantı Durumunu Denetleme'
ms.date: 07/20/2015
helpviewer_keywords:
- Web connections [Visual Basic]
- IsAvailable property [Visual Basic], about IsAvailable
- connections [Visual Basic], checking status
- connection status [Visual Basic]
ms.assetid: 4d9ee8ab-9a6f-4279-ace4-b75afc976a74
ms.openlocfilehash: c568e3be5d8fedb1ae12c748110b23218deaf069
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797750"
---
# <a name="how-to-check-connection-status-in-visual-basic"></a><span data-ttu-id="5867a-103">Nasıl Yapılır: Visual Basic'te Bağlantı Durumunu Denetleme</span><span class="sxs-lookup"><span data-stu-id="5867a-103">How to: Check Connection Status in Visual Basic</span></span>

<span data-ttu-id="5867a-104"><xref:Microsoft.VisualBasic.Devices.Network.IsAvailable>Özelliği, bilgisayarın çalışan bir ağa veya Internet bağlantısına sahip olup olmadığını anlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5867a-104">The <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable> property can be used to determine whether the computer has a working network or Internet connection.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-check-whether-a-computer-has-a-working-connection"></a><span data-ttu-id="5867a-105">Bilgisayarda çalışan bir bağlantı olup olmadığını denetlemek için</span><span class="sxs-lookup"><span data-stu-id="5867a-105">To check whether a computer has a working connection</span></span>  
  
- <span data-ttu-id="5867a-106">`IsAvailable`Özelliğin veya olup olmadığını belirleme `True` `False` .</span><span class="sxs-lookup"><span data-stu-id="5867a-106">Determine whether the `IsAvailable` property is `True` or `False`.</span></span> <span data-ttu-id="5867a-107">Aşağıdaki kod özelliğin durumunu denetler ve raporlar:</span><span class="sxs-lookup"><span data-stu-id="5867a-107">The following code checks the property's status and reports it:</span></span>  
  
     [!code-vb[VbResourceTasks#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#3)]  
  
     <span data-ttu-id="5867a-108">Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5867a-108">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="5867a-109">Kod parçacığı seçicide, **bağlantı ve ağ** bölümünde bulunur.</span><span class="sxs-lookup"><span data-stu-id="5867a-109">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="5867a-110">Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="5867a-110">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5867a-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5867a-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable>
