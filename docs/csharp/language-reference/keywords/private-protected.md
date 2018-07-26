---
title: private protected (C# Başvurusu)
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 0d511f55f44511590fbe92a98cef118e0cb482e2
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37961138"
---
# <a name="private-protected-c-reference"></a>private protected (C# Başvurusu)
`private protected` Anahtar sözcüğü bir üye erişim değiştiricisi oluşur. Özel bir korumalı üye, kapsayan sınıfı ancak kendi içeren bütünleştirilmiş kod içinde yalnızca türetilen türler tarafından erişilebilir. Bir karşılaştırması `private protected` diğer erişim değiştiricileri ile bkz [erişilebilirlik düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md). 

> [!NOTE]
> `private protected` Erişim değiştiricisi geçerli sürümde C# 7.2 ve üzeri.
   
## <a name="example"></a>Örnek  
 Yalnızca statik değişken türü türetilmiş sınıf türü ise bir taban sınıfın özel ve korumalı bir üye türetilen türler, içeren derlemede erişilebilir. Örneğin, aşağıdaki kod kesimi göz önünde bulundurun:  
  
 ```csharp
 // Assembly1.cs  
 // Compile with: /target:library  
 public class BaseClass
 {
     private protected int myValue = 0;
 }
 
 public class DerivedClass1 : BaseClass
 {
     void Access()
     {
         BaseClass baseObject = new BaseClass();
 
         // Error CS1540, because myValue can only be accessed by
         // classes derived from BaseClass.
         // baseObject.myValue = 5;  
 
         // OK, accessed through the current derived class instance
         myValue = 5;
     }
 }
```  
  
```csharp  
 // Assembly2.cs  
 // Compile with: /reference:Assembly1.dll  
 class DerivedClass2 : BaseClass
 {
     void Access()
     {
         // Error CS0122, because myValue can only be
         // accessed by types in Assembly1
         // myValue = 10;
     }
 }
```  
 Bu örnek iki dosyayı içeren `Assembly1.cs` ve `Assembly2.cs`. İlk dosyayı içeren genel bir temel sınıf `BaseClass`ve bu türden türetilmiş tür `DerivedClass1`. `BaseClass` özel bir korumalı üye sahibi `myValue`, hangi `DerivedClass1` iki yolla erişmeyi dener. Erişmek için yapılan ilk girişim `myValue` örneği üzerinden `BaseClass` hataya neden olur. Ancak, devralınan bir üyesi olarak kullanma girişimi `DerivedClass1` başarılı olur.
İkinci dosyasında, erişme denemesi `myValue` devralınan bir üyesi olarak `DerivedClass2` yalnızca Assembly1 türetilmiş türleri tarafından erişilebilir olduğundan bir hata üretecektir. 

 Yapı üyeleri olamaz `private protected` struct devraldığından.  
  
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
