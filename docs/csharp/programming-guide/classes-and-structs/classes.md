---
title: Sınıflar-C# Programlama Kılavuzu
description: Sınıf türleri ve bunların nasıl oluşturulacağı hakkında bilgi edinin
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
[Sınıf](../../language-reference/keywords/class.md) olarak tanımlanan bir tür, *başvuru türüdür*. Çalışma zamanında, bir başvuru türünde bir değişken bildirdiğinizde, [New](../../language-reference/operators/new-operator.md) işlecini kullanarak sınıfın bir örneğini açıkça oluşturana veya onu aşağıdaki örnekte gösterildiği gibi başka bir yerde oluşturulmuş olan uyumlu bir türde bir nesne atayarak, değişken [null](../../language-reference/keywords/null.md) değerini içerir:

```csharp
//Declaring an object of type MyClass.
MyClass mc = new MyClass();

//Declaring another object of the same type, assigning it the value of the first object.
MyClass mc2 = mc;
```

Nesne oluşturulduğunda, söz konusu nesne için yönetilen yığında yeterli bellek ayrılır ve değişken yalnızca belirtilen nesnenin konumuna bir başvuru içerir. Yönetilen yığında bulunan türler, her ikisi de ayrıldıklarında ve *çöp toplama*olarak bilinen clr 'nin otomatik bellek yönetimi işlevselliği tarafından geri kazanıyorsa ek yük gerektirir. Ancak çöp toplama da yüksek oranda iyileştirilmiştir ve çoğu senaryoda bir performans sorunu oluşturmaz. Çöp toplama hakkında daha fazla bilgi için bkz. [Otomatik bellek yönetimi ve çöp toplama](../../../standard/garbage-collection/fundamentals.md).  
  
## <a name="declaring-classes"></a>Sınıfları Bildirme

 Sınıflar, aşağıdaki örnekte gösterildiği gibi, [Class](../../language-reference/keywords/class.md) anahtar sözcüğü ve ardından benzersiz bir tanımlayıcı kullanılarak bildirilenler:

 ```csharp
//[access modifier] - [class] - [identifier]
 public class Customer
 {
    // Fields, properties, methods and events go here...
 }
```

 `class`Anahtar sözcüğü öncesinde erişim düzeyidir. Bu durumda [genel](../../language-reference/keywords/public.md) kullanıldığından, herkes bu sınıfın örneklerini oluşturabilir. Sınıfın adı `class` anahtar sözcüğünü izler. Sınıfın adı geçerli bir C# [tanımlayıcı adı](../inside-a-program/identifier-names.md)olmalıdır. Tanımın geri kalanı, davranışın ve verilerin tanımlandığı sınıf gövdesidir. Bir sınıftaki alanlar, özellikler, Yöntemler ve olaylar topluca *sınıf üyeleri*olarak adlandırılır.  
  
## <a name="creating-objects"></a>Nesneler oluşturma

Bazen birbirinin yerine kullanıldıkları halde bir sınıf ve bir nesne farklı şeylerdir. Bir sınıf nesne türünü tanımlar, ancak nesnenin kendisi değildir. Bir nesne, bir sınıfı temel alan somut bir varlıktır ve bazen bir sınıfın örneği olarak adlandırılır.  
  
 Nesneler [Yeni](../../language-reference/operators/new-operator.md) anahtar sözcüğü kullanılarak, ardından nesnenin temel aldığı sınıfın adı tarafından oluşturulabilir ve şöyle olur:  

 ```csharp
 Customer object1 = new Customer();
 ```

 Bir sınıfın bir örneği oluşturulduğunda, nesnesine bir başvuru, programcıya geri geçirilir. Önceki örnekte, `object1` temel alan bir nesnesine başvurudur `Customer` . Bu başvuru yeni nesneye başvurur ancak nesne verilerinin kendisini içermez. Aslında, herhangi bir nesne oluşturmadan bir nesne başvurusu oluşturabilirsiniz:  

