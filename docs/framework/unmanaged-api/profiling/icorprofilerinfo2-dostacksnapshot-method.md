---
title: "ICorProfilerInfo2::DoStackSnapshot Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.DoStackSnapshot
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::DoStackSnapshot
helpviewer_keywords:
- ICorProfilerInfo2::DoStackSnapshot method [.NET Framework profiling]
- DoStackSnapshot method [.NET Framework profiling]
ms.assetid: 287b11e9-7c52-4a13-ba97-751203fa97f4
topic_type: apiref
caps.latest.revision: "25"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6a210fc0c1984ee9bc77114ba30c3287ae43b169
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2dostacksnapshot-method"></a>ICorProfilerInfo2::DoStackSnapshot Yöntemi
Belirtilen iş parçacığı için yığında yönetilen çerçeveler anlatılmaktadır ve profil oluşturucu bir geri çağırma aracılığıyla bilgi gönderir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT DoStackSnapshot(  
    [in] ThreadID thread,  
    [in] StackSnapshotCallback *callback,  
    [in] ULONG32 infoFlags,  
    [in] void *clientData,  
    [in, size_is(contextSize), length_is(contextSize)] BYTE context[],  
    [in] ULONG32 contextSize);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `thread`  
 [in] Hedef iş parçacığı kimliği.  
  
 Null geçirme `thread` bir anlık görüntü geçerli iş parçacığının verir. Varsa bir `ThreadID` , farklı bir iş parçacığı geçirilir, ortak dil çalışma zamanı (CLR) o iş parçacığı askıya alır, anlık görüntü gerçekleştirir ve sürdürür.  
  
 `callback`  
 [in] Uygulaması için bir işaretçi [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) profil oluşturucu her yönetilen çerçeve ve yönetilmeyen çerçeve her çalıştırma hakkında bilgi sağlamak için CLR tarafından çağrılan yöntem.  
  
 `StackSnapshotCallback` Yöntemi profil oluşturucu yazıcı tarafından gerçekleştirilir.  
  
 `infoFlags`  
 [in] Değerini [cor_prf_snapshot_ınfo](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md) tarafından her çerçeve için geri geçirilmesi veri miktarını belirtir numaralandırma `StackSnapshotCallback`.  
  
 `clientData`  
 [in] Düz aracılığıyla geçirilir, istemci verilerini gösteren bir işaretçi `StackSnapshotCallback` geri çağırma işlevi.  
  
 `context`  
 [in] Bir işaretçi bir Win32 `CONTEXT` yığın ilerlemesi oluşturmak için kullanılan yapısı. Win32 `CONTEXT` yapısı CPU yazmaçların değerleri içeren ve zaman içinde belirli bir anda CPU durumunu temsil eder.  
  
 Çekirdek yığının üst yönetilmeyen yardımcı kodu ise yığın ilerlemesi başlamak nereye belirlemek CLR yardımcı olur; Aksi takdirde, çekirdek göz ardı edilir. Çekirdek için zaman uyumsuz bir ilerlemesi sağlanmalıdır. Zaman uyumlu ilerlemesi yapıyorsanız, hiçbir çekirdek gereklidir.  
  
 `context` Parametredir COR_PRF_SNAPSHOT_CONTEXT bayrağı yalnızca geçildi geçerli `infoFlags` parametresi.  
  
 `contextSize`  
 [in] Boyutunu `CONTEXT` tarafından başvurulan yapısı `context` parametresi.  
  
