---
title: "ICorDebugProcess6::DecodeEvent Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 1453bc0c-6e0d-4d5a-b176-22607f8a3e6c
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 753dce06d9481165bd2f0f1e49fe3c50fc6b3c40
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess6decodeevent-method"></a>ICorDebugProcess6::DecodeEvent Yöntemi
Özel olarak hazırlanmış yerel özel durum hata ayıklama olayları yükünde kapsüllenmiş yönetilen hata ayıklama olayları kodunu çözer.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT DecodeEvent(  
        [in, length_is(countBytes), size_is(countBytes)]  const BYTE pRecord[],  
        [in] DWORD countBytes,  
        [in] CorDebugRecordFormat format,  
        [in] DWORD dwFlags,   
        [in] DWORD dwThreadId,   
        [out] ICorDebugDebugEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pRecord`  
 [in] Bir bayt dizisine bir işaretçi yerel özel durum hata ayıklama olaydan yönetilen hata ayıklama olayla ilgili bilgiler içerir.  
  
 `countBytes`  
 [in] Öğe sayısı `pRecord` bayt dizisi.  
  
 `format`  
 [in] A [CorDebugRecordFormat](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md) yönetilmeyen hata ayıklama olayı biçimini belirten numaralandırma üyesi.  
  
 `dwFlags`  
 [in] Hedef mimarisine bağlıdır ve hata ayıklama olayla ilgili ek bilgi belirten bir bit alanı. Windows sistemleri için bir üyesi olabilir [CorDebugDecodeEventFlagsWindows](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md) numaralandırması.  
  
 `dwThreadId`  
 [in] Özel durum oluştu iş parçacığı işletim sistemi tanımlayıcısı.  
  
 `ppEvent`  
 [out] Adresine bir işaretçi bir [Icordebugdebugevent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) kodu çözülmüş yönetilen hata ayıklama olayı temsil eden nesne.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu yöntem yalnızca .NET yerel ile kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugProcess6 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
