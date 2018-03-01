---
title: "private (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d9cc8f86166888b47a758e200182d319c68ca6d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="private-c-reference"></a>private (C# Başvurusu)
`private` Sözcüktür üye erişim değiştiricisi. 
   
 > Bu sayfayı kapsayan `private` erişim. `private` Sözcüktür ayrıca parçası [ `private protected` ](./private-protected.md) erişim değiştiricisi.
  
Özel erişim en az izin veren bir erişim düzeydir. Özel üyeler, yalnızca sınıf ya da, bunlar, bu örnekteki bildirilir yapı gövdesi içinde erişilebilir:  
  
```  
class Employee  
{  
    private int i;  
    double d;   // private access by default  
}  
```  

 İç içe geçmiş türler aynı gövdesinde, bu özel üyeler de erişebilirsiniz.  
  
 Özel üye sınıfta veya yapı içinde bildirilmiş dışında başvurmak için bir derleme zamanı hata var.  
  
 Bir karşılaştırması `private` diğer erişim değiştiricileri ile bkz [erişilebilirlik düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md) ve [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
## <a name="example"></a>Örnek  
 Bu örnekte, `Employee` sınıfı içeren iki özel veri üyesi `name` ve `salary`. Özel üye olarak, bunlar dışındaki üye yöntemleri tarafından erişilemez. Genel yöntemler adlı `GetName` ve `Salary` özel üyelerin denetimli erişmesine izin vermek için eklenir. `name` Üye genel bir yöntem aracılığıyla erişilen ve `salary` üye genel salt okunur özelliği aracılığıyla erişilir. (Bkz [özellikleri](../../../csharp/programming-guide/classes-and-structs/properties.md) daha fazla bilgi için.)  
  
 [!code-csharp[csrefKeywordsModifiers#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/private_1.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Erişim değiştiricileri](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [Erişilebilirlik düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [Değiştiriciler](../../../csharp/language-reference/keywords/modifiers.md)  
 [Ortak](../../../csharp/language-reference/keywords/public.md)  
 [korumalı](../../../csharp/language-reference/keywords/protected.md)  
 [İç](../../../csharp/language-reference/keywords/internal.md)
