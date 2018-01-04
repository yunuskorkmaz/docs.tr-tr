---
title: "ICorDebugMergedAssemblyRecord::GetPublicKey yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a47eb051cd9922b8640b8b612ff0ac5882b6a8ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="89799-102">ICorDebugMergedAssemblyRecord::GetPublicKey yöntemi</span><span class="sxs-lookup"><span data-stu-id="89799-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>
<span data-ttu-id="89799-103">Derlemenin ortak anahtarı alır.</span><span class="sxs-lookup"><span data-stu-id="89799-103">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89799-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="89799-104">Syntax</span></span>  
  
```  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,   
   [out] ULONG32 *pcbPublicKey,   
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="89799-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="89799-105">Parameters</span></span>  
 `cbPublicKey`  
 <span data-ttu-id="89799-106">[in] Bayt cinsinden en büyük sayısını `pbPublicKey` dizi.</span><span class="sxs-lookup"><span data-stu-id="89799-106">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="89799-107">[out] Yazılan bayt sayısını gösteren bir işaretçi `pbPublicKey` dizi.</span><span class="sxs-lookup"><span data-stu-id="89799-107">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="89799-108">[out] Derlemenin ortak anahtarı içeren bir bayt dizisine bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="89799-108">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89799-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="89799-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="89799-110">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="89799-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89799-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="89799-111">Requirements</span></span>  
 <span data-ttu-id="89799-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89799-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89799-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="89799-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="89799-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89799-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89799-115">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89799-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89799-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="89799-116">See Also</span></span>  
 [<span data-ttu-id="89799-117">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="89799-117">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="89799-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="89799-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
