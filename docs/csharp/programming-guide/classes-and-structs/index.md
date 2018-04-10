---
title: Sınıflar ve Yapılar (C# Programlama Kılavuzu)
description: Sınıflar ve yapılar (yapılar) C# kullanımını açıklar.
keywords: sınıflar (C#), yapılar (C#), yapıları (yapı) (C#) başvuru türleri (C#) değer türleri (C#)
ms.date: 01/17/2016
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- structs [C#], about structs
- classes [C#], overview
- C# language, structs
- C# language, objects
- objects [C#]
- C# language, classes
ms.assetid: cc39dbda-8754-423e-b5b1-16a1db0734c0
caps.latest.revision: 48
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8c4cbbdd0384c0c0e97d6a7c655e798d0562d9a8
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2017
---
# <a name="classes-and-structs-c-programming-guide"></a>Sınıflar ve Yapılar (C# Programlama Kılavuzu)
Sınıflar ve yapılar .NET Framework'teki ortak tür sistemi temel yapıları ikisidir. Her bir veri kümesini ve birlikte bir mantıksal birim olarak ait davranışları yalıtan aslında bir veri yapısıdır. Veri ve davranışları *üyeleri* sınıf veya yapı, ve yöntemleri, özellikleri ve olayları ve benzeri, bu konunun ilerleyen bölümlerinde listelendiği gibi içerirler.  
  
 Bir sınıf veya yapı çalışma zamanında örnekleri veya nesneler oluşturmak için kullanılan bir şeması gibi bildirimidir. Sınıfta veya yapı adlı tanımlarsanız `Person`, `Person` türünün adı. Bildirme ve bir değişkeni başlatmak `p` türü `Person`, `p` bir nesneye veya örneği olarak kabul edilir `Person`. Birden çok örneğini aynı `Person` türü oluşturulabilir ve her bir örneği, özellikleri ve alanları farklı değerlere sahip olabilir.  
  
 Bir sınıf bir başvuru türüdür. Sınıfın bir nesnesi oluşturulduğunda, nesne atandığı değişkeni yalnızca o bellek başvuru tutar. Nesne başvurusu için yeni bir değişken atandığında, yeni değişken özgün bir nesneye başvuruyor. Her ikisi de aynı verilere başvurmak için bir değişken üzerinden yapılan değişiklikler diğer bir değişkende yansıtılır.  
  
 Yapı değer türüdür. Yapı oluşturulurken yapı atandığı değişkeni yapının gerçek veri tutar. Yapı için yeni bir değişken atandığında, kopyalanır. Bu nedenle yeni değişken ve özgün değişkeni iki ayrı bir kopyasını aynı verileri içerir. Bir kopya için yapılan değişiklikler diğer kopya etkilemez.  
  
 Genel olarak, sınıflar, daha karmaşık davranışı ya da bir sınıf nesnesi oluşturulduktan sonra değiştirilecek hedeflenen veri modeli için kullanılır. Yapılar öncelikle yapısı oluşturulduktan sonra değiştirilecek amaçlanmamıştır verileri içeren küçük veri yapıları için uygundur.  
  
 Daha fazla bilgi için bkz: [sınıfları](../../../csharp/programming-guide/classes-and-structs/classes.md), [nesneleri](../../../csharp/programming-guide/classes-and-structs/objects.md), ve [yapılar](../../../csharp/programming-guide/classes-and-structs/structs.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `CustomClass` içinde `ProgrammingGuide` ad alanına sahip üç üye: örnek oluşturucu, adında bir özellik `Number`ve adlı bir yöntem `Multiply`. `Main` Yönteminde `Program` sınıfının bir örneğini oluşturur (nesne) `CustomClass`, ve nesnenin yöntem ve özellik noktalı gösterim kullanılarak erişilir.
  
 [!code-csharp[csProgGuideObjects#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/class1.cs#1)]  
  
## <a name="encapsulation"></a>Kapsülleme  
 *Kapsülleme* bazen ilk sütun veya nesne odaklı programlama ilkesini olarak adlandırılır. Kapsülleme ilkesine göre sınıfta veya yapı nasıl erişilebilir her üyeleri sınıfta veya yapı dışında kodu belirtebilirsiniz. Yöntemleri ve sınıf veya derleme dışında gelen sonuna kullanılmak üzere tasarlanmamıştır değişkenleri, hatalar veya kötü amaçlı açıkları kodlamak için olası sınırlamak için gizlenebilir.  
  
 Sınıfları hakkında daha fazla bilgi için bkz: [sınıfları](../../../csharp/programming-guide/classes-and-structs/classes.md) ve [nesneleri](../../../csharp/programming-guide/classes-and-structs/objects.md).  
  
### <a name="members"></a>Üyeler  
 Tüm yöntemleri, alanları, sabitleri, özellikleri ve olayları içinde bir tür bildirilmelidir; Bunlar adlandırılır *üyeleri* türü. C# ' ta genel değişkenler veya yok yöntemleri gibi diğer bazı dillerde. Bile bir programın giriş noktası `Main` yöntemi, bir sınıf veya yapı içinde bildirilmelidir. Aşağıdaki listede, bir sınıf veya yapı biriminde bildirilmelidir üyeleri tüm çeşitli türleri içerir.  
  
-   [Alanları](../../../csharp/programming-guide/classes-and-structs/fields.md)  
  
-   [Sabitleri](../../../csharp/programming-guide/classes-and-structs/constants.md)  
  
-   [Özellikleri](../../../csharp/programming-guide/classes-and-structs/properties.md)  
  
-   [Yöntemleri](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [Oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [Olayları](../../../csharp/programming-guide/events/index.md)  
  
-   [Sonlandırıcılar](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
  
-   [Dizin oluşturucular](../../../csharp/programming-guide/indexers/index.md)  
  
-   [İşleçler](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
  
-   [İç içe geçmiş türler](../../../csharp/programming-guide/classes-and-structs/nested-types.md)  
  
### <a name="accessibility"></a>Erişilebilirlik  
 Bazı yöntemleri ve özellikleri adlı veya sınıf veya yapı olarak bilinen, dışındaki koddan erişilen yöneliktir *istemci kodu*. Diğer yöntemleri ve özellikleri yalnızca sınıfta veya yapı kendisini kullanmak için olabilir. Yalnızca hedeflenen istemci kodu erişebilmesi kodunuzu erişilebilirliğini sınırlamak önemlidir. Nasıl, türleri ve üyeleri için istemci kodu erişim değiştiricileri kullanarak erişilebilir belirttiğiniz [ortak](../../../csharp/language-reference/keywords/public.md), [korumalı](../../../csharp/language-reference/keywords/protected.md), [iç](../../../csharp/language-reference/keywords/internal.md), [ İç korumalı](../../../csharp/language-reference/keywords/protected-internal.md), [özel](../../../csharp/language-reference/keywords/private.md) ve [korumalı özel](../../../csharp/language-reference/keywords/private-protected.md). Varsayılan erişilebilirlik olduğu `private`. Daha fazla bilgi için bkz: [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
### <a name="inheritance"></a>Devralma  
 Sınıflar (ancak değil yapılar) devralma kavramını destekler. Başka bir sınıftan türeyen bir sınıf ( *temel sınıfı*) otomatik olarak temel sınıf oluşturucular ve sonlandırıcılar dışındaki tüm ortak, korumalı ve iç üyeleri içerir. Daha fazla bilgi için bkz: [devralma](../../../csharp/programming-guide/classes-and-structs/inheritance.md) ve [çok biçimlilik](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).  
  
 Sınıflar olarak bildirilebilir [soyut](../../../csharp/language-reference/keywords/abstract.md), bir veya daha fazla yöntemleriyle uygulaması olduğunu anlamına gelir. Soyut sınıflar doğrudan başlatılamaz rağmen eksik uygulama sağlayan diğer sınıflar için taban sınıflar olarak hizmet verebilir. Sınıfları ayrıca olarak bildirilebilir [korumalı](../../../csharp/language-reference/keywords/sealed.md) onlardan devralan diğer sınıflara önlemek için. Daha fazla bilgi için bkz: [soyut ve korumalı sınıflar ve sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
### <a name="interfaces"></a>Arabirimler  
 Sınıflar ve yapılar birden çok arabirim devralabilirsiniz. Türü arabiriminde tanımlanan tüm yöntemleri uygulayan bir arabirim anlamına gelir devralmak için. Daha fazla bilgi için bkz: [arabirimleri](../../../csharp/programming-guide/interfaces/index.md).  
  
### <a name="generic-types"></a>Genel türler  
 Bir veya daha fazla tür parametreleri ile sınıfları ve yapıları tanımlanabilir. Türünün bir örneğini oluşturduğunda, istemci kodu türü sağlar. Örneğin <xref:System.Collections.Generic.List%601> sınıfını <xref:System.Collections.Generic> ad alanı, bir tür parametresi ile tanımlanır. İstemci kodu bir örneğini oluşturur bir `List<string>` veya `List<int>` listesi tutacak türünü belirtin. Daha fazla bilgi için bkz: [genel türler](../../../csharp/programming-guide/generics/index.md).  
  
### <a name="static-types"></a>Statik türler  
 Olarak sınıflar (ancak değil yapılar) bildirilebilir [statik](../../../csharp/language-reference/keywords/static.md). Statik sınıf yalnızca statik üyeler içerebilir ve new anahtar sözcüğü ile başlatılamaz. Sınıfının bir kopya program yüklediğinde belleğe yüklendiği ve üyeleri sınıf adı erişilir. Sınıflar ve yapılar statik üyeler içerebilir. Daha fazla bilgi için bkz: [statik sınıflar ve statik sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
### <a name="nested-types"></a>İç içe Geçmiş Türler  
 Sınıfta veya yapı başka bir sınıf veya yapı içinde iç içe. Daha fazla bilgi için bkz: [iç içe geçmiş türler](../../../csharp/programming-guide/classes-and-structs/nested-types.md).  
  
### <a name="partial-types"></a>Kısmi türler  
 Bir sınıf, yapı veya bir kod dosyasında yöntemi bir parçası ve başka bir bölümü ayrı kod dosyasında tanımlayabilirsiniz. Daha fazla bilgi için bkz: [kısmi sınıflar ve yöntemler](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).  
  
### <a name="object-initializers"></a>Nesne başlatıcıları  
 Örneği ve bunların Oluşturucusu açıkça çağırmadan sınıf veya yapı nesneleri ve nesnelerin koleksiyonu başlatma. Daha fazla bilgi için bkz: [nesne ve koleksiyon başlatıcıları](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
### <a name="anonymous-types"></a>Anonim Türler  
 Bu kullanışlı veya adlandırılmış bir sınıf oluşturmak gerekli olduğu durumlarda, örneğin ne zaman listesini verilerle doldurma yapıları devam veya başka bir yönteme geçirin gerekmez, anonim türler kullanın. Daha fazla bilgi için bkz: [anonim türler](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
### <a name="extension-methods"></a>Uzantı Metotları  
 "Bir sınıf özgün türüne aitse gibi yöntemleri çağrılabilir ayrı bir türü oluşturarak türetilmiş bir sınıf oluşturmadan genişletebilirsiniz". Daha fazla bilgi için bkz: [genişletme yöntemleri](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).  
  
### <a name="implicitly-typed-local-variables"></a>Örtülü Olarak Yazılan Yerel Değişkenler  
 Bir sınıf veya yapı yöntemi içinde örtülü yazma doğru türde derleme zamanında belirlemek için görevlendirin için kullanabilirsiniz. Daha fazla bilgi için bkz: [örtük olarak yazılan yerel değişkenler](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)
