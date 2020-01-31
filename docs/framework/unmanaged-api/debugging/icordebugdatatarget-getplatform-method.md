---
title: ICorDebugDataTarget::GetPlatform Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetPlatform Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetPlatform
helpviewer_keywords:
- GetPlatform method [.NET Framework debugging]
- ICorDebugDataTarget::GetPlatform method [.NET Framework debugging]
ms.assetid: 9ee96c9d-7a3d-4129-a6cc-7675c7f2dda4
topic_type:
- apiref
ms.openlocfilehash: 3654c94975d16e35d5c3d8e762730d17509a2c6d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788872"
---
# <a name="icordebugdatatargetgetplatform-method"></a>ICorDebugDataTarget::GetPlatform Metodu
Hedef işlemin çalıştığı işlemci mimarisi ve işletim sistemi dahil olmak üzere platform hakkında bilgi sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetPlatform([out] CorDebugPlatform * pTargetPlatform);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pTargetPlatform`  
 dışı Hedef platformu açıklayan [CorDebugPlatformEnum](cordebugplatform-enumeration.md) numaralandırması için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `CorDebugPlatformEnum` numaralandırma dönüş değeri [ICorDebug](icordebug-interface.md) arabirimi tarafından, işaretçi boyutu, adres alanı düzeni, YAZMAÇ kümesi, yönerge biçimi, bağlam düzeni ve çağırma kuralları gibi hedef işlemin ayrıntılarını belirlemede kullanılır.  
  
 `pTargetPlatform` değeri, kullanımdaki gerçek donanımı belirtmek yerine, hedef için Öykünülen bir platforma başvurabilir. Örneğin, Windows işletim sisteminin 64 bitlik bir sürümünde Windows on Windows (WOW) ortamında çalışan bir işlem [CorDebugPlatformEnum](cordebugplatform-enumeration.md) numaralandırmasının `CORDB_PLATFORM_WINDOWS_X86` değerini kullanmalıdır.  
  
 Bu yöntem başarılı olmalıdır. Başarısız olursa, hedef platform kullanılamaz olur. Yöntemi aşağıdaki nedenlerden dolayı başarısız olabilir:  
  
- Hedef için Öykünülen platform kullanılamıyor.  
  
- Hedef Platformdaki gerçek donanım kullanılamaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugDataTarget Arabirimi](icordebugdatatarget-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
