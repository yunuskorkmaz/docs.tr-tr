---
title: DLL İşlevini Çağırma
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged functions, calling
- unmanaged functions
- COM interop, platform invoke
- platform invoke, calling unmanaged functions
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 113646de-7ea0-4f0e-8df0-c46dab3e8733
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 98d363b6c0838ff1211d969391f04ce8ccddd003
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33387139"
---
# <a name="calling-a-dll-function"></a>DLL İşlevini Çağırma
Yönetilmeyen DLL işlevleri çağırma diğer yönetilen kodu çağırma için neredeyse aynı olsa da, DLL işlevleri kafa karıştırıcı göründüğü yapabilirsiniz farklar vardır ilk. Bu bölümde bazı olağan dışı arama ile ilgili sorunları açıklayan konulara tanıtır.  
  
 Platformundan döndürülen yapıları çağırma çağrıları aynı gösterimi yönetilen ve yönetilmeyen kodunda varsa veri türleri olması gerekir. Bu tür türleri olarak adlandırılır *blittable türleri* dönüştürme gerektirmediği için (bkz [blok halinde kopyalanabilir ve olmayan Blittable türleri](../../../docs/framework/interop/blittable-and-non-blittable-types.md)). Dönüş türü olarak blittable olmayan yapısının bir işlevi çağırmak için aynı boyutta blittable Yardımcısı tür blittable olmayan türü olarak tanımlama ve işlev döndükten sonra verileri dönüştürün.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Yapıları Geçirme](../../../docs/framework/interop/passing-structures.md)  
 Önceden tanımlanmış bir düzende veri yapıları geçirme sorunlarını tanımlar.  
  
 [Geri Arama İşlevleri](../../../docs/framework/interop/callback-functions.md)  
 Geri arama işlevleri ile ilgili temel bilgileri sağlar.  
  
 [Nasıl yapılır: Geri Çağırma İşlevlerini Uygulama](../../../docs/framework/interop/how-to-implement-callback-functions.md)  
 Yönetilen kodda geri çağırma işlevlerini gerçekleştirmek açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Yönetilmeyen DLL İşlevlerini Kullanma](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 Yönetilmeyen çağrılacağını açıklar platformu kullanılarak DLL işlevleri çağırma.  
  
 [Platform Çağırma ile Veri Hazırlama](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)  
 Yöntem parametreleri bildirme ve yönetilmeyen kitaplıkları tarafından dışarı aktarılan işlevler için bağımsız değişkenler geçirmek açıklar.
