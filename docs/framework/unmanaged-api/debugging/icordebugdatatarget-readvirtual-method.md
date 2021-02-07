---
description: ': ICorDebugDataTarget:: ReadVirtual yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 4525ba1e5dc685813d963dab96879b886987f38f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710614"
---
# <a name="icordebugdatatargetreadvirtual-method"></a><span data-ttu-id="e0eda-103">ICorDebugDataTarget::ReadVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e0eda-103">ICorDebugDataTarget::ReadVirtual Method</span></span>

<span data-ttu-id="e0eda-104">Belirtilen adresten başlayarak bir ardışık bellek bloğunu alır ve sağlanan arabellekte döndürür.</span><span class="sxs-lookup"><span data-stu-id="e0eda-104">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0eda-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e0eda-105">Syntax</span></span>  
  
```cpp  
HRESULT ReadVirtual(  
    [in] CORDB_ADDRESS   address,  
    [out, size_is(bytesRequested), length_is(*pBytesRead)]  
          BYTE *     pBuffer,  
    [in]  ULONG32    bytesRequested,  
    [out] ULONG32 *  pBytesRead);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0eda-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e0eda-106">Parameters</span></span>  

 `address`  
 <span data-ttu-id="e0eda-107">'ndaki İstenen belleğin başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="e0eda-107">[in] The start address of requested memory.</span></span>  
  
 `pbuffer`  
 <span data-ttu-id="e0eda-108">dışı Belleğin depolanacağı arabellek.</span><span class="sxs-lookup"><span data-stu-id="e0eda-108">[out] The buffer where the memory will be stored.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="e0eda-109">'ndaki Hedef adresten alınacak bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="e0eda-109">[in] The number of bytes to get from the target address.</span></span>  
  
 `pBytesRead`  
 <span data-ttu-id="e0eda-110">dışı Hedef adresten gerçekten okunan bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="e0eda-110">[out] The number of bytes actually read from the target address.</span></span> <span data-ttu-id="e0eda-111">Bu daha az olabilir `bytesRequested` .</span><span class="sxs-lookup"><span data-stu-id="e0eda-111">This can be fewer than `bytesRequested`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0eda-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e0eda-112">Remarks</span></span>  

 <span data-ttu-id="e0eda-113">İlk bayt (belirtilen başlangıç adresinde) okunurken, çağrının başarılı döndürmesi gerekir (null ile sonlandırılmış dizeler gibi, kendi kendine tanımlayan uzunlukla veri yapılarının etkili şekilde okunmasını desteklemek için).</span><span class="sxs-lookup"><span data-stu-id="e0eda-113">If the first byte (at the specified start address) can be read, the call should return success (to support efficient reading of data structures with self-describing length, like null-terminated strings).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0eda-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e0eda-114">Requirements</span></span>  

 <span data-ttu-id="e0eda-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0eda-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0eda-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e0eda-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0eda-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e0eda-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0eda-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0eda-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0eda-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0eda-119">See also</span></span>

- [<span data-ttu-id="e0eda-120">ICorDebugDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e0eda-120">ICorDebugDataTarget Interface</span></span>](icordebugdatatarget-interface.md)
- [<span data-ttu-id="e0eda-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e0eda-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="e0eda-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="e0eda-122">Debugging</span></span>](index.md)
