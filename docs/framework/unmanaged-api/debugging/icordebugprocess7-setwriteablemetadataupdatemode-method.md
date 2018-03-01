---
title: "ICorDebugProcess7::SetWriteableMetadataUpdateMode Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- cpp
api_name:
- ICorDebugProcess7.SetWriteableMetadataUpdateMode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 8589bba7-7304-45ba-9e31-7bf43dfd5c19
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e901fd623893b9c03e1b5835adc72c6bd225ead4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess7setwriteablemetadataupdatemode-method"></a>ICorDebugProcess7::SetWriteableMetadataUpdateMode Yöntemi
[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]  
  
 Hata ayıklayıcı bellek içi güncelleştirmeleri meta verilerinin hedef işlem içinde nasıl işlediğini yapılandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT SetWriteableMetadataUpdateMode(  
   WriteableMetadataUpdateMode flags  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `flags`  
 A [WriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md) hedef işlem meta veriler için bellek içi güncelleştirmeleri görünür olup olmayacağını belirten numaralandırma değeri (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) veya görünür (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) hata ayıklayıcı için.  
  
## <a name="remarks"></a>Açıklamalar  
 Düzenle ve devam et, bir profil oluşturucu hedef işleminin meta veri güncelleştirmeleri gelebilir veya <xref:System.Reflection.Emit?displayProperty=nameWithType>.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugProcess7 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
