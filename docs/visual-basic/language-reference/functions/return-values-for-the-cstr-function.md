---
title: "CStr İşlevinin Dönüş Değerleri (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b498c9b1b7916467c96ed2c645c7131192a5e8b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a>CStr İşlevinin Dönüş Değerleri (Visual Basic)
Dönüş değerleri aşağıdaki tabloda açıklanmaktadır `CStr` farklı veri türleri için `expression`.  
  
|Varsa `expression` türü|`CStr`döndürür|  
|-----------------------------|--------------------|  
|[Boole veri türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|"True" içeren bir dize veya "False".|  
|[Tarih veri türü](../../../visual-basic/language-reference/data-types/date-data-type.md)|Bir dizeyi içeren bir `Date` sisteminizin kısa tarih biçiminde (tarih ve saat) değeri.|  
|[Sayısal veri türleri](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|Sayısını temsil eden bir dize.|  
  
## <a name="cstr-and-date"></a>CStr ve tarihi  
 `Date` Türü her zaman tarih ve saat bilgilerini içerir. Tür dönüşümü amaçları doğrultusunda, Visual Basic 1/1/0001 (Ocak 1 yılının 1) olarak göz önünde bulundurur bir *nötr değeri* tarihini ve 00:00:00 (gece yarısı) süresi dilden bağımsız bir değer olmalıdır. `CStr`dilden bağımsız değerleri sonuç dizesinde içermez. Örneğin, dönüştürmek, `#January 1, 0001 9:30:00#` bir dizeye sonucu "9:30:00 AM"; tarih bilgisini engellenir. Ancak, tarih bilgisini özgün hala mevcut olduğu `Date` değer ve işlevleriyle gibi kurtarılabilir <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.  
  
> [!NOTE]
>  `CStr` İşlevi uygulama için geçerli kültür ayarları göre kendi dönüştürme gerçekleştirir. Bir sayı dize gösterimini içinde belirli bir kültür almak için sayının kullanmak `ToString(IFormatProvider)` yöntemi. Örneğin, <xref:System.Double.ToString%2A?displayProperty=nameWithType> türünde bir değer dönüştürülürken `Double` için bir `String`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>  
 [Tür dönüşüm işlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Boole veri türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md)  
 [Tarih veri türü](../../../visual-basic/language-reference/data-types/date-data-type.md)
