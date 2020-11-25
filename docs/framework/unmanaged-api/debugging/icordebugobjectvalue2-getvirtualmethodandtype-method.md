---
title: ICorDebugObjectValue2::GetVirtualMethodAndType Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue2.GetVirtualMethodAndType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue2::GetVirtualMethodAndType
helpviewer_keywords:
- GetVirtualMethodAndType method [.NET Framework debugging]
- ICorDebugObjectValue2::GetVirtualMethodAndType method
ms.assetid: 621b4543-a8f7-4117-98e4-930992cd688a
topic_type:
- apiref
ms.openlocfilehash: 2a74688b90fbce63c9107d9389ddfd7bf5cd717b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695185"
---
# <a name="icordebugobjectvalue2getvirtualmethodandtype-method"></a><span data-ttu-id="eb198-102">ICorDebugObjectValue2::GetVirtualMethodAndType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eb198-102">ICorDebugObjectValue2::GetVirtualMethodAndType Method</span></span>

<span data-ttu-id="eb198-103">Bu yöntem henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="eb198-103">This method is not yet implemented.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb198-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="eb198-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVirtualMethodAndType (  
    [in] mdMemberRef          memberRef,  
    [out] ICorDebugFunction   **ppFunction,  
    [out] ICorDebugType       **ppType  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="eb198-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eb198-105">Remarks</span></span>  

 <span data-ttu-id="eb198-106">"ICorDebugFunction" ve "ICorDebugType" örneklerine, belirtilen üye başvurusu için en çok türetilmiş yöntemi ve türü temsil eden arabirim işaretçileri alır.</span><span class="sxs-lookup"><span data-stu-id="eb198-106">Gets interface pointers to the "ICorDebugFunction" and "ICorDebugType" instances that represent the most derived method and type for the specified member reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb198-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb198-107">See also</span></span>
