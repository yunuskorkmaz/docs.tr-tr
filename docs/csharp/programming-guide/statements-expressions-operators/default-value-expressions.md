---
title: "Varsayılan değer ifadeleri (C# programlama Kılavuzu)"
description: "Varsayılan değer ifadeleri herhangi bir başvuru türü veya değer türü için varsayılan değer üretmek"
ms.date: 08/23/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], default keyword
- default keyword [C#], generic programming
ms.assetid: b9daf449-4e64-496e-8592-6ed2c8875a98
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c2bb1c269e5347d615c47ab828506aef538c4761
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="default-value-expressions-c-programming-guide"></a>Varsayılan değer ifadeleri (C# programlama Kılavuzu)

Varsayılan değer ifadesi bir tür için varsayılan değer oluşturur. Varsayılan değer ifadeleri Genel sınıflar ve yöntemler özellikle yararlı olur. Genel türler kullanma ortaya bir sorundur parametreli türü için varsayılan bir değer atamak nasıl `T` değil bildiğinizde aşağıdaki önceden:

- Olup olmadığını `T` bir başvuru türü ya da bir değer türü.
- Varsa `T` bir değer türü sayısal bir değer veya kullanıcı tanımlı bir yapı olup olmadığı.

 Bir değişken verilen `t` parametreli bir türde `T`, deyim `t = null` yalnızca geçerlidir, `T` bir başvuru türüdür. Atama `t = 0` yalnızca sayısal değer türleri için ancak yapılar için çalışır. Çözüm döndüren bir varsayılan değer ifadesi kullanmaktır `null` başvuru türleri (sınıf ve arabirim türlerini) ve sıfır sayısal değer türleri için. İsteğe bağlı olarak kullanıcı tanımlı yapılar için 0 üreten sıfır bit düzeni için başlatılan yapısı döndürür veya `null` bu üye bir değer veya başvuru türünde olup olmamasına bağlı olarak her üye için. Boş değer atanabilen değer türleri için `default` döndüren bir <xref:System.Nullable%601?displayProperty=nameWithType>, gibi herhangi bir yapı başlatıldı.

`default(T)` İfade Genel sınıflar ve yöntemler için sınırlı değildir. Varsayılan değer ifadeleri ile herhangi bir yönetilen türü kullanılabilir. Bu ifadelerden herhangi biri geçerlidir:

 [!code-csharp[csProgGuideGenerics#1](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-value-expressions.cs)]

 Aşağıdaki örnekte `GenericList<T>` sınıfının nasıl kullanılacağını gösterir `default(T)` genel bir sınıf içinde işleci. Daha fazla bilgi için bkz: [genel türler genel bakış](../generics/introduction-to-generics.md).

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

 <xref:System.Collections.Generic>[C# programlama kılavuzu](../index.md)  
 [Genel türler](../generics/index.md)  
 [Genel yöntemler](../generics/generic-methods.md)  
 [Genel türler](~/docs/standard/generics/index.md)  
