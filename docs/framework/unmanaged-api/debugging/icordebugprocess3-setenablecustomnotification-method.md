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
ms.openlocfilehash: f2f365f3fe1568f2dd3bad677dd77a13946002e1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792462"
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
 `fEnable` `true`olarak ayarlandığında <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> yöntemine yapılan çağrılar bir [ICorDebugManagedCallback3:: CustomNotification](icordebugmanagedcallback3-customnotification-method.md) geri çağırması tetikler. Bildirimler varsayılan olarak devre dışıdır; Bu nedenle, hata ayıklayıcı, bildiği ve işlemek istediği herhangi bir bildirim türü belirtmelidir. [ICorDebugClass](icordebug-interface.md) sınıfı, uygulama etki alanı tarafından kapsamlandırdığı için, hata ayıklayıcının tüm işlem genelinde bildirimi almasını istiyorsa, işlemdeki her uygulama etki alanı için `SetEnableCustomNotification` çağırmalıdır.  
  
 .NET Framework 4 ' te başlayarak, tek desteklenen bildirim bir çapraz iş parçacığı bağımlılığı bildirimidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugProcess3 Arabirimi](icordebugprocess3-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
