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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73120794"
---
# <a name="performing-culture-insensitive-string-operations"></a>Kültüre duyarsız dize işlemleri gerçekleştirme
Varsayılan olarak kültüre duyarlı dize işlemleri gerçekleştiren çoğu .NET Framework yöntemi, bir <xref:System.Globalization.CultureInfo> parametre geçerek kullanılacak kültürü açıkça belirtmenize olanak tanıyan yöntem aşırı yüklemeleri sağlar. Bu aşırı yüklemeler, durum haritalama ve sıralama kurallarındaki kültürel varyasyonları ortadan kaldırmanızı ve kültüre duyarsız sonuçları garanti etmenizi sağlar.  
  
 Bu bölümde, varsayılan olarak kültüre duyarlı .NET Framework yöntemlerini kullanarak kültüre duyarsız dize işlemlerinin nasıl gerçekleştirildiğini göstermek için aşağıdaki konular sağlanmaktadır.  
  
## <a name="in-this-section"></a>Bu bölümde  
 [Kültüre Duyarsız Dize Karşılaştırmalarını Gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md)  
 Kültüre duyarsız <xref:System.String.Compare%2A?displayProperty=nameWithType> dize karşılaştırmaları gerçekleştirmek için yöntemlerin ve <xref:System.String.CompareTo%2A?displayProperty=nameWithType> yöntemlerin nasıl kullanılacağını açıklar.  
  
 [Kültüre Duyarsız Büyük/Küçük Harf Değişikliklerini Gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md)  
 Kültür duyarsız büyük/küçük harf <xref:System.String.ToUpper%2A?displayProperty=nameWithType>değişikliklerini gerçekleştirmek için , , ve <xref:System.String.ToLower%2A?displayProperty=nameWithType> <xref:System.Char.ToUpper%2A?displayProperty=nameWithType> <xref:System.Char.ToLower%2A?displayProperty=nameWithType> yöntemleri nasıl kullanılacağını açıklar.  
  
 [Koleksiyonlarda Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)  
 <xref:System.Collections.CaseInsensitiveComparer>Sınıf, <xref:System.Collections.CaseInsensitiveHashCodeProvider> <xref:System.Collections.SortedList>'ı nasıl kullanacağımı <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> ve <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> koleksiyonlarda kültüre duyarsız işlemleri nasıl gerçekleştireceklerini açıklar.  
  
 [Dizilerde Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md)  
 Diziler halinde <xref:System.Array.Sort%2A?displayProperty=nameWithType> kültüre duyarsız işlemler gerçekleştirmek için yöntemleri ve <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> yöntemleri nasıl kullanacağımı açıklar.  
  
## <a name="related-sections"></a>İlgili bölümler  
 [Kültür-Duyarsız Dize İşlemleri](../../../docs/standard/globalization-localization/culture-insensitive-string-operations.md)  
 Dizeleri üzerinde işlem yaparken kültürün neden farkında olmanız gerektiğini açıklar ve kültüre duyarlı işlemleri ne zaman gerçekleştireceğiniz ve kültüre duyarlı işlemleri ne zaman gerçekleştireceğiniz için yönergeler sağlar.

## <a name="see-also"></a>Ayrıca bkz.

- [Ağırlık Tablolarını Sıralama (Windows sistemlerinde .NET için)](https://www.microsoft.com/download/details.aspx?id=10921)
- [Varsayılan Unicode Collation Element Table (Linux ve macOS'ta .NET Core için)](https://www.unicode.org/Public/UCA/latest/allkeys.txt)
