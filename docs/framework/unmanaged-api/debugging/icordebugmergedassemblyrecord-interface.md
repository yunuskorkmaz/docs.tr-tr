---
title: ICorDebugMergedAssemblyRecord Arabirimi
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1118c879da4376bda0c73368a8b15df4f7a3d014
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180472"
---
# <a name="icordebugmergedassemblyrecord-interface"></a><span data-ttu-id="3e0fa-102">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3e0fa-102">ICorDebugMergedAssemblyRecord Interface</span></span>
<span data-ttu-id="3e0fa-103">Birleştirilmiş bir derleme hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e0fa-103">Provides information about a merged assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3e0fa-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="3e0fa-104">Methods</span></span>  
  
|<span data-ttu-id="3e0fa-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="3e0fa-105">Method</span></span>|<span data-ttu-id="3e0fa-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e0fa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3e0fa-107">GetCulture Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3e0fa-107">GetCulture Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getculture-method.md)|<span data-ttu-id="3e0fa-108">Derlemenin kültür adı dizesi alır.</span><span class="sxs-lookup"><span data-stu-id="3e0fa-108">Gets the culture name string of the assembly.</span></span>|  
|[<span data-ttu-id="3e0fa-109">GetIndex Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3e0fa-109">GetIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getindex-method.md)|<span data-ttu-id="3e0fa-110">Derlemenin ön eki dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="3e0fa-110">Gets the assembly's prefix index.</span></span>|  
|[<span data-ttu-id="3e0fa-111">GetPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3e0fa-111">GetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickey-method.md)|<span data-ttu-id="3e0fa-112">Derlemenin ortak anahtarı alır.</span><span class="sxs-lookup"><span data-stu-id="3e0fa-112">Gets the assembly's public key.</span></span>|  
|[<span data-ttu-id="3e0fa-113">GetPublicKeyToken Metodu</span><span class="sxs-lookup"><span data-stu-id="3e0fa-113">GetPublicKeyToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickeytoken-method.md)|<span data-ttu-id="3e0fa-114">Derlemenin genel anahtar belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="3e0fa-114">Gets the assembly's public key token.</span></span>|  
|[<span data-ttu-id="3e0fa-115">GetSimpleName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3e0fa-115">GetSimpleName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getsimplename-method.md)|<span data-ttu-id="3e0fa-116">Derlemenin basit adını alır.</span><span class="sxs-lookup"><span data-stu-id="3e0fa-116">Gets the simple name of the assembly.</span></span>|  
|[<span data-ttu-id="3e0fa-117">GetVersion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3e0fa-117">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getversion-method.md)|<span data-ttu-id="3e0fa-118">Derlemenin sürüm bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="3e0fa-118">Gets the assembly's version information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e0fa-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3e0fa-119">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3e0fa-120">Bu arabirim yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3e0fa-120">This interface is available with .NET Native only.</span></span> <span data-ttu-id="3e0fa-121">Bu arabirim .NET Native dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="3e0fa-121">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e0fa-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3e0fa-122">Requirements</span></span>  
 <span data-ttu-id="3e0fa-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e0fa-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e0fa-124">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3e0fa-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3e0fa-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e0fa-125">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="3e0fa-126">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="3e0fa-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3e0fa-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e0fa-127">See also</span></span>

- [<span data-ttu-id="3e0fa-128">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3e0fa-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="3e0fa-129">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="3e0fa-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
