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
ms.openlocfilehash: a0f5316900dedc6c8983f9e670f60767ed783a40
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494000"
---
# <a name="stacksnapshotcallback-function"></a>StackSnapshotCallback İşlevi
, Profil oluşturucuyu her yönetilen çerçeve ve yığın üzerinde her yönetilmeyen çerçeve, [ICorProfilerInfo2::D oStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) yöntemi tarafından başlatılan bir yığın ilerleme durumuyla ilgili bilgilerle birlikte sağlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki `COR_PRF_FRAME_INFO`Yığın çerçevesiyle ilgili bilgilere başvuran bir değer. Bu değer yalnızca bu geri çağırma sırasında kullanım için geçerlidir.  
  
 `contextSize`  
 'ndaki `CONTEXT`Parametrenin başvurduğu yapının boyutu `context` .  
  
 `context`  
 'ndaki `CONTEXT`Bu ÇERÇEVENIN CPU durumunu temsil eden Win32 yapısına yönelik bir işaretçi.  
  
 `context`Parametresi yalnızca COR_PRF_SNAPSHOT_CONTEXT bayrağının geçirilmesi durumunda geçerlidir `ICorProfilerInfo2::DoStackSnapshot` .  
  
 `clientData`  
 'ndaki İstemci verilerine yönelik bir işaretçi, ' den doğrudan geçirilir `ICorProfilerInfo2::DoStackSnapshot` .  
  
## <a name="remarks"></a>Açıklamalar  
 `StackSnapshotCallback`İşlev, profil oluşturucu yazıcı tarafından uygulanır. ' De yapılan çalışmanın karmaşıklığını sınırlamanız gerekir `StackSnapshotCallback` . Örneğin, `ICorProfilerInfo2::DoStackSnapshot` zaman uyumsuz bir şekilde kullanırken, hedef iş parçacığı kilitleri tutuyor olabilir. İçindeki kod `StackSnapshotCallback` aynı kilitleri gerektiriyorsa, bir kilitlenme olabilir.  
  
 `ICorProfilerInfo2::DoStackSnapshot`Yöntemi `StackSnapshotCallback` yönetilen çerçeveye göre veya yönetilmeyen çerçevelerin her biri için bir kez işlevini çağırır. `StackSnapshotCallback`Yönetilmeyen çerçevelerin bir çalıştırması için çağrılırsa, profil oluşturucu `context` kendi yönetilmeyen yığın yürüme işlemini gerçekleştirmek için YAZMAÇ bağlamını (parametresi tarafından başvurulan) kullanabilir. Bu durumda, Win32 `CONTEXT` yapısı yönetilmeyen çerçevelerin çalıştırılmasındaki en son gönderilen çerçeveye AIT CPU durumunu temsil eder. Win32 `CONTEXT` yapısı tüm yazmaçların değerlerini içerse de, yalnızca yığın işaretçisi yazmacı, çerçeve işaretçisi kaydı, yönerge işaretçisi kaydı ve kalıcı (yani korunan) tamsayı Yazmaçları değerlerini de bilmelisiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DoStackSnapshot Yöntemi](icorprofilerinfo2-dostacksnapshot-method.md)
- [Profil Oluşturma Genel Statik İşlevleri](profiling-global-static-functions.md)
