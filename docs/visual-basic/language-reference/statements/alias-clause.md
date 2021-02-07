---
description: 'Daha fazla bilgi edinin: alias tümcesi (Visual Basic)'
title: Alias Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: bf0ee1c22105b29aedb99ce45a99ba866f4b93c1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99674083"
---
# <a name="alias-clause-visual-basic"></a>Alias Tümcesi (Visual Basic)

Bir dış yordamın DLL 'sinde başka bir ada sahip olduğunu gösterir.  
  
## <a name="remarks"></a>Açıklamalar  

 `Alias`Anahtar sözcüğü bu bağlamda kullanılabilir:  
  
 [Declare Deyimi](declare-statement.md)  
  
 Aşağıdaki örnekte `Alias` anahtar sözcüğü, `GetUserNameA` `getUserName` Bu örnekte yerine kullanılan advapi32.dll, işlevin adını sağlamak için kullanılır. İşlevi `getUserName` `getUser` , geçerli kullanıcının adını görüntüleyen Sub içinde çağırılır.  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Anahtar sözcükler](../keywords/index.md)
