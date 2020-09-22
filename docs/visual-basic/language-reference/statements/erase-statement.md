---
title: Erase Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 33d88b5ce71ceab8d4b4b59d356c53a804c360be
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873283"
---
# <a name="erase-statement-visual-basic"></a>Erase Deyimi (Visual Basic)

Dizi değişkenlerini serbest bırakmak ve öğeleri için kullanılan belleği serbest bırakmak için kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Erase arraylist  
```  
  
## <a name="parts"></a>Bölümler  

 `arraylist`  
 Gereklidir. Silinecek dizi değişkenlerinin listesi. Birden çok değişken virgülle ayrılır.  
  
## <a name="remarks"></a>Açıklamalar  

 `Erase`Deyimde yalnızca yordam düzeyinde görünebilir. Bu, bir yordam içinde dizileri serbest bırakabilir, ancak sınıf veya modül düzeyinde değil.  
  
 `Erase`Deyimleri `Nothing` her dizi değişkenine atamaya eşdeğerdir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, iki diziyi `Erase` temizlemek ve bellek (1000 ve 100 depolama öğelerini sırasıyla) boşaltmak için ifadesini kullanır. `ReDim`Daha sonra ifade, üç boyutlu diziye yeni bir dizi örneği atar.  
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yapma](../nothing.md)
- [ReDim Deyimi](redim-statement.md)
