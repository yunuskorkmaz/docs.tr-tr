---
title: ICorDebugEval::GetResult Metodu
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7e160eddf667b542929c8dd3790de666a8e8bb77
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413065"
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
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
