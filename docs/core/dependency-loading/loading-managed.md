---
title: Yönetilen derleme yükleme algoritması-.NET Core
description: .NET Core 'da yönetilen derleme yükleme algoritması ayrıntılarının açıklaması
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: bf95cbd0eebed064f0198ae9b0f7a4288a938f8a
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105367"
---
# <a name="managed-assembly-loading-algorithm"></a>Yönetilen derleme yükleme algoritması

Yönetilen derlemeler, çeşitli aşamalar içeren bir algoritmayla bulunur ve yüklenir.

Uydu derlemeleri ve `WinRT` derlemeler hariç tüm yönetilen derlemeler aynı algoritmayı kullanır.

## <a name="when-are-managed-assemblies-loaded"></a>Yönetilen derlemeler ne zaman yüklenir?

Yönetilen bir derleme yükünü tetiklemek için en yaygın mekanizma statik bir derleme başvurusudur. Bu başvurular, kod başka bir derlemede tanımlı bir tür kullandığında derleyici tarafından eklenir. Bu derlemeler çalışma zamanının gerektirdiği`load-by-name`şekilde yüklenir ().

Belirli API 'lerin doğrudan kullanımı da yükleri tetikleyecektir:

|API  |Açıklama  |`Active`<xref:System.Runtime.Loader.AssemblyLoadContext> |
|---------|---------|---------|
|<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyName%2A?displayProperty=nameWithType>|`Load-by-name`|[Bu](../../csharp/language-reference/keywords/this.md) örnek.|
|<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyPath%2A?displayProperty=nameWithType><p><xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromNativeImagePath%2A?displayProperty=nameWithType>|Yoldan yükle.|[Bu](../../csharp/language-reference/keywords/this.md) örnek.|
<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromStream%2A?displayProperty=nameWithType>|Nesnesinden yükle.|[Bu](../../csharp/language-reference/keywords/this.md) örnek.|
|<xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType>|Yeni <xref:System.Runtime.Loader.AssemblyLoadContext> bir örnekteki yoldan yükleme|Yeni <xref:System.Runtime.Loader.AssemblyLoadContext> örnek.|
<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>|<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> Örnekteki yoldan yükleyin.<p><xref:System.Runtime.Loader.AssemblyLoadContext.Resolving> Öğesine<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>bir işleyici ekler. İşleyici, derlemenin bağımlılıklarını dizinden yükleyecek.|<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> Örnek.|
|<xref:System.Reflection.Assembly.Load(System.Reflection.AssemblyName)?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.Load(System.String)?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>|`Load-by-name`.|Çağırandan çıkarsandı.<p>Yöntemleri <xref:System.Runtime.Loader.AssemblyLoadContext> tercih edin.|
|<xref:System.Reflection.Assembly.Load(System.Byte[])?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.Load(System.Byte[],System.Byte[])?displayProperty=nameWithType>|Nesnesinden yükle.|Çağırandan çıkarsandı.<p>Yöntemleri <xref:System.Runtime.Loader.AssemblyLoadContext> tercih edin.|
<xref:System.Type.GetType(System.String)?displayProperty=nameWithType><p><xref:System.Type.GetType(System.String,System.Boolean)?displayProperty=nameWithType><p><xref:System.Type.GetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType>|`Load-by-name`.|Çağırandan çıkarsandı.<p>Bağımsız`assemblyResolver` değişken içeren yöntemleri tercih <xref:System.Type.GetType%2A?displayProperty=nameWithType> edin.|
<xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>|Tür `name` , derleme nitelikli genel tür tanımlıyor, a `Load-by-name`tetikleyicisi.|Çağırandan çıkarsandı.<p>Derleme <xref:System.Type.GetType%2A?displayProperty=nameWithType> nitelikli tür adları kullanırken tercih edilir.|
<xref:System.Activator.CreateInstance(System.String,System.String)?displayProperty=nameWithType><p><xref:System.Activator.CreateInstance(System.String,System.String,System.Object[])?displayProperty=nameWithType><p><xref:System.Activator.CreateInstance(System.String,System.String,System.Boolean,System.Reflection.BindingFlags,System.Reflection.Binder,System.Object[],System.Globalization.CultureInfo,System.Object[])?displayProperty=nameWithType>|`Load-by-name`.|Çağırandan çıkarsandı.<p>Bağımsız<xref:System.Type> değişken alan yöntemler tercih <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> edin.|

## <a name="algorithm"></a>Algoritmalar

Aşağıdaki algoritma, çalışma zamanının yönetilen bir derlemeyi nasıl yüklediğini açıklar.

1. `active` Öğesini<xref:System.Runtime.Loader.AssemblyLoadContext>saptayın.

    - Statik derleme başvurusu `active` <xref:System.Runtime.Loader.AssemblyLoadContext> için, başvuran derlemeyi yükleyen örnek olur.
    - Tercih edilen API 'ler `active` <xref:System.Runtime.Loader.AssemblyLoadContext> açık hale getirir.
    - Diğer API 'Ler `active`. <xref:System.Runtime.Loader.AssemblyLoadContext> Bu API 'ler için, <xref:System.Runtime.Loader.AssemblyLoadContext.CurrentContextualReflectionContext?displayProperty=nameWithType> özelliği kullanılır. Değeri ise `null`, çıkartılan <xref:System.Runtime.Loader.AssemblyLoadContext> örnek kullanılır.
    - Yukarıdaki tabloya bakın.

2. Yöntemler için, etkin <xref:System.Runtime.Loader.AssemblyLoadContext> derlemeyi yükler. `Load-by-name` Öncelik sırasına göre:
    - `cache-by-name`Denetleniyor.

    - <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> İşlevi çağrılıyor.

    - Örneklerin önbelleği denetleniyor ve [yönetilen derleme varsayılan araştırma](default-probing.md#managed-assembly-default-probing) mantığı çalıştırılıyor. <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>

    - Etkin assemblyloadcontext için olay oluşturma. <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType>

    - <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> Olayı oluşturma.

3. Diğer yük `active` <xref:System.Runtime.Loader.AssemblyLoadContext> türleri için, derlemeyi yükler. Öncelik sırasına göre:
    - `cache-by-name`Denetleniyor.

    - Belirtilen yoldan veya ham derleme nesnesinden yükleniyor.

4. Her iki durumda da, bir derleme yeni yüklenmişse:
   - <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> Olay tetiklenir.
   - <xref:System.Runtime.Loader.AssemblyLoadContext> Derlemenin`cache-by-name`örneğine bir başvuru eklenir.

5. Derleme bulunursa, `active` <xref:System.Runtime.Loader.AssemblyLoadContext> örnek `cache-by-name`için gerektiğinde bir başvuru eklenir.
