---
title: İlkel Türler (F#)
description: 'F # dilinde kullanılan temel ilkel türler bulur.'
ms.date: 05/16/2016
ms.openlocfilehash: efe419e5ebf2e49be9433bbd3025ff290d648296
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="primitive-types"></a>İlkel Türler

Bu konu F # dilinde kullanılan temel ilkel türlerini listeler. Ayrıca karşılık gelen .NET türleri ve minimum ve maksimum değerleri her tür için sağlar.

## <a name="summary-of-primitive-types"></a>İlkel türler özeti
Aşağıdaki tabloda temel F # türleri özelliklerini özetler.

|Tür|.NET türü|Açıklama|
|----|---------|-----------|
|`bool`|`System.Boolean`|Olası değerler şunlardır: `true` ve `false`.|
|`byte`|`System.Byte`|0 ile 255 değerleri.|
|`sbyte`|`System.SByte`|127 -128 değerleri.|
|`int16`|`System.Int16`|-32768 değerleri ile 32767 arasında.|
|`uint16`|`System.UInt16`|0 ile 65535 değerleri.|
|`int`|`System.Int32`|2.147.483.647 değerleri 2,147,483,648.|
|`uint32`|`System.UInt32`|4.294.967.295 için değerleri 0.|
|`int64`|`System.Int64`|9,223,372,036,854,775,807 için-9,223,372,036,854,775,808 değerleri.|
|`uint64`|`System.UInt64`|18,446,744,073,709,551,615 için değerleri 0.|
|`nativeint`|`System.IntPtr`|İmzalı bir tamsayı olarak yerel bir işaretçi.|
|`unativeint`|`System.UIntPtr`|İmzalanmamış tamsayı olarak yerel bir işaretçi.|
|`char`|`System.Char`|Unicode karakter değerleri.|
|`string`|`System.String`|Unicode metin.|
|`decimal`|`System.Decimal`|Kayan nokta en az 28 basamaktan oluşur veri türü.|
|`unit`|Geçerli değil|Gerçek bir değer yokluğu gösterir. Gösterilir tek bir resmi değer türüne sahip `()`. Birim değeri `()`, çoğunlukla burada bir değer gerekli ancak herhangi bir gerçek değer kullanılabilir veya anlamlı bir yer tutucu olarak kullanılır.|
|`void`|`System.Void`|Hiçbir tür veya değeri gösterir.|
|`float32, single`|`System.Single`|Bir 32 bit kayan nokta türü.|
|`float, double`|`System.Double`|Bir 64-bit kayan nokta türü.|

>[!NOTE]
Kullanarak 64-bit tamsayı türü için çok büyük tamsayılı hesaplamalar gerçekleştirebilirsiniz [bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa) türü. `bigint` Basit tür olarak kabul edilmez; ifadesinin kısaltmasıdır `System.Numerics.BigInteger`.

## <a name="see-also"></a>Ayrıca Bkz.
[F# Dili Başvurusu](index.md)
