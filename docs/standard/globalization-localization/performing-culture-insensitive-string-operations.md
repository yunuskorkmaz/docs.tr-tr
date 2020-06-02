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
ms.openlocfilehash: 79ff899e2964ae2c1e90b7178616c612dddf6d86
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287512"
---
# <a name="performing-culture-insensitive-string-operations"></a>Kültüre duyarsız dize işlemlerini gerçekleştirme
Kültüre duyarlı dize işlemleri gerçekleştiren çoğu .NET Framework yöntemi varsayılan olarak, bir parametre geçirerek kullanılacak kültürü açıkça belirtmenize imkan tanıyan yöntem aşırı yüklemeleri sağlar <xref:System.Globalization.CultureInfo> . Bu aşırı yüklemeler, büyük/küçük harf eşlemeleri ve sıralama kurallarında kültürel değişimlerini ortadan kaldırmanıza ve kültüre duyarsız sonuçların sağlanmasına imkan sağlar  
  
 Bu bölümde, varsayılan olarak kültüre duyarlı .NET Framework yöntemlerini kullanarak kültüre duyarsız dize işlemlerinin nasıl gerçekleştirileceği gösterilmektedir.  
  
## <a name="in-this-section"></a>Bu bölümde  
 [Kültüre Duyarsız Dize Karşılaştırmalarını Gerçekleştirme](performing-culture-insensitive-string-comparisons.md)  
 <xref:System.String.Compare%2A?displayProperty=nameWithType>Ve <xref:System.String.CompareTo%2A?displayProperty=nameWithType> yöntemlerinin kültüre duyarsız dize karşılaştırmaları gerçekleştirmek için nasıl kullanılacağını açıklar.  
  
 [Kültüre Duyarsız Büyük/Küçük Harf Değişikliklerini Gerçekleştirme](performing-culture-insensitive-case-changes.md)  
 <xref:System.String.ToUpper%2A?displayProperty=nameWithType> <xref:System.String.ToLower%2A?displayProperty=nameWithType> <xref:System.Char.ToUpper%2A?displayProperty=nameWithType> <xref:System.Char.ToLower%2A?displayProperty=nameWithType> Kültüre duyarsız büyük/küçük harf değişiklikleri gerçekleştirmek için,, ve yöntemlerinin nasıl kullanılacağını açıklar.  
  
 [Koleksiyonlarda Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme](performing-culture-insensitive-string-operations-in-collections.md)  
 <xref:System.Collections.CaseInsensitiveComparer> <xref:System.Collections.CaseInsensitiveHashCodeProvider> <xref:System.Collections.SortedList> <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> Koleksiyonlarda kültüre duyarsız işlemler gerçekleştirmek için,, sınıfının ve ' nin nasıl kullanılacağını açıklar.  
  
 [Dizilerde Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme](performing-culture-insensitive-string-operations-in-arrays.md)  
 <xref:System.Array.Sort%2A?displayProperty=nameWithType>Ve <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> yöntemlerinin, diziler içinde kültüre duyarsız işlemler gerçekleştirmek için nasıl kullanılacağını açıklar.  
  
## <a name="related-sections"></a>İlgili bölümler  
 [Kültüre duyarsız dize Işlemleri](culture-insensitive-string-operations.md)  
 Dizeler üzerinde işlem gerçekleştirirken kültür için neden farkında olmanız gerektiğini ve kültüre duyarlı işlemlerin ne zaman gerçekleştirileceğini ve kültüre duyarsız işlemlerin ne zaman gerçekleştirileceğini açıklar.

## <a name="see-also"></a>Ayrıca bkz.

- [Sıralama ağırlığı tabloları (Windows sistemlerinde .NET için)](https://www.microsoft.com/download/details.aspx?id=10921)
- [Varsayılan Unicode harmanlama öğesi tablosu (Linux ve macOS 'ta .NET Core için)](https://www.unicode.org/Public/UCA/latest/allkeys.txt)
