---
title: "false İşleci (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- false operator keyword [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6f9761fb49e2c7f6e4a7615e64cec9fed88318c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="false-operator-c-reference"></a>false İşleci (C# Başvurusu)
Döndürür [bool](../../../csharp/language-reference/keywords/bool.md) değeri `true` işleneni olduğunu belirtmek için `false` ve döndürür `false` Aksi takdirde.  
  
 C# 2.0 önce `true` ve `false` işleçleri gibi türleri ile uyumlu kullanıcı tanımlı boş değer atanabilen değer türleri oluşturmak için kullanılan `SqlBool`. Ancak, dil, boş değer atanabilen değer türleri için yerleşik destek sağlar ve mümkün olduğunda bu aşırı yüklemesi yerine kullanmalısınız `true` ve `false` işleçler. Daha fazla bilgi için bkz: [boş değer atanabilir türler](../../../csharp/programming-guide/nullable-types/index.md).  
  
 Boş değer atanabilir Boole değerlerini, ifade ile `a != b` mutlaka eşit değil `!(a == b)` birine veya ikisine de değerleri null olabilir çünkü. Her ikisi de aşırı yükleme zorunda `true` ve `false` işleçleri ayrı olarak ifade null değerler düzgün bir şekilde işler. Aşağıdaki örnek aşırı yükleme ve nasıl kullanılacağını gösterir `true` ve `false` işleçler.  
  
 [!code-csharp[csrefKeywordsOperator#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/false-operator_1.cs)]  
  
 Overloads türü `true` ve `false` işleçleri, denetleme ifade için kullanılabilir [varsa](../../../csharp/language-reference/keywords/if-else.md), [yapmak](../../../csharp/language-reference/keywords/do.md), [sırada](../../../csharp/language-reference/keywords/while.md), ve [ için](../../../csharp/language-reference/keywords/for.md) deyimleri ve [koşullu ifadeler](../../../csharp/language-reference/operators/conditional-operator.md).  
  
 Bir tür işleci tanımlıyorsa `false`, işleci tanımlamalısınız [doğru](../../../csharp/language-reference/keywords/true.md).  
  
 Bir tür doğrudan koşullu mantıksal işleçler tekrar yükleyemez [ && ](../../../csharp/language-reference/operators/conditional-and-operator.md) ve [&#124; &#124;](../../../csharp/language-reference/operators/conditional-or-operator.md), ancak eşdeğer efekt normal mantıksal işleç aşırı yüklemesi tarafından gerçekleştirilebilir. ve işleçleri `true` ve `false`.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [C# işleçleri](../../../csharp/language-reference/operators/index.md)  
 [TRUE](../../../csharp/language-reference/keywords/true.md)
