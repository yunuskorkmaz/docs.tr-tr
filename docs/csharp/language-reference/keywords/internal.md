---
title: iç C# başvuru
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: 7d97b7b05645b02a31af848c97758c7a1f6423b9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602076"
---
# <a name="internal-c-reference"></a>internal (C# Başvurusu)
Anahtar `internal` sözcüğü, türler ve tür üyeleri için bir [erişim değiştiricisidir](./access-modifiers.md) . 
  
 > Bu sayfa erişimi `internal` içerir. Anahtar sözcüğü ayrıca [`protected internal`](./protected-internal.md) erişim değiştiricisinin bir parçasıdır. `internal`
  
İç türlere veya üyelere, bu örnekte olduğu gibi, yalnızca aynı derlemede bulunan dosyalar içinde erişilebilir:  
  
```csharp  
public class BaseClass   
{  
    // Only accessible within the same assembly.
    internal static int x = 0;
}  
```  

 Diğer erişim değiştiricilerine `internal` kıyasla, bkz. [Erişilebilirlik düzeyleri](./accessibility-levels.md) ve [erişim değiştiricileri](../../programming-guide/classes-and-structs/access-modifiers.md).  
  
 Derlemeler hakkında daha fazla bilgi için bkz. [.net 'Teki derlemeler](../../../standard/assembly/index.md).  
  
 İç erişimin yaygın olarak kullanılması bileşen tabanlı geliştirmede olduğundan, bir grup bileşenin, uygulama kodunun geri kalanında gösterilmeksizin özel bir biçimde birlikte çalışabilmesine olanak sağlar. Örneğin, grafik kullanıcı arabirimleri oluşturmaya yönelik bir çerçeve, iç erişimi `Control` olan `Form` üyeleri kullanarak birlikte çalışan sınıflar sağlayabilir ve sınıflardır. Bu Üyeler iç olduğundan, Framework kullanan koda gösterilmez.  
  
 Bir tür ya da bir üyeye, tanımlandıkları derlemenin dışında iç erişimle başvurulmaları hatadır.  
  
## <a name="example"></a>Örnek  
 Bu örnek, ve `Assembly1.cs` `Assembly1_a.cs`olmak üzere iki dosya içerir. İlk dosya, `BaseClass`bir iç temel sınıf içerir. İkinci dosyada, örnek oluşturma `BaseClass` girişimi bir hata oluşturur.  
  
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
      var myBase = new BaseClass();   // CS0122  
   }  
}  
```  
  
## <a name="example"></a>Örnek  
 Bu örnekte, örnek 1 ' de kullandığınız dosyaları kullanın ve erişilebilirlik düzeyini `BaseClass` olarak `public`değiştirin. Ayrıca üyenin `intM` `internal`erişilebilirlik düzeyini de değiştirin. Bu durumda, sınıfının örneğini oluşturabilirsiniz, ancak iç üyeye erişemezsiniz.  
  
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
      var myBase = new BaseClass();   // Ok.  
      BaseClass.intM = 444;    // CS0117  
   }  
}  
```  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için bkz. [ C# dil belirtiminde](../language-specification/index.md) [Erişilebilirlik bildirimi](~/_csharplang/spec/basic-concepts.md#declared-accessibility) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](./index.md)
- [Erişim Değiştiricileri](./access-modifiers.md)
- [Erişilebilirlik Düzeyleri](./accessibility-levels.md)
- [Değiştiriciler](./modifiers.md)
- [public](./public.md)
- [private](./private.md)
- [protected](./protected.md)
