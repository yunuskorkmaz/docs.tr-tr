---
title: "Dinamik tür oluşturma için collectible derlemeler"
description: 
ms.date: 08/29/2017
ms.prod: .net
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reflection, dynamic assembly
- assemblies, collectible
- collectible assemblies, retrieving
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2c9a613f4cc13c3e4189a59ace2e05d01d1bcb4f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="collectible-assemblies-for-dynamic-type-generation"></a>Dinamik tür oluşturma için collectible derlemeler

*Collectible derlemeleri* , oluşturuldukları uygulama etki alanı kaldırılması olmadan kaldırılamıyor dinamik derlemeler. Collectible derleme ve içerdiği türleri tarafından kullanılan tüm yönetilen ve yönetilmeyen bellek istenemiyor. Derleme adı gibi bilgileri iç tablodan kaldırılır.

Eklentiyi etkinleştirmek için <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndCollect?displayProperty=nameWithType> bir dinamik derleme oluşturduğunuzda bayrak. Geçici bir derlemedir (diğer bir deyişle, kaydedilemez) ve açıklanan sınırlamalara tabidir [Collectible derlemeler kısıtlamalar](#restrictions-on-collectible-assemblies) bölümü. Derleme ile ilişkili tüm nesneleri serbest bıraktığınızda ortak dil çalışma zamanı (CLR) collectible derleme otomatik olarak kaldırır. Tüm diğer yönden collectible derlemeler oluşturulur ve diğer dinamik derlemeleri aynı şekilde kullanılır.

## <a name="lifetime-of-collectible-assemblies"></a>Collectible derlemeler ömrü

Collectible derleme ömrü içerdiği türleri ve bu türlerden oluşturulan nesneleri başvuruları varlığını tarafından denetlenir. Bir veya daha fazlasını mevcut olduğu sürece ortak dil çalışma zamanı bütünleştirilmiş kaldırmaz (`T` derlemede tanımlanan herhangi bir tür): 

- Örneği `T`.

- Bir dizi örneği `T`.
 
- Sahip genel bir tür örneği `T` , tür bağımsız değişkenleri biri olarak. Bu genel koleksiyonları içerir `T`, o koleksiyonu boş olsa bile.

- Örneği <xref:System.Type> veya <xref:System.Reflection.Emit.TypeBuilder> temsil eden `T`. 

   > [!IMPORTANT]
   > Derleme bölümlerini temsil eden tüm nesneleri serbest bırakmanız gerekir. <xref:System.Reflection.Emit.ModuleBuilder> Tanımlayan `T` bir başvuru <xref:System.Reflection.Emit.TypeBuilder>ve <xref:System.Reflection.Emit.AssemblyBuilder> nesne başvuru tutar <xref:System.Reflection.Emit.ModuleBuilder>, bu nesnelerin referansları yayımlanması gerekir. Hatta varlığını bir <xref:System.Reflection.Emit.LocalBuilder> veya bir <xref:System.Reflection.Emit.ILGenerator> yapımı içinde kullanılan `T` kaldırılmasını engeller.

- Statik başvuru `T` başka bir dinamik olarak tanımlanan türü tarafından `T1` olan hala erişilebilir kodu yürüterek. Örneğin, `T1` öğesinden türetilen `T`, veya `T` bir yöntem parametresinde tür olabilir `T1`.
 
- A **ByRef** ait statik bir alana `T`.

- A <xref:System.RuntimeTypeHandle>, <xref:System.RuntimeFieldHandle>, veya <xref:System.RuntimeMethodHandle> , başvurduğu `T` veya bir bileşeninin `T`.

- Bir örneği erişmek için doğrudan veya dolaylı olarak kullanılabilecek herhangi bir yansıma nesnenin <xref:System.Type> temsil eden nesnesi `T`. Örneğin, <xref:System.Type> için nesne `T` öğe türü olan bir dizi türünden alınan `T`, veya sahip genel bir tür `T` tür bağımsız değişkeni olarak. 

- Bir yöntem `M` tüm iş parçacığının çağrı yığınında nerede `M` bir yöntemi `T` veya derlemede tanımlanan bir modül düzeyi yöntemi.

- Derlemenin modülde tanımlanmış bir statik yöntem için temsilci.

Yalnızca tek bir tür ya da derlemesindeki bir yöntemi için bu listeden bir öğe varsa, çalışma zamanı derlemesi kaldıramıyor.

> [!NOTE]
> Listedeki tüm öğelerin sonlandırıcılar çalıştırılana kadar çalışma zamanı derlemesi gerçekte kaldırmaz.

İzleme ömrü amaçları doğrultusunda, oluşturulan genel türü gibi `List<int>` (C# ' ta) veya `List(Of Integer)` (Visual Basic'te), oluşturulur ve kullanılan collectible derleme nesil silinmiş kabul derlemede tanımlanmış, Genel içeren tanımı yazın veya bir derleme, tür bağımsız değişkenleri birini tanımını içeren. Kullanılan tam bir uygulama ayrıntılarını ve değiştirmek için konu derlemesidir.
 
## <a name="restrictions-on-collectible-assemblies"></a>Kısıtlamaları collectible derlemeler hakkında

Collectible derlemeler için aşağıdaki kısıtlamalar geçerlidir: 

- **Statik başvuruları**   
  Sıradan dinamik derlemedeki türleri collectible bir derlemede tanımlanan türlerine statik başvuruları sahip olamaz. Örneğin, bir collectible derlemesindeki türünden devralan bir sıradan türü tanımlarsanız bir <xref:System.NotSupportedException> özel durumu oluşur. Collectible derlemesindeki bir türü statik başvuru türü için başka bir collectible derlemede sahip olabilir, ancak bu başvurulan derlemeyi başvuran derlemenin ömrü için ömrü genişletir.

- **COM birlikte çalışma**   
   COM arabirimleri collectible bir derlemede tanımlanmış olması ve COM nesnelerini collectible derleme içinde tür hiçbir örneği dönüştürülebilir. Bir tür collectible derlemesindeki COM aranabilir sarmalayıcısı (saat) veya çalışma zamanı aranabilir sarmalayıcısı (RCW) olarak sunulamıyor. Ancak, collectible derlemelerindeki COM arabirimleri uygulayan nesneler kullanabilirsiniz.

- **Platform çağırma**   
   Sahip yöntemleri <xref:System.Runtime.InteropServices.DllImportAttribute> öznitelik collectible derlemesinde bildirirken derlenmez. <xref:System.Reflection.Emit.OpCodes.Calli?displayProperty=nameWithType> Yönerge collectible derlemesindeki bir türü uyarlamasını kullanılamaz ve bu tür türler yönetilmeyen koda sıralanamaz. Ancak, collectible olmayan bir derlemede bildirilmiş bir giriş noktasını kullanarak yerel kod içine çağırabilirsiniz.
 
- **Hazırlama**   
   Collectible derlemede tanımlanan nesneler (özellikle, temsilcileri) sıralanamaz. Bu, tüm geçici verilmiş türler bir kısıtlamadır.

- **Derleme yükleme**   
   Yansıma yayma collectible derlemeleri yükleme için desteklenen tek mekanizmadır. Herhangi bir biçimde yüklenmesi derlemenin kullanılarak yüklenen derlemeler kaldırılamıyor.
 
- **Bağlam bağımlı nesneler**    
   Statik içerik değişkenleri desteklenmez. Olamaz collectible derlemesindeki türler genişletmek <xref:System.ContextBoundObject>. Ancak, kod collectible derlemelerde tanımlanan bağlam bağımlı nesneleri başka bir yerde kullanabilirsiniz.

- **İş parçacığı statik verileri**       
   İş parçacığı statik değişkenler desteklenmiyor.

## <a name="see-also"></a>Ayrıca bkz.

[Dinamik yöntemleri ve derlemeleri Yayma](emitting-dynamic-methods-and-assemblies.md)
