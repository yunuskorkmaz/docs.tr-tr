---
title: ICorDebugMergedAssemblyRecord Arabirimi
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
ms.openlocfilehash: 8dc07cb8c2f57ee6f9598c727cbd6de38bf4625f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139191"
---
# <a name="icordebugmergedassemblyrecord-interface"></a><span data-ttu-id="40b71-102">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="40b71-102">ICorDebugMergedAssemblyRecord Interface</span></span>
<span data-ttu-id="40b71-103">Birleştirilmiş bir derleme hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="40b71-103">Provides information about a merged assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="40b71-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="40b71-104">Methods</span></span>  
  
|<span data-ttu-id="40b71-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="40b71-105">Method</span></span>|<span data-ttu-id="40b71-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40b71-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="40b71-107">GetCulture Yöntemi</span><span class="sxs-lookup"><span data-stu-id="40b71-107">GetCulture Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getculture-method.md)|<span data-ttu-id="40b71-108">Derlemenin kültür adı dizesini alır.</span><span class="sxs-lookup"><span data-stu-id="40b71-108">Gets the culture name string of the assembly.</span></span>|  
|[<span data-ttu-id="40b71-109">GetIndex Yöntemi</span><span class="sxs-lookup"><span data-stu-id="40b71-109">GetIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getindex-method.md)|<span data-ttu-id="40b71-110">Derlemenin önek dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="40b71-110">Gets the assembly's prefix index.</span></span>|  
|[<span data-ttu-id="40b71-111">GetPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="40b71-111">GetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickey-method.md)|<span data-ttu-id="40b71-112">Derlemenin ortak anahtarını alır.</span><span class="sxs-lookup"><span data-stu-id="40b71-112">Gets the assembly's public key.</span></span>|  
|[<span data-ttu-id="40b71-113">GetPublicKeyToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="40b71-113">GetPublicKeyToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickeytoken-method.md)|<span data-ttu-id="40b71-114">Derlemenin ortak anahtar belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="40b71-114">Gets the assembly's public key token.</span></span>|  
|[<span data-ttu-id="40b71-115">GetSimpleName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="40b71-115">GetSimpleName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getsimplename-method.md)|<span data-ttu-id="40b71-116">Derlemenin basit adını alır.</span><span class="sxs-lookup"><span data-stu-id="40b71-116">Gets the simple name of the assembly.</span></span>|  
|[<span data-ttu-id="40b71-117">GetVersion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="40b71-117">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getversion-method.md)|<span data-ttu-id="40b71-118">Derlemenin sürüm bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="40b71-118">Gets the assembly's version information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40b71-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="40b71-119">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="40b71-120">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="40b71-120">This interface is available with .NET Native only.</span></span> <span data-ttu-id="40b71-121">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="40b71-121">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40b71-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="40b71-122">Requirements</span></span>  
 <span data-ttu-id="40b71-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40b71-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40b71-124">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="40b71-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="40b71-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="40b71-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40b71-126">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40b71-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40b71-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40b71-127">See also</span></span>

- [<span data-ttu-id="40b71-128">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="40b71-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="40b71-129">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="40b71-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
