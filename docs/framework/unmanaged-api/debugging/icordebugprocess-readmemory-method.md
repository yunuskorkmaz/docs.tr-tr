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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 218279684304b766a9bf009f5891ac4910254a3c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994389"
---
# <a name="icordebugprocessreadmemory-method"></a><span data-ttu-id="a2646-102">ICorDebugProcess::ReadMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a2646-102">ICorDebugProcess::ReadMemory Method</span></span>
<span data-ttu-id="a2646-103">Bu işlem için bellek belirtilen bir alan okur.</span><span class="sxs-lookup"><span data-stu-id="a2646-103">Reads a specified area of memory for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2646-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a2646-104">Syntax</span></span>  
  
```  
HRESULT ReadMemory(  
    [in]  CORDB_ADDRESS address,   
    [in]  DWORD size,  
    [out, size_is(size), length_is(size)] BYTE buffer[],  
    [out] SIZE_T *read);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2646-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a2646-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="a2646-106">[in] A `CORDB_ADDRESS` okumak için bellek taban adresini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="a2646-106">[in] A `CORDB_ADDRESS` value that specifies the base address of the memory to be read.</span></span>  
  
 `size`  
 <span data-ttu-id="a2646-107">[in] Bellekten okunacak bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="a2646-107">[in] The number of bytes to be read from memory.</span></span>  
  
 `buffer`  
 <span data-ttu-id="a2646-108">[out] Bellek içerikleri alan arabellek.</span><span class="sxs-lookup"><span data-stu-id="a2646-108">[out] A buffer that receives the contents of the memory.</span></span>  
  
 `read`  
 <span data-ttu-id="a2646-109">[out] Bir işaretçi bayt sayısı belirtilen arabelleğe aktardı.</span><span class="sxs-lookup"><span data-stu-id="a2646-109">[out] A pointer to the number of bytes transferred into the specified buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2646-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a2646-110">Remarks</span></span>  
 <span data-ttu-id="a2646-111">`ReadMemory` Yöntemi yönetilmeyen hata ayıklanan bölümü tarafından kullanılmakta olan bellek bölümlerinin incelemek için birlikte çalışma hata ayıklama tarafından kullanılması amaçlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a2646-111">The `ReadMemory` method is primarily intended to be used by interop debugging to inspect memory regions that are being used by the unmanaged portion of the debuggee.</span></span> <span data-ttu-id="a2646-112">Bu yöntem, Microsoft Ara dil (MSIL) kodu ve JIT olarak derlenmiş yerel kod okumak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a2646-112">This method can also be used to read Microsoft intermediate language (MSIL) code and native JIT-compiled code.</span></span>  
  
 <span data-ttu-id="a2646-113">Yönetilen herhangi bir kesme noktası içerisinde geri dönmemiş ise veri kaldırılacak `buffer` parametresi.</span><span class="sxs-lookup"><span data-stu-id="a2646-113">Any managed breakpoints will be removed from the data that is returned in the `buffer` parameter.</span></span> <span data-ttu-id="a2646-114">Yerel kesme noktaları ayarlayın hiçbir düzeltme yapılan [Icordebugprocess2::setunmanagedbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span><span class="sxs-lookup"><span data-stu-id="a2646-114">No adjustments will be made for native breakpoints set by [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="a2646-115">Önbelleksizlik işlem bellek gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a2646-115">No caching of process memory is performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2646-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a2646-116">Requirements</span></span>  
 <span data-ttu-id="a2646-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2646-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2646-118">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a2646-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2646-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2646-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2646-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2646-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
