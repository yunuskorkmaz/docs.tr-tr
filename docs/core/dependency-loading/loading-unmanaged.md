---
title: Yönetilmeyen kitaplık yükleme algoritması-.NET Core
description: .NET Core 'da yönetilmeyen derleme yükleme algoritmasının ayrıntılarının açıklaması
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 8240cb730180637393e2545f8013d3f1439be719
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70017331"
---
# <a name="unmanaged-native-library-loading-algorithm"></a>Yönetilmeyen (yerel) kitaplık yükleme algoritması

Yönetilmeyen kitaplıklar, çeşitli aşamalar içeren bir algoritmayla bulunur ve yüklenir.

Aşağıdaki algoritma, yerel kitaplıkların aracılığıyla `PInvoke`nasıl yükleneceğini açıklar.

## <a name="pinvoke-load-library-algorithm"></a>`PInvoke`Yükleme Kitaplığı algoritması

`PInvoke`yönetilmeyen bir derlemeyi yüklemeye çalışırken aşağıdaki algoritmayı kullanır:

1. `active` Öğesini<xref:System.Runtime.Loader.AssemblyLoadContext>saptayın. Yönetilmeyen yük kitaplığı için, `active` assemblyloadcontext, ' `PInvoke`ın çağıranıdır.

2. `active` İçin,derlemeyişuşekildeöncelik<xref:System.Runtime.Loader.AssemblyLoadContext>sırasına göre bulmayı deneyin:
    * Önbelleği denetleniyor.

    * İşlev tarafından ayarlanan <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> geçerli temsilciyi çağırma. <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType>

    * <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> İşlevi çağrılıyor.

    * Örneğin önbelleği denetleniyor ve [yönetilmeyen (yerel) kitaplık yoklama](default-probing.md#unmanaged-native-library-probing) mantığını çalıştırıyor. <xref:System.AppDomain>

    * Assemblyloadcontext`active` için olay oluşturma. <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType>

3. Yönetilmeyen kitaplık yeni yüklenmişse, <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> olay tetiklenir.
