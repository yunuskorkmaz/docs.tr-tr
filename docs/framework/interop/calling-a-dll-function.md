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
ms.openlocfilehash: b842f44711d38a996b9d710dbe8bd369d30c5443
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71051879"
---
# <a name="calling-a-dll-function"></a>DLL İşlevini Çağırma
Yönetilmeyen DLL işlevlerinin çağrılması, diğer yönetilen kodu çağırmaya neredeyse özdeş olsa da, ilk olarak DLL işlevlerinin kafa karıştırıcı görünmesine neden olabilir. Bu bölümde, bazı olağan dışı arama ile ilgili sorunlardan bazıları açıklanır.  
  
 Platform çağırma çağrılarının döndürdüğü yapıların, yönetilen ve yönetilmeyen koddaki aynı gösterimine sahip veri türleri olması gerekir. Bu tür türler, dönüşüm gerektirmediğinden *blittable türler* olarak adlandırılır (bkz. [blittable ve blittable olmayan türler](blittable-and-non-blittable-types.md)). Dönüş türü olarak blittable olmayan bir yapıya sahip bir işlevi çağırmak için, blittable olmayan türle aynı büyüklükte bir blittable yardımcı türü tanımlayabilir ve işlevin döndürdüğü sonra verileri dönüştürebilirsiniz.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Yapıları Geçirme](passing-structures.md)  
 Önceden tanımlanmış bir düzen ile veri yapıları geçirme sorunlarını belirler.  
  
 [Geri Arama İşlevleri](callback-functions.md)  
 Geri çağırma işlevleriyle ilgili temel bilgileri sağlar.  
  
 [Nasıl yapılır: Geri çağırma Işlevlerini Uygula](how-to-implement-callback-functions.md)  
 Yönetilen kodda geri çağırma işlevlerinin nasıl uygulanacağını açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Yönetilmeyen DLL İşlevlerini Kullanma](consuming-unmanaged-dll-functions.md)  
 Platform Invoke kullanılarak yönetilmeyen DLL işlevlerinin nasıl çağrılacağını açıklar.  
  
 [Platform Çağırma ile Veri Hazırlama](marshaling-data-with-platform-invoke.md)  
 Yöntem parametrelerinin nasıl bildirilemeyeceğini ve yönetilmeyen kitaplıklar tarafından dışarıya alınan işlevlere bağımsız değişkenlerin nasıl geçirileceğini açıklar.
