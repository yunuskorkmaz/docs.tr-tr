---
title: Derleyicinin ürettiği özel durumlar- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
ms.openlocfilehash: 2a6b2c3fa053f1c555856df8098975340e78e2b2
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705320"
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a>Derleyicinin Ürettiği Özel Durumlar (C# Programlama Kılavuzu)
Bazı özel durumlar, temel işlemler başarısız olduğunda .NET Framework ortak dil çalışma zamanı (CLR) tarafından otomatik olarak oluşturulur. Bu özel durumlar ve bunların hata koşulları aşağıdaki tabloda listelenmiştir.  
  
|Özel Durum|Açıklama|  
|---------------|-----------------|  
|<xref:System.ArithmeticException>|<xref:System.DivideByZeroException> ve <xref:System.OverflowException>gibi aritmetik işlemler sırasında oluşan özel durumlar için temel sınıf.|  
|<xref:System.ArrayTypeMismatchException>|Öğenin gerçek türü dizinin gerçek türüyle uyumlu olmadığından, bir dizi belirli bir öğeyi depolayamadığı zaman oluşturulur.|  
|<xref:System.DivideByZeroException>|İntegral değeri sıfıra bölmek için bir deneme yapıldığında oluşturulur.|  
|<xref:System.IndexOutOfRangeException>|Dizin sıfırdan küçükse veya dizinin sınırları dışında bir diziyi dizinlemek için bir girişim yapıldığında oluşturulur.|  
|<xref:System.InvalidCastException>|Temel türden bir arabirime ya da türetilmiş bir türe açık bir dönüştürme çalışma zamanında başarısız olduğunda oluşturulur.|  
|<xref:System.NullReferenceException>|Değeri [null](../../language-reference/keywords/null.md)olan bir nesneye başvuru yapıldığında oluşturulur.|  
|<xref:System.OutOfMemoryException>|[New](../../language-reference/operators/new-operator.md) işlecini kullanarak bellek ayırma girişimi başarısız olduğunda oluşturulur. Bu, ortak dil çalışma zamanı için kullanılabilir belleğin tükendiğini gösterir.|  
|<xref:System.OverflowException>|`checked` bağlamdaki bir aritmetik işlem taştığında oluşturulur.|  
|<xref:System.StackOverflowException>|Yürütme yığını çok fazla sayıda bekleyen Yöntem çağrısı ile tükendiğinde oluşturulur; genellikle çok derin veya sonsuz özyineleme gösterir.|  
|<xref:System.TypeInitializationException>|Statik bir Oluşturucu bir özel durum oluşturduğunda ve bunu yakalamak için uyumlu `catch` yan tümcesi yoksa oluşturulur.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Özel Durumlar ve Özel Durum İşleme](./index.md)
- [Özel Durum İşleme](./exception-handling.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
