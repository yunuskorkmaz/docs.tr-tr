---
title: ICorDebugMergedAssemblyRecord::GetCulture Yöntemi
ms.date: 03/30/2017
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
ms.openlocfilehash: ad54a93b16e803170987dd56d8063669f7e67f94
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178748"
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a>ICorDebugMergedAssemblyRecord::GetCulture Yöntemi
Derlemenin kültür adı dizesini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,
   [out] ULONG32 *pcchCulture,
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cchCulture`  
 [içinde] `szCulture` Arabellekteki karakter sayısı.  
  
 `pcchCulture`  
 [çıkış] `szCulture` Arabelleğe yazılan karakter sayısı.  
  
 `szCulture`  
 [çıkış] Kültür adını içeren bir karakter dizisi.  
  
## <a name="remarks"></a>Açıklamalar  
 Kültür adı, "en-US" (İngilizce (ABD) kültürü veya "tarafsız" (tarafsız bir kültür için) gibi bir kültürü tanımlayan benzersiz bir dizedir.  
  
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
