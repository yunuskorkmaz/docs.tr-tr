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
ms.openlocfilehash: 3653194c7e48533e664ac7513ca7f4f48d1c69f7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819521"
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a>CStr İşlevinin Dönüş Değerleri (Visual Basic)
Dönüş değerleri aşağıdaki tabloda açıklanmıştır `CStr` farklı veri türleri için `expression`.  
  
|Varsa `expression` türü|`CStr` döndürür|  
|-----------------------------|--------------------|  
|[Boolean Veri Türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|"True" içeren bir dize veya "False".|  
|[Date Veri Türü](../../../visual-basic/language-reference/data-types/date-data-type.md)|Bir dizeyi içeren bir `Date` sisteminizin kısa tarih biçiminde bir değer (tarih ve saat).|  
|[Sayısal Veri Türleri](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|Sayısını temsil eden bir dize.|  
  
## <a name="cstr-and-date"></a>CStr ve tarih  
 `Date` Türü her zaman bir tarih ve saat bilgilerini içerir. Tür dönüştürme amacı doğrultusunda, Visual Basic 1/1/0001 (Ocak 1 yılının 1) olarak göz önünde bulundurur bir *bağımsız değer* tarihini ve 00:00:00 (gece yarısı) süresi için bağımsız bir değer olarak. `CStr` nötr değerleri sonuç dizesindeki içermez. Örneğin, dönüştürmek, `#January 1, 0001 9:30:00#` bir dize, "9:30:00 AM" sonucudur; tarih bilgisi bastırılır. Ancak, tarih bilgileri özgün hala mevcut `Date` değeri ve işlevlerinde aşağıdaki gibi kurtarılabilir <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.  
  
> [!NOTE]
>  `CStr` Uygulama için geçerli kültür ayarları göre kendi dönüştürme işlevi görür. Bir sayının dize gösterimini belirli bir kültürün almak için sayının kullanın `ToString(IFormatProvider)` yöntemi. Örneğin, <xref:System.Double.ToString%2A?displayProperty=nameWithType> türünde bir değer dönüştürülürken `Double` için bir `String`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>
- [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Boolean Veri Türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [Date Veri Türü](../../../visual-basic/language-reference/data-types/date-data-type.md)
