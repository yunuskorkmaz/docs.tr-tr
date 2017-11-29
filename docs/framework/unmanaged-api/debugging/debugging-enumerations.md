---
title: "Hata Ayıklama Numaralandırmaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
caps.latest.revision: "27"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c24882f2bd9819043bbc786bd2e5f35129a92744
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="debugging-enumerations"></a>Hata Ayıklama Numaralandırmaları
Bu bölümde, hata ayıklama API'si kullanan yönetilmeyen numaralandırmalar açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Clr_debuggıng_process_flags numaralandırması](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md)  
 Tarafından kullanılan değerleri sağlayan [Iclrdebugging::openvirtualprocess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) yöntemi.  
  
 [CLRDataEnumMemoryFlags numaralandırması](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md)  
 Hangi bellek bölümlerinin yapılan bir çağrı gösterir [Iclrdataenummemoryregions::enummemoryregions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) yöntemi içermelidir.  
  
 [COR_PUB_ENUMPROCESS numaralandırması](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md)  
 Numaralandırılacak işlem türünü tanımlar.  
  
 [CorDebugBlockingReason numaralandırması](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingreason-enumeration.md)  
 Bir iş parçacığı neden engellenmiş duruma nedeniyle belirli bir nesne üzerinde belirtir.  
  
 CorDebugChainReason  
 Neden veya çağrı zincirine başlatma nedenlerle gösterir.  
  
 [Cordebugcodeınvokekind numaralandırması](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md)  
 Yönetilen kod nasıl verilen işlevi çağırır açıklar.  
  
 [Cordebugcodeınvokepurpose numaralandırması](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md)  
 Yönetilen kod neden verilen işlevi çağırır açıklar.  
  
 CorDebugCreateProcessFlags  
 Çağrıda kullanılan ek hata ayıklama seçenekleri sunar [Icordebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) yöntemi.  
  
 [CorDebugDebugEventKind numaralandırması](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)  
 , Bilgileri kodunu çözdü olay türünü gösterir [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) yöntemi.  
  
 [CorDebugDecodeEventFlagsWindows numaralandırması](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md)  
 Hata ayıklama olaylar hakkında ek bilgi Windows platformunda sağlar.  
  
 CorDebugExceptionCallbackType  
 Gelen yaptığınız geri çağırma türünü gösteren bir [Icordebugmanagedcallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) olay.  
  
 [CorDebugExceptionFlags numaralandırması](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)  
 Bir özel durum hakkında ek bilgi sağlar.  
  
 CorDebugExceptionUnwindCallbackType  
 Geri çağırma göre geriye doğru izleme aşamasında işaret olay gösterir.  
  
 [Cordebuggctype sabit listesi](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md)  
 Çöp toplayıcı bir iş istasyonunda veya sunucuda çalışıp çalışmadığını gösterir.  
  
 [Cordebuggenerationtypes sabit listesi](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md)  
 Bellek bölgesi nesil yönetilen yığında belirtir.  
  
 CorDebugHandleType  
 Tanıtıcı türü gösterir.  
  
 [Cordebugıltonativemappingtypes numaralandırması](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md)  
 Yerel yönergeleri belirli bir dizi özel kod bölgesine karşılık gelen olup olmadığını gösterir.  
  
 Cordebugıntercept  
 İçine adım adım kod türlerini belirtir.  
  
 [Cordebugınterfaceversion numaralandırması](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md)  
 .NET Framework sürümü ya da bir arabirim kullanılmaya başlanan .NET Framework sürümünü belirtir.  
  
 Cordebugınternalframetype  
 Yığın çerçevesi türünü tanımlar.  
  
 [Cordebugjıtcompilerflags numaralandırması](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)  
 Yönetilen tam zamanında (JIT) derleyici davranışını etkilemek değerlerini içerir.  
  
 [Cordebugjıtcompilerflagsdeprecated numaralandırması](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflagsdeprecated-enumeration.md)  
 Kullanımdan kalktı. Kullanım `CORDEBUG_JIT_DEFAULT` üyesi [Cordebugjıtcompilerflags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) numaralandırma yerine.  
  
 CorDebugMappingResult  
 Yönerge işaretçisi (IP) değerini nasıl edinilen ayrıntılarını sağlar.  
  
 [CorDebugMDAFlags numaralandırması](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md)  
 İş parçacığı üzerinde yönetilen hata ayıklama Yardımcısı (MDA) tetiklenir durumunu belirtir.  
  
 [Cordebugngenpolicy sabit listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md)  
 Bir hata ayıklayıcısı yerel görüntü önbellekten yerel (NGen) görüntüler yükler olup olmadığını belirleyen bir değer sağlar.  
  
 [CorDebugPlatform numaralandırması](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md)  
 Tarafından kullanılan hedef platform değerleri sağlayan [Icordebugdatatarget::getplatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) yöntemi.  
  
 [CorDebugRecordFormat numaralandırması](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
 Yerel özel durum hata ayıklama olay hakkında bilgi içeren bir bayt dizisi verilerin biçimini tanımlar.  
  
 CorDebugRegister  
 Verilen işlemci mimarisi ile ilişkili olan kayıtları belirtir.  
  
 [CorDebugSetContextFlag numaralandırması](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md)  
 Bağlam etkin olup olmadığını gösterir (veya yaprak) çerçeve yığında veya başka bir çerçevesinden geriye doğru izleme tarafından hesaplanır.  
  
 [CorDebugStateChange numaralandırması](../../../../docs/framework/unmanaged-api/debugging/cordebugstatechange-enumeration.md)  
 Değişiklikleri işleme dayalı atılan gerekir önbelleğe alınan veri miktarı açıklar.  
  
 CorDebugStepReason  
 Tek bir adımı sonucunu gösterir.  
  
 CorDebugThreadState  
 Hata ayıklama için bir iş parçacığı durumunu belirtir.  
  
 \>CorDebugUnmappedStop  
 Kod yürütülmesine durdurmak tarafından Adımlayıcı tetikleyebilir eşlenmemiş kod türünü belirtir.  
  
 CorDebugUserState  
 Bir iş parçacığı kullanıcı durumunu gösterir.  
  
 [CorGCReferenceType sabit listesi](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)  
 Çöp toplanan olması için bir nesne kaynak tanımlar.  
  
 [Ilcodekind numaralandırması](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md)  
 Hata ayıklayıcı yerel değişkenler veya profiler ReJIT araçları eklenen kod erişmek yapılıp yapılamayacağını belirten değerleri sağlar.  
  
 [LoggingLevelEnum numaralandırması](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md)  
 Yönetilen iş parçacığı bir olayı günlüğe kaydettiğinde, olay günlüğüne yazılır açıklayıcı bir ileti önem düzeyini gösterir.  
  
 [LogSwitchCallReason numaralandırması](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md)  
 Hata ayıklama izleme anahtarı üzerinde gerçekleştirilen işlemi gösterir.  
  
 [VariableLocationType numaralandırması](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)  
 Bir değişken yerel konum türünü belirtir.  
  
 [WriteableMetadataUpdateMode numaralandırması](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md)  
 Bellek içi güncelleştirmeleri meta verilerinin bir hata ayıklayıcısı görünür olup olmadığını belirten değerleri sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Hata ayıklama coclass'ları](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [Hata ayıklama arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [Hata ayıklama genel statik işlevleri](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [Hata ayıklama yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
