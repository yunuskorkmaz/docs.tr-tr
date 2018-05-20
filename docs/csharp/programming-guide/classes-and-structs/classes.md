---
title: Sınıflar (C# Programlama Kılavuzu)
description: Sınıf türleri ve bunların nasıl oluşturulacağı hakkında bilgi edinin
ms.date: 04/05/2018
helpviewer_keywords:
- classes [C#]
- C# language, classes
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
ms.openlocfilehash: 688736aa8556719789b02d7db25858f442b4309e
ms.sourcegitcommit: 895c7602386a6dfe7ca4facce3d965b27e5c6e87
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2018
---
# <a name="classes-c-programming-guide"></a>Sınıflar (C# Programlama Kılavuzu)
A *sınıfı* değişkenleri diğer türleri, yöntemleri ve olayları bir arada gruplandırma tarafından kendi özel türler oluşturmanızı sağlayan bir yapıdır. Şeması gibi bir sınıftır. Veri ve türü davranışını tanımlar. Sınıf static olarak bildirilmedi, istemci kodu oluşturabilirsiniz *örnekleri* bunu. Bu örnekleri *nesneleri* bir değişkene atanır. Bir sınıf örneği kapsamının dışında tüm başvuruları oluncaya kadar bellekte kalır. O anda CLR, atık toplama için uygun olarak işaretler. Sınıf olarak bildirilirse [statik](../../../csharp/language-reference/keywords/static.md)örnekleri oluşturulamıyor ve istemci kodu yalnızca erişebileceği sınıfı aracılığıyla. Daha fazla bilgi için bkz: [statik sınıflar ve statik sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  

## <a name="reference-types"></a>Başvuru türleri  
Olarak tanımlanan bir tür bir [sınıfı](../../../csharp/language-reference/keywords/class.md) olan bir *başvuru türüne*. Ne zaman bildirdiğiniz başvuru türünde bir değişken, çalışma zamanında değişken değeri içeren [null](../../../csharp/language-reference/keywords/null.md) açıkça sınıfının bir örneğini kullanarak oluşturduğunuz kadar [yeni](../../../csharp/language-reference/keywords/new.md) işleci, veya bir nesne atama, başka bir yerde, aşağıdaki örnekte gösterildiği gibi oluşturuldu:

```csharp
MyClass mc = new MyClass();
MyClass mc2 = mc;
```

Nesne oluşturulduğunda, bellek yönetilen yığında ayrılan ve yalnızca bir nesnenin konumunu başvuru değişkeni içerir. Yönetilen yığın türlerinde gerektiren ek yükü bunlar ayırırken hem olarak adlandırılıyor CLR otomatik bellek yönetimi işlevselliğini tarafından talep edilen zaman *çöp toplama*. Ancak, atık toplama ayrıca getirilmiş ve çoğu senaryoda, bir performans sorunu oluşturmaz. Çöp toplama hakkında daha fazla bilgi için bkz: [otomatik bellek yönetimi ve çöp toplama](../../../standard/garbage-collection/gc.md).  
  
## <a name="declaring-classes"></a>Sınıfları Bildirme  
 Sınıfları kullanarak bildirildiğinde [sınıfı](../../../csharp/language-reference/keywords/class.md) anahtar sözcüğü, aşağıdaki örnekte gösterildiği gibi:

 ```csharp
 public class Customer
 {
    // Fields, properties, methods and events go here...
 }
```

 `class` Anahtar sözcüğü erişim düzeyi tarafından öncesinde. Çünkü [ortak](../../../csharp/language-reference/keywords/public.md) kullanılan herkes bu sınıfın örnekleri, bu durumda, oluşturabilirsiniz. Sınıf adı `class` anahtar sözcüğü. Davranış ve veri tanımlandığı sınıf gövdesi tanımı kalanı var. Alanlar, özellikleri, yöntemleri ve bir sınıf olaylarına topluca denir *sınıfı üyeleri*.  
  
## <a name="creating-objects"></a>Nesne Oluşturma  
 Bazen birbirinin yerine kullanıldığı rağmen sınıf ve nesne farklı noktalardır. Bir sınıf nesne türünü tanımlar, ancak bir nesne değil. Bir nesne sınıfına göre somut bir varlık ve bazen sınıfının bir örneği da adlandırılır.  
  
 Nesneleri kullanarak oluşturulabilir [yeni](../../../csharp/language-reference/keywords/new.md) nesne, temel sınıfın adını ve ardından anahtar sözcüğü şöyle:  

 ```csharp
 Customer object1 = new Customer();
 ```
  
 Sınıfının bir örneği oluşturulduğunda, nesneye bir başvurusu Programcı geri gönderilir. Önceki örnekte, `object1` temel alan bir nesneye bir başvurusu olan `Customer`. Bu başvuru, yeni bir nesneye başvuruyor ancak nesne verileri içermiyor. Aslında, bir nesne başvurusu bir nesnenin oluşturmadan oluşturabilirsiniz:  
  
  ```csharp
  Customer object2;
  ```
  
 Böyle bir başvuru bir nesneye erişilmeye çalışılırken çalışma zamanında başarısız olacağı için bir nesneye başvuran yok nesne başvuruları bunun gibi oluşturmanızı öneririz yok. Ancak, böyle bir başvuru bir nesne, yeni bir nesne oluşturma veya bu gibi varolan bir nesne atama başvurmak için yapılabilir:  

 ```csharp
 Customer object3 = new Customer();
 Customer object4 = object3;
 ```
  
 Bu kod iki nesne başvuruları oluşturan her ikisi de aynı nesneye başvuruyor. Bu nedenle, herhangi bir değişiklik üzerinden yapılan nesne `object3` içinde sonraki kullanımlarını yansıtılır `object4`. Sınıflara göre nesneleri başvuruya göre adlandırılır çünkü sınıfları başvuru türleri olarak bilinir.  
  
## <a name="class-inheritance"></a>Sınıf Devralma  

 Sınıfları tam destek *devralma*, nesne odaklı programlama temel bir özelliğidir. Bir sınıf oluşturduğunuzda, herhangi bir arabirim veya olarak tanımlanmamış sınıfı devralabilirsiniz [korumalı](../../../csharp/language-reference/keywords/sealed.md), ve diğer sınıflar, sınıfından devralınır ve sınıf sanal yöntemlerini geçersiz kılar.

 Devralma kullanarak gerçekleştirilir bir *türetme*, bir sınıfın başka bir deyişle, kullanarak bildirilmiş bir *temel sınıfı* aldığı veri ve davranış devralır. Bir taban sınıf, bir iki nokta üst üste ve bu gibi türetilmiş sınıf adı şu temel sınıfın adını ekleyerek belirtilmiştir:  

 ```csharp
 public class Manager : Employee
 {
     // Employee fields, properties, methods and events are inherited
     // New Manager fields, properties, methods and events go here...
 }
 ```
  
 Bir sınıf bir taban sınıf bildirir, Oluşturucular dışında temel sınıfın tüm üyeleri devralır. Daha fazla bilgi için bkz: [devralma](../../../csharp/programming-guide/classes-and-structs/inheritance.md).
  
 C++ C# sınıfı yalnızca doğrudan bir temel sınıfı devralabilirsiniz. Ancak, bir temel sınıf kendisini başka bir sınıftan çünkü bir sınıfın birden çok taban sınıfı devralır dolaylı olarak. Ayrıca, bir sınıfın doğrudan birden fazla arabirimi uygulayabilirsiniz. Daha fazla bilgi için bkz: [arabirimleri](../../../csharp/programming-guide/interfaces/index.md).  
  
 Bir sınıf bildirilebilir [soyut](../../../csharp/language-reference/keywords/abstract.md). Bir Özet sınıf bir imza tanımı ancak uygulaması olan soyut yöntemler içerir. Soyut sınıfların örneği oluşturulamıyor. Soyut yöntemler uygulayan türetilmiş sınıflar yalnızca kullanılabilir. Bunun aksine, bir [korumalı](../../../csharp/language-reference/keywords/sealed.md) sınıfı diğer sınıfların buradan türetebilir izin vermez. Daha fazla bilgi için bkz: [soyut ve korumalı sınıflar ve sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
 Sınıf tanımları farklı kaynak dosyalar arasında bölünebilir. Daha fazla bilgi için bkz: [kısmi sınıflar ve yöntemler](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek içeren genel bir sınıf tanımlayan bir [otomatik uygulanan özelliği](auto-implemented-properties.md), yöntemi ve bir oluşturucu adlı özel bir yöntem. Daha fazla bilgi için bkz: [özellikleri](properties.md), [yöntemleri](methods.md), ve [oluşturucular](constructors.md) Konular. Sınıfın örnekleri, ile örneği oluşturulmadan `new` anahtar sözcüğü.  
  
 [!code-csharp[Class Example](~/samples/snippets/csharp/programming-guide/classes-and-structs/class-example.cs)] 
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Nesne Odaklı Programlama](../concepts/object-oriented-programming.md)  
 [Çok biçimlilik](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)  
 [Üyeler](../../../csharp/programming-guide/classes-and-structs/members.md)  
 [Yöntemler](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [Oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [Sonlandırıcılar](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
 [Nesneler](../../../csharp/programming-guide/classes-and-structs/objects.md)
