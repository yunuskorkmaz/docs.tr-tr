---
title: "ICorDebugProcess::ReadMemory Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.ReadMemory
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::ReadMemory
helpviewer_keywords:
- ReadMemory method [.NET Framework debugging]
- ICorDebugProcess::ReadMemory method [.NET Framework debugging]
ms.assetid: 28e4b2f6-9589-445c-be24-24a3306795e7
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 33345ada6606bc1a43a630340251d3ba1404b2f2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocessreadmemory-method"></a><span data-ttu-id="9a59f-102">ICorDebugProcess::ReadMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9a59f-102">ICorDebugProcess::ReadMemory Method</span></span>
<span data-ttu-id="9a59f-103">Bu işlem için bellek belirtilen alan okur.</span><span class="sxs-lookup"><span data-stu-id="9a59f-103">Reads a specified area of memory for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a59f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9a59f-104">Syntax</span></span>  
  
```  
HRESULT ReadMemory(  
    [in]  CORDB_ADDRESS address,   
    [in]  DWORD size,  
    [out, size_is(size), length_is(size)] BYTE buffer[],  
    [out] SIZE_T *read);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9a59f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9a59f-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="9a59f-106">[in] A `CORDB_ADDRESS` okumak için bellek taban adresini belirten değer.</span><span class="sxs-lookup"><span data-stu-id="9a59f-106">[in] A `CORDB_ADDRESS` value that specifies the base address of the memory to be read.</span></span>  
  
 `size`  
 <span data-ttu-id="9a59f-107">[in] Bellekten okunacak bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="9a59f-107">[in] The number of bytes to be read from memory.</span></span>  
  
 `buffer`  
 <span data-ttu-id="9a59f-108">[out] Bellek içeriğini alır arabelleği.</span><span class="sxs-lookup"><span data-stu-id="9a59f-108">[out] A buffer that receives the contents of the memory.</span></span>  
  
 `read`  
 <span data-ttu-id="9a59f-109">[out] Bir işaretçi bayt sayısı belirtilen arabelleğe aktarılan.</span><span class="sxs-lookup"><span data-stu-id="9a59f-109">[out] A pointer to the number of bytes transferred into the specified buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a59f-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9a59f-110">Remarks</span></span>  
 <span data-ttu-id="9a59f-111">`ReadMemory` Yöntemi ayıklayıcı yönetilmeyen bölümü tarafından kullanılan bellek bölümlerinin incelemek için birlikte çalışma hata ayıklama tarafından kullanılmak üzere öncelikle amaçlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9a59f-111">The `ReadMemory` method is primarily intended to be used by interop debugging to inspect memory regions that are being used by the unmanaged portion of the debuggee.</span></span> <span data-ttu-id="9a59f-112">Bu yöntem, Microsoft Ara dili (MSIL) kodu ve yerel JIT derlenmiş kod okumak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9a59f-112">This method can also be used to read Microsoft intermediate language (MSIL) code and native JIT-compiled code.</span></span>  
  
 <span data-ttu-id="9a59f-113">Tüm yönetilen kesme noktalarını döndürülür verileri kaldırılacak `buffer` parametresi.</span><span class="sxs-lookup"><span data-stu-id="9a59f-113">Any managed breakpoints will be removed from the data that is returned in the `buffer` parameter.</span></span> <span data-ttu-id="9a59f-114">Yerel kesme noktaları ayarlayın ayarlama yapılmayan yapılan [Icordebugprocess2::setunmanagedbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span><span class="sxs-lookup"><span data-stu-id="9a59f-114">No adjustments will be made for native breakpoints set by [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="9a59f-115">Önbelleğe alma işlemi bellek gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="9a59f-115">No caching of process memory is performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a59f-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9a59f-116">Requirements</span></span>  
 <span data-ttu-id="9a59f-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a59f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a59f-118">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9a59f-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9a59f-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a59f-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a59f-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a59f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
