---
title: Stop Deyimi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Stop
helpviewer_keywords:
- breakpoints, Stop statements
- Stop statements [Visual Basic], syntax
- Stop statements [Visual Basic]
- execution [Visual Basic], suspending
- processing, interrupting
- processes, interrupting
- execution [Visual Basic], stopping
ms.assetid: c9a9fde0-d649-4662-9bef-bd0146ebc2a7
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d4b7f04214234837a86bf0c77c0d7b6934e2babd
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
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
 [End deyimi](../../../visual-basic/language-reference/statements/end-statement.md)