## <a name="remarks"></a>Açıklamalar  
 İçin null geçirme `thread` bir anlık görüntü geçerli iş parçacığının verir. Hedef iş parçacığı aynı anda yalnızca askıya alınırsa anlık görüntüleri diğer iş parçacıklarının alınabilir.  
  
 Profil Oluşturucu yığının yol istediğinde, çağıran `DoStackSnapshot`. Bu çağrısından CLR döndürmeden önce çağrıları, `StackSnapshotCallback` birkaç kez kez her biri için çerçeve (veya yönetilmeyen çerçeveler çalışması) yığında yönetilen. Yönetilmeyen çerçeveler karşılaştığında, bunları kendiniz yol gerekir.  
  
 Çerçeveler yığına nasıl iletilmesini tersi yığın gitti sırasıdır: (son gönderilir) ilk, ana (ilk gönderilir) kareler son yaprak.  
  
 Yönetilen yığın yürütmek için profil oluşturucu programı hakkında daha fazla bilgi için bkz: [profil oluşturucu yığınının taramasını, .NET Framework 2.0: temel kavramları ve ötesine](http://go.microsoft.com/fwlink/?LinkId=73638).  
  
 Yığın ilerlemesi, zaman uyumlu veya zaman uyumsuz, aşağıdaki bölümlerde açıklandığı gibi olabilir.  
  
## <a name="synchronous-stack-walk"></a>Zaman uyumlu yığın ilerlemesi  
 Zaman uyumlu yığın ilerlemesi yanıt olarak bir geri çağırma yığını geçerli iş parçacığının taramasını içerir. Dengeli veya askıya gerektirmez.  
  
 Bir zaman uyumlu yaptığınız zaman, yanıt oluşturucunuz 's birini çağırma CLR olarak çağrı [Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) (veya [Icorprofilercallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)) yöntemlerini çağırırsınız `DoStackSnapshot` yığınını yürütmek için Geçerli iş parçacığının. Yığın nasıl bir bildirim gibi göründüğünü görmek istediğinizde yararlıdır [Icorprofilercallback::objectallocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md). Yalnızca çağrısı `DoStackSnapshot` içinden, `ICorProfilerCallback` null geçirerek yöntemini `context` ve `thread` parametreleri.  
  
## <a name="asynchronous-stack-walk"></a>Zaman uyumsuz yığın ilerlemesi  
 Zaman uyumsuz yığın ilerlemesi farklı bir iş parçacığı yığınını taramasını veya yanıt için bir geri çağırma ancak geçerli iş parçacığının yönerge işaretçisi ele geçirme tarafından değil, geçerli iş parçacığının yığınını taramasını kapsar. Zaman uyumsuz bir ilerlemesi yığının üst bir platform parçası olmayan yönetilmeyen kodu ise çekirdek çağırma (PInvoke) gerektirir veya COM çağrısı ancak CLR yardımcı kodu. Örneğin, tam zamanında (JIT) derleme veya atık toplama yapan yardımcı kodu kodudur.  
  
 Doğrudan hedef iş parçacığı askıya alma çekirdek almak ve kendi yığını taramasını kendiniz, üstteki bulana kadar çerçeve yönetilir. Hedef iş parçacığı askıya sonra hedef iş parçacığının geçerli kayıt bağlamı alır. Ardından, çağırarak kayıt bağlam yönetilmeyen koda işaret edip etmediğini belirlemek [Icorprofilerınfo::getfunctionfromıp](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md) — döndürürse bir `FunctionID` sıfıra eşit, yönetilmeyen kod çerçevedir. Şimdi, ilk yönetilen çerçeve erişmek ve bu çerçeve kaydı bağlamının temel çekirdek bağlamı hesaplamak kadar yığın yol.  
  
 Çağrı `DoStackSnapshot` zaman uyumsuz yığın ilerlemesi başlamak için çekirdek bağlamına sahip. Bir çekirdek belirtmezseniz `DoStackSnapshot` yığının üst yönetilen çerçeveler atla ve sonuç olarak, bir eksik yığın ilerlemesi verecektir. Çekirdek sağlarsanız, JIT derleme ya da yerel Görüntü Oluşturucu'için (Ngen.exe) işaret etmelidir-oluşturulan kodda; Aksi takdirde, `DoStackSnapshot` CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX hata kodu döndürüyor.  
  
 Zaman uyumsuz yığını yetenekte kolayca kilitlenmeleri neden veya bu yönergelere uymanızı sürece ihlalleri, erişim:  
  
-   Doğrudan iş parçacıklarını askıya alma, yalnızca yönetilen kod çalıştırılmadı bir iş parçacığı başka bir iş parçacığı askıya alabilirsiniz unutmayın.  
  
-   Her zaman engelleyin, [Icorprofilercallback::threaddestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md) parçacığının yığın ilerlemesi tamamlanana kadar geri çağırma.  
  
-   Çöp toplama tetikleyebilir bir CLR işlevini oluşturucunuz çağırır kilit tutarken değil. Diğer bir deyişle, sahibi olan iş parçacığı çöp toplama tetikleyen bir arama yapabilir, kilit tutmayın.  
  
 Olup olmadığını da kilitlenme riski çağırmanız `DoStackSnapshot` oluşturucunuz oluşturdu ve böylece ayrı hedef iş parçacığı yığınını yol akıştan. İlk kez oluşturduğunuz iş parçacığı girer belirli `ICorProfilerInfo*` yöntemleri (de dahil olmak üzere `DoStackSnapshot`), CLR iş parçacığı başına, bu iş parçacığında CLR özel başlatma gerçekleştirir. Oluşturucunuz yığını yol çalıştığınız hedef iş parçacığı askıya aldı ve bu hedef iş parçacığı bir kilidi bu iş parçacığı başına başlatma gerçekleştirmek için gereken kendi oldu, kilitlenme meydana gelir. Bu kilitlenmeyi önlemek için bir başlangıç çağrısına olun `DoStackSnapshot` yürütmek için Profil Oluşturucu tarafından oluşturulan iş parçacığı ayrı bir hedef iş parçacığı, ancak hedef iş parçacığı ilk askıya değil. Bu ilk çağrı başına iş parçacığı başlatma kilitlenme tamamlayabilirsiniz sağlar. Varsa `DoStackSnapshot` başarılı ve en az bir çerçeve, raporlar bu noktadan sonra herhangi bir hedef iş parçacığı ve çağrı askıya almak bu profil oluşturucu tarafından oluşturulan iş parçacığı güvenli olacaktır `DoStackSnapshot` o hedef iş parçacığı yığınını yürütmek için.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Icorprofilerınfo arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Icorprofilerınfo2 arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
