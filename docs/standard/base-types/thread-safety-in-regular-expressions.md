---
title: Normal İfadelerde İş Parçacığı Güvenliği
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET Framework regular expressions, threads
- regular expressions, threads
- searching with regular expressions, threads
- parsing text with regular expressions, threads
- pattern-matching with regular expressions, threads
ms.assetid: 7c4a167b-5236-4cde-a2ca-58646230730f
ms.openlocfilehash: db25028e10872cfca08d28518c795414d06c5d49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73124793"
---
# <a name="thread-safety-in-regular-expressions"></a>Normal İfadelerde İş Parçacığı Güvenliği
Sınıfın <xref:System.Text.RegularExpressions.Regex> kendisi iş parçacığı güvenli ve değişmez (salt okunur). Diğer bir diğer nokta, **Regex** nesneleri herhangi bir iş parçacığı üzerinde oluşturulabilir ve iş parçacıkları arasında paylaşılabilir; eşleşen yöntemler herhangi bir iş parçacığı çağrılabilir ve herhangi bir küresel durumu değiştirmek asla.  
  
 Ancak, **Regex** tarafından döndürülen sonuç nesneleri **(Match** ve **MatchCollection)** tek bir iş parçacığı üzerinde kullanılmalıdır. Bu nesnelerin çoğu mantıksal olarak değişmez olsa da, uygulamaları performansı artırmak için bazı sonuçların hesaplanmasını geciktirebilir ve sonuç olarak arayanların bunlara erişimi seri hale getirmelidir.  
  
 **Regex** sonuç nesnelerini birden çok iş parçacığı üzerinde paylaşma ihtiyacı varsa, bu nesneler eşitlenmiş yöntemlerini çağırarak iş parçacığı güvenli örneklerine dönüştürülebilir. Tümumerators dışında, tüm düzenli ifade sınıfları iş parçacığı güvenli veya eşitlenmiş bir yöntem le iş parçacığı güvenli nesnelere dönüştürülebilir.  
  
 Sayısallaştırıcılar tek istisnadır. Bir uygulama toplama sayısalatörler için çağrıları seri hale getirmek gerekir. Kural, bir koleksiyon aynı anda birden fazla iş parçacığı üzerinde numaralandırılabilir, sen enumerator tarafından geçen koleksiyonun kök nesnesi üzerinde numaralandırma yöntemleri eşitlemek gerektiğidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET Düzenli İfadeler](../../../docs/standard/base-types/regular-expressions.md)
