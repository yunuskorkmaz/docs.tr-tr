---
title: private (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: 89bc23e91bf693f0a95b75dffe2399cb7e865b50
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
---
# <a name="private-c-reference"></a>private (C# Başvurusu)
`private` Sözcüktür üye erişim değiştiricisi. 
   
 > Bu sayfayı kapsayan `private` erişim. `private` Sözcüktür ayrıca parçası [ `private protected` ](./private-protected.md) erişim değiştiricisi.
  
Özel erişim en az izin veren bir erişim düzeydir. Özel üyeler, yalnızca sınıf ya da, bunlar, bu örnekteki bildirilir yapı gövdesi içinde erişilebilir:  
  
```csharp  
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
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Erişim Değiştiricileri](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [Erişilebilirlik Düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [Değiştiriciler](../../../csharp/language-reference/keywords/modifiers.md)  
 [public](../../../csharp/language-reference/keywords/public.md)  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 [internal](../../../csharp/language-reference/keywords/internal.md)
