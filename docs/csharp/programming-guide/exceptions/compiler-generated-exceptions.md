---
title: Derleyici-Oluşturulan Özel Durumlar - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
ms.openlocfilehash: 2a6b2c3fa053f1c555856df8098975340e78e2b2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705320"
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a>Derleyicinin Ürettiği Özel Durumlar (C# Programlama Kılavuzu)
Bazı özel durumlar,.NET Framework'ün ortak dil çalışma süresi (CLR) tarafından temel işlemler başarısız olduğunda otomatik olarak atılır. Bu özel durumlar ve hata koşulları aşağıdaki tabloda listelenmiştir.  
  
|Özel durum|Açıklama|  
|---------------|-----------------|  
|<xref:System.ArithmeticException>|Aritmetik işlemler sırasında oluşan özel durumlar için <xref:System.DivideByZeroException> bir <xref:System.OverflowException>taban sınıf, ve.|  
|<xref:System.ArrayTypeMismatchException>|Öğenin gerçek türü dizinin gerçek türüyle uyumsuz olduğundan, bir dizi belirli bir öğeyi depolayamadığında atılır.|  
|<xref:System.DivideByZeroException>|İntegral değerini sıfıra bölmegirişiminde bulunulduğunda atılır.|  
|<xref:System.IndexOutOfRangeException>|Dizin sıfırdan küçükse veya dizinin sınırlarının dışında yken bir diziyi diziyi diziye dizidetme girişiminde bulunulduğunda atılır.|  
|<xref:System.InvalidCastException>|Bir temel türden arabirime veya türetilmiş türe açık bir dönüştürme çalışma zamanında başarısız olduğunda atılır.|  
|<xref:System.NullReferenceException>|Değeri [null](../../language-reference/keywords/null.md)olan bir nesneye başvuru yapmak için bir girişim yapıldığında atılan.|  
|<xref:System.OutOfMemoryException>|[Yeni](../../language-reference/operators/new-operator.md) işleci kullanarak bellek ayırma girişimi başarısız olduğunda atılır. Bu, ortak dil çalışma zamanı için kullanılabilir bellek tükendi gösterir.|  
|<xref:System.OverflowException>|Bir `checked` bağlamda bir aritmetik işlem taştığında atılır.|  
|<xref:System.StackOverflowException>|Yürütme yığını çok fazla bekleyen yöntem çağrıları olan zaman atılır; genellikle çok derin veya sonsuz bir özyineleme gösterir.|  
|<xref:System.TypeInitializationException>|Statik bir oluşturucu bir özel durum `catch` attığında ve onu yakalamak için uyumlu bir yan tümce olmadığında atılır.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Özel Durumlar ve Özel Durum Kullanımı](./index.md)
- [Özel Durum Taşıma](./exception-handling.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
