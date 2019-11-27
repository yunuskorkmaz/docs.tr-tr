---
title: CStr İşlevinin Dönüş Değerleri
ms.date: 07/20/2015
helpviewer_keywords:
- times [Visual Basic], CStr Function return values
- type conversion [Visual Basic]
- dates [Visual Basic], CStr Function return values
- CStr function
- strings [Visual Basic], return value
- Date data type [Visual Basic], converting
- dates [Visual Basic]
- String data type [Visual Basic], converting
ms.assetid: 3aa744e7-1419-45d5-85e3-e5abc2953673
ms.openlocfilehash: 4a40777c7290ec6d8c0d032f2edca5d889e20f04
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349997"
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a>CStr İşlevinin Dönüş Değerleri (Visual Basic)
Aşağıdaki tabloda, `expression`farklı veri türleri için `CStr` için dönüş değerleri açıklanmaktadır.  
  
|`expression` tür|`CStr` döndürür|  
|-----------------------------|--------------------|  
|[Boolean Veri Türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|"True" veya "false" içeren bir dize.|  
|[Date Veri Türü](../../../visual-basic/language-reference/data-types/date-data-type.md)|Sisteminizin kısa tarih biçiminde bir `Date` değeri (Tarih ve saat) içeren bir dize.|  
|[Sayısal Veri Türleri](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|Sayıyı temsil eden bir dize.|  
  
## <a name="cstr-and-date"></a>CStr ve Tarih  
 `Date` türü her zaman hem tarih hem de saat bilgilerini içerir. Tür dönüştürme amaçları doğrultusunda Visual Basic, 1/1/0001 (yıl 1 ' den 1 ' de) tarih için nötr bir *değer* ve 00:00:00 (gece yarısı) zaman için nötr bir değer olacak şekilde değerlendirir. `CStr`, sonuçta elde edilen dizedeki nötr değerler içermez. Örneğin, `#January 1, 0001 9:30:00#` bir dizeye dönüştürürseniz, sonuç "9:30:00" olur. tarih bilgileri bastırılır. Ancak, tarih bilgileri özgün `Date` değerinde hala vardır ve <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>gibi işlevlerle kurtarılabilir.  
  
> [!NOTE]
> `CStr` işlevi, uygulamanın geçerli kültür ayarlarına bağlı olarak dönüşümünü gerçekleştirir. Belirli bir kültürdeki bir sayının dize gösterimini almak için, sayının `ToString(IFormatProvider)` yöntemini kullanın. Örneğin, `Double` türündeki bir değeri bir `String`dönüştürrken <xref:System.Double.ToString%2A?displayProperty=nameWithType> kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>
- [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Boolean Veri Türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [Date Veri Türü](../../../visual-basic/language-reference/data-types/date-data-type.md)
