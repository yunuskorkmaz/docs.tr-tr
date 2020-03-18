---
title: try-finally - C# Referans
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: 2c4c69b1e104aed968bc24bac690de83026643a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713020"
---
# <a name="try-finally-c-reference"></a>try-finally (C# Başvurusu)

Bir `finally` blok kullanarak, [try](try-catch.md) bloğunda ayrılan kaynakları temizleyebilir ve `try` blokta bir özel durum oluşsa bile kodu çalıştırabilirsiniz. Genellikle, denetim bir `finally` `try` deyim bırakırken bir blok çalışması ifadeleri. Denetim aktarımı, normal yürütme, `break`bir , , `continue` `goto`, veya `return` deyimi, ya da `try` bir özel durum dış deyimi nin yayılması nın bir sonucu olarak oluşabilir.

İşlenen özel durum `finally` içinde, ilişkili bloğun çalıştırılması garanti edilir. Ancak, özel durum işlenmemişse, `finally` bloğun yürütülmesi özel durum gevşeme işleminin nasıl tetiklendirilen bağlıdır. Bu da bilgisayarınızın nasıl ayarlıyorumuna bağlıdır.

Genellikle, işlenmemiş bir özel durum bir uygulamayı `finally` sona erdirdiğinde, bloğun çalışıp çalışmadığı önemli değildir. Ancak, bu durumda bile `finally` çalıştırılması gereken bir blokta ifadeler varsa, `catch` bir çözüm `try` - `finally` deyimi bir blok eklemektir. Alternatif olarak, çağrı yığınının yukarısındaki `try` bir `try` - `finally` deyimin bloğuna atılabilecek özel durumu yakalayabilirsiniz. Diğer bir deyişle, `try` - `finally` deyimi içeren yöntemi çağıran yöntemde veya bu yöntemi çağıran yöntemde veya çağrı yığınındaki herhangi bir yöntemde özel durumu yakalayabilirsiniz. Özel durum yakalanmazsa, `finally` bloğun yürütülmesi işletim sisteminin bir özel durum gevşeme işlemini tetiklemeyi seçip seçmediğine bağlıdır.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, geçersiz bir dönüşüm `System.InvalidCastException` bildirimi özel bir özel durum neden olur. Özel durum işlenmemiş.

[!code-csharp[csrefKeywordsExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#4)]

Aşağıdaki örnekte, yöntemden `TryCast` bir özel durum, çağrı yığınının daha yukarısındaki bir yöntemde yakalanır.

[!code-csharp[csrefKeywordsExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#6)]

Hakkında `finally`daha fazla bilgi için, [try-catch-finally](try-catch-finally.md)bakın.

C# ayrıca, kullanışlı bir sözdiziminde nesneler için <xref:System.IDisposable> benzer işlevler sağlayan using [deyimini](using-statement.md)de içerir.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [try deyimi](~/_csharplang/spec/statements.md#the-try-statement) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](index.md)
- [try, throw ve catch Deyimleri (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [throw](throw.md)
- [try-catch](try-catch.md)
- [Nasıl yapılır: Açıkça Özel Durumlar Oluşturma](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
