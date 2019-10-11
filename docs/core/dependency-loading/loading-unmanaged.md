---
title: Yönetilmeyen kitaplık yükleme algoritması-.NET Core
description: .NET Core 'da yönetilmeyen derleme yükleme algoritmasının ayrıntılarının açıklaması
ms.date: 10/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: c651aa6e0f37a968e6f8b26d1909def6fa488ccd
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250034"
---
# <a name="unmanaged-native-library-loading-algorithm"></a>Yönetilmeyen (yerel) kitaplık yükleme algoritması

Yönetilmeyen kitaplıklar, çeşitli aşamalar içeren bir algoritmayla bulunur ve yüklenir.

Aşağıdaki algoritma, yerel kitaplıkların `PInvoke` ile nasıl yükleneceğini açıklar.

## <a name="pinvoke-load-library-algorithm"></a>`PInvoke` yükleme kitaplığı algoritması

`PInvoke`, yönetilmeyen bir derlemeyi yüklemeye çalışırken aşağıdaki algoritmayı kullanır:

1. @No__t-0 <xref:System.Runtime.Loader.AssemblyLoadContext> ' i saptayın. Yönetilmeyen bir yük kitaplığı için `active` AssemblyLoadContext, `PInvoke` tanımlayan derlemeden biridir.

2. @No__t-0 <xref:System.Runtime.Loader.AssemblyLoadContext> için, derlemeyi şu şekilde öncelik sırasına göre bulmayı deneyin:
    * Önbelleği denetleniyor.

    * @No__t-1 işlevi tarafından ayarlanan geçerli <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> temsilcisi çağrılıyor.

    * @No__t-1 AssemblyLoadContext üzerinde <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> işlevi çağrılıyor.

    * @No__t-0 örneğinin önbelleği denetleniyor ve [yönetilmeyen (yerel) kitaplık yoklama](default-probing.md#unmanaged-native-library-probing) mantığını çalıştırılıyor.

    * @No__t-1 AssemblyLoadContext için <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> olayı oluşturma.
