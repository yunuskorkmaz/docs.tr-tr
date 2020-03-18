---
title: dahili - C# Referans
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: e5a5ca18828b689241abbb6d80c5adc51efb073c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173607"
---
# <a name="internal-c-reference"></a>internal (C# Başvurusu)
`internal` Anahtar kelime, türler ve tür üyeleri için bir erişim [değiştiricidir.](./access-modifiers.md)
  
 > Bu sayfa `internal` erişimi kapsar. Anahtar `internal` kelime de erişim [`protected internal`](./protected-internal.md) değiştiricinin bir parçasıdır.
  
İç türlere veya üyelere, bu örnekte olduğu gibi, yalnızca aynı derlemedeki dosyalarda erişilebilir:  
  
```csharp  
public class BaseClass
{  
    // Only accessible within the same assembly.
    internal static int x = 0;
}  
```  

 Diğer erişim `internal` değiştiriciler ile karşılaştırma [için, Erişilebilirlik Düzeyleri](./accessibility-levels.md) ve [Erişim Değiştiriciler](../../programming-guide/classes-and-structs/access-modifiers.md)bakın.  
  
 Derlemeler hakkında daha fazla bilgi için [.NET'teki Derlemeler'e](../../../standard/assembly/index.md)bakın.  
  
 Bir grup bileşenin uygulama kodunun geri kalanına maruz kalmadan özel bir şekilde işbirliği yapmalarını sağladığından, dahili erişimin yaygın kullanımı bileşen tabanlı geliştirmededir. Örneğin, grafik kullanıcı arabirimleri oluşturmak için `Control` bir `Form` çerçeve sağlayabilir ve dahili erişim ile üyeleri kullanarak işbirliği sınıfları. Bu üyeler dahili olduğundan, çerçeveyi kullanan koda maruz kalmamış olurlar.  
  
 Bir türe veya dahili erişimi olan bir üyeye, tanımlandığı derleme dışında başvuru yapmak bir hatadır.  
  
## <a name="example"></a>Örnek  
 Bu örnekte iki `Assembly1.cs` `Assembly1_a.cs`dosya ve . İlk dosya bir iç taban `BaseClass`sınıf içerir. İkinci dosyada, anlık bir hata `BaseClass` üretecektir.  
  
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
 Bu örnekte, örnek 1'de kullandığınız aynı dosyaları kullanın ve `BaseClass` erişilebilirlik düzeyini `public`' ye göre değiştirin. Ayrıca üyenin `intM` erişilebilirlik düzeyini `internal`de . Bu durumda, sınıfı anında atabilirsiniz, ancak dahili üyeye erişemezsiniz.  
  
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

Daha fazla bilgi için [C# Dil Belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Bildirilen Erişilebilirlik'e](~/_csharplang/spec/basic-concepts.md#declared-accessibility) bakın. Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](./index.md)
- [Erişim Değiştiricileri](./access-modifiers.md)
- [Erişilebilirlik Düzeyleri](./accessibility-levels.md)
- [Değiştiriciler](index.md)
- [Kamu](./public.md)
- [Özel](./private.md)
- [protected](./protected.md)
