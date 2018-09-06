---
title: ICorProfilerInfo2::DoStackSnapshot Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.DoStackSnapshot
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::DoStackSnapshot
helpviewer_keywords:
- ICorProfilerInfo2::DoStackSnapshot method [.NET Framework profiling]
- DoStackSnapshot method [.NET Framework profiling]
ms.assetid: 287b11e9-7c52-4a13-ba97-751203fa97f4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3c65e48595f2b49abe06e649898649d76a0668a0
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43733930"
---
# <a name="icorprofilerinfo2dostacksnapshot-method"></a>ICorProfilerInfo2::DoStackSnapshot Yöntemi
Belirtilen iş parçacığı için yığın üzerinde yönetilen çerçeve size yol gösterir ve profil oluşturucu bir geri çağırma aracılığıyla bilgi gönderir.  
  
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
  
 Null geçirme `thread` bir anlık görüntü geçerli iş parçacığının verir. Varsa bir `ThreadID` , farklı bir iş parçacığına geçirilir, ortak dil çalışma zamanı (CLR), iş parçacığını askıya alır, anlık görüntü gerçekleştirir ve sürdürür.  
  
 `callback`  
 [in] Uygulanmasına yönelik bir işaretçi [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) profil oluşturucu yönetilen her çerçeve ve yönetilmeyen karelerin her çalıştırma hakkında bilgi sağlamak için CLR tarafından çağrılan yöntem.  
  
 `StackSnapshotCallback` Yöntemi, profil oluşturucu yazıcı tarafından uygulanır.  
  
 `infoFlags`  
 [in] Değerini [cor_prf_snapshot_ınfo](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md) tarafından her çerçeve için geri geçirilmesi veri miktarını belirten sabit listesi `StackSnapshotCallback`.  
  
 `clientData`  
 [in] Düz aracılığıyla geçirilen istemci verilerini bir işaretçiye `StackSnapshotCallback` geri çağırma işlevi.  
  
 `context`  
 [in] Bir Win32 işaretçisi `CONTEXT` yapısı, yığın ilerlemesi sağlamak için kullanılır. Win32 `CONTEXT` yapısı CPU yazmaçların değerleri içeren ve zaman içinde belirli bir anda CPU durumunu temsil eder.  
  
 Çekirdek yığının üstü Yardımcısı yönetilmeyen kodu varsa, yığın ilerlemesi başlamak nereye belirleme CLR yardımcı olur; Aksi takdirde, çekirdek göz ardı edilir. Bir çekirdek için zaman uyumsuz bir Yürüme sağlanmalıdır. Zaman uyumlu Yürüme yapıyorsanız, hiçbir çekirdek gereklidir.  
  
 `context` Parametredir COR_PRF_SNAPSHOT_CONTEXT bayrağı yalnızca geçirilen geçerli `infoFlags` parametresi.  
  
 `contextSize`  
 [in] Boyutu `CONTEXT` tarafından başvurulan yapısını `context` parametresi.  
  
