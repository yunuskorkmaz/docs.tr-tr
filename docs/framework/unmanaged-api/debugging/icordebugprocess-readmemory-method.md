---
description: ': ICorDebugProcess:: ReadMemory yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: bdf1bda9df416b6d3142e3ae09955e706f260802
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746808"
---
# <a name="icordebugprocessreadmemory-method"></a><span data-ttu-id="740cb-103">ICorDebugProcess::ReadMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="740cb-103">ICorDebugProcess::ReadMemory Method</span></span>

<span data-ttu-id="740cb-104">Bu işlem için belirtilen bellek alanını okur.</span><span class="sxs-lookup"><span data-stu-id="740cb-104">Reads a specified area of memory for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="740cb-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="740cb-105">Syntax</span></span>  
  
```cpp  
HRESULT ReadMemory(  
    [in]  CORDB_ADDRESS address,
    [in]  DWORD size,  
    [out, size_is(size), length_is(size)] BYTE buffer[],  
    [out] SIZE_T *read);  
```  
  
## <a name="parameters"></a><span data-ttu-id="740cb-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="740cb-106">Parameters</span></span>  

 `address`  
 <span data-ttu-id="740cb-107">'ndaki `CORDB_ADDRESS` Okunacak belleğin temel adresini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="740cb-107">[in] A `CORDB_ADDRESS` value that specifies the base address of the memory to be read.</span></span>  
  
 `size`  
 <span data-ttu-id="740cb-108">'ndaki Bellekten okunacak bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="740cb-108">[in] The number of bytes to be read from memory.</span></span>  
  
 `buffer`  
 <span data-ttu-id="740cb-109">dışı Belleğin içeriğini alan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="740cb-109">[out] A buffer that receives the contents of the memory.</span></span>  
  
 `read`  
 <span data-ttu-id="740cb-110">dışı Belirtilen arabelleğe aktarılan bayt sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="740cb-110">[out] A pointer to the number of bytes transferred into the specified buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="740cb-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="740cb-111">Remarks</span></span>  

 <span data-ttu-id="740cb-112">`ReadMemory`Yöntemi öncelikle, hata ayıklanan yönetilmeyen bölümü tarafından kullanılmakta olan bellek bölgelerini incelemek için birlikte çalışma hata ayıklaması tarafından kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="740cb-112">The `ReadMemory` method is primarily intended to be used by interop debugging to inspect memory regions that are being used by the unmanaged portion of the debuggee.</span></span> <span data-ttu-id="740cb-113">Bu yöntem, Microsoft ara dili (MSIL) kodu ve yerel JıT derlenmiş kod okumak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="740cb-113">This method can also be used to read Microsoft intermediate language (MSIL) code and native JIT-compiled code.</span></span>  
  
 <span data-ttu-id="740cb-114">Yönetilen kesme noktaları, parametrede döndürülen verilerden kaldırılır `buffer` .</span><span class="sxs-lookup"><span data-stu-id="740cb-114">Any managed breakpoints will be removed from the data that is returned in the `buffer` parameter.</span></span> <span data-ttu-id="740cb-115">[ICorDebugProcess2:: SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md)tarafından ayarlanan yerel kesme noktaları için hiçbir değişiklik yapılmayacak.</span><span class="sxs-lookup"><span data-stu-id="740cb-115">No adjustments will be made for native breakpoints set by [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="740cb-116">İşlem belleğini önbelleğe alma işlemi yapılmaz.</span><span class="sxs-lookup"><span data-stu-id="740cb-116">No caching of process memory is performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="740cb-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="740cb-117">Requirements</span></span>  

 <span data-ttu-id="740cb-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="740cb-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="740cb-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="740cb-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="740cb-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="740cb-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="740cb-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="740cb-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
