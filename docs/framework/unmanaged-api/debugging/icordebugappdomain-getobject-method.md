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
ms.openlocfilehash: a21f3b36e418bbde5dcb90f25a39dae03fde77c9
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895209"
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
 Bu uygulama etki <xref:System.AppDomain?displayProperty=nameWithType> alanı için yönetilen bir nesne oluşturulmadıysa, yöntemi öğesini döndürür `S_FALSE` ve içine `NULL` `*ppObject`koyar.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir işlemdeki her uygulama etki alanının kendisini temsil eden çalışma <xref:System.AppDomain?displayProperty=nameWithType> zamanında yönetilen bir nesnesi olabilir. Bu işlev, bu yönetilen <xref:System.AppDomain?displayProperty=nameWithType> nesneye karşılık gelen bir ICorDebugValue arabirim nesnesi alır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]
