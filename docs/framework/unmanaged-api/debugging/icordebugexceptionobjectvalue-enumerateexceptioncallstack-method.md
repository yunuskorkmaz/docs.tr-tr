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
ms.openlocfilehash: e45b180ac6d943d89740ad7ae10500ea4ad1aa9c
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975972"
---
# <a name="icordebugexceptionobjectvalueenumerateexceptioncallstack-method"></a><span data-ttu-id="177ff-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack Yöntemi</span><span class="sxs-lookup"><span data-stu-id="177ff-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack Method</span></span>
<span data-ttu-id="177ff-103">Özel durum nesnesine katıştırılmış çağrı yığınına bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="177ff-103">Gets an enumerator to the call stack embedded in an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="177ff-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="177ff-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateExceptionCallStack(  
    [out] ICorDebugExceptionObjectCallStackEnum **ppCallStackEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="177ff-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="177ff-105">Parameters</span></span>  
 <span data-ttu-id="177ff-106">ppCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="177ff-106">ppCallStackEnum</span></span>  
 <span data-ttu-id="177ff-107">dışı Yönetilen bir özel durum nesnesi için yığın izleme numaralandırıcısı olan [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) arabirimi nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="177ff-107">[out] A pointer to the address of an [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) interface object that is a stack trace enumerator for a managed exception object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="177ff-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="177ff-108">Remarks</span></span>  
 <span data-ttu-id="177ff-109">Hiçbir çağrı yığını bilgisi yoksa, yöntemi döndürür `S_OK`ve [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) , 0 uzunluğunda geçerli bir Numaralandırıcı olur.</span><span class="sxs-lookup"><span data-stu-id="177ff-109">If no call stack information is available, the method returns `S_OK`, and [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) is a valid enumerator with a length of 0.</span></span> <span data-ttu-id="177ff-110">Yöntem yığın izleme bilgilerini alamadığında, dönüş değeri olur `E_FAIL` ve hiçbir Numaralandırıcı döndürülmez.</span><span class="sxs-lookup"><span data-stu-id="177ff-110">If the method is unable to retrieve stack trace information, the return value is `E_FAIL` and no enumerator is returned.</span></span>  
  
 <span data-ttu-id="177ff-111">[ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) nesnesi, özel durum nesnesinin `_stackTrace` alanından yığın izleme verilerinin kodunu çözmekten sorumludur.</span><span class="sxs-lookup"><span data-stu-id="177ff-111">The [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) object is responsible for decoding the stack trace data from the `_stackTrace` field of the exception object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="177ff-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="177ff-112">Requirements</span></span>  
 <span data-ttu-id="177ff-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="177ff-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="177ff-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="177ff-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="177ff-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="177ff-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="177ff-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="177ff-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="177ff-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="177ff-117">See also</span></span>

- [<span data-ttu-id="177ff-118">ICorDebugExceptionObjectValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="177ff-118">ICorDebugExceptionObjectValue Interface</span></span>](icordebugexceptionobjectvalue-interface.md)
- [<span data-ttu-id="177ff-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="177ff-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
