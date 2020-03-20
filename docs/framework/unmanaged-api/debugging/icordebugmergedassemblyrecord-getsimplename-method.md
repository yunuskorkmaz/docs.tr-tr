---
title: ICorDebugMergedAssemblyRecord::GetSimpleName Yöntemi
ms.date: 03/30/2017
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
ms.openlocfilehash: 99ba27171e129e8725c3e0555a6991ef08b893da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178714"
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a>ICorDebugMergedAssemblyRecord::GetSimpleName Yöntemi
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
 [içinde] `szName` Arabellekteki karakter sayısı.  
  
 `pcchName`  
 [çıkış] Arabelleğe yazılan karakter sayısına `szName` işaretçi.  
  
 `szName`  
 Karakter dizisiiçin bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, dosya uzantısı, sürüm, kültür veya ortak anahtar belirteci olmadan bir derlemenin ("System.Collections" gibi) basit adını alır. Yönetilen koddaki <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> özelliğe karşılık gelir.  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native ile kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorDebug.idl, CorDebug.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugMergedAssemblyRecord Arabirimi](icordebugmergedassemblyrecord-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
