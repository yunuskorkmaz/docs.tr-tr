---
title: ICorDebugExceptionObjectValue::EnumerateExceptionCallStack Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectValue.EnumerateExceptionCallStack
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectValue::EnumerateExceptionCallStack
helpviewer_keywords:
- EnumerateExceptionCallStack method, ICorDebugExceptionObjectValue interface [.NET Framework debugging]
- ICorDebugExceptionObjectValue::EnumerateExceptionCallStack method [.NET Framework debugging]
ms.assetid: 00c64533-15dd-47f4-bb97-fe80a1ebadef
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9a58a62dbcd69d1847ab5a0b0109fe4eea53a4f3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754227"
---
# <a name="icordebugexceptionobjectvalueenumerateexceptioncallstack-method"></a><span data-ttu-id="e4cb8-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e4cb8-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack Method</span></span>
<span data-ttu-id="e4cb8-103">Bir özel durum nesnesine katıştırılmış çağrı yığını için bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="e4cb8-103">Gets an enumerator to the call stack embedded in an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4cb8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e4cb8-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateExceptionCallStack(  
    [out] ICorDebugExceptionObjectCallStackEnum **ppCallStackEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4cb8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e4cb8-105">Parameters</span></span>  
 <span data-ttu-id="e4cb8-106">ppCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="e4cb8-106">ppCallStackEnum</span></span>  
 <span data-ttu-id="e4cb8-107">[out] Adresine bir işaretçi bir [Icordebugexceptionobjectcallstackenum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) yönetilen özel durum nesnesi için bir yığın izleme Numaralandırıcı arabirimi nesnesi.</span><span class="sxs-lookup"><span data-stu-id="e4cb8-107">[out] A pointer to the address of an [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) interface object that is a stack trace enumerator for a managed exception object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4cb8-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e4cb8-108">Remarks</span></span>  
 <span data-ttu-id="e4cb8-109">Hiçbir çağrı yığını bilgileri bulunup bulunmadığını yöntemi döndürür `S_OK`, ve [Icordebugexceptionobjectcallstackenum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) uzunluğu 0 ile geçerli bir numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="e4cb8-109">If no call stack information is available, the method returns `S_OK`, and [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) is a valid enumerator with a length of 0.</span></span> <span data-ttu-id="e4cb8-110">Yöntemin yığın izleme bilgileri alınamıyor, dönüş değeri ise `E_FAIL` ve hiçbir Numaralandırıcı döndürülür.</span><span class="sxs-lookup"><span data-stu-id="e4cb8-110">If the method is unable to retrieve stack trace information, the return value is `E_FAIL` and no enumerator is returned.</span></span>  
  
 <span data-ttu-id="e4cb8-111">[Icordebugexceptionobjectcallstackenum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) nesnedir yığın izleme verileri kod çözme için sorumlu `_stackTrace` alanını özel durum nesnesi.</span><span class="sxs-lookup"><span data-stu-id="e4cb8-111">The [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) object is responsible for decoding the stack trace data from the `_stackTrace` field of the exception object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4cb8-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e4cb8-112">Requirements</span></span>  
 <span data-ttu-id="e4cb8-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4cb8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4cb8-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e4cb8-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e4cb8-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4cb8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4cb8-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4cb8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4cb8-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4cb8-117">See also</span></span>

- [<span data-ttu-id="e4cb8-118">ICorDebugExceptionObjectValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e4cb8-118">ICorDebugExceptionObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-interface.md)
- [<span data-ttu-id="e4cb8-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e4cb8-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
