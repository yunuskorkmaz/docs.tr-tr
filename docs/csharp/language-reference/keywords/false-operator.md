---
title: false işleci (C# Başvurusu)
ms.date: 07/20/2015
helpviewer_keywords:
- false operator keyword [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: e1c6da604f35031dd9d712125356243e1735f452
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027843"
---
# <a name="false-operator-c-reference"></a>false işleci (C# Başvurusu)

Döndürür [bool](bool.md) değeri `true` işleneni olduğunu belirtmek için `false` ve döndürür `false` Aksi takdirde.

C# 2.0 önce `true` ve `false` işleçleri gibi türleri ile uyumlu kullanıcı tanımlı boş değer atanabilen değer türleri oluşturmak için kullanılan `SqlBool`. Ancak, dil, boş değer atanabilen değer türleri için yerleşik destek sağlar ve mümkün olduğunda bu aşırı yüklemesi yerine kullanmalısınız `true` ve `false` işleçler. Daha fazla bilgi için bkz: [boş değer atanabilir türler](../../programming-guide/nullable-types/index.md).

Boş değer atanabilir Boole değerlerini, ifade ile `a != b` mutlaka eşit değil `!(a == b)` birine veya ikisine de değerleri null olabilir çünkü. Her ikisi de aşırı yükleme zorunda `true` ve `false` işleçleri ayrı olarak ifade null değerler düzgün bir şekilde işler. Aşağıdaki örnek aşırı yükleme ve nasıl kullanılacağını gösterir `true` ve `false` işleçler.

[!code-csharp[csrefKeywordsOperator#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#16)]

Overloads türü `true` ve `false` işleçleri, denetleme ifade için kullanılabilir [varsa](if-else.md), [yapmak](do.md), [sırada](while.md), ve [ için](for.md) deyimleri ve [koşullu ifadeler](../operators/conditional-operator.md).

Bir tür işleci tanımlıyorsa `false`, işleci tanımlamalısınız [doğru](true.md).

Bir tür doğrudan koşullu mantıksal işleçler tekrar yükleyemez [ && ](../operators/conditional-and-operator.md) ve [ &#124; &#124; ](../operators/conditional-or-operator.md), ancak eşdeğer efekt normal mantıksal işleç aşırı yüklemesi tarafından gerçekleştirilebilir. ve işleçleri `true` ve `false`.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

[C# başvurusu](../index.md)  
[C# Programlama Kılavuzu](../../programming-guide/index.md)  
[C# Anahtar Sözcükleri](index.md)  
[C# İşleçleri](../operators/index.md)  
[true](true.md)  