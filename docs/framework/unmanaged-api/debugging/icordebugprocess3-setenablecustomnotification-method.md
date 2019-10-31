---
title: ICorDebugProcess3::SetEnableCustomNotification Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess3.SetEnableCustomNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess3::SetEnableCustomNotification
helpviewer_keywords:
- ICorDebugProcess3::SetEnableCustomNotification method [.NET Framework debugging]
- SetEnableCustomNotification method [.NET Framework debugging]
ms.assetid: afd88ee9-2589-4461-a75a-9b6fe55a2525
topic_type:
- apiref
ms.openlocfilehash: ec60274648315c4fa38f3832d8d39c1a269956b1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129700"
---
# <a name="icordebugprocess3setenablecustomnotification-method"></a>ICorDebugProcess3::SetEnableCustomNotification Yöntemi
Belirtilen türdeki özel hata ayıklayıcı bildirimlerini etkinleştir ve devre dışı bırakır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetEnableCustomNotification(ICorDebugClass * pClass,  
                                    BOOL fEnable);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pClass`  
 'ndaki Özel hata ayıklayıcı bildirimlerini belirten tür.  
  
 `fEnable`  
 [in] özel hata ayıklayıcı bildirimlerini etkinleştirmek için `true`; bildirimleri devre dışı bırakmak için `false`. Varsayılan değer `false` şeklindedir.  
  
## <a name="remarks"></a>Açıklamalar  
 `fEnable` `true`olarak ayarlandığında <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> yöntemine yapılan çağrılar bir [ICorDebugManagedCallback3:: CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) geri çağırması tetikler. Bildirimler varsayılan olarak devre dışıdır; Bu nedenle, hata ayıklayıcı, bildiği ve işlemek istediği herhangi bir bildirim türü belirtmelidir. [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) sınıfı, uygulama etki alanı tarafından kapsamlandırdığı için, hata ayıklayıcının tüm işlem genelinde bildirimi almasını istiyorsa, işlemdeki her uygulama etki alanı için `SetEnableCustomNotification` çağırmalıdır.  
  
 .NET Framework 4 ' te başlayarak, tek desteklenen bildirim bir çapraz iş parçacığı bağımlılığı bildirimidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugProcess3 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
