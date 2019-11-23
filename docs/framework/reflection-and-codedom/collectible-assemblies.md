---
title: Dinamik tür oluşturma için toplanabilir derlemeler
description: ''
ms.date: 08/29/2017
helpviewer_keywords:
- reflection, dynamic assembly
- assemblies, collectible
- collectible assemblies, retrieving
ms.openlocfilehash: 85eacff22cf2e1c0b8c3d74a4971de035dfafbe4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130287"
---
# <a name="collectible-assemblies-for-dynamic-type-generation"></a>Dinamik tür oluşturma için toplanabilir derlemeler

*Toplanabilir derlemeler* , oluşturuldukları uygulama etki alanının kaldırılması gerekmeden bellekten kaldırılabilen dinamik derlemelerdir. Bir toplanabilir derleme tarafından kullanılan tüm yönetilen ve yönetilmeyen bellek ve içerdiği türler geri kazanılır. Derleme adı gibi bilgiler iç tablolardan kaldırılır.

Kaldırmayı etkinleştirmek için, dinamik bir derleme oluştururken <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndCollect?displayProperty=nameWithType> bayrağını kullanın. Derleme geçicidir (diğer bir deyişle, kaydedilemez) ve [toplanabilir derlemelerde kısıtlamalar](#restrictions-on-collectible-assemblies) bölümünde açıklanan sınırlamalara tabidir. Ortak dil çalışma zamanı (CLR), derlemeyle ilişkili tüm nesneleri serbest bırakırsanız, toplanabilir bir derlemeyi otomatik olarak kaldırır. Diğer tüm yönden, toplanabilir derlemeler diğer dinamik Derlemelerle aynı şekilde oluşturulur ve kullanılır.

## <a name="lifetime-of-collectible-assemblies"></a>Toplanabilir derlemelerin ömrü

Toplanabilir bir derlemenin ömrü, içerdiği türlere yapılan başvuruların ve bu türlerden oluşturulan nesnelerin varlığı tarafından denetlenir. Ortak dil çalışma zamanı, aşağıdakilerden biri veya daha fazlası mevcut olduğu sürece bir derlemeyi kaldırmaz (`T` derlemede tanımlı herhangi bir türdür): 

- `T`örneği.

- Bir dizi `T`örneği.
 
- Tür bağımsız değişkenlerinden biri olarak `T` olan bir genel türün örneği. Bu, söz konusu koleksiyon boş olsa bile, `T`genel koleksiyonlarını içerir.

- `T`temsil eden bir <xref:System.Type> veya <xref:System.Reflection.Emit.TypeBuilder> örneği. 

   > [!IMPORTANT]
   > Derlemenin parçalarını temsil eden tüm nesneleri serbest bırakmanız gerekir. `T` tanımlayan <xref:System.Reflection.Emit.ModuleBuilder> <xref:System.Reflection.Emit.TypeBuilder>bir başvuru tutar ve <xref:System.Reflection.Emit.AssemblyBuilder> nesnesi <xref:System.Reflection.Emit.ModuleBuilder>bir başvuru tutar, bu nedenle bu nesnelere yapılan başvuruların serbest bırakılması gerekir. Bir <xref:System.Reflection.Emit.LocalBuilder> veya `T` oluşturulması sırasında kullanılan bir <xref:System.Reflection.Emit.ILGenerator> bile kaldırılması önlenir.

- Kod yürütülerek hala erişilebilir olan başka bir dinamik olarak tanımlanmış tür `T1` tarafından `T` statik bir başvuru. Örneğin, `T1` `T`türetilebilir veya `T` `T1`bir yöntemde parametre türü olabilir.
 
- `T`ait bir statik alana **ByRef** .

- `T` veya `T`bileşenine başvuran bir <xref:System.RuntimeTypeHandle>, <xref:System.RuntimeFieldHandle>veya <xref:System.RuntimeMethodHandle>.

- `T`temsil eden <xref:System.Type> nesnesine dolaylı olarak veya doğrudan erişim için kullanılabilecek herhangi bir yansıma nesnesinin örneği. Örneğin, `T` <xref:System.Type> nesnesi, öğe türü `T`olan bir dizi türünden veya tür bağımsız değişkeni olarak `T` olan genel bir türden elde edilebilir. 

- Bir yöntem, her bir iş parçacığının çağrı yığınında `M`; burada `M`, derlemede tanımlanan bir `T` veya modül düzeyi yöntemi olan bir yöntemdir.

- Derlemenin modülünde tanımlanan statik metoda bir temsilci.

Bu listedeki yalnızca bir öğe, derlemede yalnızca bir tür veya bir yöntem için mevcutsa, çalışma zamanı derlemeyi kaldıramıyor.

> [!NOTE]
> Çalışma zamanı, listedeki tüm öğeler için sonlandırıcılar çalıştırılıncaya kadar derlemeyi gerçekten kaldırmaz.

Kullanım ömrü açısından, toplanabilir bir derlemenin oluşturulmasında oluşturulan ve kullanılan `List<int>` (ın C#) veya `List(Of Integer)` (Visual Basic) gibi oluşturulmuş bir genel tür, genel tür tanımını içeren derlemede veya tür bağımsız değişkenlerinden birinin tanımını içeren bir derlemede tanımlanmış olarak değerlendirilir. Kullanılan kesin derleme bir uygulama ayrıntısı ve değiştirilebilir.
 
## <a name="restrictions-on-collectible-assemblies"></a>Toplanabilir derlemelerdeki kısıtlamalar

Aşağıdaki kısıtlamalar toplanabilir derlemeler için geçerlidir: 

- **Statik başvurular**   
  Sıradan dinamik bir derlemede bulunan türlerin toplanabilir bir derlemede tanımlanan türlere statik başvuruları olamaz. Örneğin, toplanabilir derlemedeki bir türden devralan sıradan bir tür tanımlarsanız, <xref:System.NotSupportedException> bir özel durum oluşturulur. Toplanabilir bir derlemede bulunan bir tür, başka bir toplanabilir derlemede bulunan bir türe statik başvuruları olabilir, ancak bu, başvurulan derlemenin yaşam süresini başvuran derlemenin ömrüne genişletir.

- **Com birlikte çalışabilirlik**   
   Toplanabilir bir derlemede hiçbir COM arabirimi tanımlanamaz ve bir toplanabilir derleme içindeki tür örnekleri COM nesnelerine dönüştürülebilirler. Toplanabilir derlemedeki bir tür, COM çağrılabilir sarmalayıcı (CCW) veya çalışma zamanı çağrılabilir sarmalayıcı (RCW) olarak görev alamaz. Ancak, toplanabilir derlemelerdeki türler COM arabirimlerini uygulayan nesneleri kullanabilir.

- **Platform çağırma**   
   <xref:System.Runtime.InteropServices.DllImportAttribute> özniteliğine sahip Yöntemler, toplanabilir bir derlemede bildirildiğinde derlenmeyecektir. <xref:System.Reflection.Emit.OpCodes.Calli?displayProperty=nameWithType> yönergesi, toplanabilir bir derlemede bulunan bir türün uygulamasında kullanılamaz ve bu tür türler yönetilmeyen koda sıralanamaz. Bununla birlikte, toplanabilir olmayan bir derlemede belirtilen bir giriş noktasını kullanarak yerel koda çağrı yapabilirsiniz.
 
-   **sıralaması**  
   Toplanabilir derlemelerde tanımlanan nesneler (özellikle de temsilciler) sıralanamaz. Bu, tüm geçici olarak yayınlanan türler için bir kısıtlamadır.

- **Derleme yükleme**   
   Yansıma yayma, toplanabilir derlemeleri yüklemek için desteklenen tek mekanizmadır. Herhangi bir derleme yükleme formu kullanılarak yüklenen derlemeler kaldırılamıyor.
 
- **Bağlama dayalı nesneler**    
   Bağlam statik değişkenleri desteklenmez. Toplanabilir derlemedeki türler <xref:System.ContextBoundObject>genişletilemiyor. Ancak, toplanabilir derlemelerdeki kod, başka bir yerde tanımlanan bağlama dayalı nesneleri kullanabilir.

- **Iş parçacığı statik veri**       
   Thread-static değişkenler desteklenmez.

## <a name="see-also"></a>Ayrıca bkz.

- [Dinamik Yöntemleri ve Derlemeleri Yayma](emitting-dynamic-methods-and-assemblies.md)
