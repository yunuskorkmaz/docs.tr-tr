---
description: 'Daha fazla bilgi: Numaralandırmalar hata ayıklaması'
title: Hata Ayıklama Numaralandırmaları
ms.date: 03/30/2017
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
ms.openlocfilehash: 4a1d2fc9061fec7f5384418e4893c357f5d340ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801429"
---
# <a name="debugging-enumerations"></a>Hata Ayıklama Numaralandırmaları

Bu bölümde hata ayıklama API 'sinin kullandığı yönetilmeyen numaralandırmalar açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [CLR_DEBUGGING_PROCESS_FLAGS Numaralandırması](clr-debugging-process-flags-enumeration.md)  
 [ICLRDebugging:: OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) yöntemi tarafından kullanılan değerleri sağlar.  
  
 [CLRDataEnumMemoryFlags Numaralandırması](clrdataenummemoryflags-enumeration.md)  
 Hangi bellek bölgelerinin [ıclrdataenummemoryregion:: EnumMemoryRegion](iclrdataenummemoryregions-enummemoryregions-method.md) yöntemine yönelik bir çağrı içermesi gerektiğini gösterir.  
  
 [COR_PUB_ENUMPROCESS Numaralandırması](cor-pub-enumprocess-enumeration.md)  
 Numaralandırılacak işlemin türünü tanımlar.  
  
 [CorDebugBlockingReason Numaralandırması](cordebugblockingreason-enumeration.md)  
 Bir iş parçacığının belirli bir nesne üzerinde engellenip engellenme nedenlerini belirtir.  
  
 CorDebugChainReason  
 Bir çağrı zincirinin başlatılması için neden veya nedenleri gösterir.  
  
 [CorDebugCodeInvokeKind Numaralandırması](cordebugcodeinvokekind-enumeration.md)  
 Bir içe aktarılmış işlevin yönetilen kodu nasıl çağırılacağını açıklar.  
  
 [CorDebugCodeInvokePurpose Numaralandırması](cordebugcodeinvokepurpose-enumeration.md)  
 Bir içe aktarılmış işlevin neden yönetilen kodu çağırıyor olduğunu açıklar.  
  
 CorDebugCreateProcessFlags  
 [ICorDebug:: CreateProcess](icordebug-createprocess-method.md) metoduna yapılan bir çağrıda kullanılabilecek ek hata ayıklama seçenekleri sağlar.  
  
 [CorDebugDebugEventKind Numaralandırması](cordebugdebugeventkind-enumeration.md)  
 Bilgileri [DecodeEvent](icordebugprocess6-decodeevent-method.md) yöntemi tarafından kodu çözülen olay türünü gösterir.  
  
 [CorDebugDecodeEventFlagsWindows Numaralandırması](cordebugdecodeeventflagswindows-enumeration.md)  
 Windows platformunda hata ayıklama olayları hakkında ek bilgi sağlar.  
  
 CorDebugExceptionCallbackType  
 Bir [ICorDebugManagedCallback2:: Exception](icordebugmanagedcallback2-exception-method.md) olayından yapılan geri aramanın türünü gösterir.  
  
 [CorDebugExceptionFlags Numaralandırması](cordebugexceptionflags-enumeration.md)  
 Bir özel durum hakkında ek bilgi sağlar.  
  
 CorDebugExceptionUnwindCallbackType  
 Geriye doğru izleme aşamasında geri çağırma tarafından sinyal edilen olayı gösterir.  
  
 [CorDebugGCType Sabit Listesi](cordebuggctype-enumeration.md)  
 Çöp toplayıcının bir iş istasyonunda veya sunucuda çalışıp çalışmadığını belirtir.  
  
 [CorDebugGenerationTypes Sabit Listesi](cordebuggenerationtypes-enumeration.md)  
 Yönetilen yığında bir bellek bölgesinin üretilmesini belirtir.  
  
 CorDebugHandleType  
 Tanıtıcı türünü gösterir.  
  
 [CorDebugIlToNativeMappingTypes Numaralandırması](cordebugiltonativemappingtypes-enumeration.md)  
 Belirli bir yerel yönerge aralığının özel bir kod bölgesine karşılık geldiğini gösterir.  
  
 CorDebugIntercept  
 İçine bulanan kod türlerini gösterir.  
  
 [CorDebugInterfaceVersion Numaralandırması](cordebuginterfaceversion-enumeration.md)  
 .NET Framework sürümünü veya bir arabirimin tanıtılmasıyla .NET Framework sürümünü belirtir.  
  
 CorDebugInternalFrameType  
 Yığın çerçevesinin türünü tanımlar.  
  
 [CorDebugJITCompilerFlags Numaralandırması](cordebugjitcompilerflags-enumeration.md)  
 Yönetilen Just-In-Time (JıT) derleyicisinin davranışını etkileyen değerler içerir.  
  
 [CorDebugJITCompilerFlagsDeprecated Numaralandırması](cordebugjitcompilerflagsdeprecated-enumeration.md)  
 Kullanımdan kalktı. `CORDEBUG_JIT_DEFAULT`Bunun yerine [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) numaralandırmasının üyesini kullanın.  
  
 CorDebugMappingResult  
 Yönerge işaretçisinin (IP) değerinin nasıl alındıklarına ilişkin ayrıntıları sağlar.  
  
 [CorDebugMDAFlags Numaralandırması](cordebugmdaflags-enumeration.md)  
 Yönetilen hata ayıklama Yardımcısı 'nın (MDA) harekete geçirildiği iş parçacığının durumunu belirtir.  
  
 [CorDebugNGenPolicy Sabit Listesi](cordebugngenpolicy-enumeration.md)  
 Bir hata ayıklayıcının yerel görüntü önbelleğinden yerel (NGen) görüntüler yükleyip yüklemeyeceğini belirleyen bir değer sağlar.  
  
 [CorDebugPlatform Numaralandırması](cordebugplatform-enumeration.md)  
 [ICorDebugDataTarget:: GetPlatform](icordebugdatatarget-getplatform-method.md) yöntemi tarafından kullanılan hedef platform değerlerini sağlar.  
  
 [CorDebugRecordFormat Numaralandırması](cordebugrecordformat-enumeration.md)  
 Bir yerel özel durum ayıklama olayı hakkında bilgi içeren bir bayt dizisindeki verilerin biçimini açıklar.  
  
 CorDebugRegister  
 Belirli bir işlemci mimarisiyle ilişkili kayıtları belirtir.  
  
 [CorDebugSetContextFlag Numaralandırması](cordebugsetcontextflag-enumeration.md)  
 Bağlamın yığındaki etkin (veya yaprak) kareden mi olduğunu yoksa başka bir çerçeveden geriye doğru bir şekilde mi hesaplandığını gösterir.  
  
 [CorDebugStateChange Numaralandırması](cordebugstatechange-enumeration.md)  
 İşlemdeki değişikliklere göre atılması gereken önbelleğe alınmış verilerin miktarını açıklar.  
  
 CorDebugStepReason  
 Tek bir adımın sonucunu gösterir.  
  
 CorDebugThreadState  
 Hata ayıklama için bir iş parçacığının durumunu belirtir.  
  
 \>CorDebugUnmappedStop  
 Stepper tarafından kod yürütmede bir durdurmak tetikleyemeyecek eşlenmemiş kod türünü belirtir.  
  
 CorDebugUserState  
 Bir iş parçacığının kullanıcı durumunu belirtir.  
  
 [CorGCReferenceType Sabit Listesi](corgcreferencetype-enumeration.md)  
 Atık olarak toplanmış bir nesnenin kaynağını tanımlar.  
  
 [ILCodeKind Numaralandırması](ilcodekind-enumeration.md)  
 Hata ayıklayıcının profil oluşturucu ReJIT araçları 'nda eklenen yerel değişkenlere veya koda erişip erişemeyeceğini belirten değerler sağlar.  
  
 [LoggingLevelEnum Numaralandırması](logginglevelenum-enumeration.md)  
 Yönetilen bir iş parçacığı bir olay günlüğe kaydederken olay günlüğüne yazılan açıklayıcı bir iletinin önem derecesini gösterir.  
  
 [LogSwitchCallReason Numaralandırması](logswitchcallreason-enumeration.md)  
 Hata ayıklama/izleme anahtarı üzerinde gerçekleştirilen işlemi gösterir.  
  
 [VariableLocationType Sabit Listesi](variablelocationtype-enumeration.md)  
 Bir değişkenin yerel konum türünü gösterir.  
  
 [WriteableMetadataUpdateMode Numaralandırması](writeablemetadataupdatemode-enumeration.md)  
 Meta verilerde bellek içi güncelleştirmelerin hata ayıklayıcıya görünür olup olmadığını belirten değerler sağlar.

 [ClrDataSourceType numaralandırması](clrdatasourcetype-enumeration.md) CLRDATA_IL_ADDRESS_MAP yapısı tarafından kullanılan değerleri sağlar.

## <a name="related-sections"></a>İlgili Bölümler  

 [Hata Ayıklama Yardımcı Sınıfları](debugging-coclasses.md)  
  
 [Hata Ayıklama Arabirimleri](debugging-interfaces.md)  
  
 [Hata Ayıklama Genel Statik İşlevleri](debugging-global-static-functions.md)  
  
 [Hata Ayıklama Yapıları](debugging-structures.md)
