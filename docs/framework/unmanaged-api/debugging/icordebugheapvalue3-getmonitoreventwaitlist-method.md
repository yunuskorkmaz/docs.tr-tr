---
title: ICorDebugHeapValue3::GetMonitorEventWaitList Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3.GetMonitorEventWaitList
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList
helpviewer_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList method [.NET Framework debugging]
- GetMonitorEventWaitList method [.NET Framework debugging]
ms.assetid: 035a9035-ac66-4953-b48a-99652b42b7fe
topic_type:
- apiref
ms.openlocfilehash: 21bf0122039a720ff8a1d38d62e77c2560dcc435
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726541"
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a>ICorDebugHeapValue3::GetMonitorEventWaitList Yöntemi

Bir izleyici kilidi ile ilişkili olayda sıraya alınan iş parçacıklarının sıralı bir listesini sağlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `ppThreadEnum`  
 dışı Sıralı iş parçacığı listesini sağlayan ICorDebugThreadEnum numaralandırıcısı.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Liste boş değil.|  
|S_FALSE|Liste boş.|  
  
## <a name="exceptions"></a>Özel Durumlar  
  
## <a name="remarks"></a>Açıklamalar  

 Listedeki ilk iş parçacığı, sonraki çağrısıyla yayınlanan ilk iş parçacığıdır <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType> . Listedeki bir sonraki iş parçacığı aşağıdaki çağrıda yayımlanır ve bu şekilde devam eder.  
  
 Liste boş değilse, bu yöntem S_OK döndürür. Liste boşsa, yöntem S_FALSE döndürür; Bu durumda, numaralandırma hala geçerlidir, ancak boş olur.  
  
 Her iki durumda da, numaralandırma arabirimi yalnızca geçerli eşitlenmiş durumun süresi boyunca kullanılabilir. Ancak, iş parçacığından gelen arabirimler, iş parçacığı çıkıncaya kadar geçerlidir.  
  
 `ppThreadEnum`Geçerli bir işaretçi değilse, sonuç tanımsızdır.  
  
 Bir hata oluşursa, herhangi bir iş parçacığı izleyiciden bekliyorsa, yöntem hata belirten bir HRESULT döndürür.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
