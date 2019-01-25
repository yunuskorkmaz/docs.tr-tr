---
title: Dinamik tür oluşturma için toplanabilir derlemeler
description: ''
ms.date: 08/29/2017
helpviewer_keywords:
- reflection, dynamic assembly
- assemblies, collectible
- collectible assemblies, retrieving
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b26da264b2da40e19db4bc5e3b3575505f5c979c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54637748"
---
# <a name="collectible-assemblies-for-dynamic-type-generation"></a>Dinamik tür oluşturma için toplanabilir derlemeler

*Toplanabilir derlemeler* içinde oluşturuldukları uygulama etki alanını kaldırmadan kaldırılabilip kaldırılamayacağını dinamik derlemeler. Toplanabilir derleme ve içerdiği türleri tarafından kullanılan tüm yönetilen ve yönetilmeyen bellek istenemiyor. Derleme adı gibi bilgileri, iç tablodan kaldırılır.

Eklentiyi etkinleştirmek için <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndCollect?displayProperty=nameWithType> dinamik bir derleme oluşturduğunuzda bayrak. Geçici bir derlemedir (diğer bir deyişle, kaydedilemez) ve kısıtlamaları bölümünde açıklanan tabidir [toplanabilir derlemeler kısıtlamalar](#restrictions-on-collectible-assemblies) bölümü. Bütünleştirilmiş kod ile ilişkili tüm nesneleri serbest bıraktığınızda, ortak dil çalışma zamanı (CLR) toplanabilir derleme otomatik olarak kaldırır. Diğer tüm yönden toplanabilir derlemeler oluşturulur ve diğer dinamik derlemeler aynı şekilde kullanılır.

## <a name="lifetime-of-collectible-assemblies"></a>Toplanabilir derlemeler ömrü

Toplanabilir derleme ömrünü içerdiği türleri ve bu türlerden oluşturulan nesnelere başvurular varlığını tarafından denetlenir. Bir veya daha fazlasını mevcut olduğu sürece ortak dil çalışma zamanının bir derlemeyi kaldırmaz (`T` derlemede tanımlanan herhangi bir tür): 

- Örneği `T`.

- Bir dizi örneği `T`.
 
- Genel türün örneğini `T` tür bağımsız değişkenlerinden biri olarak. Bu, genel koleksiyonlar içerir `T`bile, boş bir koleksiyondur.

- Örneği <xref:System.Type> veya <xref:System.Reflection.Emit.TypeBuilder> temsil eden `T`. 

   > [!IMPORTANT]
   > Bütünleştirilmiş kod parçalarını temsil eden tüm nesneleri serbest bırakmanız gerekir. <xref:System.Reflection.Emit.ModuleBuilder> Tanımlayan `T` bir başvuru tutar <xref:System.Reflection.Emit.TypeBuilder>ve <xref:System.Reflection.Emit.AssemblyBuilder> nesne başvuru tutar <xref:System.Reflection.Emit.ModuleBuilder>, bu nesnelere başvuruları serbest bırakılması gerekir. Varlığı bile bir <xref:System.Reflection.Emit.LocalBuilder> veya <xref:System.Reflection.Emit.ILGenerator> oluşumunu kullanılan `T` kaldırma engeller.

- Statik başvuru `T` başka bir dinamik olarak tanımlanan bir tür tarafından `T1` olan hala erişilebilir kodu yürüterek. Örneğin, `T1` öğesinden türetilen `T`, veya `T` yöntemi içindeki bir parametre türü olabilir `T1`.
 
- A **ByRef** ait olduğu statik bir alana `T`.

- A <xref:System.RuntimeTypeHandle>, <xref:System.RuntimeFieldHandle>, veya <xref:System.RuntimeMethodHandle> , başvurduğu `T` 'in bir bileşeni için veya `T`.

- Örneği dolaylı olarak kullanılabilecek herhangi bir yansıma nesnenin veya doğrudan erişim <xref:System.Type> temsil eden nesne `T`. Örneğin, <xref:System.Type> nesnesi `T` öğe türüne sahip bir dizi türünden alınan `T`, veya olan bir genel türü `T` tür bağımsız değişkeni olarak. 

- Bir yöntem `M` tüm iş parçacığı çağrı yığınında burada `M` bir yöntemidir `T` veya derlemede tanımlanan bir modül düzeyinde yöntemi.

- Derlemenin bir modülde tanımlanan statik bir yöntem için temsilci.

Yalnızca bu listedeki bir öğe yalnızca bir tür veya derlemedeki bir yöntemi varsa, çalışma zamanı derleme kaldıramıyor.

> [!NOTE]
> Listedeki tüm öğeler için sonlandırıcılar çalıştırılana kadar çalışma zamanı derleme gerçekten kaldırmaz.

İzleme ömrü amaçları doğrultusunda oluşturulmuş bir genel türü gibi `List<int>` (içinde C#) veya `List(Of Integer)` (Visual Basic'te), oluşturulur ve kullanılan toplanabilir derleme nesil olduğunu kabul derlemede tanımlanmış genel tür tanımı içeren veya bir derlemede, tür bağımsız değişkenlerinden biri tanımını içerir. Kullanılan tam bir uygulama ayrıntısı ve değiştirmek için konu derlemesidir.
 
## <a name="restrictions-on-collectible-assemblies"></a>Toplanabilir derlemeler kısıtlamaları

Toplanabilir derlemeler için aşağıdaki kısıtlamalar uygulanır: 

- **Statik başvuruları**   
  Sıradan dinamik derlemedeki türleri toplanabilir derlemesinde tanımlanan türleri statik başvuruları olamaz. Toplanabilir derlemedeki bir türe devralan bir sıradan tür tanımlarsanız, örneğin, bir <xref:System.NotSupportedException> özel durumu oluşturulur. Toplanabilir derlemedeki bir türe toplanabilir başka bir derlemede statik başvuru türüne sahip olabilir, ancak bu başvurulan derlemeyi başvuran derlemenin ömrü ömrünü genişletir.

- **COM birlikte çalışma**   
   COM arabirimlerine toplanabilir bir derleme içinde tanımlanabilir ve hiçbir örneği toplanabilir derlemedeki türleri COM nesnelerine dönüştürülebilir. Toplanabilir derlemedeki bir türe COM çağrılabilir sarmalayıcı (CCW) veya çalışma zamanı çağrılabilir sarmalayıcı (RCW) olarak hizmet veremez. Ancak, toplanabilir bütünleştirilmiş kodlar içindeki türleri COM arabirimleri uygulayan nesneler kullanabilirsiniz.

- **Platform çağırma**   
   Sahip yöntemleri <xref:System.Runtime.InteropServices.DllImportAttribute> özniteliği toplanabilir bir derleme içinde bildirildiğinde derlenmez. <xref:System.Reflection.Emit.OpCodes.Calli?displayProperty=nameWithType> Yönerge toplanabilir derlemedeki bir türe uygulamasında kullanılamaz ve bu türler, yönetilmeyen koda sıralanamaz. Ancak, yerel kod içine toplanabilir olmayan bir derlemede bildirilmiş bir giriş noktası kullanarak çağırabilirsiniz.
 
- **Hazırlama**   
   Toplanabilir derlemeler içinde tanımlanan nesneler (özellikle, temsilciler) sıralanamaz. Tüm geçici yayılan türlerinde bir sınırlama budur.

- **Derleme yükleme**   
   Yansıma yayma toplanabilir derlemeler yüklemek için desteklenen tek mekanizmadır. Derleme yükleme, herhangi bir biçimde kullanarak yüklenen derlemeler kaldırılamıyor.
 
- **Bağlam bağımlı nesneler**    
   Statik bağlam değişkenleri desteklenmez. Toplanabilir derlemedeki türleri genişletemez <xref:System.ContextBoundObject>. Ancak, toplanabilir bütünleştirilmiş kod başka bir yerde tanımlanmış bağlam bağımlı nesneler kullanabilirsiniz.

- **İş parçacığı statik veri**       
   İş parçacığı statik değişkenler desteklenmez.

## <a name="see-also"></a>Ayrıca bkz.

- [Dinamik Yöntemleri ve Derlemeleri Yayma](emitting-dynamic-methods-and-assemblies.md)
