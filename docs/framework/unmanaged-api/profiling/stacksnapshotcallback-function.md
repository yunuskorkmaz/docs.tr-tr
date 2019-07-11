---
title: StackSnapshotCallback İşlevi
ms.date: 03/30/2017
api_name:
- StackSnapshotCallback
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- StackSnapshotCallback
helpviewer_keywords:
- StackSnapshotCallback function [.NET Framework profiling]
ms.assetid: d0f235b2-91fe-4f82-b7d5-e5c64186eea8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6140ecda1d12c26e1936daee4eaad11cbd9b6ba4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781233"
---
# <a name="stacksnapshotcallback-function"></a>StackSnapshotCallback İşlevi
Profil Oluşturucu yönetilen her çerçeve ve her bir çalıştırmanın yönetilmeyen çerçeveler hakkında tarafından başlatılan bir yığın ilerlemesi sırasında bilgileri yığında sağlar [Icorprofilerınfo2::dostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) yöntemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT __stdcall StackSnapshotCallback (  
    [in] FunctionID funcId,  
    [in] UINT_PTR ip,  
    [in] COR_PRF_FRAME_INFO frameInfo,  
    [in] ULONG32 contextSize,  
    [in] BYTE context[],  
    [in] void *clientData  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `funcId`  
 [in] Bu değer sıfır ise, bu geri çağırma bir yönetilmeyen çerçeveler çalıştırma için olan; Aksi takdirde, yönetilen bir işlevin tanımlayıcısıdır ve bu geri çağırma için yönetilen bir çerçevedir.  
  
 `ip`  
 [in] Yerel kod yönerge işaretçisini çerçevesinde değeri.  
  
 `frameInfo`  
 [in] A `COR_PRF_FRAME_INFO` yığın çerçevesi hakkında bilgi başvuran değeri. Bu değer yalnızca bu geri çağırma sırasında kullanım için geçerlidir.  
  
 `contextSize`  
 [in] Boyutu `CONTEXT` tarafından başvurulan yapısını `context` parametresi.  
  
 `context`  
 [in] Bir Win32 işaretçisi `CONTEXT` bu çerçevesi için CPU durumunu temsil eden yapısı.  
  
 `context` Parametredir COR_PRF_SNAPSHOT_CONTEXT bayrağı yalnızca geçirilen geçerli `ICorProfilerInfo2::DoStackSnapshot`.  
  
 `clientData`  
 [in] Doğrudan gelen geçirilen istemci verilerini bir işaretçiye `ICorProfilerInfo2::DoStackSnapshot`.  
  
## <a name="remarks"></a>Açıklamalar  
 `StackSnapshotCallback` İşlevi, profil oluşturucu yazıcı tarafından uygulanır. Gerçekleştirilen iş karmaşıklığını sınırlaması gerekir `StackSnapshotCallback`. Örneğin, kullanırken `ICorProfilerInfo2::DoStackSnapshot` zaman uyumsuz olarak hedef iş parçacığının kilitler tutabilir. Varsa içinde kod `StackSnapshotCallback` aynı kilitler gerektirir ardından bir kilitlenme.  
  
 `ICorProfilerInfo2::DoStackSnapshot` Yöntem çağrılarını `StackSnapshotCallback` işlevi yönetilen çerçeve başına bir kere veya çalışma yönetilmeyen çerçeve başına bir kez. Varsa `StackSnapshotCallback` çağrılır yönetilmeyen çerçeveler çalıştırma için profil oluşturucu kayıt bağlam kullanabilir (tarafından başvurulan `context` parametresi) kendi yönetilmeyen yığın ilerlemesi gerçekleştirmek için. Bu durumda, Win32 `CONTEXT` yapısı yönetilmeyen çerçeveler yürütülmesi en yakın zamanda gönderilen çerçevesinde CPU durumunu temsil eder. Olsa da Win32 `CONTEXT` yapısı tüm kayıtları için değerler içeriyorsa, yığın işaretçisi kaydı, çerçeve işaretçisi kaydı, yönerge işaretçisi kaydı ve (yani korunur) kalıcı değerlerine yalnızca yararlanmalıdır tamsayı kaydeder.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DoStackSnapshot Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)
- [Profil Oluşturma Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
