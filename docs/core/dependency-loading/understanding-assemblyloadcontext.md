---
title: AssemblyLoadContext-.NET Core 'ı anlama
description: .NET Core 'da AssemblyLoadContext 'in amacını ve davranışını anlamak için temel kavramlar.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 293c586163921f9226916b177b3a29cc99c3e695
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70017343"
---
# <a name="understanding-systemruntimeloaderassemblyloadcontext"></a>System. Runtime. Loader. AssemblyLoadContext 'i anlama

<xref:System.Runtime.Loader.AssemblyLoadContext> Sınıfı .NET Core için benzersizdir. Bu makale, <xref:System.Runtime.Loader.AssemblyLoadContext> kavramsal bilgilerle API belgelerini tamamlayacak şekilde çalışır.

Bu makale, dinamik yükleme, özellikle dinamik yükleme çerçevesi geliştiricileri uygulayan geliştiricilerle ilgilidir.

## <a name="what-is-the-assemblyloadcontext"></a>AssemblyLoadContext nedir?

Her .NET Core uygulaması, <xref:System.Runtime.Loader.AssemblyLoadContext>örtülü olarak öğesini kullanır.
Bağımlılıkları bulmak ve yüklemek için çalışma zamanının sağlayıcısıdır. Her bağımlılık yüklendiğinde, bunu bulmak için <xref:System.Runtime.Loader.AssemblyLoadContext> bir örnek çağırılır.

- Yönetilen derlemeleri ve diğer bağımlılıkları bulma, yükleme ve önbelleğe alma hizmeti sağlar.

- Dinamik kod yüklemeyi ve kaldırmayı desteklemek için, kodu ve onun bağımlılıklarını kendi <xref:System.Runtime.Loader.AssemblyLoadContext> örneğinde yüklemek için yalıtılmış bir bağlam oluşturur.

## <a name="when-do-you-need-multiple-assemblyloadcontext-instances"></a>Birden çok AssemblyLoadContext örneğine ne zaman ihtiyacınız var?

Tek <xref:System.Runtime.Loader.AssemblyLoadContext> bir örnek <xref:System.Reflection.Assembly> ,<xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>basit bir derleme adının tam olarak bir sürümünü yüklemek için sınırlıdır.

Bu kısıtlama, kod modüllerini dinamik olarak yüklerken bir sorun olabilir. Her modül bağımsız olarak derlenir ve farklı sürümlerine <xref:System.Reflection.Assembly>bağlı olabilir. Bu sorun genellikle farklı modüller yaygın olarak kullanılan bir kitaplığın farklı sürümlerine bağımlıysa oluşur.

Kodu dinamik olarak yüklemeyi desteklemek için, <xref:System.Runtime.Loader.AssemblyLoadContext> API, aynı uygulamada çakışan sürümlerini <xref:System.Reflection.Assembly> yüklemeyi sağlar. Her <xref:System.Runtime.Loader.AssemblyLoadContext> örnek, her biri <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> belirli <xref:System.Reflection.Assembly> bir örneğe benzersiz bir sözlük eşlemesi sağlar.

Ayrıca, daha sonra kaldırmak üzere bir kod modülüyle ilişkili bağımlılıkları gruplandırmak için kullanışlı bir mekanizma sağlar.

## <a name="what-is-special-about-the-assemblyloadcontextdefault-instance"></a>AssemblyLoadContext. Default örneği hakkında özel nedir?

<xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> Örnek, başlangıçta çalışma zamanına göre otomatik olarak doldurulur.  Tüm statik bağımlılıkları bulmak ve bulmak için [Varsayılan yoklama](default-probing.md) kullanır.

En yaygın bağımlılık yükleme senaryolarını çözer.

## <a name="how-does-assemblyloadcontext-support-dynamic-dependencies"></a>AssemblyLoadContext dinamik bağımlılıkları nasıl destekler?

<xref:System.Runtime.Loader.AssemblyLoadContext>geçersiz kılınabilen çeşitli olaylara ve sanal işlevlere sahiptir.

<xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> Örnek yalnızca olayları geçersiz kılmayı destekler.

Makale [yönetilen derleme yükleme algoritması](loading-managed.md), [uydu derleme yükleme algoritması](loading-resources.md)ve [yönetilmeyen (yerel) kitaplık yükleme algoritması](loading-unmanaged.md) , tüm kullanılabilir olaylara ve sanal işlevlere başvurur.  Makaleler, yükleme algoritmalarında her bir olay ve işlevin göreli konumunu gösterir. Bu makale, bu bilgileri yeniden oluşturmaz.

Bu bölüm, ilgili olaylar ve işlevler için genel ilkeleri ele alır.

- **Tekrarlanabilir**. Belirli bir bağımlılık sorgusu her zaman aynı yanıta neden olmalıdır. Aynı yüklü bağımlılık örneğinin döndürülmesi gerekir. Bu gereksinim, önbellek tutarlılığı için temel bir gereksinimdir. Özel olarak yönetilen derlemeler için bir <xref:System.Reflection.Assembly> önbellek oluşturuyoruz. Önbellek anahtarı basit bir derleme adıdır, <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>.
- **Genellikle oluşturmayın**.  İstenen bağımlılığı bulamadığınızda bu işlevlerin throw `null` yerine dönmesi beklenmektedir. Oluşturma, aramayı erken sona erdirmek ve çağırana bir özel durum yaymaya çalışır. Oluşturma, bozuk bir derleme veya bellek yetersiz durumu gibi beklenmeyen hatalarla sınırlandırılmalıdır.
- **Özyineleme kullanmaktan kaçının**. Bu işlevlerin ve işleyicilerin bağımlılıkları bulmak için yükleme kurallarını uyguladığının farkında olun. Uygulamanız özyineleme tetikleyen API 'Leri çağırmalıdır. Kodunuz, genellikle belirli bir yol veya bellek başvuru bağımsız değişkeni gerektiren **Assemblyloadcontext** yükleme işlevlerini çağırmalıdır.
- **Doğru AssemblyLoadContext Içine yükleyin**. Bağımlılıkların nereye yükleneceğini seçme seçeneği uygulamaya özgüdür.  Bu seçenek, bu olaylar ve işlevler tarafından uygulanır. Kodunuz **Assemblyloadcontext** load-path işlevlerini çağırdığında, kodu kodun yüklenmesini istediğiniz örnekte çağırır. Yükün döndürülmesinin `null` ve <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> tanıtıcının bir süre, en basit seçenek olabilir.
- **İş parçacığı rampalarından haberdar olun**. Yükleme birden çok iş parçacığı tarafından tetiklenebilir. AssemblyLoadContext, kendi önbelleğine derleme ekleyerek iş parçacığı parçacıklarını işler. Yarış Loser 'ın örneği atılır. Uygulama mantığınızdaki birden çok iş parçacığını düzgün bir şekilde işlemeyen ek mantık eklemeyin.

## <a name="how-are-dynamic-dependencies-isolated"></a>Dinamik bağımlılıklar nasıl yalıtılmalıdır?

Her <xref:System.Runtime.Loader.AssemblyLoadContext> örnek, örnekler ve <xref:System.Type> tanımlar için <xref:System.Reflection.Assembly> benzersiz bir kapsamı temsil eder.

Bu bağımlılıklar arasında ikili yalıtım yoktur. Bunlar yalnızca adı tarafından birbirini bulmayan yalıtılırlar.

Her <xref:System.Runtime.Loader.AssemblyLoadContext>birinde:

- <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>, farklı <xref:System.Reflection.Assembly> bir örneğe başvurabilir.
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>aynı tür `name`için farklı bir tür örneği döndürebilir.

## <a name="how-are-dependencies-shared"></a>Bağımlılıklar nasıl paylaşılır?

