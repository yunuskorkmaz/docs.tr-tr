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
ms.openlocfilehash: 52e3498b54f90e7d9d1d1d79ae0817cca511af4e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459511"
---
# <a name="iclrprofilingattachprofiler-method"></a>ICLRProfiling::AttachProfiler Yöntemi
Belirtilen profil oluşturucu için belirtilen işlem ekler.  
  
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
  
#### <a name="parameters"></a>Parametreler  
 `dwProfileeProcessID`  
 [in] Profil Oluşturucu eklenmesi işlemin işlem kimliği. Bir 64-bit makine profili işlemin verileri aradığı tetikleyici işlem verileri eşleşmelidir `AttachProfiler`. Altında kullanıcı hesabı `AttachProfiler` çağrılır yönetimsel ayrıcalıklara sahip, hedef işlem sistem üzerindeki herhangi bir işlem olabilir. Aksi takdirde, hedef işlem aynı kullanıcı hesabı tarafından ait olmalıdır.  
  
 `dwMillisecondsMax`  
 [in] Milisaniye cinsinden süre için `AttachProfiler` tamamlamak için. Tetikleyici işlemi belirli profiler kendi başlatma işlemini tamamlamak yeterli olduğu bilinen bir zaman aşımı geçirmelisiniz.  
  
 `pClsidProfiler`  
 [in] Yüklenecek profil oluşturucu CLSID gösteren bir işaretçi. Tetikleyici işlemi bu bellek sonra yeniden `AttachProfiler` döndürür.  
  
 `wszProfilerPath`  
 [in] Yüklenecek Profil Oluşturucu'nın DLL dosyasının tam yolu. Bu dize null Sonlandırıcı dahil olmak üzere en fazla 260 karakter içermelidir. Varsa `wszProfilerPath` null veya boş bir dize ortak dil çalışma zamanı (CLR) CLSID kayıt defterinde bakarak Profil Oluşturucu'nın DLL dosyasının konumunu bulmayı dener, `pClsidProfiler` işaret eder.  
  
 `pvClientData`  
 [in] Profil Oluşturucu tarafından geçirilecek veriler için bir işaretçi [Icorprofilercallback3::ınitializeforattach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) yöntemi. Tetikleyici işlemi bu bellek sonra yeniden `AttachProfiler` döndürür. Varsa `pvClientData` null, `cbClientData` 0 (sıfır) olması gerekir.  
  
 `cbClientData`  
 [in] Bayt cinsinden veri boyutu, `pvClientData` işaret eder.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki HRESULTs döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Belirtilen profil oluşturucu hedef işlem başarıyla eklenmiş.|  
|CORPROF_E_PROFILER_ALREADY_ACTIVE|Aynı zamanda active veya düğmelere hedef işlem için zaten bir profil oluşturucu yoktur.|  
|CORPROF_E_PROFILER_NOT_ATTACHABLE|Belirtilen profil oluşturucu desteklemez. Tetikleyici işlemi farklı bir profil oluşturucu ekleme girişiminde bulunabilir.|  
|CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER|Hedef işlemin sürümü çağırma geçerli işlem ile uyumlu olmadığı için bir profil oluşturucu ek istek kurulamıyor `AttachProfiler`.|  
|HRESULT_FROM_WIN32(ERROR_ACCESS_DENIED)|Tetikleyici işleminin kullanıcının hedef işlem erişimi yok.|  
|HRESULT_FROM_WIN32(ERROR_PRIVILEGE_NOT_HELD)|Tetikleyici işleminin kullanıcı için belirtilen hedef işlem bir profil oluşturucu ekleme için gerekli ayrıcalıklara sahip değil. Uygulama olay günlüğü daha fazla bilgi içerebilir.|  
|CORPROF_E_IPC_FAILED|Hedef işlemiyle iletişim kurarken bir hata oluştu. Hedef işlem kapatılıyor varsa bu yaygın olarak gerçekleşir.|  
|HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)|Hedef işlem yok veya ek destekleyen bir CLR çalışmıyor. Bu durum, CLR çalışma zamanı numaralandırma yöntemi çağrısından itibaren kaldırıldı olduğunu gösteriyor olabilir.|  
|HRESULT_FROM_WIN32(ERROR_TIMEOUT)|Profil Oluşturucu yüklemek için başlangıç olmadan süresi doldu. Ekleme işlemi yeniden deneyin. Zaman aşımları sonlandırıcıyı hedef işleminde zaman aşımı değeri daha uzun süre çalışırsa oluşur.|  
|E_INVALIDARG|Bir veya daha fazla parametre geçersiz değerlere sahip.|  
|E_FAIL|Bazı diğer, belirtilmeyen bir hata oluştu.|  
|Diğer hata kodları|Varsa profil oluşturucu 's [Icorprofilercallback3::ınitializeforattach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) yöntemi döndürür hatası gösteren bir HRESULT `AttachProfiler` , aynı döndürür HRESULT. Bu durumda, E_NOTIMPL CORPROF_E_PROFILER_NOT_ATTACHABLE için dönüştürülür.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="memory-management"></a>Bellek Yönetimi  
 Çağıranın COM kuralları ile güvenliğini koruma açısından `AttachProfiler` (örneğin, tetikleyici kod profil oluşturucu geliştirici tarafından yazılan) ayırma ve veriler için bellek ayırmasını sorumlu, `pvClientData` parametresi işaret eder. Ne zaman CLR yürütür `AttachProfiler` çağrısı kolaylaştırır bellek bir kopyasını, `pvClientData` işaret ve hedef işlem iletir. Ne zaman CLR'nin hedef işlem içinde kendine ait kopyasını alır `pvClientData` bloğu, profil oluşturucu blok geçirir `InitializeForAttach` yöntemi ve kendi kopyasını kaldırır `pvClientData` hedef işlem bloğundan.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerInfo3 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
