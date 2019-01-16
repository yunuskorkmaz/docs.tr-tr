---
title: () işleci - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ()_CSharpKeyword
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
ms.openlocfilehash: 656a1ca7a992df43ff857d2c4ecb62b044f7e06f
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333284"
---
# <a name="-operator-c-reference"></a>() işleci (C# Başvurusu)

Bir ifadede işlemlerin sırasını belirlemek için kullanılan ek olarak, parantezler, aşağıdaki görevleri gerçekleştirmek için kullanılır:

1. Atamaları belirtin veya türü dönüşümleri.

    [!code-csharp[csRefOperators#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#1)]

2. Yöntem veya temsilci çağırır.

    [!code-csharp[csRefOperators#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#2)]

## <a name="remarks"></a>Açıklamalar

Bir yayın, bir türden diğerine dönüştürme işleci açıkça çağırır; Böyle bir dönüştürme işleci tanımlanırsa, dönüştürme başarısız. Bir dönüşüm işleci tanımlama için bkz: [açık](../keywords/explicit.md) ve [örtük](../keywords/implicit.md).

 `()` İşleci aşırı yüklenemez.

 Daha fazla bilgi için [atama ve tür dönüşümleri](../../programming-guide/types/casting-and-type-conversions.md).

 Yöntem çağırma hakkında daha fazla bilgi için bkz: [yöntemleri](../../programming-guide/classes-and-structs/methods.md).

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# İşleçleri](index.md)