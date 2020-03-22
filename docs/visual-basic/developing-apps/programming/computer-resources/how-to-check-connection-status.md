---
title: 'Nasıl Yapılır: Bağlantı Durumunu Denetleme'
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
# <a name="how-to-check-connection-status-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Bağlantı Durumunu Denetleme

Özellik, <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable> bilgisayarın çalışma ağı veya Internet bağlantısı olup olmadığını belirlemek için kullanılabilir.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-check-whether-a-computer-has-a-working-connection"></a>Bilgisayarın çalışma bağlantısı olup olmadığını denetlemek için  
  
- Özelliğin `IsAvailable` olup `True` olmadığını `False`veya . Aşağıdaki kod özelliğin durumunu denetler ve bildirir:  
  
     [!code-vb[VbResourceTasks#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#3)]  
  
     Bu kod örneği, IntelliSense kod parçacığı olarak da kullanılabilir. Kod snippet toplayıcı, **bağlantı ve ağ**bulunmaktadır. Daha fazla bilgi için [Kod Parçacıkları'na](/visualstudio/ide/code-snippets)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable>
