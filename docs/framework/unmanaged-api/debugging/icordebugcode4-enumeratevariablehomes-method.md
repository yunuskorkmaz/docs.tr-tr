---
description: 'Hakkında daha fazla bilgi edinin: ICorDebugCode4:: Enumeratevariableevler yöntemi'
title: 'ICorDebugCode4:: Enumeratevariableevler yöntemi'
ms.date: 03/30/2017
api_name:
- ICorDebugCode4.EnumerateVariableHomes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode4::EnumerateVariableHomes
helpviewer_keywords:
- EnumerateVariableHomes method [.NET Framework debugging]
- ICorDebugCode4::EnumerateVariableHomes method [.NET Framework debugging]
ms.assetid: 802c01ff-8b80-4733-b6dd-03ab6ff7fa11
topic_type:
- apiref
ms.openlocfilehash: 58f5f9063cd22356efd3a77ece9fb43b6b4c1062
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710965"
---
# <a name="icordebugcode4enumeratevariablehomes-method"></a>ICorDebugCode4:: Enumeratevariableevler yöntemi

Bir işlevdeki yerel değişkenlere ve bağımsız değişkenlere bir Numaralandırıcı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumerateVariableHomes(  
    [out] ICorDebugVariableHomeEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `ppEnum`  
 Bir işlevdeki yerel değişkenler ve bağımsız değişkenler için bir Numaralandırıcı olan [ıcordebugvariablehomeenum](icordebugvariablehomeenum-interface.md) arabirim nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 [Icordebugvariablehomeenum](icordebugvariablehomeenum-interface.md) arabirimi nesnesi, [ıcordebugvariablehome](icordebugvariablehome-interface.md) nesnelerini Listeletmanızı sağlayan "ıcordebugger genum" arabiriminden türetilmiş standart bir Numaralandırıcı. Koleksiyonda farklı noktalarda farklı evler varsa, koleksiyonda aynı yuva veya bağımsız değişken dizini için birden çok [ıcordebugvariablehome](icordebugvariablehome-interface.md) nesnesi bulunabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugCode4 Arabirimi](icordebugcode4-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
