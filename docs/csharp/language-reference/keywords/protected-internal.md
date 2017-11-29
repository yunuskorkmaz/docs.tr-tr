---
title: "korumalı iç (C# Başvurusu)"
ms.date: 11/15/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
author: sputier
ms.author: wiwagn
ms.openlocfilehash: f9004a5e8d65179c9ff2e30688e63c14c95ab431
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2017
---
# <a name="protected-internal-c-reference"></a>korumalı iç (C# Başvurusu)
`protected internal` Anahtar sözcüğü birleşimi olan bir üye erişim değiştiricisi. Korumalı bir iç üye geçerli derlemesinden veya içeren sınıfından türetilen türlerden erişilebilir. Bir karşılaştırması `protected internal` diğer erişim değiştiricileri ile bkz [erişilebilirlik düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md). 
   
## <a name="example"></a>Örnek  
 Bir taban sınıfın korumalı bir iç üye içeren derleme içinde herhangi bir türü erişilebilir. Yalnızca türetilmiş sınıf türünde bir değişken erişim oluşursa, başka bir derlemesinde bulunan bir türetilmiş sınıfta da erişilebilir. Örneğin, aşağıdaki kod kesimi göz önünde bulundurun:  

```
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
  
```  
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
 Bu örnek iki dosya içerir `Assembly1.cs` ve `Assembly2.cs`. İlk dosya ortak bir taban sınıf içeren `BaseClass`ve başka bir sınıf `TestAccess`. `BaseClass`korumalı bir iç üye sahibi `myValue`, tarafından erişilen `TestAccess` türü. İkinci dosyasında, erişme denemesi `myValue` örneği üzerinden `BaseClass` türetilmiş bir sınıf örneği üzerinden bu üye için bir erişim sırasında bir hata üretecektir `DerivedClass` başarılı olur. 

 Yapı üyeleri olamaz `protected internal` yapısı devraldığından.  
  
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
 [Özel](../../../csharp/language-reference/keywords/private.md)   
 [İç](../../../csharp/language-reference/keywords/internal.md)   
 [İç sanal anahtar ile ilgili güvenlik konuları](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))
