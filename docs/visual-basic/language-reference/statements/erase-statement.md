---
title: Erase Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 7dec2a859f664ee8dcbb305082ec33aeacbaccb4
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583396"
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
 @No__t_0 deyimleri yalnızca yordam düzeyinde görünebilir. Bu, bir yordam içinde dizileri serbest bırakabilir, ancak sınıf veya modül düzeyinde değil.  
  
 @No__t_0 deyimin her dizi değişkenine `Nothing` atamaya eşdeğerdir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki diziyi temizlemek ve bellek (1000 ve 100 depolama öğelerini sırasıyla) boşaltmak için `Erase` ifadesini kullanır. @No__t_0 deyimleri, üç boyutlu diziye yeni bir dizi örneği atar.  
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nothing](../../../visual-basic/language-reference/nothing.md)
- [ReDim Deyimi](../../../visual-basic/language-reference/statements/redim-statement.md)
