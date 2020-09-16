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
ms.openlocfilehash: ff0ff35f42e20725cab49afd971523aabda866c3
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547830"
---
# <a name="icorprofilerinfo2dostacksnapshot-method"></a>ICorProfilerInfo2::DoStackSnapshot Yöntemi
Belirtilen iş parçacığı için yığındaki yönetilen çerçevelere kılavuzluk eder ve geri çağırma yoluyla profil oluşturucuya bilgi gönderir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT DoStackSnapshot(  
    [in] ThreadID thread,  
    [in] StackSnapshotCallback *callback,  
    [in] ULONG32 infoFlags,  
    [in] void *clientData,  
    [in, size_is(contextSize), length_is(contextSize)] BYTE context[],  
    [in] ULONG32 contextSize);  
```  
  
## <a name="parameters"></a>Parametreler  
 `thread`  
 'ndaki Hedef iş parçacığının KIMLIĞI.  
  
 İçinde null geçirme `thread` , geçerli iş parçacığının bir anlık görüntüsünü verir. Farklı bir `ThreadID` iş parçacığından biri geçirilirse, ortak dil çalışma zamanı (CLR) bu iş parçacığını askıya alır, anlık görüntüyü gerçekleştirir ve sürdürür.  
  
 `callback`  
 'ndaki Profil oluşturucuyu, yönetilen her çerçeve ve her yönetilmeyen çerçeve çalıştırması hakkında bilgi sağlamak için CLR tarafından çağrılan [StackSnapshotCallback](stacksnapshotcallback-function.md) yönteminin uygulamasına yönelik bir işaretçi.  
  
 `StackSnapshotCallback`Yöntemi profil oluşturucu yazıcı tarafından uygulanır.  
  
 `infoFlags`  
 'ndaki Tarafından her çerçeve için geri geçirilecek veri miktarını belirten [COR_PRF_SNAPSHOT_INFO](cor-prf-snapshot-info-enumeration.md) numaralandırması değeri `StackSnapshotCallback` .  
  
 `clientData`  
 'ndaki İstemci verilerine yönelik bir işaretçi, `StackSnapshotCallback` geri çağırma işlevine doğrudan geçirilir.  
  
 `context`  
 'ndaki `CONTEXT` Yığın ilerlemesini temel almak için kullanılan Win32 yapısına yönelik bir işaretçi. Win32 `CONTEXT` yapısı, CPU yazmaçlarının değerlerini içerir ve zaman içinde belirli bir anda CPU 'nun durumunu temsil eder.  
  
 Çekirdek, yığının en üstünde yönetilmeyen yardımcı kod olması halinde CLR 'nin yığın ilerleme durumunu belirlemesine yardımcı olur. Aksi takdirde, çekirdek yok sayılır. Zaman uyumsuz bir ilerleme için çekirdek sağlanmalıdır. Zaman uyumlu bir adım yapıyorsanız, hiçbir çekirdek gerekmez.  
  
 `context`Parametresi yalnızca COR_PRF_SNAPSHOT_CONTEXT bayrağı parametreye geçirilmemişse geçerlidir `infoFlags` .  
  
 `contextSize`  
 'ndaki `CONTEXT` Parametrenin başvurduğu yapının boyutu `context` .  
  
## <a name="remarks"></a>Açıklamalar  
 İçin null geçirme `thread` , geçerli iş parçacığının bir anlık görüntüsünü verir. Yalnızca hedef iş parçacığı zaman askıya alınırsa, anlık görüntüler diğer iş parçacıklarından alınabilir.  
  
 Profil Oluşturucu yığına ilerlemek istediğinde, çağırır `DoStackSnapshot` . CLR Bu çağrıdan geri dönüşden önce, `StackSnapshotCallback` yığın üzerinde her yönetilen çerçeve (veya yönetilmeyen çerçeveler) için birkaç kez bir kez çağrı yapılır. Yönetilmeyen çerçevelerle karşılaşıldığında, bunları kendiniz yapmanız gerekir.  
  
 Yığının hangi sıraya gönderildiği sırası, çerçevelerin yığına nasıl itileceği, ana (ilk itilmiş) çerçevenin en sonda yer aldığı sıra.  
  
 Profil oluşturucunun yönetilen yığınları izlenecek şekilde programlamanın nasıl yapılacağı hakkında daha fazla bilgi için, bkz. [.NET Framework 2,0: temel bilgiler ve daha fazlası Için Profiler Stack](/previous-versions/dotnet/articles/bb264782(v=msdn.10)).  
  
 Aşağıdaki bölümlerde açıklandığı gibi bir yığın adım zaman uyumlu veya zaman uyumsuz olabilir.  
  
## <a name="synchronous-stack-walk"></a>Zaman uyumlu yığın Ilerleme  
 Zaman uyumlu bir yığın, geri çağırmaya yanıt olarak geçerli iş parçacığının yığınını yürüter. Dengeli dağıtım veya askıya alma gerektirmez.  
  
 Profil oluşturucunun [ICorProfilerCallback](icorprofilercallback-interface.md) (veya [ICorProfilerCallback2](icorprofilercallback2-interface.md)) yöntemlerinden birini çağıran clr 'ye yanıt olarak, `DoStackSnapshot` geçerli iş parçacığının yığınını göstermek için çağırdığınız zaman zaman uyumlu bir çağrı yaparsınız. Bu, yığının [ICorProfilerCallback:: Objectalkonumlandırılan](icorprofilercallback-objectallocated-method.md)gibi bir bildirimde nasıl göründüğünü görmek istediğinizde yararlıdır. Yalnızca `DoStackSnapshot` yönteminizin içinden çağrı `ICorProfilerCallback` yapın, ve parametrelerinde null değeri geçirerek `context` `thread` .  
  
## <a name="asynchronous-stack-walk"></a>Zaman uyumsuz yığın Ilerleme  
 Zaman uyumsuz bir yığın, farklı bir iş parçacığının yığınını yürüyerek veya geçerli iş parçacığının yığınını yürüyerek geri çağırmaya yanıt vermez, ancak geçerli iş parçacığının yönerge işaretçisini ele alarak. Zaman uyumsuz bir izlenecek yol, yığının en üstünde platform Invoke (PInvoke) veya COM çağrısının bir parçası olmayan yönetilmeyen kod ise ve CLR 'nin kendisindeki yardımcı kod ise çekirdek gerektirir. Örneğin, tam zamanında (JıT) derleme veya çöp toplama yapan kod yardımcı koddur.  
  
 Hedef iş parçacığını doğrudan askıya alarak ve en üstteki yönetilen çerçeveyi bulana kadar kendi yığınını yürüyerek bir çekirdek elde edersiniz. Hedef iş parçacığı askıya alındıktan sonra, hedef iş parçacığının geçerli kayıt bağlamını alın. Sonra, YAZMAÇ bağlamının [ICorProfilerInfo:: GetFunctionFromIP](icorprofilerinfo-getfunctionfromip-method.md) öğesini çağırarak yönetilmeyen koda işaret ettiğini ve `FunctionID` sıfıra eşit bir değere döndürürse, çerçevenin yönetilmeyen kod olduğunu saptayın. Şimdi, ilk yönetilen çerçeveye ulaşana kadar yığına ilerleme uygulayın ve ardından bu çerçeveye ait yazmaç bağlamına göre çekirdek bağlamını hesaplayın.  
  
 `DoStackSnapshot`Zaman uyumsuz yığın Yürüme başlamak için çekirdek bağlamınıza çağrı yapın. Bir çekirdek sağlamadıysanız, `DoStackSnapshot` yığının en üstünde yönetilen çerçeveleri atlayabilir ve sonuç olarak size tamamlanmamış bir yığın yürüme olanağı verecektir. Çekirdek sağlarsanız, JıT ile derlenen veya yerel görüntü Oluşturucu (Ngen.exe) tarafından oluşturulan kodu işaret etmelidir; Aksi takdirde, `DoStackSnapshot` CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX hata kodunu döndürür.  
  
 Bu yönergeleri izlemeden zaman uyumsuz yığın, kilitlenmeleri veya erişim ihlallerine kolayca yol açabilir:  
  
- İş parçacıklarını doğrudan askıya aldığınızda, yalnızca yönetilen kodu çalıştırmayan bir iş parçacığının başka bir iş parçacığını askıya alamayacağını unutmayın.  
  
- [ICorProfilerCallback:: threadnot](icorprofilercallback-threaddestroyed-method.md) , iş parçacığının yığın yürüme tamamlanana kadar geri çağırmada her zaman engellenir.  
  
- Profiler, bir atık toplamayı tetikleyebilen bir CLR işlevine çağrı yaparken bir kilit tutmayın. Yani, sahip iş parçacığı çöp toplamayı tetikleyen bir çağrı yapamadığında bir kilit tutmayın.  
  
 Ayrıca, `DoStackSnapshot` profil oluşturucunun oluşturduğu bir iş parçacığından çağırdığınızda, ayrı bir hedef iş parçacığının yığınına yol gösterecek bir kilitlenme riski de vardır. Oluşturduğunuz iş parçacığı bazı `ICorProfilerInfo*` yöntemlere (dahil `DoStackSnapshot` ) GIRDIĞINDE, clr bu iş parçacığında iş parçacığı BAŞıNA, clr 'ye özgü başlatma işlemini gerçekleştirir. Profil oluşturucunuz, yığınına kılavuzluk eden hedef iş parçacığını askıya alıyorsa ve bu hedef iş parçacığı bu iş parçacığı başına başlatmayı gerçekleştirmek için gerekli bir kilide gerçekleştiyse, bir kilitlenme meydana gelir. Bu kilitlenmeyi önlemek için, `DoStackSnapshot` Profil Oluşturucu oluşturulmuş iş parçacığından, ayrı bir hedef iş parçacığı için bir ilk çağrı yapın, ancak önce hedef iş parçacığını askıya alın. Bu ilk çağrı, iş parçacığı başına başlatmanın kilitlenme olmadan tamamlanmamasını sağlar. `DoStackSnapshot`Başarılı olursa ve en az bir çerçeve bildirirse, bu noktadan sonra herhangi bir hedef iş parçacığını askıya almak ve `DoStackSnapshot` Bu hedef iş parçacığı yığınını göstermek için çağırmak üzere, profil oluşturucu tarafından oluşturulan iş parçacığı için güvenli olacaktır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 Arabirimi](icorprofilerinfo2-interface.md)
