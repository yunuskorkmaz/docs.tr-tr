---
title: 'Icordebugmergedassemblyrecord:: GetPublicKeyToken yöntemi'
ms.date: 03/30/2017
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
ms.openlocfilehash: c642d8af7e84288d3aa8912372a2f169b8f22503
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710577"
---
# <a name="icordebugmergedassemblyrecordgetpublickeytoken-method"></a>Icordebugmergedassemblyrecord:: GetPublicKeyToken yöntemi

Derlemenin ortak anahtar belirtecini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetPublicKeyToken(  
   [in] ULONG32 cbPublicKeyToken,
   [out] ULONG32 *pcbPublicKeyToken,
   [out, size_is(cbPublicKeyToken), length_is(*pcbPublicKeyToken)] BYTE pbPublicKeyToken[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `cbPublicKeyToken`  
 'ndaki Dizideki en fazla bayt sayısı `pbPublicKeyToken` .  
  
 `pcbPublicKeyToken`  
 dışı Diziye yazılan gerçek bayt sayısına yönelik bir işaretçi `pbPublicKeyToken` .  
  
 `pbPublicKeyToken`  
 dışı Derlemenin ortak anahtar belirtecini içeren bir bayt dizisine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Bir derlemenin ortak anahtar belirteci, ortak anahtarının SHA1 karmasının son sekiz bayttır.  
  
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
