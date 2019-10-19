---
title: Stop Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Stop
helpviewer_keywords:
- breakpoints, Stop statements
- Stop statements [Visual Basic], syntax
- Stop statements [Visual Basic]
- execution [Visual Basic], suspending
- processing, interrupting
- processes, interrupting
- execution [Visual Basic], stopping
ms.assetid: c9a9fde0-d649-4662-9bef-bd0146ebc2a7
ms.openlocfilehash: e9382ee34842fc3a3b4b23f71848bda602c99780
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583217"
---
# <a name="stop-statement-visual-basic"></a>Stop Deyimi (Visual Basic)
Yürütmeyi askıya alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Stop  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Yürütmeyi askıya almak için `Stop` deyimlerini yordamların herhangi bir yerinde yerleştirebilirsiniz. @No__t_0 deyimin kullanılması, kodda kesme noktası ayarlamaya benzerdir.  
  
 @No__t_0 deyimin yürütülmesi askıya alınır, ancak `End` aksine, derlenmiş bir çalıştırılabilir (. exe) dosyasında karşılaşılmadığı takdirde hiçbir dosyayı kapatmaz veya hiçbir değişkeni temizlemez.  
  
> [!NOTE]
> Tümleşik geliştirme ortamı (IDE) dışında çalışan kodda `Stop` ifadesine karşılaşılırsa, hata ayıklayıcı çağrılır. Bu, kodun hata ayıklama veya perakende modunda derlenmesinden bağımsız olarak geçerlidir.  
  
## <a name="example"></a>Örnek  
 Bu örnek, `For...Next` döngüsü aracılığıyla her yineleme için yürütmeyi askıya almak üzere `Stop` ifadesini kullanır.  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [End Deyimi](../../../visual-basic/language-reference/statements/end-statement.md)
