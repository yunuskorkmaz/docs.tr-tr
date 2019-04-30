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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c0bcab0757bc48f6a8216dd5878f0289e49a275
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766759"
---
# <a name="thread-safety-in-regular-expressions"></a>Normal İfadelerde İş Parçacığı Güvenliği
<xref:System.Text.RegularExpressions.Regex> Sınıfının kendisini güvenli ve sabit (salt okunur) iş parçacığıdır. Diğer bir deyişle, **Regex** nesneler üzerinde herhangi bir iş parçacığı oluşturulabilir ve iş parçacıkları arasında paylaşılan; eşleme yöntemlerini herhangi bir iş parçacığından çağrılabilir ve hiçbir zaman herhangi bir genel durumu değiştirme.  
  
 Ancak, sonuç nesnelerini (**eşleşme** ve **MatchCollection**) tarafından döndürülen **Regex** tek bir iş parçacığında kullanılmalıdır. Çoğu bu nesnelerin mantıksal sabittir, ancak kendi uygulamalarını hesaplama performansını artırmak için bazı sonuçları geciktirebilir ve sonuç olarak, Arayanların onlara yönelik erişimi seri gerekir.  
  
 Paylaşımı yapmanız ise **Regex** sonuç nesneleri birden çok iş parçacığında bu nesneler dönüştürülebilir iş parçacığı açısından güvenli örneklerine eşitlenmiş kendi yöntemlerini çağırarak. Numaralandırıcılar dışında tüm normal ifade sınıfları iş parçacığı güvenlidir veya iş parçacığı nesneleri eşitlenmiş bir yöntemle dönüştürülebilir.  
  
 Numaralandırıcılar tek özel durumdur. Uygulama koleksiyonu numaralandırıcılar çağrıları seri gerekir. Bir koleksiyon birden fazla iş parçacığında aynı anda numaralandırılabilir, numaralandırıcı yöntemlerde geçiş tarafından numaralandırıcıyı koleksiyonun kök nesnesi eşitlemeniz gerekir kuralıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET normal ifadeler](../../../docs/standard/base-types/regular-expressions.md)
