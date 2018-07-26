---
title: korumalı iç (C# Başvurusu)
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 5ba2c811a1a4f095bcee65ed6678a7dc50fe94db
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/25/2018
ms.locfileid: "39244864"
---
# <a name="protected-internal-c-reference"></a>korumalı iç (C# Başvurusu)
`protected internal` Anahtar sözcüğü bir üye erişim değiştiricisi oluşur. Korumalı bir iç üye geçerli derleme veya içeren sınıfından türetilen türler erişilebilir. Bir karşılaştırması `protected internal` diğer erişim değiştiricileri ile bkz [erişilebilirlik düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md). 
   
## <a name="example"></a>Örnek  
 Bir taban sınıfın korumalı bir iç üye içeren kendi derlemesi içindeki herhangi bir türü erişilebilir. Yalnızca türetilmiş sınıf türünde bir değişken erişim oluşması durumunda başka bir derlemede bulunan türetilen bir sınıfta da erişilebilir. Örneğin, aşağıdaki kod kesimi göz önünde bulundurun:  

```csharp
// Assembly1.cs  
// Compile with: /target:library  
public class BaseClass   
{  
   protected internal int myValue = 0;  
}

class TestAccess 
{
    void Access()
    {
        BaseClass baseObject = new BaseClass();
        baseObject.myValue = 5;
    }
}  
```  
  
```csharp  
// Assembly2.cs  
// Compile with: /reference:Assembly1.dll  
class DerivedClass : BaseClass   
{  
    static void Main()
    {
        BaseClass baseObject = new BaseClass();
        DerivedClass derivedObject = new DerivedClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 10; 

        // OK, because this class derives from BaseClass.
        derivedObject.myValue = 10;
    }
} 
```  
 Bu örnek iki dosyayı içeren `Assembly1.cs` ve `Assembly2.cs`. İlk dosyayı içeren genel bir temel sınıf `BaseClass`ve başka bir sınıf `TestAccess`. `BaseClass` korumalı bir iç üye sahibi `myValue`, tarafından erişilen `TestAccess` türü. İkinci dosyasında, erişme denemesi `myValue` örneği üzerinden `BaseClass` bu üyeye türetilmiş bir sınıfın bir örnek üzerinden erişim sırasında bir hata üretecektir `DerivedClass` başarılı olur. 

 Yapı üyeleri olamaz `protected internal` struct devraldığından.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)   
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)   
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)   
 [Erişim değiştiricileri](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [Erişilebilirlik düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md)   
 [Değiştiriciler](../../../csharp/language-reference/keywords/modifiers.md)   
 [Genel](../../../csharp/language-reference/keywords/public.md)   
 [Özel](../../../csharp/language-reference/keywords/private.md)   
 [İç](../../../csharp/language-reference/keywords/internal.md)   
 [İç sanal anahtar sözcükleri ile ilgili güvenlik konuları](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))
