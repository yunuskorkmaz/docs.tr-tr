---
description: ': ICLRDataTarget:: ReadVirtual yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 740a89c95092cfad7974d6bc708c5d8b0d2a9172
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738214"
---
# <a name="iclrdatatargetreadvirtual-method"></a><span data-ttu-id="31221-103">ICLRDataTarget::ReadVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="31221-103">ICLRDataTarget::ReadVirtual Method</span></span>

<span data-ttu-id="31221-104">Belirtilen sanal bellek adresinden belirtilen arabelleğe verileri okur.</span><span class="sxs-lookup"><span data-stu-id="31221-104">Reads data from the specified virtual memory address into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31221-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="31221-105">Syntax</span></span>  
  
```cpp  
HRESULT ReadVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [out, size_is(bytesRequested), length_is(*bytesRead)]
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31221-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="31221-106">Parameters</span></span>  

 `address`  
 <span data-ttu-id="31221-107">'ndaki Sanal bellek adresini depolayan bir CLRDATA_ADDRESS.</span><span class="sxs-lookup"><span data-stu-id="31221-107">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="31221-108">dışı Verileri alan bir arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="31221-108">[out] A pointer to a buffer that receives the data.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="31221-109">'ndaki Arabelleğin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="31221-109">[in] The length of the buffer.</span></span>  
  
 `bytesRead`  
 <span data-ttu-id="31221-110">dışı Döndürülen bayt sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="31221-110">[out] A pointer to the number of bytes returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31221-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="31221-111">Requirements</span></span>  

 <span data-ttu-id="31221-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31221-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31221-113">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="31221-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="31221-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="31221-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31221-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31221-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31221-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31221-116">See also</span></span>

- [<span data-ttu-id="31221-117">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31221-117">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