## <a name="remarks"></a>Açıklamalar  
 Null geçirme `thread` bir anlık görüntü geçerli iş parçacığının verir. Yalnızca hedef iş parçacığı zaman askıya alınırsa anlık görüntüleri diğer iş parçacıklarını alınabilir.  
  
 Profil Oluşturucu yığın geçmek istediği zaman, çağırdığı `DoStackSnapshot`. CLR döndürür o çağrıdan önce çağırır, `StackSnapshotCallback` birkaç kez kez her biri için çerçeve (veya yönetilmeyen çerçeve Çalıştır) yığın üzerinde yönetilen. Yönetilmeyen çerçeveler karşılaştığında, bunları kendiniz yol gerekir.  
  
 Çerçeve yığınına nasıl gönderildi, geriye doğru yığın öğrendiniz, sırasıdır: son (en son gönderilen) ilk, ana (ilk gönderildi) kareler yaprak.  
  
 Profil oluşturucuyu yönetilen yığınları ilerletmek hakkında daha fazla bilgi için bkz. [.NET Framework 2.0 Profiler Programlayacağınız yığın: temeller ve ötesi](https://go.microsoft.com/fwlink/?LinkId=73638).  
  
 Yığın ilerlemesi, aşağıdaki bölümlerde açıklandığı gibi zaman uyumlu veya zaman uyumsuz olabilir.  
  
## <a name="synchronous-stack-walk"></a>Zaman uyumlu yığın ilerlemesi  
 Zaman uyumlu yığın ilerlemesi, geçerli iş parçacığının yığınını yanıt olarak bir geri çağırma walking içerir. Dengeli dağıtım veya askıya alma gerektirmez.  
  
 Eş zamanlı yaptığınız zaman, yanıt olarak CLR, profil oluşturucunun birini çağırma çağrısı [Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) (veya [Icorprofilercallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)) yöntemleri çağırmanızı `DoStackSnapshot` yığınını görmek için Geçerli iş parçacığı. Yığın bir bildirim gibi nasıl göründüğünü görmek istediğinizde yararlıdır [Icorprofilercallback::objectallocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md). Çağrı `DoStackSnapshot` içinden, `ICorProfilerCallback` null geçirerek yöntemini `context` ve `thread` parametreleri.  
  
## <a name="asynchronous-stack-walk"></a>Zaman uyumsuz yığın ilerlemesi  
 Bir zaman uyumsuz yığın ilerlemesi, farklı iş parçacığı yığınının walking veya yanıt için bir geri çağırma, ancak geçerli iş parçacığının yönerge işaretçisini ele geçirme tarafından değil, geçerli iş parçacığının yığınını walking kapsar. Zaman uyumsuz bir Yürüme yığının üstü bir platform parçası değil, yönetilmeyen kod ise bir çekirdek çağırma (PInvoke) gerektirir. COM çağrısı ancak veya CLR yardımcı kod. Örneğin, just-ın-time (JIT) derleme veya çöp toplama yapan kod Yardımcısını kodudur.  
  
 Doğrudan hedef iş parçacığını askıya alma, bir çekirdek elde ve kendi yığınını walking kendiniz, üstteki bulana kadar çerçeve yönetilir. Hedef iş parçacığını askıya sonra hedef iş parçacığının geçerli kayıt bağlamını alın. Ardından, çağırarak kayıt bağlam yönetilmeyen koda işaret edip etmediğini belirleme [Icorprofilerınfo::getfunctionfromıp](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md) — döndürürse bir `FunctionID` sıfıra eşit, yönetilmeyen kod çerçevesidir. Şimdi ilk yönetilen çerçeve ulaşın ve daha sonra bu kare için kayıt bağlam temel çekirdek bağlam hesaplamak kadar yığın yol.  
  
 Çağrı `DoStackSnapshot` ile zaman uyumsuz yığın ilerlemesi başlamak için çekirdek bağlamı. Bir çekirdek sağlamazsanız `DoStackSnapshot` yığının üstünde bir yönetilen çerçeve atla ve sonuç olarak, bir tam bir yığın ilerlemesi verecektir. Bir çekirdek sağlarsanız, JIT olarak derlenmiş veya yerel Görüntü Oluşturucu (Ngen.exe) için işaret etmelidir-oluşturulan kod; Aksi takdirde, `DoStackSnapshot` CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX hata kodu döndürüyor.  
  
 Zaman uyumsuz yığın Yürüyüşü kolayca kilitlenmeleri neden veya bu yönergelere uymanızı sürece ihlalleri, erişim:  
  
-   Doğrudan iş parçacıkları askıya aldığınızda, yalnızca yönetilen kod çalıştırılmadı bir iş parçacığı başka bir iş parçacığını askıya alabilirsiniz unutmayın.  
  
-   Her zaman engellenmesi, [Icorprofilercallback::threaddestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md) parçacığının yığın ilerlemesi tamamlanana kadar geri çağırma.  
  
-   Profil Oluşturucu bir çöp toplama tetikleyen bir CLR işleve çağrı sırasında kilit tutmayın. Diğer bir deyişle, sahip olan iş parçacığı bir atık toplama işlemini tetikleyen bir çağrı yaparsanız bir kilit tutmayın.  
  
 Olup olmadığını da kilitlenme riski çağırmanızı `DoStackSnapshot` , profil oluşturucu oluşturdu ve böylece ayrı hedef iş parçacığı yığınının inceleyebileceğiniz bir iş parçacığından. İlk kez oluşturduğunuz iş parçacığı girer belirli `ICorProfilerInfo*` yöntemleri (dahil olmak üzere `DoStackSnapshot`), CLR iş parçacığı başına, bu iş parçacığı üzerinde CLR özel başlatma gerçekleştirir. Profil Oluşturucu yığını yol çalıştığınız hedef diziyle askıya aldı ve bu hedef iş parçacığı bir kilide bu iş parçacığı başına başlatma gerçekleştirmek için gerekli sahip oluştuysa, karşılıklı bir kilitlenme ortaya çıkar. Bu kilitlenmeyi önlemek için bir ilk çağrı yapmak `DoStackSnapshot` yürütmek için Profil Oluşturucu tarafından oluşturulan iş parçacığından ayrı bir hedef iş parçacığı, ancak hedef iş parçacığı önce askıya değil. Bu ilk çağrı, iş parçacığı başına başlatma kilitlenme tamamlayabilirsiniz sağlar. Varsa `DoStackSnapshot` başarılı olur ve en az bir çerçeve raporları bu noktadan sonra herhangi bir hedef iş parçacığı ve çağrı askıya alma, Profil Oluşturucu tarafından oluşturulan iş parçacığı için güvenli olacaktır `DoStackSnapshot` bu hedef iş parçacığı yığınını görmek için.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
