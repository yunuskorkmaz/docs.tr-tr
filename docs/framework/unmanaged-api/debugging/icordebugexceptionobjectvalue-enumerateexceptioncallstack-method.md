---
title: "ICorDebugExceptionObjectValue::EnumerateExceptionCallStack Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugExceptionObjectValue.EnumerateExceptionCallStack
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugExceptionObjectValue::EnumerateExceptionCallStack
helpviewer_keywords:
- EnumerateExceptionCallStack method, ICorDebugExceptionObjectValue interface [.NET Framework debugging]
- ICorDebugExceptionObjectValue::EnumerateExceptionCallStack method [.NET Framework debugging]
ms.assetid: 00c64533-15dd-47f4-bb97-fe80a1ebadef
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 861d2ad5f9ce0fcc11ea7b1743cd369235cbd878
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugexceptionobjectvalueenumerateexceptioncallstack-method"></a><span data-ttu-id="6a884-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6a884-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack Method</span></span>
<span data-ttu-id="6a884-103">Bir özel durum nesnesi katıştırılmış çağrı yığını için bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="6a884-103">Gets an enumerator to the call stack embedded in an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a884-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a884-104">Syntax</span></span>  
  
```  
HRESULT EnumerateExceptionCallStack(  
    [out] ICorDebugExceptionObjectCallStackEnum **ppCallStackEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6a884-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6a884-105">Parameters</span></span>  
 <span data-ttu-id="6a884-106">ppCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="6a884-106">ppCallStackEnum</span></span>  
 <span data-ttu-id="6a884-107">[out] Adresine bir işaretçi bir [Icordebugexceptionobjectcallstackenum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) yönetilen özel durum nesnesi için bir yığın izleme Numaralandırıcı arabirimi nesnesi.</span><span class="sxs-lookup"><span data-stu-id="6a884-107">[out] A pointer to the address of an [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) interface object that is a stack trace enumerator for a managed exception object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a884-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6a884-108">Remarks</span></span>  
 <span data-ttu-id="6a884-109">Hiçbir çağrı yığını bilgileri bulunup bulunmadığını yöntemi döndürür `S_OK`, ve [Icordebugexceptionobjectcallstackenum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) uzunluğu 0 ile geçerli bir Numaralayıcı değil.</span><span class="sxs-lookup"><span data-stu-id="6a884-109">If no call stack information is available, the method returns `S_OK`, and [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) is a valid enumerator with a length of 0.</span></span> <span data-ttu-id="6a884-110">Yöntem yığın izleme bilgilerini alamadı dönüş değeri ise, `E_FAIL` ve hiçbir Numaralandırıcı döndürülür.</span><span class="sxs-lookup"><span data-stu-id="6a884-110">If the method is unable to retrieve stack trace information, the return value is `E_FAIL` and no enumerator is returned.</span></span>  
  
 <span data-ttu-id="6a884-111">[Icordebugexceptionobjectcallstackenum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) nesnesidir yığın izleme verileri çözülmesi için sorumlu `_stackTrace` özel durum nesnesi alanı.</span><span class="sxs-lookup"><span data-stu-id="6a884-111">The [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) object is responsible for decoding the stack trace data from the `_stackTrace` field of the exception object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a884-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6a884-112">Requirements</span></span>  
 <span data-ttu-id="6a884-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a884-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a884-114">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6a884-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a884-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a884-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a884-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a884-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a884-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6a884-117">See Also</span></span>  
 [<span data-ttu-id="6a884-118">Icordebugexceptionobjectvalue arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a884-118">ICorDebugExceptionObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-interface.md)  
 [<span data-ttu-id="6a884-119">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6a884-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
