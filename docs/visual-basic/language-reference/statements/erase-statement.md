---
title: Erase Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 317e2a7dc5facb08388f3a3e635734e4daed5eac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33601799"
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
 [Nothing](../../../visual-basic/language-reference/nothing.md)  
 [ReDim Deyimi](../../../visual-basic/language-reference/statements/redim-statement.md)
