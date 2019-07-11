---
title: ICorDebugProcess6::DecodeEvent Yöntemi
ms.date: 03/30/2017
ms.assetid: 1453bc0c-6e0d-4d5a-b176-22607f8a3e6c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 30df2d4a958b82a5a877b5d3efe5936f6498433b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736464"
---
# <a name="icordebugprocess6decodeevent-method"></a>ICorDebugProcess6::DecodeEvent Yöntemi
Özel olarak hazırlanmış yerel özel durum hata ayıklama olaylarını yükteki kapsüllenmiş yönetilen hata ayıklama olaylarını kodunu çözer.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT DecodeEvent(  
        [in, length_is(countBytes), size_is(countBytes)]  const BYTE pRecord[],  
        [in] DWORD countBytes,  
        [in] CorDebugRecordFormat format,  
        [in] DWORD dwFlags,   
        [in] DWORD dwThreadId,   
        [out] ICorDebugDebugEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pRecord`  
 [in] Bir bayt dizisine bir işaretçi yerel özel durum hata ayıklama olayından yönetilen hata ayıklama olay hakkında bilgiler içerir.  
  
 `countBytes`  
 [in] İçindeki öğelerin sayısını `pRecord` bayt dizisi.  
  
 `format`  
 [in] A [CorDebugRecordFormat](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md) yönetilmeyen hata ayıklama olayı biçimini belirten numaralandırma üyesi.  
  
 `dwFlags`  
 [in] Hedef mimarisine bağlıdır ve hata ayıklama olay hakkında ek bilgi belirten bir bit alanı. Windows sistemleri için bir üyesi olabilir [CorDebugDecodeEventFlagsWindows](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md) sabit listesi.  
  
 `dwThreadId`  
 [in] Özel durumun oluştuğu iş parçacığı işletim sistemi tanımlayıcısı.  
  
 `ppEvent`  
 [out] Adresine bir işaretçi bir [Icordebugdebugevent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) kodu çözülmüş yönetilen hata ayıklama olayı temsil eden nesne.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu yöntem yalnızca .NET Native ile kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugProcess6 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
