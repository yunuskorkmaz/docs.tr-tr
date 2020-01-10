---
title: Sınıflar ve yapılar- C# Programlama Kılavuzu
description: İçinde C#sınıfların ve yapıların (yapılar) kullanımını açıklar.
ms.date: 01/17/2016
helpviewer_keywords:
- structs [C#], about structs
- classes [C#], overview
- C# language, structs
- C# language, objects
- objects [C#]
- C# language, classes
ms.assetid: cc39dbda-8754-423e-b5b1-16a1db0734c0
ms.openlocfilehash: 301ba292010470208e92a225c1014bcb50497106
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714817"
---
# <a name="classes-and-structs-c-programming-guide"></a>Sınıflar ve Yapılar (C# Programlama Kılavuzu)
Sınıflar ve yapılar, .NET Framework ortak tür sisteminin temel yapılarıdır. Her biri, mantıksal birim olarak birbirine ait bir veri kümesini ve davranışları kapsülleyen bir veri yapısıdır. Veri ve davranışlar, sınıfın veya yapının *üyeleridir* ve bu konuda daha sonra listelendiği gibi yöntemleri, özellikleri ve olayları gibi, vb. içerir.  
  
 Sınıf veya yapı bildirimi, çalışma zamanında örnek veya nesne oluşturmak için kullanılan bir şema gibidir. `Person`adlı bir sınıf veya yapı tanımlarsanız `Person` türün adıdır. `Person`türünde bir değişken `p` bildirir ve başladıysanız `p` bir nesne veya `Person`örneği olarak ifade edilir. Aynı `Person` türünün birden çok örneği oluşturulabilir ve her bir örnek, özelliklerinde ve alanlarında farklı değerlere sahip olabilir.  
  
 Sınıf bir başvuru türüdür. Sınıfın bir nesnesi oluşturulduğunda, nesnenin atandığı değişken yalnızca o belleğe yönelik bir başvuru barındırır. Nesne başvurusu yeni bir değişkene atandığında, yeni değişken özgün nesneye başvurur. Her ikisi de aynı verilere başvurduğundan, bir değişken aracılığıyla yapılan değişiklikler diğer değişkene yansıtılır.  
  
 Struct bir değer türüdür. Bir struct oluşturulduğunda, yapının atandığı değişken yapının gerçek verilerini barındırır. Yapı yeni bir değişkene atandığında, kopyalanır. Bu nedenle, yeni değişken ve özgün değişken aynı verilerin iki ayrı kopyasını içerir. Bir kopyada yapılan değişiklikler diğer kopyayı etkilemez.  
  
 Genel olarak, sınıflar daha karmaşık davranışı modellemek veya bir sınıf nesnesi oluşturulduktan sonra değiştirilmesi amaçlanan veriler için kullanılır. Yapılar, öncelikle yapı oluşturulduktan sonra değiştirilmesi amaçlanmayan verileri içeren küçük veri yapıları için idealdir.  
  
 Daha fazla bilgi için bkz. [sınıflar](./classes.md), [nesneler](./objects.md)ve [yapılar](./structs.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `ProgrammingGuide` ad alanındaki `CustomClass` üç üyeye sahiptir: bir örnek Oluşturucu, `Number`adlı bir özellik ve `Multiply`adlı bir yöntem. `Program` sınıfındaki `Main` yöntemi, `CustomClass`bir örnek (nesne) oluşturur ve nesnenin yöntemi ile özelliğine nokta gösterimi kullanılarak erişilir.
  
 [!code-csharp[csProgGuideObjects#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/class1.cs#1)]  
  
## <a name="encapsulation"></a>Kapsül  
 *Kapsülleme* bazen nesne odaklı programlamanın ilk ve prensibi olarak adlandırılır. Kapsülleme ilkelerine göre, bir sınıf veya yapı, üyelerinin her birinin ne şekilde erişilebilir olduğunu belirtebilir sınıfın veya yapının dışında kod alma. Sınıf veya derleme dışından kullanılması amaçlanmayan Yöntemler ve değişkenler, kodlama hataları veya kötü amaçlı yazılımlar için potansiyelini sınırlamak üzere gizlenebilir.  
  
 Sınıflar hakkında daha fazla bilgi için bkz. [sınıflar](./classes.md) ve [nesneler](./objects.md).  
  
### <a name="members"></a>Üyeler  
 Tüm Yöntemler, alanlar, sabitler, Özellikler ve olaylar bir tür içinde bildirilmelidir; Bunlara tür *üyeleri* denir. İçinde C#, bazı dillerde olduğu gibi genel değişkenler veya yöntemler yoktur. Bir programın giriş noktası bile, `Main` yöntemi bir sınıf veya yapı içinde bildirilmelidir. Aşağıdaki liste, bir sınıfta veya yapıda bildirilebilecek çeşitli üye türlerini içerir.  
  
- [Alanlar](./fields.md)  
  
- [Sabitler](./constants.md)  
  
- [Veri Erişimi](./properties.md)  
  
- [Yöntemler](./methods.md)  
  
- [Oluşturucular](./constructors.md)  
  
- [Olaylar](../events/index.md)  
  
- [Sonlandırıcılar](./destructors.md)  
  
- [Dizin Oluşturucular](../indexers/index.md)  
  
- [İşleçler](../../language-reference/operators/index.md)  
  
- [İç içe Geçmiş Türler](./nested-types.md)  
  
### <a name="accessibility"></a>Erişilebilirlik  
 Bazı yöntemler ve özellikler, sınıf veya yapı birimi dışında, *istemci kodu*olarak bilinen koddan çağrılmalıdır veya erişilmek üzere tasarlanmıştır. Diğer yöntemler ve özellikler yalnızca sınıfta veya yapıda kullanım için olabilir. Yalnızca amaçlanan istemci kodunun ulaşabilmesi için kodunuzun erişilebilirliğini sınırlandırmamak önemlidir. Türlerinizin ve üyelerinin istemci koduna ne kadar erişilebilir olduğunu, [genel](../../language-reference/keywords/public.md), [korunan](../../language-reference/keywords/protected.md), [dahili](../../language-reference/keywords/internal.md), [korunan iç](../../language-reference/keywords/protected-internal.md), [özel](../../language-reference/keywords/private.md) ve [özel korumalı](../../language-reference/keywords/private-protected.md)erişim değiştiricilerini kullanarak belirtirsiniz. Varsayılan erişilebilirlik `private`. Daha fazla bilgi için bkz. [erişim değiştiricileri](./access-modifiers.md).  
  
### <a name="inheritance"></a>Devralma  
 Sınıflar (ancak yapılar değil) devralma kavramını destekler. Başka bir sınıftan ( *temel sınıf*) türetilen bir sınıf, oluşturucular ve sonlandırıcılar hariç temel sınıfın tüm genel, korunan ve dahili üyelerini otomatik olarak içerir. Daha fazla bilgi için bkz. [Devralma](./inheritance.md) ve çok [biçimlilik](./polymorphism.md).  
  
 Sınıflar [Özet](../../language-reference/keywords/abstract.md)olarak, bir veya daha fazla yönteminin bir uygulama olmadığı anlamına gelir. Soyut sınıflar doğrudan örneklenemez, ancak eksik uygulamayı sağlayan diğer sınıflar için temel sınıf olarak görev yapabilir. Sınıflar, diğer sınıfların bunlardan devralmasını engellemek için [Sealed](../../language-reference/keywords/sealed.md) olarak da bildirilemez. Daha fazla bilgi için bkz. [soyut ve korumalı sınıflar ve sınıf üyeleri](./abstract-and-sealed-classes-and-class-members.md).  
  
### <a name="interfaces"></a>Arabirimler  
 Sınıflar ve yapılar birden çok arabirimi kalýtýmla alabilir. Bir arabirimden devralması için, türün arabirimde tanımlanmış tüm yöntemleri uyguladığı anlamına gelir. Daha fazla bilgi için bkz. [arabirimler](../interfaces/index.md).  
  
### <a name="generic-types"></a>Genel Türler  
 Sınıflar ve yapılar, bir veya daha fazla tür parametresiyle tanımlanabilir. İstemci kodu, türün bir örneğini oluşturduğunda türü sağlar. Örneğin, <xref:System.Collections.Generic> ad alanındaki <xref:System.Collections.Generic.List%601> sınıfı bir tür parametresiyle tanımlanmıştır. İstemci kodu, listenin tutacağız türü belirtmek için bir `List<string>` veya `List<int>` örneği oluşturur. Daha fazla bilgi için bkz. [Genel türler](../generics/index.md).  
  
### <a name="static-types"></a>Statik türler  
 Sınıflar (ancak yapılar için değil) [statik](../../language-reference/keywords/static.md)olarak bildirilemez. Statik bir sınıf yalnızca statik üyeler içerebilir ve yeni anahtar sözcüğüyle başlatılamaz. Program yüklendiğinde sınıfın bir kopyası belleğe yüklenir ve onun üyelerine sınıf adından erişilir. Sınıfların ve yapıların her ikisi de statik üye içerebilir. Daha fazla bilgi için bkz. [statik sınıflar ve statik sınıf üyeleri](./static-classes-and-static-class-members.md).  
  
### <a name="nested-types"></a>İç içe Geçmiş Türler  
 Bir sınıf veya yapı, başka bir sınıf veya yapı içinde iç içe olabilir. Daha fazla bilgi için bkz. [Iç Içe türler](./nested-types.md).  
  
### <a name="partial-types"></a>Kısmi türler  
 Bir sınıf, yapı veya yöntemin bir parçasını bir kod dosyasında ve farklı bir kod dosyasındaki başka bir bölüme tanımlayabilirsiniz. Daha fazla bilgi için bkz. [kısmi sınıflar ve Yöntemler](./partial-classes-and-methods.md).  
  
### <a name="object-initializers"></a>Nesne başlatıcıları  
 Yapıcısını açıkça çağırmadan sınıf veya yapı nesneleri ve nesne koleksiyonları oluşturabilir ve başlatabilir. Daha fazla bilgi için bkz. [nesne ve koleksiyon başlatıcıları](./object-and-collection-initializers.md).  
  
### <a name="anonymous-types"></a>Anonim Türler  
 Adlandırılmış bir sınıf oluşturmak için uygun veya gerekli olmadığı durumlarda (örneğin, bir listeyi kalıcı hale getirmek veya başka bir yönteme geçirmek zorunda değilsiniz veri yapıları içeren bir liste doldururken), anonim türler kullanırsınız. Daha fazla bilgi için bkz. [anonim türler](./anonymous-types.md).  
  
### <a name="extension-methods"></a>Genişletme Yöntemleri  
 Metotları özgün türe ait gibi çağrılabilecek ayrı bir tür oluşturarak, türetilmiş sınıf oluşturmadan bir sınıfı "genişletebilirsiniz". Daha fazla bilgi için bkz. [Uzantı yöntemleri](./extension-methods.md).  
  
### <a name="implicitly-typed-local-variables"></a>Örtülü Olarak Yazılan Yerel Değişkenler  
 Bir sınıf veya yapı yönteminde, derleyicinin derleme zamanında doğru türü belirlemesini söylemek için örtük yazma kullanabilirsiniz. Daha fazla bilgi için bkz. [örtülü olarak yazılan yerel değişkenler](./implicitly-typed-local-variables.md).  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
