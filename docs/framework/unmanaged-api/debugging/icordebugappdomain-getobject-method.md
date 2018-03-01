---
title: ICorDebugAppDomain::GetObject Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5f8206c6e5efbee8522f425f9078d99a39bbdd42
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomaingetobject-method"></a>ICorDebugAppDomain::GetObject Metodu
Ortak dil çalışma zamanı (CLR) uygulama etki alanı için bir arabirim işaretçisi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppObject`  
 [out] CLR uygulama etki alanını temsil eden bir Icordebugvalue arabirimi nesnesi adresini gösteren bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yönetilen varsa <xref:System.AppDomain?displayProperty=nameWithType> nesne kurmadı oluşturulan bu uygulama etki alanı için yöntem `S_FALSE` ve yerleştirir `NULL` içinde `*ppObject`.  
  
## <a name="remarks"></a>Açıklamalar  
 Her uygulama etki alanının bir işlemde bir yönetilen olabilir <xref:System.AppDomain?displayProperty=nameWithType> temsil ettiği çalışma zamanında nesne. Bu işlev bu yönetilen karşılık gelen bir Icordebugvalue arabirimi nesneyi alır <xref:System.AppDomain?displayProperty=nameWithType> nesnesi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]
