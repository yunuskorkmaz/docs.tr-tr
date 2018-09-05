---
title: Sınıflar (C# Programlama Kılavuzu)
description: Sınıf türleri ve bunların nasıl oluşturulacağı hakkında bilgi edinin
ms.date: 04/05/2018
helpviewer_keywords:
- classes [C#]
- C# language, classes
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
ms.openlocfilehash: 070288d40501dbaebd5e5fbc27ea53fa1a03df30
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43523166"
---
# <a name="classes-c-programming-guide"></a>Sınıflar (C# Programlama Kılavuzu)
A *sınıfı* diğer türleri, yöntemleri ve olayları değişkenleri birlikte gruplandırarak kendi özel türlerinizde oluşturmanızı sağlayan bir yapıdır. Gibi bir sınıf plandır. Bu, veri ve türü davranışını tanımlar. Sınıfın statik olarak bildirilmedi, istemci kodu oluşturabilirsiniz *örnekleri* bunu. Bu örnekleri *nesneleri* bir değişkene atanır. Bir sınıf örneği, tüm başvuruları kapsam dışına çıkmadan kadar bellekte kalır. Bu sırada, CLR, çöp toplama işlemi için uygun olarak işaretler. Sınıf olarak bildirilirse [statik](../../../csharp/language-reference/keywords/static.md)örnekleri oluşturulamaz ve istemci kodu yalnızca erişebilirsiniz sınıfı aracılığıyla. Daha fazla bilgi için [statik sınıflar ve statik sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  

## <a name="reference-types"></a>Başvuru türleri  
Olarak tanımlanan bir tür bir [sınıfı](../../../csharp/language-reference/keywords/class.md) olduğu bir *başvuru türüne*. Bir değişken bildirdiğinizde başvuru türü, çalışma zamanında değişken değeri içeren [null](../../../csharp/language-reference/keywords/null.md) açıkça kullanarak sınıfının bir örneğini oluşturana kadar [yeni](../../../csharp/language-reference/keywords/new.md) işleci veya bir nesne atama bir başka bir yerde, aşağıdaki örnekte gösterildiği gibi oluşturulmuş olabilir uyumlu türü:

```csharp
//Declaring a object of type MyClass.
MyClass mc = new MyClass();

//Declaring another object of the same type, assigning it the value of the first object.
MyClass mc2 = mc;
```

Nesne oluşturulduğunda, yeterli bellek, belirli bir nesnesi için yönetilen yığında ayrılır ve değişken yalnızca söz konusu nesnenin konumuna yönelik bir başvuru tutar. Yönetilen yığındaki türler ayrıldıkları zaman hem olarak da bilinen CLR'nin otomatik bellek yönetimi işlevinin tarafından talep edilen zaman ek yükü gerektirir *çöp toplama*. Ancak, çöp toplama yüksek oranda iyileştirilmiştir ve çoğu senaryoda, bir performans sorununa neden olmaz. Çöp toplama hakkında daha fazla bilgi için bkz: [otomatik bellek yönetimi ve çöp toplama](../../../standard/garbage-collection/gc.md).  
  
## <a name="declaring-classes"></a>Sınıfları Bildirme  
 Sınıfları kullanarak bildirilir [sınıfı](../../../csharp/language-reference/keywords/class.md) benzersiz bir tanımlayıcı aşağıdaki örnekte gösterildiği gibi anahtar sözcüğünü:

 ```csharp
//[access modifier] - [class] - [identifier]
 public class Customer
 {
    // Fields, properties, methods and events go here...
 }
```

 `class` Anahtar sözcüğü erişim düzeyi tarafından öncesinde. Çünkü [genel](../../../csharp/language-reference/keywords/public.md) kullanılan herkes bu sınıfın örnekleri, bu durumda, oluşturabilirsiniz. Sınıf adını izleyen `class` anahtar sözcüğü. Tanımı geri kalanında sınıfı, davranış ve veri tanımlandığı gövdesidir. Alanlar, özellikler, yöntemler ve olaylar sınıfta topluca denir *sınıf üyeleri*.  
  
## <a name="creating-objects"></a>Nesne Oluşturma  
 Bazen kavramlarının birbirinin yerine kullanıldığı olsa da, bir sınıf ve nesne farklı noktalardır. Bir nesne türüyle bir sınıf tanımlar, ancak bir nesne değil. Bir nesne sınıfına göre somut bir varlık ve bazen bir sınıfın bir örneği da adlandırılır.  
  
 Nesneleri kullanarak oluşturulabilir [yeni](../../../csharp/language-reference/keywords/new.md) anahtar sözcüğü bir nesne, temel sınıfın adını ardından şöyle:  

 ```csharp
 Customer object1 = new Customer();
 ```
  
 Bir sınıfın bir örneği oluşturulduğunda nesnesine bir başvuru programcıya geçirilir. Önceki örnekte, `object1` temel alan bir nesneye bir başvurudur `Customer`. Bu başvuru yeni bir nesneye başvuruyor, ancak nesne verisi içermiyor. Aslında, bir nesne başvurusu bir nesne oluşturulmadan oluşturabilirsiniz:  
  
  ```csharp
  Customer object2;
  ```
  
 Bunun gibi bir nesne gibi bir başvuru erişmeye çalışıyor, çalışma zamanında başarısız olacağı için bir nesneye başvuran olmayan nesne başvuruları oluşturmak önerilmemektedir. Ancak, bir nesneye yeni bir nesne oluşturarak veya atayarak bu gibi varolan bir nesneye başvurmak için böyle bir başvuruyu yapılabilir:  

 ```csharp
 Customer object3 = new Customer();
 Customer object4 = object3;
 ```
  
 Bu kod, iki nesne başvuru oluşturur hem de aynı nesneye başvurur. Bu nedenle, nesne aracılığıyla yapılan değişiklikleri `object3` sonraki kullanımları içinde yansıtılır `object4`. Sınıflara göre nesneleri başvuruya göre adlandırılır çünkü sınıflar başvuru türleri olarak bilinir.  
  
## <a name="class-inheritance"></a>Sınıf Devralma  

 Sınıfları tam destek *devralma*, nesne yönelimli programlama temel bir özelliğidir. Bir sınıf oluşturduğunuz zaman, herhangi bir arabirim veya tanımlanmamış sınıfı devralabilirsiniz [korumalı](../../../csharp/language-reference/keywords/sealed.md), ve diğer sınıflar, sizin sınıfınızdan miras ve sınıf sanal yöntemleri geçersiz kılın.

 Devralma kullanılarak gerçekleştirilir bir *türetme*, yani bir sınıf kullanılarak bildirilen bir *temel sınıfı* aldığı verilerini ve davranışlarını devralır. Bir temel sınıf, bir iki nokta üst üste ve bunun gibi türetilmiş sınıf adını izleyen temel sınıfın adını ekleyerek belirtilir:  

 ```csharp
 public class Manager : Employee
 {
     // Employee fields, properties, methods and events are inherited
     // New Manager fields, properties, methods and events go here...
 }
 ```
  
 Bir sınıf bir taban sınıfı bildirir, temel sınıf oluşturucuları dışındaki tüm üyelerini devralır. Daha fazla bilgi için [devralma](../../../csharp/programming-guide/classes-and-structs/inheritance.md).
  
 C++ programında farklı olarak, C# ' ta bir sınıf yalnızca doğrudan bir taban sınıftan devralabilir. Ancak, bir temel sınıf kendisi başka bir sınıftan devralabilir olduğundan, bir sınıf dolaylı olarak birden çok taban sınıfı devralabilir. Ayrıca, bir sınıf doğrudan birden fazla arabirim uygulayabilir. Daha fazla bilgi için [arabirimleri](../../../csharp/programming-guide/interfaces/index.md).  
  
 Bir sınıf bildirilebilir [soyut](../../../csharp/language-reference/keywords/abstract.md). Bir Özet sınıf, bir imza tanımı ancak hiçbir uygulama soyut yöntemler içerir. Soyut sınıflar oluşturulamaz. Soyut yöntemlerini uygulayan türetilmiş sınıfları yalnızca kullanılabilir. Bunun aksine, bir [korumalı](../../../csharp/language-reference/keywords/sealed.md) sınıfı diğer sınıfların türetmeniz izin vermez. Daha fazla bilgi için [soyut ve korumalı sınıflar ve sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
 Sınıf tanımları farklı kaynak dosyaları arasında bölünebilir. Daha fazla bilgi için [kısmi sınıflar ve yöntemler](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, içeren genel bir sınıf tanımlar. bir [otomatik uygulanan özellik](auto-implemented-properties.md), bir yöntem ve oluşturucu olarak adlandırılan özel bir yöntem. Daha fazla bilgi için [özellikleri](properties.md), [yöntemleri](methods.md), ve [oluşturucular](constructors.md) konuları. Sınıf örnekleri, ile örneği oluşturulur `new` anahtar sözcüğü.  
  
 [!code-csharp[Class Example](~/samples/snippets/csharp/programming-guide/classes-and-structs/class-example.cs)] 
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Nesne Odaklı Programlama](../concepts/object-oriented-programming.md)  
- [Çok biçimlilik](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)  
- [Üyeler](../../../csharp/programming-guide/classes-and-structs/members.md)  
- [Yöntemler](../../../csharp/programming-guide/classes-and-structs/methods.md)  
- [Oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
- [Sonlandırıcılar](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
- [Nesneler](../../../csharp/programming-guide/classes-and-structs/objects.md)
