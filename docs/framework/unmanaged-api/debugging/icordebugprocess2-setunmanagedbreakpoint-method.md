---
title: ICorDebugProcess2::SetUnmanagedBreakpoint Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.SetUnmanagedBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint
helpviewer_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint method [.NET Framework debugging]
- SetUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 93829d15-d942-4e2d-b7a4-dfc9d7fb96be
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f16a5d1bad80a5aad8573508aab5fbf98c8c2a03
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736829"
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a><span data-ttu-id="aeeda-102">ICorDebugProcess2::SetUnmanagedBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aeeda-102">ICorDebugProcess2::SetUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="aeeda-103">Belirtilen yerel görüntü uzaklığında yönetilmeyen bir kesme noktası ayarlar.</span><span class="sxs-lookup"><span data-stu-id="aeeda-103">Sets an unmanaged breakpoint at the specified native image offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aeeda-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aeeda-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmanagedBreakpoint (  
    [in]  CORDB_ADDRESS    address,  
    [in]  ULONG32          bufsize,  
    [out, size_is(bufsize), length_is(*bufLen)]   
        BYTE               buffer[],  
    [out] ULONG32          *bufLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aeeda-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aeeda-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="aeeda-106">[in] A `CORDB_ADDRESS` nesnesini yerel görüntü uzaklığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="aeeda-106">[in] A `CORDB_ADDRESS` object that specifies the native image offset.</span></span>  
  
 `bufsize`  
 <span data-ttu-id="aeeda-107">[in] Bayt cinsinden boyutu, `buffer` dizisi.</span><span class="sxs-lookup"><span data-stu-id="aeeda-107">[in] The size, in bytes, of the `buffer` array.</span></span>  
  
 `buffer`  
 <span data-ttu-id="aeeda-108">[out] Kesme noktası tarafından değiştirilen bir işlem kodu içeren bir dizi.</span><span class="sxs-lookup"><span data-stu-id="aeeda-108">[out] An array that contains the opcode that is replaced by the breakpoint.</span></span>  
  
 `bufLen`  
 <span data-ttu-id="aeeda-109">[out] Döndürülen bayt sayısı için bir işaretçi `buffer` dizisi.</span><span class="sxs-lookup"><span data-stu-id="aeeda-109">[out] A pointer to the number of bytes returned in the `buffer` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aeeda-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aeeda-110">Remarks</span></span>  
 <span data-ttu-id="aeeda-111">Yerel görüntü uzaklığı ortak dil çalışma zamanı içinde (CLR) ise, kesme noktasına göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="aeeda-111">If the native image offset is within the common language runtime (CLR), the breakpoint will be ignored.</span></span> <span data-ttu-id="aeeda-112">Kesme noktası hata ayıklayıcı tarafından olarak ayarlandığında bir bant dışı kesme noktası göndermeyi önlemek CLR böylece.</span><span class="sxs-lookup"><span data-stu-id="aeeda-112">This allows the CLR to avoid dispatching an out-of-band breakpoint, when the breakpoint is set by the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aeeda-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aeeda-113">Requirements</span></span>  
 <span data-ttu-id="aeeda-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aeeda-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aeeda-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aeeda-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aeeda-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aeeda-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aeeda-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aeeda-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
