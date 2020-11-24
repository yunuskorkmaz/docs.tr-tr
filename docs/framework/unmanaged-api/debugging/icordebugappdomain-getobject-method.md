---
title: ICorDebugAppDomain::GetObject Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetObject
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetObject
helpviewer_keywords:
- ICorDebugAppDomain::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 78232e6f-ae18-4cfa-a6cd-e79471cf9d76
topic_type:
- apiref
ms.openlocfilehash: a163667ea7eca1ed817d642efdb8fc4efa2a0651
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676068"
---
# <a name="icordebugappdomaingetobject-method"></a>ICorDebugAppDomain::GetObject Yöntemi

Ortak dil çalışma zamanı (CLR) uygulama etki alanına bir arabirim işaretçisi alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `ppObject`  
 dışı CLR uygulama etki alanını temsil eden ICorDebugValue arabirimi nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 <xref:System.AppDomain?displayProperty=nameWithType>Bu uygulama etki alanı için yönetilen bir nesne oluşturulmadıysa, yöntemi öğesini döndürür `S_FALSE` ve içine koyar `NULL` `*ppObject` .  
  
## <a name="remarks"></a>Açıklamalar  

 Bir işlemdeki her uygulama etki alanının <xref:System.AppDomain?displayProperty=nameWithType> kendisini temsil eden çalışma zamanında yönetilen bir nesnesi olabilir. Bu işlev, bu yönetilen nesneye karşılık gelen bir ICorDebugValue arabirim nesnesi alır <xref:System.AppDomain?displayProperty=nameWithType> .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]
