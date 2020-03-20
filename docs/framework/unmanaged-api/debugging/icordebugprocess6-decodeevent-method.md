---
title: ICorDebugProcess6::DecodeEvent Yöntemi
ms.date: 03/30/2017
ms.assetid: 1453bc0c-6e0d-4d5a-b176-22607f8a3e6c
ms.openlocfilehash: a0b77724a5a70461073d554a9794c5a904f6a363
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178575"
---
# <a name="icordebugprocess6decodeevent-method"></a>ICorDebugProcess6::DecodeEvent Yöntemi
Özel olarak hazırlanmış yerel özel durum hata ayıklama olaylarının yükünde kapsüllenmiş yönetilen hata ayıklama olaylarını çözme.  
  
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
 [içinde] Yönetilen hata ayıklama olayı hakkında bilgi içeren yerel bir özel durum hata ayıklama olayından bir bayt diziiçin işaretçi.  
  
 `countBytes`  
 [içinde] Bayt dizisindeki `pRecord` öğelerin sayısı.  
  
 `format`  
 [içinde] Yönetilmeyen hata ayıklama olayının biçimini belirten [bir CorDebugRecordFormat](cordebugrecordformat-enumeration.md) numaralandırma üyesi.  
  
 `dwFlags`  
 [içinde] Hedef mimariye bağlı olan ve hata ayıklama olayı hakkında ek bilgiler belirten bir bit alanı. Windows sistemleri için, [CorDebugDecodeEventFlagsWindows](cordebugdecodeeventflagswindows-enumeration.md) numaralandırma üyesi olabilir.  
  
 `dwThreadId`  
 [içinde] Özel durum atıldığı iş parçacığının işletim sistemi tanımlayıcısı.  
  
 `ppEvent`  
 [çıkış] Çözülmüş yönetilen hata ayıklama olayını temsil eden bir [ICorDebugDebugEvent](icordebugdebugevent-interface.md) nesnesinin adresine işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native ile kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorDebug.idl, CorDebug.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugProcess6 Arabirimi](icordebugprocess6-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
