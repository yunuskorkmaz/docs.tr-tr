---
title: ICLRProfiling::AttachProfiler Yöntemi
ms.date: 03/30/2017
api_name:
- IClrProfiling.AttachProfiler Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- IClrProfiling::AttachProfiler
helpviewer_keywords:
- AttachProfiler method [.NET Framework profiling]
- IClrProfiling::AttachProfiler method [.NET Framework profiling]
ms.assetid: 535a6839-c443-405b-a6f4-e2af90725d5b
topic_type:
- apiref
ms.openlocfilehash: 48ac09e1862ae58e79707235e891f72920de1251
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500565"
---
# <a name="iclrprofilingattachprofiler-method"></a>ICLRProfiling::AttachProfiler Yöntemi
Belirtilen işlem oluşturucuyu belirtilen işleme iliştirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT AttachProfiler(  
  [in] DWORD dwProfileeProcessID,  
  [in] DWORD dwMillisecondsMax,                     // optional  
  [in] const CLSID * pClsidProfiler,  
  [in] LPCWSTR wszProfilerPath,                     // optional  
  [in] size_is(cbClientData)] void * pvClientData,  // optional  
  [in] UINT cbClientData);                          // optional  
```  
  
## <a name="parameters"></a>Parametreler

- `dwProfileeProcessID`

  \[içinde] profil oluşturucunun eklendiği işlemin işlem KIMLIĞI. 64 bitlik bir makinede, profili oluşturulan işlemin bit genişliği, çağıran tetikleyici işlemin bit durumuyla aynı olmalıdır `AttachProfiler` . `AttachProfiler`İçinde çağrılan kullanıcı hesabının yönetim ayrıcalıkları varsa, hedef işlem sistemde herhangi bir işlem olabilir. Aksi takdirde, hedef işlem aynı kullanıcı hesabına ait olmalıdır.

- `dwMillisecondsMax`

  \[' de] için milisaniye cinsinden süre `AttachProfiler` . Tetikleme işlemi, belirli bir profil oluşturucunun başlatma işlemini tamamlaması için yeterince bilinen bir zaman aşımı süresi iletmelidir.
  
- `pClsidProfiler`

  \[' de] yüklenecek profil oluşturucunun CLSID 'sine yönelik bir işaretçi. Tetikleme işlemi, bu belleği döndürbaşladıktan sonra yeniden kullanabilir `AttachProfiler` .

- `wszProfilerPath`

  \[' de] yüklenecek profil oluşturucunun DLL dosyasının tam yolu. Bu dize, null Sonlandırıcı dahil olmak üzere en fazla 260 karakter içermelidir. `wszProfilerPath`Null veya boş bir dize ise, ortak dil çalışma zamanı (CLR), öğesine işaret eden CLSID için kayıt defterine bakarak profil OLUŞTURUCUNUN dll dosyasının konumunu bulmaya çalışır `pClsidProfiler` .

- `pvClientData`

  \[' de] [ICorProfilerCallback3:: InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) yöntemi tarafından Profiler 'a geçirilecek verilerin bir işaretçisi. Tetikleme işlemi, bu belleği döndürbaşladıktan sonra yeniden kullanabilir `AttachProfiler` . `pvClientData`Null ise `cbClientData` 0 (sıfır) olmalıdır.

- `cbClientData`

  \[' de] işaret eden verilerin bayt cinsinden boyutu `pvClientData` .

## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki HRESULTs 'leri döndürür.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Belirtilen profil oluşturucu hedef işleme başarıyla eklendi.|  
|CORPROF_E_PROFILER_ALREADY_ACTIVE|Zaten bir profil oluşturucu etkin veya hedef işleme iliştiriliyor.|  
|CORPROF_E_PROFILER_NOT_ATTACHABLE|Belirtilen profil oluşturucu eki desteklemiyor. Tetikleyici işlemi, farklı bir profil oluşturucu iliştirmeye çalışabilir.|  
|CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER|Hedef işlemin sürümü çağıran geçerli işlemle uyumsuz olduğundan profil oluşturucu eki istenmedi `AttachProfiler` .|  
|HRESULT_FROM_WIN32 (ERROR_ACCESS_DENIED)|Tetikleyici işleminin kullanıcısının hedef işleme erişimi yok.|  
|HRESULT_FROM_WIN32 (ERROR_PRIVILEGE_NOT_HELD)|Tetikleyici işleminin kullanıcısı, belirtilen hedef işleme bir profil oluşturucu eklemek için gerekli ayrıcalıklara sahip değil. Uygulama olay günlüğünde daha fazla bilgi bulunabilir.|  
|CORPROF_E_IPC_FAILED|Hedef işlemle iletişim kurulurken bir hata oluştu. Bu, genellikle hedef işlem kapatıldıysa meydana gelir.|  
|HRESULT_FROM_WIN32 (ERROR_FILE_NOT_FOUND)|Hedef işlem yok ya da eki destekleyen bir CLR çalıştırmıyor. Bu, çalışma zamanı numaralandırma yöntemine yapılan çağrıdan bu yana CLR 'nin kaldırıldığından emin olabilir.|  
|HRESULT_FROM_WIN32 (ERROR_TIMEOUT)|Zaman aşımı, profil oluşturucuyu yüklemeye başlamadan önce doldu. İliştirme işlemini yeniden deneyebilirsiniz. Hedef işlemdeki bir Sonlandırıcı, zaman aşımı değerinden daha uzun bir süre çalıştığında zaman aşımları oluşur.|  
|E_INVALIDARG|Bir veya daha fazla parametrenin geçersiz değerleri var.|  
|E_FAIL|Belirtilmeyen bir hata oluştu.|  
|Diğer hata kodları|Profiler 'ın [ICorProfilerCallback3:: InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) yöntemi hata BELIRTEN bir HRESULT döndürürse, `AttachProfiler` aynı hresult döndürür. Bu durumda, E_NOTIMPL CORPROF_E_PROFILER_NOT_ATTACHABLE dönüştürülür.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="memory-management"></a>Bellek Yönetimi  
 COM kuralları ile birlikte, çağıran `AttachProfiler` (örneğin, profil oluşturucu geliştiricisi tarafından yazılan tetikleyici kodu), parametresinin işaret ettiği veriler için bellek ayırmayı ve serbest bırakmayı sağlamaktan sorumludur `pvClientData` . CLR çağrıyı yürüttüğünde `AttachProfiler` , ' a `pvClientData` işaret eden ve hedef işleme ileten belleğin bir kopyasını oluşturur. Hedef işlemin içindeki CLR kendi bloğunun kopyasını aldığında `pvClientData` , bloğunu yöntemi aracılığıyla Profiler 'a geçirir `InitializeForAttach` ve sonra `pvClientData` bloğun kopyasını hedef işlemden kaldırır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [ICorProfilerInfo3 Arabirimi](icorprofilerinfo3-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [Profil Oluşturma](index.md)
