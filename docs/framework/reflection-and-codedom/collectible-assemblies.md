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

*Tahsil edilebilir derlemeler,* oluşturuldukları uygulama etki alanını boşaltmadan boşaltılabilen dinamik derlemelerdir. Tahsil edilebilir bir derleme tarafından kullanılan tüm yönetilen ve yönetilmeyen bellek ve içerdiği türleri geri alınabilir. Derleme adı gibi bilgiler iç tablolardan kaldırılır.

Boşaltmayı etkinleştirmek için <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndCollect?displayProperty=nameWithType> dinamik bir derleme oluştururken bayrağı kullanın. Derleme geçicidir (yani kaydedilemez) ve [Tahsil Edilebilir Montajlar](#restrictions-on-collectible-assemblies) Hakkındaki Kısıtlamalar bölümünde açıklanan sınırlamalara tabidir. Ortak dil çalışma süresi (CLR), derlemeyle ilişkili tüm nesneleri serbest bırakdığınızda otomatik olarak tahsil edilebilir bir derlemeyi boşaltır. Diğer tüm açılardan, tahsil edilebilir derlemeler oluşturulur ve diğer dinamik derlemeler gibi aynı şekilde kullanılır.

## <a name="lifetime-of-collectible-assemblies"></a>Tahsil montajlarının ömrü

Bir tahsil derlemesinin ömrü, içerdiği türlere ve bu türlerden oluşturulan nesnelere yapılan başvuruların varlığıyla denetlenir. Ortak dil çalışma süresi, aşağıdakilerden biri veya birkaçı var olduğu`T` sürece (derlemede tanımlanan herhangi bir türdür) bir derlemeyi boşaltmaz:

- `T` öğesinin bir örneği.

- Bir dizi `T`bir örnek .

- Kendi tür bağımsız değişkenlerinden `T` biri olarak olan genel bir tür örneği. Bu, bu koleksiyon `T`boş olsa bile, genel koleksiyonlarını içerir.

- Bir örneği <xref:System.Type> <xref:System.Reflection.Emit.TypeBuilder> veya `T`temsil eder.

   > [!IMPORTANT]
   > Derlemenin parçalarını temsil eden tüm nesneleri serbest bırakmanız gerekir. <xref:System.Reflection.Emit.ModuleBuilder> `T` Bu tanımlar <xref:System.Reflection.Emit.TypeBuilder>, ve <xref:System.Reflection.Emit.AssemblyBuilder> nesne bir referans tutar <xref:System.Reflection.Emit.ModuleBuilder>, bu nedenle bu nesnelere başvurular serbest bırakılmalıdır. Hatta yapımında kullanılan <xref:System.Reflection.Emit.LocalBuilder> bir <xref:System.Reflection.Emit.ILGenerator> veya bir `T` varlığı boşaltma önler.

- Kodu yürüterek `T` hala erişilebilen `T1` başka bir dinamik olarak tanımlanmış türtarafından statik bir başvuru. Örneğin, `T1` bir yöntemdeki `T`parametre türünden türetilebilir veya `T` parametre türü `T1`olabilir.

- A **ByRef'e** ait statik `T`bir alana.

- A <xref:System.RuntimeTypeHandle> <xref:System.RuntimeFieldHandle>, <xref:System.RuntimeMethodHandle> veya bir `T` bileşenine veya `T`bileşenine atıfta bulunan.

- Temsil eden <xref:System.Type> nesneye erişmek için dolaylı veya doğrudan kullanılabilecek herhangi `T`bir yansıtma nesnesinin bir örneği. Örneğin, <xref:System.Type> öğe `T` türü `T`olan bir dizi türünden veya tür bağımsız değişkeni `T` olan genel bir türden elde edilebilir.

- Herhangi `M` bir iş parçacığının çağrı `M` yığınındaki bir `T` yöntem, montajda tanımlanan bir yöntem veya modül düzeyinde bir yöntemdir.

- Derlemenin bir modülünde tanımlanan statik bir yöntemin temsilcisi.

Bu listeden yalnızca bir öğe derlemede yalnızca bir tür veya bir yöntem için varsa, çalışma süresi derlemeyi boşaltamaz.

> [!NOTE]
> Sonlandırıcılar listedeki tüm öğeler için çalışana kadar çalışma süresi aslında derlemeyi boşaltmaz.

Ömür boyu izleme amacıyla, (C#' da) `List<int>` veya `List(Of Integer)` (Visual Basic'te) olarak oluşturulan ve bir tahsil edilebilir derlemenin oluşumunda kullanılan genel bir tür, genel tür tanımını içeren derlemede veya tür bağımsız değişkenlerinden birinin tanımını içeren bir derlemede tanımlanmış olarak kabul edilir. Kullanılan tam derleme bir uygulama ayrıntısı ve değiştirebilirsiniz.

## <a name="restrictions-on-collectible-assemblies"></a>Tahsil edilebilir montajlarla ilgili kısıtlamalar

Aşağıdaki kısıtlamalar tahsil montajları için geçerlidir:

- **Statik referanslar** Olağan dinamik derlemedeki türlerin, tahsil edilebilir bir derlemede tanımlanan türlere statik başvuruları olamaz. Örneğin, tahsil edilebilir bir derlemedeki bir türden devralınan sıradan <xref:System.NotSupportedException> bir tür tanımlarsanız, bir özel durum atılır. Tahsil edilebilir bir derlemedeki bir tür, başka bir tahsil edilebilir derlemedeki bir türe statik başvurulara sahip olabilir, ancak bu, başvurulan derlemenin kullanım ömrünü başvuru derlemesinin ömrüne kadar uzatır.

- **COM interop** Tahsil edilebilir bir derleme içinde com arabirimleri tanımlanamaz ve tahsil edilebilir bir derlemedeki türlerin hiçbir örneği COM nesnelerine dönüştürülemez. Tahsil edilebilir bir derlemedeki bir tür, COM çağrılabilir sarıcı (CCW) veya çalışma zamanı çağrılabilir sarıcı (RCW) olarak hizmet veremez. Ancak, tahsil edilebilir derlemelerde türleri COM arabirimleri uygulayan nesneleri kullanabilirsiniz.

- **Platform çağırma** Öznitelik sahibi <xref:System.Runtime.InteropServices.DllImportAttribute> yöntemler, tahsil edilebilir bir derlemede beyan edildiğinde derlenecektir. Yönerge, <xref:System.Reflection.Emit.OpCodes.Calli?displayProperty=nameWithType> tahsil edilebilir bir derlemede bir türün uygulanmasında kullanılamaz ve bu tür türler yönetilmeyen koda dönüştürülemez. Ancak, tahsil edilemeyen bir derlemede bildirilen bir giriş noktası kullanarak yerel koda çağrı yapabilirsiniz.

- **Mareşallik** Tahsil meclislerinde tanımlanan nesneler (özellikle, temsilciler) marshaled olamaz. Bu, tüm geçici yayılan türleri için bir kısıtlamadır.

- **Montaj yüklemesi** Yansıma yayı, tahsil edilebilir montajların yüklenmesi için desteklenen tek mekanizmadır. Başka bir montaj yükleme biçimi kullanılarak yüklenen derlemeler boşaltılamaz.

- **İçeribağlı nesneler** Bağlam statik değişkenler desteklenmez. Tahsil edilebilir bir derlemedeki <xref:System.ContextBoundObject>türler uzatılamaz. Ancak, tahsil edilebilir derlemelerde kod başka bir yerde tanımlanan içeriğe bağlı nesneleri kullanabilirsiniz.

- **İş parçacığı statik verileri** İş parçacığı statik değişkenler desteklenmez.

## <a name="see-also"></a>Ayrıca bkz.

- [Dinamik Yöntemleri ve Derlemeleri Yayma](emitting-dynamic-methods-and-assemblies.md)
