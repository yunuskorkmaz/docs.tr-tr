---
title: ICorProfilerCallback::COMClassicVTableDestroyed Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.COMClassicVTableDestroyed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::COMClassicVTableDestroyed
helpviewer_keywords:
- ICorProfilerCallback::COMClassicVTableDestroyed method [.NET Framework profiling]
- COMClassicVTableDestroyed method [.NET Framework profiling]
ms.assetid: 29da20ca-bf39-4356-8099-d9c3ac3423a9
topic_type:
- apiref
ms.openlocfilehash: 708981155589d491a3b1819adb611a28072dd1bf
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500331"
---
# <a name="icorprofilercallbackcomclassicvtabledestroyed-method"></a>ICorProfilerCallback::COMClassicVTableDestroyed Yöntemi
Profil oluşturucuyu bir COM birlikte çalışma vtable 'ın yok edildiğini bildirir.  
  
> [!NOTE]
> Vtables yok etme işlemi kapanmaya yakın bir şekilde gerçekleştiğinden, bu geri aramanın hiçbir şekilde gerçekleşmemesi olasıdır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT COMClassicVTableDestroyed(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable);  
```  
  
## <a name="parameters"></a>Parametreler

- `wrappedClassId`

  \[' de] Bu vtable 'ın oluşturulduğu sınıfın KIMLIĞI.

- `implementedIID`

  \[' de] sınıf tarafından uygulanan arabirimin KIMLIĞI. Arabirim yalnızca dahili ise bu değer NULL olabilir.

- `pVTable`

  \[' de] vtable başlangıcını gösteren bir işaretçidir.

## <a name="remarks"></a>Açıklamalar  
 Yığın atık toplamaya izin veren bir durumda olmadığından profil oluşturucu bu yöntemin uygulamasında engellenmemelidir, bu nedenle preemptive çöp toplama etkinleştirilemez. Profil Oluşturucu burada ve çöp toplama denendiğinde, bu geri arama dönene kadar çalışma zamanı engellenir.  
  
 Profil oluşturucunun bu yöntemin uygulanması yönetilen koda veya herhangi bir şekilde bir yönetilen bellek ayırmaya yol açmaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [COMClassicVTableCreated Yöntemi](icorprofilercallback-comclassicvtablecreated-method.md)
