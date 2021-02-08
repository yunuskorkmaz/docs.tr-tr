---
description: ': Icordebugmergedassemblyrecord:: GetPublicKeyToken metodu hakkında daha fazla bilgi edinin'
title: 'Icordebugmergedassemblyrecord:: GetPublicKeyToken yöntemi'
ms.date: 03/30/2017
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
ms.openlocfilehash: 5ff870355ddf521012e93ed01a63e32358ca95cb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801073"
---
# <a name="icordebugmergedassemblyrecordgetpublickeytoken-method"></a>Icordebugmergedassemblyrecord:: GetPublicKeyToken yöntemi

Derlemenin ortak anahtar belirtecini alır.  
  
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
