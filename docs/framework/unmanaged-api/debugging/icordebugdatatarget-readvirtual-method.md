---
title: "ICorDebugDataTarget::ReadVirtual Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugDataTarget.ReadVirtual Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::ReadVirtual
helpviewer_keywords:
- ICorDebugDataTarget::ReadVirtual method [.NET Framework debugging]
- ReadVirtual method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: 55e57640-b3d2-413d-b4f4-fbc27fb8e37c
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a406af14d4cb5612009972542c0efe9c1b5f62cc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatargetreadvirtual-method"></a><span data-ttu-id="fe167-102">ICorDebugDataTarget::ReadVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe167-102">ICorDebugDataTarget::ReadVirtual Method</span></span>
<span data-ttu-id="fe167-103">Belirtilen adresten başlayarak bitişik bellek bloğu alır ve sağlanan arabellek döndürür.</span><span class="sxs-lookup"><span data-stu-id="fe167-103">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe167-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fe167-104">Syntax</span></span>  
  
```  
HRESULT ReadVirtual(  
    [in] CORDB_ADDRESS   address,  
    [out, size_is(bytesRequested), length_is(*pBytesRead)]  
          BYTE *     pBuffer,  
    [in]  ULONG32    bytesRequested,  
    [out] ULONG32 *  pBytesRead);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fe167-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fe167-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="fe167-106">[in] İstenen bellek başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="fe167-106">[in] The start address of requested memory.</span></span>  
  
 `pbuffer`  
 <span data-ttu-id="fe167-107">[out] Bellek depolanacağı arabelleği.</span><span class="sxs-lookup"><span data-stu-id="fe167-107">[out] The buffer where the memory will be stored.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="fe167-108">[in] Hedef adres almak için bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="fe167-108">[in] The number of bytes to get from the target address.</span></span>  
  
 `pBytesRead`  
 <span data-ttu-id="fe167-109">[out] Hedef adres gerçekte okunan bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="fe167-109">[out] The number of bytes actually read from the target address.</span></span> <span data-ttu-id="fe167-110">Bu daha az olabilir `bytesRequested`.</span><span class="sxs-lookup"><span data-stu-id="fe167-110">This can be fewer than `bytesRequested`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe167-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fe167-111">Remarks</span></span>  
 <span data-ttu-id="fe167-112">İlk bayta kalan (belirtilen başlangıç adresindeki) okuyabilir, çağrı (null ile sonlandırılmış dizeler gibi uzunluğu kendiliğinden açıklayıcı ile veri yapılarının verimli okuma desteklemek için) başarı döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="fe167-112">If the first byte (at the specified start address) can be read, the call should return success (to support efficient reading of data structures with self-describing length, like null-terminated strings).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe167-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fe167-113">Requirements</span></span>  
 <span data-ttu-id="fe167-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe167-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe167-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fe167-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fe167-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe167-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe167-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe167-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe167-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fe167-118">See Also</span></span>  
 [<span data-ttu-id="fe167-119">ICorDebugDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe167-119">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 [<span data-ttu-id="fe167-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fe167-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="fe167-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="fe167-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
