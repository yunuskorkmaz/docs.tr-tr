---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugProcess3:: SetEnableCustomNotification yöntemi'
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
ms.openlocfilehash: 71d1d23b1fa4ba16b26b7c9bacf7fb5cec5e5074
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746481"
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
 [in] `true` özel hata ayıklayıcı bildirimlerini etkinleştirmek için; `false` bildirimleri devre dışı bırakmak için. `false` varsayılan değerdir.  
  
## <a name="remarks"></a>Açıklamalar  

 Ne zaman `fEnable` ayarlandığında `true` , yöntemine yapılan çağrılar <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> bir [ICorDebugManagedCallback3:: CustomNotification](icordebugmanagedcallback3-customnotification-method.md) geri çağırması tetikler. Bildirimler varsayılan olarak devre dışıdır; Bu nedenle, hata ayıklayıcı, bildiği ve işlemek istediği herhangi bir bildirim türü belirtmelidir. [ICorDebugClass](icordebug-interface.md) sınıfı, uygulama etki alanı tarafından kapsamlandırdığı için, hata ayıklayıcının `SetEnableCustomNotification` tüm işlem genelinde bildirimi almasını istemesi durumunda, işlemdeki her uygulama etki alanı için çağrı yapmanız gerekir.  
  
 .NET Framework 4 ' te başlayarak, tek desteklenen bildirim bir çapraz iş parçacığı bağımlılığı bildirimidir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugProcess3 Arabirimi](icordebugprocess3-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
