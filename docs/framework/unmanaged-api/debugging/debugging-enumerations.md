---
title: Hata Ayıklama Numaralandırmaları
ms.date: 03/30/2017
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
ms.openlocfilehash: a83b1aa0b2cc068ed2f73dca04083b1085d45201
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789168"
---
# <a name="debugging-enumerations"></a>Hata Ayıklama Numaralandırmaları
Bu bölümde hata ayıklama API 'sinin kullandığı yönetilmeyen numaralandırmalar açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [CLR_DEBUGGING_PROCESS_FLAGS Sabit Listesi](clr-debugging-process-flags-enumeration.md)  
 [ICLRDebugging:: OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) yöntemi tarafından kullanılan değerleri sağlar.  
  
 [CLRDataEnumMemoryFlags Sabit Listesi](clrdataenummemoryflags-enumeration.md)  
 Hangi bellek bölgelerinin [ıclrdataenummemoryregion:: EnumMemoryRegion](iclrdataenummemoryregions-enummemoryregions-method.md) yöntemine yönelik bir çağrı içermesi gerektiğini gösterir.  
  
 [COR_PUB_ENUMPROCESS Sabit Listesi](cor-pub-enumprocess-enumeration.md)  
 Numaralandırılacak işlemin türünü tanımlar.  
  
 [CorDebugBlockingReason Sabit Listesi](cordebugblockingreason-enumeration.md)  
 Bir iş parçacığının belirli bir nesne üzerinde engellenip engellenme nedenlerini belirtir.  
  
 CorDebugChainReason  
 Bir çağrı zincirinin başlatılması için neden veya nedenleri gösterir.  
  
 [CorDebugCodeInvokeKind Sabit Listesi](cordebugcodeinvokekind-enumeration.md)  
 Bir içe aktarılmış işlevin yönetilen kodu nasıl çağırılacağını açıklar.  
  
 [CorDebugCodeInvokePurpose Sabit Listesi](cordebugcodeinvokepurpose-enumeration.md)  
 Bir içe aktarılmış işlevin neden yönetilen kodu çağırıyor olduğunu açıklar.  
  
 CorDebugCreateProcessFlags  
 [ICorDebug:: CreateProcess](icordebug-createprocess-method.md) metoduna yapılan bir çağrıda kullanılabilecek ek hata ayıklama seçenekleri sağlar.  
  
 [CorDebugDebugEventKind Sabit Listesi](cordebugdebugeventkind-enumeration.md)  
 Bilgileri [DecodeEvent](icordebugprocess6-decodeevent-method.md) yöntemi tarafından kodu çözülen olay türünü gösterir.  
  
 [CorDebugDecodeEventFlagsWindows Sabit Listesi](cordebugdecodeeventflagswindows-enumeration.md)  
 Windows platformunda hata ayıklama olayları hakkında ek bilgi sağlar.  
  
 CorDebugExceptionCallbackType  
 Bir [ICorDebugManagedCallback2:: Exception](icordebugmanagedcallback2-exception-method.md) olayından yapılan geri aramanın türünü gösterir.  
  
 [CorDebugExceptionFlags Sabit Listesi](cordebugexceptionflags-enumeration.md)  
 Bir özel durum hakkında ek bilgi sağlar.  
  
 CorDebugExceptionUnwindCallbackType  
 Geriye doğru izleme aşamasında geri çağırma tarafından sinyal edilen olayı gösterir.  
  
 [CorDebugGCType Sabit Listesi](cordebuggctype-enumeration.md)  
 Çöp toplayıcının bir iş istasyonunda veya sunucuda çalışıp çalışmadığını belirtir.  
  
 [CorDebugGenerationTypes Sabit Listesi](cordebuggenerationtypes-enumeration.md)  
 Yönetilen yığında bir bellek bölgesinin üretilmesini belirtir.  
  
 CorDebugHandleType  
 Tanıtıcı türünü gösterir.  
  
 [CorDebugIlToNativeMappingTypes Sabit Listesi](cordebugiltonativemappingtypes-enumeration.md)  
 Belirli bir yerel yönerge aralığının özel bir kod bölgesine karşılık geldiğini gösterir.  
  
 CorDebugIntercept  
 İçine bulanan kod türlerini gösterir.  
  
 [CorDebugInterfaceVersion Sabit Listesi](cordebuginterfaceversion-enumeration.md)  
 .NET Framework sürümünü veya bir arabirimin tanıtılmasıyla .NET Framework sürümünü belirtir.  
  
 CorDebugInternalFrameType  
 Yığın çerçevesinin türünü tanımlar.  
  
 [CorDebugJITCompilerFlags Sabit Listesi](cordebugjitcompilerflags-enumeration.md)  
 Yönetilen Just-In-Time (JıT) derleyicisinin davranışını etkileyen değerler içerir.  
  
 [CorDebugJITCompilerFlagsDeprecated Sabit Listesi](cordebugjitcompilerflagsdeprecated-enumeration.md)  
 {1&gt;Artık kullanılmıyor.&lt;1} Bunun yerine [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) numaralandırmasının `CORDEBUG_JIT_DEFAULT` üyesini kullanın.  
  
 CorDebugMappingResult  
 Yönerge işaretçisinin (IP) değerinin nasıl alındıklarına ilişkin ayrıntıları sağlar.  
  
 [CorDebugMDAFlags Sabit Listesi](cordebugmdaflags-enumeration.md)  
 Yönetilen hata ayıklama Yardımcısı 'nın (MDA) harekete geçirildiği iş parçacığının durumunu belirtir.  
  
 [CorDebugNGenPolicy Sabit Listesi](cordebugngenpolicy-enumeration.md)  
 Bir hata ayıklayıcının yerel görüntü önbelleğinden yerel (NGen) görüntüler yükleyip yüklemeyeceğini belirleyen bir değer sağlar.  
  
 [CorDebugPlatform Sabit Listesi](cordebugplatform-enumeration.md)  
 [ICorDebugDataTarget:: GetPlatform](icordebugdatatarget-getplatform-method.md) yöntemi tarafından kullanılan hedef platform değerlerini sağlar.  
  
 [CorDebugRecordFormat Sabit Listesi](cordebugrecordformat-enumeration.md)  
 Bir yerel özel durum ayıklama olayı hakkında bilgi içeren bir bayt dizisindeki verilerin biçimini açıklar.  
  
 CorDebugRegister  
 Belirli bir işlemci mimarisiyle ilişkili kayıtları belirtir.  
  
 [CorDebugSetContextFlag Sabit Listesi](cordebugsetcontextflag-enumeration.md)  
 Bağlamın yığındaki etkin (veya yaprak) kareden mi olduğunu yoksa başka bir çerçeveden geriye doğru bir şekilde mi hesaplandığını gösterir.  
  
 [CorDebugStateChange Sabit Listesi](cordebugstatechange-enumeration.md)  
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
  
 [ILCodeKind Sabit Listesi](ilcodekind-enumeration.md)  
 Hata ayıklayıcının profil oluşturucu ReJIT araçları 'nda eklenen yerel değişkenlere veya koda erişip erişemeyeceğini belirten değerler sağlar.  
  
 [LoggingLevelEnum Sabit Listesi](logginglevelenum-enumeration.md)  
 Yönetilen bir iş parçacığı bir olay günlüğe kaydederken olay günlüğüne yazılan açıklayıcı bir iletinin önem derecesini gösterir.  
  
 [LogSwitchCallReason Sabit Listesi](logswitchcallreason-enumeration.md)  
 Hata ayıklama/izleme anahtarı üzerinde gerçekleştirilen işlemi gösterir.  
  
 [VariableLocationType Sabit Listesi](variablelocationtype-enumeration.md)  
 Bir değişkenin yerel konum türünü gösterir.  
  
 [WriteableMetadataUpdateMode Sabit Listesi](writeablemetadataupdatemode-enumeration.md)  
 Meta verilerde bellek içi güncelleştirmelerin hata ayıklayıcıya görünür olup olmadığını belirten değerler sağlar. 

 [ClrDataSourceType numaralandırması](clrdatasourcetype-enumeration.md) CLRDATA_IL_ADDRESS_MAP yapısı tarafından kullanılan değerleri sağlar.

## <a name="related-sections"></a>İlgili Bölümler  
 [Hata Ayıklama Coclass’ları](debugging-coclasses.md)  
  
 [Hata Ayıklama Arabirimleri](debugging-interfaces.md)  
  
 [Hata Ayıklama Genel Statik İşlevleri](debugging-global-static-functions.md)  
  
 [Hata Ayıklama Yapıları](debugging-structures.md)
