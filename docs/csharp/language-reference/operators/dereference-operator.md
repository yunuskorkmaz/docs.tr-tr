---
title: -&gt; İşleci (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
ms.openlocfilehash: 037229b2081a43077cb4b5d02a8929b06ba9e077
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
---
# <a name="-gt-operator-c-reference"></a>-&gt; İşleci (C# Başvurusu)
`->` İşleci, birleştirir işaretçi başvurusunun kaldırılmasının ve üye erişimi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir ifade formun  
  
```csharp  
x->y  
```  
  
 (burada `x` işaretçi türü `T*` ve `y` üyesi `T`), eşdeğerdir  
  
```csharp  
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
