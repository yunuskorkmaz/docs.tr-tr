---
title: "Örtük Sayısal Dönüşümler Tablosu (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f6b1705dca357fd2a155fc1ea9c7fe0f65bad8a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="implicit-numeric-conversions-table-c-reference"></a>Örtük Sayısal Dönüşümler Tablosu (C# Başvurusu)
Aşağıdaki tabloda önceden tanımlanmış örtük sayısal dönüşümler gösterir. Örtük dönüşümler yöntemi çağırma ve atama deyimleri dahil olmak üzere birçok durumda oluşabilir.  
  
|Başlangıç|Bitiş|  
|----------|--------|  
|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|`short`, `int`, `long`, `float`, `double`, veya`decimal`|  
|[bayt](../../../csharp/language-reference/keywords/byte.md)|`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, veya`decimal`|  
|[kısa](../../../csharp/language-reference/keywords/short.md)|`int`, `long`, `float`, `double`, veya`decimal`|  
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|`int`, `uint`, `long`, `ulong`, `float`, `double`, veya`decimal`|  
|[int](../../../csharp/language-reference/keywords/int.md)|`long`, `float`, `double`, veya`decimal`|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|`long`, `ulong`, `float`, `double`, veya`decimal`|  
|[uzun](../../../csharp/language-reference/keywords/long.md)|`float`, `double`, veya`decimal`|  
|[char](../../../csharp/language-reference/keywords/char.md)|`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, veya`decimal`|  
|[kayan nokta](../../../csharp/language-reference/keywords/float.md)|`double`|  
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|`float`, `double`, veya`decimal`|  
  
## <a name="remarks"></a>Açıklamalar  
  
-   Dönüşümleri içinde duyarlık ancak değil büyüklük kaybedilebilir `int`, `uint`, `long`, veya `ulong` için `float` ve `long` veya `ulong` için `double`.  
  
-   Hiçbir örtük dönüşümler vardır `char` türü.  
  
-   Kayan nokta türleri arasında örtük hiçbir dönüştürme vardır ve `decimal` türü.  
  
-   Sabit bir ifade türü `int` dönüştürülebilir `sbyte`, `byte`, `short`, `ushort`, `uint`, veya `ulong`, sağlanan Hedef aralık içinde sabit ifade değeri yazın.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Tam sayı türleri tablosu](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Yerleşik türler tablosu](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Açık sayısal dönüşümler tablosu](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
 [Atama ve tür dönüşümleri](../../../csharp/programming-guide/types/casting-and-type-conversions.md)
