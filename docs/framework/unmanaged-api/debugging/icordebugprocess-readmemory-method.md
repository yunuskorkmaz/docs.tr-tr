---
title: "ICorDebugProcess::ReadMemory Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.ReadMemory
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::ReadMemory
helpviewer_keywords:
- ReadMemory method [.NET Framework debugging]
- ICorDebugProcess::ReadMemory method [.NET Framework debugging]
ms.assetid: 28e4b2f6-9589-445c-be24-24a3306795e7
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2d282e83fc7b7632bde850ac1341eef938d8e0dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessreadmemory-method"></a>ICorDebugProcess::ReadMemory Yöntemi
Bu işlem için bellek belirtilen alan okur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ReadMemory(  
    [in]  CORDB_ADDRESS address,   
    [in]  DWORD size,  
    [out, size_is(size), length_is(size)] BYTE buffer[],  
    [out] SIZE_T *read);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `address`  
 [in] A `CORDB_ADDRESS` okumak için bellek taban adresini belirten değer.  
  
 `size`  
 [in] Bellekten okunacak bayt sayısı.  
  
 `buffer`  
 [out] Bellek içeriğini alır arabelleği.  
  
 `read`  
 [out] Bir işaretçi bayt sayısı belirtilen arabelleğe aktarılan.  
  
## <a name="remarks"></a>Açıklamalar  
 `ReadMemory` Yöntemi ayıklayıcı yönetilmeyen bölümü tarafından kullanılan bellek bölümlerinin incelemek için birlikte çalışma hata ayıklama tarafından kullanılmak üzere öncelikle amaçlanmıştır. Bu yöntem, Microsoft Ara dili (MSIL) kodu ve yerel JIT derlenmiş kod okumak için de kullanılabilir.  
  
 Tüm yönetilen kesme noktalarını döndürülür verileri kaldırılacak `buffer` parametresi. Yerel kesme noktaları ayarlayın ayarlama yapılmayan yapılan [Icordebugprocess2::setunmanagedbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).  
  
 Önbelleğe alma işlemi bellek gerçekleştirilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
