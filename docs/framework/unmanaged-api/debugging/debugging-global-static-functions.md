---
title: "Hata Ayıklama Genel Statik İşlevleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- global static functions [.NET Framework debugging]
- debugging global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], debugging
ms.assetid: efc64414-77c3-48d0-881a-8594ed416aad
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7fde0941959619f4832019806401be0ffddb81e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-global-static-functions"></a>Hata Ayıklama Genel Statik İşlevleri
Bu bölümde, hata ayıklama API'si kullanan yönetilmeyen genel statik işlevler açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [_EFN_GetManagedExcepStack İşlevi](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedexcepstack-function.md)  
 Yönetilen özel durum nesnesi adresi içinde yer alan yığın izleme dize sürümünü döndürür.  
  
 [_EFN_GetManagedObjectFieldInfo İşlevi](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectfieldinfo-function.md)  
 Uzaklık, bir alan ve alanın değerini, sağlanan nesne işaretçisi ve alan adını kullanarak bir nesne başından alır.  
  
 [_EFN_GetManagedObjectName İşlevi](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectname-function.md)  
 Sağlanan yönetilen nesne işaretçisi kullanılarak bir türün adını alır.  
  
 [_EFN_StackTrace İşlevi](../../../../docs/framework/unmanaged-api/debugging/efn-stacktrace-function.md)  
 Yönetilen yığın izlemesi metin gösterimini ve bir dizi sağlar `CONTEXT` kaydeder, bir yönetilmeyen ve yönetilen kod arasında her geçiş için.  
  
 [CLRDataCreateInstance İşlevi](../../../../docs/framework/unmanaged-api/debugging/clrdatacreateinstance-function.md)  
 Belirtilen hedef işlem için belirtilen arabirimi nesnesi oluşturmak için ortak dil çalışma zamanı (CLR) veri erişim hizmeti tarafından çağrılır.  
  
 [PFN_CLRDataCreateInstance İşlev İşaretçisi](../../../../docs/framework/unmanaged-api/debugging/pfn-clrdatacreateinstance-function-pointer.md)  
 Belirtilen hedef işlem için belirtilen arabirimi nesnesi oluşturmak için Sertifika Hizmetleri'ni erişim noktaları tarafından CLR veri adlı bir işlev.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Hata Ayıklama Coclass’ları](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [Hata Ayıklama Yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
