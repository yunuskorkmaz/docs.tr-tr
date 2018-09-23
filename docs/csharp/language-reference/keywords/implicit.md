---
title: implicit (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- implicit
- implicit_CSharpKeyword
helpviewer_keywords:
- implicit keyword [C#]
ms.assetid: 34db590e-eb3a-4f11-88d0-ffb3cd753dab
ms.openlocfilehash: 70379136fd4b14403eac919ac15590250b17b416
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2018
ms.locfileid: "46702703"
---
# <a name="implicit-c-reference"></a>implicit (C# Başvurusu)

`implicit` Anahtar sözcüğü, bir kullanıcı tanımlı örtük tür dönüştürme işleci bildirmek için kullanılır. Dönüştürme veri kaybına neden olmayan garanti, kullanıcı tanımlı bir tür ve başka bir türü arasında örtülü dönüştürmeler etkinleştirmek için bunu kullanın.

## <a name="example"></a>Örnek

[!code-csharp[csrefKeywordsConversion#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#5)]

Örtük dönüştürmeleri gereksiz atamalar ortadan kaldırarak, kaynak kodunun okunabilirliğini artırabilir. Ancak, örtük dönüştürmelerin açıkça bir türden diğerine dönüştürme yapmak programcılar gerektirmediğinden, bakım beklenmeyen sonuçları engellemek için izlenmelidir. Genel olarak, örtük dönüşüm işleçleri, hiçbir zaman özel durumlar ve Programcı tanıma güvenli bir şekilde kullanılabilir böylece hiçbir zaman bilgileri kaybedersiniz. Bir dönüştürme işleci bu ölçütlerin karşılayamazsanız işaretlenmelidir `explicit`. Daha fazla bilgi için [dönüştürme işleçleri kullanarak](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)  
- [C# Programlama Kılavuzu](../../programming-guide/index.md)  
- [C# Anahtar Sözcükleri](index.md)  
- [explicit](explicit.md)  
- [İşleci (C# Başvurusu)](operator.md)  
- [Nasıl yapılır: Yapılar Arasında Kullanıcı Tanımlı Dönüştürmeler Uygulama](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
