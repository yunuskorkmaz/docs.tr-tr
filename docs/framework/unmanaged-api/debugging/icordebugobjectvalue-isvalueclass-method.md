---
title: ICorDebugObjectValue::IsValueClass Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.IsValueClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::IsValueClass
helpviewer_keywords:
- ICorDebugObjectValue::IsValueClass method [.NET Framework debugging]
- IsValueClass method [.NET Framework debugging]
ms.assetid: 13d89a4a-5d9d-4a79-9600-5e2a98c3d166
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7deab95db2e7ccfd167f3158f0f008c6b077a012
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416445"
---
# <a name="icordebugobjectvalueisvalueclass-method"></a><span data-ttu-id="77629-102">ICorDebugObjectValue::IsValueClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="77629-102">ICorDebugObjectValue::IsValueClass Method</span></span>
<span data-ttu-id="77629-103">Bu nesne değeri bir değer türü olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="77629-103">Gets a value that indicates whether this object value is a value type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77629-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="77629-104">Syntax</span></span>  
  
```  
HRESULT IsValueClass (  
    [out] BOOL               *pbIsValueClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="77629-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="77629-105">Parameters</span></span>  
 `pbIsValueClass`  
 <span data-ttu-id="77629-106">[out] Boolean bir değer için bir işaretçi `true` bu "Icordebugobjectvalue tarafından", temsil edilen nesne değeri bir başvuru türü; yerine bir değer türü ise, aksi takdirde, `pbIsValueClass` olan `false`.</span><span class="sxs-lookup"><span data-stu-id="77629-106">[out] A pointer to a Boolean value that is `true` if the object value, represented by this "ICorDebugObjectValue", is a value type rather than a reference type; otherwise, `pbIsValueClass` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77629-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="77629-107">Requirements</span></span>  
 <span data-ttu-id="77629-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77629-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77629-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="77629-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="77629-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77629-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77629-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77629-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77629-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="77629-112">See Also</span></span>  
    
 
