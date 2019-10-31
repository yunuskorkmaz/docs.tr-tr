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
ms.openlocfilehash: 17cb3440c5b33d461b1624608ce115e1942d6beb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129714"
---
# <a name="icordebugobjectvalue2getvirtualmethodandtype-method"></a>ICorDebugObjectValue2::GetVirtualMethodAndType Yöntemi
Bu yöntem henüz uygulanmadı.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetVirtualMethodAndType (  
    [in] mdMemberRef          memberRef,  
    [out] ICorDebugFunction   **ppFunction,  
    [out] ICorDebugType       **ppType  
);  
```  
  
## <a name="remarks"></a>Açıklamalar  
 "ICorDebugFunction" ve "ICorDebugType" örneklerine, belirtilen üye başvurusu için en çok türetilmiş yöntemi ve türü temsil eden arabirim işaretçileri alır.  
  
## <a name="see-also"></a>Ayrıca bkz.
