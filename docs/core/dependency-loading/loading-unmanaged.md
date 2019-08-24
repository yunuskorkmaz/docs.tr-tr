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
# <a name="unmanaged-native-library-loading-algorithm"></a><span data-ttu-id="08e0c-103">Yönetilmeyen (yerel) kitaplık yükleme algoritması</span><span class="sxs-lookup"><span data-stu-id="08e0c-103">Unmanaged (native) library loading algorithm</span></span>

<span data-ttu-id="08e0c-104">Yönetilmeyen kitaplıklar, çeşitli aşamalar içeren bir algoritmayla bulunur ve yüklenir.</span><span class="sxs-lookup"><span data-stu-id="08e0c-104">Unmanaged libraries are located and loaded with an algorithm involving various stages.</span></span>

<span data-ttu-id="08e0c-105">Aşağıdaki algoritma, yerel kitaplıkların aracılığıyla `PInvoke`nasıl yükleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="08e0c-105">The following algorithm describes how native libraries are loaded through `PInvoke`.</span></span>

## <a name="pinvoke-load-library-algorithm"></a><span data-ttu-id="08e0c-106">`PInvoke`Yükleme Kitaplığı algoritması</span><span class="sxs-lookup"><span data-stu-id="08e0c-106">`PInvoke` load library algorithm</span></span>

<span data-ttu-id="08e0c-107">`PInvoke`yönetilmeyen bir derlemeyi yüklemeye çalışırken aşağıdaki algoritmayı kullanır:</span><span class="sxs-lookup"><span data-stu-id="08e0c-107">`PInvoke` uses the following algorithm when attempting to load an unmanaged assembly:</span></span>

1. <span data-ttu-id="08e0c-108">`active` Öğesini<xref:System.Runtime.Loader.AssemblyLoadContext>saptayın.</span><span class="sxs-lookup"><span data-stu-id="08e0c-108">Determine the `active` <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="08e0c-109">Yönetilmeyen yük kitaplığı için, `active` assemblyloadcontext, ' `PInvoke`ın çağıranıdır.</span><span class="sxs-lookup"><span data-stu-id="08e0c-109">For an unmanaged load library, the `active` AssemblyLoadContext is the caller of the `PInvoke`.</span></span>

2. <span data-ttu-id="08e0c-110">`active` İçin,derlemeyişuşekildeöncelik<xref:System.Runtime.Loader.AssemblyLoadContext>sırasına göre bulmayı deneyin:</span><span class="sxs-lookup"><span data-stu-id="08e0c-110">For the `active` <xref:System.Runtime.Loader.AssemblyLoadContext>, try to find the assembly in priority order by:</span></span>
    * <span data-ttu-id="08e0c-111">Önbelleği denetleniyor.</span><span class="sxs-lookup"><span data-stu-id="08e0c-111">Checking its cache.</span></span>

    * <span data-ttu-id="08e0c-112">İşlev tarafından ayarlanan <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> geçerli temsilciyi çağırma. <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="08e0c-112">Calling the current <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> delegate set by the <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType> function.</span></span>

    * <span data-ttu-id="08e0c-113"><xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> İşlevi çağrılıyor.</span><span class="sxs-lookup"><span data-stu-id="08e0c-113">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> function.</span></span>

    * <span data-ttu-id="08e0c-114">Örneğin önbelleği denetleniyor ve [yönetilmeyen (yerel) kitaplık yoklama](default-probing.md#unmanaged-native-library-probing) mantığını çalıştırıyor. <xref:System.AppDomain></span><span class="sxs-lookup"><span data-stu-id="08e0c-114">Checking the <xref:System.AppDomain> instance's cache and running the [Unmanaged (native) library probing](default-probing.md#unmanaged-native-library-probing) logic.</span></span>

    * <span data-ttu-id="08e0c-115">Assemblyloadcontext`active` için olay oluşturma. <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="08e0c-115">Raising the <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> event for the `active` AssemblyLoadContext.</span></span>

3. <span data-ttu-id="08e0c-116">Yönetilmeyen kitaplık yeni yüklenmişse, <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> olay tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="08e0c-116">If the unmanaged library is newly loaded, the <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> event is raised.</span></span>
