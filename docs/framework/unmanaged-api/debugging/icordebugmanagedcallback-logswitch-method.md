---
title: ICorDebugManagedCallback::LogSwitch Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LogSwitch
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LogSwitch
helpviewer_keywords:
- LogSwitch method [.NET Framework debugging]
- ICorDebugManagedCallback::LogSwitch method [.NET Framework debugging]
ms.assetid: 0ac59d27-783f-4a87-b7a8-baa3ccc54582
topic_type:
- apiref
ms.openlocfilehash: db6ccd63bbeadd7dcff1c7f8491b59017d431d12
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720704"
---
# <a name="icordebugmanagedcallbacklogswitch-method"></a>ICorDebugManagedCallback::LogSwitch Yöntemi

Hata ayıklayıcıyı bir ortak dil çalışma zamanı (CLR) yönetilen iş parçacığının, <xref:System.Diagnostics.Switch> bir hata ayıklama/izleme anahtarı oluşturmak, değiştirmek veya silmek için sınıfında bir yöntemi çağırdığını bildirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT LogSwitch (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] ULONG                ulReason,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pParentName);  
```  
  
## <a name="parameters"></a>Parametreler  

 `PAppDomain`  
 'ndaki Bir hata ayıklama/izleme anahtarını oluşturan, değiştiren veya silen yönetilen iş parçacığını içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.  
  
 `pThread`  
 'ndaki Yönetilen iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.  
  
 `lLevel`  
 'ndaki Olay günlüğüne yazılan açıklayıcı iletinin önem derecesini gösteren bir değer.  
  
 `ulReason`  
 'ndaki Hata ayıklama/izleme anahtarında gerçekleştirilen işlemi belirten [LogSwitchCallReason](logswitchcallreason-enumeration.md) numaralandırması değeri.  
  
 `pLogSwitchName`  
 'ndaki Hata ayıklama/izleme anahtarının adına yönelik bir işaretçi.  
  
 `pParentName`  
 'ndaki Hata ayıklama/izleme anahtarının üst öğesinin adı için bir işaretçi.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugManagedCallback Arabirimi](icordebugmanagedcallback-interface.md)
