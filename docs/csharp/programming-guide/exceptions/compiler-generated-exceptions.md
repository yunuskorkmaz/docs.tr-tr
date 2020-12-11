---
title: Compiler-Generated özel durumları-C# Programlama Kılavuzu
description: Derleyicinin ürettiği özel durumlar hakkında bilgi edinin. Otomatik olarak oluşturulan özel durumların ve bunların hata koşullarının listesini gözden geçirin.
ms.date: 12/09/2020
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
ms.openlocfilehash: 43bacbb1025bc0af3a5f21979315b3d1b0d61066
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110357"
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a>Derleyicinin Ürettiği Özel Durumlar (C# Programlama Kılavuzu)

Bazı özel durumlar, temel işlemler başarısız olduğunda .NET çalışma zamanı tarafından otomatik olarak oluşturulur. Bu özel durumlar ve bunların hata koşulları aşağıdaki tabloda listelenmiştir.

|Özel durum|Açıklama|
|---------------|-----------------|
|<xref:System.ArithmeticException>|Ve gibi aritmetik işlemler sırasında oluşan özel durumlar için temel sınıf <xref:System.DivideByZeroException> <xref:System.OverflowException> .|
|<xref:System.ArrayTypeMismatchException>|Öğenin gerçek türü dizinin gerçek türüyle uyumlu olmadığından, bir dizi belirli bir öğeyi depolayamadığı zaman oluşturulur.|
|<xref:System.DivideByZeroException>|İntegral değeri sıfıra bölmek için bir deneme yapıldığında oluşturulur.|
|<xref:System.IndexOutOfRangeException>|Dizin sıfırdan küçükse veya dizinin sınırları dışında bir diziyi dizinlemek için bir girişim yapıldığında oluşturulur.|
|<xref:System.InvalidCastException>|Temel türden bir arabirime ya da türetilmiş bir türe açık bir dönüştürme çalışma zamanında başarısız olduğunda oluşturulur.|
|<xref:System.NullReferenceException>|Değeri [null](../../language-reference/keywords/null.md)olan bir nesneye başvuru yapıldığında oluşturulur.|
|<xref:System.OutOfMemoryException>|[New](../../language-reference/operators/new-operator.md) işlecini kullanarak bellek ayırma girişimi başarısız olduğunda oluşturulur. Bu özel durum, ortak dil çalışma zamanı için kullanılabilir belleğin tükendiğini gösterir.|
|<xref:System.OverflowException>|`checked`Bağlamdaki aritmetik işlem taştığında oluşturulur.|
|<xref:System.StackOverflowException>|Yürütme yığını çok fazla sayıda bekleyen Yöntem çağrısı ile tükendiğinde oluşturulur; genellikle çok derin veya sonsuz özyineleme gösterir.|
|<xref:System.TypeInitializationException>|Statik bir Oluşturucu bir özel durum oluşturduğunda ve `catch` bunu yakalamak için uyumlu bir yan tümce yoksa oluşturulur.|

## <a name="see-also"></a>Ayrıca bkz.

- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
