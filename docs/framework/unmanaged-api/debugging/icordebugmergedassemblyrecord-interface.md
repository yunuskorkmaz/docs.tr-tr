---
title: Icordebugmergedassemblyrecord arabirimi
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c0f42b8d6eb1a35052b25fda6e7cc9c7d00836df
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559365"
---
# <a name="icordebugmergedassemblyrecord-interface"></a><span data-ttu-id="dedbc-102">Icordebugmergedassemblyrecord arabirimi</span><span class="sxs-lookup"><span data-stu-id="dedbc-102">ICorDebugMergedAssemblyRecord Interface</span></span>
<span data-ttu-id="dedbc-103">Birleştirilmiş bir derleme hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="dedbc-103">Provides information about a merged assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dedbc-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="dedbc-104">Methods</span></span>  
  
|<span data-ttu-id="dedbc-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="dedbc-105">Method</span></span>|<span data-ttu-id="dedbc-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dedbc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dedbc-107">GetCulture Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dedbc-107">GetCulture Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getculture-method.md)|<span data-ttu-id="dedbc-108">Derlemenin kültür adı dizesi alır.</span><span class="sxs-lookup"><span data-stu-id="dedbc-108">Gets the culture name string of the assembly.</span></span>|  
|[<span data-ttu-id="dedbc-109">GetIndex Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dedbc-109">GetIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getindex-method.md)|<span data-ttu-id="dedbc-110">Derlemenin ön eki dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="dedbc-110">Gets the assembly's prefix index.</span></span>|  
|[<span data-ttu-id="dedbc-111">GetPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dedbc-111">GetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickey-method.md)|<span data-ttu-id="dedbc-112">Derlemenin ortak anahtarı alır.</span><span class="sxs-lookup"><span data-stu-id="dedbc-112">Gets the assembly's public key.</span></span>|  
|[<span data-ttu-id="dedbc-113">GetPublicKeyToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dedbc-113">GetPublicKeyToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickeytoken-method.md)|<span data-ttu-id="dedbc-114">Derlemenin genel anahtar belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="dedbc-114">Gets the assembly's public key token.</span></span>|  
|[<span data-ttu-id="dedbc-115">GetSimpleName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dedbc-115">GetSimpleName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getsimplename-method.md)|<span data-ttu-id="dedbc-116">Derlemenin basit adını alır.</span><span class="sxs-lookup"><span data-stu-id="dedbc-116">Gets the simple name of the assembly.</span></span>|  
|[<span data-ttu-id="dedbc-117">GetVersion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dedbc-117">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getversion-method.md)|<span data-ttu-id="dedbc-118">Derlemenin sürüm bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="dedbc-118">Gets the assembly's version information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dedbc-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dedbc-119">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dedbc-120">Bu arabirim yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dedbc-120">This interface is available with .NET Native only.</span></span> <span data-ttu-id="dedbc-121">Bu arabirim .NET Native dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="dedbc-121">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dedbc-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dedbc-122">Requirements</span></span>  
 <span data-ttu-id="dedbc-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dedbc-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dedbc-124">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dedbc-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dedbc-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dedbc-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dedbc-126">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dedbc-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dedbc-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dedbc-127">See also</span></span>
- [<span data-ttu-id="dedbc-128">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="dedbc-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="dedbc-129">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="dedbc-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
