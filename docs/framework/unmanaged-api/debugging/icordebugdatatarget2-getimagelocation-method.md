---
title: ICorDebugDataTarget2::GetImageLocation Yöntemi
ms.date: 03/30/2017
ms.assetid: 696afe71-5852-478d-a33f-b2d2dbc4b91f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c7acf08262c73df00a96cfb5c244cdfc352e51ea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789759"
---
# <a name="icordebugdatatarget2getimagelocation-method"></a>ICorDebugDataTarget2::GetImageLocation Yöntemi
Modülün temel adres bir modülün yolu döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetImageLocation(    [in] CORDB_ADDRESS baseAddress,  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `baseAddress`  
 [in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) modülün taban adresini gösteren bir değer.  
  
 `cchName`  
 [in] Modül yolu alacak arabellek karakter sayısı.  
  
 `pcchName`  
 [out] Yazılan karakter sayısı için bir işaretçi `szName` arabellek.  
  
 `szName`  
 [out] Modülün yolu.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu yöntem yalnızca .NET Native ile kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugDataTarget2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
