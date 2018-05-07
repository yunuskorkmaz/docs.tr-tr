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
ms.openlocfilehash: 955a3b6a2f7dc1d0e9823ed6d500ab7f7f9fe5b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="stop-statement-visual-basic"></a>Stop Deyimi (Visual Basic)
Yürütme askıya alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Stop  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Yerleştireceğiniz `Stop` yürütme askıya almak için herhangi bir yere yordamları deyimlerinde. Kullanarak `Stop` deyimi kodda kesme noktası ayarlama benzer.  
  
 `Stop` Deyimi askıya alır, ancak yürütme `End`, bırakmaz tüm dosyaları kapatın veya bir derlenmiş yürütülebilir dosyanın (.exe) dosyasında karşılaşılan sürece herhangi bir değişkeni temizleyin.  
  
> [!NOTE]
>  Varsa `Stop` deyimi tümleşik geliştirme ortamı (IDE) dışında çalışan kodu ile karşılaştı, hata ayıklayıcı çağrılır. Bu kod hata ayıklama veya perakende modunda olup olmadığını derlenen bağımsız olarak geçerlidir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte `Stop` yürütme her bir yineleme için askıya almak için deyimi `For...Next` döngü.  
  
 [!code-vb[VbVbalrStatements#56](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/stop-statement_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [End Deyimi](../../../visual-basic/language-reference/statements/end-statement.md)
