---
title: Sınıflar - C# Programlama Kılavuzu
description: Sınıf türleri ve bunları nasıl oluşturabilirsiniz hakkında bilgi edinin
ms.date: 08/21/2018
helpviewer_keywords:
- classes [C#]
- C# language, classes
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
ms.openlocfilehash: d726ab3a882d2e6913fa69c7b82f1d6db78dd47d
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102053"
---
# <a name="classes-c-programming-guide"></a>Sınıflar (C# Programlama Kılavuzu)

## <a name="reference-types"></a>Başvuru türleri  
[Sınıf](../../language-reference/keywords/class.md) olarak tanımlanan bir tür *bir başvuru türüdür.* Çalışma zamanında, bir başvuru türüdeğişkenini beyan ettiğinizde, yeni [işleci](../../language-reference/operators/new-operator.md) kullanarak sınıfın bir örneğini açıkça oluşturana veya aşağıdaki örnekte gösterildiği gibi başka bir yerde oluşturulmuş olabilecek uyumlu bir türe ait bir nesne atayıncaya kadar değişken [geçersiz](../../language-reference/keywords/null.md) değer içerir:

```csharp
//Declaring an object of type MyClass.
MyClass mc = new MyClass();

//Declaring another object of the same type, assigning it the value of the first object.
MyClass mc2 = mc;
```

Nesne oluşturulduğunda, yönetilen yığına belirli bir nesne için yeterli bellek ayrılır ve değişken yalnızca bu nesnenin konumuna bir başvuru tutar. Yönetilen yığındaki türler, hem ayrıldıklarında hem de *çöp toplama*olarak bilinen CLR'nin otomatik bellek yönetimi işlevi tarafından geri alındıklarında ek yükü gerektirir. Ancak, çöp toplama da son derece iyi leştirilmiştir ve çoğu senaryoda bir performans sorunu oluşturmaz. Çöp toplama hakkında daha fazla bilgi için [Otomatik bellek yönetimi ve çöp toplama](../../../standard/garbage-collection/fundamentals.md)bilgisine bakın.  
  
## <a name="declaring-classes"></a>Sınıfları Bildirme

 Sınıflar, aşağıdaki örnekte gösterildiği [gibi, sınıf](../../language-reference/keywords/class.md) anahtar sözcüğü kullanılarak ve ardından benzersiz bir tanımlayıcı kullanılarak bildirilir:

 ```csharp
//[access modifier] - [class] - [identifier]
 public class Customer
 {
    // Fields, properties, methods and events go here...
 }
```

 Anahtar `class` kelimenin önünde erişim düzeyi gelir. Bu durumda [genel](../../language-reference/keywords/public.md) olarak kullanıldığından, herkes bu sınıfın örneklerini oluşturabilir. Sınıfın adı anahtar sözcüğü `class` izler. Sınıfın adı geçerli bir C# [tanımlayıcı adı](../inside-a-program/identifier-names.md)olmalıdır. Tanımın geri kalanı, davranış ve verilerin tanımlandığı sınıf gövdesidir. Bir sınıftaki alanlar, özellikler, yöntemler ve olaylar topluca *sınıf üyeleri*olarak adlandırılır.  
  
## <a name="creating-objects"></a>Nesne oluşturma

Bazen birbirlerinin yerine kullanılmasına rağmen, bir sınıf ve bir nesne farklı şeylerdir. Bir sınıf bir nesne türünü tanımlar, ancak nesnenin kendisi değildir. Nesne, bir sınıfa dayalı somut bir varlıktır ve bazen bir sınıfın örneği olarak adlandırılır.  
  
 Nesneler, nesnenin temel alacağı sınıfın adını izleyen [yeni](../../language-reference/operators/new-operator.md) anahtar sözcük kullanılarak oluşturulabilir:  

 ```csharp
 Customer object1 = new Customer();
 ```

 Bir sınıf örneği oluşturulduğunda, nesneye yapılan bir başvuru programcıya geri aktarılır. Önceki örnekte, `object1` `Customer`'yi temel alan bir nesneye başvuru Bu başvuru yeni nesneye başvurur, ancak nesne verisinin kendisini içermez. Aslında, hiç bir nesne oluşturmadan bir nesne başvurusu oluşturabilirsiniz:  

```csharp
 Customer object2;
```

 Böyle bir başvuru aracılığıyla bir nesneye erişmeye çalışmak çalışma zamanında başarısız olacağından, bir nesneye başvurmadan bunun gibi nesne başvuruları oluşturmanızı önermiyoruz. Ancak, böyle bir başvuru, yeni bir nesne oluşturarak veya aşağıdaki gibi varolan bir nesneye atayarak bir nesneye başvurmak için yapılabilir:  

 ```csharp
 Customer object3 = new Customer();
 Customer object4 = object3;
```
  
 Bu kod, her ikisi de aynı nesneye başvuran iki nesne başvurur. Bu nedenle, nesne üzerinden `object3` yapılan herhangi bir değişiklik `object4`sonraki kullanımlarında yansıtılır. Sınıfları temel alan nesneler referans olarak anılacaktır, sınıflar başvuru türleri olarak bilinir.  
  
## <a name="class-inheritance"></a>Sınıf kalıbı  

Sınıflar, nesne yönelimli programlamanın temel bir özelliği olan *kalıtımı*tam olarak destekler. Bir sınıf oluşturduğunuzda, [mühürlü](../../language-reference/keywords/sealed.md)olarak tanımlanmayan başka bir arabirim veya sınıftan devralabilir ve diğer sınıflar sınıfınızdan devralabilir ve sınıf sanal yöntemlerini geçersiz kılabilir.

Devralma bir *türetme*kullanılarak gerçekleştirilir , yani bir sınıf, verileri ve davranışı devraldığı bir *taban sınıf* kullanılarak bildirilir. Bir taban sınıf, bir üst üste ve türemiş sınıf adını izleyen taban sınıfın adını ekleyerek şu şekilde belirtilir:  

 ```csharp
 public class Manager : Employee
 {
     // Employee fields, properties, methods and events are inherited
     // New Manager fields, properties, methods and events go here...
 }
 ```

Bir sınıf bir taban sınıf beyan ettiğinde, oluşturucular dışında taban sınıfın tüm üyelerini devralır. Daha fazla bilgi için [Bkz. Kalıtım.](inheritance.md)
  
C++'ın aksine, C#'daki bir sınıf yalnızca doğrudan bir taban sınıftan devralınabilir. Ancak, bir taban sınıf başka bir sınıftan devralabileceğinden, bir sınıf dolaylı olarak birden çok temel sınıfı devralabilir. Ayrıca, bir sınıf doğrudan birden fazla arabirim uygulayabilirsiniz. Daha fazla bilgi için [Arabirimler'e](../interfaces/index.md)bakın.  
  
Bir sınıf [soyut](../../language-reference/keywords/abstract.md)olarak ilan edilebilir. Soyut bir sınıf, imza tanımı na sahip ancak uygulama olmayan soyut yöntemler içerir. Soyut sınıflar anında kullanılamaz. Bunlar yalnızca soyut yöntemleri uygulayan türemiş sınıflar aracılığıyla kullanılabilir. Bunun aksine, [mühürlü](../../language-reference/keywords/sealed.md) bir sınıf diğer sınıfların ondan türemesine izin vermez. Daha fazla bilgi için [Bkz. Özet ve Mühürlü Sınıflar ve Sınıf Üyeleri.](abstract-and-sealed-classes-and-class-members.md)  
  
Sınıf tanımları farklı kaynak dosyaları arasında bölünebilir. Daha fazla bilgi için Kısmi [Sınıflar ve Yöntemler'e](partial-classes-and-methods.md)bakın.  
  
## <a name="example"></a>Örnek

Aşağıdaki örnek, otomatik olarak uygulanan bir [özellik,](auto-implemented-properties.md)bir yöntem ve oluşturucu adı verilen özel bir yöntem içeren ortak bir sınıf tanımlar. Daha fazla bilgi için [Özellikler,](properties.md) [Yöntemler](methods.md)ve [Kurucular](constructors.md) konularına bakın. Sınıfın örnekleri daha sonra `new` anahtar kelime ile anında.  
  
[!code-csharp[Class Example](~/samples/snippets/csharp/programming-guide/classes-and-structs/class-example.cs)]
  
## <a name="c-language-specification"></a>C# Dil Belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Nesne Odaklı Programlama](../concepts/object-oriented-programming.md)
- [Çok Biçimlilik](polymorphism.md)
- [Tanımlayıcı adları](../inside-a-program/identifier-names.md)
- [Üyeler](members.md)
- [Yöntemler](methods.md)
- [Oluşturucular](constructors.md)
- [Sonlandırıcılar](destructors.md)
- [Nesneler](objects.md)
