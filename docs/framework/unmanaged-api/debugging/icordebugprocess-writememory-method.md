---
title: ICorDebugProcess::WriteMemory Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.WriteMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::WriteMemory
helpviewer_keywords:
- ICorDebugProcess::WriteMemory method [.NET Framework debugging]
- WriteMemory method [.NET Framework debugging]
ms.assetid: d5c07d86-045d-4391-893b-0bcd2959f90e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e9d640fb1c9dae5bb195baa504e560ba8e45821
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497099"
---
# <a name="icordebugprocesswritememory-method"></a><span data-ttu-id="8b230-102">ICorDebugProcess::WriteMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b230-102">ICorDebugProcess::WriteMemory Method</span></span>
<span data-ttu-id="8b230-103">Bu işlem belleği veri yazar.</span><span class="sxs-lookup"><span data-stu-id="8b230-103">Writes data to an area of memory in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b230-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8b230-104">Syntax</span></span>  
  
```  
HRESULT WriteMemory(  
    [in]  CORDB_ADDRESS address,  
    [in]  DWORD size,  
    [in, size_is(size)] BYTE buffer[],  
    [out] SIZE_T *written);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b230-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8b230-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="8b230-106">[in] A `CORDB_ADDRESS` hangi verilere bellek alanı taban adresini değer yazılır.</span><span class="sxs-lookup"><span data-stu-id="8b230-106">[in] A `CORDB_ADDRESS` value that is the base address of the memory area to which data is written.</span></span> <span data-ttu-id="8b230-107">Veri aktarımı gerçekleşmeden önce sistem temel adreste başlayan belirtilen boyut, bellek alanını yazma için erişilebilir olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="8b230-107">Before data transfer occurs, the system verifies that the memory area of the specified size, beginning at the base address, is accessible for writing.</span></span> <span data-ttu-id="8b230-108">Erişilebilir durumda değilse, yöntem başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="8b230-108">If it is not accessible, the method fails.</span></span>  
  
 `size`  
 <span data-ttu-id="8b230-109">[in] Bellek alanına yazılacak bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="8b230-109">[in] The number of bytes to be written to the memory area.</span></span>  
  
 `buffer`  
 <span data-ttu-id="8b230-110">[in] Yazılacak veriler içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="8b230-110">[in] A buffer that contains data to be written.</span></span>  
  
 `written`  
 <span data-ttu-id="8b230-111">[out] Bu işlem bellek alanında yazılan bayt sayısını alır bir değişken için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8b230-111">[out] A pointer to a variable that receives the number of bytes written to the memory area in this process.</span></span> <span data-ttu-id="8b230-112">Varsa `written` NULL ise bu parametre yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="8b230-112">If `written` is NULL, this parameter is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b230-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8b230-113">Remarks</span></span>  
 <span data-ttu-id="8b230-114">Veriler herhangi bir kesme noktası otomatik olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="8b230-114">Data is automatically written behind any breakpoints.</span></span> <span data-ttu-id="8b230-115">.NET Framework sürüm 2. 0'da, yerel hata ayıklayıcılarının bu yöntem kesme noktaları yönerge akımına eklenecek kullanmamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8b230-115">In the .NET Framework version 2.0, native debuggers should not use this method to inject breakpoints into the instruction stream.</span></span> <span data-ttu-id="8b230-116">Kullanım [Icordebugprocess2::setunmanagedbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) yerine.</span><span class="sxs-lookup"><span data-stu-id="8b230-116">Use [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) instead.</span></span>  
  
 <span data-ttu-id="8b230-117">`WriteMemory` Yöntemi yalnızca yönetilen kod dışında kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8b230-117">The `WriteMemory` method should be used only outside of managed code.</span></span> <span data-ttu-id="8b230-118">Bu yöntem, çalışma zamanı yanlış kullandıysanız bozabilir.</span><span class="sxs-lookup"><span data-stu-id="8b230-118">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b230-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8b230-119">Requirements</span></span>  
 <span data-ttu-id="8b230-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b230-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b230-121">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8b230-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b230-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b230-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b230-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b230-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
