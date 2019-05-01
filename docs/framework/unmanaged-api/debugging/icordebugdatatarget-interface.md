---
title: ICorDebugDataTarget Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget
helpviewer_keywords:
- ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: df5f05be-bed7-4f3c-bc89-dbb435d79a0b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 480fc27bd41f7ca559ceee379b7f6f81c94da0ba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989202"
---
# <a name="icordebugdatatarget-interface"></a>ICorDebugDataTarget Arabirimi
Belirli bir hedef işleme erişim sağlayan bir geri arama arabirimi sunar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetPlatform Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)|İşlemci mimarisi ve hedef işlem üzerinde çalıştığı işletim sistemi dahil olmak üzere platform hakkında bilgi sağlar.|  
|[ReadVirtual Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-readvirtual-method.md)|Belirtilen adres'ten itibaren bitişik bellek bloğunu alır ve sağlanan arabellek döndürür.|  
|[GetThreadContext Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getthreadcontext-method.md)|Belirtilen iş parçacığı için geçerli iş parçacığı bağlamını ister.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugDataTarget` ve metotlarını şu özelliklere sahiptir:  
  
- Hata ayıklama hizmetlerini, bellek ve diğer verileri hedef işlemde erişmek için bu arabirimdeki yöntemleri çağırır.  
  
- Hata ayıklayıcı istemcisi bu arabirimi belirli hedef (örneğin, canlı bir işlem ya da bir bellek dökümü) için uygun şekilde uygulamalıdır.  
  
- `ICorDebugDataTarget` Yöntemleri çağrılacak yalnızca diğer uygulanmış olan yöntemlerle içinde `ICorDebug*` arabirimleri. Bu, hata ayıklayıcı istemcisi olan denetim üzerinde hangi iş parçacığı üzerinde ve çağrılan sağlar.  
  
- `ICorDebugDataTarget` Uygulama hedef hakkında güncel bilgiler her zaman döndürmesi gerekir.  
  
 Hedef işlem durdurulması ve herhangi bir şekilde değişmemiş `ICorDebug*` arabirimleri (ve bu nedenle `ICorDebugDataTarget` yöntemleri) adı verilir. Hedef canlı bir işlem ve durum değişikliklerini ise [Iclrdebugging::openvirtualprocess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) yöntemi olan yeniden değiştirme Icordebugprocess örneği sağlamak için çağrılabilir.  
  
> [!NOTE]
>  Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
