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
ms.openlocfilehash: 78fdcb69e73bc7238972d1a6ffb37b5ba91c7953
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="stacksnapshotcallback-function"></a>StackSnapshotCallback İşlevi
Profil Oluşturucu bilgiler her yönetilen çerçeve ve her çalışma yönetilmeyen çerçeve yığında tarafından başlatılan bir yığın ilerlemesi sırasında verir [Icorprofilerınfo2::dostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) yöntemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT __stdcall StackSnapshotCallback (  
    [in] FunctionID funcId,  
    [in] UINT_PTR ip,  
    [in] COR_PRF_FRAME_INFO frameInfo,  
    [in] ULONG32 contextSize,  
    [in] BYTE context[],  
    [in] void *clientData  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `funcId`  
 [in] Bu değer sıfır ise, bu geri çağırma bir yönetilmeyen çerçeveler çalıştırması için yeterli; Aksi takdirde, yönetilen bir işlevin tanımlayıcısıdır ve bu geri çağırma için yönetilen bir çerçevedir.  
  
 `ip`  
 [in] Yerel kod yönerge işaretçisi çerçevesinde değeri.  
  
 `frameInfo`  
 [in] A `COR_PRF_FRAME_INFO` yığın çerçevesi hakkında bilgi başvuran değeri. Bu değer yalnızca bu geri çağırma sırasında kullanım için geçerli olur.  
  
 `contextSize`  
 [in] Boyutunu `CONTEXT` tarafından başvurulan yapısı `context` parametresi.  
  
 `context`  
 [in] Bir işaretçi bir Win32 `CONTEXT` yapısı bu çerçeve CPU durumunu temsil eder.  
  
 `context` Parametredir COR_PRF_SNAPSHOT_CONTEXT bayrağı yalnızca geçildi geçerli `ICorProfilerInfo2::DoStackSnapshot`.  
  
 `clientData`  
 [in] Doğrudan gelen geçirilir istemci verilerini gösteren bir işaretçi `ICorProfilerInfo2::DoStackSnapshot`.  
  
## <a name="remarks"></a>Açıklamalar  
 `StackSnapshotCallback` İşlevi profil oluşturucu yazıcı tarafından gerçekleştirilir. İşlerini karmaşıklığını sınırlamak `StackSnapshotCallback`. Örneğin, kullanırken `ICorProfilerInfo2::DoStackSnapshot` zaman uyumsuz bir şekilde hedef iş parçacığı kilitleri tutabilir. Varsa içindeki kod `StackSnapshotCallback` aynı kilitler gerektirir kilitlenme olun.  
  
 `ICorProfilerInfo2::DoStackSnapshot` Yöntem çağrılarını `StackSnapshotCallback` yönetilen çerçeve başına bir kez veya bir kez çalıştır yönetilmeyen çerçeve başına işlevi. Varsa `StackSnapshotCallback` çağrılır yönetilmeyen çerçeveler çalıştırma için profil oluşturucu kayıt bağlam kullanabilir (tarafından başvurulan `context` parametresi) kendi yönetilmeyen yığın ilerlemesi gerçekleştirmek için. Bu durumda, Win32 `CONTEXT` yapısı yönetilmeyen çerçeveler Çalıştır en yakın zamanda basılmış çerçevesinde CPU ili temsil eder. Ancak Win32 `CONTEXT` yapısı tüm kayıtları için değerleri içerir, yığın işaretçi kaydı, çerçeve işaretçisi kaydı, yönerge işaretçisi kaydı ve (yani korundu) kalıcı değerlerine yalnızca yararlanmalıdır tamsayı kaydeder.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DoStackSnapshot Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
 [Profil Oluşturma Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
