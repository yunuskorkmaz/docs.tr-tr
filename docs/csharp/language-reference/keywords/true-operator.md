---
title: true İşleci (C# Başvurusu)
ms.date: 07/20/2015
helpviewer_keywords:
- true operator [C#]
ms.assetid: acaba817-5da5-4364-b3b2-2e5c75ec1839
ms.openlocfilehash: 54b8d764dc673598474d6adbbee82e0223a16b93
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44271318"
---
# <a name="true-operator-c-reference"></a>true İşleci (C# Başvurusu)
Döndürür [bool](../../../csharp/language-reference/keywords/bool.md) değer `true` bir işlenen true ise ve döndürür belirtmek için `false` Aksi takdirde.  
  
 C# 2.0 önce `true` ve `false` işleçler gibi türleri ile uyumlu olan kullanıcı tanımlı değer atanabilen değer türleri oluşturmak için kullanılan `SqlBool`. Ancak, dil artık boş değer atanabilen değer türleri için yerleşik destek sağlar ve mümkün olduğunda bu aşırı yükleme yerine bu kullanması gereken `true` ve `false` işleçleri. Daha fazla bilgi için [boş değer atanabilir türler](../../../csharp/programming-guide/nullable-types/index.md).  
  
 Boş değer atanabilir Boole değerlerini, ifade ile `a != b` eşit değil `!(a == b)` çünkü bir veya iki değer null olabilir. Her ikisi de aşırı yükleme yapmanız `true` ve `false` işleçleri ayrı olarak ifade null değerler doğru bir şekilde tanımlamak için. Aşağıdaki örnek, aşırı yükleme ve kullanma işlemi gösterilmektedir `true` ve `false` işleçleri.  
  
 [!code-csharp[csrefKeywordsOperator#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/true-operator_1.cs)]  
  
 Aşırı bir tür `true` ve `false` işleçleri, Denetim ifadesi için kullanılabilir [varsa](../../../csharp/language-reference/keywords/if-else.md), [yapmak](../../../csharp/language-reference/keywords/do.md), [sırada](../../../csharp/language-reference/keywords/while.md), ve [ için](../../../csharp/language-reference/keywords/for.md) deyimleri ve [koşullu ifadeler](../../../csharp/language-reference/operators/conditional-operator.md).  
  
 İşleci bir türü tanımlıyorsa `true`, işlecini tanımlamalıdır [false](../../../csharp/language-reference/keywords/false.md).  
  
 Bir tür doğrudan koşullu mantıksal işleçler aşırı yüklenemez ([ && ](../../../csharp/language-reference/operators/conditional-and-operator.md) ve [ &#124; &#124; ](../../../csharp/language-reference/operators/conditional-or-operator.md)), ancak eşdeğer efekt normal aşırı yüklenerek ulaşılabilecek mantıksal işleçler ve işleçler `true` ve `false`.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
- [C# İşleçleri](../../../csharp/language-reference/operators/index.md)  
- [false](../../../csharp/language-reference/keywords/false.md)
