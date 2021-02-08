---
description: ': Icordebugmergedassemblyrecord:: GetPublicKey Yöntemi hakkında daha fazla bilgi edinin'
title: 'Icordebugmergedassemblyrecord:: GetPublicKey Yöntemi'
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
ms.openlocfilehash: 15175b0d02773bcbce46bfaec9ce1de3021b7dde
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801104"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a>Icordebugmergedassemblyrecord:: GetPublicKey Yöntemi

Derlemenin ortak anahtarını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,
   [out] ULONG32 *pcbPublicKey,
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a>Parametreler  

 `cbPublicKey`  
 'ndaki Dizideki en fazla bayt sayısı `pbPublicKey` .  
  
 `pcbPublicKey`  
 dışı Diziye yazılan gerçek bayt sayısına yönelik bir işaretçi `pbPublicKey` .  
  
 `pbPublicKey`  
 dışı Derlemenin ortak anahtarını içeren bir bayt dizisine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
  
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
