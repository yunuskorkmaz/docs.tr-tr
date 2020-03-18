---
title: Oluşturucu Tasarımı
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines, constructors
- constructors, design guidelines
- instance constructors
- type constructors
- virtual members
- constructors, types
- parameterless constructors
- static constructors
ms.assetid: b4496afe-5fa7-4bb0-85ca-70b0ef21e6fc
ms.openlocfilehash: 7ab795cd4c6e0ff5e1451c05987848c41bd69577
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400605"
---
# <a name="constructor-design"></a>Oluşturucu Tasarımı

İki tür yapıcı vardır: tip yapıcılar ve örnek yapıcılar.

Tür oluşturucular statiktir ve tür kullanılmadan önce CLR tarafından çalıştırılır. Örnek oluşturucular, bir tür örneği oluşturulduğunda çalışır.

Tür oluşturucular herhangi bir parametre alamaz. Örnek yapıcılar yapabilir. Herhangi bir parametre almayan örnek yapıcılar genellikle parametresiz yapıcılar olarak adlandırılır.

Yapıcılar, bir tür örnekleri oluşturmanın en doğal yoludur. Çoğu geliştirici, örnek oluşturmanın alternatif yollarını (fabrika yöntemleri gibi) düşünmeden önce bir oluşturucuüzerinde arama yapar ve kullanmaya çalışır.

✔️ basit, ideal varsayılan, yapıcılar sağlayan düşünün.

Basit bir oluşturucu nun çok az sayıda parametresi vardır ve tüm parametreler ilkel veya enumdur. Bu tür basit yapıcılar çerçevenin kullanılabilirliğini artırır.

✔️, istenilen işlemin anlambilimi doğrudan yeni bir örneğin yapımıyla eşleninmiyorsa veya konstrüktör tasarım yönergelerini izleyerek doğal değilse, yapıcı yerine statik bir fabrika yöntemi kullanmayı düşünün.

✔️ DO, ana özellikleri ayarlamak için kısayol olarak oluşturucu parametreleri kullanır.

Boş yapıcıyı ve ardından bazı özellik kümelerini kullanmakla birden çok bağımsız değişkeni olan bir oluşturucu kullanmak arasında anlam ayrımı olmamalıdır.

✔️ Yapı parametreleri için aynı adı ve bir özellik için yapı parametreleri yalnızca özelliği ayarlamak için kullanılırsa kullanın.

Bu parametreler ve özellikleri arasındaki tek fark kasa olmalıdır.

✔️ yapıcı minimum iş yapmak.

Yapıcılar, yapıcı parametreleri yakalamak dışında çok fazla iş yapmamalıdır. Başka bir işlemin maliyeti gerekli olana kadar geciktirilmelidir.

✔️ DO, uygunsa örnek oluşturuculardan özel durumlar atar.

✔️ DO, böyle bir oluşturucu gerekliyse, sınıflardaki kamu parametresiz oluşturucuyu açıkça beyan edin.

Bir türde herhangi bir oluşturucuaçıkça beyan etmezseniz, birçok dil (C# gibi) otomatik olarak bir kamu parametresiz oluşturucu ekler. (Soyut sınıflar korunan bir yapıcı alır.)

Bir sınıfa parametreli oluşturucu eklemek derleyicinin parametresiz oluşturucuyu eklemesini engeller. Bu genellikle kazara kırılma değişikliklerine neden olur.

❌Yapılar üzerinde parametresiz yapıcıları açıkça tanımlamaktan kaçının.

Bu, parametresiz oluşturucu tanımlanmamışsa, dizideki her yuvada çalıştırılması gerekmedığından, dizi oluşturmayı hızlandırır. C# da dahil olmak üzere birçok derleyicinin bu nedenle yapı oluşturuculara sahip olması izin vermeyin.

❌Oluşturucusu içindeki bir nesneye sanal üyeleri çağırmaktan kaçının.

En çok türetilmiş türün oluşturucusu henüz tam olarak çalıştırılmasa bile, sanal bir üyeyi çağırmak en çok türetilmiş geçersiz kılmanın çağrılmasını sağlar.

## <a name="type-constructor-guidelines"></a>Tip Oluşturucu Yönergeleri

✔️ statik yapıcılar özel yapmak.

Bir tür e-baş harflerini almak için sınıf oluşturucu olarak da adlandırılan statik bir oluşturucu kullanılır. CLR, türün ilk örneği oluşturulmadan veya bu türdeki statik üyeler çağrılmadan önce statik oluşturucuyu çağırır. Statik oluşturucu çağrıldığında kullanıcının denetimi yoktur. Statik bir oluşturucu özel değilse, CLR dışındaki kodla çağrılabilir. Oluşturucuda gerçekleştirilen işlemlere bağlı olarak, bu beklenmeyen davranışlara neden olabilir. C# derleyicisi statik yapıcıları özel olmaya zorlar.

❌Statik oluşturuculardan özel durumlar ATMAYIN.

Bir tür oluşturucudan bir özel durum atılırsa, tür geçerli uygulama etki alanında kullanılabilir değildir.

✔️, çalışma zamanı açıkça tanımlanmış statik oluşturucusu olmayan türlerin performansını en iyi duruma getirebildiği için, statik alanları açıkça statik oluşturucukullanmak yerine satır satır da başlatmayı düşünün.

*2005, 2009 Microsoft Corporation © bölümleri. Tüm hakları saklıdır.*

*Pearson Education, Inc.'in izniyle [Framework Design Guidelines: Conventions, Idioms and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina ve Brad Abrams tarafından 22 Ekim 2008'de Addison-Wesley Professional tarafından Microsoft Windows Geliştirme Serisi'nin bir parçası olarak yayımlandı.*

## <a name="see-also"></a>Ayrıca bkz.

- [Üye Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/member.md)
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
