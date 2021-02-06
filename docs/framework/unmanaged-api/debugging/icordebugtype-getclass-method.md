---
description: ': ICorDebugType:: GetClass yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugType::GetClass Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetClass
helpviewer_keywords:
- ICorDebugType::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: 2644f48b-db3c-429f-ae62-76f1c98a1af5
topic_type:
- apiref
ms.openlocfilehash: 2e8d68fbc8909599ca649ba0e226cc84af820939
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658353"
---
# <a name="icordebugtypegetclass-method"></a><span data-ttu-id="ab5f0-103">ICorDebugType::GetClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ab5f0-103">ICorDebugType::GetClass Method</span></span>

<span data-ttu-id="ab5f0-104">Örneklenmiş genel türü temsil eden bir ICorDebugClass için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="ab5f0-104">Gets an interface pointer to an ICorDebugClass that represents the uninstantiated generic type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab5f0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ab5f0-105">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab5f0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ab5f0-106">Parameters</span></span>  

 `ppClass`  
 <span data-ttu-id="ab5f0-107">dışı `ICorDebugClass` Örneklenmiş genel türü temsil eden bir arabirimin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ab5f0-107">[out] A pointer to the address of an `ICorDebugClass` interface that represents the uninstantiated generic type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab5f0-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ab5f0-108">Remarks</span></span>  

 <span data-ttu-id="ab5f0-109">`GetClass` yalnızca belirli koşullar altında çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="ab5f0-109">`GetClass` can be called only under certain conditions.</span></span> <span data-ttu-id="ab5f0-110">Çağrılmadan önce [ICorDebugType:: GetType](icordebugtype-gettype-method.md) çağırın `GetClass` .</span><span class="sxs-lookup"><span data-stu-id="ab5f0-110">Call [ICorDebugType::GetType](icordebugtype-gettype-method.md) before calling `GetClass`.</span></span> <span data-ttu-id="ab5f0-111">`ICorDebugType::GetType`Element_type_class veya element_type_valuetype bir CorElementType değeri döndürürse, `GetClass` genel bir türün örneklenmemiş türünü almak için çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="ab5f0-111">If `ICorDebugType::GetType` returns a CorElementType value that is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, `GetClass` can be called to get the uninstantiated type for a generic type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab5f0-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ab5f0-112">Requirements</span></span>  

 <span data-ttu-id="ab5f0-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab5f0-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab5f0-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ab5f0-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab5f0-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ab5f0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab5f0-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab5f0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
