---
title: "?? İşleci (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ??_CSharpKeyword
helpviewer_keywords:
- coalesce operator [C#]
- ?? operator [C#]
- conditional-AND operator (&&) [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6c2372380d8162d3e7760bba4a43cdb1c568bf5b
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/06/2017
---
# <a name="-operator-c-reference"></a>?? İşleci (C# Başvurusu)
`??` İşleci, null birleşim işlecinin çağrılır.  İşlenen null değilse, sol taraf işlenenini döndürür; tersi durumda, sağ el işlenenini döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Null yapılabilir bir tür, türün etki alanından bir değeri gösterebilir veya değer tanımsız olabilir (bu durumda, değer null olur). Kullanabileceğiniz `??` işlecin söz dizimi anlamlılık uygun bir değer (sağ işleneni) dönmek için sol işleneni null atanabilir bir tür değeri null olduğunda. Bir boş değer atanabilen değer atanamayan değer türüne kullanmadan atamak üzere çalışırsanız `??` işleci, derleme zamanı hata üretir. Bir cast kullanıyorsanız ve boş değer atanabilen değer türü şu anda tanımlanmamış bir `InvalidOperationException` özel durum.  
  
 Daha fazla bilgi için bkz: [boş değer atanabilir türler](../../../csharp/programming-guide/nullable-types/index.md).  
  
 Sonucunu bir?? işleç iki bağımsız değişkenlerini sabitleri olsa bile bir sabit olarak kabul değil.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csRefOperators#53](../../../csharp/language-reference/operators/codesnippet/CSharp/null-conditional-operator_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# işleçleri](../../../csharp/language-reference/operators/index.md)  
 [Boş değer atanabilir türler](../../../csharp/programming-guide/nullable-types/index.md)  
 [Hangi tam olarak 'Kaldırılmış' anlamına mu?](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
