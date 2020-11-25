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
ms.openlocfilehash: 3455397345451cc0c39cc98a0ea4374eab8350a8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703389"
---
# <a name="iclrdatatargetreadvirtual-method"></a><span data-ttu-id="a3ec3-102">ICLRDataTarget::ReadVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a3ec3-102">ICLRDataTarget::ReadVirtual Method</span></span>

<span data-ttu-id="a3ec3-103">Belirtilen sanal bellek adresinden belirtilen arabelleğe verileri okur.</span><span class="sxs-lookup"><span data-stu-id="a3ec3-103">Reads data from the specified virtual memory address into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3ec3-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a3ec3-104">Syntax</span></span>  
  
```cpp  
HRESULT ReadVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [out, size_is(bytesRequested), length_is(*bytesRead)]
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3ec3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a3ec3-105">Parameters</span></span>  

 `address`  
 <span data-ttu-id="a3ec3-106">'ndaki Sanal bellek adresini depolayan bir CLRDATA_ADDRESS.</span><span class="sxs-lookup"><span data-stu-id="a3ec3-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="a3ec3-107">dışı Verileri alan bir arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a3ec3-107">[out] A pointer to a buffer that receives the data.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="a3ec3-108">'ndaki Arabelleğin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="a3ec3-108">[in] The length of the buffer.</span></span>  
  
 `bytesRead`  
 <span data-ttu-id="a3ec3-109">dışı Döndürülen bayt sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a3ec3-109">[out] A pointer to the number of bytes returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3ec3-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a3ec3-110">Requirements</span></span>  

 <span data-ttu-id="a3ec3-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3ec3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3ec3-112">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="a3ec3-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="a3ec3-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a3ec3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3ec3-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3ec3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3ec3-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3ec3-115">See also</span></span>

- [<span data-ttu-id="a3ec3-116">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a3ec3-116">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
