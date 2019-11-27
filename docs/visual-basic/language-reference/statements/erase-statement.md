---
title: Erase Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 6d2052ceccbecd772c4e4bb18052aed74223a36e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343694"
---
# <a name="erase-statement-visual-basic"></a>Erase Deyimi (Visual Basic)
Dizi değişkenlerini serbest bırakmak ve öğeleri için kullanılan belleği serbest bırakmak için kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Erase arraylist  
```  
  
## <a name="parts"></a>Bölümler  
 `arraylist`  
 Gerekli. Silinecek dizi değişkenlerinin listesi. Birden çok değişken virgülle ayrılır.  
  
## <a name="remarks"></a>Açıklamalar  
 `Erase` deyimleri yalnızca yordam düzeyinde görünebilir. Bu, bir yordam içinde dizileri serbest bırakabilir, ancak sınıf veya modül düzeyinde değil.  
  
 `Erase` deyimin her dizi değişkenine `Nothing` atamaya eşdeğerdir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki diziyi temizlemek ve bellek (1000 ve 100 depolama öğelerini sırasıyla) boşaltmak için `Erase` ifadesini kullanır. `ReDim` deyimleri, üç boyutlu diziye yeni bir dizi örneği atar.  
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nothing](../../../visual-basic/language-reference/nothing.md)
- [ReDim Deyimi](../../../visual-basic/language-reference/statements/redim-statement.md)
