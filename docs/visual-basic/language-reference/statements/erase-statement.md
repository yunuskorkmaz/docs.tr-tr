---
description: ': Erase açıklaması hakkında daha fazla bilgi edinin (Visual Basic)'
title: Erase Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 295abec89f3d69f8f2641a5a3d574a2d10f98474
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99769162"
---
# <a name="erase-statement-visual-basic"></a>Erase Deyimi (Visual Basic)

Dizi değişkenlerini serbest bırakmak ve öğeleri için kullanılan belleği serbest bırakmak için kullanılır.  
  
## <a name="syntax"></a>Syntax  
  
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

- [Nothing](../nothing.md)
- [ReDim Deyimi](redim-statement.md)
