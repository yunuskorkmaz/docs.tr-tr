---
title: "ICorDebugMergedAssemblyRecord::GetPublicKeyToken yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4c286981def6f12f8e5b8fa5397f23535d4d4623
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmergedassemblyrecordgetpublickeytoken-method"></a><span data-ttu-id="ec8be-102">ICorDebugMergedAssemblyRecord::GetPublicKeyToken yöntemi</span><span class="sxs-lookup"><span data-stu-id="ec8be-102">ICorDebugMergedAssemblyRecord::GetPublicKeyToken Method</span></span>
<span data-ttu-id="ec8be-103">Derlemenin ortak anahtar belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="ec8be-103">Gets the assembly's public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec8be-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ec8be-104">Syntax</span></span>  
  
```  
HRESULT GetPublicKeyToken(  
   [in] ULONG32 cbPublicKeyToken,   
   [out] ULONG32 *pcbPublicKeyToken,   
   [out, size_is(cbPublicKeyToken), length_is(*pcbPublicKeyToken)] BYTE pbPublicKeyToken[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ec8be-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ec8be-105">Parameters</span></span>  
 `cbPublicKeyToken`  
 <span data-ttu-id="ec8be-106">[in] Bayt cinsinden en büyük sayısını `pbPublicKeyToken` dizi.</span><span class="sxs-lookup"><span data-stu-id="ec8be-106">[in] The maximum number of bytes in the `pbPublicKeyToken` array.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="ec8be-107">[out] Yazılan bayt sayısını gösteren bir işaretçi `pbPublicKeyToken` dizi.</span><span class="sxs-lookup"><span data-stu-id="ec8be-107">[out] A pointer to the actual number of bytes written to the `pbPublicKeyToken` array.</span></span>  
  
 `pbPublicKeyToken`  
 <span data-ttu-id="ec8be-108">[out] Derlemenin ortak anahtar belirteci içeren bayt dizisi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ec8be-108">[out] A pointer to a byte array that contains the assembly's public key token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec8be-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ec8be-109">Remarks</span></span>  
 <span data-ttu-id="ec8be-110">Bir derlemenin ortak anahtar belirteci, ortak anahtarı SHA1 karmasını, son sekiz bayttır.</span><span class="sxs-lookup"><span data-stu-id="ec8be-110">An assembly's public key token is the last eight bytes of a SHA1 hash of its public key.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ec8be-111">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ec8be-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec8be-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ec8be-112">Requirements</span></span>  
 <span data-ttu-id="ec8be-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec8be-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec8be-114">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ec8be-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ec8be-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec8be-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec8be-116">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec8be-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec8be-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ec8be-117">See Also</span></span>  
 [<span data-ttu-id="ec8be-118">ICorDebugMergedAssemblyRecord arabirimi</span><span class="sxs-lookup"><span data-stu-id="ec8be-118">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="ec8be-119">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ec8be-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
