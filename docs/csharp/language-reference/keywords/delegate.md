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
ms.openlocfilehash: 7a5f46d137e22da01b2ab6cd3eee57d66c411e8f
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44353479"
---
# <a name="delegate-c-reference"></a>delegate (C# Başvurusu)

Bir temsilci türü bildirimi için bir yöntem imzası benzerdir. Bu, dönüş değeri ve herhangi bir sayıda herhangi bir türde parametreleri vardır:

```csharp
public delegate void TestDelegate(string message);
public delegate int TestDelegate(MyType m, long num);
```

A `delegate` adlandırılmış kapsüllemek için kullanılabilecek bir başvuru türü veya anonim yöntemi. Temsilciler c++ işlev işaretçilerine benzer; Ancak, temsilciler, tür kullanımı uyumlu ve güvenli değildir. Temsilciler uygulamalar için bkz [Temsilciler](../../../csharp/programming-guide/delegates/index.md) ve [genel temsilciler](../../../csharp/programming-guide/generics/generic-delegates.md).

## <a name="remarks"></a>Açıklamalar

Temsilcileri, bir temel [olayları](../../../csharp/programming-guide/events/index.md).

Temsilci adlandırılmış ve anonim bir yöntem ile ilişkilendirerek oluşturulabilir. Daha fazla bilgi için [adlı yöntemleri](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) ve [anonim yöntemler](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).

Uyumlu bir dönüş türü ve giriş parametrelerini içeren bir yöntem veya lambda ifadesiyle, temsilci örneği gerekir. Yöntem imzası izin verilen fark derecesi hakkında daha fazla bilgi için bkz. [Temsilcilerde varyans](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md). Anonim yöntemler ile kullanım için temsilci ve kod ile ilişkilendirilmesi birlikte bildirilir. Her iki yönde örnekleme temsilcilerin, bu bölümde ele alınmıştır.

## <a name="example"></a>Örnek

[!code-csharp[csrefKeywordsTypes#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#8)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
- [Başvuru Türleri](../../../csharp/language-reference/keywords/reference-types.md)  
- [Temsilciler](../../../csharp/programming-guide/delegates/index.md)  
- [Olaylar](../../../csharp/programming-guide/events/index.md)  
- [Temsilcilerin Adlandırılmış ve Anonim Yöntemlerde Karşılaştırılması](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)  
- [Anonim Metotlar](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)
