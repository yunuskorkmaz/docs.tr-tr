---
title: ICLRDataTarget::WriteVirtual Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.WriteVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::WriteVirtual
helpviewer_keywords:
- ICLRDataTarget::WriteVirtual method [.NET Framework debugging]
- WriteVirtual method [.NET Framework debugging]
ms.assetid: d627e8b7-a605-40ac-b9bb-da9a3f1b66d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 540f9d1a765ff46235f3c3d62f5da4a00b8ab85a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745486"
---
# <a name="iclrdatatargetwritevirtual-method"></a><span data-ttu-id="040c9-102">ICLRDataTarget::WriteVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="040c9-102">ICLRDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="040c9-103">Verileri belirtilen arabellek belirtilen sanal bellek adresini yazar.</span><span class="sxs-lookup"><span data-stu-id="040c9-103">Writes data from the specified buffer to the specified virtual memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="040c9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="040c9-104">Syntax</span></span>  
  
```  
HRESULT WriteVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [in, size_is(bytesRequested)]   
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesWritten  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="040c9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="040c9-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="040c9-106">[in] Sanal bellek adresi depolar CLRDATA_ADDRESS.</span><span class="sxs-lookup"><span data-stu-id="040c9-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="040c9-107">[in] Yazılacak veri depolayan arabellek için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="040c9-107">[in] A pointer to a buffer that stores the data to be written.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="040c9-108">[in] Yazılacak bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="040c9-108">[in] The number of bytes to be written.</span></span>  
  
 `bytesWritten`  
 <span data-ttu-id="040c9-109">[out] Gerçek yazılan bayt sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="040c9-109">[out] A pointer to the actual number of bytes that were written.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="040c9-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="040c9-110">Requirements</span></span>  
 <span data-ttu-id="040c9-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="040c9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="040c9-112">**Üst bilgi:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="040c9-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="040c9-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="040c9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="040c9-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="040c9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="040c9-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="040c9-115">See also</span></span>
- [<span data-ttu-id="040c9-116">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="040c9-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
