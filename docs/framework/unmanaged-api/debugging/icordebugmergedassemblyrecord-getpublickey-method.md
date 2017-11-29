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
ms.openlocfilehash: 7d379f0df70690501920a9ba5b40d560b10a7cb7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="707d7-102">ICorDebugMergedAssemblyRecord::GetPublicKey yöntemi</span><span class="sxs-lookup"><span data-stu-id="707d7-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>
<span data-ttu-id="707d7-103">Derlemenin ortak anahtarı alır.</span><span class="sxs-lookup"><span data-stu-id="707d7-103">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="707d7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="707d7-104">Syntax</span></span>  
  
```  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,   
   [out] ULONG32 *pcbPublicKey,   
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="707d7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="707d7-105">Parameters</span></span>  
 `cbPublicKey`  
 <span data-ttu-id="707d7-106">[in] Bayt cinsinden en büyük sayısını `pbPublicKey` dizi.</span><span class="sxs-lookup"><span data-stu-id="707d7-106">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="707d7-107">[out] Yazılan bayt sayısını gösteren bir işaretçi `pbPublicKey` dizi.</span><span class="sxs-lookup"><span data-stu-id="707d7-107">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="707d7-108">[out] Derlemenin ortak anahtarı içeren bir bayt dizisine bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="707d7-108">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="707d7-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="707d7-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="707d7-110">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="707d7-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="707d7-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="707d7-111">Requirements</span></span>  
 <span data-ttu-id="707d7-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="707d7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="707d7-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="707d7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="707d7-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="707d7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="707d7-115">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="707d7-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="707d7-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="707d7-116">See Also</span></span>  
 [<span data-ttu-id="707d7-117">ICorDebugMergedAssemblyRecord arabirimi</span><span class="sxs-lookup"><span data-stu-id="707d7-117">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="707d7-118">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="707d7-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
