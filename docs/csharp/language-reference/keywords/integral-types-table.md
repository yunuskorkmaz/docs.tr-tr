---
title: Tam sayı türleri tablosu - C# başvurusu
ms.custom: seodec18
description: Yerleşik C# tamsayı türleri'ne genel bakış
ms.date: 08/20/2018
helpviewer_keywords:
- integral types, C#
- Visual C#, integral types
- types [C#], integral types
- ranges of integral types [C#]
ms.assetid: 62e86126-46ff-40b0-9028-e61d7558268c
ms.openlocfilehash: dc093def716a624162cb695d1151d8a722807094
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61661379"
---
# <a name="integral-types-table-c-reference"></a>Tam sayı türleri tablosu (C# Başvurusu)

Aşağıdaki tabloda, boyutları ve basit türler kümesini oluşturan tam sayı türleri aralığı gösterir.  
  
|Tür|Aralık|Boyut|  
|----------|-----------|----------|  
|[sbyte](sbyte.md)|-128 ila 127 arasında|İşaretli 8 bit tam sayı|  
|[byte](byte.md)|0 ile 255 arasında|İmzalanmamış 8 bit tam sayı|  
|[char](char.md)|U + 0000'u + ffff için|Unicode 16-bit karakteri|  
|[short](short.md)|-32.768 için 32.767|İşaretli 16 bit tam sayı|  
|[ushort](ushort.md)|0 ile 65.535 arasındaki|16 bit işaretsiz tamsayı|  
|[int](int.md)|-2.147.483.648 için 2.147.483.647|İşaretli 32 bit tam sayı|  
|[uint](uint.md)|0 için 4.294.967.295'e|32-bit işaretsiz tamsayı|  
|[long](long.md)|-9,223,372,036,854,775,808 için 9.223.372.036.854.775.807|İşaretli 64 bit tam sayı|  
|[ulong](ulong.md)|0 için 18,446,744,073,709,551,615|64-bit işaretsiz tamsayı|  

## <a name="remarks"></a>Açıklamalar
  
Bir tamsayı sabit değeri tarafından temsil edilen değeri aşarsa <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, bir derleyici hatası [CS1021](../../misc/cs1021.md) gerçekleşir.

Kullanım <xref:System.Numerics.BigInteger?displayProperty=nameWithType> yapısını temsil eden büyük bir işaretli tamsayı.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Türler için başvuru tabloları](reference-tables-for-types.md)
- [Kayan nokta türleri tablosu](floating-point-types-table.md)
- [Varsayılan değerler tablosu](default-values-table.md)
- [Sayısal sonuçlar tablosunu biçimlendirme](formatting-numeric-results-table.md)
- [Yerleşik türler tablosu](built-in-types-table.md)
- [.NET Sayısal Değerleri](../../../standard/numerics.md)
