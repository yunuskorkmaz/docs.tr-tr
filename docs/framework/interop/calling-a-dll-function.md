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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61643575"
---
# <a name="calling-a-dll-function"></a>DLL İşlevini Çağırma
Yönetilmeyen DLL işlevleri çağırma diğer yönetilen kod çağırmak için neredeyse aynı olsa da, karmaşık görünen DLL işlevleri yapabilirsiniz farklar vardır ilk. Bu bölüm, olağan dışı arama ile ilgili sorunlardan bazılarını açıklayan konulara tanıtır.  
  
 Platformdan iade yapıları çağrıları çağırma veri türleri, yönetilen ve yönetilmeyen kod içinde aynı gösterimi sahip olması gerekir. Bu türler olarak adlandırılır *türlerse* dönüştürme gerektirmediğinden (bkz [blok halinde kopyalanabilir ve örnekteki](../../../docs/framework/interop/blittable-and-non-blittable-types.md)). Dönüş türü olarak kopyalanamaz yapısının bir işlevi çağırmak için kopyalanamaz türü olarak aynı boyutta blittable Yardımcısı tür tanımlama ve işlev döndürdükten sonra verileri dönüştürün.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Yapıları Geçirme](../../../docs/framework/interop/passing-structures.md)  
 Önceden tanımlanmış bir düzen ile veri yapıları geçirme sorunları tanımlar.  
  
 [Geri Arama İşlevleri](../../../docs/framework/interop/callback-functions.md)  
 Geri çağırma işlevleri hakkında temel bilgiler sağlar.  
  
 [Nasıl yapılır: Geri çağırma işlevlerini uygulama](../../../docs/framework/interop/how-to-implement-callback-functions.md)  
 Geri çağırma işlevleri yönetilen koda uygulanması açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Yönetilmeyen DLL İşlevlerini Kullanma](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 Yönetilmeyen çağrı açıklamaktadır platformunu kullanarak DLL işlevleri çağırma.  
  
 [Platform Çağırma ile Veri Hazırlama](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)  
 Yöntem parametreleri bildirmek ve yönetilmeyen kitaplıkları tarafından dışarı aktarılan işlevler için bağımsız değişkenler geçirmek açıklar.
