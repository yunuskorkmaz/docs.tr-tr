---
title: Erase Deyimi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 45a2b439cf5ad04d59cea59bb21d345d0057b322
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="erase-statement-visual-basic"></a>Erase Deyimi (Visual Basic)
Dizi değişkenleri serbest bırakır ve bunların öğeler için kullanılan bellek ayırması için kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Erase arraylist  
```  
  
## <a name="parts"></a>Bölümler  
 `arraylist`  
 Gerekli. Dizi değişkenleri silinmesi listesi. Birden çok değişkenleri virgülle ayrılır.  
  
## <a name="remarks"></a>Açıklamalar  
 `Erase` Deyimi yalnızca yordamı düzeyinde görünebilir. Bu yordam içindeki ancak düzeyinde sınıfı veya modülü diziler serbest bırakabilirsiniz anlamına gelir.  
  
 `Erase` Açıklamadır atama için eşdeğer `Nothing` her bir dizi değişken için.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `Erase` dizilerinin temizlemek ve bunların belleği boşaltmak için deyimi (1000 ve 100 depolama öğeleri, sırasıyla). `ReDim` Sonra deyim üç boyutlu diziye yeni bir dizi örnek atar.  
  
 [!code-vb[VbVbalrStatements#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/erase-statement_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hiçbir şey](../../../visual-basic/language-reference/nothing.md)  
 [ReDim deyimi](../../../visual-basic/language-reference/statements/redim-statement.md)
