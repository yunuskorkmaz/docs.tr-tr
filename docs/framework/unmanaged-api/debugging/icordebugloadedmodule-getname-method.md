---
title: ICorDebugLoadedModule::GetName Yöntemi
ms.date: 03/30/2017
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
ms.openlocfilehash: c18af45184f5a9485e13b9d4789bff2c570834cc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731858"
---
# <a name="icordebugloadedmodulegetname-method"></a>ICorDebugLoadedModule::GetName Yöntemi

Yüklenen modülün adını alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `cchName`  
 'ndaki Arabellekteki karakterlerin sayısı `szName` .  
  
 `pcchName`  
 dışı Gerçekte arabelleğe yazılan karakter sayısına yönelik bir işaretçi `szName` .  
  
 `szName`  
 dışı Yüklenen modülün adını içeren bir karakter dizisi.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugLoadedModule Arabirimi](icordebugloadedmodule-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
