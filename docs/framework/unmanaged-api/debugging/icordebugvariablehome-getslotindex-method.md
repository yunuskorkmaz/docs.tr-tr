---
description: ': Icordebugvariablehome:: Getslotındex yöntemi hakkında daha fazla bilgi edinin'
title: 'Icordebugvariablehome:: Getslotındex yöntemi'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetSlotIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetSlotIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetSlotIndex method [.NET Framework debugging]
- GetSlotIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 966da50d-5665-4fff-bf7b-1c72bbadd9a4
topic_type:
- apiref
ms.openlocfilehash: 7f6ee01c2bfcee4c78f8463a7cefac1f90a3295f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790652"
---
# <a name="icordebugvariablehomegetslotindex-method"></a>Icordebugvariablehome:: Getslotındex yöntemi

Yerel bir değişkenin yönetilen yuva dizinini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pSlotIndex`  
 dışı Yerel bir değişkenin yuva dizinine yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntemi aşağıdaki değerleri döndürür.  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem çağrısı ' de bir yuva dizini değeri döndürdü `pSlotIndex` .|  
|`E_FAIL`|Geçerli [ıcordebugvariablehome](icordebugvariablehome-interface.md) örneği bir işlev bağımsız değişkenini temsil eder.|  
  
## <a name="remarks"></a>Açıklamalar  

 Bu yerel değişken için meta verileri almak için yuva dizini kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugVariableHome Arabirimi](icordebugvariablehome-interface.md)
