---
title: "internal (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords: internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a3b115022ed2b38dfcfbbfad3c5fc00e0203b255
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="internal-c-reference"></a>internal (C# Başvurusu)
`internal` Anahtar sözcüğü bir [erişim değiştiricisi](../../../csharp/language-reference/keywords/access-modifiers.md) türleri ve tür üyeleri için. 
  
 > Bu sayfayı kapsayan `internal` erişim. `internal` Sözcüktür ayrıca parçası [ `protected internal` ](./protected-internal.md) erişim değiştiricisi.
  
İç türleri veya üyeleri yalnızca bu örnekte olduğu gibi aynı bütünleştirilmiş kodda dosyalarındaki erişilebilir:  
  
```  
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
  
```  
// Assembly1.cs  
// Compile with: /target:library  
internal class BaseClass   
{  
   public static int intM = 0;  
}  
```  
  
```  
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
  
```  
// Assembly2.cs  
// Compile with: /target:library  
public class BaseClass   
{  
   internal static int intM = 0;  
}  
```  
  
```  
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
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Erişim değiştiricileri](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [Erişilebilirlik düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [Değiştiriciler](../../../csharp/language-reference/keywords/modifiers.md)  
 [Ortak](../../../csharp/language-reference/keywords/public.md)  
 [Özel](../../../csharp/language-reference/keywords/private.md)  
 [korumalı](../../../csharp/language-reference/keywords/protected.md)
