---
title: Stop Deyimi
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
ms.openlocfilehash: c9226ccaea9a0709a9d6a49900f69cb9ac9e1dbe
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871739"
---
# <a name="stop-statement-visual-basic"></a>Stop Deyimi (Visual Basic)

Yürütmeyi askıya alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Stop  
```  
  
## <a name="remarks"></a>Açıklamalar  

 `Stop`Çalışmayı askıya almak için deyimleri yordamların herhangi bir yerinde yerleştirebilirsiniz. İfadesinin kullanılması `Stop` kodda bir kesme noktası ayarlamaya benzerdir.  
  
 `Stop`İfade yürütmeyi askıya alır, ancak farklı olarak, `End` derlenmiş bir çalıştırılabilir (. exe) dosyasında karşılaşılmadığı takdirde herhangi bir dosyayı kapatmaz veya hiçbir değişkeni temizlemez.  
  
> [!NOTE]
> `Stop`Tümleşik geliştirme ortamı (IDE) dışında çalışan kodda deyime karşılaşılırsa, hata ayıklayıcı çağrılır. Bu, kodun hata ayıklama veya perakende modunda derlenmesinden bağımsız olarak geçerlidir.  
  
## <a name="example"></a>Örnek  

 Bu örnek, `Stop` döngüsü aracılığıyla her yineleme için yürütmeyi askıya almak üzere ifadesini kullanır `For...Next` .  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [End ekstresi](end-statement.md)
