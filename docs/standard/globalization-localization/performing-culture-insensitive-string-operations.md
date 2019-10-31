---
title: Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme
ms.date: 08/22/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- case mappings
- custom case mappings
- culture, custom sorting rules
- custom sorting rules
- culture-insensitive string operations, options for performing
- culture, custom case mappings
- culture-insensitive string operations, method overloads
ms.assetid: 579ef891-1f83-4c63-9ebd-2f40406b5b91
ms.openlocfilehash: 183078b1f7a3eb3530fea8af06dbb59055d7d25d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120794"
---
# <a name="performing-culture-insensitive-string-operations"></a>Kültüre duyarsız dize işlemlerini gerçekleştirme
Kültüre duyarlı dize işlemleri gerçekleştiren çoğu .NET Framework yöntemi varsayılan olarak, bir <xref:System.Globalization.CultureInfo> parametresi geçirerek kullanılacak kültürü açıkça belirtmenize imkan tanıyan yöntem aşırı yüklemeleri sağlar. Bu aşırı yüklemeler, büyük/küçük harf eşlemeleri ve sıralama kurallarında kültürel değişimlerini ortadan kaldırmanıza ve kültüre duyarsız sonuçların sağlanmasına imkan sağlar  
  
 Bu bölümde, varsayılan olarak kültüre duyarlı .NET Framework yöntemlerini kullanarak kültüre duyarsız dize işlemlerinin nasıl gerçekleştirileceği gösterilmektedir.  
  
## <a name="in-this-section"></a>Bu bölümde  
 [Kültüre Duyarsız Dize Karşılaştırmalarını Gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md)  
 Kültüre duyarsız dize karşılaştırmaları gerçekleştirmek için <xref:System.String.Compare%2A?displayProperty=nameWithType> ve <xref:System.String.CompareTo%2A?displayProperty=nameWithType> yöntemlerinin nasıl kullanılacağını açıklar.  
  
 [Kültüre Duyarsız Büyük/Küçük Harf Değişikliklerini Gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md)  
 <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>ve <xref:System.Char.ToLower%2A?displayProperty=nameWithType> yöntemlerinin kültüre duyarsız büyük/küçük harf değişiklikleri gerçekleştirmek için nasıl kullanılacağını açıklar.  
  
 [Koleksiyonlarda Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)  
 Koleksiyonlarda kültüre duyarsız işlemler gerçekleştirmek için <xref:System.Collections.CaseInsensitiveComparer>, <xref:System.Collections.CaseInsensitiveHashCodeProvider> sınıfı, <xref:System.Collections.SortedList>, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> ve <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> nasıl kullanılacağını açıklar.  
  
 [Dizilerde Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md)  
 Dizilerde kültüre duyarsız işlemler gerçekleştirmek için <xref:System.Array.Sort%2A?displayProperty=nameWithType> ve <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> yöntemlerinin nasıl kullanılacağını açıklar.  
  
## <a name="related-sections"></a>İlgili bölümler  
 [Kültüre Duyarsız Dize İşlemleri](../../../docs/standard/globalization-localization/culture-insensitive-string-operations.md)  
 Dizeler üzerinde işlem gerçekleştirirken kültür için neden farkında olmanız gerektiğini ve kültüre duyarlı işlemlerin ne zaman gerçekleştirileceğini ve kültüre duyarsız işlemlerin ne zaman gerçekleştirileceğini açıklar.

## <a name="see-also"></a>Ayrıca bkz.

- [Sıralama ağırlığı tabloları (Windows sistemlerinde .NET için)](https://www.microsoft.com/download/details.aspx?id=10921)
- [Varsayılan Unicode harmanlama öğesi tablosu (Linux ve macOS 'ta .NET Core için)](https://www.unicode.org/Public/UCA/latest/allkeys.txt)
