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
ms.openlocfilehash: ffab2762fd86e95c3272ca456039028e0897bc41
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137173"
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a><span data-ttu-id="bedd4-102">ICorDebugProcess2::SetUnmanagedBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bedd4-102">ICorDebugProcess2::SetUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="bedd4-103">Belirtilen yerel görüntü uzaklığında yönetilmeyen bir kesme noktası ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bedd4-103">Sets an unmanaged breakpoint at the specified native image offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bedd4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bedd4-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmanagedBreakpoint (  
    [in]  CORDB_ADDRESS    address,  
    [in]  ULONG32          bufsize,  
    [out, size_is(bufsize), length_is(*bufLen)]   
        BYTE               buffer[],  
    [out] ULONG32          *bufLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bedd4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bedd4-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="bedd4-106">'ndaki Yerel görüntü sapmasını belirten `CORDB_ADDRESS` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="bedd4-106">[in] A `CORDB_ADDRESS` object that specifies the native image offset.</span></span>  
  
 `bufsize`  
 <span data-ttu-id="bedd4-107">'ndaki `buffer` dizisinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="bedd4-107">[in] The size, in bytes, of the `buffer` array.</span></span>  
  
 `buffer`  
 <span data-ttu-id="bedd4-108">dışı Kesme noktası tarafından değiştirilmiş Opcode içeren bir dizi.</span><span class="sxs-lookup"><span data-stu-id="bedd4-108">[out] An array that contains the opcode that is replaced by the breakpoint.</span></span>  
  
 `bufLen`  
 <span data-ttu-id="bedd4-109">dışı `buffer` dizisinde döndürülen bayt sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bedd4-109">[out] A pointer to the number of bytes returned in the `buffer` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bedd4-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bedd4-110">Remarks</span></span>  
 <span data-ttu-id="bedd4-111">Yerel görüntü boşluğu ortak dil çalışma zamanı (CLR) içindeyse, kesme noktası yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="bedd4-111">If the native image offset is within the common language runtime (CLR), the breakpoint will be ignored.</span></span> <span data-ttu-id="bedd4-112">Bu, bir kesme noktası hata ayıklayıcı tarafından ayarlandığında, CLR 'nin bant dışı bir kesme noktası gönderdikten engel olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="bedd4-112">This allows the CLR to avoid dispatching an out-of-band breakpoint, when the breakpoint is set by the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bedd4-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bedd4-113">Requirements</span></span>  
 <span data-ttu-id="bedd4-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bedd4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bedd4-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bedd4-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bedd4-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="bedd4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bedd4-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bedd4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
