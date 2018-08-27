---
title: "Nasıl Yapılır: Visual Basic'te Bağlantı Durumunu Denetleme"
ms.date: 07/20/2015
helpviewer_keywords:
- Web connections [Visual Basic]
- IsAvailable property [Visual Basic], about IsAvailable
- connections [Visual Basic], checking status
- connection status [Visual Basic]
ms.assetid: 4d9ee8ab-9a6f-4279-ace4-b75afc976a74
ms.openlocfilehash: 4a6cb67474d03ada5e0a73d94f65da7a381c44a8
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2018
ms.locfileid: "42911947"
---
# <a name="how-to-check-connection-status-in-visual-basic"></a><span data-ttu-id="3b174-102">Nasıl Yapılır: Visual Basic'te Bağlantı Durumunu Denetleme</span><span class="sxs-lookup"><span data-stu-id="3b174-102">How to: Check Connection Status in Visual Basic</span></span>
<span data-ttu-id="3b174-103"><xref:Microsoft.VisualBasic.Devices.Network.IsAvailable> Özelliği, bilgisayar bir çalışma ağ veya Internet bağlantısı olup olmadığını belirlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3b174-103">The <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable> property can be used to determine whether the computer has a working network or Internet connection.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-check-whether-a-computer-has-a-working-connection"></a><span data-ttu-id="3b174-104">Bir bilgisayarda çalışan bir bağlantı olup olmadığını denetlemek için</span><span class="sxs-lookup"><span data-stu-id="3b174-104">To check whether a computer has a working connection</span></span>  
  
-   <span data-ttu-id="3b174-105">Belirlemek olmadığını `IsAvailable` özelliği `True` veya `False`.</span><span class="sxs-lookup"><span data-stu-id="3b174-105">Determine whether the `IsAvailable` property is `True` or `False`.</span></span> <span data-ttu-id="3b174-106">Aşağıdaki kod, özelliğin durumunu denetler ve rapor:</span><span class="sxs-lookup"><span data-stu-id="3b174-106">The following code checks the property's status and reports it:</span></span>  
  
     [!code-vb[VbResourceTasks#3](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-check-connection-status_1.vb)]  
  
     <span data-ttu-id="3b174-107">Bu kod örneği, bir IntelliSense kod parçacığı da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3b174-107">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="3b174-108">Kod parçacığı Seçici'de bulunur **bağlantı ve ağ**.</span><span class="sxs-lookup"><span data-stu-id="3b174-108">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="3b174-109">Daha fazla bilgi için [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="3b174-109">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b174-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3b174-110">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable>
