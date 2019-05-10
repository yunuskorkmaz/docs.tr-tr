---
title: "Nasıl yapılır: Visual Basic'te bağlantı durumunu denetleyin"
ms.date: 07/20/2015
helpviewer_keywords:
- Web connections [Visual Basic]
- IsAvailable property [Visual Basic], about IsAvailable
- connections [Visual Basic], checking status
- connection status [Visual Basic]
ms.assetid: 4d9ee8ab-9a6f-4279-ace4-b75afc976a74
ms.openlocfilehash: 1a03b181c2e363c3380c4f9858b629713641f2c2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64620683"
---
# <a name="how-to-check-connection-status-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te bağlantı durumunu denetleyin
<xref:Microsoft.VisualBasic.Devices.Network.IsAvailable> Özelliği, bilgisayar bir çalışma ağ veya Internet bağlantısı olup olmadığını belirlemek için kullanılabilir.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-check-whether-a-computer-has-a-working-connection"></a>Bir bilgisayarda çalışan bir bağlantı olup olmadığını denetlemek için  
  
- Belirlemek olmadığını `IsAvailable` özelliği `True` veya `False`. Aşağıdaki kod, özelliğin durumunu denetler ve rapor:  
  
     [!code-vb[VbResourceTasks#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#3)]  
  
     Bu kod örneği, bir IntelliSense kod parçacığı da kullanılabilir. Kod parçacığı Seçici'de bulunur **bağlantı ve ağ**. Daha fazla bilgi için [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable>
