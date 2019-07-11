---
title: ICorDebugFunction::GetILCode Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetILCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetILCode
helpviewer_keywords:
- ICorDebugFunction::GetILCode method [.NET Framework debugging]
- GetILCode method [.NET Framework debugging]
ms.assetid: f794dd47-a7cd-47f6-96e9-a41a4dae8e72
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e32ce10b708afa5741d83cbd05f14accb4b2014f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754675"
---
# <a name="icordebugfunctiongetilcode-method"></a>ICorDebugFunction::GetILCode Metodu
ICorDebugFunction Bu nesneyle ilişkili Microsoft Ara dili (MSIL) kodu temsil eden Icordebugcode örneği alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetILCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppCode`  
 [out] Bir işaretçi `ICorDebugCode` örneği veya işlevin MSIL derlenmedi yoksa null.  
  
## <a name="remarks"></a>Açıklamalar  
 Düzenle ve devam et izin veriyorsa bu işlev üzerinde `GetILCode` yöntemi, bu işlevin düzenlenen kodu ortak dil çalışma zamanı (CLR) sürümüne karşılık gelen MSIL kodu alırsınız.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
