---
title: try-finally- C# Reference
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: a8d18a6ae8b3f8f6cde76b1b296ac6a317ca1ed1
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168574"
---
# <a name="try-finally-c-reference"></a>try-finally (C# Başvurusu)

Bir `finally` blok kullanarak, bir [TRY](try-catch.md) bloğunda ayrılan tüm kaynakları temizleyebilir ve bir `try` özel durum bloğunda meydana gelirse bile kodu çalıştırabilirsiniz. Genellikle, denetim bir `finally` `try` deyiminden ayrıldığında blok deyimleri çalışır. Denetimin aktarımı normal yürütme,, `break`, veya `continue` `goto` `return` bildiriminin yürütülmesi ya da deyimdenbirözeldurumunyayılmasındankaynaklanıyorolabilir.`try`

İşlenmiş bir özel durum içinde, ilişkili `finally` bloğun çalıştırılması garanti edilir. Ancak, özel durum işlenmemiş ise, `finally` bloğun yürütülmesi özel durum geriye doğru tetikleme işleminin tetiklendiği duruma bağlıdır. Bu da, bilgisayarınızın nasıl ayarlanmayacağına bağlıdır.

Genellikle, işlenmeyen bir özel durum uygulamayı sona erdirdiğinde, `finally` bloğun çalıştırılıp çalıştırılmayacağı önemli değildir. Ancak, bu durumda bile çalıştırılması gereken bir `finally` blokta deyimler varsa, bir çözüm `finally` ifadeye bir `catch` blok `try` - eklemektir. Alternatif olarak, çağrı yığınının `try` üst kısmında yer alan bir `try` - `finally` deyimin bloğunda ortaya atılmış olabilecek özel durumu yakalayabilirsiniz. Diğer bir deyişle, bir yöntemi, `try` `finally` ifadeyi içeren - yöntemi veya bu yöntemi çağıran yöntemi ya da çağrı yığınında herhangi bir yöntemi çağıran yöntemini yakalayabilirsiniz. Özel durum yakalanmadığında, `finally` bloğun yürütülmesi işletim sisteminin özel durum geriye doğru izleme işlemi tetiklemeyi seçip seçmediğine bağlıdır.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, geçersiz bir dönüştürme açıklaması `System.InvalidCastException` özel duruma neden olur. Özel durum işlenmemiş olur.

[!code-csharp[csrefKeywordsExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#4)]

Aşağıdaki örnekte, `TryCast` yöntem içindeki bir özel durum, çağrı yığınının ardından bir yöntemde yakalanır.

[!code-csharp[csrefKeywordsExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#6)]

Hakkında `finally`daha fazla bilgi için bkz. [try-catch-finally](try-catch-finally.md).

C#Ayrıca, uygun bir sözdiziminde nesneler için <xref:System.IDisposable> benzer işlevler sağlayan [using ifadesini](using-statement.md)de içerir.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [TRY deyimin](~/_csharplang/spec/statements.md#the-try-statement) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [try, throw ve catch Deyimleri (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [throw](throw.md)
- [try-catch](try-catch.md)
- [Nasıl yapılır: Özel durumları açık olarak oluştur](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
