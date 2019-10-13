---
title: AssemblyLoadContext-.NET Core 'ı anlama
description: .NET Core 'da AssemblyLoadContext 'in amacını ve davranışını anlamak için temel kavramlar.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 8a73a432bf8cc72cced77cf6c62a785b72032913
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291255"
---
# <a name="understanding-systemruntimeloaderassemblyloadcontext"></a>System. Runtime. Loader. AssemblyLoadContext 'i anlama

@No__t-0 sınıfı .NET Core için benzersizdir. Bu makale, kavramsal bilgilerle <xref:System.Runtime.Loader.AssemblyLoadContext> API belgelerini tamamlayacak şekilde çalışır.

Bu makale, dinamik yükleme, özellikle dinamik yükleme çerçevesi geliştiricileri uygulayan geliştiricilerle ilgilidir.

## <a name="what-is-the-assemblyloadcontext"></a>AssemblyLoadContext nedir?

Her .NET Core uygulaması örtük olarak <xref:System.Runtime.Loader.AssemblyLoadContext> kullanır.
Bağımlılıkları bulmak ve yüklemek için çalışma zamanının sağlayıcısıdır. Her bağımlılık yüklendiğinde, bunu bulmak için bir <xref:System.Runtime.Loader.AssemblyLoadContext> örneği çağırılır.

- Yönetilen derlemeleri ve diğer bağımlılıkları bulma, yükleme ve önbelleğe alma hizmeti sağlar.

- Dinamik kod yüklemeyi ve kaldırmayı desteklemek için, kodu ve onun bağımlılıklarını kendi <xref:System.Runtime.Loader.AssemblyLoadContext> örneğine yüklemek için yalıtılmış bir bağlam oluşturur.

## <a name="when-do-you-need-multiple-assemblyloadcontext-instances"></a>Birden çok AssemblyLoadContext örneğine ne zaman ihtiyacınız var?

Tek bir <xref:System.Runtime.Loader.AssemblyLoadContext> örneği, basit derleme adı başına <xref:System.Reflection.Assembly> ' in tam olarak bir sürümünü yüklemek için sınırlıdır <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>.

Bu kısıtlama, kod modüllerini dinamik olarak yüklerken bir sorun olabilir. Her modül bağımsız olarak derlenir ve <xref:System.Reflection.Assembly> ' ın farklı sürümlerine bağlı olabilir. Bu sorun genellikle farklı modüller yaygın olarak kullanılan bir kitaplığın farklı sürümlerine bağımlıysa oluşur.

Kodu dinamik olarak yüklemeyi desteklemek için <xref:System.Runtime.Loader.AssemblyLoadContext> API 'SI, aynı uygulamada bir <xref:System.Reflection.Assembly> ' in çakışan sürümlerini yüklemeyi sağlar. Her <xref:System.Runtime.Loader.AssemblyLoadContext> örneği, belirli bir <xref:System.Reflection.Assembly> örneğine her <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> benzersiz bir sözlük eşlemesi sağlar.

Ayrıca, daha sonra kaldırmak üzere bir kod modülüyle ilişkili bağımlılıkları gruplandırmak için kullanışlı bir mekanizma sağlar.

## <a name="what-is-special-about-the-assemblyloadcontextdefault-instance"></a>AssemblyLoadContext. Default örneği hakkında özel nedir?

@No__t-0 örneği başlangıçta çalışma zamanına göre otomatik olarak doldurulur.  Tüm statik bağımlılıkları bulmak ve bulmak için [Varsayılan yoklama](default-probing.md) kullanır.

En yaygın bağımlılık yükleme senaryolarını çözer.

## <a name="how-does-assemblyloadcontext-support-dynamic-dependencies"></a>AssemblyLoadContext dinamik bağımlılıkları nasıl destekler?

<xref:System.Runtime.Loader.AssemblyLoadContext> ' da geçersiz kılınabilen çeşitli olaylar ve sanal işlevler bulunur.

@No__t-0 örneği yalnızca olayları geçersiz kılmayı destekler.

Makale [yönetilen derleme yükleme algoritması](loading-managed.md), [uydu derleme yükleme algoritması](loading-resources.md)ve [yönetilmeyen (yerel) kitaplık yükleme algoritması](loading-unmanaged.md) , tüm kullanılabilir olaylara ve sanal işlevlere başvurur.  Makaleler, yükleme algoritmalarında her bir olay ve işlevin göreli konumunu gösterir. Bu makale, bu bilgileri yeniden oluşturmaz.

Bu bölüm, ilgili olaylar ve işlevler için genel ilkeleri ele alır.

