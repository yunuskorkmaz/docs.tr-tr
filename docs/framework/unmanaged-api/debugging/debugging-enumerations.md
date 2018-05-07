---
title: Hata Ayıklama Numaralandırmaları
ms.date: 03/30/2017
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b81e7c2ffabdee78af34d00c48fb29c7525dea08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="debugging-enumerations"></a>Hata Ayıklama Numaralandırmaları
Bu bölümde, hata ayıklama API'si kullanan yönetilmeyen numaralandırmalar açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [CLR_DEBUGGING_PROCESS_FLAGS Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md)  
 Tarafından kullanılan değerleri sağlayan [Iclrdebugging::openvirtualprocess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) yöntemi.  
  
 [CLRDataEnumMemoryFlags Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md)  
 Hangi bellek bölümlerinin yapılan bir çağrı gösterir [Iclrdataenummemoryregions::enummemoryregions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) yöntemi içermelidir.  
  
 [COR_PUB_ENUMPROCESS Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md)  
 Numaralandırılacak işlem türünü tanımlar.  
  
 [CorDebugBlockingReason Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingreason-enumeration.md)  
 Bir iş parçacığı neden engellenmiş duruma nedeniyle belirli bir nesne üzerinde belirtir.  
  
 CorDebugChainReason  
 Neden veya çağrı zincirine başlatma nedenlerle gösterir.  
  
 [CorDebugCodeInvokeKind Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md)  
 Yönetilen kod nasıl verilen işlevi çağırır açıklar.  
  
 [CorDebugCodeInvokePurpose Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md)  
 Yönetilen kod neden verilen işlevi çağırır açıklar.  
  
 CorDebugCreateProcessFlags  
 Çağrıda kullanılan ek hata ayıklama seçenekleri sunar [Icordebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) yöntemi.  
  
 [CorDebugDebugEventKind Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)  
 , Bilgileri kodunu çözdü olay türünü gösterir [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) yöntemi.  
  
 [CorDebugDecodeEventFlagsWindows Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md)  
 Hata ayıklama olaylar hakkında ek bilgi Windows platformunda sağlar.  
  
 CorDebugExceptionCallbackType  
 Gelen yaptığınız geri çağırma türünü gösteren bir [Icordebugmanagedcallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) olay.  
  
 [CorDebugExceptionFlags Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)  
 Bir özel durum hakkında ek bilgi sağlar.  
  
 CorDebugExceptionUnwindCallbackType  
 Geri çağırma göre geriye doğru izleme aşamasında işaret olay gösterir.  
  
 [CorDebugGCType Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md)  
 Çöp toplayıcı bir iş istasyonunda veya sunucuda çalışıp çalışmadığını gösterir.  
  
 [CorDebugGenerationTypes Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md)  
 Bellek bölgesi nesil yönetilen yığında belirtir.  
  
 CorDebugHandleType  
 Tanıtıcı türü gösterir.  
  
 [CorDebugIlToNativeMappingTypes Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md)  
 Yerel yönergeleri belirli bir dizi özel kod bölgesine karşılık gelen olup olmadığını gösterir.  
  
 Cordebugıntercept  
 İçine adım adım kod türlerini belirtir.  
  
 [CorDebugInterfaceVersion Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md)  
 .NET Framework sürümü ya da bir arabirim kullanılmaya başlanan .NET Framework sürümünü belirtir.  
  
 Cordebugınternalframetype  
 Yığın çerçevesi türünü tanımlar.  
  
 [CorDebugJITCompilerFlags Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)  
 Yönetilen tam zamanında (JIT) derleyici davranışını etkilemek değerlerini içerir.  
  
 [CorDebugJITCompilerFlagsDeprecated Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflagsdeprecated-enumeration.md)  
 Kullanımdan kalktı. Kullanım `CORDEBUG_JIT_DEFAULT` üyesi [Cordebugjıtcompilerflags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) numaralandırma yerine.  
  
 CorDebugMappingResult  
 Yönerge işaretçisi (IP) değerini nasıl edinilen ayrıntılarını sağlar.  
  
 [CorDebugMDAFlags Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md)  
 İş parçacığı üzerinde yönetilen hata ayıklama Yardımcısı (MDA) tetiklenir durumunu belirtir.  
  
 [CorDebugNGenPolicy Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md)  
 Bir hata ayıklayıcısı yerel görüntü önbellekten yerel (NGen) görüntüler yükler olup olmadığını belirleyen bir değer sağlar.  
  
 [CorDebugPlatform Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md)  
 Tarafından kullanılan hedef platform değerleri sağlayan [Icordebugdatatarget::getplatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) yöntemi.  
  
 [CorDebugRecordFormat Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
 Yerel özel durum hata ayıklama olay hakkında bilgi içeren bir bayt dizisi verilerin biçimini tanımlar.  
  
 CorDebugRegister  
 Verilen işlemci mimarisi ile ilişkili olan kayıtları belirtir.  
  
 [CorDebugSetContextFlag Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md)  
 Bağlam etkin olup olmadığını gösterir (veya yaprak) çerçeve yığında veya başka bir çerçevesinden geriye doğru izleme tarafından hesaplanır.  
  
 [CorDebugStateChange Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugstatechange-enumeration.md)  
 Değişiklikleri işleme dayalı atılan gerekir önbelleğe alınan veri miktarı açıklar.  
  
 CorDebugStepReason  
 Tek bir adımı sonucunu gösterir.  
  
 CorDebugThreadState  
 Hata ayıklama için bir iş parçacığı durumunu belirtir.  
  
 \>CorDebugUnmappedStop  
 Kod yürütülmesine durdurmak tarafından Adımlayıcı tetikleyebilir eşlenmemiş kod türünü belirtir.  
  
 CorDebugUserState  
 Bir iş parçacığı kullanıcı durumunu gösterir.  
  
 [CorGCReferenceType Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)  
 Çöp toplanan olması için bir nesne kaynak tanımlar.  
  
 [ILCodeKind Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md)  
 Hata ayıklayıcı yerel değişkenler veya profiler ReJIT araçları eklenen kod erişmek yapılıp yapılamayacağını belirten değerleri sağlar.  
  
 [LoggingLevelEnum Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md)  
 Yönetilen iş parçacığı bir olayı günlüğe kaydettiğinde, olay günlüğüne yazılır açıklayıcı bir ileti önem düzeyini gösterir.  
  
 [LogSwitchCallReason Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md)  
 Hata ayıklama izleme anahtarı üzerinde gerçekleştirilen işlemi gösterir.  
  
 [VariableLocationType Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)  
 Bir değişken yerel konum türünü belirtir.  
  
 [WriteableMetadataUpdateMode Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md)  
 Bellek içi güncelleştirmeleri meta verilerinin bir hata ayıklayıcısı görünür olup olmadığını belirten değerleri sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Hata Ayıklama Coclass’ları](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [Hata Ayıklama Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [Hata Ayıklama Yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
