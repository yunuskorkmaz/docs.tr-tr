---
title: Derleyicinin Ürettiği Özel Durumlar (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
ms.openlocfilehash: a1746a492685cf25869bd06935bfd056de257fea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331447"
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a>Derleyicinin Ürettiği Özel Durumlar (C# Programlama Kılavuzu)
Temel işlemleri başarısız olduğunda bazı otomatik olarak .NET Framework'ün ortak dil çalışma zamanı tarafından (CLR) özel durumlar. Bu özel durumlar ve bunların hata koşulları aşağıdaki tabloda listelenmiştir.  
  
|Özel Durum|Açıklama|  
|---------------|-----------------|  
|<xref:System.ArithmeticException>|Gibi aritmetik işlemler sırasında oluşan özel durumlar için temel sınıf <xref:System.DivideByZeroException> ve <xref:System.OverflowException>.|  
|<xref:System.ArrayTypeMismatchException>|Öğesinin gerçek türü dizi gerçek türü ile uyumlu olmadığı için belirli bir öğenin diziyi depolanamıyor zaman oluşturulur.|  
|<xref:System.DivideByZeroException>|Bir tam sayı değeri bölmek için sıfıra girişimde zaman oluşturulur.|  
|<xref:System.IndexOutOfRangeException>|Dizini sıfırdan küçük veya dizinin sınırları dışında olduğunda bir dizi dizini oluşturmak için bir girişimde zaman oluşturulur.|  
|<xref:System.InvalidCastException>|Taban türünden bir açık dönüştürme bir arabirim veya türetilmiş bir tür için çalışma zamanında başarısız olduğunda oluşturulur.|  
|<xref:System.NullReferenceException>|Değeri olan bir nesne başvurusu denediğinizde durum [null](../../../csharp/language-reference/keywords/null.md).|  
|<xref:System.OutOfMemoryException>|Bellek kullanarak ayırma girişimi zaman oluşturulur [yeni](../../../csharp/language-reference/keywords/new-operator.md) işleci başarısız olur. Bu, ortak dil çalışma zamanı için kullanılabilir bellek tükendi olduğunu gösterir.|  
|<xref:System.OverflowException>|Aritmetik bir işlem, zaman oluşturulan bir `checked` bağlamı taşar.|  
|<xref:System.StackOverflowException>|Yürütme yığını çok fazla bekleyen yöntem çağrılarını sağlayarak kaldığında oluşturulur; genellikle çok derin veya sonsuz özyineleme gösterir.|  
|<xref:System.TypeInitializationException>|Statik Oluşturucusu bir özel durum ve hiçbir uyumlu oluşturduğunda durum `catch` yan tümcesi var. Bu yakalamak için.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Özel Durumlar ve Özel Durum İşleme](../../../csharp/programming-guide/exceptions/index.md)  
 [Özel Durum İşleme](../../../csharp/programming-guide/exceptions/exception-handling.md)  
 [try-catch](../../../csharp/language-reference/keywords/try-catch.md)  
 [try-finally](../../../csharp/language-reference/keywords/try-finally.md)  
 [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)
