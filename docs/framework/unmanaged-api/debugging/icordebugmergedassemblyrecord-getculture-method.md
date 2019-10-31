---
title: 'Icordebugmergedassemblyrecord:: GetCulture yöntemi'
ms.date: 03/30/2017
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
ms.openlocfilehash: f39a1f17c80d27a38c0f2a8a516405f72c79bbcf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131419"
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a>Icordebugmergedassemblyrecord:: GetCulture yöntemi
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
 'ndaki `szCulture` arabelleğindeki karakterlerin sayısı.  
  
 `pcchCulture`  
 dışı Gerçekten `szCulture` arabelleğine yazılan karakterlerin sayısı.  
  
 `szCulture`  
 dışı Kültür adını içeren bir karakter dizisi.  
  
## <a name="remarks"></a>Açıklamalar  
 Kültür adı, "en-US" (Ingilizce (Birleşik Devletler) kültürü için) veya "nötr" (nötr kültür için) gibi bir kültürü tanımlayan benzersiz bir dizedir.  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugMergedAssemblyRecord Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
