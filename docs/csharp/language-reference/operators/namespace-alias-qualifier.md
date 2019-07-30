---
title: ':: operator- C# Reference'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ::_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: c494e8dbb18f44ce5520b21800a21d3feb03da59
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631136"
---
# <a name="-operator-c-reference"></a>:: işleci (C# başvuru)

Ad alanı diğer adı niteleyicisi`::`(), tanımlayıcıları aramak için kullanılır. Bu örnekte olduğu gibi her zaman iki tanımlayıcı arasında konumlandırılır:

[!code-csharp[csRefOperators#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#27)]

İşleci bir *using diğer adı yönergesi*ile de kullanılabilir: `::`

```csharp
// using Col=System.Collections.Generic;
var numbers = new Col::List<int> { 1, 2, 3 };
```

## <a name="remarks"></a>Açıklamalar

Ad alanı diğer adı niteleyicisi `global`olabilir. Bu, diğer ad alanı yerine genel ad alanında bir arama çağırır.

## <a name="for-more-information"></a>Daha fazla bilgi için

`::` İşlecinin nasıl kullanılacağına ilişkin bir örnek için aşağıdaki bölüme bakın:

- [Nasıl yapılır: Genel ad alanı diğer adını kullan](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# işleçleri](index.md)
- [. işlecinde](member-access-operators.md#member-access-operator-)
- [extern diğer adı](../keywords/extern-alias.md)
