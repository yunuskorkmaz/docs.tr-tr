---
title: Erişilebilirlik Düzeylerinin Kullanılmasındaki Kısıtlamalar (C# Başvurusu)
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
ms.openlocfilehash: fd2f9b11523aac1cb720559db44aa36029d52ddb
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960911"
---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a>Erişilebilirlik Düzeylerinin Kullanılmasındaki Kısıtlamalar (C# Başvurusu)
Bir bildirim türü belirttiğinizde, türün erişilebilirlik düzeyi erişilebilirlik düzeyine üyesi veya başka bir türe bağımlı olup olmadığını denetleyin. Örneğin, doğrudan temel sınıf en az türetilen sınıf olarak olarak erişilebilir olması gerekir. Aşağıdaki bildirimleri için bir derleyici hatasına neden temel sınıf `BaseClass` daha az erişilebilir `MyClass`:  
  
```csharp  
class BaseClass {...}  
public class MyClass: BaseClass {...} // Error  
```  
  
 Bildirilen erişilebilirlik düzeyi kısıtlamaları aşağıdaki tabloda özetlenmiştir.  
  
|Bağlam|Açıklamalar|  
|-------------|-------------|  
|[Sınıflar](../../../csharp/programming-guide/classes-and-structs/classes.md)|Bir sınıf türünün doğrudan temel sınıf en az sınıf türü kendisini olarak erişilebilir olması gerekir.|  
|[Arabirimler](../../../csharp/programming-guide/interfaces/index.md)|Açık bir arabirim türü temel arabirimleri en az arabirim türü kendisini olarak erişilebilir olması gerekir.|  
|[Temsilciler](../../../csharp/programming-guide/delegates/index.md)|Bir temsilci türü parametre türleri ve dönüş türü, en az temsilci türü kendisini olarak erişilebilir olması gerekir.|  
|[Sabitler](../../../csharp/programming-guide/classes-and-structs/constants.md)|Bir sabit değer türü en az sabit olarak olarak erişilebilir olması gerekir.|  
|[Alanlar](../../../csharp/programming-guide/classes-and-structs/fields.md)|Bir alan türü en az alan olarak olarak erişilebilir olması gerekir.|  
|[Yöntemler](../../../csharp/programming-guide/classes-and-structs/methods.md)|Bir yöntemin parametre türleri ve dönüş türü, en az yöntemi olarak olarak erişilebilir olması gerekir.|  
|[Özellikler](../../../csharp/programming-guide/classes-and-structs/properties.md)|Bir özelliğin türünü en az özelliği olarak olarak erişilebilir olması gerekir.|  
|[Olaylar](../../../csharp/programming-guide/events/index.md)|Bir olay türü en az olay olarak olarak erişilebilir olması gerekir.|  
|[Dizin Oluşturucular](../../../csharp/programming-guide/indexers/index.md)|Bir dizin oluşturucu türü ve parametre türleri, en az Indexer olarak erişilebilir olması gerekir.|  
|[İşleçler](../../../csharp/programming-guide/statements-expressions-operators/operators.md)|Operatör için parametre türleri ve dönüş türü, en azından operatör olarak olarak erişilebilir olması gerekir.|  
|[Oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md)|Parametre türleri bir oluşturucunun en az Oluşturucu olarak olarak erişilebilir olması gerekir.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, farklı türlerdeki hatalı bildirimi içerir. Her bildiriminin açıklama beklenen derleyici hata olduğunu gösterir.  
  
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
