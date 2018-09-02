---
title: ':: İşleci (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- ::_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: 077d5835b372897cbe797385271effc5d00bf6e3
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43473979"
---
# <a name="-operator-c-reference"></a>:: İşleci (C# Başvurusu)
Ad alanı diğer ad niteleyicisi (`::`) tanımlayıcıları aramak için kullanılır. Her zaman, bu örnekte olduğu gibi iki tanımlayıcı arasında konumlandırılmış:  
  
 [!code-csharp[csRefOperators#27](../../../csharp/language-reference/operators/codesnippet/CSharp/namespace-alias-qualifer_1.cs)]  

`::` İşleci de kullanılabilir olan bir *ALIAS yönergesi kullanarak*:

```csharp
// using Col=System.Collections.Generic;
var numbers = new Col::List<int> { 1, 2, 3 };
```

## <a name="remarks"></a>Açıklamalar  
 Ad alanı diğer ad niteleyicisi olabilir `global`. Bu genel ad alanı yerine bir diğer adlı ad alanı içinde bir arama başlatır.  
  
## <a name="for-more-information"></a>Daha Fazla Bilgi İçin  
 Nasıl kullanılacağına ilişkin bir örnek `::` işleci, aşağıdaki bölüme bakın:  
  
-   [Nasıl yapılır: Genel Ad Alanı Diğer Adlarını Kullanma](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# İşleçleri](../../../csharp/language-reference/operators/index.md)  
- [Ad Alanı Anahtar Sözcükleri](../../../csharp/language-reference/keywords/namespace-keywords.md)  
- [. İşleç](../../../csharp/language-reference/operators/member-access-operator.md)  
- [extern diğer adı](../../../csharp/language-reference/keywords/extern-alias.md)