```csharp
 Customer object2;
```

 Bir nesneye başvurmayan bu gibi nesne başvuruları oluşturmanızı önermeyiz, çünkü bu başvuru, bu tür bir başvuruya erişim denemesi çalışma zamanında başarısız olur. Ancak, bu tür bir başvuru, yeni bir nesne oluşturarak ya da bunun gibi var olan bir nesneye atanarak bir nesneye başvurmak için kullanılabilir:  

 ```csharp
 Customer object3 = new Customer();
 Customer object4 = object3;
```
  
 Bu kod, her ikisi de aynı nesneye başvuran iki nesne başvurusu oluşturur. Bu nedenle, nesne üzerinde yapılan tüm değişiklikler `object3` sonraki kullanımlarda yansıtılır `object4` . Sınıfları temel alan nesneler başvuruya göre başvurulduğu için sınıflar başvuru türleri olarak bilinir.  
  
## <a name="class-inheritance"></a>Sınıf devralma  

Sınıflar, nesne odaklı programlamanın temel bir özelliği olan *devralmayı*tamamen destekler. Bir sınıf oluşturduğunuzda, [korumalı](../../language-reference/keywords/sealed.md)olarak tanımlanmayan diğer bir arabirim veya sınıftan kalıtımla alabilir ve diğer sınıflar sınıfınızdan devralınabilir ve sınıf sanal yöntemlerini geçersiz kılabilir.

Devralma bir *türetme*kullanılarak gerçekleştirilir. Bu, bir sınıfın veri ve davranış devraldığı *temel sınıf* kullanılarak bildirildiği anlamına gelir. Bir temel sınıf, bir iki nokta üst üste eklenerek ve türetilmiş sınıf adından sonra temel sınıfın adı aşağıdaki gibi olarak belirtilir:  

 ```csharp
 public class Manager : Employee
 {
     // Employee fields, properties, methods and events are inherited
     // New Manager fields, properties, methods and events go here...
 }
 ```

Bir sınıf bir temel sınıf bildiriyorsa, oluşturucular hariç, taban sınıfın tüm üyelerini devralır. Daha fazla bilgi için bkz. [Devralma](inheritance.md).
  
C++ ' dan farklı olarak, C# ' deki bir sınıf yalnızca bir temel sınıftan doğrudan devralınabilir. Ancak, bir temel sınıfın kendisi başka bir sınıftan devraldığı için, bir sınıf dolaylı olarak birden fazla temel sınıfı devralınabilir. Ayrıca, bir sınıf doğrudan birden fazla arabirim uygulayabilir. Daha fazla bilgi için bkz. [arabirimler](../interfaces/index.md).  
  
Bir sınıf, [soyut](../../language-reference/keywords/abstract.md)olarak bildirilemez. Soyut bir sınıf imza tanımına sahip ancak uygulamaya sahip olmayan soyut yöntemler içerir. Soyut sınıfların örneği oluşturulamıyor. Yalnızca soyut yöntemleri uygulayan türetilmiş sınıflar aracılığıyla kullanılabilir. Buna karşılık, [korumalı](../../language-reference/keywords/sealed.md) bir sınıf diğer sınıfların bundan türemesine izin vermez. Daha fazla bilgi için bkz. [soyut ve korumalı sınıflar ve sınıf üyeleri](abstract-and-sealed-classes-and-class-members.md).  
  
Sınıf tanımları, farklı kaynak dosyalar arasında bölünebilir. Daha fazla bilgi için bkz. [kısmi sınıflar ve Yöntemler](partial-classes-and-methods.md).  
  
## <a name="example"></a>Örnek

Aşağıdaki örnek, bir [Otomatik uygulanan özellik](auto-implemented-properties.md), bir yöntem ve Oluşturucu olarak adlandırılan özel bir yöntem içeren bir ortak sınıf tanımlar. Daha fazla bilgi için bkz. [Özellikler](properties.md), [Yöntemler](methods.md)ve [oluşturucular](constructors.md) konuları. Daha sonra sınıfının örnekleri `new` anahtar sözcüğüyle oluşturulur.  
  
[!code-csharp[Class Example](~/samples/snippets/csharp/programming-guide/classes-and-structs/class-example.cs)]
  
## <a name="c-language-specification"></a>C# Dil Belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Nesne Odaklı Programlama](../concepts/object-oriented-programming.md)
- [Çok biçimlilik](polymorphism.md)
- [Tanımlayıcı adları](../inside-a-program/identifier-names.md)
- [Üyeler](members.md)
- [Yöntemler](methods.md)
- [Oluşturucular](constructors.md)
- [Sonlandırıcılar](destructors.md)
- [Nesneler](objects.md)
