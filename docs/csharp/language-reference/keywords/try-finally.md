---
title: try-finally (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: beb54cf6c4e6dc87b9a08b81586b24d72f92b84b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43505948"
---
# <a name="try-finally-c-reference"></a>try-finally (C# Başvurusu)
Kullanarak bir `finally` bloğu içinde ayrılan tüm kaynakları temizleyebilirsiniz bir [deneyin](../../../csharp/language-reference/keywords/try-catch.md) bloğu ve kodu çalıştırabilir bir özel durum meydana gelse bile `try` blok. Genellikle, deyimleri bir `finally` denetimi terk ettiğinde çalıştırmak blok bir `try` deyimi. Denetim aktarımı yürütülmesini normal yürütülmesi sonucunda oluşabilir bir `break`, `continue`, `goto`, veya `return` deyimi veya bir özel durumun yayılmasının `try` deyimi.  
  
 İşlenen özel durum, ilişkili içinde `finally` blokun çalıştırılacak. Ancak, özel durum işlenmezse yürütülmesini `finally` bloğunun nasıl özel durumu geriye doğru izlenme işleminin tetiklenir. Buna karşılık, bilgisayarınızın nasıl ayarlandığına bağlıdır.
  
 Genelde işlenmeyen bir özel durum sona erdiğinde bir uygulama olup olmadığını `finally` blokunun çalıştırılıp çalıştırılmaması önemli değildir. Ancak, varsa bir `finally` bile bu durumda, tek bir çözüm çalıştırılması gereken bloğudur eklemek için bir `catch` bloğunu `try` - `finally` deyimi. Alternatif olarak, oluşturulmuş olabilecek istisnayı yakalamak mümkündür `try` bloğu bir `try` - `finally` çağrı yığınının üstlerinde deyimi. Diğer bir deyişle, özel durum içeren yöntemi çağıran yöntemi yakalayabilir `try` - `finally` deyimi, veya bu yöntemi çağıran yöntemdeki veya çağrı yığınındaki herhangi bir yöntemi. Özel durum yakalanmazsa yürütülmesini `finally` blok bağlı olup bir işletim sistemi bir özel durum harekete seçer üzerinde bırakma işlemi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, geçersiz dönüştürme deyimi neden olan bir `System.InvalidCastException` özel durum. İşlenmeyen özel durum.  
  
 [!code-csharp[csrefKeywordsExceptions#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_1.cs)]  
  
 Aşağıdaki örnekte, bir özel durumdan `TryCast` yöntemi bir yöntem çağrı yığınında yığınından uzakta yakalandı.  
  
 [!code-csharp[csrefKeywordsExceptions#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_2.cs)]  
  
 Hakkında daha fazla bilgi için `finally`, bkz: [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md).  
  
 C# ayrıca içerir [using deyimi](../../../csharp/language-reference/keywords/using-statement.md), için benzer işlevsellik sağlayan <xref:System.IDisposable> bir sözdizimindeki nesneleri.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
- [try, throw ve catch Deyimleri (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)  
- [Özel Durum İşleme Deyimleri](../../../csharp/language-reference/keywords/exception-handling-statements.md)  
- [throw](../../../csharp/language-reference/keywords/throw.md)  
- [try-catch](../../../csharp/language-reference/keywords/try-catch.md)  
- [Nasıl yapılır: Açıkça Özel Durumlar Oluşturma](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
