---
title: Boş değer atanabilir türler (C# programlama Kılavuzu)
description: C# boş değer atanabilir türleri ve bunların nasıl kullanıldığı hakkında bilgi edinin
ms.date: 07/30/2018
helpviewer_keywords:
- nullable types [C#]
- C# language, nullable types
- types [C#], nullable
ms.assetid: e473cb01-28ca-42be-9cea-f717055d72c6
ms.openlocfilehash: 2af0704abcad00c75a5d40bfe2d0523d07ee6a3f
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44700813"
---
# <a name="nullable-types-c-programming-guide"></a>Boş değer atanabilir türler (C# programlama Kılavuzu)

Boş değer atanabilir türler örnekleridir <xref:System.Nullable%601?displayProperty=nameWithType> yapısı. Boş değer atanabilir türler bir temel türünün tüm değerleri temsil eden `T`ve ek [null](../../language-reference/keywords/null.md) değeri. Temel alınan türü `T` alamayan herhangi olabilir [değer türü](../../language-reference/keywords/value-types.md). `T` bir başvuru türü olamaz.

Örneğin, atayabilirsiniz `null` veya tamsayı değerdeki <xref:System.Int32.MinValue?displayProperty=nameWithType> için <xref:System.Int32.MaxValue?displayProperty=nameWithType> için bir `Nullable<int>` ve [true](../../language-reference/keywords/true-literal.md), [false](../../language-reference/keywords/false-literal.md), veya `null` için bir `Nullable<bool>`.

Boş değer atanabilir bir tür, bir temel türü tanımlanmamış değerini temsil etmek, ihtiyacınız olduğunda kullanın. Bir Boolean değişkeni yalnızca iki değere sahip olabilir: true ve false. "Tanımlanmamış" değer yoktur. Birçok programlama uygulamada, bir değişken değeri en önemlisi veritabanı etkileşimleri tanımsız veya eksik olabilir. Örneğin, bir veritabanındaki bir alanı true veya false değerleri içerebilir veya hiç değer içerebilir. Kullandığınız bir `Nullable<bool>` durumda yazın.

Boş değer atanabilir türler aşağıdaki özelliklere sahiptir:
  
- Boş değer atanabilir türleri temsil eden atanabilir değer türü değişkenler `null` değeri. Bir başvuru türüne göre boş değer atanabilir bir tür oluşturulamıyor. (Başvuru türleri halihazırda desteklediği `null` değeri.)  
  
- Söz dizimi `T?` için toplu özelliktir `Nullable<T>`. İki tür birbirinin yerine kullanılabilir.  
  
- Temel alınan bir değer türü için yaptığınız gibi boş değer atanabilir bir tür için bir değer atayın: `int? x = 10;` veya `double? d = 4.108;`. Ayrıca atayabilirsiniz `null` değer: `int? x = null;`.  
  
- Kullanım <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> ve <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> salt okunur özellikler için null test etmek ve değerini, aşağıdaki örnekte gösterildiği gibi almak için: `if (x.HasValue) y = x.Value;`  
  
  - <xref:System.Nullable%601.HasValue%2A> Özelliği döndürür `true` değişken bir değer içeriyorsa veya `false` ise `null`.
  
  - <xref:System.Nullable%601.Value%2A> Özelliği, bir değer döndürür <xref:System.Nullable%601.HasValue%2A> döndürür `true`. Aksi takdirde, bir <xref:System.InvalidOperationException> oluşturulur.  
  
- Ayrıca `==` ve `!=` işleçleri aşağıdaki örnekte gösterildiği gibi boş değer atanabilir bir tür ile: `if (x != null) y = x.Value;`. Varsa `a` ve `b` her ikisi de null olan `a == b` değerlendiren `true`.  

- Kullanabileceğiniz C# 7.0 ile başlayarak, [desen eşleştirme](../../pattern-matching.md#the-is-type-pattern-expression) hem incelemek ve boş değer atanabilir bir tür değerini almak için: `if (x is int valueOfX) y = valueOfX;`.
  
- Varsayılan değer olan `T?` bir örneği olan <xref:System.Nullable%601.HasValue%2A> özelliği döndürür `false`.  

- Kullanım <xref:System.Nullable%601.GetValueOrDefault> ya da atanan değer döndürmek için yöntemi veya [varsayılan](../../language-reference/keywords/default-values-table.md) değer boş değer atanabilir türde ise temel değer türünün `null`.  

- Kullanım <xref:System.Nullable%601.GetValueOrDefault(%600)> atanan değer veya sağlanan varsayılan değer boş değer atanabilir tür değeri ise döndürülecek yöntemi `null`.
  
- Kullanım [null birleşim işleci](../../language-reference/operators/null-coalescing-operator.md), `??`, boş değer atanabilir türde bir değere göre bir temel türü bir değer atamak için: `int? x = null; int y = x ?? -1;`. Örnekte, bu yana `x` null, sonuç değeri olan `y` olduğu `-1`.

- Bir kullanıcı tanımlı dönüştürme iki veri türleri arasında tanımlıysa, bu veri türlerini boş değer atanabilir sürümleriyle aynı dönüştürme de kullanılabilir.
  
- İç içe geçmiş boş değer atanabilir türler izin verilmez. Aşağıdaki satırı derleme değil: `Nullable<Nullable<int>> n;`  

Daha fazla bilgi için [boş değer atanabilir türleri kullanma](using-nullable-types.md) ve [nasıl yapılır: boş değer atanabilir bir tür belirleme](how-to-identify-a-nullable-type.md) konuları.
  
## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Nullable%601?displayProperty=nameWithType>  
- <xref:System.Nullable?displayProperty=nameWithType>  
- [?? İşleç](../../language-reference/operators/null-coalescing-operator.md)  
- [C# Programlama Kılavuzu](../index.md)  
- [C# Kılavuzu](../../index.md)  
- [C# başvurusu](../../language-reference/index.md)  
- [Boş değer atanabilen değer türleri (Visual Basic)](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
