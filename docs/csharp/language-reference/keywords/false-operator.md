---
title: false işleci (C# Başvurusu)
ms.date: 07/20/2015
helpviewer_keywords:
- false operator keyword [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: e73113bd37dbb68590267141ad037f78919520bc
ms.sourcegitcommit: daa8788af67ac2d1cecd24f9f3409babb2f978c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47862895"
---
# <a name="false-operator-c-reference"></a>false işleci (C# Başvurusu)

Döndürür [bool](bool.md) değer `true` işleneni olduğunu belirtmek için `false` ve döndürür `false` Aksi takdirde.

C# 2.0 önce `true` ve `false` işleçler gibi türleri ile uyumlu olan kullanıcı tanımlı değer atanabilen değer türleri oluşturmak için kullanılan `SqlBool`. Ancak, dil artık boş değer atanabilen değer türleri için yerleşik destek sağlar ve mümkün olduğunda bu aşırı yükleme yerine bu kullanması gereken `true` ve `false` işleçleri. Daha fazla bilgi için [boş değer atanabilir türler](../../programming-guide/nullable-types/index.md).

Boş değer atanabilir Boole değerlerini, ifade ile `a != b` eşit değil `!(a == b)` çünkü bir veya iki değer null olabilir. Her ikisi de aşırı yüklemeye sahip `true` ve `false` işleçleri ayrı olarak ifade boş değerler doğru bir şekilde işlemek için. Aşağıdaki örnek, aşırı yükleme ve kullanma işlemi gösterilmektedir `true` ve `false` işleçleri.

[!code-csharp[csrefKeywordsOperator#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#16)]

Aşırı bir tür `true` ve `false` işleçleri, Denetim ifadesi için kullanılabilir [varsa](if-else.md), [yapmak](do.md), [sırada](while.md), ve [ için](for.md) deyimleri ve [koşullu ifadeler](../operators/conditional-operator.md).

İşleci bir türü tanımlıyorsa `false`, işlecini tanımlamalıdır [true](true.md).

Bir tür doğrudan koşullu mantıksal işleçler aşırı yüklenemez [ && ](../operators/conditional-and-operator.md) ve [ &#124; &#124; ](../operators/conditional-or-operator.md), ancak eşdeğer efekt normal mantıksal işleçler aşırı yükleme tarafından gerçekleştirilebilir. ve işleçleri `true` ve `false`.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)  
- [C# Programlama Kılavuzu](../../programming-guide/index.md)  
- [C# Anahtar Sözcükleri](index.md)  
- [C# İşleçleri](../operators/index.md)  
- [true](true.md)  