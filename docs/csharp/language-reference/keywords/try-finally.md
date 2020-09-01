---
description: try-finally-C# başvurusu
title: try-finally-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: 621c5bf1607136361b72f978681607ec2aec150f
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141978"
---
# <a name="try-finally-c-reference"></a>try-finally (C# Başvurusu)

Bir blok kullanarak `finally` , bir [TRY](try-catch.md) bloğunda ayrılan tüm kaynakları temizleyebilir ve bir özel durum bloğunda meydana gelirse bile kodu çalıştırabilirsiniz `try` . Genellikle, `finally` Denetim bir deyiminden ayrıldığında blok deyimleri çalışır `try` . Denetimin aktarımı normal yürütme,,, `break` `continue` `goto` veya `return` bildiriminin yürütülmesi ya da deyimden bir özel durumun yayılmasından kaynaklanıyor olabilir `try` .

İşlenmiş bir özel durum içinde, ilişkili `finally` bloğun çalıştırılması garanti edilir. Ancak, özel durum işlenmemiş ise, `finally` bloğun yürütülmesi özel durum geriye doğru tetikleme işleminin tetiklendiği duruma bağlıdır. Bu da, bilgisayarınızın nasıl ayarlanmayacağına bağlıdır.

Genellikle, işlenmeyen bir özel durum uygulamayı sona erdirdiğinde, `finally` bloğun çalıştırılıp çalıştırılmayacağı önemli değildir. Ancak, `finally` Bu durumda bile çalıştırılması gereken bir blokta deyimler varsa, bir çözüm `catch` ifadeye bir blok eklemektir `try` - `finally` . Alternatif olarak, `try` `try` - çağrı yığınının üst kısmında yer alan bir deyimin bloğunda ortaya atılmış olabilecek özel durumu yakalayabilirsiniz `finally` . Diğer bir deyişle, bir yöntemi `try` - `finally` , ifadeyi içeren yöntemi veya bu yöntemi çağıran yöntemi ya da çağrı yığınında herhangi bir yöntemi çağıran yöntemini yakalayabilirsiniz. Özel durum yakalanmadığında, `finally` bloğun yürütülmesi işletim sisteminin özel durum geriye doğru izleme işlemi tetiklemeyi seçip seçmediğine bağlıdır.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, geçersiz bir dönüştürme açıklaması özel duruma neden olur `System.InvalidCastException` . Özel durum işlenmemiş olur.

[!code-csharp[csrefKeywordsExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#4)]

Aşağıdaki örnekte, yöntem içindeki bir özel durum, `TryCast` çağrı yığınının ardından bir yöntemde yakalanır.

[!code-csharp[csrefKeywordsExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#6)]

Hakkında daha fazla bilgi için `finally` bkz. [try-catch-finally](try-catch-finally.md).

C# Ayrıca, uygun bir sözdiziminde nesneler için benzer işlevler sağlayan [using ifadesini](using-statement.md)de içerir <xref:System.IDisposable> .

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [TRY deyimin](~/_csharplang/spec/statements.md#the-try-statement) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](index.md)
- [try, throw ve catch Deyimleri (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [throw](throw.md)
- [try-catch](try-catch.md)
- [Nasıl yapılır: Açıkça Özel Durumlar Oluşturma](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
