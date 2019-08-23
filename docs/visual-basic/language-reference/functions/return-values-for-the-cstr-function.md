---
title: CStr İşlevinin Dönüş Değerleri (Visual Basic)
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
ms.openlocfilehash: cd525ea5a295411e509f3bc37285675d15a8c4f4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930043"
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a>CStr İşlevinin Dönüş Değerleri (Visual Basic)
Aşağıdaki tabloda, farklı veri `CStr` `expression`türleri için dönüş değerleri açıklanmaktadır.  
  
|Eğer `expression` tür ise|`CStr`döndürdüğü|  
|-----------------------------|--------------------|  
|[Boolean Veri Türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|"True" veya "false" içeren bir dize.|  
|[Date Veri Türü](../../../visual-basic/language-reference/data-types/date-data-type.md)|Sisteminizin kısa tarih biçiminde `Date` bir değer (Tarih ve saat) içeren bir dize.|  
|[Sayısal Veri Türleri](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|Sayıyı temsil eden bir dize.|  
  
## <a name="cstr-and-date"></a>CStr ve Tarih  
 `Date` Tür her zaman hem tarih hem de saat bilgilerini içerir. Tür dönüştürme amaçları doğrultusunda Visual Basic, 1/1/0001 (yıl 1 ' den 1 ' de) tarih için nötr bir *değer* ve 00:00:00 (gece yarısı) zaman için nötr bir değer olacak şekilde değerlendirir. `CStr`Sonuç dizesinde nötr değerler içermez. Örneğin, bir dizeye dönüştürürseniz `#January 1, 0001 9:30:00#` , sonuç "9:30:00 har" olur; tarih bilgileri bastırılır. Ancak, tarih bilgileri özgün `Date` değerde hala bulunur ve gibi işlevlerle <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>kurtarılabilir.  
  
> [!NOTE]
> `CStr` İşlevi, uygulamanın geçerli kültür ayarlarına bağlı olarak dönüşümünü gerçekleştirir. Belirli bir kültürdeki bir sayının dize gösterimini almak için, sayının `ToString(IFormatProvider)` metodunu kullanın. Örneğin, türünde `Double` bir <xref:System.Double.ToString%2A?displayProperty=nameWithType> değer bir `String`değeri olarak dönüştürülürken kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>
- [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Boolean Veri Türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [Date Veri Türü](../../../visual-basic/language-reference/data-types/date-data-type.md)
