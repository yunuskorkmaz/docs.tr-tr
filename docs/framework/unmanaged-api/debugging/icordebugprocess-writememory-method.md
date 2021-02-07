---
description: ': ICorDebugProcess:: WriteMemory yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 6ea48aff2e1ea812d851a228976b458f58a60e14
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746631"
---
# <a name="icordebugprocesswritememory-method"></a><span data-ttu-id="50ed4-103">ICorDebugProcess::WriteMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50ed4-103">ICorDebugProcess::WriteMemory Method</span></span>

<span data-ttu-id="50ed4-104">Bu işlemdeki bir bellek alanına veri yazar.</span><span class="sxs-lookup"><span data-stu-id="50ed4-104">Writes data to an area of memory in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50ed4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="50ed4-105">Syntax</span></span>  
  
```cpp  
HRESULT WriteMemory(  
    [in]  CORDB_ADDRESS address,  
    [in]  DWORD size,  
    [in, size_is(size)] BYTE buffer[],  
    [out] SIZE_T *written);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50ed4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="50ed4-106">Parameters</span></span>  

 `address`  
 <span data-ttu-id="50ed4-107">'ndaki `CORDB_ADDRESS` Verilerin yazıldığı bellek alanının temel adresi olan bir değer.</span><span class="sxs-lookup"><span data-stu-id="50ed4-107">[in] A `CORDB_ADDRESS` value that is the base address of the memory area to which data is written.</span></span> <span data-ttu-id="50ed4-108">Veri aktarımı gerçekleşmeden önce, sistem, belirtilen boyuttaki bellek alanının temel adresten başlayarak, yazma için erişilebilir olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="50ed4-108">Before data transfer occurs, the system verifies that the memory area of the specified size, beginning at the base address, is accessible for writing.</span></span> <span data-ttu-id="50ed4-109">Erişilebilir değilse, yöntemi başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="50ed4-109">If it is not accessible, the method fails.</span></span>  
  
 `size`  
 <span data-ttu-id="50ed4-110">'ndaki Bellek alanına yazılacak baytların sayısı.</span><span class="sxs-lookup"><span data-stu-id="50ed4-110">[in] The number of bytes to be written to the memory area.</span></span>  
  
 `buffer`  
 <span data-ttu-id="50ed4-111">'ndaki Yazılacak verileri içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="50ed4-111">[in] A buffer that contains data to be written.</span></span>  
  
 `written`  
 <span data-ttu-id="50ed4-112">dışı Bu işlemdeki bellek alanına yazılan bayt sayısını alan bir değişken işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="50ed4-112">[out] A pointer to a variable that receives the number of bytes written to the memory area in this process.</span></span> <span data-ttu-id="50ed4-113">`written`Null ise, bu parametre yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="50ed4-113">If `written` is NULL, this parameter is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50ed4-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="50ed4-114">Remarks</span></span>  

 <span data-ttu-id="50ed4-115">Veriler, herhangi bir kesme noktası arkasında otomatik olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="50ed4-115">Data is automatically written behind any breakpoints.</span></span> <span data-ttu-id="50ed4-116">.NET Framework sürüm 2,0 ' de yerel hata ayıklayıcılar, yönerge akışına kesme noktaları eklemek için bu yöntemi kullanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="50ed4-116">In the .NET Framework version 2.0, native debuggers should not use this method to inject breakpoints into the instruction stream.</span></span> <span data-ttu-id="50ed4-117">Bunun yerine [ICorDebugProcess2:: SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="50ed4-117">Use [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) instead.</span></span>  
  
 <span data-ttu-id="50ed4-118">`WriteMemory`Yöntem yalnızca yönetilen kodun dışında kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="50ed4-118">The `WriteMemory` method should be used only outside of managed code.</span></span> <span data-ttu-id="50ed4-119">Yanlış kullanılırsa, bu yöntem çalışma zamanını bozabilir.</span><span class="sxs-lookup"><span data-stu-id="50ed4-119">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50ed4-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="50ed4-120">Requirements</span></span>  

 <span data-ttu-id="50ed4-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50ed4-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50ed4-122">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="50ed4-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="50ed4-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="50ed4-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50ed4-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50ed4-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
