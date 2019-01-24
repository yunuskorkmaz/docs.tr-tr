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
ms.openlocfilehash: fa9a1942903dff6f673d87b67ebcad047a410425
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624788"
---
# <a name="stop-statement-visual-basic"></a>Stop Deyimi (Visual Basic)
Yürütmeyi askıya alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Stop  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Koyabilirsiniz `Stop` deyimleri yürütmeyi askıya almak için herhangi bir yordamda. Kullanarak `Stop` kodda bir kesme noktası ayarlamak ifade benzerdir.  
  
 `Stop` Deyimi askıya alır, ancak yürütme `End`, tüm dosyaları kapatın veya desteklemez derlenmiş yürütülebilir (.exe) dosyasında karşılaşılanaa sürece herhangi bir değişkeni temizleyin.  
  
> [!NOTE]
>  Varsa `Stop` deyimi tümleşik geliştirme ortamı (IDE) dışında çalışan kodu ile karşılaşıldı, hata ayıklayıcı çağrılır. Bu, perakende veya hata ayıklama modunda kod olup olmadığını derlenen bağımsız olarak geçerlidir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte `Stop` her yineleme için yürütmeyi askıya almak için deyimi `For...Next` döngü.  
  
 [!code-vb[VbVbalrStatements#56](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/stop-statement_1.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [End Deyimi](../../../visual-basic/language-reference/statements/end-statement.md)
