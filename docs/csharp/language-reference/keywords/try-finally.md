---
title: try-finally- C# Reference
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: 2c4c69b1e104aed968bc24bac690de83026643a0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713020"
---
# <a name="try-finally-c-reference"></a>try-finally (C# Başvurusu)

Bir `finally` bloğu kullanarak, bir [TRY](try-catch.md) bloğunda ayrılan tüm kaynakları temizleyebilir ve `try` bloğunda bir özel durum meydana gelirse bile kodu çalıştırabilirsiniz. Genellikle, denetim bir `try` deyiminden ayrıldığında `finally` bloğunun deyimleri çalışır. Denetim aktarımı, `break`, `continue`, `goto`veya `return` deyimlerinin yürütülmesi ya da `try` deyimindeki bir özel durumun yayılmasından kaynaklanan normal yürütmenin sonucu olarak ortaya çıkabilir.

İşlenmiş bir özel durum içinde, ilişkili `finally` bloğunun çalıştırılması garanti edilir. Ancak, özel durum işlenmemiş ise, `finally` bloğunun yürütülmesi özel durum geriye doğru izleme işleminin nasıl tetiklendiğine bağlıdır. Bu da, bilgisayarınızın nasıl ayarlanmayacağına bağlıdır.

Genellikle, işlenmeyen bir özel durum uygulamayı sona erdirdiğinde, `finally` bloğunun çalıştırılıp çalıştırılmayacağı önemli değildir. Ancak, bu durumda bile çalıştırılması gereken bir `finally` bloğunda deyiminiz varsa, tek bir çözüm `try`-`finally` ifadesine bir `catch` bloğu eklemektir. Alternatif olarak, çağrı yığınında daha yüksek bir `try`-`finally` ifadesinin `try` bloğunda oluşturulan özel durumu yakalayabilirsiniz. Diğer bir deyişle, `try`-`finally` ifadesini veya bu yöntemi çağıran yöntemi ya da çağrı yığınındaki herhangi bir yöntemi çağıran yöntemi çağıran özel durumu yakalayabilirsiniz. Özel durum yakalanmadığında, `finally` bloğunun yürütülmesi işletim sisteminin özel durum geriye doğru izleme işlemi tetiklemeyi seçip seçmeyeceğini bağlıdır.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, geçersiz bir dönüştürme ekstresi `System.InvalidCastException` bir özel duruma neden olur. Özel durum işlenmemiş olur.

[!code-csharp[csrefKeywordsExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#4)]

Aşağıdaki örnekte, `TryCast` yönteminden bir özel durum, çağrı yığınının ardından bir yöntemde yakalanır.

[!code-csharp[csrefKeywordsExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#6)]

`finally`hakkında daha fazla bilgi için bkz. [try-catch-finally](try-catch-finally.md).

C#Ayrıca, uygun bir sözdiziminde <xref:System.IDisposable> nesneler için benzer işlevler sağlayan [using ifadesini](using-statement.md)de içerir.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [TRY deyimin](~/_csharplang/spec/statements.md#the-try-statement) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [try, throw ve catch Deyimleri (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [throw](throw.md)
- [try-catch](try-catch.md)
- [Nasıl yapılır: Açıkça Özel Durumlar Oluşturma](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
