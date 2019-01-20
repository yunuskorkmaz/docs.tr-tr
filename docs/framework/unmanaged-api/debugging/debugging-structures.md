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
ms.openlocfilehash: 23aa619d666f2e0b9eb67ab4cf8d4f92761865d3
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415331"
---
# <a name="debugging-structures"></a>Hata Ayıklama Yapıları
Bu bölümde, hata ayıklama API'SİNİN kullandığı yönetilmeyen yapıları açıklar.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [CLR_DEBUGGING_VERSION Yapısı](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md)  
 Ürün sürümü, hata ayıklama amacıyla ortak dil çalışma zamanı (CLR) tanımlar.  
  
 [CodeChunkInfo Yapısı1](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md)  
 Tek bir öbek kod bellekte temsil eder.  
  
 [CorDebugBlockingObject Yapısı](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)  
 Bir iş parçacığı ve iş parçacığı neden engellenir nedeni engelleyen bir nesneyi tanımlar.  
  
 [CorDebugEHClause Yapısı](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)  
 Bir özel durum işleme (EH) yan tümcesi için Ara dil (IL) belirli bir parçasını temsil eder.  
  
 [CorDebugExceptionObjectStackFrame Yapısı](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 Temsil, çerçeve bilgileri bir özel durum nesnesinden yığın.  
  
 [CorDebugExceptionObjectStackFrame Yapısı](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 Eşlemeleri bir [!INCLUDE[wrt](../../../../includes/wrt-md.md)] , karşılık gelen GUID [Icordebugtype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) nesne.  
  
 COR_ACTIVE_FUNCTION  
 Bir iş parçacığının çerçevelerde şu an etkin olan işlevler hakkında bilgiler içerir.  
  
 [COR_ARRAY_LAYOUT Yapısı](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md)  
 Bir dizi nesnesinin bellek düzeni hakkında bilgi sağlar.  
  
 COR_DEBUG_IL_TO_NATIVE_MAP  
 Yerel kod için Microsoft Ara dil (MSIL) kodu eşlemek için kullanılan uzaklıkları içerir.  
  
 COR_DEBUG_STEP_RANGE  
 Kod aralığı uzaklık bilgilerini içerir.  
  
 [COR_FIELD Yapısı](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)  
 Bir alan bir nesne hakkında bilgi sağlar.  
  
 [COR_GC_REFERENCE Yapısı](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)  
 Atık olarak toplanmış olacak bir nesneyle ilgili bilgileri içerir.  
  
 [COR_HEAPINFO Yapısı](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)  
 Numaralandırılabilir olup olmadığı dahil çöp toplama yığınındaki hakkında genel bilgiler sağlar.  
  
 [COR_HEAPOBJECT Yapısı](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)  
 Yönetilen yığındaki bir nesne hakkında bilgi sağlar.  
  
 COR_IL_MAP  
 Değişiklikleri, bir işlevin göreli uzaklığı belirtir.  
  
 [COR_SEGMENT Yapısı](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md)  
 Bellek yönetilen yığında bir bölge hakkında bilgi içerir.  
  
 [COR_TYPEID Yapısı](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)  
 Tür tanımlayıcısını içerir.  
  
 [COR_TYPE_LAYOUT Yapısı](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)  
 Bellekte bir nesne düzeni hakkında bilgiler sağlar.  
  
 COR_VERSION  
 Ortak dil çalışma zamanı standart Dört bölümlü sürüm numarasını depolar.  
  
 [StackTrace_SimpleContext Yapısı](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md)  
 Tam yerine kullanılabilecek basit bir bağlam sağlar `CONTEXT` yapısı.

 [CLRDATA_ADDRESS_RANGE yapısı](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md) bir adres aralığı tanımlar.
 
 [CLRDATA_IL_ADDRESS_MAP yapısı](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md) bir IL adresi eşleme tanımlar.
 
 [DacpGetModuleAddress yapısı](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md) modülü adresi isteği için bir kapsayıcı tanımlar.

  
## <a name="related-sections"></a>İlgili Bölümler  
 [Hata Ayıklama Coclass’ları](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [Hata Ayıklama Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
