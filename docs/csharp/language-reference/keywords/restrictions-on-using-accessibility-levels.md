---
title: Erişilebilirlik Düzeylerinin Kullanılmasındaki Kısıtlamalar (C# Başvurusu)
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
ms.openlocfilehash: fd2f9b11523aac1cb720559db44aa36029d52ddb
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a>Erişilebilirlik Düzeylerinin Kullanılmasındaki Kısıtlamalar (C# Başvurusu)
Bir bildiriminde bir türü belirttiğinizde, türü erişilebilirlik düzeyi erişilebilirlik düzeyinde bir üye veya başka bir türde bağımlı olup olmadığını denetleyin. Örneğin, doğrudan temel sınıf en az türetilmiş sınıf olarak erişilebilir olmalıdır. Aşağıdaki bildirimler için derleyici hatası neden temel sınıfı `BaseClass` daha az erişilebilen `MyClass`:  
  
```csharp  
class BaseClass {...}  
public class MyClass: BaseClass {...} // Error  
```  
  
 Aşağıdaki tabloda bildirilen erişilebilirlik düzeyi kısıtlamaları özetlenir.  
  
|Bağlam|Açıklamalar|  
|-------------|-------------|  
|[Sınıflar](../../../csharp/programming-guide/classes-and-structs/classes.md)|Sınıf türü doğrudan temel sınıfını en az sınıf türü kendisi olarak erişilebilir olmalıdır.|  
|[Arabirimler](../../../csharp/programming-guide/interfaces/index.md)|Bir arabirim türünün açık temel arabirimler en az arabirim türü kendisi olarak erişilebilir olmalıdır.|  
|[Temsilciler](../../../csharp/programming-guide/delegates/index.md)|Dönüş türü ve bir temsilci türü parametre türleri, en az temsilci türü olarak kendisi olarak erişilebilir olması gerekir.|  
|[Sabitler](../../../csharp/programming-guide/classes-and-structs/constants.md)|Bir sabit türü en az sabit olarak olarak erişilebilir olmalıdır.|  
|[Alanlar](../../../csharp/programming-guide/classes-and-structs/fields.md)|Bir alan türü en az alan olarak olarak erişilebilir olmalıdır.|  
|[Yöntemler](../../../csharp/programming-guide/classes-and-structs/methods.md)|Bir yöntemin parametre türleri ve dönüş türü, en az yöntemi olarak olarak erişilebilir olması gerekir.|  
|[Özellikler](../../../csharp/programming-guide/classes-and-structs/properties.md)|Bir özelliğin türünü en az özelliği olarak olarak erişilebilir olmalıdır.|  
|[Olaylar](../../../csharp/programming-guide/events/index.md)|Bir olay türü en az olayı olarak olarak erişilebilir olmalıdır.|  
|[Dizin Oluşturucular](../../../csharp/programming-guide/indexers/index.md)|Bir dizin oluşturucu türü ve parametre türleri en az dizinleyici olarak erişilebilir olmalıdır.|  
|[İşleçler](../../../csharp/programming-guide/statements-expressions-operators/operators.md)|Dönüş türü ve bir işleç parametre türleri, en azından operatör olarak olarak erişilebilir olması gerekir.|  
|[Oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md)|Bir oluşturucu parametre türleri en az oluşturucusu olarak erişilebilir olmalıdır.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, farklı türlerde hatalı bildirimleri içerir. Her bildirim aşağıdaki açıklama beklenen derleyici hatası gösterir.  
  
```csharp  
// Restrictions on Using Accessibility Levels  
// CS0052 expected as well as CS0053, CS0056, and CS0057  
// To make the program work, change access level of both class B  
// and MyPrivateMethod() to public.  
  
using System;  
  
// A delegate:  
delegate int MyDelegate();  
  
class B  
{  
    // A private method:  
    static int MyPrivateMethod()  
    {  
        return 0;  
    }  
}  
  
public class A  
{  
    // Error: The type B is less accessible than the field A.myField.  
    public B myField = new B();  
  
    // Error: The type B is less accessible  
    // than the constant A.myConst.  
    public readonly B myConst = new B();  
  
    public B MyMethod()  
    {  
        // Error: The type B is less accessible   
        // than the method A.MyMethod.  
        return new B();  
    }  
  
    // Error: The type B is less accessible than the property A.MyProp  
    public B MyProp  
    {  
        set  
        {  
        }  
    }  
  
    MyDelegate d = new MyDelegate(B.MyPrivateMethod);  
    // Even when B is declared public, you still get the error:   
    // "The parameter B.MyPrivateMethod is not accessible due to   
    // protection level."  
  
    public static B operator +(A m1, B m2)  
    {  
        // Error: The type B is less accessible  
        // than the operator A.operator +(A,B)  
        return new B();  
    }  
  
    static void Main()  
    {  
        Console.Write("Compiled successfully");  
    }  
}  
```  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Erişim Değiştiricileri](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [Erişilebilirlik Etki Alanı](../../../csharp/language-reference/keywords/accessibility-domain.md)  
 [Erişilebilirlik Düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [Erişim Değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [public](../../../csharp/language-reference/keywords/public.md)  
 [private](../../../csharp/language-reference/keywords/private.md)  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 [internal](../../../csharp/language-reference/keywords/internal.md)
