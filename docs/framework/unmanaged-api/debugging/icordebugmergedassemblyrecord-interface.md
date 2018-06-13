---
title: ICorDebugMergedAssemblyRecord arabirimi
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e135166b79bb130e271549228418881b0c7587c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419682"
---
# <a name="icordebugmergedassemblyrecord-interface"></a><span data-ttu-id="e9a1b-102">ICorDebugMergedAssemblyRecord arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9a1b-102">ICorDebugMergedAssemblyRecord Interface</span></span>
<span data-ttu-id="e9a1b-103">Birleştirilmiş bir derleme hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e9a1b-103">Provides information about a merged assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e9a1b-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e9a1b-104">Methods</span></span>  
  
|<span data-ttu-id="e9a1b-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e9a1b-105">Method</span></span>|<span data-ttu-id="e9a1b-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9a1b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e9a1b-107">GetCulture Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e9a1b-107">GetCulture Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getculture-method.md)|<span data-ttu-id="e9a1b-108">Derleme kültür adı dizesini alır.</span><span class="sxs-lookup"><span data-stu-id="e9a1b-108">Gets the culture name string of the assembly.</span></span>|  
|[<span data-ttu-id="e9a1b-109">GetIndex Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e9a1b-109">GetIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getindex-method.md)|<span data-ttu-id="e9a1b-110">Derlemenin ön eki dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="e9a1b-110">Gets the assembly's prefix index.</span></span>|  
|[<span data-ttu-id="e9a1b-111">GetPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e9a1b-111">GetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickey-method.md)|<span data-ttu-id="e9a1b-112">Derlemenin ortak anahtarı alır.</span><span class="sxs-lookup"><span data-stu-id="e9a1b-112">Gets the assembly's public key.</span></span>|  
|[<span data-ttu-id="e9a1b-113">GetPublicKeyToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e9a1b-113">GetPublicKeyToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickeytoken-method.md)|<span data-ttu-id="e9a1b-114">Derlemenin ortak anahtar belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="e9a1b-114">Gets the assembly's public key token.</span></span>|  
|[<span data-ttu-id="e9a1b-115">GetSimpleName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e9a1b-115">GetSimpleName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getsimplename-method.md)|<span data-ttu-id="e9a1b-116">Basit derlemenin adını alır.</span><span class="sxs-lookup"><span data-stu-id="e9a1b-116">Gets the simple name of the assembly.</span></span>|  
|[<span data-ttu-id="e9a1b-117">GetVersion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e9a1b-117">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getversion-method.md)|<span data-ttu-id="e9a1b-118">Derlemenin sürüm bilgisi alır.</span><span class="sxs-lookup"><span data-stu-id="e9a1b-118">Gets the assembly's version information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9a1b-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e9a1b-119">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9a1b-120">Bu arabirim yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e9a1b-120">This interface is available with .NET Native only.</span></span> <span data-ttu-id="e9a1b-121">Bu arabirim .NET yerel dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirim göz ardı eder.</span><span class="sxs-lookup"><span data-stu-id="e9a1b-121">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9a1b-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e9a1b-122">Requirements</span></span>  
 <span data-ttu-id="e9a1b-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9a1b-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9a1b-124">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9a1b-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9a1b-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9a1b-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9a1b-126">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9a1b-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9a1b-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e9a1b-127">See Also</span></span>  
 [<span data-ttu-id="e9a1b-128">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e9a1b-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="e9a1b-129">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="e9a1b-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
