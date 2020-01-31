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
ms.openlocfilehash: 20cea94961a250c3981d892910da1dcee20a060b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783733"
---
# <a name="icordebugdatatargetreadvirtual-method"></a><span data-ttu-id="b3d9a-102">ICorDebugDataTarget::ReadVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b3d9a-102">ICorDebugDataTarget::ReadVirtual Method</span></span>
<span data-ttu-id="b3d9a-103">Belirtilen adresten başlayarak bir ardışık bellek bloğunu alır ve sağlanan arabellekte döndürür.</span><span class="sxs-lookup"><span data-stu-id="b3d9a-103">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3d9a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b3d9a-104">Syntax</span></span>  
  
```cpp  
HRESULT ReadVirtual(  
    [in] CORDB_ADDRESS   address,  
    [out, size_is(bytesRequested), length_is(*pBytesRead)]  
          BYTE *     pBuffer,  
    [in]  ULONG32    bytesRequested,  
    [out] ULONG32 *  pBytesRead);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3d9a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b3d9a-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="b3d9a-106">'ndaki İstenen belleğin başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="b3d9a-106">[in] The start address of requested memory.</span></span>  
  
 `pbuffer`  
 <span data-ttu-id="b3d9a-107">dışı Belleğin depolanacağı arabellek.</span><span class="sxs-lookup"><span data-stu-id="b3d9a-107">[out] The buffer where the memory will be stored.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="b3d9a-108">'ndaki Hedef adresten alınacak bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="b3d9a-108">[in] The number of bytes to get from the target address.</span></span>  
  
 `pBytesRead`  
 <span data-ttu-id="b3d9a-109">dışı Hedef adresten gerçekten okunan bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="b3d9a-109">[out] The number of bytes actually read from the target address.</span></span> <span data-ttu-id="b3d9a-110">Bu, `bytesRequested`daha az olabilir.</span><span class="sxs-lookup"><span data-stu-id="b3d9a-110">This can be fewer than `bytesRequested`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3d9a-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b3d9a-111">Remarks</span></span>  
 <span data-ttu-id="b3d9a-112">İlk bayt (belirtilen başlangıç adresinde) okunurken, çağrının başarılı döndürmesi gerekir (null ile sonlandırılmış dizeler gibi, kendi kendine tanımlayan uzunlukla veri yapılarının etkili şekilde okunmasını desteklemek için).</span><span class="sxs-lookup"><span data-stu-id="b3d9a-112">If the first byte (at the specified start address) can be read, the call should return success (to support efficient reading of data structures with self-describing length, like null-terminated strings).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3d9a-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b3d9a-113">Requirements</span></span>  
 <span data-ttu-id="b3d9a-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3d9a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3d9a-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b3d9a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b3d9a-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b3d9a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3d9a-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3d9a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3d9a-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3d9a-118">See also</span></span>

- [<span data-ttu-id="b3d9a-119">ICorDebugDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b3d9a-119">ICorDebugDataTarget Interface</span></span>](icordebugdatatarget-interface.md)
- [<span data-ttu-id="b3d9a-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b3d9a-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="b3d9a-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="b3d9a-121">Debugging</span></span>](index.md)
