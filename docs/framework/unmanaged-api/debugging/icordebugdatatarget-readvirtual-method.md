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
ms.openlocfilehash: 4749bfee22e58ad7c3ca29ec992da88493ca2c5c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763847"
---
# <a name="icordebugdatatargetreadvirtual-method"></a><span data-ttu-id="7f010-102">ICorDebugDataTarget::ReadVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7f010-102">ICorDebugDataTarget::ReadVirtual Method</span></span>
<span data-ttu-id="7f010-103">Belirtilen adres'ten itibaren bitişik bellek bloğunu alır ve sağlanan arabellek döndürür.</span><span class="sxs-lookup"><span data-stu-id="7f010-103">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f010-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7f010-104">Syntax</span></span>  
  
```  
HRESULT ReadVirtual(  
    [in] CORDB_ADDRESS   address,  
    [out, size_is(bytesRequested), length_is(*pBytesRead)]  
          BYTE *     pBuffer,  
    [in]  ULONG32    bytesRequested,  
    [out] ULONG32 *  pBytesRead);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f010-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7f010-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="7f010-106">[in] İstenen bellek başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="7f010-106">[in] The start address of requested memory.</span></span>  
  
 `pbuffer`  
 <span data-ttu-id="7f010-107">[out] Bellek depolanacağı arabelleği.</span><span class="sxs-lookup"><span data-stu-id="7f010-107">[out] The buffer where the memory will be stored.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="7f010-108">[in] Hedef adres alınacağı bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="7f010-108">[in] The number of bytes to get from the target address.</span></span>  
  
 `pBytesRead`  
 <span data-ttu-id="7f010-109">[out] Hedef adres gerçekten okunan bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="7f010-109">[out] The number of bytes actually read from the target address.</span></span> <span data-ttu-id="7f010-110">Bu daha az olabilir `bytesRequested`.</span><span class="sxs-lookup"><span data-stu-id="7f010-110">This can be fewer than `bytesRequested`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f010-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7f010-111">Remarks</span></span>  
 <span data-ttu-id="7f010-112">(Belirtilen başlangıç adresindeki) ilk baytı okunabiliyorsa çağrı başarılı (uzunluğu, null ile sonlandırılmış dizeler gibi kendini açıklayan ile veri yapılarının verimli okuma desteklemek için) döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="7f010-112">If the first byte (at the specified start address) can be read, the call should return success (to support efficient reading of data structures with self-describing length, like null-terminated strings).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f010-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7f010-113">Requirements</span></span>  
 <span data-ttu-id="7f010-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f010-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f010-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7f010-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7f010-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7f010-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f010-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f010-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f010-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f010-118">See also</span></span>

- [<span data-ttu-id="7f010-119">ICorDebugDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7f010-119">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [<span data-ttu-id="7f010-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7f010-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="7f010-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="7f010-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
