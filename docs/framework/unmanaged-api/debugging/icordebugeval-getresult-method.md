---
title: ICorDebugEval::GetResult Metodu
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
- ICorDebugEval.GetResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::GetResult
helpviewer_keywords:
- ICorDebugEval::GetResult method [.NET Framework debugging]
- GetResult method [.NET Framework debugging]
ms.assetid: 50dbb9af-58a1-41f4-b56d-3da20011884f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7f3d17e28686d1697417dd380782b1f037e0b5a4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugevalgetresult-method"></a>ICorDebugEval::GetResult Metodu
Bu değerlendirme sonuçlarını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetResult (  
    [out] ICorDebugValue    **ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppResult`  
 [out] İşaretçi değerlendirme normalde tamamlarsa, bu değerlendirme sonuçlarını temsil eden Icordebugvalue nesne adresine.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetResult` Yöntemi, yalnızca değerlendirme tamamlandıktan sonra geçerlidir.  
  
 Değerlendirme normalde tamamlarsa `ppResult` sonuçları belirtir. Bir özel durumla sona ererse, oluşturulan özel durum oluşur. Değerlendirme için yeni bir nesne varsa, yeni nesne başvurusunu sonucudur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
