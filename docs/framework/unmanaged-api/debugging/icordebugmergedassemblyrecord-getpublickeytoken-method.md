---
title: ICorDebugMergedAssemblyRecord::GetPublicKeyToken yöntemi
ms.date: 03/30/2017
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71b70118d77deb7ad6879ed4bd48b1cd37122820
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414014"
---
# <a name="icordebugmergedassemblyrecordgetpublickeytoken-method"></a>ICorDebugMergedAssemblyRecord::GetPublicKeyToken yöntemi
Derlemenin ortak anahtar belirteci alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetPublicKeyToken(  
   [in] ULONG32 cbPublicKeyToken,   
   [out] ULONG32 *pcbPublicKeyToken,   
   [out, size_is(cbPublicKeyToken), length_is(*pcbPublicKeyToken)] BYTE pbPublicKeyToken[]  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cbPublicKeyToken`  
 [in] Bayt cinsinden en büyük sayısını `pbPublicKeyToken` dizi.  
  
 `pcbPublicKeyToken`  
 [out] Yazılan bayt sayısını gösteren bir işaretçi `pbPublicKeyToken` dizi.  
  
 `pbPublicKeyToken`  
 [out] Derlemenin ortak anahtar belirteci içeren bayt dizisi için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir derlemenin ortak anahtar belirteci, ortak anahtarı SHA1 karmasını, son sekiz bayttır.  
  
> [!NOTE]
>  Bu yöntem yalnızca .NET yerel ile kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugMergedAssemblyRecord Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
