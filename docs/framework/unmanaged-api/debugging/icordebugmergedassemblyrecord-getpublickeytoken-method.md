---
title: ICorDebugMergedAssemblyRecord::GetPublicKeyToken Yöntemi
ms.date: 03/30/2017
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
ms.openlocfilehash: 79df5c3e8b07879a26272f595664abab011101bd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178717"
---
# <a name="icordebugmergedassemblyrecordgetpublickeytoken-method"></a>ICorDebugMergedAssemblyRecord::GetPublicKeyToken Yöntemi
Meclisin ortak anahtar belirteci alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetPublicKeyToken(  
   [in] ULONG32 cbPublicKeyToken,
   [out] ULONG32 *pcbPublicKeyToken,
   [out, size_is(cbPublicKeyToken), length_is(*pcbPublicKeyToken)] BYTE pbPublicKeyToken[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cbPublicKeyToken`  
 [içinde] `pbPublicKeyToken` Dizideki maksimum bayt sayısı.  
  
 `pcbPublicKeyToken`  
 [çıkış] Diziye yazılan gerçek bayt sayısına `pbPublicKeyToken` işaretçi.  
  
 `pbPublicKeyToken`  
 [çıkış] Derlemenin ortak anahtar belirteci içeren bir bayt dizisiiçin işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir derlemenin ortak anahtar belirteci, bir SHA1 karmasının son sekiz baytıdır.  
  
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
