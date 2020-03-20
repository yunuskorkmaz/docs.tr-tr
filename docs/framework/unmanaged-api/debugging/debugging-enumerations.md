---
title: Hata Ayıklama Numaralandırmaları
ms.date: 03/30/2017
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
ms.openlocfilehash: c37b6ff42b428184d301d63b6dbbd9d80a72bf3f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179137"
---
# <a name="debugging-enumerations"></a>Hata Ayıklama Numaralandırmaları
Bu bölümde, hata ayıklama API'sinin kullandığı yönetilmeyen sayısallaştırmalar açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [CLR_DEBUGGING_PROCESS_FLAGS Numaralandırması](clr-debugging-process-flags-enumeration.md)  
 [ICLRDebugging::OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) yöntemi tarafından kullanılan değerleri sağlar.  
  
 [CLRDataEnumMemoryFlags Sabit Listesi](clrdataenummemoryflags-enumeration.md)  
 [ICLRDataEnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) için bir çağrı hangi bellek bölgeleri gösterir::EnumMemoryRegions yöntemi içermelidir.  
  
 [COR_PUB_ENUMPROCESS Numaralandırması](cor-pub-enumprocess-enumeration.md)  
 Numaralandırılacak işlem türünü tanımlar.  
  
 [CorDebugBlockingReason Numaralandırması](cordebugblockingreason-enumeration.md)  
 Bir iş parçacığının belirli bir nesne üzerinde engellenme nedenlerini belirtir.  
  
 CorDebugChainReason  
 Çağrı zincirinin başlatılmasının nedenini veya nedenlerini gösterir.  
  
 [CorDebugCodeInvokeKind Numaralandırması](cordebugcodeinvokekind-enumeration.md)  
 Dışa aktarılan bir işlevin yönetilen kodu nasıl çağırdığını açıklar.  
  
 [CorDebugCodeInvokePurpose Numaralandırması](cordebugcodeinvokepurpose-enumeration.md)  
 Dışa aktarılan bir işlevin yönetilen kodu neden aradığını açıklar.  
  
 CorDebugCreateProcessFlags  
 [ICorDebug::CreateProcess](icordebug-createprocess-method.md) yöntemine yapılan bir çağrıda kullanılabilecek ek hata ayıklama seçenekleri sağlar.  
  
 [CorDebugDebugEventKind Numaralandırması](cordebugdebugeventkind-enumeration.md)  
 [DecodeEvent](icordebugprocess6-decodeevent-method.md) yöntemiyle bilgileri deşifre edilen olayın türünü gösterir.  
  
 [CorDebugDecodeEventFlagsWindows Sabit Listesi](cordebugdecodeeventflagswindows-enumeration.md)  
 Windows platformundaki hata ayıklama olayları hakkında ek bilgiler sağlar.  
  
 CorDebugExceptionCallbackType  
 [ICorDebugManagedCallback2::Özel durum](icordebugmanagedcallback2-exception-method.md) olayından yapılan geri arama türünü gösterir.  
  
 [CorDebugExceptionFlags Sabit Listesi](cordebugexceptionflags-enumeration.md)  
 Özel durum hakkında ek bilgiler sağlar.  
  
 CorDebugExceptionUnwindCallbackType  
 Gevşeme aşamasında geri arama tarafından sinyal verilen olayı gösterir.  
  
 [CorDebugGCType Sabit Listesi](cordebuggctype-enumeration.md)  
 Çöp toplayıcısının iş istasyonunda mı yoksa sunucuda mı çalıştığını gösterir.  
  
 [CorDebugGenerationTypes Sabit Listesi](cordebuggenerationtypes-enumeration.md)  
 Yönetilen yığında bellek bir bölgenin nesil belirtir.  
  
 CorDebugHandleType  
 Tutamaç türünü gösterir.  
  
 [CorDebugIlToNativeMappingTypes Numaralandırması](cordebugiltonativemappingtypes-enumeration.md)  
 Belirli bir yerel yönerge aralığının özel bir kod bölgesine karşılık gelip gelmediğini gösterir.  
  
 CorDebugIntercept  
 Adım atılabilir kod türlerini gösterir.  
  
 [CorDebugInterfaceVersion Numaralandırması](cordebuginterfaceversion-enumeration.md)  
 .NET Framework'ün bir sürümünü veya arabirimin tanıtıldığı .NET Framework sürümünü belirtir.  
  
 CorDebugInternalFrameType  
 Yığın çerçevesinin türünü tanımlar.  
  
 [CorDebugJITCompilerFlags Numaralandırması](cordebugjitcompilerflags-enumeration.md)  
 Yönetilen tam zamanında (JIT) derleyicisinin davranışını etkileyen değerler içerir.  
  
 [CorDebugJITCompilerFlagsDeprecated Numaralandırması](cordebugjitcompilerflagsdeprecated-enumeration.md)  
 Kullanımdan kalktı. Bunun `CORDEBUG_JIT_DEFAULT` yerine [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) numaralandırma üyesini kullanın.  
  
 CorDebugMappingResult  
 Yönerge işaretçisinin (IP) değerinin nasıl elde edildiğine ilişkin ayrıntıları sağlar.  
  
 [CorDebugMDAFlags Sabit Listesi](cordebugmdaflags-enumeration.md)  
 Yönetilen hata ayıklama yardımcısının (MDA) kovulduğunuiş iş parçacığının durumunu belirtir.  
  
 [CorDebugNGenPolicy Sabit Listesi](cordebugngenpolicy-enumeration.md)  
 Hata ayıkıcının yerel görüntü önbelleğinden yerel (NGen) görüntüler yükleyip yüklemediğini belirleyen bir değer sağlar.  
  
 [CorDebugPlatform Numaralandırması](cordebugplatform-enumeration.md)  
 [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) yöntemi tarafından kullanılan hedef platform değerlerini sağlar.  
  
 [CorDebugRecordFormat Sabit Listesi](cordebugrecordformat-enumeration.md)  
 Yerel bir özel durum hata ayıklama olayı hakkında bilgi içeren bir bayt dizisinde verilerin biçimini açıklar.  
  
 CorDebugRegister  
 Belirli bir işlemci mimarisiyle ilişkili kayıtları belirtir.  
  
 [CorDebugSetContextFlag Numaralandırması](cordebugsetcontextflag-enumeration.md)  
 Bağlamın yığındaki etkin (veya yaprak) çerçeveden mi yoksa başka bir çerçeveden gevşemeyle hesaplanıp hesaplanmadığını gösterir.  
  
 [CorDebugStateChange Sabit Listesi](cordebugstatechange-enumeration.md)  
 İşlemdeki değişikliklere bağlı olarak atılması gereken önbelleğe alınmış veri miktarını açıklar.  
  
 CorDebugStepReason  
 Tek bir adımın sonucunu gösterir.  
  
 CorDebugThreadState  
 Hata ayıklama için bir iş parçacığının durumunu belirtir.  
  
 \>CorDebugUnmappedStop  
 Adım layıcı tarafından kod yürütülmesinde durmayı tetiklenebilen eşlenmemiş kod türünü belirtir.  
  
 CorDebugUserState  
 İş parçacığının kullanıcı durumunu gösterir.  
  
 [CorGCReferenceType Sabit Listesi](corgcreferencetype-enumeration.md)  
 Çöp toplanacak bir nesnenin kaynağını tanımlar.  
  
 [ILCodeKind Numaralandırması](ilcodekind-enumeration.md)  
 Hata ayıklayıcının yerel değişkenlere veya profil oluşturucu ReJIT enstrümantasyonuna eklenen koda erişip erişemeyeceğini belirten değerler sağlar.  
  
 [LoggingLevelEnum Sabit Listesi](logginglevelenum-enumeration.md)  
 Yönetilen bir iş parçacığı bir olay günlüğe kaydettiğinde olay günlüğüne yazılan açıklayıcı iletinin önem düzeyini gösterir.  
  
 [LogSwitchCallReason Numaralandırması](logswitchcallreason-enumeration.md)  
 Hata ayıklama/izleme anahtarında gerçekleştirilen işlemi gösterir.  
  
 [VariableLocationType Sabit Listesi](variablelocationtype-enumeration.md)  
 Bir değişkenin yerel konum türünü gösterir.  
  
 [WriteableMetadataUpdateMode Sabit Listesi](writeablemetadataupdatemode-enumeration.md)  
 Meta verilerdeki bellek güncelleştirmelerinin hata ayıklayan tarafından görülüp görülemeyeceğini belirten değerler sağlar.

 [ClrDataSourceType Numaralandırma](clrdatasourcetype-enumeration.md) CLRDATA_IL_ADDRESS_MAP yapısı tarafından kullanılan değerleri sağlar.

## <a name="related-sections"></a>İlgili Bölümler  
 [Hata Ayıklama Yardımcı Sınıfları](debugging-coclasses.md)  
  
 [Hata Ayıklama Arabirimleri](debugging-interfaces.md)  
  
 [Hata Ayıklama Genel Statik İşlevleri](debugging-global-static-functions.md)  
  
 [Hata Ayıklama Yapıları](debugging-structures.md)
