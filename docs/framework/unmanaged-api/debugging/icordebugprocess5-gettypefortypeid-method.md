---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugProcess5:: GetTypeForTypeID Yöntemi'
title: ICorDebugProcess5::GetTypeForTypeID Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeForTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeForTypeID
helpviewer_keywords:
- GetTypeForTypeID method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeForTypeID method [.NET Framework debugging]
ms.assetid: e0eed5a8-fa6d-4818-bd00-7babcea30325
topic_type:
- apiref
ms.openlocfilehash: a18543b0afc867dc3796264ac1d08a775c73ca59
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746379"
---
# <a name="icordebugprocess5gettypefortypeid-method"></a>ICorDebugProcess5::GetTypeForTypeID Metodu

Bir tür tanımlayıcısını ICorDebugType değerine dönüştürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetTypeForTypeID(  
    [in] COR_TYPEID id, [  
    out] ICorDebugType **ppType  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `id`  
 'ndaki Tür tanımlayıcısı.  
  
 `ppType`  
 dışı ICorDebugType nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Bazı durumlarda, bir tür tanımlayıcısı döndüren yöntemler null `COR_TYPEID` değer döndürebilir. Bu değer `id` bağımsız değişken olarak geçirilirse, `GetTypeForTypeID` yöntemi başarısız olur ve döndürür `E_FAIL` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugProcess5 Arabirimi](icordebugprocess5-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
