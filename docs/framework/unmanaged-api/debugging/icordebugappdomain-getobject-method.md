---
description: ': ICorDebugAppDomain:: GetObject yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 59389e2a4ca72f8dcdd7117213e968440d30aaa6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754218"
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

 <xref:System.AppDomain?displayProperty=nameWithType>Bu uygulama etki alanı için yönetilen bir nesne oluşturulmadıysa, yöntemi öğesini döndürür `S_FALSE` ve içine koyar `NULL` `*ppObject` .  
  
## <a name="remarks"></a>Açıklamalar  

 Bir işlemdeki her uygulama etki alanının <xref:System.AppDomain?displayProperty=nameWithType> kendisini temsil eden çalışma zamanında yönetilen bir nesnesi olabilir. Bu işlev, bu yönetilen nesneye karşılık gelen bir ICorDebugValue arabirim nesnesi alır <xref:System.AppDomain?displayProperty=nameWithType> .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]
