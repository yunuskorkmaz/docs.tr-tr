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
# <a name="how-to-check-connection-status-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Bağlantı Durumunu Denetleme

<xref:Microsoft.VisualBasic.Devices.Network.IsAvailable>Özelliği, bilgisayarın çalışan bir ağa veya Internet bağlantısına sahip olup olmadığını anlamak için kullanılabilir.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-check-whether-a-computer-has-a-working-connection"></a>Bilgisayarda çalışan bir bağlantı olup olmadığını denetlemek için  
  
- `IsAvailable`Özelliğin veya olup olmadığını belirleme `True` `False` . Aşağıdaki kod özelliğin durumunu denetler ve raporlar:  
  
     [!code-vb[VbResourceTasks#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#3)]  
  
     Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir. Kod parçacığı seçicide, **bağlantı ve ağ** bölümünde bulunur. Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable>
