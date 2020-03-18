---
title: Yönetilen montaj yükleme algoritması - .NET Core
description: .NET Core'da yönetilen montaj yükleme algoritmasının ayrıntılarının açıklaması
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 312a320676be6eb453697e0704ab771a6707618b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73973507"
---
# <a name="managed-assembly-loading-algorithm"></a>Yönetilen montaj yükleme algoritması

Yönetilen derlemeler bulunur ve çeşitli aşamaları içeren bir algoritma ile yüklenir.

Uydu derlemeleri ve `WinRT` derlemeler hariç tüm yönetilen derlemeler aynı algoritmayı kullanır.

## <a name="when-are-managed-assemblies-loaded"></a>Yönetilen derlemeler ne zaman yüklenir?

Yönetilen montaj yükünü tetikleyen en yaygın mekanizma statik montaj başvurusudur. Bu başvurular, kod başka bir derlemede tanımlanan bir tür kullandığında derleyici tarafından eklenir. Bu derlemeler çalışma`load-by-name`zamanının gerektirdiği şekilde ( ) yüklenir.

Belirli API'lerin doğrudan kullanımı da yükleri tetikler:

|API  |Açıklama  |`Active` <xref:System.Runtime.Loader.AssemblyLoadContext> |
|---------|---------|---------|
|<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyName%2A?displayProperty=nameWithType>|`Load-by-name`|[Bu](../../csharp/language-reference/keywords/this.md) örnek.|
|<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyPath%2A?displayProperty=nameWithType><p><xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromNativeImagePath%2A?displayProperty=nameWithType>|Yoldan yükleyin.|[Bu](../../csharp/language-reference/keywords/this.md) örnek.|
<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromStream%2A?displayProperty=nameWithType>|Nesneden yük.|[Bu](../../csharp/language-reference/keywords/this.md) örnek.|
|<xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType>|Yeni <xref:System.Runtime.Loader.AssemblyLoadContext> bir örnekte yoldan yükleme|Yeni <xref:System.Runtime.Loader.AssemblyLoadContext> örnek.|
<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>|Örnekte yoldan <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> yük.<p>Bir <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving> işleyici <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>ekler. İşleyici, derlemenin bağımlılıklarını dizininden yükler.|<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> örneği.|
|<xref:System.Reflection.Assembly.Load(System.Reflection.AssemblyName)?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.Load(System.String)?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>|`Load-by-name`.|Arayan kişiden çıkarılan.<p>Yöntemleri <xref:System.Runtime.Loader.AssemblyLoadContext> tercih edin.|
|<xref:System.Reflection.Assembly.Load(System.Byte[])?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.Load(System.Byte[],System.Byte[])?displayProperty=nameWithType>|Yeni <xref:System.Runtime.Loader.AssemblyLoadContext> bir örnekte nesneden yük.|Yeni <xref:System.Runtime.Loader.AssemblyLoadContext> örnek.|
<xref:System.Type.GetType(System.String)?displayProperty=nameWithType><p><xref:System.Type.GetType(System.String,System.Boolean)?displayProperty=nameWithType><p><xref:System.Type.GetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType>|`Load-by-name`.|Arayan kişiden çıkarılan.<p>Bağımsız değişkenli yöntemleri tercih edin. <xref:System.Type.GetType%2A?displayProperty=nameWithType> `assemblyResolver`|
<xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>|Tür, `name` bir derleme nitelikli genel `Load-by-name`türü açıklarsa, bir .|Arayan kişiden çıkarılan.<p>Montaj <xref:System.Type.GetType%2A?displayProperty=nameWithType> nitelikli tür adlarını kullanırken tercih edin.|
<xref:System.Activator.CreateInstance(System.String,System.String)?displayProperty=nameWithType><p><xref:System.Activator.CreateInstance(System.String,System.String,System.Object[])?displayProperty=nameWithType><p><xref:System.Activator.CreateInstance(System.String,System.String,System.Boolean,System.Reflection.BindingFlags,System.Reflection.Binder,System.Object[],System.Globalization.CultureInfo,System.Object[])?displayProperty=nameWithType>|`Load-by-name`.|Arayan kişiden çıkarılan.<p>Argüman alma yöntemlerini tercih edin. <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> <xref:System.Type>|

## <a name="algorithm"></a>Algoritma

Aşağıdaki algoritma, çalışma zamanının yönetilen bir derlemeyi nasıl yükletildiğini açıklar.

1. Belirleyin. `active` <xref:System.Runtime.Loader.AssemblyLoadContext>

    - Statik bir derleme başvurusu `active` <xref:System.Runtime.Loader.AssemblyLoadContext> için, başvuru yapan derlemeyi yükleyen örnektir.
    - Tercih edilen API'ler `active` <xref:System.Runtime.Loader.AssemblyLoadContext> açık olun.
    - Diğer API'ler `active` <xref:System.Runtime.Loader.AssemblyLoadContext>çıkarsA. Bu API'ler <xref:System.Runtime.Loader.AssemblyLoadContext.CurrentContextualReflectionContext?displayProperty=nameWithType> için özellik kullanılır. Değeri ise, `null`çıkarılan <xref:System.Runtime.Loader.AssemblyLoadContext> örnek kullanılır.
    - Yukarıdaki tabloya bakın.

2. Yöntemler `Load-by-name` için, etkin <xref:System.Runtime.Loader.AssemblyLoadContext> yükler montaj. Öncelik sırasına göre:
    - Onun `cache-by-name`kontrol .

    - <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> İşlevi çağırıyor.

    - Örneklerin <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> önbelleğini denetleme ve [yönetilen derleme varsayılan sondalama](default-probing.md#managed-assembly-default-probing) mantığını çalıştırma.

    - Etkin <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> AssemblyLoadContext için etkinliği yükseltme.

    - Olayı <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> yükseltiyor.

3. Diğer yük türleri için, `active` <xref:System.Runtime.Loader.AssemblyLoadContext> montaj yükler. Öncelik sırasına göre:
    - Onun `cache-by-name`kontrol .

    - Belirtilen yoldan veya ham montaj nesnesinden yükleme.

4. Her iki durumda da, bir derleme yeni yüklenirse, aşağıdakileri
   - Olay <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> yükseltilir.
   - Derleme <xref:System.Runtime.Loader.AssemblyLoadContext> örneğine bir başvuru `cache-by-name`eklenir.

5. Derleme bulunursa, `active` <xref:System.Runtime.Loader.AssemblyLoadContext> bir başvuru, gerektiğinde örneğin `cache-by-name`.
