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
ms.openlocfilehash: 383e3f8990a1f355c94ff5e9f9daa69bdbdd97bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178657"
---
# <a name="icordebugprocessreadmemory-method"></a><span data-ttu-id="0304b-102">ICorDebugProcess::ReadMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0304b-102">ICorDebugProcess::ReadMemory Method</span></span>
<span data-ttu-id="0304b-103">Bu işlem için belirli bir bellek alanını okur.</span><span class="sxs-lookup"><span data-stu-id="0304b-103">Reads a specified area of memory for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0304b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0304b-104">Syntax</span></span>  
  
```cpp  
HRESULT ReadMemory(  
    [in]  CORDB_ADDRESS address,
    [in]  DWORD size,  
    [out, size_is(size), length_is(size)] BYTE buffer[],  
    [out] SIZE_T *read);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0304b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0304b-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="0304b-106">[içinde] Okunacak belleğin temel adresini belirten bir `CORDB_ADDRESS` değer.</span><span class="sxs-lookup"><span data-stu-id="0304b-106">[in] A `CORDB_ADDRESS` value that specifies the base address of the memory to be read.</span></span>  
  
 `size`  
 <span data-ttu-id="0304b-107">[içinde] Bellekten okunacak bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="0304b-107">[in] The number of bytes to be read from memory.</span></span>  
  
 `buffer`  
 <span data-ttu-id="0304b-108">[çıkış] Belleğin içeriğini alan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="0304b-108">[out] A buffer that receives the contents of the memory.</span></span>  
  
 `read`  
 <span data-ttu-id="0304b-109">[çıkış] Belirtilen arabelleğe aktarılan bayt sayısına işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0304b-109">[out] A pointer to the number of bytes transferred into the specified buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0304b-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0304b-110">Remarks</span></span>  
 <span data-ttu-id="0304b-111">Yöntem `ReadMemory` öncelikle hata ayıklama nın yönetilmeyen bölümü tarafından kullanılan bellek bölgelerini incelemek için interop hata ayıklama tarafından kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0304b-111">The `ReadMemory` method is primarily intended to be used by interop debugging to inspect memory regions that are being used by the unmanaged portion of the debuggee.</span></span> <span data-ttu-id="0304b-112">Bu yöntem, Microsoft ara dili (MSIL) kodunu ve yerel JIT tarafından derlenen kodu okumak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0304b-112">This method can also be used to read Microsoft intermediate language (MSIL) code and native JIT-compiled code.</span></span>  
  
 <span data-ttu-id="0304b-113">Yönetilen kesme noktaları `buffer` parametrede döndürülen verilerden kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="0304b-113">Any managed breakpoints will be removed from the data that is returned in the `buffer` parameter.</span></span> <span data-ttu-id="0304b-114">ICorDebugProcess2 tarafından ayarlanan yerel kesme noktaları için ayarlama [yapılmaz::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md).</span><span class="sxs-lookup"><span data-stu-id="0304b-114">No adjustments will be made for native breakpoints set by [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="0304b-115">İşlem belleği önbelleğe alma işlemi yapılmaz.</span><span class="sxs-lookup"><span data-stu-id="0304b-115">No caching of process memory is performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0304b-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0304b-116">Requirements</span></span>  
 <span data-ttu-id="0304b-117">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0304b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0304b-118">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0304b-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0304b-119">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0304b-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0304b-120">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0304b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
