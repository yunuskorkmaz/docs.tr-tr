---
title: ICorDebugProcess::ReadMemory Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ReadMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ReadMemory
helpviewer_keywords:
- ReadMemory method [.NET Framework debugging]
- ICorDebugProcess::ReadMemory method [.NET Framework debugging]
ms.assetid: 28e4b2f6-9589-445c-be24-24a3306795e7
topic_type:
- apiref
ms.openlocfilehash: a0abc7168ff7bffdbb835c1c1bc93de9df6e381c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95694873"
---
# <a name="icordebugprocessreadmemory-method"></a><span data-ttu-id="8daf6-102">ICorDebugProcess::ReadMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8daf6-102">ICorDebugProcess::ReadMemory Method</span></span>

<span data-ttu-id="8daf6-103">Bu işlem için belirtilen bellek alanını okur.</span><span class="sxs-lookup"><span data-stu-id="8daf6-103">Reads a specified area of memory for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8daf6-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8daf6-104">Syntax</span></span>  
  
```cpp  
HRESULT ReadMemory(  
    [in]  CORDB_ADDRESS address,
    [in]  DWORD size,  
    [out, size_is(size), length_is(size)] BYTE buffer[],  
    [out] SIZE_T *read);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8daf6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8daf6-105">Parameters</span></span>  

 `address`  
 <span data-ttu-id="8daf6-106">'ndaki `CORDB_ADDRESS` Okunacak belleğin temel adresini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="8daf6-106">[in] A `CORDB_ADDRESS` value that specifies the base address of the memory to be read.</span></span>  
  
 `size`  
 <span data-ttu-id="8daf6-107">'ndaki Bellekten okunacak bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="8daf6-107">[in] The number of bytes to be read from memory.</span></span>  
  
 `buffer`  
 <span data-ttu-id="8daf6-108">dışı Belleğin içeriğini alan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="8daf6-108">[out] A buffer that receives the contents of the memory.</span></span>  
  
 `read`  
 <span data-ttu-id="8daf6-109">dışı Belirtilen arabelleğe aktarılan bayt sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8daf6-109">[out] A pointer to the number of bytes transferred into the specified buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8daf6-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8daf6-110">Remarks</span></span>  

 <span data-ttu-id="8daf6-111">`ReadMemory`Yöntemi öncelikle, hata ayıklanan yönetilmeyen bölümü tarafından kullanılmakta olan bellek bölgelerini incelemek için birlikte çalışma hata ayıklaması tarafından kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8daf6-111">The `ReadMemory` method is primarily intended to be used by interop debugging to inspect memory regions that are being used by the unmanaged portion of the debuggee.</span></span> <span data-ttu-id="8daf6-112">Bu yöntem, Microsoft ara dili (MSIL) kodu ve yerel JıT derlenmiş kod okumak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8daf6-112">This method can also be used to read Microsoft intermediate language (MSIL) code and native JIT-compiled code.</span></span>  
  
 <span data-ttu-id="8daf6-113">Yönetilen kesme noktaları, parametrede döndürülen verilerden kaldırılır `buffer` .</span><span class="sxs-lookup"><span data-stu-id="8daf6-113">Any managed breakpoints will be removed from the data that is returned in the `buffer` parameter.</span></span> <span data-ttu-id="8daf6-114">[ICorDebugProcess2:: SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md)tarafından ayarlanan yerel kesme noktaları için hiçbir değişiklik yapılmayacak.</span><span class="sxs-lookup"><span data-stu-id="8daf6-114">No adjustments will be made for native breakpoints set by [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="8daf6-115">İşlem belleğini önbelleğe alma işlemi yapılmaz.</span><span class="sxs-lookup"><span data-stu-id="8daf6-115">No caching of process memory is performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8daf6-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8daf6-116">Requirements</span></span>  

 <span data-ttu-id="8daf6-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8daf6-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8daf6-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8daf6-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8daf6-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8daf6-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8daf6-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8daf6-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
