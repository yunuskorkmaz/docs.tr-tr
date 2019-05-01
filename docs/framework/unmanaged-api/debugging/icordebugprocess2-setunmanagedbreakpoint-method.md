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
ms.openlocfilehash: b374720bd7bdad48222da006b809702de6462a62
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948854"
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a><span data-ttu-id="f7da5-102">ICorDebugProcess2::SetUnmanagedBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f7da5-102">ICorDebugProcess2::SetUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="f7da5-103">Belirtilen yerel görüntü uzaklığında yönetilmeyen bir kesme noktası ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f7da5-103">Sets an unmanaged breakpoint at the specified native image offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7da5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f7da5-104">Syntax</span></span>  
  
```  
HRESULT SetUnmanagedBreakpoint (  
    [in]  CORDB_ADDRESS    address,  
    [in]  ULONG32          bufsize,  
    [out, size_is(bufsize), length_is(*bufLen)]   
        BYTE               buffer[],  
    [out] ULONG32          *bufLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7da5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f7da5-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="f7da5-106">[in] A `CORDB_ADDRESS` nesnesini yerel görüntü uzaklığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f7da5-106">[in] A `CORDB_ADDRESS` object that specifies the native image offset.</span></span>  
  
 `bufsize`  
 <span data-ttu-id="f7da5-107">[in] Bayt cinsinden boyutu, `buffer` dizisi.</span><span class="sxs-lookup"><span data-stu-id="f7da5-107">[in] The size, in bytes, of the `buffer` array.</span></span>  
  
 `buffer`  
 <span data-ttu-id="f7da5-108">[out] Kesme noktası tarafından değiştirilen bir işlem kodu içeren bir dizi.</span><span class="sxs-lookup"><span data-stu-id="f7da5-108">[out] An array that contains the opcode that is replaced by the breakpoint.</span></span>  
  
 `bufLen`  
 <span data-ttu-id="f7da5-109">[out] Döndürülen bayt sayısı için bir işaretçi `buffer` dizisi.</span><span class="sxs-lookup"><span data-stu-id="f7da5-109">[out] A pointer to the number of bytes returned in the `buffer` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7da5-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f7da5-110">Remarks</span></span>  
 <span data-ttu-id="f7da5-111">Yerel görüntü uzaklığı ortak dil çalışma zamanı içinde (CLR) ise, kesme noktasına göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="f7da5-111">If the native image offset is within the common language runtime (CLR), the breakpoint will be ignored.</span></span> <span data-ttu-id="f7da5-112">Kesme noktası hata ayıklayıcı tarafından olarak ayarlandığında bir bant dışı kesme noktası göndermeyi önlemek CLR böylece.</span><span class="sxs-lookup"><span data-stu-id="f7da5-112">This allows the CLR to avoid dispatching an out-of-band breakpoint, when the breakpoint is set by the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7da5-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f7da5-113">Requirements</span></span>  
 <span data-ttu-id="f7da5-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7da5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7da5-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f7da5-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7da5-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7da5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7da5-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7da5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
