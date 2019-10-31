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
ms.openlocfilehash: f2c881603cfa0e4b3d2dc8d1e996631b51d1e850
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134710"
---
# <a name="icordebugappdomaingetobject-method"></a>ICorDebugAppDomain::GetObject Yöntemi
Ortak dil çalışma zamanı (CLR) uygulama etki alanına bir arabirim işaretçisi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppObject`  
 dışı CLR uygulama etki alanını temsil eden ICorDebugValue arabirimi nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu uygulama etki alanı için yönetilen bir <xref:System.AppDomain?displayProperty=nameWithType> nesnesi oluşturulmadıysa, yöntem `S_FALSE` döndürür ve `*ppObject``NULL` koyar.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir işlemdeki her uygulama etki alanı, onu temsil eden çalışma zamanında yönetilen bir <xref:System.AppDomain?displayProperty=nameWithType> nesnesine sahip olabilir. Bu işlev, bu yönetilen <xref:System.AppDomain?displayProperty=nameWithType> nesnesine karşılık gelen bir ICorDebugValue arabirim nesnesi alır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]
