---
title: ICorDebugDataTarget::ReadVirtual Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8bc807906af67350f309a4fc9439899cea328be8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54575495"
---
# <a name="icordebugdatatargetreadvirtual-method"></a><span data-ttu-id="5105f-102">ICorDebugDataTarget::ReadVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5105f-102">ICorDebugDataTarget::ReadVirtual Method</span></span>
<span data-ttu-id="5105f-103">Belirtilen adres'ten itibaren bitişik bellek bloğunu alır ve sağlanan arabellek döndürür.</span><span class="sxs-lookup"><span data-stu-id="5105f-103">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5105f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5105f-104">Syntax</span></span>  
  
```  
HRESULT ReadVirtual(  
    [in] CORDB_ADDRESS   address,  
    [out, size_is(bytesRequested), length_is(*pBytesRead)]  
          BYTE *     pBuffer,  
    [in]  ULONG32    bytesRequested,  
    [out] ULONG32 *  pBytesRead);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5105f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5105f-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="5105f-106">[in] İstenen bellek başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="5105f-106">[in] The start address of requested memory.</span></span>  
  
 `pbuffer`  
 <span data-ttu-id="5105f-107">[out] Bellek depolanacağı arabelleği.</span><span class="sxs-lookup"><span data-stu-id="5105f-107">[out] The buffer where the memory will be stored.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="5105f-108">[in] Hedef adres alınacağı bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="5105f-108">[in] The number of bytes to get from the target address.</span></span>  
  
 `pBytesRead`  
 <span data-ttu-id="5105f-109">[out] Hedef adres gerçekten okunan bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="5105f-109">[out] The number of bytes actually read from the target address.</span></span> <span data-ttu-id="5105f-110">Bu daha az olabilir `bytesRequested`.</span><span class="sxs-lookup"><span data-stu-id="5105f-110">This can be fewer than `bytesRequested`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5105f-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5105f-111">Remarks</span></span>  
 <span data-ttu-id="5105f-112">(Belirtilen başlangıç adresindeki) ilk baytı okunabiliyorsa çağrı başarılı (uzunluğu, null ile sonlandırılmış dizeler gibi kendini açıklayan ile veri yapılarının verimli okuma desteklemek için) döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="5105f-112">If the first byte (at the specified start address) can be read, the call should return success (to support efficient reading of data structures with self-describing length, like null-terminated strings).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5105f-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5105f-113">Requirements</span></span>  
 <span data-ttu-id="5105f-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5105f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5105f-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5105f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5105f-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5105f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5105f-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5105f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5105f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5105f-118">See also</span></span>
- [<span data-ttu-id="5105f-119">ICorDebugDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5105f-119">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [<span data-ttu-id="5105f-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5105f-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="5105f-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="5105f-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
