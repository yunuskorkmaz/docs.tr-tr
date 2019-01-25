---
title: Aralık değişkeni adı ancak bağımsız değişken içermeyen bir basit veya tam addan gösterilebilir
ms.date: 07/20/2015
f1_keywords:
- vbc36599
- bc36599
helpviewer_keywords:
- BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
ms.openlocfilehash: 8b95bb3c53210cc11966466d32924c13aee8234b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54581963"
---
# <a name="range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a>Aralık değişkeni adı ancak bağımsız değişken içermeyen bir basit veya tam addan gösterilebilir
Bir veya daha fazla bağımsız değişken alan bir programlama öğesinin bir LINQ Sorgu dahil edilir. Derleyici, bir aralık değişkenine programlama bu öğeden çıkarmak silemiyor.  
  
 **Hata Kimliği:** BC36599  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Programlama öğesi için açık bir değişken adı, aşağıdaki kodda gösterildiği gibi sağlayın:  
  
```  
Dim query = From var1 In collection1   
            Select VariableAlias= SampleFunction(var1), var1  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Visual Basic'de LINQ'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)
