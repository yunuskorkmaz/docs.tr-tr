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
ms.openlocfilehash: 71e32211e6ab16fb5e4e2c624dbad3af5fd6b09f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132033"
---
# <a name="icordebugobjectvalueisvalueclass-method"></a><span data-ttu-id="48f11-102">ICorDebugObjectValue::IsValueClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="48f11-102">ICorDebugObjectValue::IsValueClass Method</span></span>
<span data-ttu-id="48f11-103">Bu nesne değeri bir değer türü olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="48f11-103">Gets a value that indicates whether this object value is a value type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48f11-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="48f11-104">Syntax</span></span>  
  
```  
HRESULT IsValueClass (  
    [out] BOOL               *pbIsValueClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="48f11-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="48f11-105">Parameters</span></span>  
 `pbIsValueClass`  
 <span data-ttu-id="48f11-106">[out] Boolean bir değer için bir işaretçi `true` bu "Icordebugobjectvalue tarafından", temsil edilen nesne değeri, bir başvuru türü; yerine bir değer türü ise, aksi takdirde, `pbIsValueClass` olduğu `false`.</span><span class="sxs-lookup"><span data-stu-id="48f11-106">[out] A pointer to a Boolean value that is `true` if the object value, represented by this "ICorDebugObjectValue", is a value type rather than a reference type; otherwise, `pbIsValueClass` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48f11-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="48f11-107">Requirements</span></span>  
 <span data-ttu-id="48f11-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48f11-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48f11-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="48f11-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="48f11-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48f11-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="48f11-111">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="48f11-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="48f11-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48f11-112">See also</span></span>
