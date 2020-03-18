---
title: AssemblyLoadContext'ı Anlama - .NET Core
description: .NET Core'da AssemblyLoadContext'ın amacını ve davranışını anlamak için temel kavramlar.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 8a73a432bf8cc72cced77cf6c62a785b72032913
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72291255"
---
# <a name="understanding-systemruntimeloaderassemblyloadcontext"></a>Anlama Sistemi.Runtime.Loader.AssemblyLoadContext

Sınıf <xref:System.Runtime.Loader.AssemblyLoadContext> .NET Core'a özgüdür. Bu makalede, API dokümantasyonlarını <xref:System.Runtime.Loader.AssemblyLoadContext> kavramsal bilgilerle tamamlamaya çalışır.

Bu makale, dinamik yükleme, özellikle dinamik yükleme çerçeve geliştiricileri uygulayan geliştiriciler için ilgilidir.

## <a name="what-is-the-assemblyloadcontext"></a>AssemblyLoadContext nedir?

Her .NET Core uygulaması <xref:System.Runtime.Loader.AssemblyLoadContext>örtülü olarak .
Bağımlılıkları bulmak ve yüklemek için çalışma zamanı sağlayıcısıdır. Bir bağımlılık yüklendiğinde, onu <xref:System.Runtime.Loader.AssemblyLoadContext> bulmak için bir örnek çağrılır.

- Yönetilen derlemeleri ve diğer bağımlılıkları bulma, yükleme ve önbelleğe alma hizmeti sağlar.

- Dinamik kod yükleme ve boşaltmayı desteklemek için, kod yükleme ve kendi <xref:System.Runtime.Loader.AssemblyLoadContext> örneğindeki bağımlılıkları için yalıtılmış bir bağlam oluşturur.

## <a name="when-do-you-need-multiple-assemblyloadcontext-instances"></a>Birden çok AssemblyLoadContext örneğine ne zaman ihtiyacınız var?

Tek <xref:System.Runtime.Loader.AssemblyLoadContext> bir örnek, basit bir montaj <xref:System.Reflection.Assembly> adı başına <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>tam bir sürümünü yüklemekle sınırlıdır.

Kod modüllerini dinamik olarak yüklerken bu kısıtlama sorun haline gelebilir. Her modül bağımsız olarak derlenir ve bir <xref:System.Reflection.Assembly>.'ün farklı sürümlerine bağlı olabilir. Bu sorun genellikle farklı modüller yaygın olarak kullanılan kitaplığın farklı sürümlerine bağlı olduğunda oluşur.

Dinamik yükleme kodunu desteklemek <xref:System.Runtime.Loader.AssemblyLoadContext> için API, aynı uygulamadaki <xref:System.Reflection.Assembly> bir uygulamanın çakışan sürümlerini yüklemeyi sağlar. Her <xref:System.Runtime.Loader.AssemblyLoadContext> örnek, her <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> biri belirli <xref:System.Reflection.Assembly> bir örneğin eşlemesini benzersiz bir sözlük sağlar.

Ayrıca, daha sonra boşaltmak için bir kod modülü ile ilgili bağımlılıkları gruplandırmak için kullanışlı bir mekanizma sağlar.

## <a name="what-is-special-about-the-assemblyloadcontextdefault-instance"></a>AssemblyLoadContext.Default örneğinin özel özelliği nedir?

Örnek, <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> başlangıçtaçalışma süresine göre otomatik olarak doldurulur.  Tüm statik bağımlılıkları bulmak ve bulmak için [varsayılan sondalama](default-probing.md) kullanır.

En yaygın bağımlılık yükleme senaryolarını çözer.

## <a name="how-does-assemblyloadcontext-support-dynamic-dependencies"></a>AssemblyLoadContext dinamik bağımlılıkları nasıl destekler?

<xref:System.Runtime.Loader.AssemblyLoadContext>geçersiz kılınabilecek çeşitli olaylara ve sanal işlevlere sahiptir.

