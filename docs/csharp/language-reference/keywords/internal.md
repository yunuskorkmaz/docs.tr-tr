---
title: internal (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: 54ec003683953b53dedf8885a41350daf5338f83
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43523367"
---
# <a name="internal-c-reference"></a>internal (C# Başvurusu)
`internal` Anahtar sözcüğü bir [erişim değiştiricisi](../../../csharp/language-reference/keywords/access-modifiers.md) türler ve tür üyeleri için. 
  
 > Bu sayfa kapsayan `internal` erişim. `internal` Anahtar sözcüğü, ayrıca parçası [ `protected internal` ](./protected-internal.md) erişim değiştiricisi.
  
İç türleri veya üyeleri yalnızca bu örnekte olduğu gibi aynı derleme dosyalarında erişilebilir:  
  
```csharp  
public class BaseClass   
{  
    // Only accessible within the same assembly  
    internal static int x = 0;  
}  
```  

 Bir karşılaştırması `internal` diğer erişim değiştiricileri ile bkz [erişilebilirlik düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md) ve [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Derlemeler hakkında daha fazla bilgi için bkz. [derlemeler ve genel derleme önbelleği](../../../csharp/programming-guide/concepts/assemblies-gac/index.md).  
  
 Bir grup için uygulama kodunun kalanı görmeden özel bir şekilde işbirliği bileşenlerinin sağladığından bir ortak iç erişim bileşeni tabanlı geliştirme kullanılır. Örneğin, grafik kullanıcı arabirimleri oluşturmaya yönelik bir çerçeve sağlayabilir `Control` ve `Form` iç erişimle üyeleri kullanarak iş Birliği sınıfları. Bu üyeleri iç olduğundan, framework kullanan kodu sunulmaz.  
  
 Bu bir tür veya üye, içinde tanımlandı derleme dışından iç erişimle başvurmak için bir hatadır.  
  
## <a name="example"></a>Örnek  
 Bu örnek iki dosyayı içeren `Assembly1.cs` ve `Assembly1_a.cs`. İlk dosya içeren bir iç temel sınıf `BaseClass`. İkinci örneğini oluşturma girişiminde dosyasında `BaseClass` hataya neden olur.  
  
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
 Bu örnekte, örnek 1 kullanılan de indirdiğiniz dosyaları kullanarak ve erişilebilirlik düzeyini değiştirme `BaseClass` için `public`. Ayrıca üyenin erişilebilirlik düzeyi değiştirme `IntM` için `internal`. Bu durumda, sınıfın örneğini oluşturabilir, ancak iç üyeye erişemez.  
  
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
// Compile with: /reference:Assembly2.dll  
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

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
- [Erişim Değiştiricileri](../../../csharp/language-reference/keywords/access-modifiers.md)  
- [Erişilebilirlik Düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md)  
- [Değiştiriciler](../../../csharp/language-reference/keywords/modifiers.md)  
- [public](../../../csharp/language-reference/keywords/public.md)  
- [private](../../../csharp/language-reference/keywords/private.md)  
- [protected](../../../csharp/language-reference/keywords/protected.md)
