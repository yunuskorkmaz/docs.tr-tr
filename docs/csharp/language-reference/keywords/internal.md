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
ms.openlocfilehash: f72866cafbf291310d88fc6f18a5a15dc77c621d
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422722"
---
# <a name="internal-c-reference"></a>internal (C# Başvurusu)
`internal` anahtar sözcüğü, türler ve tür üyeleri için bir [erişim değiştiricisidir](./access-modifiers.md) . 
  
 > Bu sayfa `internal` erişimi içerir. `internal` anahtar sözcüğü ayrıca [`protected internal`](./protected-internal.md) erişim değiştiricisinin bir parçasıdır.
  
İç türlere veya üyelere, bu örnekte olduğu gibi, yalnızca aynı derlemede bulunan dosyalar içinde erişilebilir:  
  
```csharp  
public class BaseClass   
{  
    // Only accessible within the same assembly.
    internal static int x = 0;
}  
```  

 Diğer erişim değiştiricilerine sahip `internal` bir karşılaştırması için bkz. [Erişilebilirlik düzeyleri](./accessibility-levels.md) ve [erişim değiştiricileri](../../programming-guide/classes-and-structs/access-modifiers.md).  
  
 Derlemeler hakkında daha fazla bilgi için bkz. [.net 'Teki derlemeler](../../../standard/assembly/index.md).  
  
 İç erişimin yaygın olarak kullanılması bileşen tabanlı geliştirmede olduğundan, bir grup bileşenin, uygulama kodunun geri kalanında gösterilmeksizin özel bir biçimde birlikte çalışabilmesine olanak sağlar. Örneğin, grafik kullanıcı arabirimleri oluşturmak için bir çerçeve, iç erişimi olan üyeleri kullanarak birlikte çalışan `Control` ve `Form` sınıfları sağlayabilir. Bu Üyeler iç olduğundan, Framework kullanan koda gösterilmez.  
  
 Bir tür ya da bir üyeye, tanımlandıkları derlemenin dışında iç erişimle başvurulmaları hatadır.  
  
## <a name="example"></a>Örnek  
 Bu örnek, `Assembly1.cs` ve `Assembly1_a.cs`iki dosya içerir. İlk dosya, `BaseClass`iç temel sınıf içerir. İkinci dosyada `BaseClass` örneğini oluşturma girişimi bir hata oluşturacaktır.  
  
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
 Bu örnekte, örnek 1 ' de kullandığınız dosyaları kullanın ve `BaseClass` erişilebilirlik düzeyini `public`olarak değiştirin. Ayrıca üye `intM` erişilebilirlik düzeyini `internal`olarak değiştirin. Bu durumda, sınıfının örneğini oluşturabilirsiniz, ancak iç üyeye erişemezsiniz.  
  
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

Daha fazla bilgi için bkz. [ C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Erişilebilirlik bildirimi](~/_csharplang/spec/basic-concepts.md#declared-accessibility) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](./index.md)
- [Erişim Değiştiricileri](./access-modifiers.md)
- [Erişilebilirlik Düzeyleri](./accessibility-levels.md)
- [Değiştiriciler](index.md)
- [public](./public.md)
- [private](./private.md)
- [protected](./protected.md)
