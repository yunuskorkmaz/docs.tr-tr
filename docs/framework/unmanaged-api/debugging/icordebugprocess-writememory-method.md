---
title: "ICorDebugProcess::WriteMemory Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.WriteMemory
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::WriteMemory
helpviewer_keywords:
- ICorDebugProcess::WriteMemory method [.NET Framework debugging]
- WriteMemory method [.NET Framework debugging]
ms.assetid: d5c07d86-045d-4391-893b-0bcd2959f90e
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 053c6bf5f451377308f4defbeb6eff9525c4332e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocesswritememory-method"></a><span data-ttu-id="52065-102">ICorDebugProcess::WriteMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="52065-102">ICorDebugProcess::WriteMemory Method</span></span>
<span data-ttu-id="52065-103">Bu işlem bellekte bir alanına veri yazar.</span><span class="sxs-lookup"><span data-stu-id="52065-103">Writes data to an area of memory in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52065-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="52065-104">Syntax</span></span>  
  
```  
HRESULT WriteMemory(  
    [in]  CORDB_ADDRESS address,  
    [in]  DWORD size,  
    [in, size_is(size)] BYTE buffer[],  
    [out] SIZE_T *written);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="52065-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="52065-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="52065-106">[in] A `CORDB_ADDRESS` hangi veriler için bellek alanı taban adresini değer yazılır.</span><span class="sxs-lookup"><span data-stu-id="52065-106">[in] A `CORDB_ADDRESS` value that is the base address of the memory area to which data is written.</span></span> <span data-ttu-id="52065-107">Veri aktarımı oluşmadan önce sistem temel adresinde başlayarak belirtilen boyut, bellek alanını yazma için erişilebilir olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="52065-107">Before data transfer occurs, the system verifies that the memory area of the specified size, beginning at the base address, is accessible for writing.</span></span> <span data-ttu-id="52065-108">Erişilebilir durumda değilse, yöntem başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="52065-108">If it is not accessible, the method fails.</span></span>  
  
 `size`  
 <span data-ttu-id="52065-109">[in] Bellek alanı yazılacak bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="52065-109">[in] The number of bytes to be written to the memory area.</span></span>  
  
 `buffer`  
 <span data-ttu-id="52065-110">[in] Yazılacak veriler içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="52065-110">[in] A buffer that contains data to be written.</span></span>  
  
 `written`  
 <span data-ttu-id="52065-111">[out] Bu işlem bellek alanına yazılan bayt sayısı alan bir değişken için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="52065-111">[out] A pointer to a variable that receives the number of bytes written to the memory area in this process.</span></span> <span data-ttu-id="52065-112">Varsa `written` null, bu parametre yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="52065-112">If `written` is NULL, this parameter is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52065-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="52065-113">Remarks</span></span>  
 <span data-ttu-id="52065-114">Veriler otomatik olarak tüm kesme noktalarını yazılır.</span><span class="sxs-lookup"><span data-stu-id="52065-114">Data is automatically written behind any breakpoints.</span></span> <span data-ttu-id="52065-115">.NET Framework sürüm 2. 0'da, yerel hata ayıklayıcıları bu yöntem yönerge akışa kesme noktaları eklemesine kullanmamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="52065-115">In the .NET Framework version 2.0, native debuggers should not use this method to inject breakpoints into the instruction stream.</span></span> <span data-ttu-id="52065-116">Kullanım [Icordebugprocess2::setunmanagedbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) yerine.</span><span class="sxs-lookup"><span data-stu-id="52065-116">Use [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) instead.</span></span>  
  
 <span data-ttu-id="52065-117">`WriteMemory` Yöntemi yalnızca yönetilen kod dışında kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="52065-117">The `WriteMemory` method should be used only outside of managed code.</span></span> <span data-ttu-id="52065-118">Bu yöntem, yanlış kullandıysanız çalışma zamanı bozabilir.</span><span class="sxs-lookup"><span data-stu-id="52065-118">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52065-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="52065-119">Requirements</span></span>  
 <span data-ttu-id="52065-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52065-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52065-121">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="52065-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="52065-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52065-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52065-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52065-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
