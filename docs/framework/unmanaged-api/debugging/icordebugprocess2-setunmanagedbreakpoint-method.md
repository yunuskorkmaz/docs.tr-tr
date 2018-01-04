---
title: "ICorDebugProcess2::SetUnmanagedBreakpoint Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess2.SetUnmanagedBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess2::SetUnmanagedBreakpoint
helpviewer_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint method [.NET Framework debugging]
- SetUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 93829d15-d942-4e2d-b7a4-dfc9d7fb96be
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 825917d48aaab5d9d5ce482fa600ca02efa158ce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a><span data-ttu-id="39883-102">ICorDebugProcess2::SetUnmanagedBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="39883-102">ICorDebugProcess2::SetUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="39883-103">Yönetilmeyen bir kesme noktası belirtilen yerel görüntü uzaklığı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="39883-103">Sets an unmanaged breakpoint at the specified native image offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39883-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="39883-104">Syntax</span></span>  
  
```  
HRESULT SetUnmanagedBreakpoint (  
    [in]  CORDB_ADDRESS    address,  
    [in]  ULONG32          bufsize,  
    [out, size_is(bufsize), length_is(*bufLen)]   
        BYTE               buffer[],  
    [out] ULONG32          *bufLen  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="39883-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="39883-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="39883-106">[in] A `CORDB_ADDRESS` nesne yerel görüntü uzaklığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="39883-106">[in] A `CORDB_ADDRESS` object that specifies the native image offset.</span></span>  
  
 `bufsize`  
 <span data-ttu-id="39883-107">[in] Bayt olarak boyutu, `buffer` dizi.</span><span class="sxs-lookup"><span data-stu-id="39883-107">[in] The size, in bytes, of the `buffer` array.</span></span>  
  
 `buffer`  
 <span data-ttu-id="39883-108">[out] Kesme noktası tarafından değiştirilir işlem kodu içeren bir dizi.</span><span class="sxs-lookup"><span data-stu-id="39883-108">[out] An array that contains the opcode that is replaced by the breakpoint.</span></span>  
  
 `bufLen`  
 <span data-ttu-id="39883-109">[out] Döndürülen bayt sayısı için bir işaretçi `buffer` dizi.</span><span class="sxs-lookup"><span data-stu-id="39883-109">[out] A pointer to the number of bytes returned in the `buffer` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39883-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="39883-110">Remarks</span></span>  
 <span data-ttu-id="39883-111">Yerel görüntü uzaklık ortak dil çalışma zamanı içinde (CLR) ise, kesme yoksayılacak.</span><span class="sxs-lookup"><span data-stu-id="39883-111">If the native image offset is within the common language runtime (CLR), the breakpoint will be ignored.</span></span> <span data-ttu-id="39883-112">Bu kesme hata ayıklayıcı ayarlandığında, bant dışı kesme göndermeyi önlemek CLR sağlar.</span><span class="sxs-lookup"><span data-stu-id="39883-112">This allows the CLR to avoid dispatching an out-of-band breakpoint, when the breakpoint is set by the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39883-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="39883-113">Requirements</span></span>  
 <span data-ttu-id="39883-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39883-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39883-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="39883-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="39883-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="39883-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39883-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39883-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
