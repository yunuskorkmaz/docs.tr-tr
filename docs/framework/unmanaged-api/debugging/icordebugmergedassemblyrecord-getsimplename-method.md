---
description: ': Icordebugmergedassemblyrecord:: GetSimpleName metodu hakkında daha fazla bilgi edinin'
title: 'Icordebugmergedassemblyrecord:: GetSimpleName yöntemi'
ms.date: 03/30/2017
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
ms.openlocfilehash: e77a5cc7df009a5bc55a7eb952ead80e5f81f271
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650397"
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a>Icordebugmergedassemblyrecord:: GetSimpleName yöntemi

Derlemenin basit adını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
