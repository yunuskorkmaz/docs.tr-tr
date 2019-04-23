---
title: System.Convert Yöntemleri
ms.date: 03/30/2017
ms.assetid: 3ca6c5b6-ea5d-4ab0-b675-f082135b342c
ms.openlocfilehash: 9836820f2c084a80fcc0a4856f20597716344dfd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59480657"
---
# <a name="systemconvert-methods"></a>System.Convert Yöntemleri

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] şunları desteklemez <xref:System.Convert> yöntemleri.

- Sürümleriyle bir <xref:System.IFormatProvider> parametresi.

- Karakter dizileri veya bayt dizileri içeren yöntemler:

  - <xref:System.Convert.FromBase64CharArray%2A>

  - <xref:System.Convert.ToBase64CharArray%2A>

  - <xref:System.Convert.FromBase64String%2A>

  - <xref:System.Convert.ToBase64String%2A>

- Aşağıdaki yöntemleri:

  - `public static <Type2> To<Type2>(<Type1> value);` Burada

    `Type1` ve `Type2` her biri için olan `sbyte`, `uint`, `ulong`, veya `ushort`.

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

- [Veri Türleri ve İşlevleri](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
