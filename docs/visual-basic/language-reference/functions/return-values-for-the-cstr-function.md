---
title: CStr için Dönüş Değerleri İşlevi
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
ms.openlocfilehash: cc5e5cc437175e9aebfba559488ca74283faa9ad
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870158"
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a>CStr İşlevinin Dönüş Değerleri (Visual Basic)

Aşağıdaki tabloda, `CStr` farklı veri türleri için dönüş değerleri açıklanmaktadır `expression` .  
  
|Eğer `expression` tür ise|`CStr` döndürdüğü|  
|-----------------------------|--------------------|  
|[Boolean Veri Türü](../data-types/boolean-data-type.md)|"True" veya "false" içeren bir dize.|  
|[Date Veri Türü](../data-types/date-data-type.md)|`Date`Sisteminizin kısa tarih biçiminde bir değer (Tarih ve saat) içeren bir dize.|  
|[Sayısal Veri Türleri](../../programming-guide/language-features/data-types/numeric-data-types.md)|Sayıyı temsil eden bir dize.|  
  
## <a name="cstr-and-date"></a>CStr ve Tarih  

 `Date`Tür her zaman hem tarih hem de saat bilgilerini içerir. Tür dönüştürme amaçları doğrultusunda Visual Basic, 1/1/0001 (yıl 1 ' den 1 ' de) tarih için nötr bir *değer* ve 00:00:00 (gece yarısı) zaman için nötr bir değer olacak şekilde değerlendirir. `CStr` Sonuç dizesinde nötr değerler içermez. Örneğin, `#January 1, 0001 9:30:00#` bir dizeye dönüştürürseniz, sonuç "9:30:00 har" olur; tarih bilgileri bastırılır. Ancak, tarih bilgileri özgün değerde hala bulunur `Date` ve gibi işlevlerle kurtarılabilir <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> .  
  
> [!NOTE]
> `CStr`İşlevi, uygulamanın geçerli kültür ayarlarına bağlı olarak dönüşümünü gerçekleştirir. Belirli bir kültürdeki bir sayının dize gösterimini almak için, sayının `ToString(IFormatProvider)` metodunu kullanın. Örneğin, türünde bir <xref:System.Double.ToString%2A?displayProperty=nameWithType> değer bir değeri olarak dönüştürülürken kullanın `Double` `String` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>
- [Tür Dönüştürme İşlevleri](type-conversion-functions.md)
- [Boolean Veri Türü](../data-types/boolean-data-type.md)
- [Date Veri Türü](../data-types/date-data-type.md)
