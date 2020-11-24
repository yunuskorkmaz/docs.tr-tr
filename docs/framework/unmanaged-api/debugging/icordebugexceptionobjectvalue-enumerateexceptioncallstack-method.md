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
ms.openlocfilehash: 101151469e2eece20afe289c9d95387ce6dc7c6a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672129"
---
# <a name="icordebugexceptionobjectvalueenumerateexceptioncallstack-method"></a><span data-ttu-id="a2d39-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a2d39-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack Method</span></span>

<span data-ttu-id="a2d39-103">Özel durum nesnesine katıştırılmış çağrı yığınına bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="a2d39-103">Gets an enumerator to the call stack embedded in an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2d39-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a2d39-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateExceptionCallStack(  
    [out] ICorDebugExceptionObjectCallStackEnum **ppCallStackEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2d39-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a2d39-105">Parameters</span></span>  

 <span data-ttu-id="a2d39-106">ppCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="a2d39-106">ppCallStackEnum</span></span>  
 <span data-ttu-id="a2d39-107">dışı Yönetilen bir özel durum nesnesi için yığın izleme numaralandırıcısı olan [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) arabirimi nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a2d39-107">[out] A pointer to the address of an [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) interface object that is a stack trace enumerator for a managed exception object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2d39-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a2d39-108">Remarks</span></span>  

 <span data-ttu-id="a2d39-109">Hiçbir çağrı yığını bilgisi yoksa, yöntemi döndürür `S_OK` ve [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) , 0 uzunluğunda geçerli bir Numaralandırıcı olur.</span><span class="sxs-lookup"><span data-stu-id="a2d39-109">If no call stack information is available, the method returns `S_OK`, and [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) is a valid enumerator with a length of 0.</span></span> <span data-ttu-id="a2d39-110">Yöntem yığın izleme bilgilerini alamadığında, dönüş değeri olur `E_FAIL` ve hiçbir Numaralandırıcı döndürülmez.</span><span class="sxs-lookup"><span data-stu-id="a2d39-110">If the method is unable to retrieve stack trace information, the return value is `E_FAIL` and no enumerator is returned.</span></span>  
  
 <span data-ttu-id="a2d39-111">[ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) nesnesi, `_stackTrace` özel durum nesnesinin alanından yığın izleme verilerinin kodunu çözmekten sorumludur.</span><span class="sxs-lookup"><span data-stu-id="a2d39-111">The [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) object is responsible for decoding the stack trace data from the `_stackTrace` field of the exception object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2d39-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a2d39-112">Requirements</span></span>  

 <span data-ttu-id="a2d39-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2d39-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2d39-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a2d39-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2d39-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a2d39-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2d39-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2d39-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2d39-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2d39-117">See also</span></span>

- [<span data-ttu-id="a2d39-118">ICorDebugExceptionObjectValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a2d39-118">ICorDebugExceptionObjectValue Interface</span></span>](icordebugexceptionobjectvalue-interface.md)
- [<span data-ttu-id="a2d39-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a2d39-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
