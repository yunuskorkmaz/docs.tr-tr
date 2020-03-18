---
title: Yönetilmeyen kitaplık yükleme algoritması - .NET Core
description: .NET Core'da yönetilmeyen montaj yükleme algoritmasının ayrıntılarının açıklaması
ms.date: 10/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: c651aa6e0f37a968e6f8b26d1909def6fa488ccd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72250034"
---
# <a name="unmanaged-native-library-loading-algorithm"></a>Yönetilmeyen (yerel) kitaplık yükleme algoritması

Yönetilmeyen kitaplıklar bulunur ve çeşitli aşamaları içeren bir algoritma ile yüklenir.

Aşağıdaki algoritma, yerel kitaplıkların `PInvoke`nasıl yüklendiğini açıklar.

## <a name="pinvoke-load-library-algorithm"></a>`PInvoke`yük kitaplığı algoritması

`PInvoke`yönetilmeyen bir derlemeyüklemeye çalışırken aşağıdaki algoritmayı kullanır:

1. Belirleyin. `active` <xref:System.Runtime.Loader.AssemblyLoadContext> Yönetilmeyen bir yük kitaplığı için `active` AssemblyLoadContext, `PInvoke`'yi tanımlayan derlemeye sahip olandır.

2. `active` <xref:System.Runtime.Loader.AssemblyLoadContext>Için , tarafından öncelikli sırada montaj bulmaya çalışın:
    * Önbelleğini kontrol ediyorum.

    * İşlev <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> tarafından ayarlanan <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType> geçerli temsilciyi çağırma.

    * <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> AssemblyLoadContext işlevi `active` arama.

    * Örnek <xref:System.AppDomain> önbelleğini denetleme ve [Yönetilmeyen (yerel) kitaplık sondalama](default-probing.md#unmanaged-native-library-probing) mantığını çalıştırma.

    * `active` AssemblyLoadContext için <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> etkinliği yükseltme.
