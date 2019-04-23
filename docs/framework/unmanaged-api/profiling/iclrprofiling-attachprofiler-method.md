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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0e3898fb836409df3b685d985d0d72ab63230a93
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59174180"
---
# <a name="iclrprofilingattachprofiler-method"></a>ICLRProfiling::AttachProfiler Yöntemi
Belirtilen işleme belirtilen profil oluşturucuyu ekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT AttachProfiler(  
  [in] DWORD dwProfileeProcessID,  
  [in] DWORD dwMillisecondsMax,                     // optional  
  [in] const CLSID * pClsidProfiler,  
  [in] LPCWSTR wszProfilerPath,                     // optional  
  [in] size_is(cbClientData)] void * pvClientData,  // optional  
  [in] UINT cbClientData);                          // optional  
```  
  
## <a name="parameters"></a>Parametreler  
 `dwProfileeProcessID`  
 [in] Profil Oluşturucu eklenmesi işlemin işlem kimliği. Bir 64-bit makinede profilli işlemin bit genişliği bit genişliğinde çağıran bir tetikleyici işlem eşleşmelidir `AttachProfiler`. Altında kullanıcı hesabı `AttachProfiler` çağrılır yönetici ayrıcalıklarına sahip, hedef işlem sistem üzerindeki herhangi bir işlem olabilir. Aksi takdirde, hedef işlem, aynı kullanıcı hesabı tarafından sahiplenilmelidir.  
  
 `dwMillisecondsMax`  
 [in] Milisaniye cinsinden süre için `AttachProfiler` tamamlanması. Tetikleyici işlem, belirli bir profil, başlatma işlemini tamamlamak yeterli olduğu bilinen bir zaman aşımı geçmelidir.  
  
 `pClsidProfiler`  
 [in] Yüklenecek profil oluşturucu CLSID değeri için bir işaretçi. Tetikleyici işlem, bu bellek sonra yeniden kullanabilirsiniz `AttachProfiler` döndürür.  
  
 `wszProfilerPath`  
 [in] Yüklenecek profil oluşturucunun DLL dosyasının tam yolu. Bu dize null Sonlandırıcı dahil olmak üzere, en fazla 260 karakter içermelidir. Varsa `wszProfilerPath` null veya boş bir dize ortak dil çalışma zamanı (CLR) profil oluşturucunun DLL dosyasının konumunu CLSID kayıt defterinde bakarak bulmayı dener, `pClsidProfiler` işaret eder.  
  
 `pvClientData`  
 [in] Profil Oluşturucu tarafından geçirilecek veriler için bir işaretçi [Icorprofilercallback3::ınitializeforattach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) yöntemi. Tetikleyici işlem, bu bellek sonra yeniden kullanabilirsiniz `AttachProfiler` döndürür. Varsa `pvClientData` boş `cbClientData` 0 (sıfır) olmalıdır.  
  
 `cbClientData`  
 [in] Bayt cinsinden veri boyutu, `pvClientData` işaret eder.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki HRESULT'ları döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Belirtilen profil oluşturucuyu hedef işleme başarıyla eklenmiş.|  
|CORPROF_E_PROFILER_ALREADY_ACTIVE|Aynı zamanda etkin veya düğmelere hedef işlem için zaten bir profil oluşturucu yok.|  
|CORPROF_E_PROFILER_NOT_ATTACHABLE|Belirtilen profil oluşturucu bağlantısını desteklemez. Tetikleyici işlem, farklı bir profil oluşturucu ekleme girişiminde bulunabilir.|  
|CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER|Hedef işlemin sürümü çağıran geçerli işlem ile uyumsuz olduğundan bir profil oluşturucu ek istek kurulamıyor `AttachProfiler`.|  
|HRESULT_FROM_WIN32(ERROR_ACCESS_DENIED)|Tetikleyici işlem, kullanıcı hedef işlem erişiminiz yok.|  
|HRESULT_FROM_WIN32(ERROR_PRIVILEGE_NOT_HELD)|Tetikleyici işlem, kullanıcı için belirtilen hedef işlemin bir profil oluşturucuyu eklemek gerekli ayrıcalıklara sahip değil. Uygulama olay günlüğü daha fazla bilgi içeriyor olabilir.|  
|CORPROF_E_IPC_FAILED|Hedef işlemle iletişim kurulurken bir hata oluştu. Hedef işlem kapatılıyor, bu yaygın olarak gerçekleşir.|  
|HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)|Hedef işlem yok veya ek destekleyen bir CLR çalışmıyor. Bu durum, CLR çalışma zamanı numaralandırma yöntem çağrısından sonra kaldırılmış olduğunu gösteriyor olabilir.|  
|HRESULT_FROM_WIN32(ERROR_TIMEOUT)|Profiler'ı yüklemek için başlangıç olmadan süresi doldu. İliştirme işlemini yeniden deneyebilirsiniz. Hedef işlem içindeki bir sonlandırıcı zaman aşımı değerinden daha uzun bir süre çalıştığında zaman aşımı oluşur.|  
|E_INVALIDARG|Bir veya daha fazla parametreler geçersiz değerlere sahip.|  
|E_FAIL|Bazı diğer, belirtilmeyen bir hata oluştu.|  
|Diğer hata kodları|Profil oluşturucunun [Icorprofilercallback3::ınitializeforattach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) yöntemi hatası gösteren HRESULT döndürür `AttachProfiler` döndürür, aynı HRESULT. Bu durumda, E_NOTIMPL CORPROF_E_PROFILER_NOT_ATTACHABLE için dönüştürülür.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="memory-management"></a>Bellek Yönetimi  
 COM kuralları ile çağıran tutma içinde `AttachProfiler` (örneğin, tetikleyici kod profil oluşturucu geliştirici tarafından yazılan) ayırma ve veriler için bellek ayırmasını sorumludur, `pvClientData` parametre işaret eder. Ne zaman CLR yürütür `AttachProfiler` , bu çağrıda bir kopyasını bellek, `pvClientData` işaret ve hedef işlem için iletir. CLR'nin hedef işlemin içinde kendine ait kopyasını aldığında `pvClientData` bloğu, bloğun profil oluşturucu geçirir `InitializeForAttach` yöntemi ve kopyasını ayırmayı iptal eder `pvClientData` hedef işlem bloğundan.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerInfo3 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