Örnek <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> yalnızca olayları geçersiz kılmayı destekler.

Makaleler [Yönetilen montaj yükleme algoritması,](loading-managed.md) [Uydu montaj yükleme algoritması](loading-resources.md)ve [Yönetilmeyen (yerel) kitaplık yükleme algoritması](loading-unmanaged.md) tüm kullanılabilir olaylar ve sanal işlevleri bakın.  Makaleler, yükleme algoritmalarında her olay ve işlevin göreli konumunu gösterir. Bu makale, bu bilgileri çoğaltmaz.

Bu bölüm, ilgili olaylar ve işlevler için genel ilkeleri kapsar.

- **Tekrarlanabilir olun.** Belirli bir bağımlılık için bir sorgu her zaman aynı yanıt neden olmalıdır. Aynı yüklenen bağımlılık örneği döndürülmelidir. Bu gereksinim, önbellek tutarlılığı için temeldir. Özellikle yönetilen derlemeler için bir <xref:System.Reflection.Assembly> önbellek oluşturuyoruz. Önbellek anahtarı basit bir derleme <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>adıdır.
- **Genellikle atmayın.**  İstenen bağımlılık bulamadığında bu işlevlerin atmak yerine dönmesi `null` beklenir. Atma erken arama sona erecek ve arayan için bir özel durum yaymak olacaktır. Atma bozuk bir derleme veya bellek dışı bir durum gibi beklenmeyen hatalarla sınırlı olmalıdır.
- **Özyinelemeden kaçının.** Bu işlevlerin ve işleyicilerin bağımlılıkları bulmak için yükleme kurallarını uyguladığını unutmayın. Uygulamanız, özyinelemeyi tetikleyen API'leri aramamalıdır. Kodunuz genellikle belirli bir yol veya bellek başvuru argümanı gerektiren **AssemblyLoadContext** yük işlevlerini çağırmalıdır.
- **Doğru AssemblyLoadContext'a yükleyin.** Bağımlılıkların yüklendiği yerin seçimi uygulamaya özgüdür.  Seçim bu olaylar ve işlevler tarafından uygulanır. Kodunuz **AssemblyLoadContext** load-by-path işlevlerini aradığında, kodun yüklenmesini istediğiniz durumda bunları arayın. Bazen geri `null` dönen ve <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> yükün işlemesine izin vermek en basit seçenek olabilir.
- **Konu yarışları farkında olun.** Yükleme birden çok iş parçacığı tarafından tetiklenebilir. AssemblyLoadContext, önbelleğine atomik olarak derlemeler ekleyerek iş parçacığı yarışlarını işler. Yarış kaybedeninin örneği atılır. Uygulama mantığınızda, birden çok iş parçacığı düzgün işlemeyen ekstra mantık eklemeyin.

## <a name="how-are-dynamic-dependencies-isolated"></a>Dinamik bağımlılıklar nasıl yalıtılır?

Her <xref:System.Runtime.Loader.AssemblyLoadContext> örnek, örnekler <xref:System.Reflection.Assembly> ve <xref:System.Type> tanımlar için benzersiz bir kapsamı temsil eder.

Bu bağımlılıklar arasında ikili izolasyon yok. Sadece birbirlerini isme göre bulamadıkları için izole edilmişler.

Her <xref:System.Runtime.Loader.AssemblyLoadContext>birinde:

- <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>farklı <xref:System.Reflection.Assembly> bir örneğe başvurabilir.
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>aynı tür `name`için farklı bir tür örneği döndürebilir.

## <a name="how-are-dependencies-shared"></a>Bağımlılıklar nasıl paylaşılır?

Bağımlılıklar örnekler arasında <xref:System.Runtime.Loader.AssemblyLoadContext> kolayca paylaşılabilir. Genel model bir <xref:System.Runtime.Loader.AssemblyLoadContext> bağımlılık yüklemek için bir.  Diğer, yüklenen derlemeye bir başvuru kullanarak bağımlılığı paylaşır.

