---
title: Sınıflar ve yapılar - C# Programlama Kılavuzu
ms.custom: seodec18
description: Sınıflar ve yapılar (yapı) C# kullanımını açıklar.
ms.date: 01/17/2016
helpviewer_keywords:
- structs [C#], about structs
- classes [C#], overview
- C# language, structs
- C# language, objects
- objects [C#]
- C# language, classes
ms.assetid: cc39dbda-8754-423e-b5b1-16a1db0734c0
ms.openlocfilehash: 9380a06b733546cdf5af959868fcdfdcc7189ded
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242561"
---
# <a name="classes-and-structs-c-programming-guide"></a>Sınıflar ve Yapılar (C# Programlama Kılavuzu)
Sınıflar ve yapı birimleri .NET Framework'teki ortak tür sisteminin temel yapılarından ikisidir. Her bir veri kümesini ve birlikte bir mantıksal birim olarak ait davranışları kapsülleyen aslında bir veri yapısıdır. Veri ve davranışlar *üyeleri* sınıfın veya yapının ve yöntemleri, özellikleri ve olayları ve benzeri, bu konunun ilerleyen bölümlerinde listelenen içerirler.  
  
 Bir sınıf veya yapı bildirimi, çalışma zamanında örnekler ve nesneler oluşturmak için kullanılan bir şema gibidir. Bir sınıf veya yapı adı tanımlarsanız `Person`, `Person` türünün adı. Bildirme ve bir değişkeni başlatarak `p` türü `Person`, `p` bir nesne veya örneği olduğu söylenir `Person`. Birden çok örneği aynı `Person` türü oluşturulabilir ve her örneği, özellikleri ve alanları farklı değerlere sahip olabilir.  
  
 Bir sınıf bir başvuru türüdür. Sınıfın bir nesnesi oluşturulduğunda, nesnenin atandığı değişken yalnızca belleğe bir başvuru tutar. Nesne başvurusu yeni bir değişkene atandığında yeni değişken özgün nesneye başvurur. Her ikisi de aynı veriye başvurmaktadır çünkü bir değişken üzerinden yapılan değişiklikler diğer değişkene de yansıtılır.  
  
 Bir yapı bir değer türüdür. Bir yapı oluşturulduğunda yapının atanmış olduğu değişken yapının gerçek verilerini tutar. Struct için yeni bir değişken atandığında kopyalanır. Bu nedenle yeni değişken ve özgün değişken aynı verilerin iki ayrı kopyasını içerir. Bir kopyaya yapılan değişiklikler diğer kopyayı etkilemez.  
  
 Genel olarak sınıflar daha karmaşık bir davranış veya bir sınıf nesnesi oluşturulduktan sonra değiştirilmesine yönelik veri modelini oluşturmak için kullanılır. Yapılar, öncelikle yapı oluşturulduktan sonra değiştirilmesine yönelik değildir veriler içeren küçük veri yapıları için en uygun seçenektir.  
  
 Daha fazla bilgi için [sınıfları](../../../csharp/programming-guide/classes-and-structs/classes.md), [nesneleri](../../../csharp/programming-guide/classes-and-structs/objects.md), ve [yapılar](../../../csharp/programming-guide/classes-and-structs/structs.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `CustomClass` içinde `ProgrammingGuide` ad alanına sahip üç üye: örnek oluşturucusu, adlı bir özellik `Number`, adlı bir yöntem `Multiply`. `Main` Yönteminde `Program` sınıfı bir örneğini oluşturur (nesne) `CustomClass`, ve nesnenin yöntem ve özellik nokta gösterimi kullanılarak erişilir.
  
 [!code-csharp[csProgGuideObjects#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/class1.cs#1)]  
  
## <a name="encapsulation"></a>Kapsülleme  
 *Kapsülleme* bazen birinci unsuru veya prensibi nesne yönelimli programlama adlandırılır. Kapsülleme ilkesine göre bir sınıf veya yapı nasıl her üyenin sınıf veya yapı dışında koda erişilebilir belirtebilirsiniz. Yöntemleri ve sınıfın veya derlemenin dışından gelen sonuna kullanılmak üzere tasarlanmamıştır değişkenler olası kodlama hatalarını veya kötü niyetli davranışları için sınırlandırmak için gizlenebilir.  
  
 Sınıfları hakkında daha fazla bilgi için bkz. [sınıfları](../../../csharp/programming-guide/classes-and-structs/classes.md) ve [nesneleri](../../../csharp/programming-guide/classes-and-structs/objects.md).  
  
### <a name="members"></a>Üyeler  
 Tüm yöntemler, alanlar, sabitler, özellikler ve olaylar için bir tür içinde bildirilmesi gerekir; Bunlar adlandırılır *üyeleri* türü. C# ' ta var. genel değişkenler veya yöntemler gibi diğer dillerde Hatta bir programın giriş noktası `Main` yöntemi, bir sınıf veya yapı içinde bildirilmelidir. Aşağıdaki listede, bir sınıf veya yapıda bildirilebilecek üyelerin tüm çeşitli türleri içerir.  
  
-   [Alanlar](../../../csharp/programming-guide/classes-and-structs/fields.md)  
  
-   [Sabitler](../../../csharp/programming-guide/classes-and-structs/constants.md)  
  
-   [Özellikler](../../../csharp/programming-guide/classes-and-structs/properties.md)  
  
-   [Yöntemler](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [Oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [Olaylar](../../../csharp/programming-guide/events/index.md)  
  
-   [Sonlandırıcılar](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
  
-   [Dizin Oluşturucular](../../../csharp/programming-guide/indexers/index.md)  
  
-   [İşleçler](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
  
-   [İç içe Geçmiş Türler](../../../csharp/programming-guide/classes-and-structs/nested-types.md)  
  
### <a name="accessibility"></a>Erişilebilirlik  
 Bazı yöntemler ve Özellikler çağrılan veya erişilen sınıf veya yapının bilinen dışındaki kod yöneliktir *istemci kodu*. Diğer yöntemler ve özellikler yalnızca sınıf veya yapı biriminde kullanmak için olabilir. Kodunuzun erişilebilirliğini, yalnızca amaçlanan istemci kodunun erişebileceği şekilde sınırlamak önemlidir. Belirttiğiniz nasıl Türlerinizin ve üyelerinin istemci kodu erişim değiştiricilerini kullanarak erişilebilir [genel](../../../csharp/language-reference/keywords/public.md), [korumalı](../../../csharp/language-reference/keywords/protected.md), [iç](../../../csharp/language-reference/keywords/internal.md), [ İç korumalı](../../../csharp/language-reference/keywords/protected-internal.md), [özel](../../../csharp/language-reference/keywords/private.md) ve [korunan özel](../../../csharp/language-reference/keywords/private-protected.md). Varsayılan erişilebilirlik, `private`. Daha fazla bilgi için [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
### <a name="inheritance"></a>Devralma  
 Sınıflar (ancak değil yapı birimleri değil) devralma kavramını destekler. Başka bir sınıftan türetilen bir sınıf ( *temel sınıfı*) dışında oluşturucular ve sonlandırıcılar taban sınıfın tüm genel, korumalı ve iç üyelerini otomatik olarak kapsar. Daha fazla bilgi için [devralma](../../../csharp/programming-guide/classes-and-structs/inheritance.md) ve [çok biçimlilik](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).  
  
 Sınıflar olarak belirtilebilir [soyut](../../../csharp/language-reference/keywords/abstract.md), bir veya daha fazla kendi yöntemlerini uygulaması bulunmuyor anlamına gelir. Soyut sınıflar doğrudan oluşturulamaz ancak eksik uygulama sağlayan diğer sınıflar için temel sınıf olarak hizmet verebilir. Sınıfları ayrıca olarak bildirilebilir [korumalı](../../../csharp/language-reference/keywords/sealed.md) diğer sınıfların kendilerinden devralmasını önlemek için. Daha fazla bilgi için [soyut ve korumalı sınıflar ve sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
### <a name="interfaces"></a>Arabirimler  
 Sınıfları ve yapıları birden çok arabirim devralabilir. Türün uyguladığı arabirim içinde tanımlanmış tüm yöntemleri arabirimi anlamına gelir devralmak için. Daha fazla bilgi için [arabirimleri](../../../csharp/programming-guide/interfaces/index.md).  
  
### <a name="generic-types"></a>Genel türler  
 Sınıflar ve yapılar, bir veya daha fazla tür parametreleri ile tanımlanabilir. İstemci kodu, türün bir örneğini oluşturduğunda, türü sağlar. Örneğin <xref:System.Collections.Generic.List%601> sınıfını <xref:System.Collections.Generic> ad alanı, bir tür parametreyle tanımlanır. İstemci kodu bir örneğini oluşturur bir `List<string>` veya `List<int>` listenin tutulacağı türü belirlemek için. Daha fazla bilgi için [genel türler](../../../csharp/programming-guide/generics/index.md).  
  
### <a name="static-types"></a>Statik türler  
 Olarak sınıflar (ancak değil yapı birimleri değil) bildirilebilir [statik](../../../csharp/language-reference/keywords/static.md). Statik sınıf yalnızca statik üyeleri içerebilir ve yeni anahtar sözcükle oluşturulamaz. Program yüklendiğinde sınıfın bir kopyası belleğe yüklendiği ve sınıf adı aracılığıyla üyelerine erişilir. Sınıflar ve yapı birimleri statik üyeler içerebilir. Daha fazla bilgi için [statik sınıflar ve statik sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
### <a name="nested-types"></a>İç içe Geçmiş Türler  
 Bir sınıf veya yapı başka bir sınıf veya yapıyla iç içe olabilir. Daha fazla bilgi için [iç içe türler](../../../csharp/programming-guide/classes-and-structs/nested-types.md).  
  
### <a name="partial-types"></a>Kısmi türler  
 Bir sınıf, yapı veya yöntemi bir kod dosyasında bir parçası ve başka bir parçası ayrı bir kod dosyasında tanımlayabilirsiniz. Daha fazla bilgi için [kısmi sınıflar ve yöntemler](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).  
  
### <a name="object-initializers"></a>Nesne başlatıcıları  
 Örneği oluşturmak ve açıkça çağırmadan sınıf veya yapı nesneleri ve nesne koleksiyonları başlatır. Daha fazla bilgi için [nesne ve koleksiyon başlatıcıları](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
### <a name="anonymous-types"></a>Anonim Türler  
 Bu kullanışlı veya adlandırılmış bir sınıf oluşturmak gerekli olduğu durumlarda, örneğin ne zaman, bir liste veri yapılarıyla kalıcı hale getirmek ya da başka yönteme geçirin gerekmez, anonim türleri kullanırsınız. Daha fazla bilgi için [anonim türler](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
### <a name="extension-methods"></a>Uzantı Metotları  
 "Bir sınıfı yöntemleri orijinal türe aitse gibi çağrılabilir ayrı bir tür oluşturarak türetilmiş sınıf oluşturmadan genişletebileceğiniz". Daha fazla bilgi için [genişletme yöntemleri](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).  
  
### <a name="implicitly-typed-local-variables"></a>Örtülü Olarak Yazılan Yerel Değişkenler  
 Bir sınıf veya yapı birimi yöntemi içinde örtülü yazma kullanarak derleyicinin derleme zamanında doğru türünü belirlemek için kullanabilirsiniz. Daha fazla bilgi için [örtük olarak yazılan yerel değişkenler](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
