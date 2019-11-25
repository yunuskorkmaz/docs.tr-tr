---
title: Yönetilen derleme yükleme algoritması-.NET Core
description: .NET Core 'da yönetilen derleme yükleme algoritması ayrıntılarının açıklaması
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 312a320676be6eb453697e0704ab771a6707618b
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973507"
---
# <a name="managed-assembly-loading-algorithm"></a>Yönetilen derleme yükleme algoritması

Yönetilen derlemeler, çeşitli aşamalar içeren bir algoritmayla bulunur ve yüklenir.

Uydu derlemeleri ve `WinRT` derlemeleri dışındaki tüm yönetilen derlemeler aynı algoritmayı kullanır.

## <a name="when-are-managed-assemblies-loaded"></a>Yönetilen derlemeler ne zaman yüklenir?

Yönetilen bir derleme yükünü tetiklemek için en yaygın mekanizma statik bir derleme başvurusudur. Bu başvurular, kod başka bir derlemede tanımlı bir tür kullandığında derleyici tarafından eklenir. Bu derlemeler çalışma zamanının gerektirdiği şekilde yüklenir (`load-by-name`).

Belirli API 'lerin doğrudan kullanımı da yükleri tetikleyecektir:

|API  |Açıklama  |`Active`<xref:System.Runtime.Loader.AssemblyLoadContext> |
|---------|---------|---------|
|<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyName%2A?displayProperty=nameWithType>|`Load-by-name`|[Bu](../../csharp/language-reference/keywords/this.md) örnek.|
|<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyPath%2A?displayProperty=nameWithType><p><xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromNativeImagePath%2A?displayProperty=nameWithType>|Yoldan yükle.|[Bu](../../csharp/language-reference/keywords/this.md) örnek.|
<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromStream%2A?displayProperty=nameWithType>|Nesnesinden yükle.|[Bu](../../csharp/language-reference/keywords/this.md) örnek.|
|<xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType>|Yeni bir <xref:System.Runtime.Loader.AssemblyLoadContext> örneğindeki yoldan yükleme|Yeni <xref:System.Runtime.Loader.AssemblyLoadContext> örneği.|
<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>|<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> örneğindeki yoldan yükleyin.<p><xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>için <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving> işleyicisi ekler. İşleyici, derlemenin bağımlılıklarını dizinden yükleyecek.|<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> örneği.|
|<xref:System.Reflection.Assembly.Load(System.Reflection.AssemblyName)?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.Load(System.String)?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>|`Load-by-name`.|Çağırandan çıkarsandı.<p><xref:System.Runtime.Loader.AssemblyLoadContext> yöntemleri tercih edin.|
|<xref:System.Reflection.Assembly.Load(System.Byte[])?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.Load(System.Byte[],System.Byte[])?displayProperty=nameWithType>|Yeni bir <xref:System.Runtime.Loader.AssemblyLoadContext> örneğindeki nesnesinden yükle.|Yeni <xref:System.Runtime.Loader.AssemblyLoadContext> örneği.|
<xref:System.Type.GetType(System.String)?displayProperty=nameWithType><p><xref:System.Type.GetType(System.String,System.Boolean)?displayProperty=nameWithType><p><xref:System.Type.GetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType>|`Load-by-name`.|Çağırandan çıkarsandı.<p>`assemblyResolver` bağımsız değişkenle <xref:System.Type.GetType%2A?displayProperty=nameWithType> Yöntemler tercih edin.|
<xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>|Tür `name`, derleme nitelikli genel türü açıklar, bir `Load-by-name`tetikler.|Çağırandan çıkarsandı.<p>Derleme nitelikli tür adlarını kullanırken <xref:System.Type.GetType%2A?displayProperty=nameWithType> tercih edin.|
<xref:System.Activator.CreateInstance(System.String,System.String)?displayProperty=nameWithType><p><xref:System.Activator.CreateInstance(System.String,System.String,System.Object[])?displayProperty=nameWithType><p><xref:System.Activator.CreateInstance(System.String,System.String,System.Boolean,System.Reflection.BindingFlags,System.Reflection.Binder,System.Object[],System.Globalization.CultureInfo,System.Object[])?displayProperty=nameWithType>|`Load-by-name`.|Çağırandan çıkarsandı.<p><xref:System.Type> bağımsız değişken alan <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> Yöntemler tercih edin.|

## <a name="algorithm"></a>Algoritmalar

Aşağıdaki algoritma, çalışma zamanının yönetilen bir derlemeyi nasıl yüklediğini açıklar.

1. `active` <xref:System.Runtime.Loader.AssemblyLoadContext>belirleme.

    - Statik derleme başvurusu için, `active` <xref:System.Runtime.Loader.AssemblyLoadContext> başvuran derlemeyi yükleyen örneğidir.
    - Tercih edilen API 'Ler `active` <xref:System.Runtime.Loader.AssemblyLoadContext> açık hale getirir.
    - Diğer API 'Ler `active` <xref:System.Runtime.Loader.AssemblyLoadContext>çıkarçıkar. Bu API 'Ler için <xref:System.Runtime.Loader.AssemblyLoadContext.CurrentContextualReflectionContext?displayProperty=nameWithType> özelliği kullanılır. Değeri `null`ise, çıkartılan <xref:System.Runtime.Loader.AssemblyLoadContext> örneği kullanılır.
    - Yukarıdaki tabloya bakın.

2. `Load-by-name` yöntemler için, etkin <xref:System.Runtime.Loader.AssemblyLoadContext> derlemeyi yükler. Öncelik sırasına göre:
    - `cache-by-name`denetleniyor.

    - <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> işlevi çağrılıyor.

    - <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> örneklerinin önbelleği denetleniyor ve [yönetilen derleme varsayılan araştırma](default-probing.md#managed-assembly-default-probing) mantığı çalıştırılıyor.

    - Etkin AssemblyLoadContext için <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> olayı oluşturma.

    - <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olayını oluşturma.

3. Diğer yük türleri için `active` <xref:System.Runtime.Loader.AssemblyLoadContext> derlemeyi yükler. Öncelik sırasına göre:
    - `cache-by-name`denetleniyor.

    - Belirtilen yoldan veya ham derleme nesnesinden yükleniyor.

4. Her iki durumda da, bir derleme yeni yüklenmişse:
   - <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> olay tetiklenir.
   - Derlemenin <xref:System.Runtime.Loader.AssemblyLoadContext> örneğinin `cache-by-name`bir başvuru eklenir.

5. Derleme bulunursa, `active` <xref:System.Runtime.Loader.AssemblyLoadContext> örneğinin `cache-by-name`gerektiğinde bir başvuru eklenir.