- **Tekrarlanabilir**. Belirli bir bağımlılık sorgusu her zaman aynı yanıta neden olmalıdır. Aynı yüklü bağımlılık örneğinin döndürülmesi gerekir. Bu gereksinim, önbellek tutarlılığı için temel bir gereksinimdir. Özellikle yönetilen derlemeler için <xref:System.Reflection.Assembly> önbelleği oluşturacağız. Önbellek anahtarı basit bir derleme adıdır, <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>.
- **Genellikle oluşturmayın**.  İstenen bağımlılığı bulamadığınızda bu işlevlerin throw yerine 0 @no__t döndürmesi beklenir. Oluşturma, aramayı erken sona erdirmek ve çağırana bir özel durum yaymaya çalışır. Oluşturma, bozuk bir derleme veya bellek yetersiz durumu gibi beklenmeyen hatalarla sınırlandırılmalıdır.
- **Özyineleme kullanmaktan kaçının**. Bu işlevlerin ve işleyicilerin bağımlılıkları bulmak için yükleme kurallarını uyguladığının farkında olun. Uygulamanız özyineleme tetikleyen API 'Leri çağırmalıdır. Kodunuz, genellikle belirli bir yol veya bellek başvuru bağımsız değişkeni gerektiren **Assemblyloadcontext** yükleme işlevlerini çağırmalıdır.
- **Doğru AssemblyLoadContext Içine yükleyin**. Bağımlılıkların nereye yükleneceğini seçme seçeneği uygulamaya özgüdür.  Bu seçenek, bu olaylar ve işlevler tarafından uygulanır. Kodunuz **Assemblyloadcontext** load-path işlevlerini çağırdığında, kodu kodun yüklenmesini istediğiniz örnekte çağırır. @No__t-0 döndürme ve <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> tanıtıcısına izin verme en basit seçenek olabilir.
- **İş parçacığı rampalarından haberdar olun**. Yükleme birden çok iş parçacığı tarafından tetiklenebilir. AssemblyLoadContext, kendi önbelleğine derleme ekleyerek iş parçacığı parçacıklarını işler. Yarış Loser 'ın örneği atılır. Uygulama mantığınızdaki birden çok iş parçacığını düzgün bir şekilde işlemeyen ek mantık eklemeyin.

## <a name="how-are-dynamic-dependencies-isolated"></a>Dinamik bağımlılıklar nasıl yalıtılmalıdır?

Her <xref:System.Runtime.Loader.AssemblyLoadContext> örneği, <xref:System.Reflection.Assembly> örnekleri ve <xref:System.Type> tanımları için benzersiz bir kapsamı temsil eder.

Bu bağımlılıklar arasında ikili yalıtım yoktur. Bunlar yalnızca adı tarafından birbirini bulmayan yalıtılırlar.

Her <xref:System.Runtime.Loader.AssemblyLoadContext>:

- <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>, farklı bir <xref:System.Reflection.Assembly> örneğine başvurabilir.
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>, aynı `name` türü için farklı bir tür örneği döndürebilir.

## <a name="how-are-dependencies-shared"></a>Bağımlılıklar nasıl paylaşılır?

Bağımlılıklar, <xref:System.Runtime.Loader.AssemblyLoadContext> örnekleri arasında kolayca paylaşılabilir. Bir bağımlılığı yüklemek için genel model bir <xref:System.Runtime.Loader.AssemblyLoadContext> ' dır.  Diğeri, yüklenen derlemeye bir başvuru kullanarak bağımlılığı paylaşır.

Bu paylaşım, çalışma zamanı derlemeleri için gereklidir. Bu derlemeler yalnızca <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> ' a yüklenebilir. @No__t-0, `WPF` veya `WinForms` gibi çerçeveler için de aynı gereklidir.

Paylaşılan bağımlılıkların <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> ' a yüklenmesi önerilir. Bu paylaşım, ortak tasarım modelidir.

Paylaşım, özel <xref:System.Runtime.Loader.AssemblyLoadContext> örneğinin kodlamasına uygulanır. <xref:System.Runtime.Loader.AssemblyLoadContext> ' da geçersiz kılınabilen çeşitli olaylar ve sanal işlevler bulunur. Bu işlevlerden herhangi biri başka bir <xref:System.Runtime.Loader.AssemblyLoadContext> örneğine yüklenmiş <xref:System.Reflection.Assembly> örneğine bir başvuru döndürzaman, <xref:System.Reflection.Assembly> örneği paylaşılır. Standart yük algoritması, ortak paylaşım deseninin basitleştirilmesi için yükleme için <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> ' a erteler.  Bkz. [yönetilen derleme yükleme algoritması](loading-managed.md).

## <a name="complications"></a>Zorluk

### <a name="type-conversion-issues"></a>Tür dönüştürme sorunları

İki <xref:System.Runtime.Loader.AssemblyLoadContext> örneği aynı `name` ile tür tanımları içerdiğinde, aynı türde değildir. Bunlar yalnızca aynı <xref:System.Reflection.Assembly> örneğinden geliyorsa aynı türdür.

Önemli bir karmaşıklaşmak için, bu eşleşmeyen türler hakkındaki özel durum iletileri kafa karıştırıcı olabilir. Türler, özel durum iletilerinde basit tür adlarına göre adlandırılır. Bu durumda ortak özel durum iletisi şu biçimdedir:

> ' IsolatedType ' türündeki nesne ' IsolatedType ' türüne dönüştürülemez.

### <a name="debugging-type-conversion-issues"></a>Tür dönüştürme sorunlarını ayıklama

Eşleşmeyen türlerin çifti verildiğinde şunları da bilmelidir:

- Her türün <xref:System.Type.Assembly?displayProperty=nameWithType>
- Her türün <xref:System.Runtime.Loader.AssemblyLoadContext> ' ı <xref:System.Runtime.Loader.AssemblyLoadContext.GetLoadContext(System.Reflection.Assembly)?displayProperty=nameWithType> işlevi aracılığıyla elde edilebilir.

@No__t-0 ve `b` olmak üzere iki nesne verildiğinde, hata ayıklayıcıda şunları değerlendirmek yararlı olacaktır:

```csharp
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
