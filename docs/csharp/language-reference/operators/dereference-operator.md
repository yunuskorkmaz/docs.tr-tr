---
title: -&gt; İşleci (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
ms.openlocfilehash: fb95e508ce1339868723bcc3178851e8c1355c1f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43552172"
---
# <a name="-gt-operator-c-reference"></a>-&gt; İşleci (C# Başvurusu)
`->` İşleci, bir araya getirir işaretçi başvurusunun kaldırılması ve üye erişimi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir ifade form  
  
```csharp  
x->y  
```  
  
 (burada `x` bir işaretçi türü `T*` ve `y` üyesi `T`) için eşdeğerdir  
  
```csharp  
(*x).y  
```  
  
 `->` İşleci olarak işaretlenmiş kod kullanılabilir [güvenli](../../../csharp/language-reference/keywords/unsafe.md).  
  
 `->` İşleci aşırı yüklenemez.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csRefOperators#15](../../../csharp/language-reference/operators/codesnippet/CSharp/dereference-operator_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# İşleçleri](../../../csharp/language-reference/operators/index.md)
