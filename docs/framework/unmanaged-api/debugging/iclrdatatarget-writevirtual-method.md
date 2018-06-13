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
ms.openlocfilehash: e55bc18c7a41e235d1ba6274067c45c26dc7262a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405466"
---
# <a name="iclrdatatargetwritevirtual-method"></a><span data-ttu-id="95be3-102">ICLRDataTarget::WriteVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="95be3-102">ICLRDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="95be3-103">Verileri belirtilen arabelleğinden belirtilen sanal bellek adresi yazar.</span><span class="sxs-lookup"><span data-stu-id="95be3-103">Writes data from the specified buffer to the specified virtual memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95be3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="95be3-104">Syntax</span></span>  
  
```  
HRESULT WriteVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [in, size_is(bytesRequested)]   
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesWritten  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="95be3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="95be3-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="95be3-106">[in] Sanal bellek adresi depolar CLRDATA_ADDRESS.</span><span class="sxs-lookup"><span data-stu-id="95be3-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="95be3-107">[in] Yazılacak verilerini depolayan bir arabellek için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="95be3-107">[in] A pointer to a buffer that stores the data to be written.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="95be3-108">[in] Yazılacak bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="95be3-108">[in] The number of bytes to be written.</span></span>  
  
 `bytesWritten`  
 <span data-ttu-id="95be3-109">[out] Gerçek yazılan bayt sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="95be3-109">[out] A pointer to the actual number of bytes that were written.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95be3-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="95be3-110">Requirements</span></span>  
 <span data-ttu-id="95be3-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95be3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95be3-112">**Başlık:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="95be3-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="95be3-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95be3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95be3-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95be3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95be3-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="95be3-115">See Also</span></span>  
 [<span data-ttu-id="95be3-116">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="95be3-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
