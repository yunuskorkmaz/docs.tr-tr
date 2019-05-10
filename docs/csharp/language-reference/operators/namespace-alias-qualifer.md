---
title: ':: işleci - C# başvurusu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ::_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: 324f6711cdec478e5647b05d84c281f79e95f036
ms.sourcegitcommit: 4c10802ad003374641a2c2373b8a92e3c88babc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2019
ms.locfileid: "65452356"
---
# <a name="-operator-c-reference"></a>:: işleci (C# Başvurusu)

Ad alanı diğer ad niteleyicisi (`::`) tanımlayıcıları aramak için kullanılır. Her zaman, bu örnekte olduğu gibi iki tanımlayıcı arasında konumlandırılmış:

[!code-csharp[csRefOperators#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#27)]

`::` İşleci de kullanılabilir olan bir *ALIAS yönergesi kullanarak*:

```csharp
// using Col=System.Collections.Generic;
var numbers = new Col::List<int> { 1, 2, 3 };
```

## <a name="remarks"></a>Açıklamalar

Ad alanı diğer ad niteleyicisi olabilir `global`. Bu genel ad alanı yerine bir diğer adlı ad alanı içinde bir arama başlatır.

## <a name="for-more-information"></a>Daha fazla bilgi için

Nasıl kullanılacağına ilişkin bir örnek `::` işleci, aşağıdaki bölüme bakın:

- [Nasıl yapılır: Genel Namespace diğer adlarını kullanma](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# işleçleri](index.md)
- [Ad Alanı Anahtar Sözcükleri](../keywords/namespace-keywords.md)
- [. işleci](member-access-operators.md#member-access-operator-)
- [extern diğer adı](../keywords/extern-alias.md)