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
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960813"
---
# <a name="private-c-reference"></a>private (C# Başvurusu)
`private` Anahtar sözcüğü, bir üye erişim değiştiricisi. 
   
 > Bu sayfa kapsayan `private` erişim. `private` Anahtar sözcüğü, ayrıca parçası [ `private protected` ](./private-protected.md) erişim değiştiricisi.
  
Özel erişim en katı erişim düzeyidir. Özel üyeler, yalnızca sınıf veya yapı içinde bu örnekte olduğu gibi bildirildikleri gövdesi içinde erişilebilir:  
  
```csharp  
class Employee  
{  
    private int i;  
    double d;   // private access by default  
}  
```  

 İç içe geçmiş türler aynı gövdesinde, bu özel üyeler de erişebilirsiniz.  
  
 Bu sınıf veya yapı birimi içinde bildirildiği dışındaki özel üye başvurmak için bir derleme zamanı hatasıdır.  
  
 Bir karşılaştırması `private` diğer erişim değiştiricileri ile bkz [erişilebilirlik düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md) ve [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
## <a name="example"></a>Örnek  
 Bu örnekte, `Employee` sınıfı içeren iki özel veri üyeleri, `name` ve `salary`. Özel üyeler bunlar dışında üye yöntemleri tarafından erişilemez. Genel yöntemler adlı `GetName` ve `Salary` özel üyeler denetimli erişim izni vermek için eklenir. `name` Genel bir yöntem aracılığıyla erişilen üyenin ve `salary` genel bir salt okunur özelliği yoluyla erişilen üyenin. (Bkz [özellikleri](../../../csharp/programming-guide/classes-and-structs/properties.md) daha fazla bilgi için.)  
  
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
