---
title: ICorDebugObjectValue2::GetVirtualMethodAndType Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugObjectValue2.GetVirtualMethodAndType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugObjectValue2::GetVirtualMethodAndType
helpviewer_keywords:
- GetVirtualMethodAndType method [.NET Framework debugging]
- ICorDebugObjectValue2::GetVirtualMethodAndType method
ms.assetid: 621b4543-a8f7-4117-98e4-930992cd688a
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae45088a95b887e10fef66b5c6feab57393c6c29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugobjectvalue2getvirtualmethodandtype-method"></a><span data-ttu-id="5a355-102">ICorDebugObjectValue2::GetVirtualMethodAndType Metodu</span><span class="sxs-lookup"><span data-stu-id="5a355-102">ICorDebugObjectValue2::GetVirtualMethodAndType Method</span></span>
<span data-ttu-id="5a355-103">Bu yöntem henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="5a355-103">This method is not yet implemented.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a355-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5a355-104">Syntax</span></span>  
  
```  
HRESULT GetVirtualMethodAndType (  
    [in] mdMemberRef          memberRef,  
    [out] ICorDebugFunction   **ppFunction,  
    [out] ICorDebugType       **ppType  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="5a355-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5a355-105">Remarks</span></span>  
 <span data-ttu-id="5a355-106">Alır en çok türetilen yöntemi ve belirtilen üye başvuru türünü temsil eden "ICorDebugFunction" ve "ICorDebugType" örneklerine işaretçileri arabirim.</span><span class="sxs-lookup"><span data-stu-id="5a355-106">Gets interface pointers to the "ICorDebugFunction" and "ICorDebugType" instances that represent the most derived method and type for the specified member reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a355-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5a355-107">See Also</span></span>  
    
 
