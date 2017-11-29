---
title: "-&gt;İşleci (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: ->_CSharpKeyword
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4c5918f56257feb29d2624ba29b8cebaaa4f4ebe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="-gt-operator-c-reference"></a>-&gt;İşleci (C# Başvurusu)
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
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# işleçleri](../../../csharp/language-reference/operators/index.md)
