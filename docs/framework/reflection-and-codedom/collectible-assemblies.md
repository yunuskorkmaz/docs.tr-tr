---
title: Dinamik tür oluşturma için toplanabilir derlemeler
description: ''
ms.date: 08/29/2017
helpviewer_keywords:
- reflection, dynamic assembly
- assemblies, collectible
- collectible assemblies, retrieving
ms.openlocfilehash: 02c7048e0321282463aa3558287d1d13c5e4f8d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180538"
---
# <a name="collectible-assemblies-for-dynamic-type-generation"></a>Dinamik tür oluşturma için toplanabilir derlemeler

*Toplanabilir derlemeler* , oluşturuldukları uygulama etki alanının kaldırılması gerekmeden bellekten kaldırılabilen dinamik derlemelerdir. Bir toplanabilir derleme tarafından kullanılan tüm yönetilen ve yönetilmeyen bellek ve içerdiği türler geri kazanılır. Derleme adı gibi bilgiler iç tablolardan kaldırılır.

Kaldırmayı etkinleştirmek için, dinamik bir <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndCollect?displayProperty=nameWithType> derleme oluştururken bayrağını kullanın. Derleme geçicidir (diğer bir deyişle, kaydedilemez) ve [toplanabilir derlemelerde kısıtlamalar](#restrictions-on-collectible-assemblies) bölümünde açıklanan sınırlamalara tabidir. Ortak dil çalışma zamanı (CLR), derlemeyle ilişkili tüm nesneleri serbest bırakırsanız, toplanabilir bir derlemeyi otomatik olarak kaldırır. Diğer tüm yönden, toplanabilir derlemeler diğer dinamik Derlemelerle aynı şekilde oluşturulur ve kullanılır.

## <a name="lifetime-of-collectible-assemblies"></a>Toplanabilir derlemelerin ömrü

Toplanabilir bir derlemenin ömrü, içerdiği türlere yapılan başvuruların ve bu türlerden oluşturulan nesnelerin varlığı tarafından denetlenir. Ortak dil çalışma zamanı, aşağıdakilerden biri veya daha fazlası mevcut olduğu sürece bir derlemeyi kaldırmaz (`T` derlemede tanımlı herhangi bir tür):

- `T` öğesinin bir örneği.

- Bir dizisinin örneği `T`.

- Tür bağımsız değişkenlerinden biri olan bir genel türün `T` örneği. Bu `T`, koleksiyon boş olsa bile genel koleksiyonlarını içerir.

- Öğesini temsil <xref:System.Type> <xref:System.Reflection.Emit.TypeBuilder> `T`eden bir örneği.

   > [!IMPORTANT]
   > Derlemenin parçalarını temsil eden tüm nesneleri serbest bırakmanız gerekir. <xref:System.Reflection.Emit.ModuleBuilder> Tanımlar `T` öğesine <xref:System.Reflection.Emit.TypeBuilder>bir başvuru tutar ve <xref:System.Reflection.Emit.AssemblyBuilder> nesnesi öğesine bir başvuru <xref:System.Reflection.Emit.ModuleBuilder>tutar, bu nedenle bu nesnelere yapılan başvuruların serbest bırakılması gerekir. Bir <xref:System.Reflection.Emit.LocalBuilder> veya yapımını oluşturma sırasında <xref:System.Reflection.Emit.ILGenerator> kullanılması bile, kaldırmayı `T` engeller.

- Kod yürütülerek hala `T` erişilebilir olan, dinamik olarak `T1` tanımlanmış başka bir tür tarafından statik başvuru. Örneğin `T1` , öğesinden `T`türetilebilir veya `T` bir yöntemindeki parametre türü olabilir. `T1`

- Öğesine **ByRef** `T`ait olan statik bir alana ByRef.

- Bir <xref:System.RuntimeTypeHandle>, <xref:System.RuntimeFieldHandle>veya öğesine <xref:System.RuntimeMethodHandle> başvuran `T` bir, veya bir bileşeni `T`.

- Dolaylı olarak veya ' i temsil <xref:System.Type> `T`eden nesneye erişmek için doğrudan kullanılabilen herhangi bir yansıma nesnesinin örneği. Örneğin, <xref:System.Type> nesnesi `T` , öğe türü `T`olan bir dizi türünden veya tür bağımsız değişkeni olan genel bir türden `T` elde edilebilir.

- Herhangi bir `M` iş parçacığının çağrı yığınında bir yöntem, `M` `T` veya derlemede tanımlanan modül düzeyi bir yöntem.

- Derlemenin modülünde tanımlanan statik metoda bir temsilci.

Bu listedeki yalnızca bir öğe, derlemede yalnızca bir tür veya bir yöntem için mevcutsa, çalışma zamanı derlemeyi kaldıramıyor.

> [!NOTE]
> Çalışma zamanı, listedeki tüm öğeler için sonlandırıcılar çalıştırılıncaya kadar derlemeyi gerçekten kaldırmaz.

Kullanım ömrü açısından, bir toplanabilir derleme oluşturmak için oluşturulan ve kullanılan `List<int>` (C# dilinde) veya `List(Of Integer)` (Visual Basic) gibi oluşturulmuş bir genel tür, genel tür tanımını içeren derlemede veya tür bağımsız değişkenlerinden birinin tanımını içeren bir derlemede tanımlanmış olarak değerlendirilir. Kullanılan kesin derleme bir uygulama ayrıntısı ve değiştirilebilir.

## <a name="restrictions-on-collectible-assemblies"></a>Toplanabilir derlemelerdeki kısıtlamalar

Aşağıdaki kısıtlamalar toplanabilir derlemeler için geçerlidir:

- **Statik başvurular** Sıradan dinamik bir derlemede bulunan türlerin toplanabilir bir derlemede tanımlanan türlere statik başvuruları olamaz. Örneğin, toplanabilir derlemedeki bir türden devralan sıradan bir tür tanımlarsanız, bir <xref:System.NotSupportedException> özel durum oluşturulur. Toplanabilir bir derlemede bulunan bir tür, başka bir toplanabilir derlemede bulunan bir türe statik başvuruları olabilir, ancak bu, başvurulan derlemenin yaşam süresini başvuran derlemenin ömrüne genişletir.

- **Com birlikte çalışma** Toplanabilir bir derlemede hiçbir COM arabirimi tanımlanamaz ve bir toplanabilir derleme içindeki tür örnekleri COM nesnelerine dönüştürülebilirler. Toplanabilir derlemedeki bir tür, COM çağrılabilir sarmalayıcı (CCW) veya çalışma zamanı çağrılabilir sarmalayıcı (RCW) olarak görev alamaz. Ancak, toplanabilir derlemelerdeki türler COM arabirimlerini uygulayan nesneleri kullanabilir.

- **Platform çağırma** Özniteliği olan Yöntemler, <xref:System.Runtime.InteropServices.DllImportAttribute> toplanabilir bir derlemede bildirildiğinde derlenmeyecektir. <xref:System.Reflection.Emit.OpCodes.Calli?displayProperty=nameWithType> Yönerge, toplanabilir bir derlemede bir türün uygulamasında kullanılamaz ve bu tür türler yönetilmeyen koda sıralanamaz. Bununla birlikte, toplanabilir olmayan bir derlemede belirtilen bir giriş noktasını kullanarak yerel koda çağrı yapabilirsiniz.

- **Sıralama** Toplanabilir derlemelerde tanımlanan nesneler (özellikle de temsilciler) sıralanamaz. Bu, tüm geçici olarak yayınlanan türler için bir kısıtlamadır.

- **Derlemeyi yükleme** Yansıma yayma, toplanabilir derlemeleri yüklemek için desteklenen tek mekanizmadır. Herhangi bir derleme yükleme formu kullanılarak yüklenen derlemeler kaldırılamıyor.

- **Bağlama dayalı nesneler** Bağlam statik değişkenleri desteklenmez. Toplanabilir bir derlemedeki türler genişletilemiyor <xref:System.ContextBoundObject>. Ancak, toplanabilir derlemelerdeki kod, başka bir yerde tanımlanan bağlama dayalı nesneleri kullanabilir.

- **Thread-statik veriler** Thread-static değişkenler desteklenmez.

## <a name="see-also"></a>Ayrıca bkz.

- [Dinamik Yöntemleri ve Derlemeleri Yayma](emitting-dynamic-methods-and-assemblies.md)
