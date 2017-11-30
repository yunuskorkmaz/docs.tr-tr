---
title: "char (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords: char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
caps.latest.revision: "27"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 41f672e9b12481fa5cce78015e95d2c5245a26db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="char-c-reference"></a>char (C# Başvurusu)
`char` Örneği bildirmek için kullanılan anahtar sözcüğü <xref:System.Char?displayProperty=nameWithType> Unicode karakteri temsil etmesi için .NET Framework kullanan yapısı. Değeri bir `Char` nesnesi bir 16 bit sayısal (sıra) değerdir.  
  
 Unicode karakterler, dünyanın her yazılı dilleri çoğunu göstermek için kullanılır.  
  
|Tür|Aralık|Boyut|.NET Framework türü|  
|----------|-----------|----------|-------------------------|  
|`char`|U + U + FFFF 0000|Unicode 16 bit karakter|<xref:System.Char?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Sabit değerler  
 Sabitleri `char` türü karakter değişmez değerleri, onaltılık çıkış dizisi veya Unicode gösterimi yazılabilir. Ayrıca, tam sayı karakter kodları çevirebilirsiniz. Aşağıdaki örnekte dört `char` değişkenleri aynı karakterle başlatılmış `X`:  
  
 [!code-csharp[csrefKeywordsTypes#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/char_1.cs)]  
  
## <a name="conversions"></a>Dönüşümler  
 A `char` örtük olarak dönüştürülebilir [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [uzun](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md) , [float](../../../csharp/language-reference/keywords/float.md), [çift](../../../csharp/language-reference/keywords/double.md), veya [ondalık](../../../csharp/language-reference/keywords/decimal.md). Ancak, diğer türlerinden hiçbir örtük dönüşümler vardır `char` türü.  
  
 <xref:System.Char?displayProperty=nameWithType> Türü ile çalışmak için birkaç statik yöntemler sağlar `char` değerleri.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Char>  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Tam sayı türleri tablosu](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Yerleşik türler tablosu](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Örtük sayısal dönüşümler tablosu](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [Açık sayısal dönüşümler tablosu](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
 [Boş değer atanabilir türler](../../../csharp/programming-guide/nullable-types/index.md)  
 [Dizeleri](../../../csharp/programming-guide/strings/index.md)
