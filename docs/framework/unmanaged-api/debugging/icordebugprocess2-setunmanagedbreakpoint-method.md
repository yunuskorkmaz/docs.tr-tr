---
description: 'Daha fazla bilgi edinin: ICorDebugProcess2:: SetUnmanagedBreakpoint yöntemi'
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
ms.openlocfilehash: 7989f0fc9908941513b7d099fde81c79cef82c5b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746548"
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a><span data-ttu-id="096d3-103">ICorDebugProcess2::SetUnmanagedBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="096d3-103">ICorDebugProcess2::SetUnmanagedBreakpoint Method</span></span>

<span data-ttu-id="096d3-104">Belirtilen yerel görüntü uzaklığında yönetilmeyen bir kesme noktası ayarlar.</span><span class="sxs-lookup"><span data-stu-id="096d3-104">Sets an unmanaged breakpoint at the specified native image offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="096d3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="096d3-105">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmanagedBreakpoint (  
    [in]  CORDB_ADDRESS    address,  
    [in]  ULONG32          bufsize,  
    [out, size_is(bufsize), length_is(*bufLen)]
        BYTE               buffer[],  
    [out] ULONG32          *bufLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="096d3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="096d3-106">Parameters</span></span>  

 `address`  
 <span data-ttu-id="096d3-107">'ndaki `CORDB_ADDRESS` Yerel görüntü sapmasını belirten bir nesne.</span><span class="sxs-lookup"><span data-stu-id="096d3-107">[in] A `CORDB_ADDRESS` object that specifies the native image offset.</span></span>  
  
 `bufsize`  
 <span data-ttu-id="096d3-108">'ndaki Dizinin bayt cinsinden boyutu `buffer` .</span><span class="sxs-lookup"><span data-stu-id="096d3-108">[in] The size, in bytes, of the `buffer` array.</span></span>  
  
 `buffer`  
 <span data-ttu-id="096d3-109">dışı Kesme noktası tarafından değiştirilmiş Opcode içeren bir dizi.</span><span class="sxs-lookup"><span data-stu-id="096d3-109">[out] An array that contains the opcode that is replaced by the breakpoint.</span></span>  
  
 `bufLen`  
 <span data-ttu-id="096d3-110">dışı Dizide döndürülen bayt sayısına yönelik bir işaretçi `buffer` .</span><span class="sxs-lookup"><span data-stu-id="096d3-110">[out] A pointer to the number of bytes returned in the `buffer` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="096d3-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="096d3-111">Remarks</span></span>  

 <span data-ttu-id="096d3-112">Yerel görüntü boşluğu ortak dil çalışma zamanı (CLR) içindeyse, kesme noktası yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="096d3-112">If the native image offset is within the common language runtime (CLR), the breakpoint will be ignored.</span></span> <span data-ttu-id="096d3-113">Bu, bir kesme noktası hata ayıklayıcı tarafından ayarlandığında, CLR 'nin bant dışı bir kesme noktası gönderdikten engel olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="096d3-113">This allows the CLR to avoid dispatching an out-of-band breakpoint, when the breakpoint is set by the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="096d3-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="096d3-114">Requirements</span></span>  

 <span data-ttu-id="096d3-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="096d3-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="096d3-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="096d3-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="096d3-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="096d3-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="096d3-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="096d3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
