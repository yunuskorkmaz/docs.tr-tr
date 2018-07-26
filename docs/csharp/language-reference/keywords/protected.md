---
title: protected (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: a3115fe82b452f52ee75cf222302ece0fc67b330
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/25/2018
ms.locfileid: "39243632"
---
# <a name="protected-c-reference"></a>protected (C# Başvurusu)
`protected` Anahtar sözcüğü, bir üye erişim değiştiricisi. 

 > Bu sayfa kapsayan `protected` erişim. `protected` Anahtar sözcüğü, ayrıca parçası [ `protected internal` ](./protected-internal.md) ve [ `private protected` ](./private-protected.md) erişim değiştiricileri. 

Korumalı üye sınıfı içinde ve türetilen sınıf örnekleri tarafından erişilebilir. 

Bir karşılaştırması `protected` diğer erişim değiştiricileri ile bkz [erişilebilirlik düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md). 
  
## <a name="example"></a>Örnek  
 Yalnızca türetilmiş sınıf türü erişim ortaya çıkarsa, bir taban sınıfın korumalı bir üye türetilen bir sınıfta erişilebilir. Örneğin, aşağıdaki kod kesimi göz önünde bulundurun:  
  
 [!code-csharp[csrefKeywordsModifiers#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_1.cs)]  
  
 Deyim `a.x = 10` ana statik yöntem içinde yapılır ve örneği değil, sınıf b olduğundan bir hata oluşturur.  
  
 Yapı üyeleri struct devralınamaz korunamaz.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, sınıf `DerivedPoint` türetilir `Point`. Bu nedenle, temel sınıfın korumalı üyeler türetilmiş sınıftan doğrudan erişebilirsiniz.  
  
 [!code-csharp[csrefKeywordsModifiers#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_2.cs)]  
  
 Erişim düzeyleri değiştirirseniz `x` ve `y` için [özel](../../../csharp/language-reference/keywords/private.md), derleyici hata iletilerini verir:  
  
 `'Point.y' is inaccessible due to its protection level.`  
  
 `'Point.x' is inaccessible due to its protection level.`  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Erişim Değiştiricileri](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [Erişilebilirlik Düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [Değiştiriciler](../../../csharp/language-reference/keywords/modifiers.md)  
 [public](../../../csharp/language-reference/keywords/public.md)  
 [private](../../../csharp/language-reference/keywords/private.md)  
 [internal](../../../csharp/language-reference/keywords/internal.md)  
 [İç sanal anahtar sözcükleri ile ilgili güvenlik konuları](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))