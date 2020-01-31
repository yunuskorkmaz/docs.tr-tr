---
title: Hata Ayıklama Genel Statik İşlevleri
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework debugging]
- debugging global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], debugging
ms.assetid: efc64414-77c3-48d0-881a-8594ed416aad
ms.openlocfilehash: c20d8719b63cb40074dc740506ae4a3c0fc3a251
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793774"
---
# <a name="debugging-global-static-functions"></a>Hata Ayıklama Genel Statik İşlevleri
Bu bölümde, hata ayıklama API 'sinin kullandığı yönetilmeyen genel statik işlevler açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [_EFN_GetManagedExcepStack İşlevi](efn-getmanagedexcepstack-function.md)  
 Yönetilen bir özel durum nesne adresi verildiğinde, içinde bulunan yığın izlemenin bir dize sürümünü döndürür.  
  
 [_EFN_GetManagedObjectFieldInfo İşlevi](efn-getmanagedobjectfieldinfo-function.md)  
 Belirtilen nesne işaretçisini ve alan adını kullanarak bir nesnenin başından bir alana ve alanın değerine kadar olan sapmayı alır.  
  
 [_EFN_GetManagedObjectName İşlevi](efn-getmanagedobjectname-function.md)  
 Belirtilen yönetilen nesne işaretçisini kullanarak bir türün adını alır.  
  
 [_EFN_StackTrace İşlevi](efn-stacktrace-function.md)  
 Yönetilmeyen ve yönetilen kod arasındaki her geçiş için bir yönetilen yığın izlemenin ve bir dizi `CONTEXT` kaydın metin gösterimini sağlar.  
  
 [CLRDataCreateInstance İşlevi](clrdatacreateinstance-function.md)  
 Belirtilen hedef işlem için belirtilen arabirim nesnesini oluşturmak için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağırılır.  
  
 [PFN_CLRDataCreateInstance İşlev İşaretçisi](pfn-clrdatacreateinstance-function-pointer.md)  
 Belirtilen hedef işlem için belirtilen arabirim nesnesini oluşturmak üzere CLR veri erişim Hizmetleri tarafından çağrılan bir işleve işaret eder.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Hata Ayıklama Coclass’ları](debugging-coclasses.md)  
  
 [Hata Ayıklama Arabirimleri](debugging-interfaces.md)  
  
 [Hata Ayıklama Sabit Listeleri](debugging-enumerations.md)  
  
 [Hata Ayıklama Yapıları](debugging-structures.md)