Bu paylaşım çalışma zamanı derlemeleri için gereklidir. Bu derlemeler yalnızca <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>. Aynı şey `ASP.NET`, `WPF`, veya `WinForms`.

Paylaşılan bağımlılıkların <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>' a yüklenmesi önerilir. Bu paylaşım ortak tasarım desenidir.

Paylaşım, özel <xref:System.Runtime.Loader.AssemblyLoadContext> örneğin kodlanmasında uygulanır. <xref:System.Runtime.Loader.AssemblyLoadContext>geçersiz kılınabilecek çeşitli olaylara ve sanal işlevlere sahiptir. Bu işlevlerden herhangi biri başka <xref:System.Reflection.Assembly> <xref:System.Runtime.Loader.AssemblyLoadContext> bir örnekte yüklenen bir <xref:System.Reflection.Assembly> örne başvuru döndürdüğünde, örnek paylaşılır. Standart yükleme algoritması, <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> ortak paylaşım deseni basitleştirmek için yüklemeiçin erteler.  Bkz. [Yönetilen montaj yükleme algoritması.](loading-managed.md)

## <a name="complications"></a>Zorluk Grubu

### <a name="type-conversion-issues"></a>Tür dönüştürme sorunları

İki <xref:System.Runtime.Loader.AssemblyLoadContext> örnek aynı `name`tür tanımları içeriyorsa, aynı türde değildir. Aynı <xref:System.Reflection.Assembly> örnekten geliyorsa aynı tipteler.

Sorunları karmaşıklaştırmak için, bu eşleşmemiş türleri hakkında özel durum iletileri kafa karıştırıcı olabilir. Türler, özel durum iletilerinde basit tür adlarıyla adlandırılır. Bu durumda ortak özel durum iletisi formolacaktır:

> 'Yalıtılmış Tip' türünden bir nesne 'Yalıtılmış Yazı' türüne dönüştürülemez.

### <a name="debugging-type-conversion-issues"></a>Tür dönüştürme sorunlarını hata ayıklama

Uyumsuz türleri bir çift göz önüne alındığında da bilmek önemlidir:

- Her tür<xref:System.Type.Assembly?displayProperty=nameWithType>
- Her <xref:System.Runtime.Loader.AssemblyLoadContext>tür, <xref:System.Runtime.Loader.AssemblyLoadContext.GetLoadContext(System.Reflection.Assembly)?displayProperty=nameWithType> hangi fonksiyonu ile elde edilebilir.

Verilen iki `a` nesne `b`ve , hata ayıklama aşağıdaki değerlendirilmesi yararlı olacaktır:

```csharp
// In debugger look at each assembly's instance, Location, and FullName
a.GetType().Assembly
b.GetType().Assembly
// In debugger look at each AssemblyLoadContext's instance and name
System.Runtime.AssemblyLoadContext.GetLoadContext(a.GetType().Assembly)
System.Runtime.AssemblyLoadContext.GetLoadContext(b.GetType().Assembly)
```

### <a name="resolving-type-conversion-issues"></a>Tür dönüştürme sorunlarını çözme

Bu tür dönüştürme sorunlarını çözmek için iki tasarım delemi vardır.

1. Ortak paylaşılan türleri kullanın. Bu paylaşılan tür ilkel bir çalışma zamanı türü olabilir veya paylaşılan bir derlemede yeni bir paylaşılan tür oluşturmayı içerebilir.  Genellikle paylaşılan tür, bir uygulama derlemesinde tanımlanan bir [arabirimdir.](../../csharp/language-reference/keywords/interface.md) Ayrıca bakınız: [Bağımlılıklar nasıl paylaşılır?](#how-are-dependencies-shared)

2. Bir türden diğerine dönüştürmek için mareşalleme tekniklerini kullanın.
