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
ms.openlocfilehash: 227c880aab89d0ada4431dc50148c36ce00cfda8
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53155164"
---
# <a name="try-finally-c-reference"></a>try-finally (C# Başvurusu)

Kullanarak bir `finally` bloğu içinde ayrılan tüm kaynakları temizleyebilirsiniz bir [deneyin](try-catch.md) bloğu ve kodu çalıştırabilir bir özel durum meydana gelse bile `try` blok. Genellikle, deyimleri bir `finally` denetimi terk ettiğinde çalıştırmak blok bir `try` deyimi. Denetim aktarımı yürütülmesini normal yürütülmesi sonucunda oluşabilir bir `break`, `continue`, `goto`, veya `return` deyimi veya bir özel durumun yayılmasının `try` deyimi.

İşlenen özel durum, ilişkili içinde `finally` blokun çalıştırılacak. Ancak, özel durum işlenmezse yürütülmesini `finally` bloğunun nasıl özel durumu geriye doğru izlenme işleminin tetiklenir. Buna karşılık, bilgisayarınızın nasıl ayarlandığına bağlıdır.

Genelde işlenmeyen bir özel durum sona erdiğinde bir uygulama olup olmadığını `finally` blokunun çalıştırılıp çalıştırılmaması önemli değildir. Ancak, varsa bir `finally` bile bu durumda, tek bir çözüm çalıştırılması gereken bloğudur eklemek için bir `catch` bloğunu `try` - `finally` deyimi. Alternatif olarak, oluşturulmuş olabilecek istisnayı yakalamak mümkündür `try` bloğu bir `try` - `finally` çağrı yığınının üstlerinde deyimi. Diğer bir deyişle, özel durum içeren yöntemi çağıran yöntemi yakalayabilir `try` - `finally` deyimi, veya bu yöntemi çağıran yöntemdeki veya çağrı yığınındaki herhangi bir yöntemi. Özel durum yakalanmazsa yürütülmesini `finally` blok bağlı olup bir işletim sistemi bir özel durum harekete seçer üzerinde bırakma işlemi.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, geçersiz dönüştürme deyimi neden olan bir `System.InvalidCastException` özel durum. İşlenmeyen özel durum.

[!code-csharp[csrefKeywordsExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#4)]

Aşağıdaki örnekte, bir özel durumdan `TryCast` yöntemi bir yöntem çağrı yığınında yığınından uzakta yakalandı.

[!code-csharp[csrefKeywordsExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#6)]

Hakkında daha fazla bilgi için `finally`, bkz: [try-catch-finally](try-catch-finally.md).

C# ayrıca içerir [using deyimi](using-statement.md), için benzer işlevsellik sağlayan <xref:System.IDisposable> bir sözdizimindeki nesneleri.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [try, throw ve catch Deyimleri (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [Özel Durum İşleme Deyimleri](exception-handling-statements.md)
- [throw](throw.md)
- [try-catch](try-catch.md)
- [Nasıl Yapılır: Açıkça özel durumlar oluşturma](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)