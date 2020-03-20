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
ms.openlocfilehash: fb8b8f3e29c141e91587a4d0cdc81cdabccdbc9e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178643"
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a><span data-ttu-id="4e88f-102">ICorDebugProcess2::SetUnmanagedBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4e88f-102">ICorDebugProcess2::SetUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="4e88f-103">Belirtilen yerel görüntü ofsetinde yönetilmeyen bir kesme noktası ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4e88f-103">Sets an unmanaged breakpoint at the specified native image offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e88f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4e88f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmanagedBreakpoint (  
    [in]  CORDB_ADDRESS    address,  
    [in]  ULONG32          bufsize,  
    [out, size_is(bufsize), length_is(*bufLen)]
        BYTE               buffer[],  
    [out] ULONG32          *bufLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e88f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4e88f-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="4e88f-106">[içinde] Yerel `CORDB_ADDRESS` görüntü ofset belirten bir nesne.</span><span class="sxs-lookup"><span data-stu-id="4e88f-106">[in] A `CORDB_ADDRESS` object that specifies the native image offset.</span></span>  
  
 `bufsize`  
 <span data-ttu-id="4e88f-107">[içinde] Dizinin boyutu, baytlar halinde. `buffer`</span><span class="sxs-lookup"><span data-stu-id="4e88f-107">[in] The size, in bytes, of the `buffer` array.</span></span>  
  
 `buffer`  
 <span data-ttu-id="4e88f-108">[çıkış] Kesme noktası yla değiştirilen opcode içeren bir dizi.</span><span class="sxs-lookup"><span data-stu-id="4e88f-108">[out] An array that contains the opcode that is replaced by the breakpoint.</span></span>  
  
 `bufLen`  
 <span data-ttu-id="4e88f-109">[çıkış] Dizide döndürülen bayt sayısına `buffer` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4e88f-109">[out] A pointer to the number of bytes returned in the `buffer` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e88f-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4e88f-110">Remarks</span></span>  
 <span data-ttu-id="4e88f-111">Yerel görüntü ofset ortak dil çalışma süresi (CLR) içinde ise, kesme noktası yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="4e88f-111">If the native image offset is within the common language runtime (CLR), the breakpoint will be ignored.</span></span> <span data-ttu-id="4e88f-112">Bu, CLR'nin hata ayıklayıcı tarafından kesme noktası ayarlandığında bant dışı bir kesme noktası göndermekten kaçınmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e88f-112">This allows the CLR to avoid dispatching an out-of-band breakpoint, when the breakpoint is set by the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e88f-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4e88f-113">Requirements</span></span>  
 <span data-ttu-id="4e88f-114">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e88f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e88f-115">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4e88f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4e88f-116">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e88f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e88f-117">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e88f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
