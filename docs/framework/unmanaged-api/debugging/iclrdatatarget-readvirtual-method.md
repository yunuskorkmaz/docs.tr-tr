---
title: ICLRDataTarget::ReadVirtual Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.ReadVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::ReadVirtual
helpviewer_keywords:
- ReadVirtual method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::ReadVirtual method [.NET Framework debugging]
ms.assetid: da3769eb-1828-4aa1-b9ed-db4842136a43
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5c9080a588b96c5b89c280a0fb407952bd580f26
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404229"
---
# <a name="iclrdatatargetreadvirtual-method"></a><span data-ttu-id="d6edf-102">ICLRDataTarget::ReadVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d6edf-102">ICLRDataTarget::ReadVirtual Method</span></span>
<span data-ttu-id="d6edf-103">Verileri belirtilen sanal bellek adresinden belirtilen arabelleğe okur.</span><span class="sxs-lookup"><span data-stu-id="d6edf-103">Reads data from the specified virtual memory address into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6edf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d6edf-104">Syntax</span></span>  
  
```  
HRESULT ReadVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [out, size_is(bytesRequested), length_is(*bytesRead)]   
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesRead  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d6edf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d6edf-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="d6edf-106">[in] Sanal bellek adresi depolar CLRDATA_ADDRESS.</span><span class="sxs-lookup"><span data-stu-id="d6edf-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="d6edf-107">[out] Verileri alan bir arabellek için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d6edf-107">[out] A pointer to a buffer that receives the data.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="d6edf-108">[in] Arabellek uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="d6edf-108">[in] The length of the buffer.</span></span>  
  
 `bytesRead`  
 <span data-ttu-id="d6edf-109">[out] Bayt sayısı için bir işaretçi döndürdü.</span><span class="sxs-lookup"><span data-stu-id="d6edf-109">[out] A pointer to the number of bytes returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6edf-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d6edf-110">Requirements</span></span>  
 <span data-ttu-id="d6edf-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6edf-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6edf-112">**Başlık:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="d6edf-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="d6edf-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6edf-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6edf-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6edf-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6edf-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d6edf-115">See Also</span></span>  
 [<span data-ttu-id="d6edf-116">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6edf-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
