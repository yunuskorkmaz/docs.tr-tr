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
ms.openlocfilehash: 0a433ccb81ef62ac92a4553a838a2c98a04fc7c1
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212821"
---
# <a name="icordebugprocesswritememory-method"></a><span data-ttu-id="692de-102">ICorDebugProcess::WriteMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="692de-102">ICorDebugProcess::WriteMemory Method</span></span>
<span data-ttu-id="692de-103">Bu işlemdeki bir bellek alanına veri yazar.</span><span class="sxs-lookup"><span data-stu-id="692de-103">Writes data to an area of memory in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="692de-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="692de-104">Syntax</span></span>  
  
```cpp  
HRESULT WriteMemory(  
    [in]  CORDB_ADDRESS address,  
    [in]  DWORD size,  
    [in, size_is(size)] BYTE buffer[],  
    [out] SIZE_T *written);  
```  
  
## <a name="parameters"></a><span data-ttu-id="692de-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="692de-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="692de-106">'ndaki `CORDB_ADDRESS`Verilerin yazıldığı bellek alanının temel adresi olan bir değer.</span><span class="sxs-lookup"><span data-stu-id="692de-106">[in] A `CORDB_ADDRESS` value that is the base address of the memory area to which data is written.</span></span> <span data-ttu-id="692de-107">Veri aktarımı gerçekleşmeden önce, sistem, belirtilen boyuttaki bellek alanının temel adresten başlayarak, yazma için erişilebilir olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="692de-107">Before data transfer occurs, the system verifies that the memory area of the specified size, beginning at the base address, is accessible for writing.</span></span> <span data-ttu-id="692de-108">Erişilebilir değilse, yöntemi başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="692de-108">If it is not accessible, the method fails.</span></span>  
  
 `size`  
 <span data-ttu-id="692de-109">'ndaki Bellek alanına yazılacak baytların sayısı.</span><span class="sxs-lookup"><span data-stu-id="692de-109">[in] The number of bytes to be written to the memory area.</span></span>  
  
 `buffer`  
 <span data-ttu-id="692de-110">'ndaki Yazılacak verileri içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="692de-110">[in] A buffer that contains data to be written.</span></span>  
  
 `written`  
 <span data-ttu-id="692de-111">dışı Bu işlemdeki bellek alanına yazılan bayt sayısını alan bir değişken işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="692de-111">[out] A pointer to a variable that receives the number of bytes written to the memory area in this process.</span></span> <span data-ttu-id="692de-112">`written`Null ise, bu parametre yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="692de-112">If `written` is NULL, this parameter is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="692de-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="692de-113">Remarks</span></span>  
 <span data-ttu-id="692de-114">Veriler, herhangi bir kesme noktası arkasında otomatik olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="692de-114">Data is automatically written behind any breakpoints.</span></span> <span data-ttu-id="692de-115">.NET Framework sürüm 2,0 ' de yerel hata ayıklayıcılar, yönerge akışına kesme noktaları eklemek için bu yöntemi kullanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="692de-115">In the .NET Framework version 2.0, native debuggers should not use this method to inject breakpoints into the instruction stream.</span></span> <span data-ttu-id="692de-116">Bunun yerine [ICorDebugProcess2:: SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="692de-116">Use [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) instead.</span></span>  
  
 <span data-ttu-id="692de-117">`WriteMemory`Yöntem yalnızca yönetilen kodun dışında kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="692de-117">The `WriteMemory` method should be used only outside of managed code.</span></span> <span data-ttu-id="692de-118">Yanlış kullanılırsa, bu yöntem çalışma zamanını bozabilir.</span><span class="sxs-lookup"><span data-stu-id="692de-118">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="692de-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="692de-119">Requirements</span></span>  
 <span data-ttu-id="692de-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="692de-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="692de-121">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="692de-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="692de-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="692de-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="692de-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="692de-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
