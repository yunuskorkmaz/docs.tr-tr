---
description: ': ICorDebugObjectValue:: IsValueClass yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: bf3ce94a06092209507fd1ff737e09a77b5d0c70
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728931"
---
# <a name="icordebugobjectvalueisvalueclass-method"></a><span data-ttu-id="61f4f-103">ICorDebugObjectValue::IsValueClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="61f4f-103">ICorDebugObjectValue::IsValueClass Method</span></span>

<span data-ttu-id="61f4f-104">Bu nesne değerinin bir değer türü olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="61f4f-104">Gets a value that indicates whether this object value is a value type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61f4f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="61f4f-105">Syntax</span></span>  
  
```cpp  
HRESULT IsValueClass (  
    [out] BOOL               *pbIsValueClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61f4f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="61f4f-106">Parameters</span></span>  

 `pbIsValueClass`  
 <span data-ttu-id="61f4f-107">dışı `true` Bu "ICorDebugObjectValue" ile temsil edilen nesne değeri bir başvuru türü yerine bir değer türü ise, bir Boolean değeri işaretçisi; Aksi takdirde, `pbIsValueClass` olur `false` .</span><span class="sxs-lookup"><span data-stu-id="61f4f-107">[out] A pointer to a Boolean value that is `true` if the object value, represented by this "ICorDebugObjectValue", is a value type rather than a reference type; otherwise, `pbIsValueClass` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61f4f-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="61f4f-108">Requirements</span></span>  

 <span data-ttu-id="61f4f-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61f4f-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61f4f-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="61f4f-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="61f4f-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="61f4f-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61f4f-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61f4f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61f4f-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61f4f-113">See also</span></span>
