---
title: internal (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: d2fcc19bb7bc6de373412e7728f3025647c0435d
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
---
# <a name="internal-c-reference"></a>internal (C# Başvurusu)
`internal` Anahtar sözcüğü bir [erişim değiştiricisi](../../../csharp/language-reference/keywords/access-modifiers.md) türleri ve tür üyeleri için. 
  
 > Bu sayfayı kapsayan `internal` erişim. `internal` Sözcüktür ayrıca parçası [ `protected internal` ](./protected-internal.md) erişim değiştiricisi.
  
İç türleri veya üyeleri yalnızca bu örnekte olduğu gibi aynı bütünleştirilmiş kodda dosyalarındaki erişilebilir:  
  
```csharp  
public class BaseClass   
{  
    // Only accessible within the same assembly  
    internal static int x = 0;  
}  
```  

 Bir karşılaştırması `internal` diğer erişim değiştiricileri ile bkz [erişilebilirlik düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md) ve [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Derlemeler hakkında daha fazla bilgi için bkz: [derlemeler ve genel derleme önbelleği](../../../csharp/programming-guide/concepts/assemblies-gac/index.md).  
  
 Uygulama kodu geri kalanı için görmeden özel bir biçimde işbirliği bileşenlerinin bir grup sağladığından bir ortak iç erişim bileşen tabanlı geliştirme kullanılır. Örneğin, grafik kullanıcı arabirimi oluşturmak için bir çerçeve sağlayabilir `Control` ve `Form` iç erişimle üyeleri kullanarak iş Birliği sınıfları. Bu üyeler iç olduğundan, framework kullanarak kod sunulmaz.  
  
 Bir tür veya üye içinde tanımlandı derleme dışına dahili erişime sahip başvurmak için bir hata var.  
  
## <a name="example"></a>Örnek  
 Bu örnek iki dosya içerir `Assembly1.cs` ve `Assembly1_a.cs`. Bir iç temel sınıf ilk dosyasını içeren `BaseClass`. Örneği girişimi ikinci dosyasındaki `BaseClass` hataya neden olur.  
  
```csharp  
// Assembly1.cs  
// Compile with: /target:library  
internal class BaseClass   
{  
   public static int intM = 0;  
}  
```  
  
```csharp  
// Assembly1_a.cs  
// Compile with: /reference:Assembly1.dll  
class TestAccess   
{  
   static void Main()   
   {  
      BaseClass myBase = new BaseClass();   // CS0122  
   }  
}  
```  
  
## <a name="example"></a>Örnek  
 Bu örnekte, 1. örnekte kullanılan aynı dosyaları kullanın ve erişilebilirlik düzeyini değiştirme `BaseClass` için `public`. Ayrıca üye erişilebilirlik düzeyini değiştirme `IntM` için `internal`. Bu durumda, sınıfının örneği, ancak iç üye erişemiyor.  
  
```csharp  
// Assembly2.cs  
// Compile with: /target:library  
public class BaseClass   
{  
   internal static int intM = 0;  
}  
```  
  
```csharp  
// Assembly2_a.cs  
// Compile with: /reference:Assembly1.dll  
public class TestAccess   
{  
   static void Main()   
   {  
      BaseClass myBase = new BaseClass();   // Ok.  
      BaseClass.intM = 444;    // CS0117  
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
 [Erişilebilirlik Düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [Değiştiriciler](../../../csharp/language-reference/keywords/modifiers.md)  
 [public](../../../csharp/language-reference/keywords/public.md)  
 [private](../../../csharp/language-reference/keywords/private.md)  
 [protected](../../../csharp/language-reference/keywords/protected.md)