Bağımlılıklar, örnekler arasında <xref:System.Runtime.Loader.AssemblyLoadContext> kolayca paylaşılabilir. Genel model bir bağımlılık yüklemek içindir <xref:System.Runtime.Loader.AssemblyLoadContext> .  Diğeri, yüklenen derlemeye bir başvuru kullanarak bağımlılığı paylaşır.

Bu paylaşım, çalışma zamanı derlemeleri için gereklidir. Bu derlemeler yalnızca öğesine <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>yüklenebilir. , `ASP.NET` ,`WPF`Veya gibiçerçeveler`WinForms`için de gereklidir.

Paylaşılan bağımlılıkların ' de yüklü <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>olması önerilir. Bu paylaşım, ortak tasarım modelidir.

Paylaşma, özel <xref:System.Runtime.Loader.AssemblyLoadContext> örneğin kodlamasına uygulanır. <xref:System.Runtime.Loader.AssemblyLoadContext>geçersiz kılınabilen çeşitli olaylara ve sanal işlevlere sahiptir. Bu işlevlerden herhangi biri başka <xref:System.Reflection.Assembly> <xref:System.Runtime.Loader.AssemblyLoadContext> bir örneğe yüklenmiş bir örneğe başvuru döndürzaman, <xref:System.Reflection.Assembly> örnek paylaşılır. Standart yük algoritması, ortak paylaşım deseninin <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> basitleşmesini sağlamak için ' a erteler.  Bkz. [yönetilen derleme yükleme algoritması](loading-managed.md).

## <a name="complications"></a>Zorluk Grubu

### <a name="type-conversion-issues"></a>Tür dönüştürme sorunları

İki <xref:System.Runtime.Loader.AssemblyLoadContext> örnek aynı `name`ile tür tanımlarını içerdiğinde, aynı türde değildir. Yalnızca aynı <xref:System.Reflection.Assembly> örnekten geliyorsa, bu tür aynıdır.

Önemli bir karmaşıklaşmak için, bu eşleşmeyen türler hakkındaki özel durum iletileri kafa karıştırıcı olabilir. Türler, özel durum iletilerinde basit tür adlarına göre adlandırılır. Bu durumda ortak özel durum iletisi şu biçimdedir:

```
Object of type 'IsolatedType' cannot be converted to type 'IsolatedType'.
```

### <a name="debugging-type-conversion-issues"></a>Tür dönüştürme sorunlarını ayıklama

Eşleşmeyen türlerin çifti verildiğinde şunları da bilmelidir:
- Her tür<xref:System.Type.Assembly?displayProperty=nameWithType>
- Her tür <xref:System.Runtime.Loader.AssemblyLoadContext>, <xref:System.Runtime.Loader.AssemblyLoadContext.GetLoadContext(System.Reflection.Assembly)?displayProperty=nameWithType> işlev aracılığıyla elde edilebilir.

İki nesne `a` verildiğinde ve `b`hata ayıklayıcıda aşağıdakilerin değerlendirmesi yararlı olacaktır:

```C#
// In debugger look at each assembly's instance, Location, and FullName
a.GetType().Assembly
b.GetType().Assembly
// In debugger look at each AssemblyLoadContext's instance and name
System.Runtime.AssemblyLoadContext.GetLoadContext(a.GetType().Assembly)
System.Runtime.AssemblyLoadContext.GetLoadContext(b.GetType().Assembly)
```

### <a name="resolving-type-conversion-issues"></a>Tür dönüştürme sorunlarını çözme

Bu tür dönüştürme sorunlarını çözmek için iki tasarım deseni vardır.

1. Ortak paylaşılan türleri kullanın. Bu paylaşılan tür, temel bir çalışma zamanı türü olabilir veya paylaşılan bir derlemede yeni bir paylaşılan tür oluşturulmasını içerebilir.  Genellikle paylaşılan tür, uygulama derlemesinde tanımlanan bir [arabirimdir](../../csharp/language-reference/keywords/interface.md) . Ayrıca bkz: [Bağımlılıklar nasıl paylaşılır?](#how-are-dependencies-shared).

2. Bir türden diğerine dönüştürmek için sıralama tekniklerini kullanın.
