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
# <a name="unmanaged-native-library-loading-algorithm"></a><span data-ttu-id="cb5b9-103">Yönetilmeyen (yerel) kitaplık yükleme algoritması</span><span class="sxs-lookup"><span data-stu-id="cb5b9-103">Unmanaged (native) library loading algorithm</span></span>

<span data-ttu-id="cb5b9-104">Yönetilmeyen kitaplıklar, çeşitli aşamalar içeren bir algoritmayla bulunur ve yüklenir.</span><span class="sxs-lookup"><span data-stu-id="cb5b9-104">Unmanaged libraries are located and loaded with an algorithm involving various stages.</span></span>

<span data-ttu-id="cb5b9-105">Aşağıdaki algoritma, yerel kitaplıkların `PInvoke` ile nasıl yükleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="cb5b9-105">The following algorithm describes how native libraries are loaded through `PInvoke`.</span></span>

## <a name="pinvoke-load-library-algorithm"></a><span data-ttu-id="cb5b9-106">`PInvoke` yükleme kitaplığı algoritması</span><span class="sxs-lookup"><span data-stu-id="cb5b9-106">`PInvoke` load library algorithm</span></span>

<span data-ttu-id="cb5b9-107">`PInvoke`, yönetilmeyen bir derlemeyi yüklemeye çalışırken aşağıdaki algoritmayı kullanır:</span><span class="sxs-lookup"><span data-stu-id="cb5b9-107">`PInvoke` uses the following algorithm when attempting to load an unmanaged assembly:</span></span>

1. <span data-ttu-id="cb5b9-108">@No__t-0 <xref:System.Runtime.Loader.AssemblyLoadContext> ' i saptayın.</span><span class="sxs-lookup"><span data-stu-id="cb5b9-108">Determine the `active` <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="cb5b9-109">Yönetilmeyen bir yük kitaplığı için `active` AssemblyLoadContext, `PInvoke` tanımlayan derlemeden biridir.</span><span class="sxs-lookup"><span data-stu-id="cb5b9-109">For an unmanaged load library, the `active` AssemblyLoadContext is the one with the assembly that defines the `PInvoke`.</span></span>

2. <span data-ttu-id="cb5b9-110">@No__t-0 <xref:System.Runtime.Loader.AssemblyLoadContext> için, derlemeyi şu şekilde öncelik sırasına göre bulmayı deneyin:</span><span class="sxs-lookup"><span data-stu-id="cb5b9-110">For the `active` <xref:System.Runtime.Loader.AssemblyLoadContext>, try to find the assembly in priority order by:</span></span>
    * <span data-ttu-id="cb5b9-111">Önbelleği denetleniyor.</span><span class="sxs-lookup"><span data-stu-id="cb5b9-111">Checking its cache.</span></span>

    * <span data-ttu-id="cb5b9-112">@No__t-1 işlevi tarafından ayarlanan geçerli <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> temsilcisi çağrılıyor.</span><span class="sxs-lookup"><span data-stu-id="cb5b9-112">Calling the current <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> delegate set by the <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType> function.</span></span>

    * <span data-ttu-id="cb5b9-113">@No__t-1 AssemblyLoadContext üzerinde <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> işlevi çağrılıyor.</span><span class="sxs-lookup"><span data-stu-id="cb5b9-113">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> function on the `active` AssemblyLoadContext.</span></span>

    * <span data-ttu-id="cb5b9-114">@No__t-0 örneğinin önbelleği denetleniyor ve [yönetilmeyen (yerel) kitaplık yoklama](default-probing.md#unmanaged-native-library-probing) mantığını çalıştırılıyor.</span><span class="sxs-lookup"><span data-stu-id="cb5b9-114">Checking the <xref:System.AppDomain> instance's cache and running the [Unmanaged (native) library probing](default-probing.md#unmanaged-native-library-probing) logic.</span></span>

    * <span data-ttu-id="cb5b9-115">@No__t-1 AssemblyLoadContext için <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> olayı oluşturma.</span><span class="sxs-lookup"><span data-stu-id="cb5b9-115">Raising the <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> event for the `active` AssemblyLoadContext.</span></span>
