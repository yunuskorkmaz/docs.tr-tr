---
title: delegate (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- delegate_CSharpKeyword
- delegate
- CS0123
helpviewer_keywords:
- delegate keyword [C#]
- function pointers [C#]
ms.assetid: 0bb8cb6d-2f87-47c7-9d1f-d65c1cd01e9f
ms.openlocfilehash: ba1cfdcc56b3d2301a07ffa4af793e7002da21bb
ms.sourcegitcommit: ed7b4b9b77d35e94a35a2634e8c874f46603fb2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36948429"
---
# <a name="delegate-c-reference"></a>delegate (C# Başvurusu)

Bir temsilci türü bildirimi yöntemi imza benzer. Dönüş değeri ve parametreleri herhangi bir türde herhangi bir sayıda sahiptir:

```csharp
public delegate void TestDelegate(string message);
public delegate int TestDelegate(MyType m, long num);
```

A `delegate` adlandırılmış kapsüllemek için kullanılan bir başvuru türü veya anonim bir yöntem. C++'ta işlev işaretçileri temsilciler benzer; Ancak, temsilciler tür kullanımı uyumlu ve güvenli değildir. Temsilciler uygulamalar için bkz [Temsilciler](../../../csharp/programming-guide/delegates/index.md) ve [genel temsilciler](../../../csharp/programming-guide/generics/generic-delegates.md).

## <a name="remarks"></a>Açıklamalar

Temsilciler olan temelini [olayları](../../../csharp/programming-guide/events/index.md).

Bir temsilci, herhangi bir adlandırılmış ve anonim yöntemi ile ilişkilendirerek oluşturulabilir. Daha fazla bilgi için bkz: [adlı yöntemleri](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) ve [anonim yöntemler](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).

Temsilci uyumlu bir dönüş türü ve giriş parametreleri olan bir yöntem veya lambda ifadesi ile örneğinin oluşturulması gerekir. Yöntem imzası izin farkı derecesini hakkında daha fazla bilgi için bkz: [Temsilcilerde varyans](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md). Anonim yöntemler ile kullanım için temsilci ve kod ile ilişkilendirilmesi birlikte bildirilir. Her iki yönde temsilcilerin örnek oluşturma, bu bölümde ele alınmıştır.

## <a name="example"></a>Örnek

[!code-csharp[csrefKeywordsTypes#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#8)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

[C# başvurusu](../../../csharp/language-reference/index.md)  
[C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
[C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
[Başvuru Türleri](../../../csharp/language-reference/keywords/reference-types.md)  
[Temsilciler](../../../csharp/programming-guide/delegates/index.md)  
[Olaylar](../../../csharp/programming-guide/events/index.md)  
[Temsilcilerin Adlandırılmış ve Anonim Yöntemlerde Karşılaştırılması](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)  
[Anonim Metotlar](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)
