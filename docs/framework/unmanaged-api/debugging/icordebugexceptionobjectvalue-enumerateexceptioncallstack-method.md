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
ms.openlocfilehash: 57eb284bfe39ce92b2d6c03a2aeb4ae84d6aba91
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788676"
---
# <a name="icordebugexceptionobjectvalueenumerateexceptioncallstack-method"></a><span data-ttu-id="639b7-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack Yöntemi</span><span class="sxs-lookup"><span data-stu-id="639b7-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack Method</span></span>
<span data-ttu-id="639b7-103">Özel durum nesnesine katıştırılmış çağrı yığınına bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="639b7-103">Gets an enumerator to the call stack embedded in an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="639b7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="639b7-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateExceptionCallStack(  
    [out] ICorDebugExceptionObjectCallStackEnum **ppCallStackEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="639b7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="639b7-105">Parameters</span></span>  
 <span data-ttu-id="639b7-106">ppCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="639b7-106">ppCallStackEnum</span></span>  
 <span data-ttu-id="639b7-107">dışı Yönetilen bir özel durum nesnesi için yığın izleme numaralandırıcısı olan [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) arabirimi nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="639b7-107">[out] A pointer to the address of an [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) interface object that is a stack trace enumerator for a managed exception object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="639b7-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="639b7-108">Remarks</span></span>  
 <span data-ttu-id="639b7-109">Hiçbir çağrı yığını bilgisi yoksa, yöntem `S_OK`döndürür ve [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) , 0 uzunluğunda geçerli bir Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="639b7-109">If no call stack information is available, the method returns `S_OK`, and [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) is a valid enumerator with a length of 0.</span></span> <span data-ttu-id="639b7-110">Yöntem yığın izleme bilgilerini alamadığında, dönüş değeri `E_FAIL` ve hiçbir Numaralandırıcı döndürülmez.</span><span class="sxs-lookup"><span data-stu-id="639b7-110">If the method is unable to retrieve stack trace information, the return value is `E_FAIL` and no enumerator is returned.</span></span>  
  
 <span data-ttu-id="639b7-111">[ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) nesnesi, özel durum nesnesinin `_stackTrace` alanından yığın izleme verilerinin kodunu çözmekten sorumludur.</span><span class="sxs-lookup"><span data-stu-id="639b7-111">The [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) object is responsible for decoding the stack trace data from the `_stackTrace` field of the exception object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="639b7-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="639b7-112">Requirements</span></span>  
 <span data-ttu-id="639b7-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="639b7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="639b7-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="639b7-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="639b7-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="639b7-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="639b7-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="639b7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="639b7-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="639b7-117">See also</span></span>

- [<span data-ttu-id="639b7-118">ICorDebugExceptionObjectValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="639b7-118">ICorDebugExceptionObjectValue Interface</span></span>](icordebugexceptionobjectvalue-interface.md)
- [<span data-ttu-id="639b7-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="639b7-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
