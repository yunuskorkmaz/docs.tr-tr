---
title: Varsayılan değer ifadeleri (C# programlama Kılavuzu)
description: Varsayılan değer ifadeleri herhangi bir başvuru türü veya değer türü için varsayılan değer üretir.
ms.date: 04/25/2018
helpviewer_keywords:
- generics [C#], default keyword
- default keyword [C#], generic programming
ms.openlocfilehash: 94866f22fb3ad921a834cffb16fe17e44cef5965
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47192634"
---
# <a name="default-value-expressions-c-programming-guide"></a>Varsayılan değer ifadeleri (C# programlama Kılavuzu)

Varsayılan değer ifadesi `default(T)` bir türünün varsayılan değerini üretir `T`. Aşağıdaki tabloda, çeşitli türleri için hangi değerlerin üretilen gösterilmektedir:

|Tür|Varsayılan değer|
|---------|---------|
|herhangi bir başvuru türü|`null`|
|Sayısal değer türü|Sıfır|
|[bool](../../language-reference/keywords/bool.md)|`false`|
|[char](../../language-reference/keywords/char.md)|`'\0'`|
|[enum](../../language-reference/keywords/enum.md)|Değer ifade tarafından üretilen `(E)0`burada `E` numaralandırma tanımlayıcı.|
|[struct](../../language-reference/keywords/struct.md)|Tüm değer tür alanları ayarlayarak üretilen değer varsayılan değerlerine ve tüm tür alanları için başvuru `null`.|
|Boş değer atanabilir tür|Bir örneğin <xref:System.Nullable%601.HasValue%2A> özelliği `false` ve <xref:System.Nullable%601.Value%2A> özelliği tanımsız.|

Varsayılan değer ifadeleri Genel sınıflar ve yöntemler özellikle yararlı olur. Genel türler kullanarak ortaya bir sorundur parametreli bir türde bir varsayılan değer atama `T` zaman bilmediğiniz aşağıdaki önceden:

- Olmadığını `T` bir başvuru türü veya değer türü.
- Varsa `T` sayısal bir değer veya bir yapı olup bir değer türüdür.

 Bir değişken verilen `t` parametreli bir türün `T`, deyim `t = null` yalnızca geçerli olduğundan, `T` bir başvuru türüdür. Atama `t = 0` yalnızca sayısal değer türleri için ancak değil yapı birimleri için çalışır. Bu durumu çözmek için varsayılan değer ifadesi kullanın:

```csharp
T t = default(T);
```

`default(T)` İfade Genel sınıflar ve yöntemler için sınırlı değildir. Varsayılan değer ifadeleri herhangi bir yönetilen türü ile kullanılabilir. Bu ifadelerden herhangi biri geçerlidir:

 [!code-csharp[csProgGuideGenerics#1](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-value-expressions.cs)]

 Aşağıdaki örnekte `GenericList<T>` sınıfının nasıl kullanılacağını göstermektedir `default(T)` genel bir sınıf içinde işleci. Daha fazla bilgi için [genel türlere giriş](../generics/introduction-to-generics.md).

 [!code-csharp[csProgGuideGenerics#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#Snippet41)]

## <a name="default-literal-and-type-inference"></a>Varsayılan değişmez değer ve tür çıkarımı

C# 7.1, ile başlayan `default` değişmez değeri derleyici ifade türünü çıkarabilir, varsayılan değer ifadeleri toplama için kullanılabilir. `default` Değişmez değer üreten denk olarak aynı değeri `default(T)` burada `T` çıkarsanan tür. Bu kod daha kısa bir türü birden çok kez bildirmek, fazlalıkları azaltarak yapabilirsiniz. `default` Değişmez değeri aşağıdaki konumlardan herhangi birinde kullanılabilir:

- değişken başlatıcı
- değişken ataması
- İsteğe bağlı bir parametre için varsayılan değer bildirme
- için bir yöntem çağrısı bağımsız değişken olarak değer sunuyor
- deyimi (veya bir ifade bodied üye ifadesinde) döndürür

Aşağıdaki örnekte, fazla kullanımlar `default` varsayılan değer ifadesi sabit değer:

[!code-csharp[csProgGuideGenerics#3](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-literal.cs)]

## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Collections.Generic>  
- [C# Programlama Kılavuzu](../index.md)  
- [Genel türler (C# programlama Kılavuzu)](../generics/index.md)  
- [Genel Yöntemler](../generics/generic-methods.md)  
- [.NET içindeki genel türler](~/docs/standard/generics/index.md)  
- [Varsayılan değerler tablosu](../../language-reference/keywords/default-values-table.md)
