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
# <a name="unmanaged-native-library-loading-algorithm"></a><span data-ttu-id="31853-103">Yönetilmeyen (yerel) kitaplık yükleme algoritması</span><span class="sxs-lookup"><span data-stu-id="31853-103">Unmanaged (native) library loading algorithm</span></span>

<span data-ttu-id="31853-104">Yönetilmeyen kitaplıklar bulunur ve çeşitli aşamaları içeren bir algoritma ile yüklenir.</span><span class="sxs-lookup"><span data-stu-id="31853-104">Unmanaged libraries are located and loaded with an algorithm involving various stages.</span></span>

<span data-ttu-id="31853-105">Aşağıdaki algoritma, yerel kitaplıkların `PInvoke`nasıl yüklendiğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="31853-105">The following algorithm describes how native libraries are loaded through `PInvoke`.</span></span>

## <a name="pinvoke-load-library-algorithm"></a><span data-ttu-id="31853-106">`PInvoke`yük kitaplığı algoritması</span><span class="sxs-lookup"><span data-stu-id="31853-106">`PInvoke` load library algorithm</span></span>

<span data-ttu-id="31853-107">`PInvoke`yönetilmeyen bir derlemeyüklemeye çalışırken aşağıdaki algoritmayı kullanır:</span><span class="sxs-lookup"><span data-stu-id="31853-107">`PInvoke` uses the following algorithm when attempting to load an unmanaged assembly:</span></span>

1. <span data-ttu-id="31853-108">Belirleyin. `active` <xref:System.Runtime.Loader.AssemblyLoadContext></span><span class="sxs-lookup"><span data-stu-id="31853-108">Determine the `active` <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="31853-109">Yönetilmeyen bir yük kitaplığı için `active` AssemblyLoadContext, `PInvoke`'yi tanımlayan derlemeye sahip olandır.</span><span class="sxs-lookup"><span data-stu-id="31853-109">For an unmanaged load library, the `active` AssemblyLoadContext is the one with the assembly that defines the `PInvoke`.</span></span>

2. <span data-ttu-id="31853-110">`active` <xref:System.Runtime.Loader.AssemblyLoadContext>Için , tarafından öncelikli sırada montaj bulmaya çalışın:</span><span class="sxs-lookup"><span data-stu-id="31853-110">For the `active` <xref:System.Runtime.Loader.AssemblyLoadContext>, try to find the assembly in priority order by:</span></span>
    * <span data-ttu-id="31853-111">Önbelleğini kontrol ediyorum.</span><span class="sxs-lookup"><span data-stu-id="31853-111">Checking its cache.</span></span>

    * <span data-ttu-id="31853-112">İşlev <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> tarafından ayarlanan <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType> geçerli temsilciyi çağırma.</span><span class="sxs-lookup"><span data-stu-id="31853-112">Calling the current <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> delegate set by the <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType> function.</span></span>

    * <span data-ttu-id="31853-113"><xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> AssemblyLoadContext işlevi `active` arama.</span><span class="sxs-lookup"><span data-stu-id="31853-113">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> function on the `active` AssemblyLoadContext.</span></span>

    * <span data-ttu-id="31853-114">Örnek <xref:System.AppDomain> önbelleğini denetleme ve [Yönetilmeyen (yerel) kitaplık sondalama](default-probing.md#unmanaged-native-library-probing) mantığını çalıştırma.</span><span class="sxs-lookup"><span data-stu-id="31853-114">Checking the <xref:System.AppDomain> instance's cache and running the [Unmanaged (native) library probing](default-probing.md#unmanaged-native-library-probing) logic.</span></span>

    * <span data-ttu-id="31853-115">`active` AssemblyLoadContext için <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> etkinliği yükseltme.</span><span class="sxs-lookup"><span data-stu-id="31853-115">Raising the <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> event for the `active` AssemblyLoadContext.</span></span>
