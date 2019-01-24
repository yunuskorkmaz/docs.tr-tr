---
title: ICorDebugMergedAssemblyRecord::GetCulture yöntemi
ms.date: 03/30/2017
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0fd66ee28ca276aaa31e1e92a42d0fd88ff00d89
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654970"
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a>ICorDebugMergedAssemblyRecord::GetCulture yöntemi
Derlemenin kültür adı dizesi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,   
   [out] ULONG32 *pcchCulture,   
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cchCulture`  
 [in] Karakter sayısı `szCulture` arabellek.  
  
 `pcchCulture`  
 [out] Gerçekte yazılan karakter sayısını `szCulture` arabellek.  
  
 `szCulture`  
 [out] Kültür adı içeren bir karakter dizisi.  
  
## <a name="remarks"></a>Açıklamalar  
 Kültür adı "en-US" (için İngilizce (ABD) kültürünün) veya "belirsiz" (için bağımsız bir kültür) gibi bir kültür tanımlayan benzersiz bir dizedir.  
  
> [!NOTE]
>  Bu yöntem yalnızca .NET Native ile kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorDebugMergedAssemblyRecord Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
