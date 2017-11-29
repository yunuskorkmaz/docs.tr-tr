---
title: "try-finally (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
caps.latest.revision: "25"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 927b851419f2c5245518ee39bf847cb1f1664917
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="try-finally-c-reference"></a>try-finally (C# Başvurusu)
Kullanarak bir `finally` bloğu içinde ayrılan tüm kaynakları temizlemek bir [deneyin](../../../csharp/language-reference/keywords/try-catch.md) bloğu ve çalıştırabilirsiniz kod içinde bir özel durum oluştuğunda dahi `try` bloğu. Genellikle, bilgilerinin bir `finally` denetim ayrıldığında çalıştırmak blok bir `try` deyimi. Denetim aktarımını yürütülmesi normal yürütülmesi sonucu olarak ortaya çıkabilir bir `break`, `continue`, `goto`, veya `return` deyimi, veya bir özel durum dışında yayılmasını `try` deyimi.  
  
 Bir özel durumu, ilişkili içinde `finally` blok garanti çalıştırılacak. Ancak, işlenmemiş özel durum oluştu, yürütülmesi `finally` blok bağımlı olduğu nasıl özel durum bırakma işlemi tetiklenir. Buna karşılık, bilgisayarınızı nasıl ayarlanacağını bağımlı olmasıdır.
  
 Genellikle, işlenmeyen bir özel durum sona erdiğinde bir uygulama olup olmadığına `finally` blok çalıştırıldığında önemli değildir. Ancak, deyimleri varsa bir `finally` bile bu durumda, bir çözüm çalıştırılması gereken taşıdır eklemek için bir `catch` için engelleyin `try` - `finally` deyimi. Alternatif olarak, bir durum içinde özel durum yakalayabilir `try` , engelleme bir `try` - `finally` deyimi çağrı yığınına daha yüksek. Diğer bir deyişle, içeren yöntemini çağıran yöntemi özel durum yakalayabilir `try` - `finally` deyimi, ya da bu yöntemi çağırır yöntemi veya çağrı yığınında herhangi bir yöntemi. Özel durum yakalandı, yürütülmesi `finally` blok bağlı olup olmadığını işletim sistemi bir özel durum harekete seçti üzerinde işlem bırakma.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, bir geçersiz dönüştürme deyimi neden bir `System.InvalidCastException` özel durum. İşlenmeyen özel durum kodudur.  
  
 [!code-csharp[csrefKeywordsExceptions#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_1.cs)]  
  
 Aşağıdaki örnekte, bir özel durumundan `TryCast` yöntemi bir yöntemi uzağa çağrı yığını yakalanma yeri.  
  
 [!code-csharp[csrefKeywordsExceptions#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_2.cs)]  
  
 Hakkında daha fazla bilgi için `finally`, bkz: [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md).  
  
 C# de içerir [deyimiyle](../../../csharp/language-reference/keywords/using-statement.md), için benzer bir işlevsellik sağlayan <xref:System.IDisposable> kullanışlı bir söz dizimi nesneleri.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [deneyin, throw ve catch deyimleri (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)  
 [Özel durum işleme deyimleri](../../../csharp/language-reference/keywords/exception-handling-statements.md)  
 [throw](../../../csharp/language-reference/keywords/throw.md)  
 [try-catch](../../../csharp/language-reference/keywords/try-catch.md)  
 [Nasıl yapılır: açıkça özel durumlar oluşturma](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
