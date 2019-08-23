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
ms.openlocfilehash: a617038ec51d98c62b6cf7e3c124c8af01305bac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957615"
---
# <a name="stop-statement-visual-basic"></a>Stop Deyimi (Visual Basic)
Yürütmeyi askıya alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Stop  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Çalışmayı askıya almak `Stop` için deyimleri yordamların herhangi bir yerinde yerleştirebilirsiniz. `Stop` İfadesinin kullanılması kodda bir kesme noktası ayarlamaya benzerdir.  
  
 İfade yürütmeyi askıya alır, ancak farklı `End`olarak, derlenmiş bir çalıştırılabilir (. exe) dosyasında karşılaşılmadığı takdirde herhangi bir dosyayı kapatmaz veya hiçbir değişkeni temizlemez. `Stop`  
  
> [!NOTE]
> Tümleşik geliştirme ortamı (IDE) dışında çalışan kodda deyimekarşılaşılırsa,hataayıklayıcıçağrılır.`Stop` Bu, kodun hata ayıklama veya perakende modunda derlenmesinden bağımsız olarak geçerlidir.  
  
## <a name="example"></a>Örnek  
 Bu örnek, `Stop` `For...Next` döngüsü aracılığıyla her yineleme için yürütmeyi askıya almak üzere ifadesini kullanır.  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [End Deyimi](../../../visual-basic/language-reference/statements/end-statement.md)
