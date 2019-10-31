---
title: Hata Ayıklama Numaralandırmaları
ms.date: 03/30/2017
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
ms.openlocfilehash: 7948b78da1db5267ce53364af1e4a26ff73801e0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124327"
---
# <a name="debugging-enumerations"></a>Hata Ayıklama Numaralandırmaları
Bu bölümde hata ayıklama API 'sinin kullandığı yönetilmeyen numaralandırmalar açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [CLR_DEBUGGING_PROCESS_FLAGS Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md)  
 [ICLRDebugging:: OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) yöntemi tarafından kullanılan değerleri sağlar.  
  
 [CLRDataEnumMemoryFlags Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md)  
 Hangi bellek bölgelerinin [ıclrdataenummemoryregion:: EnumMemoryRegion](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) yöntemine yönelik bir çağrı içermesi gerektiğini gösterir.  
  
 [COR_PUB_ENUMPROCESS Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md)  
 Numaralandırılacak işlemin türünü tanımlar.  
  
 [CorDebugBlockingReason Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingreason-enumeration.md)  
 Bir iş parçacığının belirli bir nesne üzerinde engellenip engellenme nedenlerini belirtir.  
  
 CorDebugChainReason  
 Bir çağrı zincirinin başlatılması için neden veya nedenleri gösterir.  
  
 [CorDebugCodeInvokeKind Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md)  
 Bir içe aktarılmış işlevin yönetilen kodu nasıl çağırılacağını açıklar.  
  
 [CorDebugCodeInvokePurpose Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md)  
 Bir içe aktarılmış işlevin neden yönetilen kodu çağırıyor olduğunu açıklar.  
  
 CorDebugCreateProcessFlags  
 [ICorDebug:: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) metoduna yapılan bir çağrıda kullanılabilecek ek hata ayıklama seçenekleri sağlar.  
  
 [CorDebugDebugEventKind Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)  
 Bilgileri [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) yöntemi tarafından kodu çözülen olay türünü gösterir.  
  
 [CorDebugDecodeEventFlagsWindows Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md)  
 Windows platformunda hata ayıklama olayları hakkında ek bilgi sağlar.  
  
 CorDebugExceptionCallbackType  
 Bir [ICorDebugManagedCallback2:: Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) olayından yapılan geri aramanın türünü gösterir.  
  
 [CorDebugExceptionFlags Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)  
 Bir özel durum hakkında ek bilgi sağlar.  
  
 CorDebugExceptionUnwindCallbackType  
 Geriye doğru izleme aşamasında geri çağırma tarafından sinyal edilen olayı gösterir.  
  
 [CorDebugGCType Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md)  
 Çöp toplayıcının bir iş istasyonunda veya sunucuda çalışıp çalışmadığını belirtir.  
  
 [CorDebugGenerationTypes Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md)  
 Yönetilen yığında bir bellek bölgesinin üretilmesini belirtir.  
  
 CorDebugHandleType  
 Tanıtıcı türünü gösterir.  
  
 [CorDebugIlToNativeMappingTypes Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md)  
 Belirli bir yerel yönerge aralığının özel bir kod bölgesine karşılık geldiğini gösterir.  
  
 CorDebugIntercept  
 İçine bulanan kod türlerini gösterir.  
  
 [CorDebugInterfaceVersion Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md)  
 .NET Framework sürümünü veya bir arabirimin tanıtılmasıyla .NET Framework sürümünü belirtir.  
  
 CorDebugInternalFrameType  
 Yığın çerçevesinin türünü tanımlar.  
  
 [CorDebugJITCompilerFlags Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)  
 Yönetilen Just-In-Time (JıT) derleyicisinin davranışını etkileyen değerler içerir.  
  
 [CorDebugJITCompilerFlagsDeprecated Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflagsdeprecated-enumeration.md)  
 Kullanımdan kalktı. Bunun yerine [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) numaralandırmasının `CORDEBUG_JIT_DEFAULT` üyesini kullanın.  
  
 CorDebugMappingResult  
 Yönerge işaretçisinin (IP) değerinin nasıl alındıklarına ilişkin ayrıntıları sağlar.  
  
 [CorDebugMDAFlags Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md)  
 Yönetilen hata ayıklama Yardımcısı 'nın (MDA) harekete geçirildiği iş parçacığının durumunu belirtir.  
  
 [CorDebugNGenPolicy Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md)  
 Bir hata ayıklayıcının yerel görüntü önbelleğinden yerel (NGen) görüntüler yükleyip yüklemeyeceğini belirleyen bir değer sağlar.  
  
 [CorDebugPlatform Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md)  
 [ICorDebugDataTarget:: GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) yöntemi tarafından kullanılan hedef platform değerlerini sağlar.  
  
 [CorDebugRecordFormat Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
 Bir yerel özel durum ayıklama olayı hakkında bilgi içeren bir bayt dizisindeki verilerin biçimini açıklar.  
  
 CorDebugRegister  
 Belirli bir işlemci mimarisiyle ilişkili kayıtları belirtir.  
  
 [CorDebugSetContextFlag Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md)  
 Bağlamın yığındaki etkin (veya yaprak) kareden mi olduğunu yoksa başka bir çerçeveden geriye doğru bir şekilde mi hesaplandığını gösterir.  
  
 [CorDebugStateChange Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugstatechange-enumeration.md)  
 İşlemdeki değişikliklere göre atılması gereken önbelleğe alınmış verilerin miktarını açıklar.  
  
 CorDebugStepReason  
 Tek bir adımın sonucunu gösterir.  
  
 CorDebugThreadState  
 Hata ayıklama için bir iş parçacığının durumunu belirtir.  
  
 \>CorDebugUnmappedStop  
 Stepper tarafından kod yürütmede bir durdurmak tetikleyemeyecek eşlenmemiş kod türünü belirtir.  
  
 CorDebugUserState  
 Bir iş parçacığının kullanıcı durumunu belirtir.  
  
 [CorGCReferenceType Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)  
 Atık olarak toplanmış bir nesnenin kaynağını tanımlar.  
  
 [ILCodeKind Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md)  
 Hata ayıklayıcının profil oluşturucu ReJIT araçları 'nda eklenen yerel değişkenlere veya koda erişip erişemeyeceğini belirten değerler sağlar.  
  
 [LoggingLevelEnum Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md)  
 Yönetilen bir iş parçacığı bir olay günlüğe kaydederken olay günlüğüne yazılan açıklayıcı bir iletinin önem derecesini gösterir.  
  
 [LogSwitchCallReason Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md)  
 Hata ayıklama/izleme anahtarı üzerinde gerçekleştirilen işlemi gösterir.  
  
 [VariableLocationType Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)  
 Bir değişkenin yerel konum türünü gösterir.  
  
 [WriteableMetadataUpdateMode Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md)  
 Meta verilerde bellek içi güncelleştirmelerin hata ayıklayıcıya görünür olup olmadığını belirten değerler sağlar. 

 [ClrDataSourceType numaralandırması](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md) CLRDATA_IL_ADDRESS_MAP yapısı tarafından kullanılan değerleri sağlar.

## <a name="related-sections"></a>İlgili Bölümler  
 [Hata Ayıklama Coclass’ları](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [Hata Ayıklama Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [Hata Ayıklama Yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
