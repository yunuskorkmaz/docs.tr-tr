---
title: Örtük sayısal dönüşümler tablosu - C# başvurusu
ms.custom: seodec18
ms.date: 09/05/2018
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
ms.openlocfilehash: 516505ccacfd2a8a5c275b0de033e1316fa06d3a
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661325"
---
# <a name="implicit-numeric-conversions-table-c-reference"></a>Örtük sayısal dönüşümler tablosu (C# Başvurusu)

Aşağıdaki tablo, .NET sayısal türler arasında önceden tanımlanmış örtük dönüştürmeler gösterir.
  
|Başlangıç|Bitiş|  
|----------|--------|  
|[sbyte](../builtin-types/integral-numeric-types.md)|`short`, `int`, `long`, `float`, `double`, veya `decimal`|  
|[byte](../builtin-types/integral-numeric-types.md)|`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, veya `decimal`|  
|[char](char.md)|`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, veya `decimal`|  
|[short](../builtin-types/integral-numeric-types.md)|`int`, `long`, `float`, `double`, veya `decimal`|  
|[ushort](../builtin-types/integral-numeric-types.md)|`int`, `uint`, `long`, `ulong`, `float`, `double`, veya `decimal`|  
|[int](../builtin-types/integral-numeric-types.md)|`long`, `float`, `double`, veya `decimal`|  
|[uint](../builtin-types/integral-numeric-types.md)|`long`, `ulong`, `float`, `double`, veya `decimal`|  
|[long](../builtin-types/integral-numeric-types.md)|`float`, `double`, veya `decimal`|  
|[ulong](../builtin-types/integral-numeric-types.md)|`float`, `double`, veya `decimal`|  
|[float](../builtin-types/floating-point-numeric-types.md)|`double`|  
  
## <a name="remarks"></a>Açıklamalar  

- Tüm [integral türü](../builtin-types/integral-numeric-types.md) için örtük olarak dönüştürülebilir [kayan nokta türü](../builtin-types/floating-point-numeric-types.md).

- Duyarlık ancak değil büyüklük kayıp dönüşümlerse içinde `int`, `uint`, `long`, veya `ulong` için `float` ve `long` veya `ulong` için `double`.  
  
- Herhangi bir örtük dönüştürme vardır `char`, `byte`, ve `sbyte` türleri.  

- Öğesinden örtük dönüştürme işlemi yok `double` ve `decimal` türleri.
  
- Arasında örtük dönüştürme işlemi yok `decimal` türü ve `float` veya `double` türleri.  
  
- Bir değer türünde sabit bir ifadenin `int` (örneğin, bir tamsayı sabit değeri tarafından temsil edilen bir değer) dönüştürülebilir `sbyte`, `byte`, `short`, `ushort`, `uint`, veya `ulong`, onu sağlanan Hedef türün aralığı içinde:

  ```csharp
  byte a = 13;    // Compiles
  byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

Örtük dönüştürmeleri hakkında daha fazla bilgi için bkz. [örtük dönüştürmelerin](~/_csharplang/spec/conversions.md#implicit-conversions) bölümünü [C# dil belirtimi](../language-specification/index.md).
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [Tam sayı türleri](../builtin-types/integral-numeric-types.md)
- [Kayan nokta türleri tablosu](../builtin-types/floating-point-numeric-types.md)
- [Yerleşik türler tablosu](built-in-types-table.md)
- [Açık sayısal dönüşümler tablosu](explicit-numeric-conversions-table.md)
- [Atama ve tür dönüştürmeleri](../../programming-guide/types/casting-and-type-conversions.md)
