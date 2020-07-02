---
title: DLL İşlevleri için bir Sınıf Oluşturma
description: .NET ' te platform işlevlerinin kapsüllemeye yardımcı olan DLL işlevlerini barındırmak için yönetilen bir sınıf sarmalayıcı oluşturun.
ms.date: 03/30/2017
helpviewer_keywords:
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, creating class for functions
- DLL functions
ms.assetid: e08e4c34-0223-45f7-aa55-a3d8dd979b0f
ms.openlocfilehash: b8aa0361ee5213cb947a102f903d1a7a35331f17
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622178"
---
# <a name="creating-a-class-to-hold-dll-functions"></a>DLL İşlevleri için bir Sınıf Oluşturma
Yönetilen bir sınıfta sık kullanılan bir DLL işlevinin sarmalanması, platform işlevlerini kapsüllemek için etkili bir yaklaşımdır. Her durumda bunu yapmak zorunlu olmasa da, DLL işlevlerinin tanımlanması çok fazla ve hataya açık olabileceğinden sınıf sarmalayıcı sağlanması kullanışlıdır. Visual Basic veya C# ' de programlıyorsanız, DLL işlevlerini bir sınıf veya Visual Basic modülü içinde bildirmeniz gerekir.  
  
 Bir sınıf içinde, çağırmak istediğiniz her DLL işlevi için bir statik yöntem tanımlarsınız. Tanım, yöntem bağımsız değişkenlerinde kullanılan karakter kümesi veya çağırma kuralı gibi ek bilgileri içerebilir; Bu bilgileri atlayarak varsayılan ayarları seçersiniz. Bildirim seçeneklerinin ve varsayılan ayarlarının tüm listesi için bkz. [yönetilen kodda prototipler oluşturma](creating-prototypes-in-managed-code.md).  
  
 Sarmalanan bir kez, diğer herhangi bir sınıfta statik yöntemleri çağırmış olduğunuz sınıftaki yöntemleri çağırabilirsiniz. Platform çağırma, temel alınan içe aktarılmış işlevi otomatik olarak işler.  
  
 Platform çağırma için yönetilen bir sınıf tasarlarken sınıflar ve DLL işlevleri arasındaki ilişkileri göz önünde bulundurun. Örneğin, şunları yapabilirsiniz:  
  
- Varolan bir sınıf içinde DLL işlevleri bildirin.  
  
- Her DLL işlevi için tek bir sınıf oluşturun ve işlevleri yalıtılmış ve kolay bir şekilde bulabilir.  
  
- Mantıksal gruplandırmaları biçimlendirmek ve ek yükü azaltmak için bir dizi ilgili DLL işlevi için bir sınıf oluşturun.  
  
 Sınıfı ve yöntemlerini sizin gibi adlandırın. Nasıl oluşturulacağını gösteren örnekler için. Platform çağırma ile kullanılacak NET tabanlı bildirimler, bkz. [Platform çağırma Ile verileri sıralama](marshaling-data-with-platform-invoke.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilmeyen DLL İşlevlerini Kullanma](consuming-unmanaged-dll-functions.md)
- [DLL'lerde İşlevleri Tanımlama](identifying-functions-in-dlls.md)
- [Yönetilen Kodda Prototipler Oluşturma](creating-prototypes-in-managed-code.md)
- [DLL İşlevini Çağırma](calling-a-dll-function.md)
