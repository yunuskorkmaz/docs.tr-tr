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
ms.openlocfilehash: 5edd6dfb3dac05ce4614c43949f2ec4c19b5f742
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415955"
---
# <a name="debugging-enumerations"></a>Hata Ayıklama Numaralandırmaları
Bu bölümde, hata ayıklama API'SİNİN kullandığı yönetilmeyen numaralandırmaları açıklar.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [CLR_DEBUGGING_PROCESS_FLAGS Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md)  
 Tarafından kullanılan değerleri sağlar [Iclrdebugging::openvirtualprocess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) yöntemi.  
  
 [CLRDataEnumMemoryFlags Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md)  
 Hangi bellek bölgeleri için bir çağrı gösterir [Iclrdataenummemoryregions::enummemoryregions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) yöntemini içerir.  
  
 [COR_PUB_ENUMPROCESS Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md)  
 Numaralandırılacak işlem türünü belirtir.  
  
 [CorDebugBlockingReason Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingreason-enumeration.md)  
 Belirli bir nesne üzerinde bir iş parçacığı neden engellenmiş duruma nedenlerini belirtir.  
  
 CorDebugChainReason  
 Neden veya çağrı zincirinin başlatma nedenlerle gösterir.  
  
 [CorDebugCodeInvokeKind Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md)  
 Dışarı aktarılan bir işlevin yönetilen kod nasıl çağırır açıklar.  
  
 [CorDebugCodeInvokePurpose Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md)  
 Neden yönetilen kod dışa aktarılan bir işlevin çağrıları açıklar.  
  
 CorDebugCreateProcessFlags  
 Bir çağrıda kullanılan ek hata ayıklama seçenekleri sağlar [Icordebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) yöntemi.  
  
 [CorDebugDebugEventKind Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)  
 , Bilgileri kodu çözülen olay türünü gösteren [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) yöntemi.  
  
 [CorDebugDecodeEventFlagsWindows Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md)  
 Hata ayıklama olaylar hakkında ek bilgi için Windows platformunda sağlar.  
  
 CorDebugExceptionCallbackType  
 Gelen yapılan bir geri çağırma türünü gösteren bir [Icordebugmanagedcallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) olay.  
  
 [CorDebugExceptionFlags Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)  
 Bir özel durum hakkında ek bilgi sağlar.  
  
 CorDebugExceptionUnwindCallbackType  
 Geri çağırma tarafından geriye doğru izleme aşamasında sinyal olay gösterir.  
  
 [CorDebugGCType Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md)  
 Atık toplayıcı bir iş istasyonunda veya sunucuda çalışıp çalışmadığını gösterir.  
  
 [CorDebugGenerationTypes Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md)  
 Yönetilen yığında bir bellek bölgesini oluşturulmasını belirtir.  
  
 CorDebugHandleType  
 Tanıtıcı türü gösterir.  
  
 [CorDebugIlToNativeMappingTypes Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md)  
 Yerel yönergeleri belirli bir dizi özel kod bölgesine karşılık gelen olup olmadığını gösterir.  
  
 Cordebugıntercept  
 İçine girdiğiniz kod türlerini belirtir.  
  
 [CorDebugInterfaceVersion Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md)  
 .NET Framework sürümünü veya içinde bir arabirimi kullanıma sunulmuştur .NET Framework sürümünü belirtir.  
  
 Cordebugınternalframetype  
 Yığın çerçevesinin türünü tanımlar.  
  
 [CorDebugJITCompilerFlags Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)  
 Yönetilen just-ın-time (JIT) derleyici davranışını etkileyen değerlerini içerir.  
  
 [CorDebugJITCompilerFlagsDeprecated Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflagsdeprecated-enumeration.md)  
 Kullanımdan kalktı. Kullanım `CORDEBUG_JIT_DEFAULT` üyesi [Cordebugjıtcompilerflags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) numaralandırma yerine.  
  
 CorDebugMappingResult  
 Yönerge işaretçisi (IP) değerini nasıl edinilen ayrıntılarını sağlar.  
  
 [CorDebugMDAFlags Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md)  
 Yönetilen hata ayıklama Yardımcısı (MDA) harekete geçirilen iş parçacığı durumunu belirtir.  
  
 [CorDebugNGenPolicy Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md)  
 Bir hata ayıklayıcı yerel görüntü önbelleğinden kaldırırız (NGen) yerel görüntüleri yükleyip yüklemediğini belirleyen bir değer sağlar.  
  
 [CorDebugPlatform Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md)  
 Tarafından kullanılan hedef platform değerleri sağlayan [Icordebugdatatarget::getplatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) yöntemi.  
  
 [CorDebugRecordFormat Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
 Yerel özel durum hata ayıklama olayla ilgili bilgileri içeren bir bayt dizisi verilerinin biçimini tanımlar.  
  
 CorDebugRegister  
 Bir verilen işlemci mimarisi ile ilişkili olan kayıtları belirtir.  
  
 [CorDebugSetContextFlag Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md)  
 Bağlam etkin olup olmadığını belirtir (veya yaprak) çerçevesi yığın üzerinde veya başka bir çerçeveden geriye doğru izleme tarafından hesaplanır.  
  
 [CorDebugStateChange Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/cordebugstatechange-enumeration.md)  
 Değişiklikler iş akışına dayalı atılması gerekir önbelleğe alınan veri miktarı açıklar.  
  
 CorDebugStepReason  
 Bir adımın sonucunu gösterir.  
  
 CorDebugThreadState  
 Hata ayıklama için bir iş parçacığı durumunu belirtir.  
  
 \>CorDebugUnmappedStop  
 Kod yürütülmesine bir durdurmak tarafından adımlayıcıdaki tetikleyebilirsiniz eşlenmemiş kodun türünü belirtir.  
  
 CorDebugUserState  
 Kullanıcı durumunu bir iş parçacığının gösterir.  
  
 [CorGCReferenceType Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)  
 Kaynağı olarak atık olarak toplanmış bir nesneyi tanımlar.  
  
 [ILCodeKind Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md)  
 Hata ayıklayıcı yerel değişkenler veya ReJIT izleme profil oluşturucu, eklenen kod erişmek mümkün olup olmadığını belirten değerleri sağlar.  
  
 [LoggingLevelEnum Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md)  
 Yönetilen iş parçacığı bir olayı günlüğe kaydettiğinde, olay günlüğüne yazılan açıklayıcı bir iletisi önem derecesi düzeyini gösterir.  
  
 [LogSwitchCallReason Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md)  
 Hata ayıklama izlemeyi anahtarda gerçekleştirilen bir işlemi belirtir.  
  
 [VariableLocationType Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)  
 Bir değişken yerel konum türünü belirtir.  
  
 [WriteableMetadataUpdateMode Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md)  
 Meta veriler için bellek içi güncelleştirmeler için bir hata ayıklayıcı görünür olup olmadığını belirten değerleri sağlar. 

 [ClrDataSourceType numaralandırma](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md) CLRDATA_IL_ADDRESS_MAP yapısı tarafından kullanılan değerleri sağlar.

## <a name="related-sections"></a>İlgili Bölümler  
 [Hata Ayıklama Coclass’ları](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [Hata Ayıklama Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [Hata Ayıklama Yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
