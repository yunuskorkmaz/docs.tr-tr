---
title: -&gt; İşleci (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
ms.openlocfilehash: 09d67b8386da371f7d98a8171f60298b316091ea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="-gt-operator-c-reference"></a>-&gt; İşleci (C# Başvurusu)
`->` İşleci, birleştirir işaretçi başvurusunun kaldırılmasının ve üye erişimi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir ifade formun  
  
```  
x->y  
```  
  
 (burada `x` işaretçi türü `T*` ve `y` üyesi `T`), eşdeğerdir  
  
```  
(*x).y  
```  
  
 `->` İşleci olarak işaretlenen kod kullanılabilir [güvensiz](../../../csharp/language-reference/keywords/unsafe.md).  
  
 `->` İşleci olamaz aşırı yüklenebilir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csRefOperators#15](../../../csharp/language-reference/operators/codesnippet/CSharp/dereference-operator_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# İşleçleri](../../../csharp/language-reference/operators/index.md)
