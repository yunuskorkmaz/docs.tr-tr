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
ms.openlocfilehash: 29aecd530d18b931420467e9127bcbf96d3a4a5f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866780"
---
# <a name="iclrprofilingattachprofiler-method"></a>ICLRProfiling::AttachProfiler Yöntemi
Belirtilen işlem oluşturucuyu belirtilen işleme iliştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
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

  \[içinde] profil oluşturucunun eklendiği işlemin işlem KIMLIĞI. 64 bitlik bir makinede, profili oluşturulan işlemin bit genişliği, `AttachProfiler`çağıran tetikleyici işlemin bit durumuyla aynı olmalıdır. `AttachProfiler` altında çağrıldığı Kullanıcı hesabının yönetim ayrıcalıkları varsa, hedef işlem sistemde herhangi bir işlem olabilir. Aksi takdirde, hedef işlem aynı kullanıcı hesabına ait olmalıdır.

- `dwMillisecondsMax`

  \[, `AttachProfiler` tamamlanmayacak süre (milisaniye cinsinden). Tetikleme işlemi, belirli bir profil oluşturucunun başlatma işlemini tamamlaması için yeterince bilinen bir zaman aşımı süresi iletmelidir.
  
- `pClsidProfiler`

  \[içinde, yüklenecek profil oluşturucunun CLSID 'sine yönelik bir işaretçi. Tetikleyici işlemi, `AttachProfiler` döndüğünde bu belleği yeniden kullanabilir.

- `wszProfilerPath`

  \[içinde] yüklenecek profil oluşturucunun DLL dosyasının tam yolu. Bu dize, null Sonlandırıcı dahil olmak üzere en fazla 260 karakter içermelidir. `wszProfilerPath` null ya da boş bir dize ise, ortak dil çalışma zamanı (CLR) `pClsidProfiler` işaret eden CLSID için kayıt defterine bakarak profil oluşturucunun DLL dosyasının konumunu bulmaya çalışır.

- `pvClientData`

  \[içinde, [ICorProfilerCallback3:: InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) yöntemi tarafından Profiler 'a geçirilecek verilerin bir işaretçisi. Tetikleyici işlemi, `AttachProfiler` döndüğünde bu belleği yeniden kullanabilir. `pvClientData` null ise, `cbClientData` 0 (sıfır) olmalıdır.

- `cbClientData`

  \[, `pvClientData` tarafından işaret edilen verilerin bayt cinsinden boyutudur.

## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki HRESULTs 'leri döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Belirtilen profil oluşturucu hedef işleme başarıyla eklendi.|  
|CORPROF_E_PROFILER_ALREADY_ACTIVE|Zaten bir profil oluşturucu etkin veya hedef işleme iliştiriliyor.|  
|CORPROF_E_PROFILER_NOT_ATTACHABLE|Belirtilen profil oluşturucu eki desteklemiyor. Tetikleyici işlemi, farklı bir profil oluşturucu iliştirmeye çalışabilir.|  
|CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER|Hedef işlemin sürümü `AttachProfiler`çağıran geçerli işlemle uyumsuz olduğundan profil oluşturucu eki istenmedi.|  
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
 COM kurallarıyla birlikte `AttachProfiler` çağıranı (örneğin, profil oluşturucu geliştiricisi tarafından yazılan tetikleyici kodu), `pvClientData` parametresinin işaret ettiği veriler için bellek ayırmayı ve serbest bırakmayı sağlamaktan sorumludur. CLR `AttachProfiler` çağrısını yürüttüğünde, `pvClientData` işaret eden belleğin bir kopyasını oluşturur ve hedef işleme iletir. Hedef işlemin içindeki CLR `pvClientData` bloğunun kendi kopyasını aldığında, engellemeyi `InitializeForAttach` yöntemi aracılığıyla Profiler 'a geçirir ve ardından hedef işlemden `pvClientData` bloğunun kopyasını kaldırır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [ICorProfilerInfo3 Yöntemi](icorprofilerinfo3-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [Profil Oluşturma](index.md)
