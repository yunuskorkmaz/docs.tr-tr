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
ms.openlocfilehash: c0cec9eb7bb8bbc94b255152a9b4d79108bdd1b1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427072"
---
# <a name="stacksnapshotcallback-function"></a>StackSnapshotCallback İşlevi
, Profil oluşturucuyu her yönetilen çerçeve ve yığın üzerinde her yönetilmeyen çerçeve, [ICorProfilerInfo2::D oStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) yöntemi tarafından başlatılan bir yığın ilerleme durumuyla ilgili bilgilerle birlikte sağlar.  
  
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
 'ndaki Bu değer sıfırsa, bu geri çağırma, yönetilmeyen çerçevelerin çalıştırılması içindir; Aksi takdirde, yönetilen bir işlevin tanımlayıcısıdır ve bu geri çağırma yönetilen bir çerçeve içindir.  
  
 `ip`  
 'ndaki Çerçevede yerel kod yönerge işaretçisinin değeri.  
  
 `frameInfo`  
 'ndaki Yığın çerçevesiyle ilgili bilgilere başvuran bir `COR_PRF_FRAME_INFO` değeri. Bu değer yalnızca bu geri çağırma sırasında kullanım için geçerlidir.  
  
 `contextSize`  
 'ndaki `context` parametresi tarafından başvurulan `CONTEXT` yapısının boyutu.  
  
 `context`  
 'ndaki Bu çerçevenin CPU durumunu temsil eden bir Win32 `CONTEXT` yapısına yönelik bir işaretçi.  
  
 `context` parametresi yalnızca COR_PRF_SNAPSHOT_CONTEXT bayrağı `ICorProfilerInfo2::DoStackSnapshot`geçirildiğinde geçerlidir.  
  
 `clientData`  
 'ndaki `ICorProfilerInfo2::DoStackSnapshot`'den doğrudan geçirilen istemci verilerine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `StackSnapshotCallback` işlevi, profil oluşturucu yazıcı tarafından uygulanır. `StackSnapshotCallback`yapılan çalışmanın karmaşıklığını sınırlamanız gerekir. Örneğin, zaman uyumsuz bir şekilde `ICorProfilerInfo2::DoStackSnapshot` kullanırken, hedef iş parçacığı kilitleri tutuyor olabilir. `StackSnapshotCallback` içindeki kod aynı kilitleri gerektiriyorsa, bir kilitlenme olabilir.  
  
 `ICorProfilerInfo2::DoStackSnapshot` yöntemi, yönetilen çerçeveye veya yönetilmeyen çerçevelerin her biri için bir kez `StackSnapshotCallback` işlevini çağırır. Yönetilmeyen çerçevelerin bir çalıştırması için `StackSnapshotCallback` çağrılırsa, profil oluşturucu kendi yönetilmeyen yığın ilerlemesini gerçekleştirmek için Register bağlamını (`context` parametresi tarafından başvurulan) kullanabilir. Bu durumda, Win32 `CONTEXT` yapısı yönetilmeyen çerçevelerin çalıştırılmasındaki en son gönderilen çerçevenin CPU durumunu temsil eder. Win32 `CONTEXT` yapısı tüm yazmaçların değerlerini içerse de, yalnızca yığın işaretçisi yazmacı, çerçeve işaretçisi kaydı, yönerge işaretçisi kaydı ve kalıcı (yani korunan) tamsayı Yazmaçları değerlerini de bilmelisiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DoStackSnapshot Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)
- [Profil Oluşturma Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
