---
title: 'Icordebugmergedassemblyrecord:: GetSimpleName yöntemi'
ms.date: 03/30/2017
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
ms.openlocfilehash: 11e43846f7b119933fb53bdf21423e28bbb792ac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710551"
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a>Icordebugmergedassemblyrecord:: GetSimpleName yöntemi

Derlemenin basit adını alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetSimpleName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `cchName`  
 'ndaki Arabellekteki karakterlerin sayısı `szName` .  
  
 `pcchName`  
 dışı Gerçekte arabelleğe yazılan karakter sayısına yönelik bir işaretçi `szName` .  
  
 `szName`  
 Karakter dizisine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Bu yöntem, bir derlemenin ("System. Collections" gibi) basit adını dosya uzantısı, sürüm, kültür veya ortak anahtar belirteci olmadan alır. <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType>Yönetilen koddaki özelliğine karşılık gelir.  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugMergedAssemblyRecord Arabirimi](icordebugmergedassemblyrecord-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
