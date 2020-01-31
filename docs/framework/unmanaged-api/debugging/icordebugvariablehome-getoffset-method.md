---
title: 'Icordebugvariablehome:: GetOffset Yöntemi'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetOffset
helpviewer_keywords:
- ICorDebugVariableHome::GetOffset method [.NET Framework debugging]
- GetOffset method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: f025c2e5-3f6c-4be8-9ffe-c8b214617dfe
topic_type:
- apiref
ms.openlocfilehash: a6f93ec3c7ffe415c41dcf094dbde2f0a08969f6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790991"
---
# <a name="icordebugvariablehomegetoffset-method"></a>Icordebugvariablehome:: GetOffset Yöntemi
Bir değişken için temel kaydın konumunu alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pOffset`  
 dışı Temel kayıttaki fark.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi aşağıdaki değerleri döndürür:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Değişken, YAZMAÇ göreli bir bellek konumudur.|  
|`E_FAIL`|Değişken, YAZMAÇ göreli bir bellek konumunda değil.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugVariableHome Arabirimi](icordebugvariablehome-interface.md)
