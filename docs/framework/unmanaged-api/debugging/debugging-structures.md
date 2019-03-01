---
title: Hata Ayıklama Yapıları
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged structures [.NET Framework], debugging
- debugging structures [.NET Framework]
- structures [.NET Framework debugging]
ms.assetid: 173ba2c2-ab34-49ae-b6a8-e5c49882bf05
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f50db519410b9513725c3dc10637421ba8bb37ec
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965234"
---
# <a name="debugging-structures"></a>Hata Ayıklama Yapıları

Bu bölümde, hata ayıklama API'SİNİN kullandığı yönetilmeyen yapıları açıklar.

## <a name="in-this-section"></a>Bu Bölümde
 [CLRDATA_ADDRESS_RANGE yapısı](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md) bir adres aralığı tanımlar.

 [CLRDATA_IL_ADDRESS_MAP yapısı](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md) bir IL adresi eşleme tanımlar.

 [Clr_debuggıng_versıon yapısı](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) hata ayıklama amacıyla ortak dil çalışma zamanı (CLR) ürün sürümünü tanımlar.

 [Codechunkınfo yapısı](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md) kod bellekte tek bir öbek temsil eder.

 [Cor_actıve_functıon](cor-active-function-structure.md) bir iş parçacığının çerçevelerde şu an etkin olan işlevler hakkında bilgiler içerir.

 [COR_ARRAY_LAYOUT yapısı](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) bir dizi nesnesinin bellek düzeni hakkında bilgiler sağlar.

 [Cor_debug_ıl_to_natıve_map](cor-debug-il-to-native-map-structure.md) Microsoft Ara dilini (MSIL) eşlemek için kullanılan uzaklıkları yerel kod için kod içerir.

 [COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md) kod aralığı uzaklık bilgilerini içerir.

 [Cor_fıeld yapısı](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) bir alanda bir nesne hakkında bilgi sağlar.

 [COR_GC_REFERENCE yapısı](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) atık olarak toplanmış olacak bir nesneyle ilgili bilgileri içerir.

 [Cor_heapınfo yapısı](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) numaralandırılabilir olup olmadığı dahil çöp toplama yığınındaki hakkında genel bilgiler sağlar.

 [COR_HEAPOBJECT yapısı](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) yönetilen yığındaki bir nesne hakkında bilgi sağlar.

 [Cor_ıl_map](cor-il-map-structure.md) değişiklikleri bir işlevin göreli uzaklığı belirtir.

 [COR_SEGMENT yapısı](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) bellek yönetilen yığında bir bölge hakkında bilgi içerir.

 [Cor_typeıd yapısı](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) bir tür tanımlayıcısı içeriyor.

 [COR_TYPE_LAYOUT yapısı](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) bellekte bir nesne düzeni hakkında bilgiler sağlar.

 [Cor_versıon](cor-version-structure.md) ortak dil çalışma zamanı standart Dört bölümlü sürüm numarasını depolar.

 [CorDebugBlockingObject yapısı](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) bir iş parçacığı ve iş parçacığı engellendi neden neden engelleyen bir nesneyi tanımlar.

 [CorDebugEHClause yapısı](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) bir özel durum işleme (EH) yan tümcesi için Ara dil (IL) belirli bir parçasını temsil eder.

 [CorDebugExceptionObjectStackFrame yapısı](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) yığın çerçeve bilgileri bir özel durum nesnesinden temsil eder.

 [CorDebugGuidToTypeMapping yapısı](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) eşlemeleri bir [!INCLUDE[wrt](../../../../includes/wrt-md.md)] , karşılık gelen GUID [Icordebugtype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) nesne.

 [DacpGetModuleAddress yapısı](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md) modülü adresi isteği için bir kapsayıcı tanımlar.

 [DacpMethodDescData yapısı](../../../../docs/framework/unmanaged-api/debugging/dacpmethoddescdata-structure.md) bir yöntemin çalışma zamanı bilgileri için transport arabellek tanımlar.

 [DacpModuleData yapısı](../../../../docs/framework/unmanaged-api/debugging/dacpmoduledata-structure.md) aktarım arabelleği için bir modülün çalışma zamanı bilgileri tanımlar.

 [DacpReJitData yapısı](../../../../docs/framework/unmanaged-api/debugging/dacprejitdata-structure.md) belirli bir profil oluşturucu izleme eklenmiş yöntemi ile ilgili temel bilgileri tanımlar.

 [StackTrace_SimpleContext yapısı](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) tam yerine kullanılabilecek basit bir bağlam sağlar `CONTEXT` yapısı.

## <a name="related-sections"></a>İlgili Bölümler

 [Hata Ayıklama Coclass’ları](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)

 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

 [Hata Ayıklama Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)

 [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
