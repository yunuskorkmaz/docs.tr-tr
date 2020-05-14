---
title: ICorDebugVariableHome Arabirimi
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugVariableHome
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome
helpviewer_keywords:
- ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 76f2bf3b-759f-4eed-bce7-119415b25915
topic_type:
- apiref
ms.openlocfilehash: caf6a24207be98be9afb10be2bd027b51405fa3b
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396547"
---
# <a name="icordebugvariablehome-interface"></a>ICorDebugVariableHome Arabirimi
Bir işlevin yerel bir değişkenini veya bağımsız değişkenini temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetArgumentIndex Yöntemi](icordebugvariablehome-getargumentindex-method.md)|Bir işlev bağımsız değişkeninin dizinini alır.|  
|[GetCode Yöntemi](icordebugvariablehome-getcode-method.md)|Bu nesneyi içeren "ICorDebugCode" örneğini alır `ICorDebugVariableHome` .|  
|[GetLiveRange Yöntemi](icordebugvariablehome-getliverange-method.md)|Bu değişkenin canlı olduğu yerel aralığı alır.|  
|[GetLocationType Yöntemi](icordebugvariablehome-getlocationtype-method.md)|Değişkenin yerel konumunun türünü alır.|  
|[GetOffset Yöntemi](icordebugvariablehome-getoffset-method.md)|Bir değişken için temel kaydın konumunu alır.|  
|[GetRegister Yöntemi](icordebugvariablehome-getregister-method.md)|Konum türü olan bir değişken içeren kaydı `VLT_REGISTER` ve konum türü olan bir değişken için temel kaydı alır `VLT_REGISTER_RELATIVE` .|  
|[GetSlotIndex Yöntemi](icordebugvariablehome-getslotindex-method.md)|Yerel bir değişkenin yönetilen yuva dizinini alır.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod parçası adlı [ICorDebugCode4](icordebugcode4-interface.md) nesnesini kullanır `pCode4` .  
  
```cpp  
ICorDebugCode4 *pCode4 = NULL;  
pCode->QueryInterface(IID_ICorDebugCode4, &pCode4);  
  
ICorDebugVariableEnum *pVarLocEnum = NULL;  
pCode4->EnumerateVariableHomes(&pVarLocEnum);  
  
// retrieve local variables and arguments  
ULONG celt = 0;  
pVarLocEnum->GetCount(&celt);  
ICorDebugVariableHome **homes = new ICorDebugVariableHome *[celt];  
ULONG celtFetched = 0;  
pVarLocEnum->Next(celt, homes, &celtFetched);  
  
for (int i = 0; i < celtFetched; i++)  
{  
    VariableLocationType locType = VLT_INVALID;  
    homes[i].GetLocationType(&locType);  
    switch (locType)  
    {  
    case VLT_REGISTER:  
        CorDebugRegister register = 0;  
        locals[i].GetRegister(&register);  
        // now we know which register it is in  
        break;  
    case VLT_REGISTER_RELATIVE:  
        CorDebugRegister baseRegister = 0;  
        LONG offset = 0;  
        locals[i].GetRegister(&register);  
        locals[i].GetOffset(&offset);  
        // now we know the register-relative offset  
        break;  
    case VLT_INVALID:  
        // handle case where we can't access the location  
        break;  
    }  
}  
```  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [ICorDebugVariableHomeEnum Arabirimi](icordebugvariablehomeenum-interface.md)
