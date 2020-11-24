---
title: ICorDebugManagedCallback::LoadClass Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadClass
helpviewer_keywords:
- ICorDebugManagedCallback::LoadClass method [.NET Framework debugging]
- LoadClass method [.NET Framework debugging]
ms.assetid: e58dac7b-85c3-41ca-b9aa-3a7fc9ae6680
topic_type:
- apiref
ms.openlocfilehash: 6f1672d40cd495d3ec099abc703639cf52460703
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679669"
---
# <a name="icordebugmanagedcallbackloadclass-method"></a>ICorDebugManagedCallback::LoadClass Yöntemi

Bir sınıfın yüklendiğini hata ayıklayıcıya bildirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pAppDomain`  
 'ndaki Sınıfın yüklendiği uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.  
  
 `c`  
 'ndaki Sınıfını temsil eden ICorDebugClass nesnesine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Bu geri çağırma, yalnızca sınıf yüklemesi sınıfı içeren modül için etkinleştirildiyse oluşur. Sınıf yükleme her zaman dinamik modüller için etkindir.  
  
 `LoadClass`Geri arama, kesme noktalarını dinamik modüllerde yeni oluşturulan sınıflara bağlamak için uygun bir zaman sağlar.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UnloadClass Yöntemi](icordebugmanagedcallback-unloadclass-method.md)
- [ICorDebugManagedCallback Arabirimi](icordebugmanagedcallback-interface.md)
