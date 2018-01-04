---
title: "ICorDebugCode4::EnumerateVariableHomes yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugCode4.EnumerateVariableHomes
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode4::EnumerateVariableHomes
helpviewer_keywords:
- EnumerateVariableHomes method [.NET Framework debugging]
- ICorDebugCode4::EnumerateVariableHomes method [.NET Framework debugging]
ms.assetid: 802c01ff-8b80-4733-b6dd-03ab6ff7fa11
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1478ed89c216f9cd520bf1122571f09024283ac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcode4enumeratevariablehomes-method"></a>ICorDebugCode4::EnumerateVariableHomes yöntemi
Bir numaralandırıcı bir işlevde yerel değişkenleri ve bağımsız değişkenleri alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnumerateVariableHomes(  
    [out] ICorDebugVariableHomeEnum **ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppEnum`  
 Adresine bir işaretçi bir [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) yerel değişkenleri ve bir işlev bağımsız değişkenleri için bir numaralandırıcı arabirimi nesnesi.  
  
## <a name="remarks"></a>Açıklamalar  
 [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) arabiriminin nesnesidir Numaralandırılacak izin veren "ICorDebugEnum" arabirimden türetilmiş standart bir numaralandırıcı [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) nesneleri. Birden çok koleksiyonu içerebilir [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) işlevinde farklı noktalarda farklı ev varsa aynı yuva veya bağımsız değişken dizini nesneleri.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugCode4 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
