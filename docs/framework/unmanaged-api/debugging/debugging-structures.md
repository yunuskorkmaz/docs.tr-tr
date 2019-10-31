---
title: Hata Ayıklama Yapıları
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged structures [.NET Framework], debugging
- debugging structures [.NET Framework]
- structures [.NET Framework debugging]
ms.assetid: 173ba2c2-ab34-49ae-b6a8-e5c49882bf05
ms.openlocfilehash: 05a321d5025f03d6a0378b462178bf06c0291f48
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123029"
---
# <a name="debugging-structures"></a>Hata Ayıklama Yapıları

Bu bölümde hata ayıklama API 'sinin kullandığı yönetilmeyen yapılar açıklanmaktadır.

## <a name="in-this-section"></a>Bu Bölümde
 [CLRDATA_ADDRESS_RANGE yapısı](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md) Bir adres aralığı tanımlar.

 [CLRDATA_IL_ADDRESS_MAP yapısı](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md) Adres eşleme için bir Il tanımlar

 [CLR_DEBUGGING_VERSION yapısı](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) Hata ayıklama amacıyla ortak dil çalışma zamanının (CLR) ürün sürümünü tanımlar.

 [CodeChunkInfo yapısı](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md) Bellekte tek bir kod öbeğini temsil eder.

 [COR_ACTIVE_FUNCTION](cor-active-function-structure.md) Şu anda bir iş parçacığının çerçevelerinde etkin olan işlevlerle ilgili bilgiler içerir.

 [COR_ARRAY_LAYOUT yapısı](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) Bellekte bir dizi nesnesinin yerleşimi hakkında bilgi sağlar.

 [COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md) Microsoft ara dili (MSIL) kodunu yerel kodla eşlemek için kullanılan uzaklıkları içerir.

 [COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md) Bir kod aralığı için konum bilgilerini içerir.

 [COR_FIELD yapısı](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) Bir nesne içindeki bir alan hakkında bilgi sağlar.

 [Cor_gc_reference yapısı](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) Atık olarak toplanmış bir nesne hakkındaki bilgileri içerir.

 [COR_HEAPINFO yapısı](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) Çöp toplama yığını hakkında, numaralandırılabilir olup olmadığı dahil genel bilgiler sağlar.

 [COR_HEAPOBJECT Yapısı](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) Yönetilen yığında bir nesne hakkında bilgi sağlar.

 [COR_IL_MAP](cor-il-map-structure.md) Bir işlevin göreli uzaklığının değişikliklerini belirtir.

 [COR_SEGMENT Yapısı](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) Yönetilen yığında bir bellek bölgesi hakkındaki bilgileri içerir.

 [COR_TYPEID yapısı](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) Bir tür tanımlayıcısı içerir.

 [Cor_type_layout yapısı](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) Bellekteki bir nesnenin düzeni hakkında bilgi sağlar.

 [COR_VERSION](cor-version-structure.md) Ortak dil çalışma zamanının Standart Dört parçalı sürüm numarasını depolar.

 [CorDebugBlockingObject yapısı](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) Bir iş parçacığını engelleyen bir nesne ve iş parçacığının engellenme nedenini tanımlar.

 [Corhata ayıklama Gehclause yapısı](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) Belirli bir ara dil (IL) parçası için bir özel durum işleme (EH) yan tümcesini temsil eder.

 [CorDebugExceptionObjectStackFrame yapısı](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) Bir özel durum nesnesinden yığın çerçeve bilgilerini temsil eder.

 [CorDebugGuidToTypeMapping yapısı](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) Windows Çalışma Zamanı GUID 'sini karşılık gelen [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) nesnesine eşler.

 [DacpGetModuleAddress yapısı](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md) Modül adresi isteği için kapsayıcıyı tanımlar.

 [Dadcpmethoddescdata yapısı](../../../../docs/framework/unmanaged-api/debugging/dacpmethoddescdata-structure.md) Metodun çalışma zamanı bilgileri için bir aktarım arabelleği tanımlar.

 [Dadcpmoduledata yapısı](../../../../docs/framework/unmanaged-api/debugging/dacpmoduledata-structure.md) Modülün çalışma zamanı bilgileri için bir aktarım arabelleği tanımlar.

 [Dacprejdata yapısı](../../../../docs/framework/unmanaged-api/debugging/dacprejitdata-structure.md) Belirli bir profil oluşturucu tarafından işaretlenmiş yöntem hakkında temel bilgileri tanımlar.

 [StackTrace_SimpleContext yapısı](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) Tam `CONTEXT` yapısının yerine kullanılabilecek basit bir bağlam sağlar.

## <a name="related-sections"></a>İlgili Bölümler

 [Hata Ayıklama Coclass’ları](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)

 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

 [Hata Ayıklama Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)

 [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
