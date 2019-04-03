---
title: Aralık değişkeni adı ancak bağımsız değişken içermeyen bir basit veya tam addan gösterilebilir
ms.date: 07/20/2015
f1_keywords:
- vbc36599
- bc36599
helpviewer_keywords:
- BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
ms.openlocfilehash: 344a813907483dcb0e9f531b54db68a88d77f3dc
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842388"
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
