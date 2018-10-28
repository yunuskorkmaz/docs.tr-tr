---
title: Örtük sayısal dönüşümler tablosu (C# Başvurusu)
ms.date: 09/05/2018
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
ms.openlocfilehash: c3c0153a0ae3e07839822c8bb978b1a09277bd53
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188709"
---
# <a name="implicit-numeric-conversions-table-c-reference"></a>Örtük sayısal dönüşümler tablosu (C# Başvurusu)

Aşağıdaki tablo, .NET sayısal türler arasında önceden tanımlanmış örtük dönüştürmeler gösterir.
  
|Başlangıç|Bitiş|  
|----------|--------|  
|[sbyte](sbyte.md)|`short`, `int`, `long`, `float`, `double`, veya `decimal`|  
|[byte](byte.md)|`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, veya `decimal`|  
|[short](short.md)|`int`, `long`, `float`, `double`, veya `decimal`|  
|[ushort](ushort.md)|`int`, `uint`, `long`, `ulong`, `float`, `double`, veya `decimal`|  
|[int](int.md)|`long`, `float`, `double`, veya `decimal`|  
|[uint](uint.md)|`long`, `ulong`, `float`, `double`, veya `decimal`|  
|[long](long.md)|`float`, `double`, veya `decimal`|  
|[char](char.md)|`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, veya `decimal`|  
|[float](float.md)|`double`|  
|[ulong](ulong.md)|`float`, `double`, veya `decimal`|  
  
## <a name="remarks"></a>Açıklamalar  

- Tüm [integral türü](integral-types-table.md) için örtük olarak dönüştürülebilir [kayan nokta türü](floating-point-types-table.md).

- Duyarlık ancak değil büyüklük kayıp dönüşümlerse içinde `int`, `uint`, `long`, veya `ulong` için `float` ve `long` veya `ulong` için `double`.  
  
- Herhangi bir örtük dönüştürme vardır `char` türü.  
  
- Arasında örtük dönüştürme işlemi yok `float` ve `double` türleri ve `decimal` türü.  
  
- Bir değer türünde sabit bir ifadenin `int` (örneğin, bir tamsayı sabit değeri tarafından temsil edilen bir değer) dönüştürülebilir `sbyte`, `byte`, `short`, `ushort`, `uint`, veya `ulong`, onu sağlanan Hedef türün aralığı içinde:

  ```csharp
  byte a = 13;    // Compiles
  byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

Örtük dönüştürmeleri hakkında daha fazla bilgi için bkz. [örtük dönüştürmelerin](~/_csharplang/spec/conversions.md#implicit-conversions) bölümünü [C# dil belirtimi](../language-specification/index.md).
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [Tam sayı türleri tablosu](integral-types-table.md)
- [Kayan nokta türleri tablosu](floating-point-types-table.md)
- [Yerleşik türler tablosu](built-in-types-table.md)
- [Açık sayısal dönüşümler tablosu](explicit-numeric-conversions-table.md)
- [Atama ve tür dönüştürmeleri](../../programming-guide/types/casting-and-type-conversions.md)
