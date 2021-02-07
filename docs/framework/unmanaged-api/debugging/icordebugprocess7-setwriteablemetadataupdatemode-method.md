---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugProcess7:: SetWriteableMetadataUpdateMode yöntemi'
title: ICorDebugProcess7::SetWriteableMetadataUpdateMode Yöntemi
ms.date: 03/30/2017
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
ms.openlocfilehash: 86ece68e160fbd61f44adcf495656c7b5d6b5153
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691269"
---
# <a name="icordebugprocess7setwriteablemetadataupdatemode-method"></a>ICorDebugProcess7::SetWriteableMetadataUpdateMode Yöntemi

[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]  
  
 Hata ayıklayıcının, hedef işlem içindeki meta veriler için bellek içi güncelleştirmeleri nasıl işlediğini yapılandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT SetWriteableMetadataUpdateMode(  
   WriteableMetadataUpdateMode flags  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `flags`  
 Hedef işlemdeki meta verilere yönelik bellek güncelleştirmelerinin görünür olup olmadığını belirten bir [WriteableMetadataUpdateMode](writeablemetadataupdatemode-enumeration.md) numaralandırma değeri ( `WriteableMetadataUpdateMode::AlwaysShowUpdates` ) ve `WriteableMetadataUpdateMode::LegacyCompatPolicy` hata ayıklayıcıya görünür değil.  
  
## <a name="remarks"></a>Açıklamalar  

 Hedef işlemin meta verilerinde yapılan güncelleştirmeler, düzenleme ve devam etme, profil oluşturucu veya ile gelebilir <xref:System.Reflection.Emit?displayProperty=nameWithType> .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugProcess7 Arabirimi](icordebugprocess7-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
