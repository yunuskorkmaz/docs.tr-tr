---
title: Sınıflar ve Structs - C# Programlama Kılavuzu
description: C#'da sınıfların ve yapıların (yapıların) kullanımını açıklar.
ms.date: 01/17/2016
helpviewer_keywords:
- structs [C#], about structs
- classes [C#], overview
- C# language, structs
- C# language, objects
- objects [C#]
- C# language, classes
ms.assetid: cc39dbda-8754-423e-b5b1-16a1db0734c0
ms.openlocfilehash: afd9e688bd716375bafb370fad4af082a9498411
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399856"
---
# <a name="classes-and-structs-c-programming-guide"></a>Sınıflar ve Yapılar (C# Programlama Kılavuzu)
Sınıflar ve yapılar .NET Framework'deki ortak tür sisteminin temel yapılarından ikisidir. Her biri, mantıksal bir birim olarak bir araya gelen bir veri kümesini ve davranışı kapsayan bir veri yapısıdır. Veriler ve davranışlar sınıfın veya yapının *üyeleridir* ve bu konunun ilerleyen saatlerinde listelendikleri gibi yöntemlerini, özelliklerini ve olaylarını vb. içerir.  
  
 Sınıf veya yapı bildirimi, çalışma zamanında örnek veya nesne oluşturmak için kullanılan bir plan gibidir. Bir sınıf veya yapı adlı `Person`tanımlarsanız, `Person` türün adıdır. Bir `p` tür `Person`değişkeni beyan ve `p` baş harfe yazarsanız, `Person`bir nesne veya . Aynı `Person` türden birden çok örnek oluşturulabilir ve her örnek kendi özellikleri ve alanlarında farklı değerlere sahip olabilir.  
  
 Sınıf bir başvuru türüdür. Sınıfın bir nesnesi oluşturulduğunda, nesnenin atandığı değişken yalnızca bu belleğe bir başvuru tutar. Nesne başvurusu yeni bir değişkene atandığında, yeni değişken özgün nesneye başvurur. Her ikisi de aynı verilere atıfta çünkü bir değişken üzerinden yapılan değişiklikler diğer değişkene yansıtılır.  
  
 Yapı bir değer türüdür. Bir yapı oluşturulduğunda, yapının atandığı değişken yapının gerçek verilerini tutar. Yapı yeni bir değişkene atandığında kopyalanır. Bu nedenle, yeni değişken ve özgün değişken aynı verilerin iki ayrı kopyasını içerir. Bir kopyada yapılan değişiklikler diğer kopyayı etkilemez.  
  
 Genel olarak, sınıflar daha karmaşık davranışı veya bir sınıf nesnesi oluşturulduktan sonra değiştirilmesi amaçlanan verileri modellemek için kullanılır. Structs, öncelikle yapı oluşturulduktan sonra değiştirilmesi amaçlanmayan verileri içeren küçük veri yapıları için en uygun olanlardır.  
  
 Daha fazla bilgi için [Bkz. Sınıflar,](./classes.md) [Nesneler](./objects.md)ve [Yapı türleri.](../../language-reference/builtin-types/struct.md)  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `CustomClass` `ProgrammingGuide` ad alanında üç üye vardır: bir örnek `Number`oluşturucu, adlı `Multiply`bir özellik , ve adlı bir yöntem . Sınıftayöntem `Main` `Program` bir örnek (nesne) `CustomClass`oluşturur ve nesnenin yöntemi ve özelliği nokta gösterimi kullanılarak erişilir.
  
 [!code-csharp[csProgGuideObjects#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/class1.cs#1)]  
  
## <a name="encapsulation"></a>Kapsülleme  
 *Kapsülleme* bazen nesne yönelimli programlamanın ilk ayağı veya ilkesi olarak adlandırılır. Kapsülleme ilkesine göre, bir sınıf veya yapı, üyelerinin her birinin sınıf veya yapı dışında kodlama nın ne kadar erişilebilir olduğunu belirtebilir. Sınıf veya derleme dışından kullanılması amaçlanmayan yöntemler ve değişkenler, kodlama hataları veya kötü amaçlı açıklar potansiyelini sınırlamak için gizlenebilir.  
  
 Sınıflar [ve](./classes.md) [Nesneler](./objects.md)hakkında daha fazla bilgi için bkz.  
  
### <a name="members"></a>Üyeler  
 Tüm yöntemler, alanlar, sabitler, özellikler ve olaylar bir tür içinde bildirilmelidir; bunlara türünün *üyeleri* denir. C#'da, diğer bazı dillerde olduğu gibi genel değişkenler veya yöntemler yoktur. Hatta bir programın giriş noktası, `Main` yöntem, bir sınıf veya yapı içinde bildirilmelidir. Aşağıdaki liste, bir sınıf veya yapıda bildirilebilecek tüm çeşitli üyeleri içerir.  
  
- [Alanlar](./fields.md)  
  
- [Sabitler](./constants.md)  
  
- [Özellikler](./properties.md)  
  
- [Yöntemler](./methods.md)  
  
- [Oluşturucular](./constructors.md)  
  
- [Olaylar](../events/index.md)  
  
- [Sonlandırıcılar](./destructors.md)  
  
- [Dizin Oluşturucular](../indexers/index.md)  
  
- [İşleçler](../../language-reference/operators/index.md)  
  
- [İç içe Geçmiş Türler](./nested-types.md)  
  
### <a name="accessibility"></a>Erişilebilirlik  
 Bazı yöntemler ve özellikler çağrılması veya istemci *kodu*olarak bilinen sınıf veya yapı dışında koddan erişilmesi içindir. Diğer yöntemler ve özellikler yalnızca sınıf veya yapının kendisinde kullanılabilir. Yalnızca amaçlanan istemci koduna ulaşabilmesi için kodunuzun erişilebilirliğini sınırlamak önemlidir. Genel, [korumalı,](../../language-reference/keywords/protected.md) [dahili,](../../language-reference/keywords/internal.md) [korumalı dahili,](../../language-reference/keywords/protected-internal.md) [özel](../../language-reference/keywords/private.md) [public](../../language-reference/keywords/public.md)ve [özel korumalı](../../language-reference/keywords/private-protected.md)erişim değiştiriciler kullanarak türünüzün ve üyelerinin istemci koduna ne kadar erişilebilir olduğunu belirtirsiniz. Varsayılan erişilebilirlik. `private` Daha fazla bilgi için [Erişim Değiştiriciler'e](./access-modifiers.md)bakın.  
  
### <a name="inheritance"></a>Devralma  
 Sınıflar (ancak yapı değil) kalıtım kavramını destekler. Başka bir sınıftan *(taban sınıf)* türeyen bir sınıf, oluşturucuları ve sonlandırıcıları dışında taban sınıfın tüm ortak, korumalı ve dahili üyelerini otomatik olarak içerir. Daha fazla bilgi için [kalıtım](./inheritance.md) ve [çok biçimlilik](./polymorphism.md)bilgisine bakın.  
  
 Sınıflar [soyut](../../language-reference/keywords/abstract.md)olarak ilan edilebilir, bu da yöntemlerinden birinin veya daha fazlasının uygulanması olmadığı anlamına gelir. Soyut sınıflar doğrudan anında alınamasa da, eksik uygulamayı sağlayan diğer sınıflar için temel sınıflar olarak hizmet verebilirler. Sınıflar, diğer sınıfların bunlardan devralmasını önlemek için [mühürlü](../../language-reference/keywords/sealed.md) olarak da beyan edilebilir. Daha fazla bilgi için [Bkz. Özet ve Mühürlü Sınıflar ve Sınıf Üyeleri.](./abstract-and-sealed-classes-and-class-members.md)  
  
### <a name="interfaces"></a>Arabirimler  
 Sınıflar ve structs birden çok arabirim devralabilir. Bir arabirimden devralmak, türün arabirimde tanımlanan tüm yöntemleri uyguladığı anlamına gelir. Daha fazla bilgi için [Arabirimler'e](../interfaces/index.md)bakın.  
  
### <a name="generic-types"></a>Genel Türler  
 Sınıflar ve structs bir veya daha fazla tür parametreleri ile tanımlanabilir. İstemci kodu, tür eki bir örnek oluştururken türü sağlar. Örneğin <xref:System.Collections.Generic> ad <xref:System.Collections.Generic.List%601> alanındaki sınıf bir tür parametresi ile tanımlanır. İstemci kodu, bir `List<string>` `List<int>` örneğini oluşturur veya listenin tutacağı türü belirtir. Daha fazla bilgi için [Genel Bilgiler'e](../generics/index.md)bakın.  
  
### <a name="static-types"></a>Statik Türleri  
 Sınıflar (ancak structs değil) [statik](../../language-reference/keywords/static.md)olarak ilan edilebilir. Statik bir sınıf yalnızca statik üyeler içerebilir ve yeni anahtar kelimeyle anında kullanılamaz. Program yüklendiğinde sınıfın bir kopyası belleğe yüklenir ve üyelerine sınıf adı üzerinden erişilir. Hem sınıflar hem de structs statik üye içerebilir. Daha fazla bilgi için Statik [Sınıflar ve Statik Sınıf Üyeleri'ne](./static-classes-and-static-class-members.md)bakın.  
  
### <a name="nested-types"></a>İç içe Geçmiş Türler  
 Bir sınıf veya yapı başka bir sınıf veya yapı içinde iç içe olabilir. Daha fazla bilgi için İç [Içe Türler'e](./nested-types.md)bakın.  
  
### <a name="partial-types"></a>Kısmi Tipler  
 Bir kod dosyasında bir sınıfın, yapının veya yöntemin bir bölümünü ve ayrı bir kod dosyasında başka bir bölümü tanımlayabilirsiniz. Daha fazla bilgi için Kısmi [Sınıflar ve Yöntemler'e](./partial-classes-and-methods.md)bakın.  
  
### <a name="object-initializers"></a>Nesne Baş harfleri  
 Sınıf veya yapı nesneleri ve nesnelerin koleksiyonlarını, oluşturucularını açıkça çağırmadan anında ve başlangıç olarak adlandırabilirsiniz. Daha fazla bilgi için [Object ve Collection Initializers'a](./object-and-collection-initializers.md)bakın.  
  
### <a name="anonymous-types"></a>Anonim Türler  
 Adlandırılmış bir sınıf oluşturmanın uygun olmadığı veya gerekli olmadığı durumlarda, örneğin bir listeyi kalıcı olarak sürdürmek veya başka bir yönteme geçmek zorunda olmadığınız veri yapıları ile dolduruyorsanız, anonim türleri kullanırsınız. Daha fazla bilgi için [Bkz. Anonim Türler.](./anonymous-types.md)  
  
### <a name="extension-methods"></a>Genişletme Yöntemleri  
 Türemiş bir sınıf oluşturmadan, yöntemleri özgün türe aitmiş gibi çağrılabilen ayrı bir tür oluşturarak bir sınıfı "genişletebilirsiniz". Daha fazla bilgi için [Uzantı Yöntemleri'ne](./extension-methods.md)bakın.  
  
### <a name="implicitly-typed-local-variables"></a>Örtülü Olarak Yazılan Yerel Değişkenler  
 Bir sınıf veya yapı yöntemi içinde, derleme zamanında doğru türü belirlemek için derleyici talimat örtük yazarak kullanabilirsiniz. Daha fazla bilgi için [bkz.](./implicitly-typed-local-variables.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
