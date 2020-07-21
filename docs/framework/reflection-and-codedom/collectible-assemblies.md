---
title: Dinamik tür oluşturma için toplanabilir derlemeler
description: .NET ' te dinamik tür oluşturma için toplanabilir derlemeler ile çalışmaya başlayın. Toplanabilir derleme yaşam süreleri ve kısıtlamaları hakkında bilgi edinin.
ms.date: 08/29/2017
helpviewer_keywords:
- reflection, dynamic assembly
- assemblies, collectible
- collectible assemblies, retrieving
ms.openlocfilehash: 4981b93dbd49a6da96740bebed0f2ed7b89036c8
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475131"
---
# <a name="collectible-assemblies-for-dynamic-type-generation"></a>Dinamik tür oluşturma için toplanabilir derlemeler

*Toplanabilir derlemeler* , oluşturuldukları uygulama etki alanının kaldırılması gerekmeden bellekten kaldırılabilen dinamik derlemelerdir. Bir toplanabilir derleme tarafından kullanılan tüm yönetilen ve yönetilmeyen bellek ve içerdiği türler geri kazanılır. Derleme adı gibi bilgiler iç tablolardan kaldırılır.

Kaldırmayı etkinleştirmek için, <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndCollect?displayProperty=nameWithType> dinamik bir derleme oluştururken bayrağını kullanın. Derleme geçicidir (diğer bir deyişle, kaydedilemez) ve [toplanabilir derlemelerde kısıtlamalar](#restrictions-on-collectible-assemblies) bölümünde açıklanan sınırlamalara tabidir. Ortak dil çalışma zamanı (CLR), derlemeyle ilişkili tüm nesneleri serbest bırakırsanız, toplanabilir bir derlemeyi otomatik olarak kaldırır. Diğer tüm yönden, toplanabilir derlemeler diğer dinamik Derlemelerle aynı şekilde oluşturulur ve kullanılır.

## <a name="lifetime-of-collectible-assemblies"></a>Toplanabilir derlemelerin ömrü

Toplanabilir bir derlemenin ömrü, içerdiği türlere yapılan başvuruların ve bu türlerden oluşturulan nesnelerin varlığı tarafından denetlenir. Ortak dil çalışma zamanı, aşağıdakilerden biri veya daha fazlası mevcut olduğu sürece bir derlemeyi kaldırmaz ( `T` derlemede tanımlı herhangi bir tür):

- `T` öğesinin bir örneği.

- Bir dizisinin örneği `T` .

- Tür bağımsız değişkenlerinden biri olan bir genel türün örneği `T` . Bu `T` , koleksiyon boş olsa bile genel koleksiyonlarını içerir.

- Öğesini <xref:System.Type> <xref:System.Reflection.Emit.TypeBuilder> temsil eden bir örneği `T` .

   > [!IMPORTANT]
   > Derlemenin parçalarını temsil eden tüm nesneleri serbest bırakmanız gerekir. <xref:System.Reflection.Emit.ModuleBuilder>Tanımlar `T` öğesine bir başvuru tutar <xref:System.Reflection.Emit.TypeBuilder> ve <xref:System.Reflection.Emit.AssemblyBuilder> nesnesi öğesine bir başvuru tutar, <xref:System.Reflection.Emit.ModuleBuilder> Bu nedenle bu nesnelere yapılan başvuruların serbest bırakılması gerekir. Bir <xref:System.Reflection.Emit.LocalBuilder> veya <xref:System.Reflection.Emit.ILGenerator> yapımını oluşturma sırasında kullanılması bile, `T` kaldırmayı engeller.

- `T` `T1` Kod yürütülerek hala erişilebilir olan, dinamik olarak tanımlanmış başka bir tür tarafından statik başvuru. Örneğin, `T1` öğesinden türetilebilir `T` veya `T` bir yöntemindeki parametre türü olabilir `T1` .

- Öğesine ait olan statik bir alana **ByRef** `T` .

- Bir <xref:System.RuntimeTypeHandle> , veya öğesine başvuran bir, <xref:System.RuntimeFieldHandle> veya bir <xref:System.RuntimeMethodHandle> `T` bileşeni `T` .

- Dolaylı olarak veya ' i temsil eden nesneye erişmek için doğrudan kullanılabilen herhangi bir yansıma nesnesinin örneği <xref:System.Type> `T` . Örneğin, nesnesi, <xref:System.Type> `T` öğe türü olan bir dizi türünden `T` veya tür bağımsız değişkeni olan genel bir türden elde edilebilir `T` .

- `M`Herhangi bir iş parçacığının çağrı yığınında bir yöntem, `M` `T` veya derlemede tanımlanan modül düzeyi bir yöntem.

- Derlemenin modülünde tanımlanan statik metoda bir temsilci.

Bu listedeki yalnızca bir öğe, derlemede yalnızca bir tür veya bir yöntem için mevcutsa, çalışma zamanı derlemeyi kaldıramıyor.

> [!NOTE]
> Çalışma zamanı, listedeki tüm öğeler için sonlandırıcılar çalıştırılıncaya kadar derlemeyi gerçekten kaldırmaz.

Kullanım ömrü açısından, `List<int>` bir toplanabilir derleme oluşturmak için oluşturulan ve kullanılan (C# dilinde) veya (Visual Basic) gibi oluşturulmuş bir genel tür, `List(Of Integer)` genel tür tanımını içeren derlemede veya tür bağımsız değişkenlerinden birinin tanımını içeren bir derlemede tanımlanmış olarak değerlendirilir. Kullanılan kesin derleme bir uygulama ayrıntısı ve değiştirilebilir.

## <a name="restrictions-on-collectible-assemblies"></a>Toplanabilir derlemelerdeki kısıtlamalar

Aşağıdaki kısıtlamalar toplanabilir derlemeler için geçerlidir:

- **Statik başvurular** Sıradan dinamik bir derlemede bulunan türlerin toplanabilir bir derlemede tanımlanan türlere statik başvuruları olamaz. Örneğin, toplanabilir derlemedeki bir türden devralan sıradan bir tür tanımlarsanız, bir <xref:System.NotSupportedException> özel durum oluşturulur. Toplanabilir bir derlemede bulunan bir tür, başka bir toplanabilir derlemede bulunan bir türe statik başvuruları olabilir, ancak bu, başvurulan derlemenin yaşam süresini başvuran derlemenin ömrüne genişletir.

- **Com birlikte çalışma** Toplanabilir bir derlemede hiçbir COM arabirimi tanımlanamaz ve bir toplanabilir derleme içindeki tür örnekleri COM nesnelerine dönüştürülebilirler. Toplanabilir derlemedeki bir tür, COM çağrılabilir sarmalayıcı (CCW) veya çalışma zamanı çağrılabilir sarmalayıcı (RCW) olarak görev alamaz. Ancak, toplanabilir derlemelerdeki türler COM arabirimlerini uygulayan nesneleri kullanabilir.

- **Platform çağırma** Özniteliği olan Yöntemler, <xref:System.Runtime.InteropServices.DllImportAttribute> toplanabilir bir derlemede bildirildiğinde derlenmeyecektir. <xref:System.Reflection.Emit.OpCodes.Calli?displayProperty=nameWithType>Yönerge, toplanabilir bir derlemede bir türün uygulamasında kullanılamaz ve bu tür türler yönetilmeyen koda sıralanamaz. Bununla birlikte, toplanabilir olmayan bir derlemede belirtilen bir giriş noktasını kullanarak yerel koda çağrı yapabilirsiniz.

- **Sıralama** Toplanabilir derlemelerde tanımlanan nesneler (özellikle de temsilciler) sıralanamaz. Bu, tüm geçici olarak yayınlanan türler için bir kısıtlamadır.

- **Derlemeyi yükleme** Yansıma yayma, toplanabilir derlemeleri yüklemek için desteklenen tek mekanizmadır. Herhangi bir derleme yükleme formu kullanılarak yüklenen derlemeler kaldırılamıyor.

- **Bağlama dayalı nesneler** Bağlam statik değişkenleri desteklenmez. Toplanabilir bir derlemedeki türler genişletilemiyor <xref:System.ContextBoundObject> . Ancak, toplanabilir derlemelerdeki kod, başka bir yerde tanımlanan bağlama dayalı nesneleri kullanabilir.

- **Thread-statik veriler** Thread-static değişkenler desteklenmez.

## <a name="see-also"></a>Ayrıca bkz.

- [Dinamik Yöntemleri ve Derlemeleri Yayma](emitting-dynamic-methods-and-assemblies.md)
