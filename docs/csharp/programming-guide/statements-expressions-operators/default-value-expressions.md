---
title: Varsayılan değer ifadeleri (C# programlama Kılavuzu)
description: Varsayılan değer ifadeleri herhangi bir başvuru türü veya değer türü için varsayılan değer üretmek
ms.date: 04/25/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], default keyword
- default keyword [C#], generic programming
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 174ac79c9e2c4a4e628816b1178d420ec7cfc809
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="default-value-expressions-c-programming-guide"></a>Varsayılan değer ifadeleri (C# programlama Kılavuzu)

Varsayılan değer ifadesi `default(T)` türünün varsayılan değeri üretir `T`. Aşağıdaki tabloda, çeşitli türleri için hangi değerlerin üretilen gösterilmektedir:

|Tür|Varsayılan değer|
|---------|---------|
|herhangi bir başvuru türü|`null`|
|Sayısal değer türü|Sıfır|
|[bool](../../language-reference/keywords/bool.md)|`false`|
|[char](../../language-reference/keywords/char.md)|`'\0'`|
|[enum](../../language-reference/keywords/enum.md)|Değeri ifade tarafından üretilen `(E)0`, burada `E` enum tanımlayıcısıdır.|
|[struct](../../language-reference/keywords/struct.md)|Tüm değer tür alanları ayarlayarak üretilen değeri varsayılan değerlerine ve tüm tür alanları için başvuru `null`.|
|Boş değer atanabilir tür|Kendisi için bir örnek <xref:System.Nullable%601.HasValue%2A> özelliği `false` ve <xref:System.Nullable%601.Value%2A> özelliği tanımlanmadı.|

Varsayılan değer ifadeleri Genel sınıflar ve yöntemler özellikle yararlı olur. Genel türler kullanma ortaya bir sorundur parametreli türünde bir varsayılan değer atama `T` zaman bilmediğiniz aşağıdaki önceden:

- Olup olmadığını `T` bir başvuru türü ya da bir değer türü.
- Varsa `T` sayısal bir değer veya yapı olup bir değer türü değil.

 Bir değişken verilen `t` parametreli bir türde `T`, deyim `t = null` yalnızca geçerlidir, `T` bir başvuru türüdür. Atama `t = 0` yalnızca sayısal değer türleri için ancak yapılar için çalışır. Çözmek için varsayılan değer ifadesi kullanın:

```csharp
T t = default(T);
```

`default(T)` İfade Genel sınıflar ve yöntemler için sınırlı değildir. Varsayılan değer ifadeleri ile herhangi bir yönetilen türü kullanılabilir. Bu ifadelerden herhangi biri geçerlidir:

 [!code-csharp[csProgGuideGenerics#1](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-value-expressions.cs)]

 Aşağıdaki örnekte `GenericList<T>` sınıfının nasıl kullanılacağını gösterir `default(T)` genel bir sınıf içinde işleci. Daha fazla bilgi için bkz: [genel türlere giriş](../generics/introduction-to-generics.md).

 [!code-csharp[csProgGuideGenerics#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#Snippet41)]

## <a name="default-literal-and-type-inference"></a>Varsayılan değişmez değer ve tür çıkarımı

C# ile 7.1, başlayarak `default` değişmez değeri derleyici ifade türü çıkarımını, varsayılan değer ifadesi için kullanılabilir. `default` Değişmez değeri üretir eşdeğer olarak aynı değeri `default(T)` burada `T` oluşturulursa türüdür. Bu kodu daha kısa bir türü birden çok kez bildirme artıklık azaltarak yapabilirsiniz. `default` Değişmez değeri aşağıdaki konumlardan herhangi birinde kullanılabilir:

- değişken Başlatıcısı
- değişken ataması
- İsteğe bağlı bir parametre için varsayılan değer bildirme
- için bir yöntem çağrısı bağımsız değişken değeri sağlama
- deyim (veya bir ifade bodied üye ifadesinde) döndürür

Aşağıdaki örnek, birçok kullanım gösterir `default` varsayılan değer ifadesi sabit değer:

[!code-csharp[csProgGuideGenerics#3](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-literal.cs)]

## <a name="see-also"></a>Ayrıca bkz.

 <xref:System.Collections.Generic>  
 [C# Programlama Kılavuzu](../index.md)  
 [Genel türler (C# programlama Kılavuzu)](../generics/index.md)  
 [Genel Yöntemler](../generics/generic-methods.md)  
 [.NET'nda genel türler](~/docs/standard/generics/index.md)  
 [Varsayılan değerler tablosu](../../language-reference/keywords/default-values-table.md)
