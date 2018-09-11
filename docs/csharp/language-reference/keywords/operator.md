---
title: işleç anahtar sözcüğü (C# Başvurusu)
description: Yerleşik bir C# İşleç aşırı yüklemesi hakkında bilgi edinin
ms.date: 08/27/2018
f1_keywords:
- operator_CSharpKeyword
- operator
helpviewer_keywords:
- operator keyword [C#]
ms.assetid: 59218cce-e90e-42f6-a6bb-30300981b86a
ms.openlocfilehash: 1e11d7767b61becc39b1158fae9cb2abe997e4bd
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44342387"
---
# <a name="operator-c-reference"></a>operator (C# Başvurusu)

Kullanım `operator` anahtar sözcük yerleşik bir işleç aşırı yüklemesi veya bir kullanıcı tanımlı dönüştürme bir class veya struct bildiriminde sağlamak için.

Özel bir sınıf ya da yapı üzerinde operatör aşırı yükleme için karşılık gelen türü bir işleç bildirimi oluşturun. Yerleşik bir C# işleci aşırı işleç bildirimi, aşağıdaki kurallar karşılamanız gerekir:

- Her ikisini de içeren bir `public` ve `static` değiştiricisi.
- İçerdiği `operator X` burada `X` adı ya da sembol aşırı işleci.
- Birli işleçler bir parametreye sahip ve ikili işleçler iki parametreye sahiptir. Her durumda sınıfın veya yapının işleci bildiren aynı türde en az bir parametresi olmalıdır.

Dönüştürme işleçleri tanımlama hakkında daha fazla bilgi için bkz: [açık](explicit.md) ve [örtük](implicit.md) anahtar sözcüğü makaleler.

Aşırı yüklenebilir C# işleçleri genel bir bakış için bkz: [fazla yüklenebilir işleçler](../../programming-guide/statements-expressions-operators/overloadable-operators.md) makalesi.

## <a name="example"></a>Örnek

Aşağıdaki örnekte tanımlayan bir `Fraction` kesirli sayılar temsil eden tür. Aşırı `+` ve `*` kesirli toplama ve çarpma gerçekleştirmek için işleçler ve ayrıca bir dönüştürme işleci bu dönüştürür sağlar bir `Fraction` için yazın bir `double` türü.

[!code-csharp[csrefKeywordsConversion#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#6)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [implicit](implicit.md)
- [explicit](explicit.md)
- [Fazla yüklenebilir işleçler](../../programming-guide/statements-expressions-operators/overloadable-operators.md)
- [Nasıl yapılır: Yapılar Arasında Kullanıcı Tanımlı Dönüştürmeler Uygulama](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
