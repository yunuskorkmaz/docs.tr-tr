---
description: 'Daha fazla bilgi edinin: System. Convert yöntemleri'
title: System.Convert Yöntemleri
ms.date: 03/30/2017
ms.assetid: 3ca6c5b6-ea5d-4ab0-b675-f082135b342c
ms.openlocfilehash: a323f8d0c3c4a8d1248409d2ec27565acdc58222
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681415"
---
# <a name="systemconvert-methods"></a>System.Convert Yöntemleri

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Aşağıdaki <xref:System.Convert> yöntemleri desteklemez.

- Bir parametre içeren sürümler <xref:System.IFormatProvider> .

- Char dizilerini veya bayt dizilerini içeren Yöntemler:

  - <xref:System.Convert.FromBase64CharArray%2A>

  - <xref:System.Convert.ToBase64CharArray%2A>

  - <xref:System.Convert.FromBase64String%2A>

  - <xref:System.Convert.ToBase64String%2A>

- Aşağıdaki Yöntemler:

  - `public static <Type2> To<Type2>(<Type1> value);` olmadığı

    `Type1``Type2`her biri,, `sbyte` `uint` `ulong` veya `ushort` .

  - C#:

    `int To<int type>(string value, int fromBase),`

    `ToString(... value, int toBase)`

  - Visual Basic:

    `Function To(Of [Numeric])(value as String, fromBase As Integer)`

    `As [Numeric], ToString( value As …, toBase As Integer)`

  - <xref:System.Convert.IsDBNull%2A>

  - <xref:System.Convert.GetTypeCode%2A>

  - <xref:System.Convert.ChangeType%2A>

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Türleri ve İşlevleri](data-types-and-functions.md)
