---
title: Aralık değişkeni adı ancak bağımsız değişken içermeyen bir basit veya tam addan gösterilebilir
ms.date: 07/20/2015
f1_keywords:
- vbc36599
- bc36599
helpviewer_keywords:
- BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
ms.openlocfilehash: d6d082511d501b961b537317f0cb17bcd1c9370b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594627"
---
# <a name="range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a>Aralık değişkeni adı ancak bağımsız değişken içermeyen bir basit veya tam addan gösterilebilir
Bir veya daha fazla bağımsız değişken almayan bir programlama öğesi bir LINQ Sorgu dahil edilir. Derleyici aralık değişkeni bu programlama öğeden Infer alamıyor.  
  
 **Hata Kimliği:** BC36599  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Aşağıdaki kodda gösterildiği gibi programlama öğesi için açık bir değişken adı girin:  
  
```  
Dim query = From var1 In collection1   
            Select VariableAlias= SampleFunction(var1), var1  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de LINQ'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)
