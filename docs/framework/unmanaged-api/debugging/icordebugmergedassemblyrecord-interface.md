---
title: ICorDebugMergedAssemblyRecord arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 301d7d3d20b78e833101de1df8fd5c271a757144
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmergedassemblyrecord-interface"></a><span data-ttu-id="1ce18-102">ICorDebugMergedAssemblyRecord arabirimi</span><span class="sxs-lookup"><span data-stu-id="1ce18-102">ICorDebugMergedAssemblyRecord Interface</span></span>
<span data-ttu-id="1ce18-103">Birleştirilmiş bir derleme hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1ce18-103">Provides information about a merged assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1ce18-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1ce18-104">Methods</span></span>  
  
|<span data-ttu-id="1ce18-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1ce18-105">Method</span></span>|<span data-ttu-id="1ce18-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1ce18-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1ce18-107">GetCulture yöntemi</span><span class="sxs-lookup"><span data-stu-id="1ce18-107">GetCulture Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getculture-method.md)|<span data-ttu-id="1ce18-108">Derleme kültür adı dizesini alır.</span><span class="sxs-lookup"><span data-stu-id="1ce18-108">Gets the culture name string of the assembly.</span></span>|  
|[<span data-ttu-id="1ce18-109">Getındex yöntemi</span><span class="sxs-lookup"><span data-stu-id="1ce18-109">GetIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getindex-method.md)|<span data-ttu-id="1ce18-110">Derlemenin ön eki dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="1ce18-110">Gets the assembly's prefix index.</span></span>|  
|[<span data-ttu-id="1ce18-111">GetPublicKey yöntemi</span><span class="sxs-lookup"><span data-stu-id="1ce18-111">GetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickey-method.md)|<span data-ttu-id="1ce18-112">Derlemenin ortak anahtarı alır.</span><span class="sxs-lookup"><span data-stu-id="1ce18-112">Gets the assembly's public key.</span></span>|  
|[<span data-ttu-id="1ce18-113">GetPublicKeyToken yöntemi</span><span class="sxs-lookup"><span data-stu-id="1ce18-113">GetPublicKeyToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getpublickeytoken-method.md)|<span data-ttu-id="1ce18-114">Derlemenin ortak anahtar belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="1ce18-114">Gets the assembly's public key token.</span></span>|  
|[<span data-ttu-id="1ce18-115">GetSimpleName yöntemi</span><span class="sxs-lookup"><span data-stu-id="1ce18-115">GetSimpleName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getsimplename-method.md)|<span data-ttu-id="1ce18-116">Basit derlemenin adını alır.</span><span class="sxs-lookup"><span data-stu-id="1ce18-116">Gets the simple name of the assembly.</span></span>|  
|[<span data-ttu-id="1ce18-117">GetVersion yöntemi</span><span class="sxs-lookup"><span data-stu-id="1ce18-117">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-getversion-method.md)|<span data-ttu-id="1ce18-118">Derlemenin sürüm bilgisi alır.</span><span class="sxs-lookup"><span data-stu-id="1ce18-118">Gets the assembly's version information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ce18-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1ce18-119">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1ce18-120">Bu arabirim yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1ce18-120">This interface is available with .NET Native only.</span></span> <span data-ttu-id="1ce18-121">Bu arabirim .NET yerel dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirim göz ardı eder.</span><span class="sxs-lookup"><span data-stu-id="1ce18-121">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ce18-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1ce18-122">Requirements</span></span>  
 <span data-ttu-id="1ce18-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ce18-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ce18-124">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1ce18-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ce18-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ce18-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ce18-126">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ce18-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ce18-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1ce18-127">See Also</span></span>  
 [<span data-ttu-id="1ce18-128">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1ce18-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="1ce18-129">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="1ce18-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
